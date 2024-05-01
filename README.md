# docker-taxi-data-pipeline
using docker compose, postgress and other tools to create a data engineering pipeline.

# download data:

* $ mkdir data
* $ wget -P ./data https://github.com/DataTalksClub/nyc-tlc-data/releases/download/yellow/yellow_tripdata_2019-01.csv.gz
* $ gzip -d data/yellow_tripdata_2019-01.csv.gz


### DOCKER Commands used in experimentation. Ultimately the docker compose file can be used instead

## POSTGRESS DATABASE
# we can run the database first using docker for experimentation. Ultimately we will use the docker compose file
docker network create pg-network
docker run -it \
  -e POSTGRES_USER="root" \
  -e POSTGRES_PASSWORD="root" \
  -e POSTGRES_DB="ny_taxi" \
  -v $(pwd)/db/ny_taxi_postgres_data:/var/lib/postgresql/data \
  -p 5432:5432 \
  --network=pg-network \
  --name pg-database \
  postgres:13

  