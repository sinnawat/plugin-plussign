# plugin-plussign

## Installation

From the top of the cloned directory, run:

        javac -d <path>/<to>/<elasticsearch>/plugin -cp <path>/<to>/<elasticsearch>/lib:. io/citrine/pluginplussign/plugin/PlusSignPlugin.java

where `<path>/<to>/<elasticsearch>` is the path to your Elasticsearch installation.

## Running the plugin

1. Start elasticsearch with e.g. bin/elasticsearch
2. If you do not have any indexes, create one using:

        curl -XPUT 'localhost:9200/test'

3. Test the analyzer:

        curl -XGET 'localhost:9200/test/_analyze?analyzer=plus_sign&pretty=true' -d 'This+is++some+text'

You should see the following response from Elasticsearch:

        {
          "tokens" : [ {
            "token" : "this",
            "start_offset" : 0,
            "end_offset" : 0,
            "type" : "word",
            "position" : 1
          }, {
            "token" : "is",
            "start_offset" : 0,
            "end_offset" : 0,
            "type" : "word",
            "position" : 2
          }, {
            "token" : "some",
            "start_offset" : 0,
            "end_offset" : 0,
            "type" : "word",
            "position" : 3
          }, {
            "token" : "text",
            "start_offset" : 0,
            "end_offset" : 0,
            "type" : "word",
            "position" : 4
          } ]
        }

At this point you can use the `plus_sign` analyzer just as you would any of the built-in Elasticsearch analyzers.
