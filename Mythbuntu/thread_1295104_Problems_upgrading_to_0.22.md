---
title: "Problems upgrading to 0.22"
date: 2009-10-19
forum: Mythbuntu
---

### Post by orduek on 2009-10-19
Hi,
I tried to upgrade mythtv from 0.21fixes to 0.22 using avenard's repos.
the upgrade yielded many error msgs and further investigation led to the mysql database.
apparently it wasn't able to upgrade the database.
```
mysql  Ver 14.12 Distrib 5.0.67, for debian-linux-gnu (i486) using readline 5.2

Connection id:		264
Current database:	mythconverg
Current user:		mythtv@localhost
SSL:			Not in use
Current pager:		stdout
Using outfile:		''
Using delimiter:	;
Server version:		5.0.67-0ubuntu6 (Ubuntu)
Protocol version:	10
Connection:		Localhost via UNIX socket
Server characterset:	latin1
Db     characterset:	latin1
Client characterset:	latin1
Conn.  characterset:	latin1
UNIX socket:		/var/run/mysqld/mysqld.sock
Uptime:			13 hours 7 min 56 sec

Threads: 5  Questions: 70980  Slow queries: 0  Opens: 2002  Flush tables: 1  Open tables: 64  Queries per second avg: 1.501

```
this is the result of 'status;' | mysql -umythtv -p mythconverg

BTW, this is after I restored the data and downgraded back to 0.21fixes.
before the first (unsuccessful) upgrade the Db characterset was utf8.

what can I do to make the upgrade work?
P.S I'm on mythbuntu 8.10

---

### Post by orduek on 2009-10-20
anyone?

---

