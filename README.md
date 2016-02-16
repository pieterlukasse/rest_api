======================================
FLASK App for the CTTV CoreDB REST API
======================================

To test locally

- clone repository
- ```cd flask-rest-api```
- ```pip install -r requirements.txt``` (possiby in a virtualenv)
- ```python manage.py runserver``` runs the server
- ```python manage.py test``` runs the tests

Will run the rest api on: [http://localhost:5000](http://localhost:5000)

Swagger YAML documentation is exposed at  http://localhost:5000/api/docs/swagger.yaml](http://localhost:5000/api/docs/swagger.yaml)

It expects to have an elasticsearch instance on [http://localhost:9200](http://localhost:9200). Alternative configurations are available using the `CTTV_API_CONFIG` environment variable



Run Docker Container
====================

build the container
```bash
docker build -t cttv_rest_api:local .
```

run the container. Please use the correct link for 'elastic', either with the  `--link` or the `--ad-host` option
```bash
run -d -p 8008:80 --name cttv_rest_api --add-host elastic:10.0.2.2 --ulimit nofile=65535:65535 -e "CTTV_API_CONFIG=dockerlink" cttv_rest_api:local
```

Supposing the container runs in `localhost` and espose port `8008`, Swagger UI is available at: [http://localhost:8008/api-docs](http://localhost:8008/api-docs)