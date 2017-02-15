### Module Description
This module handles `push_notification` hook generated by `mod_pubsub` with active `push` node.
Each `push_notification` hook is converted as `REST` API call to [MongoosePush](https://github
.com/esl/MongoosePush) service. All `publish-options` that are added to the hook are directly
passed to `MongoosePush`.

#### Prerequisites

This module uses a connection pool created by mongoose_http_client. It must be defined
in `http_connections` setting.

### Options

* **pool_name** (atom, required) - name of the pool to use (as defined in http_connections)
* **api_version** (string, default: `v1`) - REST API version to be used. Currently only `v1` is
supported

### Example configuration

```Erlang
{http_connections, [{mongoose_push_http,
    [{server, "https:localhost:8443"}]
}]}.

{mod_push_service_mongoose_push, [
        {pool_name, mongoose_push_http}
        {api_version, "v1"}
]}.
```