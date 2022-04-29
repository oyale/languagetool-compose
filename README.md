A `docker-compose` setup to run a local instance from language-tool server in a Firefox extension compatible way.

This repo only exists to document fix to the https://github.com/Erikvl87/docker-languagetool/issues/40 issue.

## Getting started

Follow the excellent documentation at https://github.com/Erikvl87/docker-languagetool

### Structure
```
├── docker-compose.yml
├── LICENSE
├── nginx
│   ├── Dockerfile
│   └── nginx.conf
└── README.md
```

### Changes
##### `docker-compose.yml`
- *ngrams* are mounted from `\home\<user>\ngrams`.
- Mapping for `cors` container to port 8081

##### `nginx/Dockerfile`
- NGINX logs are piped to `stdout`

##### `nginx/nginx.conf`
| conf         | new value                 |
| ------------ | ------------------------- |
| `server`     | `languagetool:8010;`      |
| `listen`     | `8081`                    |
| `proxy_pass` | `http://language-tools/;` |
| `upstream`   | `language-tools`          |


### Credits
All credits to [@Erikvl87](https://github.com/Erikvl87) for the [docker-languagetool](https://github.com/Erikvl87/docker-languagetool) image and to [@maximillianfx](https://github.com/maximillianfx) for the [docker-nginx-cors](https://github.com/maximillianfx/docker-nginx-cors) image.  

