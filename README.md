# Docker Compose healthcheck examples

Docker Compose healthcheck examples for different services.

## Example use on local development

On local development it's recommend use Docker Compose version 2.1 or newer, because it allow use [condition feature](https://docs.docker.com/compose/compose-file/compose-file-v2/#depends_on). This make sure the web container doesn't start before example mysql container is healthy:

```yml
version: '2.4'
services:
  web:
    image: apache
    depends_on:
      mysql:
        condition: service_healthy
  mysql:
    image: mysql
```