---
title: "Help... totally tangled up in install"
date: 2008-01-28
forum: Mythbuntu
---

### Post by OisinT on 2008-01-28
Ok, so I've tried pretty much everything listed here ([https://help.ubuntu.com/community/MythTV/Install/Troubleshooting](https://help.ubuntu.com/community/MythTV/Install/Troubleshooting))
and I followed the instructions totally on how to install, but no matter what I do I only get this screen:
[IMG]https://help.ubuntu.com/community/MythTV/Install/Gutsy/Frontend?action=AttachFile&do=get&target=FE_2.png[/IMG]

I enter what I believe to be the correct info... and nothing seems to work.

Please help!

---

### Post by OisinT on 2008-01-28
not sure if this info will help:

```
oisint@OisinT1:~$ mysql -u root mysql
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

```

---

### Post by OisinT on 2008-01-28
```
SELECT NULL;
No error type from QSqlError?  Strange...
2008-01-29 04:43:54.028 Database not open while trying to load setting: GuiResolution
2008-01-29 04:43:54.029 Unable to connect to database!
2008-01-29 04:43:54.029 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-01-29 04:43:54.088 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-01-29 04:43:54.144 Database not open while trying to load setting: GuiWidth
2008-01-29 04:43:54.146 Unable to connect to database!
2008-01-29 04:43:54.146 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-01-29 04:43:54.200 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-01-29 04:43:54.256 Database not open while trying to load setting: GuiHeight
2008-01-29 04:43:54.267 Unable to connect to database!
2008-01-29 04:43:54.267 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-01-29 04:43:54.325 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-01-29 04:43:54.380 Database not open while trying to load setting: MenuTheme
2008-01-29 04:43:54.381 Unable to connect to database!
2008-01-29 04:43:54.382 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-01-29 04:43:54.444 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-01-29 04:43:54.500 Database not open while trying to load setting: QtFontBig
2008-01-29 04:43:54.501 Unable to connect to database!
2008-01-29 04:43:54.501 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-01-29 04:43:54.557 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-01-29 04:43:54.612 Database not open while trying to load setting: QtFontMedium
2008-01-29 04:43:54.613 Unable to connect to database!
2008-01-29 04:43:54.613 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-01-29 04:43:54.669 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-01-29 04:43:54.724 Database not open while trying to load setting: QtFontSmall
2008-01-29 04:43:54.746 Unable to connect to database!
2008-01-29 04:43:54.746 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-01-29 04:43:54.801 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-01-29 04:43:54.856 Database not open while trying to load setting: ThemePainter
2008-01-29 04:43:54.857 Using the Qt painter
2008-01-29 04:43:54.858 Unable to connect to database!
2008-01-29 04:43:54.858 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-01-29 04:43:54.913 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-01-29 04:43:54.968 Database not open while trying to load setting: HideMouseCursor
2008-01-29 04:43:54.969 Unable to connect to database!
2008-01-29 04:43:54.969 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-01-29 04:43:55.025 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-01-29 04:43:55.081 Database not open while trying to load setting: RunFrontendInWindow
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2008-01-29 04:43:55.596 Joystick disabled.
2008-01-29 04:43:55.598 Unable to connect to database!
2008-01-29 04:43:55.599 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-01-29 04:43:55.651 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-01-29 04:43:55.704 Unable to connect to database!
2008-01-29 04:43:55.704 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-01-29 04:43:55.759 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-01-29 04:43:55.812 Unable to connect to database!
2008-01-29 04:43:55.812 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-01-29 04:43:55.867 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-01-29 04:43:55.920 Unable to connect to database!
2008-01-29 04:43:55.920 Driver error was [1/1045]:

```

---

