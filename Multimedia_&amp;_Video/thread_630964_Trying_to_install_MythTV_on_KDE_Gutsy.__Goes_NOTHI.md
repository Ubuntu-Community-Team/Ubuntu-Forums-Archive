---
title: "Trying to install MythTV on KDE Gutsy.  Goes NOTHING like howtos I've tried."
date: 2007-12-03
forum: Multimedia &amp; Video
---

### Post by Mysticle31 on 2007-12-03
I've been trying to install MythTV. 

I've tried this.

[https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop)

However no mythbuntu setup to be found.  How do I run it manually?  Also I could not install by clicking the link either.

I've tried this

[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

but it goes nothing like this and does not ask about remote connections to backends.  I just get the unable to connect to database screen.  When all my passwords and information are correct as to what's in my mysql.txt file.

I've tried to Festy install guide on help.ubuntu with the same results.

What gives?  So far none of the howtos seem to apply to me..

---

### Post by Mysticle31 on 2007-12-03
2007-12-03 19:55:25.281 Using runtime prefix = /usr
2007-12-03 19:55:25.296 New DB connection, total: 1
2007-12-03 19:55:25.301 Unable to connect to database!
2007-12-03 19:55:25.302 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-12-03 19:55:25.353 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-12-03 19:55:25.403 Failed to init MythContext, exiting.

---

