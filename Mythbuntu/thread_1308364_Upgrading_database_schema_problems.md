---
title: "Upgrading database schema problems"
date: 2009-10-31
forum: Mythbuntu
---

### Post by amar on 2009-10-31
Hi folks,

I have just done an upgrade from jaunty to karmic. I did a fresh install due to limited hard disk space on root partition and have tried to follow the instructions on the mythtv website [1].

After the upgrade and replacing the database, I get asked to upgrade the database schema by running either 'mythtv-setup' or 'mythbackend' nether of which make a difference. mythbackend gives the following error:

> 2009-10-31 20:28:19.028 Backing up database with script: '/usr/share/mythtv/mythconverg_backup.pl'
2009-10-31 20:28:21.062 Database Backup complete.
2009-10-31 20:28:21.063 Backed up database to file: '/tmp/mythconverg-1230-20091031202819.sql.gz'

Warning: MythTV wants to upgrade your database,
for the TV schema, from 1230 to 1244.

Database Host: localhost
Database Name: mythconverg

If your system becomes unstable, a database backup is located in /tmp/mythconverg-1230-20091031202819.sql.gz


Shall I upgrade this database? [yes]  

There are also other clients using this database. They should be shut down first.
2009-10-31 20:28:42.225 Newest MythTV Schema Version : 1244
2009-10-31 20:28:42.232 Upgrading to MythTV schema version 1231
2009-10-31 20:28:42.315 DB Error (Performing database upgrade): 
Query was: ALTER TABLE dtv_multiplex ADD COLUMN    default_authority varchar(32) CHARACTER SET utf8 NOT NULL default ''; 
Error was: Driver error was [2/1060]:
QMYSQL3: Unable to execute statement
Database error was:
Duplicate column name 'default_authority'
 
new version: 1231
2009-10-31 20:28:42.315 Database Schema upgrade FAILED, unlocking.
2009-10-31 20:28:42.315 Couldn't upgrade database to new schema


Any suggestions?

Thanks in advance
Alistair

[1] [http://mythbuntu.org/Upgrading](http://mythbuntu.org/Upgrading)

---

### Post by ian dobson on 2009-10-31
Hi,

Maybe try editing your dtv_multiplex table and delete the 'default_authority' column. You can use phpMyAdmin (if it's installed) or from the command line using mysqladmin.

Regards
Ian Dobson

---

### Post by uncle hammy on 2009-10-31
This is the same problem I had here [http://ubuntuforums.org/showthread.php?t=1302135](http://ubuntuforums.org/showthread.php?t=1302135) 

The bottom line is, it happens if there was a prior upgrade attempt, without properly dropping the schema and restoring your backup before trying again.  Perhaps a second run through to look at the logs?

If any of the 4 tables that I mention in that link are present after the restoration, drop them...they are new with the upgrade anyways.  Go into the dtv_multiplex table and drop the default_authority column...it's also new with the upgrade. After that, try the upgrade again and see what happens.

Hope that helps,
Scott

---

### Post by gslug79 on 2009-10-31
I had the same problem after importing a database backup on a clean install. I spent hours trying to work out what was going on and eventually realised that the problem is obvious from the terminal output: ```
There are also other clients using this database. They should be shut down first.
```

I had restored the backup with mythtv-backend running. The Mythbuntu site makes no mention of the need to stop mythtv-backend before restoring the backup.

The solution was to stop mythtv-backend: ```
sudo /etc/init.d/mythtv-backend stop
```
Drop the database: ```
mysqladmin -u root -p drop mythconverg
```
Rebuild the tables: ```
mysql -u root -p < /usr/share/mythtv/sql/mc.sql
```
Restore the backup: ```
mysql -u mythtv -p mythconverg < backup.sql
``` 
Run mythbackend in the foreground and upgrade (successfully) the schema: ```
mythbackend
``` and kill it with ctl+c when done.

Restart the backend as a daemon: ```
sudo /etc/init.d/mythtv-backend start
```

This worked for me.

---

### Post by amar on 2009-11-01
> **gslug79 said:**
> I had the same problem after importing a database backup on a clean install. I spent hours trying to work out what was going on and eventually realised that the problem is obvious from the terminal output: ```
There are also other clients using this database. They should be shut down first.
```

I had restored the backup with mythtv-backend running.

Doh! Exactly the problem. I had tried dropping the tables then looking confused when they reappeared. Seems to be running fine now.

Thanks

---

### Post by gslug79 on 2009-11-01
Glad it worked.

---

### Post by paulsmith99 on 2009-11-01
Don't know whether this is the best place to say this but for what it's worth...

Apparently, the 'newer and better'(?) way to control daemons/services is via the service interface:

sudo service mythtv-backend stop

instead of 

sudo /etc/init.d/mythtv-backend stop

It's a bit easier to type and bash will auto complete the service name just as if you'd typed /etc/init.d/ anyway. Works for all other services (daemons) obviously.

Don't shoot the messenger.

:)

---

### Post by gslug79 on 2009-11-01
Thanks. I think the terminal output actually advised me of this but I guess I'm just used to ```
sudo /etc/init.d/blah....
```

---

### Post by nickrout on 2009-11-01
> **paulsmith99 said:**
> Don't know whether this is the best place to say this but for what it's worth...

Apparently, the 'newer and better'(?) way to control daemons/services is via the service interface:

sudo service mythtv-backend stop

instead of 

sudo /etc/init.d/mythtv-backend stop

It's a bit easier to type and bash will auto complete the service name just as if you'd typed /etc/init.d/ anyway. Works for all other services (daemons) obviously.

Don't shoot the messenger.

:)

you mean like redhat had 10 or more years ago? ;)

---

