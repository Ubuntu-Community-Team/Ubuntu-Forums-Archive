---
title: "Upgrade killed database.... again..."
date: 2013-01-15
forum: Mythbuntu
---

### Post by Raptor Ramjet on 2013-01-15
Hello,

I recently did a stupid thing.  I decided to upgrade my MythTV box due to it informing me the release I was using was no longer supported.  *Very* bad idea as now it doesn't work at all due to the upgrade failing to sort out the database so the database schema seems to be out of step.  

Obviously I've wasted many hours looking all over the 'net for solutions but there are so many different things to try, none of them seem to be specific to my version etc. (why the hell don't the people who wrote "How to's" always refer to the damned version they're talking about ?) so I'm after a bit of help.

I'm on 12.04 AMD 64.  The output of trying to run "Mythbackend" on the command line is as follows:

```

me@mymachine:/var/lib/mythtv/db_backups$ mythbackend
2013-01-15 22:02:47.140134 C  mythbackend version: fixes/0.25 [v0.25.2-15-g46cab93] www.mythtv.org
2013-01-15 22:02:47.140162 C  Qt version: compile: 4.8.1, runtime: 4.8.1
2013-01-15 22:02:47.140167 N  Enabled verbose msgs:  general
2013-01-15 22:02:47.140191 N  Setting Log Level to LOG_INFO
2013-01-15 22:02:47.140248 I  Added logging to the console
2013-01-15 22:02:47.140255 I  Added database logging to table logging
2013-01-15 22:02:47.140364 N  Setting up SIGHUP handler
2013-01-15 22:02:47.140440 N  Using runtime prefix = /usr
2013-01-15 22:02:47.140457 N  Using configuration directory = /home/ramjet/.mythtv
2013-01-15 22:02:47.141041 I  Assumed character encoding: en_GB.UTF-8
2013-01-15 22:02:47.141639 N  Empty LocalHostName.
2013-01-15 22:02:47.141649 I  Using localhost value of mythic
2013-01-15 22:02:47.168069 N  Setting QT default locale to EN_GB
2013-01-15 22:02:47.168138 I  Current locale EN_GB
2013-01-15 22:02:47.168189 N  Reading locale defaults from /usr/share/mythtv//locales/en_gb.xml
2013-01-15 22:02:47.175900 I  Current MythTV Schema Version (DBSchemaVer): 1280
2013-01-15 22:02:47.175915 C  MythTV database schema is old. Waiting to see if DB is being upgraded.
2013-01-15 22:02:48.181883 I  Current MythTV Schema Version (DBSchemaVer): 1280
2013-01-15 22:02:49.185776 I  Current MythTV Schema Version (DBSchemaVer): 1280
2013-01-15 22:02:50.189589 I  Current MythTV Schema Version (DBSchemaVer): 1280
2013-01-15 22:02:51.193511 I  Current MythTV Schema Version (DBSchemaVer): 1280
2013-01-15 22:02:52.197384 I  Current MythTV Schema Version (DBSchemaVer): 1280
2013-01-15 22:02:52.197518 C  Timed out waiting.
2013-01-15 22:02:52.216157 E  Backing up database with script: '/usr/share/mythtv/mythconverg_backup.pl'
2013-01-15 22:02:52.216849 I  Starting process manager
2013-01-15 22:02:52.217272 I  Starting process signal handler
2013-01-15 22:02:52.220976 I  Starting IO manager (read)
2013-01-15 22:02:52.221467 I  Starting IO manager (write)
^C2013-01-15 22:03:03.535334 E  DBUtil: Error backing up database: /usr/share/mythtv/mythconverg_backup.pl  /tmp/mythtv_db_backup_conf_uivM1s (140)
2013-01-15 22:03:03.535357 C  Script-based database backup failed. Retrying with internal backup.
2013-01-15 22:03:03.537215 C  Backing up database to file: '/var/lib/mythtv/db_backups/mythconverg-1280-20130115220303.sql'
2013-01-15 22:03:13.771824 C  Compressing database backup file.

Warning: MythTV wants to upgrade your database,
for the TV schema, from 1280 to 1299.

Database Host: localhost
Database Name: mythconverg

If your system becomes unstable, a database backup is located in /var/lib/mythtv/db_backups/mythconverg-1280-20130115220303.sql.gz


Shall I upgrade this database? [yes]  2013-01-15 22:03:21.464767 C  Database Backup filename: '/var/lib/mythtv/db_backups/mythconverg-1280-20130115220303.sql.gz'
2013-01-15 22:03:21.464786 C  Database Backup complete.

```

At this point I have to press send after which I get...

```

2013-01-15 22:07:09.822496 E  Couldn't upgrade database to new schema

```

Thanks in advance for any help.

---

### Post by BicyclerBoy on 2013-01-15
Apart from the general MythTV 0.24-->0.25 -->0.26 changes around logging/syslog/rsyslog & upstart jobs & mysql.txt vs config.xml...the process is the same.
0.26 requires the timezone package in mysql..Can install this at any time or version.

There have been changes around schema updates & exactly who/when can start the process.

The mythbuntu distro must have it's own release notes & wrangling scripts.

-1. read release notes
0. stop backend(s) , no FE running
1. backup the dB (keep it safe)
2. update s/w
3. run mythtv-setup

If successful (schema update) then:
1.start backend (terminal with verbose logging or service mythtv-backend start)
2. start frontend with verbose logging
2a. scan audio devices
2b. check video playback profiles for removed filters (vdpau stuff).

mysql.txt stuff has moved/morphed into config.xml but it is not much different.

User jobs/scripts that used mysql.txt & starttime will have problems.

---

