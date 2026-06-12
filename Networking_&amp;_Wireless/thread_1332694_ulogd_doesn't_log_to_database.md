---
title: "ulogd doesn't log to database"
date: 2009-11-20
forum: Networking &amp; Wireless
---

### Post by Salivan on 2009-11-20
Hello
1. I have Ubuntu 9.04
2. I install via apt-get: ulogd, ulogd-mysql, mysql-server.
3. I configured /etc/ulog/conf:

```

[global]
nlgroup=3
logfile="/var/log/ulog/ulogd.log"
loglevel=5
rmem=131071
bufsize=150000
plugin="/usr/lib/ulogd/ulogd_MYSQL.so"

[LOGEMU]
#file="/var/log/ulog/syslogemu.log"
#sync=1

[OPRINT]
file="/var/log/ulog/pktlog.log"

[MYSQL]
table="ulog"
pass="1234"
user="root"
db="ulog"
host="localhost"

```4. I create at database ulog table like in /usr/share/doc/ulogd-mysql/mysql.table file
5. Ulogd log correctly to file syslogemu.log
6. [PROBLEM] It cannot log to mysql. I do not see any errors.

What  I do wrong?

King regards
Salivan

---

### Post by bignellrp on 2009-12-11
> **Salivan said:**
> Hello
1. I have Ubuntu 9.04
2. I install via apt-get: ulogd, ulogd-mysql, mysql-server.
3. I configured /etc/ulog/conf:

```

[global]
nlgroup=3
logfile="/var/log/ulog/ulogd.log"
loglevel=5
rmem=131071
bufsize=150000
plugin="/usr/lib/ulogd/ulogd_MYSQL.so"

[LOGEMU]
#file="/var/log/ulog/syslogemu.log"
#sync=1

[OPRINT]
file="/var/log/ulog/pktlog.log"

[MYSQL]
table="ulog"
pass="1234"
user="root"
db="ulog"
host="localhost"

```4. I create at database ulog table like in /usr/share/doc/ulogd-mysql/mysql.table file
5. Ulogd log correctly to file syslogemu.log
6. [PROBLEM] It cannot log to mysql. I do not see any errors.

What  I do wrong?

King regards
Salivan


Im having the same problem.  Did you fix this?

---

