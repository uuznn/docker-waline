# Quick reference

- Maintained by: [uuznn](https://github.com/uuznn/docker-waline) (not the [Waline Team](https://github.com/lizheming/waline))
- Where to get help: [Documentation](https://waline.js.org/), [Telegram](https://t.me/uuznn), [Discussions](https://github.com/lizheming/waline/discussions)

# Supported tags and respective `Dockerfile` links

- [`latest`](https://github.com/uuznn/docker-waline/blob/main/0/debian/Dockerfile)
- [`alpine`](https://github.com/uuznn/docker-waline/blob/main/0/alpine/Dockerfile)

# Quick reference (cont.)

- Where to file issues: https://github.com/uuznn/docker-waline
- Supported architectures: `amd64`, `arm64`

# Waline

A simple comment system with backend support fork from [Valine](https://valine.js.org/).

> [waline.js.org](https://waline.js.org/)

# How to use this image

This will start a Waline instance listening on the default Ghost port of `8360`.

```bash
docker pull uuznn/waline:latest
docker run -d --name waline -p 8360:8360 uuznn/waline:latest
```

NOTICE: This will not preserve any data.

## ... via [docker stack deploy](https://docs.docker.com/engine/reference/commandline/stack_deploy/) or [docker-compose](https://github.com/docker/compose)

Example `docker-compose.yml` for `waline`:

```yml
# docker-compose.yml
version: "3"

services:
  waline:
    container_name: waline
    image: uuznn/waline:latest
    restart: always
    ports:
      - 127.0.0.1:8360:8360
    volumes:
      - ${PWD}/data:/app/data
    environment:
      TZ: "Asia/Shanghai"
      SQLITE_PATH: "/app/data"
      JWT_TOKEN: "Your token"
      SITE_NAME: "Your site name"
      SITE_URL: "https://example.com"
      SECURE_DOMAINS: "example.com"
      AUTHOR_EMAIL: "mail@example.com"
```

### SQLite

Before use SQLite as storage, you should download [waline.sqlite](https://github.com/lizheming/waline/blob/master/assets/waline.sqlite) (opens new window)to your server. Then set environment variables in project. See https://waline.js.org/en/server/databases.html#sqlite

# Build status

![Release](https://github.com/uuznn/docker-waline/workflows/docker-release/badge.svg?branch=main)
