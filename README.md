# Essential Docker Commands

## Filesystem
* Copy File from HOST to CONTAINER

```
docker cp foo.txt mycontainer:/foo.txt
```

* Copy File from CONTAINER to HOST

```
docker cp mycontainer:/foo.txt foo.txt
```

* Set PWD as volume

```
docker run —rm -it -v ${PWD}:<directory path> <image name>
``` 

## PostgreSQL & PgAdmin
* Start PostgreSQL

```
docker run -d --name my_postgres -v <volume name>:/var/lib/postgresql/data -p 54320:5432 postgres
```

* Terminal

```
docker exec -it my_postgres psql -U <dbname>

* default dbname - postgres
``` 

* Start PgAdmin (http)

```
docker run -p 80:80 \
    -e 'PGADMIN_DEFAULT_EMAIL=yesaswi@gmail.com' \
    -e 'PGADMIN_DEFAULT_PASSWORD=password' \
    -e 'PGADMIN_CONFIG_ENHANCED_COOKIE_PROTECTION=True' \
    -e 'PGADMIN_CONFIG_LOGIN_BANNER="Authorised users only!"' \
    -e 'PGADMIN_CONFIG_CONSOLE_LOG_LEVEL=10' \
    -d dpage/pgadmin4
```

* Start PgAdmin (https)

```
docker run -p 443:443 \
    -v /private/var/lib/pgadmin:/var/lib/pgadmin \
    -v /path/to/certificate.cert:/certs/server.cert \
    -v /path/to/certificate.key:/certs/server.key \
    -v /tmp/servers.json:/pgadmin4/servers.json \
    -e 'PGADMIN_DEFAULT_EMAIL=yesaswi' \
    -e 'PGADMIN_DEFAULT_PASSWORD=password' \
    -e 'PGADMIN_ENABLE_TLS=True' \
    -d dpage/pgadmin4
```


## MongoDB

* Start MongoDB

```
docker run -d --rm -v <volume name>:/data/db -p 27017-27019:27017-27019 --name mongodb mongo
```

* Start Mongo Express

```
docker run -it -d --rm -p 8081:8081 --link mongodb:mongo mongo-express
``` 
