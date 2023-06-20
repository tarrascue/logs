# logs

### Часть1: Journald

На LOG настроен центральный сервер логов на основе Journald: systemd-journal-gateway & systemd-journal-remote

На стороне WEB настроен systemd-journal-uload

Как результат на LOG прилетают все логи с WEB в директорию /var/log/journal/remote/

Также сюда прилетают все логи nginx

Для проcмтра логов выполните в консоли команду:

```
    journalctl -D /var/log/journal/remote --follow
```
<img width="683" alt="journalctl" src="https://github.com/tarrascue/logs/assets/117171128/355d388d-98c0-41a4-aa73-1ecd51d92e42">

### Часть2: Auditd

На WEB настроена отправка сообщений аудита, на LOG прием этих событий и изменения конфиг файлов nginx

Для проcмтра сообщений аудита необходимо:

На WEB

Внести изменение в конфиг nginx

```
    vi /etc/nginx/nginx.conf
```

На LOG выполнить команду:

```
    ausearch -k nginx
```
<img width="911" alt="Auditd" src="https://github.com/tarrascue/logs/assets/117171128/8fc8141f-2da8-452e-8c05-223f55b1881f">
