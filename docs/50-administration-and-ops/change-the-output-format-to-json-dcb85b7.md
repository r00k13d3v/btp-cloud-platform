<!-- loiodcb85b7dea61432cbafaab4ce0ec9b08 -->

# Change the Output Format to JSON

Use the `--format json` option to change the output format to JSON. This is the recommended output format for automation with the btp CLI.



## Context

The standard output format of the btp CLI is plain text, formatted in a way that an interactive user of the btp CLI can easily read it. We don't recommend using this plain text output for automatic parsing and extracting information. The text output is not stable enough, as, for example, column width or the appearance of new lines may depend on the actual content of a response.

If you're using responses of the btp CLI for automation, such as in scripts, we recommend to use the JSON output format. It is much more stable than the plain text output and it often includes more information than the respective text output, as the text output is optimized for human readability and therefore often limited to the most relevant information.

See this [Getting BTP resource GUIDs with the btp CLI](https://blogs.sap.com/2021/12/01/getting-btp-resource-guids-with-the-btp-cli-part-2-json-and-jq/) blog post for some examples.



## Procedure

Start commands with `--format json`. Currently, the only valid value is `json`.

```
btp --format json list accounts/subaccount
```



<a name="loiodcb85b7dea61432cbafaab4ce0ec9b08__result_iyy_c2k_qnb"/>

## Results



### Example with text output

```
btp list accounts/subaccount
subaccounts in global account c8XXXX3d-6XX7-4XXb-8dXX-89XXXX372eXX...
subaccount id:                         display name:                              subdomain:                             region:        beta-enabled:   parent id:                             state:            state message:                                                                                                                                                    

88XXXX80-9844-4XX7-8XXd-beXXXX42bfb2   my-subaccount-1                            my-CF-subdomain1                       us10-TEST      false           c8XXXX3d-6XX7-4XXb-8dXX-89XXXX372eXX   OK                Subaccount created.                                                                                                                                               
ebXXXX3e-f3a2-4XXf-a080-3eXXXX9b9ced   my-subaccount-2                            my-CF-subdomain2                       us10-TEST      false           c8XXXX3d-6XX7-4XXb-8dXX-89XXXX372eXX   OK                Subaccount created.
```



### Example with JSON output

```
btp list --format json accounts/subaccount
{
  "value": [

    {
      "guid": "88XXXX80-9844-4XX7-8XXd-beXXXX42bfb2",
      "displayName": "my-subaccount-1",
      "globalAccountGUID": "c8XXXX3d-6XX7-4XXb-8dXX-89XXXX372eXX",
      "parentGUID": "c8XXXX3d-6XX7-4XXb-8dXX-89XXXX372eXX",
      "parentType": "ROOT",
      "region": "us10-TEST",
      "subdomain": "my-CF-subdomain1",
      "betaEnabled": false,
      "usedForProduction": "UNSET",
      "description": null,
      "expiryDate": null,
      "state": "OK",
      "stateMessage": "Subaccount created.",
      "createdDate": 1602759737909,
      "createdBy": "name@email.com",
      "modifiedDate": 1602759737909,
      "zoneId": null
    },
    {
      "guid": "ebXXXX3e-f3a2-4XXf-a080-3eXXXX9b9ced",
      "displayName": "CF TEST",
      "globalAccountGUID": "c8XXXX3d-6XX7-4XXb-8dXX-89XXXX372eXX",
      "parentGUID": "c8XXXX3d-6XX7-4XXb-8dXX-89XXXX372eXX",
      "parentType": "ROOT",
      "region": "us10-TEST",
      "subdomain": "my-CF-subdomain2",
      "betaEnabled": false,
      "usedForProduction": "UNSET",
      "description": null,
      "expiryDate": null,
      "state": "OK",
      "stateMessage": "Subaccount created.",
      "createdDate": 1602760244477,
      "createdBy": "name@email.com",
      "modifiedDate": 1602760244477,
      "zoneId": null
    }
  ]
} 
```

