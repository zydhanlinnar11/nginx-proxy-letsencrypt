# nginx-proxy-letsencrypt

Docker compose configuration for production server using [nginx-proxy](https://github.com/nginx-proxy/nginx-proxy) and [Let's Encrypt proxy companion](https://github.com/nginx-proxy/acme-companion).

## Usage

Create a docker network named nginx-proxy-network.

```bash
docker network create --driver bridge nginx-proxy-network
```

Run the service inside nginx-proxy directory.

```bash
docker compose up -d
```

Run your web server container by adding environment variables VIRTUAL_HOST, VIRTUAL_PORT, LETSENCRYPT_HOST, and LETSENCRYPT_EMAIL. This is an example using [laravel-docker-image](https://github.com/zydhanlinnar11/laravel-docker-image).

```bash
docker run -d \
--name your.domain.com \
-v /path/to/your/web/project:/var/www/html \
-e VIRTUAL_HOST=your.domain.com \
-e VIRTUAL_PORT=8080 \
-e LETSENCRYPT_HOST=your.domain.com \
-e LETSENCRYPT_EMAIL=mail@domain.com \
zydhanlinnar11/laravel-docker-image
```

Your CA certificate and SSL certificate will be generated under `certs` directory.

## Reference

- [dptsi/nginx-proxy](https://github.com/dptsi/nginx-proxy)

## License

[GNU GPLv3](https://choosealicense.com/licenses/gpl-3.0/)
