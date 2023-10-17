# PGAdmin & PostgreSQL powered by compose

## Requirements:
- `docker >= 17.12.0+`
- `docker-compose`

## Start
- Clone or download this repository.
- Go inside of directory,  `cd compose-pgadmin`.
- Run this command `docker-compose up -d`.

## Environments
This compose file contains the following environment variables.
- `LOOPBACK` bind the service to the loopback IP address, the default is exposed.
- `POSTGRES_PORT` the default value is `5432`.
- `POSTGRES_DB` the default value is `postgres`.
- `POSTGRES_USER` the default value is `postgres`.
- `POSTGRES_PASSWORD` the default value is `changeme`.
- `PGADMIN_PORT` the default value is `5050`.
- `PGADMIN_DEFAULT_EMAIL` the default value is `pgadmin4@pgadmin.org`.
- `PGADMIN_DEFAULT_PASSWORD` the default value is `admin`.

You can create your own `.env` file within this folder.
```env
LOOPBACK=127.0.0.1
POSTGRES_PORT=5435
POSTGRES_DB=postgres_maintenance_db
POSTGRES_USER=user1
POSTGRES_PASSWORD=user12345
PGADMIN_PORT=5050
PGADMIN_DEFAULT_EMAIL=pgadmin@example.com
PGADMIN_DEFAULT_PASSWORD=admin123
```

## Access to PostgreSQL
- `localhost:5432`.
- **Username:** `postgres` (as a default).
- **Password:** `changeme` (as a default).

## Access to PGAdmin:
- **URL:** `http://127.0.0.1:5050/browser` or `http://localhost:5050`.
- **Username:** `pgadmin4@pgadmin.org` (as a default).
- **Password:** `admin` (as a default).

## Add a new server in PGAdmin
- **Host name/address:** `postgres` or container name `postgres_container`.
- **Maintaince DB:** as `POSTGRES_DB`, by default `postgres`.
- **Port:** `5432`.
- **Username:** as `POSTGRES_USER`, by default `postgres`.
- **Password:** as `POSTGRES_PASSWORD`, by default `changeme`.

## Logging
There are no easy way to configure pgadmin log verbosity and it can be overwhelming at times. It is possible to disable pgadmin logging on the container level.

Add the following to `pgadmin` service in the `docker-compose.yml`:
```yml
logging:
    driver: "none"
```

- *NOTES: see [reference](https://github.com/khezen/compose-postgres/pull/23/files) for more details.*

## Server/Desktop mode
This will run PGAdmin in `Desktop Mode`, meaning you wont need to log in to access the web interface: `PGADMIN_CONFIG_SERVER_MODE: 'False'`.
