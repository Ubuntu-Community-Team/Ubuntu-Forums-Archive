---
title: "Failed to upgrade database schema"
date: 2013-04-15
forum: Mythbuntu
---

### Post by dannyboy79 on 2013-04-15
Hi guys, I took a database backup when I was running 0.23+fixes within 10.04.4 and did a new install of mythbuntu 12.04 and installed mythtv 0.25+fixes. importing the backup was successful but when I run mythtv-setup it says it needs to upgrade the database schema but it fails. Here's the relevant log section, can anyone please help me? Don't want to lose my 200+ recordings and recording schedules.

```
Apr 15 20:54:00 dell mythtv-setup[2484]: I CoreContext schemawizard.cpp:117 (Compare) Current MythTV Schema Version (DBSchemaVer): 1266
Apr 15 20:54:00 dell mythtv-setup[2484]: C CoreContext schemawizard.cpp:135 (CompareAndWait) MythTV database schema is old. Waiting to see if DB is being upgraded.
Apr 15 20:54:01 dell mythtv-setup[2484]: I CoreContext schemawizard.cpp:117 (Compare) Current MythTV Schema Version (DBSchemaVer): 1266
Apr 15 20:54:05  mythtv-setup[2484]: last message repeated 4 times
Apr 15 20:54:05 dell mythtv-setup[2484]: C CoreContext schemawizard.cpp:179 (CompareAndWait) Timed out waiting.
Apr 15 20:54:07 dell mythtv-setup[2484]: E CoreContext dbutil.cpp:603 (DoBackup) Backing up database with script: '/usr/share/mythtv/mythconverg_backup.pl'
Apr 15 20:54:40 dell mythtv-setup[2484]: C CoreContext dbutil.cpp:624 (DoBackup) Database Backup complete.
Apr 15 20:54:40 dell mythtv-setup[2484]: C CoreContext dbutil.cpp:655 (DoBackup) Backed up database to file: '/var/lib/mythtv/recordings/mythconverg-1266-20130415205407.sql.gz'
Apr 15 20:55:09 dell mythtv-setup[2484]: C CoreContext dbcheck.cpp:495 (UpgradeTVDatabaseSchema) Newest MythTV Schema Version : 1299
Apr 15 20:55:09 dell mythtv-setup[2484]: N CoreContext videodbcheck.cpp:154 (InitializeVideoSchema) Inserting initial video database information.
Apr 15 20:55:09 dell mythtv-setup[2484]: N CoreContext videodbcheck.cpp:53 (performActualUpdate) Upgrading to MythVideo schema version 1038
Apr 15 20:55:09 dell mythtv-setup[2484]: E CoreContext mythdb.cpp:192 (DBError) DB Error (performActualUpdate):#012Query was:#012#012Driver error was [2/1050]:#012QMYSQL: Unable to execute query#012Database error was:#012Table 'dvdinput' already exists
Apr 15 20:55:09 dell mythtv-setup[2484]: E CoreContext dbcheck.cpp:509 (UpgradeTVDatabaseSchema) Database Schema upgrade FAILED, unlocking.
Apr 15 20:55:09 dell mythtv-setup[2484]: E CoreContext main.cpp:512 (main) Couldn't upgrade database to new schema.
```

---

### Post by dannyboy79 on 2013-04-15
Ok, it turned out that a long time ago I used mythvideo but stopped using it so my mythvideo tables was so old that it was having issues upgrading that database schema for the mythvideo stuff. The solution was immediately after doing a full restore of my backup I created of 0.23+fixes into the new mythtv 0.25+fixes system, I ran the following commands.

```
cat << "EOF" | mysql -umythtv -p mythconverg 
DROP TABLE IF EXISTS videocast; 
DROP TABLE IF EXISTS videocategory; 
DROP TABLE IF EXISTS videocountry; 
DROP TABLE IF EXISTS videogenre; 
DROP TABLE IF EXISTS videometadata; 
DROP TABLE IF EXISTS videometadatacast; 
DROP TABLE IF EXISTS videometadatacountry; 
DROP TABLE IF EXISTS videometadatagenre; 
DROP TABLE IF EXISTS videotypes; 
DROP TABLE IF EXISTS filemarkup; 
DROP TABLE IF EXISTS dvdinput; 
DROP TABLE IF EXISTS dvdtranscode; 
DELETE FROM settings WHERE value 
IN ('mythvideo.DBSchemaVer', 
'VideoDBSchemaVer', 
'DVDDBSchemaVer'); 
EOF 
```
once those commands were done running, I started up mythtv-setup, it upgraded the database schema and it all appears to be working correctly. The thread that I was told to refer to by sphery from the mythtv-users IRC channel was this [http://www.gossamer-threads.com/lists/mythtv/users/512916#512916]("http://www.gossamer-threads.com/lists/mythtv/users/512916#512916")

---

