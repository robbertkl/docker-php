# robbertkl/php

[![](https://badge.imagelayers.io/robbertkl/php:latest.svg)](https://imagelayers.io/?images=robbertkl/php:latest)

Docker container running PHP-FPM with NGINX:

* Meant to be run behind a reverse proxy doing SSL and/or virtual hosts (for example the awesome [jwilder/nginx-proxy](https://github.com/jwilder/nginx-proxy))
* Either run it directly with a mounted volume or extend it into an image with your code included
* Logs access to `stdout`, errors to `stderr` (so it shows up in `docker logs`)
* Contains `composer` to install your app dependencies
* Exposes port 80 (HTTP)
* By default, serves a `phpinfo()` page

## Usage

Either run it directly:

```
docker run -d -v <path-to-code>:/var/www -p 80:80 robbertkl/php
```

Or extend it:

```
FROM robbertkl/php

COPY <my code> .
RUN composer install --no-dev

...
```

## Environment variables

You can tweak the behaviour by setting the following environment variables:

* `DOCUMENT_ROOT` (default `/var/www`)
* `PHP_MEMORY_LIMIT` (default 128M)
* `PHP_ERROR_REPORTING` (default E_ALL & ~E_DEPRECATED & ~E_STRICT)
* `TZ` (default unset, which means UTC)

## Authors

* Robbert Klarenbeek, <robbertkl@renbeek.nl>

## License

This repo is published under the [MIT License](http://www.opensource.org/licenses/mit-license.php).
