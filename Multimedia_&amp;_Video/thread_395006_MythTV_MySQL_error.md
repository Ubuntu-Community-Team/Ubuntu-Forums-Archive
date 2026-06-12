---
title: "MythTV MySQL error"
date: 2007-03-27
forum: Multimedia &amp; Video
---

### Post by nathanhillinbl on 2007-03-27
I installed mythtv, and when i tried to run it, i got this:

2007-03-27 16:25:40.748 Database not open while trying to load setting: GuiOffsetX
2007-03-27 16:25:40.749 Unable to connect to database!
2007-03-27 16:25:40.749 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on 'nate-desktop' (111)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-03-27 16:25:40.800 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-03-27 16:25:40.852 Database not open while trying to load setting: GuiOffsetY
2007-03-27 16:25:40.853 Unable to connect to database!
2007-03-27 16:25:40.853 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on 'nate-desktop' (111)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open



***_(This continued for about 20 seconds, then gave me this:_***




No error type from QSqlError?  Strange...
2007-03-27 16:25:50.829 Failed to init MythContext, exiting.
nate@nate-desktop:~$


I thought this would be fairly easy to set up, it seems that it can't connnect to the mysql server, which it installed when i installed mythtv through aptitude.

Any Help is always greatly appreciated,
Nate Hill

---

### Post by majoridiot on 2007-03-28
add your main user to the mythtv group:

```
$ sudo usermod -a -G mythtv USERNAME
```

LOG OUT

and log back in.  then:

```
$ cp /etc/mythtv/mysql.txt ~/.mythtv/ 
```

and run mythtv-setup.

install guides here: [https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

---

