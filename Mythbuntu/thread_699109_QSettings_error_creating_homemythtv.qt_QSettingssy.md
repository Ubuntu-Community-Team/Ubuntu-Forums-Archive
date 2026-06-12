---
title: "QSettings: error creating /home/mythtv/.qt QSettings::sync: filename is null/empty"
date: 2008-02-17
forum: Mythbuntu
---

### Post by DuncanG on 2008-02-17
I get the following error in my  /var/log/mythtv/mythbackend.log on boot. Starting at the top, it seems to be a QSettings error.

I have installed/re-installed mythtv several times, reset passwords, reconfigured etc. I have the correct mysql password in all three mysql.txt files.
```
2008-02-17 15:07:53.543 Using runtime prefix = /usr
QSettings: error creating /home/mythtv/.qt
QSettings::sync: filename is null/empty
2008-02-17 15:07:53.870 New DB connection, total: 1
2008-02-17 15:07:53.914 Unable to connect to database!
2008-02-17 15:07:53.923 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-02-17 15:07:53.993 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-02-17 15:07:54.068 Failed to init MythContext, exiting.
```
I'd be grateful for some help, three weeks into my install !

Myth 0.20.2 on Ubuntu 7.10, GA-MA69GM-S2H, AMD BE-2350, Samsung 1TB, AVerTV Hybrid+FM PCI A16D (not working)

---

