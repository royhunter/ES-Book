curl -X GET http://127.0.0.1:9200/

# Cluster Health
curl -X GET http://127.0.0.1:9200/_cat/health?v

# List all indices
curl -X GET http://127.0.0.1:9200/_cat/indices?v

# Create an Index
#Index name: customer
curl -X PUT http://127.0.0.1:9200/customer?pretty
curl -X GET http://127.0.0.1:9200/_cat/indices?v

# Index and Query a Document
curl -d '{"name": "John Doe"}' -H "Content-Type: application/json" -X PUT http://127.0.0.1:9200/customer/_doc/1?pretty
curl -X GET http://127.0.0.1:9200/customer/_doc/1?pretty

# Delete an Index
curl -X DELETE http://127.0.0.1:9200/customer?pretty
curl -X GET http://127.0.0.1:9200/_cat/indices?v

# Indexing/Replacing Documents
curl -d '{"name": "John Doe"}' -H "Content-Type: application/json" -X PUT http://127.0.0.1:9200/customer/_doc/1?pretty
curl -d '{"name": "Jane Doe"}' -H "Content-Type: application/json" -X PUT http://127.0.0.1:9200/customer/_doc/1?pretty
# Random ID
curl -d '{"name": "Jane Doe"}' -H "Content-Type: application/json" -X POST http://127.0.0.1:9200/customer/_doc?pretty

# Updating Documents
curl -d '{"name": "John Doe"}' -H "Content-Type: application/json" -X PUT http://127.0.0.1:9200/customer/_doc/1?pretty
curl -d '{"name": "John Doe", "age":20}' -H "Content-Type: application/json" -X PUT http://127.0.0.1:9200/customer/_doc/1?pretty
curl -d '{"script" : "ctx._source.age += 5"}' -H "Content-Type: application/json" -X POST http://127.0.0.1:9200/customer/_doc/1/_update?pretty

# Deleting Documents
curl -X DELETE http://127.0.0.1:9200/customer/_doc/2?pretty
