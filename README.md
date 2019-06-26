# Para iniciar o container do Zabbix Appliance:

```
 docker run --name zabbix-appliance -t \
      -p 10051:10051 \
      -p 80:80 \
      -d zabbix/zabbix-appliance:latest
```

Usuário: Admin
Senha: zabbix

# Para iniciar o container do nginx:

```
docker run --name nginx-meetup -p 8080:80 \
      -v /meetup-zabbix/nginx-conf/default.conf:/etc/nginx/conf.d/default.conf:ro \
      -d nginx
```

# Configurar Monitoramento via Scripts e Zabbix Agent:
Segue repositório com alguns scripts/templates para monitoramento por scripts:
https://github.com/jizhang/zabbix-templates

# Configurar Monitoramento via HTTP Agent:
Utilize o Template `template_nginx.yml` para importar o monitoramento para dentro do Zabbix Server

Altere a Macro: `{$HOST.NGINX}` apontando para a URL do seu servidor nginx

# Gerar volume de monitoramento no NGINX

`ab -n 100000 -c 10 http://127.0.0.1:8080/index.html`


# Configurar Monitoramento da API Weather

Utilize o template `template_weather-meetup.yml` para importar o monitoramento para dentro do Zabbix Server

Altere a Macro `{$OPENWEATHER.APPID}` apontando para seu Token

Altere a Macro `{$CITY.NAME}` para altererar a cidade.
