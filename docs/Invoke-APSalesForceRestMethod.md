---
external help file: Snow.SnowAutomationPlatform.SalesForce.Integration-help.xml
Module Name: Snow.SnowAutomationPlatform.SalesForce.Integration
online version: https://developer.salesforce.com/docs/atlas.en-us.api_rest.meta/api_rest/intro_understanding_username_password_oauth_flow.htm
schema: 2.0.0
---

# Invoke-APSalesForceRestMethod

## SYNOPSIS
Calls the SalesForce API with added parsing of access token 

## SYNTAX

```
Invoke-APSalesForceRestMethod [-Endpoint] <String> [-AccessToken] <PSObject> [-Method] <String>
 [[-BaseURI] <Uri>] [[-Body] <Object>] [<CommonParameters>]
```

## DESCRIPTION
This finction makes a call to the SalesForce API using Invoke-WebRequest. 

It automatically parses the passed on Access Token to use correct URI and Token headers.  

It also tries to make sure you always send and receive objects as Json. 

## EXAMPLES

### EXAMPLE 1
```
Invoke-APSalesForceRestMethod -Endpoint '/services/data/v40.0/sobjects/user/' -AccessToken $SalesForceToken -Method Get
```

This command will call the User endpoint using the URI and access tokens from $SalesForceToken. 

 If any result is given it will be sent back to the pipeline.

### EXAMPLE 2
```
Invoke-APSalesForceRestMethod -Endpoint '/services/data/v40.0/sobjects/user/' -AccessToken $SalesForceToken -Method Post -Body $PSCustomObject
```

This command will post the pscustomobject to the user endpoint using the URI and access tokens from $SalesForceToken. 

 It will automatically convert the PSCustomObject to json format before sending it.

### EXAMPLE 3
```
Invoke-APSalesForceRestMethod -Endpoint '/services/data/v40.0/sobjects/user/' -AccessToken $SalesForceToken -Method Post -Body $PSCustomObject -BaseURI 'https://my.other.salesforce.com'
```

This command will post the pscustomobject to the user endpoint using access tokens from $SalesForceToken. 

It will use the base SalesForce URI 'https://my.other.salesforce.com'.

It will automatically convert the PSCustomObject to json format before sending it.

### EXAMPLE 4
```
Invoke-APSalesForceRestMethod -Endpoint '/services/data/v40.0/sobjects/user/' -AccessToken $SalesForceToken -Method Post -Body {"JsonKey":"Value","OtherJsonKey":{"JsonArray":10}}
```

This command will post the already json formated body to the user endpoint using the URI and access tokens from $SalesForceToken. 

## PARAMETERS

### -Endpoint
Path to endpoint in SalesForce API, for example '/services/data/v40.0/sobjects/user/' 


```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AccessToken
AccessToken received from Connect-APSalesForce CmdLet 


```yaml
Type: PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Method
Request method 


```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: True
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -BaseURI
Base URI to your SalesForce domain. 

Only needed if it is different from AccessToken instance_url 


```yaml
Type: Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: 4
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Body
Body to send if method is put or post 


```yaml
Type: Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 5
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS
