---
title: network_http_request
parent: Actions
grand_parent: Building Your Quest
nav_order: 11
---

# network_http_request

Category: Network
Description: Perform http request
Type: Action

### Description

**Type**: action

Perform http request using `axios`. 

→ See the [request config API]

## Params

- **method:** Request method to be used when making the request. Defaults to `GET`
- **url**: Full server url to be used for the request. URL must be specified
- **params**: URL parameters to be sent with the request
- **headers:** custom headers to be sent

## Outputs

In case of success, the action will set the returned `data` on the outputs. In case of an error, the action will set the returned `error`.

These can be accessed using:

`${outputs.<action_name>.data}`

`${outputs.<action_name>.error}`

## Usage Example

```yaml
do:
- actionId: network_http_request
  name: call_backend
  params:
    url: "${user.K8sBackendUrl}/api/items?limit=10"
if:
  conditions:
  - conditionId: is_truthy
    params:
      value: ${outputs.call_backend.data?.items}

  then:
    ...
```

In this example we make a request to a user's backend to get items. Then we verify that response data includes `items`, which means the request was successful.

## Relevant Triggers

All triggers

[request config API]: https://axios-http.com/docs/req_config