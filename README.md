# WaukeshaEngine

The Waukesha Engine is a product of GE Power that is natural gas based. It is used to power a variety of different applications ranging from powering isolated communities to usage within natural gas production applications.
More comprehensive information regarding the Waukesha Engine can be found here. [More Information](https://powergen.gepower.com/content/dam/gepower-pgdp/global/en_US/documents/product/Reciprocating%20Engines/waukesha-powering-the-world-brochure.pdf)



## Environment Variables

##### Credentials
* Client-id = app_client_id
* Secret = secret

The JSON file below includes the varying endpoints for asset ingestion, querying, and more relating to the Waukesha Engine time series data.



```json
"VCAP_SERVICES": {
  "predix-asset": [
   {
    "credentials": {
     "instanceId": "b8609eb7-bee9-40af-a907-7dd4c94e3f88",
     "scriptEngine_uri": "https://b8609eb7-bee9-40af-a907-7dd4c94e3f88.predix-script-engine.run.aws-usw02-pr.ice.predix.io",
     "uri": "https://predix-asset.run.aws-usw02-pr.ice.predix.io",
     "zone": {
      "http-header-name": "Predix-Zone-Id",
      "http-header-value": "b8609eb7-bee9-40af-a907-7dd4c94e3f88",
      "oauth-scope": "predix-asset.zones.b8609eb7-bee9-40af-a907-7dd4c94e3f88.user"
     }
    },
    "label": "predix-asset",
    "name": "mmhack-asset",
    "plan": "Tiered",
    "provider": null,
    "syslog_drain_url": null,
    "tags": [],
    "volume_mounts": []
   }
  ],
  "predix-timeseries": [
   {
    "credentials": {
     "ingest": {
      "uri": "wss://gateway-predix-data-services.run.aws-usw02-pr.ice.predix.io/v1/stream/messages",
      "zone-http-header-name": "Predix-Zone-Id",
      "zone-http-header-value": "e3fba85e-d334-409e-87ce-3a17e71b4946",
      "zone-token-scopes": [
       "timeseries.zones.e3fba85e-d334-409e-87ce-3a17e71b4946.user",
       "timeseries.zones.e3fba85e-d334-409e-87ce-3a17e71b4946.ingest"
      ]
     },
     "query": {
      "uri": "https://time-series-store-predix.run.aws-usw02-pr.ice.predix.io/v1/datapoints",
      "zone-http-header-name": "Predix-Zone-Id",
      "zone-http-header-value": "e3fba85e-d334-409e-87ce-3a17e71b4946",
      "zone-token-scopes": [
       "timeseries.zones.e3fba85e-d334-409e-87ce-3a17e71b4946.user",
       "timeseries.zones.e3fba85e-d334-409e-87ce-3a17e71b4946.query"
      ]
     }
    },
    "label": "predix-timeseries",
    "name": "mmhack-time-series",
    "plan": "Bronze",
    "provider": null,
    "syslog_drain_url": null,
    "tags": [
     "timeseries",
     "time-series",
     "time series"
    ],
    "volume_mounts": []
   }
  ],
  "predix-uaa": [
   {
    "credentials": {
     "issuerId": "https://98d4176d-a268-405b-a461-3f9944793a31.predix-uaa.run.aws-usw02-pr.ice.predix.io/oauth/token",
     "subdomain": "98d4176d-a268-405b-a461-3f9944793a31",
     "uri": "https://98d4176d-a268-405b-a461-3f9944793a31.predix-uaa.run.aws-usw02-pr.ice.predix.io",
     "zone": {
      "http-header-name": "X-Identity-Zone-Id",
      "http-header-value": "98d4176d-a268-405b-a461-3f9944793a31"
     }
    },
    "label": "predix-uaa",
    "name": "mmhack-uaa",
    "plan": "Tiered",
    "provider": null,
    "syslog_drain_url": null,
    "tags": [],
    "volume_mounts": []
   }
  ]
 }
}

{
 "VCAP_APPLICATION": {
  "application_id": "51f0ed51-59c9-4307-8b93-80be196d2e86",
  "application_name": "mmhack-hello-world",
  "application_uris": [
   "mmhack-hello-world-bigamous-varicocele.run.aws-usw02-pr.ice.predix.io"
  ],
  "application_version": "2e211fcc-f787-4187-80f3-0cfabf5aad7f",
  "limits": {
   "disk": 1024,
   "fds": 16384,
   "mem": 256
  },
  "name": "mmhack-hello-world",
  "space_id": "5c6eefb9-6d12-4053-8de9-4a65364d4e50",
  "space_name": "hackhub",
  "uris": [
   "mmhack-hello-world-bigamous-varicocele.run.aws-usw02-pr.ice.predix.io"
  ],
  "users": null,
  "version": "2e211fcc-f787-4187-80f3-0cfabf5aad7f"
 }
```

## Additional information
Currently the assets can be accessed using the query tag /engine
There are 15 assets. But data is being simulated for the following 4 for now.

*    /engine/2afbd553-8d7f-4c59-8346-d93a92b177ba
*    /engine/cb27ef1b-b0de-494d-877f-32e95b757651
*                     /engine/86d23000-3820-4d56-b755-6ea1302ddc4b
*     /engine/892e596d-3sds-4c9e-9094-078245931785

###### The available tags in the time series for Waukesha engine are:
*    "Engine Frequency",
*     "Engine Hours"
*        "Engine LB Exhaust Temp"
*        "Engine Load"
*        "Engine Oil Pressure"
*        "Engine Oil Temp"
*        "Engine Power"
*        "Engine Power - Insights"
*        "Engine RB Exhaust Temp"
*        "Engine Speed"
###### Query for the time series data  (ex: Engine oil pressure for asset with uri: "/engine/2afbd553-8d7f-4c59-8346-d93a92b177ba”)
```json
{  
   "start":"1y-ago",
   "tags":[  
      {  
         "name":"Engine Oil Pressure",
         "order":"desc",
         "filters":{  
            "attributes":{  
               "AssetUri":"/engine/2afbd553-8d7f-4c59-8346-d93a92b177ba"
            }
         }
      }
   ]
}
```
