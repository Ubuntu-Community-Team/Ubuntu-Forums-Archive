---
title: "duplicate column name 'default authority' - mythconverg database upgrade failed"
date: 2009-12-26
forum: Mythbuntu
---

### Post by ubnewbie2 on 2009-12-26
I have clean installed 9.10 and dropped the mythconverg database, then created a new one, then restored a backup from my old mythbuntu install.  When I start mythtv-setup, it offers to upgrade the database, but fails.

The log shows a duplicate column error...



```
2009-12-27 13:09:42.838 Upgrading.
2009-12-27 13:09:42.880 Newest MythTV Schema Version : 1244
2009-12-27 13:09:42.925 Upgrading to MythTV schema version 1231
2009-12-27 13:09:43.023 DB Error (Performing database upgrade): 
Query was: ALTER TABLE dtv_multiplex ADD COLUMN    default_authority varchar(32) CHARACTER SET utf8 NOT NULL default ''; 
Error was: Driver error was [2/1060]:
QMYSQL3: Unable to execute statement
Database error was:
Duplicate column name 'default_authority'
 
new version: 1231
2009-12-27 13:09:43.072 Database Schema upgrade FAILED, unlocking.
2009-12-27 13:09:43.114 Couldn't upgrade database to new schema
2009-12-27 13:09:43.256 mythbackend version: branches/release-0-22-fixes [22594] www.mythtv.org
2009-12-27 13:09:43.323 Using runtime prefix = /usr
2009-12-27 13:09:43.364 Using configuration directory = /home/mythtv/.mythtv
2009-12-27 13:09:43.406 Empty LocalHostName.
2009-12-27 13:09:43.448 Using localhost value of mythtv
2009-12-27 13:09:43.495 New DB connection, total: 1
2009-12-27 13:09:43.534 Connected to database 'mythconverg' at host: localhost
2009-12-27 13:09:43.573 Closing DB connection named 'DBManager0'
2009-12-27 13:09:43.615 Connected to database 'mythconverg' at host: localhost

```

---

### Post by ubnewbie2 on 2009-12-26
Found a cure.  Seems that it was the backend starting up that altered the table and added the column.  By killing the backend, then dropping and restoring the old databse, then running mythtv-setup, I was able to successfully upgrade mythconverg.

---

### Post by JoseRijo on 2009-12-30
Wow.  I had a heck of a time upgrading from 9.04 to 9.10.  I had to manually run sql commands to get past all of the upgrade errors (this was the first one).

I was finally able to get through it by running /usr/bin/mythbackend directly in the foreground (instead of mythtv-setup).  Then I was able to see and correct all of the errors.

How hard would it be to simply check if the tables are correct and then continue with the upgrade instead of immediately failing?

---

### Post by ubnewbie2 on 2009-12-30
> **JoseRijo said:**
> Wow.  I had a heck of a time upgrading from 9.04 to 9.10.  I had to manually run sql commands to get past all of the upgrade errors (this was the first one).

I was finally able to get through it by running /usr/bin/mythbackend directly in the foreground (instead of mythtv-setup).  Then I was able to see and correct all of the errors.

How hard would it be to simply check if the tables are correct and then continue with the upgrade instead of immediately failing?

Well, I have a problem with a process such as the backend modifying the database outside of any proper upgrade procedure.  To my mind, a program the uses the database should report problems, not modify the database silently like this behind the scenes.  The obvious reason is the problems it causes such as the subject of this thread.

---

### Post by ubnewbie2 on 2009-12-30
Oh and, instead of manually running sql to fix the problems, I find the mySQL GUI to be of great help.  A nice utility!

---

