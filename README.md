Example:

```yaml
td:
  image: takebayashi/td-agent
  ports:
    - "24224:24224"
  environment:
    - TD_API_KEY=XXXXXXXXXX
web:
  image: httpd
  ports:
    - "80:80"
  log_driver: fluentd
  log_opt:
    fluentd-address: localhost:24224
    fluentd-tag: docker.{{.Name}}
  links:
    - td
```
