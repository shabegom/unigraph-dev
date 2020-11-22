# unigraph-dev Server API

We use a websocket-based API for our server. To interact with the server, first establish a connection with the local server (default address is `ws://localhost:3000`).

After establishing the connection, you can use the event system of the server, either by sending events to the server or listening to updates (subscribing to events).

To send a event to the server, follow the event syntax such as:

```json
{
    "type": "event",
    "event": "query_by_string_with_vars",
    "query": "query findByName($a: string) {\n        entities(func: eq(name, $a)) {\n          uid\n          name\n          definition @filter(eq(name, \"Owner\")) {\n            name\n          }\n          otherField {\n            notDefined\n          }\n        }\n      }",
    "vars": {
        "$a": "TODO Model"
    },
    "id": 1
}
```

For more information on the various events and subscriptions, check out the documentation below:

## Events

To send an event, use `"type": "event"` and `"event": "<name of the event to send>"`. Here is a list of available events:

- Database operations
    * query_by_string_with_vars `{"query": "<query string>", "vars": {<maps of all vars>}}`
    * set_schema `{"schema": "<a schema string>"}`
    * create_data_by_json
    * drop_data (no parameters needed)
    * drop_all (no parameters needed)
- Administrative events
- Statistics and logging 

For more detailed info regarding each of the events, TODO

## Listening/Subscribing to events

TODO