---
title: "myth sql database from secondary backend problem"
date: 2007-11-25
forum: Multimedia &amp; Video
---

### Post by frank10 on 2007-11-25
If I manually run the backend daemon, I connect fine.  If I use the mythbackend restart in init.d, I get the following error message in the backend log


2007-11-25 07:58:30.274 Using runtime prefix = /usr
2007-11-25 07:58:30.302 New DB connection, total: 1
2007-11-25 07:58:30.323 Unable to connect to database!
2007-11-25 07:58:30.324 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-25 07:58:30.381 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-25 07:58:30.436 Failed to init MythContext, exiting.

---

### Post by superm1 on 2007-11-26
rm /home/mythtv/.mythtv -rf
rm ~/.mythtv -rf

and try again.

---

