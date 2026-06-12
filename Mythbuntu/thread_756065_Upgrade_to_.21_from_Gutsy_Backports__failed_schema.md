---
title: "Upgrade to .21 from Gutsy Backports / failed schema upgrade"
date: 2008-04-15
forum: Mythbuntu
---

### Post by sceo on 2008-04-15
I installed Mythbuntu 7.10 recently.  Overnight it found new upgrades (like to Myth .21 for example, which I wanted anyway).  I just did the upgrade from gutsy backports, and now when I try to run mythbackend, I have a failure when doing the DB schema upgrade.  

Same as here:
[http://www.gossamer-threads.com/lists/mythtv/users/322368](http://www.gossamer-threads.com/lists/mythtv/users/322368) 
...which was seemingly never resolved.

The output of running mythbackend is...
```

Shall I upgrade this database? [yes]  
2008-04-15 13:36:20.587 Newest Schema Version : 1214
2008-04-15 13:36:20.592 Upgrading to schema version 1210
2008-04-15 13:36:20.593 DB Error (Performing database upgrade): 
Query was: ALTER TABLE program ADD audioprop     tinyint(3) unsigned NOT NULL;  
Error was: Driver error was [2/1060]:
QMYSQL3: Unable to execute query
Database error was:
Duplicate column name 'audioprop'
 
new version: 1210
2008-04-15 13:36:20.594 Database Schema upgrade FAILED, unlocking.
2008-04-15 13:36:20.594 Couldn't upgrade database to new schema

```

I should add that I tried restoring the database from the backup by doing a "mysql -u root < thebackupfile.sql" and trying to run mythbackend again.  Same error.  (This was because of the thread at [http://www.mythtv.org/pipermail/mythtv-users/2008-March/214830.html](http://www.mythtv.org/pipermail/mythtv-users/2008-March/214830.html)).  Did I do the restore incorrectly or is there really something wrong with the upgrade script?

Ergh, edit again.  I hosed myself.  I restored the last backup, which already had the corrupted schema.  I should've restored the FIRST backup that it ever made... except, of course, I deleted that one with 'rm.'  So now I'm stuck re-installing anyway, unless there's a "bare" 1209-schema .sql file floating around out there somewhere?

---

### Post by ian dobson on 2008-04-15
Hi,

Why not just delete the audioprop  field from the program table then retry the "update" again.

Not a nice solution, but it might work.

Regards
Ian Dobson

---

### Post by sceo on 2008-04-15
Yeah I only didn't because in the threads I pointed to, the guy indicated that he tried it and it didn't work.  I bit the bullet and re-installed.

---

