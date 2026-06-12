---
title: "mysql.h error in Ubuntu (zabbix install)"
date: 2006-07-05
forum: Networking &amp; Wireless
---

### Post by khilari on 2006-07-05
I get this error when i run the configure command for zabbix installation.

configure: error: Invalid MySQL directory - unable to find mysql.h

The command i am running from the root of zabbix was
#     ./configure --enable-server --with-mysql --with-net-snmp

I am following the instructions from
[http://www.zabbix.com/manual/v1.1/install_server.php](http://www.zabbix.com/manual/v1.1/install_server.php)

Please advise how i can overcome that error. Thanks,

---

### Post by khilari on 2006-07-06
I had to install the development pack

apt-get install libmysqlclient14-dev

Thanks,

---

