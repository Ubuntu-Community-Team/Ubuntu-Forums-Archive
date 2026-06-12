---
title: "Issue with MythTV Schema update from 1299"
date: 2014-11-01
forum: Mythbuntu
---

### Post by BigPacks on 2014-11-01
I'm trying to update my Mythbuntu setup from 12.04 to 14.04.01.

What I've done is backup my MythTV database, got a new HDD and installed a brand new 14.04.01 version of MythTV on there (i.e. I still have my original 12.04 and it works ok).  Even with the difficult Hauppauge HVR-2250, I got it working and I can watch Live TV simply via an OTA turning.

When I try to restore the database using [these instructions]("http://www.mythtv.org/wiki/Database_Backup_and_Restore") (something I have done successfully before on other versions), it seems to work fine.  Also I'm ensuring that the timezone tables are correct as specified [here]("http://www.mythtv.org/wiki/MySQL_Time_Zone_Tables").

When I try to run the frontend, it tells me that the schema wants to update from 1299 to 1318 (from memory).  I try and run Mythbackend and let it upgrade the database, but it doesn't work.

From looking through the log files (attached), the bits which grab my attention are the following:

In mythtv-setup.log
```

Nov  2 12:55:10 mythdoukie-desktop mythtv-setup.real: mythtv-setup[4047]: I CoreContext schemawizard.cpp:118 (Compare) Current MythTV Schema Version (DBSchemaVer): 1299
Nov  2 12:55:10 mythdoukie-desktop mythtv-setup.real: mythtv-setup[4047]: E CoreContext dbutil.cpp:604 (DoBackup) Backing up database with script: '/usr/share/mythtv/mythconverg_backup.pl'
Nov  2 12:55:26 mythdoukie-desktop mythtv-setup.real: mythtv-setup[4047]: C CoreContext dbutil.cpp:625 (DoBackup) Database Backup complete.
Nov  2 12:55:26 mythdoukie-desktop mythtv-setup.real: mythtv-setup[4047]: C CoreContext dbutil.cpp:656 (DoBackup) Backed up database to file: '/var/lib/mythtv/db_backups/mythconverg-1299-20141102015510.sql.gz'
Nov  2 12:55:42 mythdoukie-desktop mythtv-setup.real: mythtv-setup[4047]: C CoreContext dbcheck.cpp:402 (performActualUpdate) Upgrading to MythTV schema version 1300
Nov  2 12:55:42 mythdoukie-desktop mythtv-setup.real: mythtv-setup[4047]: E CoreContext dbcheck.cpp:417 (performActualUpdate) DB Error (Performing database upgrade): #012Query was: ALTER TABLE recordmatch ADD COLUMN findid INT NOT NULL DEFAULT 0 #012Error was: Driver error was [2/1060]:#012QMYSQL: Unable to execute query#012Database error was:#012Duplicate column name 'findid'#012 #012new version: 1300
Nov  2 12:55:42 mythdoukie-desktop mythtv-setup.real: mythtv-setup[4047]: E CoreContext dbcheck.cpp:502 (UpgradeTVDatabaseSchema) Database schema upgrade failed.
Nov  2 12:55:42 mythdoukie-desktop mythtv-setup.real: mythtv-setup[4047]: E CoreContext main.cpp:553 (main) Couldn't upgrade database to new schema.

```

In mythbackend.log
```

Nov  2 12:57:21 mythdoukie-desktop mythbackend: mythbackend[2179]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Nov  2 12:57:21 mythdoukie-desktop mythbackend: mythbackend[2179]: I CoreContext schemawizard.cpp:118 (Compare) Current MythTV Schema Version (DBSchemaVer): 1299
Nov  2 12:57:21 mythdoukie-desktop mythbackend: mythbackend[2179]: W CoreContext dbcheck.cpp:481 (UpgradeTVDatabaseSchema) Not allowed to upgrade the database.
Nov  2 12:57:21 mythdoukie-desktop mythbackend: mythbackend[2179]: I CoreContext schemawizard.cpp:271 (PromptForUpgrade) Console is non-interactive, can't prompt user...
Nov  2 12:57:21 mythdoukie-desktop mythbackend: mythbackend[2179]: E CoreContext main_helpers.cpp:555 (run_backend) Couldn't upgrade database to new schema
Nov  2 12:57:21 mythdoukie-desktop mythbackend: mythbackend[2179]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Nov  2 12:57:21 mythdoukie-desktop mythbackend: mythbackend[2179]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging

```

It appears that the following bit in the mythtv-setup.log is the problem, but I'm not sure how to fix it.  It obviously fails trying to upgrade to Schema 1300.
```

Nov  2 12:55:42 mythdoukie-desktop mythtv-setup.real:  mythtv-setup[4047]: C CoreContext dbcheck.cpp:402 (performActualUpdate)  Upgrading to MythTV schema version 1300
Nov  2 12:55:42  mythdoukie-desktop mythtv-setup.real: mythtv-setup[4047]: E CoreContext  dbcheck.cpp:417 (performActualUpdate) DB Error (Performing database  upgrade): #012Query was: ALTER TABLE recordmatch ADD COLUMN findid INT  NOT NULL DEFAULT 0 #012Error was: Driver error was [2/1060]:#012QMYSQL:  Unable to execute query#012Database error was:#012Duplicate column name  'findid'#012 #012new version: 1300
Nov  2 12:55:42 mythdoukie-desktop  mythtv-setup.real: mythtv-setup[4047]: E CoreContext dbcheck.cpp:502  (UpgradeTVDatabaseSchema) Database schema upgrade failed.

```

Anybody got any idea how to fix this?

Thanks

---

