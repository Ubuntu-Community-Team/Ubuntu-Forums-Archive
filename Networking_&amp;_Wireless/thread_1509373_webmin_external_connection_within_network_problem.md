---
title: "webmin external connection within network problem"
date: 2010-06-14
forum: Networking &amp; Wireless
---

### Post by maclp on 2010-06-14
hi,

i installed webmin 1.310 on ubuntu 8.04 server edition.
but when i try to connect with a pc in the same network i get 'webpage cannot be found'.

can any of you help me with this?


this is a copy of my webmin/miniserv.conf:

port=10000
addtype_cgi=internal/cgi
realm=Webmin Server
logfile=/var/webmin/miniserv.log
errorlog=/var/webmin/miniserv.error
pidfile=/var/webmin/miniserv.pid
logtime=168
ppath=
ssl=1
env_WEBMIN_CONFIG=/etc/webmin
env_WEBMIN_VAR=/var/webmin
atboot=1
logout=/etc/webmin/logout-flag
listen=10000
denyfile=\.pl$
log=1
blockhost_failures=5
blockhost_time=60
syslog=1
session=1
premodules=WebminCore
userfile=/etc/webmin/miniserv.users
keyfile=/etc/webmin/miniserv.pem
passwd_file=/etc/shadow
passwd_uindex=0
passwd_pindex=1
passwd_cindex=2
passwd_mindex=4
passwd_mode=0
preroot=blue-theme
passdelay=1
sudo=1
root=/home/administrator/webmin-1.310
mimetypes=/home/administrator/webmin-1.310/mime.types
allow=26.10.0.160 to allow=26.10.0.117
allow=26.10.0.160 to allow=0.0.0.0
allow=26.10.0.117

---

### Post by maclp on 2010-06-14
hi,

i installed webmin 1.310 on ubuntu 8.04 server edition.
but when i try to connect with a pc in the same network i get 'webpage cannot be found'.

can any of you help me with this?


this is a copy of my webmin/miniserv.conf:

port=10000
addtype_cgi=internal/cgi
realm=Webmin Server
logfile=/var/webmin/miniserv.log
errorlog=/var/webmin/miniserv.error
pidfile=/var/webmin/miniserv.pid
logtime=168
ppath=
ssl=1
env_WEBMIN_CONFIG=/etc/webmin
env_WEBMIN_VAR=/var/webmin
atboot=1
logout=/etc/webmin/logout-flag
listen=10000
denyfile=\.pl$
log=1
blockhost_failures=5
blockhost_time=60
syslog=1
session=1
premodules=WebminCore
userfile=/etc/webmin/miniserv.users
keyfile=/etc/webmin/miniserv.pem
passwd_file=/etc/shadow
passwd_uindex=0
passwd_pindex=1
passwd_cindex=2
passwd_mindex=4
passwd_mode=0
preroot=blue-theme
passdelay=1
sudo=1
root=/home/administrator/webmin-1.310
mimetypes=/home/administrator/webmin-1.310/mime.types
allow=26.10.0.160 to allow=26.10.0.117
allow=26.10.0.160 to allow=0.0.0.0
allow=26.10.0.117

---

### Post by _Mark_ on 2010-06-14
What url are you using? hostname or ip of server?

try [https://server](https://server) ip address:10000

---

### Post by lisati on 2010-06-15
Threads merged. Please do not create multiple threads on the same question.

---

