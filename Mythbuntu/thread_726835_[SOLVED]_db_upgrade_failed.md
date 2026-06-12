---
title: "[SOLVED] db upgrade failed"
date: 2008-03-17
forum: Mythbuntu
---

### Post by jleiss on 2008-03-17
I recently applied all updates, which included the mythtv .21 upgrades. After doing so my backend will not longer start, I looked through the logs, and found that the db needed to be upgraded, and ran mythtv-setup to do just that, but it comes up with the following error.

2008-03-17 01:58:01.146 Newest Schema Version : 1214
2008-03-17 01:58:01.148 Upgrading to schema version 1178
2008-03-17 01:58:01.376 DB Error (Performing database upgrade): 
Query was: ALTER TABLE program           DROP INDEX programid; 
Error was: Driver error was [2/1091]:
QMYSQL3: Unable to execute query
Database error was:
Can't DROP 'programid'; check that column/key exists
 
new version: 1178
2008-03-17 01:58:01.381 Database Schema upgrade FAILED, unlocking.
2008-03-17 01:58:01.381 Couldn't upgrade database to new schema

Any ideas whats going on and what I need to do to fix it?

---

### Post by nasha on 2008-03-17
```
perl /usr/share/doc/mythtv-backend/contrib/optimize_mythdb.pl
```
Try that, might fix your db issues

---

### Post by jleiss on 2008-03-17
database is smaller, but still will not upgrade, fails with same error.

---

### Post by uopjohnson on 2008-03-17
I hate to tell you this, but I think you are in pretty bad shape here.  I would guess that something got interrupted in the process of updating your DB and the version wasn't updated.  I think this is resulting in the update script trying to re-do changes that have already been made.  
It is possible that it can be fixed manually, but you would probably save a lot of time by either restoring your original DB from a backup or rebuilding a blank DB and starting over.  
If you want to try and fix in manually then I would search the mythtv.org site and google to see if anyone has done this before.  You may also try logging into mysql and adding back in the key that it is searching for.  At the terminal do:  
```

mysql -u mythtv -p mythconverg;
mysql> ALTER TABLE program ADD INDEX programid;

```
If you don't know the password for mysql you can do:
```

cat /etc/mythtv/mysql.txt

```
and look for the PASS line.

---

### Post by jleiss on 2008-03-17
I was able to resolve it myself based upon some information i found on google about another similar type issue. I installed phpmyadmin, and then removed the programid field from the db, and then later I had to remove storagegroups due to a duplicate issue when trying to add, after doing both of those I was able to get those a successful upgrade, and get the backend back up.

---

