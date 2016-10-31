# WS-Fed

```http
http
```

```shell
GET https://${account.namespace}/wsfed/{client-id}
```

```javascript
javascript
```

The WS-Fed protocol is used for Microsoft applications (e.g.: Office365, Dynamics CRM, etc.).

This endpoint accepts a WS-Fed request to initiate a login.

<aside class="notice">
For more information, see: <a href="/protocols#ws-federation">WS-Federation Protocols</a>.
</aside>

### HTTP Request

`GET https://${account.namespace}/wsfed/{client-id}`

### Query Parameters

| Parameter        | Type       | Description |
|:-----------------|:-----------|:------------|
| `client-id`      | string     | the `client-id` of your app (optional) |
| `wtrealm`        | string     | can be used in place of `client-id` |
| `whr `           |            | the name of the connection (to skip the login page, optional) |
| wctx             |            | your application's state (optional) |
| wreply           |            | the callback URL (optional) |

<aside class="notice">
All the parameters of the SAML assertion can be modified through <a href='/rules'>rules</a>.
</aside>

### Remarks

* The `wtrealm` parameter must be in one of these formats:
  * `urn:clientID` (e.g. urn:{client-id})
  * If this parameter does not begin with a urn, the `client.clientAliases` array is used for look-up. (This can only be set with the [/api/v2/clients](/api/management/v2#!/Clients/get_clients)` Management API)
* The `whr` parameter is mapped to the connection like this: `urn:{connection_name}`. For example, `urn:google-oauth2` indicates login with Google. If there is no `whr` parameter included, the user will be directed to the [Auth0 Login Page](/login_page).

## FederationMetadata

```http
http
```

```shell
GET https://${account.namespace}/wsfed/{client-id}/FederationMetadata/2007-06/FederationMetadata.xml
```

```javascript
javascript
```

This endpoint returns the WS-Federation metadata.

### HTTP Request

`GET https://${account.namespace}/wsfed/{client-id}/FederationMetadata/2007-06/FederationMetadata.xml`