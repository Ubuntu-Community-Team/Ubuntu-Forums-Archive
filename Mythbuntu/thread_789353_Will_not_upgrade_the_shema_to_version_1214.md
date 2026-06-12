---
title: "Will not upgrade the shema to version 1214"
date: 2008-05-10
forum: Mythbuntu
---

### Post by Rhiadon on 2008-05-10
I've tried everything that I can find online to fix this issue. I've tried repairing and optimizing with no dice.

I of course want to be able to keep all of my old recordings so I did a backup of the database before attempting to upgrade to Mythbuntu 8.04. 

The error I get is as follows:

Shall I upgrade this database? [yes]  yes
2008-05-10 13:43:31.137 Newest Schema Version : 1214
2008-05-10 13:43:31.142 Upgrading to schema version 1171
2008-05-10 13:43:31.148 DB Error (Performing database upgrade):
Query was: INSERT storagegroup (groupname, hostname, dirname)     SELECT DISTINCT 'Default', hostname, data     FROM settings     WHERE value = 'RecordFilePrefix'         AND hostname IS NOT NULL         AND hostname <> '';
Error was: Driver error was [2/1062]:
QMYSQL3: Unable to execute query
Database error was:
Duplicate entry 'Default-myth-backend-/myth/recordings' for key 2

new version: 1171
2008-05-10 13:43:31.149 Database Schema upgrade FAILED, unlocking.
2008-05-10 13:43:31.150 Couldn't upgrade database to new schema

I know nearly nothing about sql so any help provided will need a lot of hand holding. :)

It seems that lots of people are having similar issues but more luck with other techniques of fixing it. What else can I do here?

Thanks,

Kris

---

### Post by Rhiadon on 2008-05-10
Apparently there is some hinky-ness about the way the schema upgrades work. I don't know.

I did figure out how to get past the issue however. Thanks to a post by 'mcsmith' I tried just truncate storagegroup.

mysql -u mythtv -p mythconverg
truncate storagegroup;

It got much farther that time. It then stopped around version 1200 telling me that some upnp table already existed. I just dropped that table and tried again. It got all the way through.

Now I just hope it all works.

---

