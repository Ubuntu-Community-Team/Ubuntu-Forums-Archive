---
title: "Upgrade problem, mythvideo db version"
date: 2010-05-01
forum: Mythbuntu
---

### Post by ian dobson on 2010-05-01
Hi All,

OK I've upgraded my backend mythtv system, that went well without any major problems, but my frontend is giving me real problems.

```

It looks as if the frontend thinks that the mythvideo table is too old and tries to upgrade it. Being a "nice" program it tries to backup the database first but fails:-
2010-05-01 10:45:52.070 New DB connection, total: 1
2010-05-01 10:45:52.072 Connected to database 'mythconverg' at host: 192.168.0.1
2010-05-01 10:45:52.074 Closing DB connection named 'DBManager0'
2010-05-01 10:45:52.091 ScreenSaverX11Private: Gnome screen saver support enabled
2010-05-01 10:45:52.093 DPMS is active.
2010-05-01 10:45:52.095 Primary screen: 0.
2010-05-01 10:45:52.097 Connected to database 'mythconverg' at host: 192.168.0.1
2010-05-01 10:45:52.098 Using screen 0, 1920x1080 at 0,0
2010-05-01 10:45:52.125 Desktop video mode: 1920x1080 60.0024 Hz
2010-05-01 10:45:52.423 MythUI Image Cache size set to 20971520 bytes
2010-05-01 10:45:52.452 Enabled verbose msgs:  important general
2010-05-01 10:45:52.461 Primary screen: 0.
2010-05-01 10:45:52.461 Using screen 0, 1920x1080 at 0,0
2010-05-01 10:45:52.463 Using theme base resolution of 1280x720
2010-05-01 10:45:52.474 LIRC: Successfully initialized '/var/run/lirc/lircd' using '/home/id/.mythtv/lircrc' config
2010-05-01 10:45:52.475 JoystickMenuThread Error: Joystick disabled - Failed to read /home/id/.mythtv/joystickmenurc
2010-05-01 10:45:52.534 Using Frameless Window
2010-05-01 10:45:52.534 Using Full Screen Window
2010-05-01 10:45:52.885 Using the Qt painter
2010-05-01 10:45:53.059 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/MythCenter-wide/base.xml'
2010-05-01 10:45:53.076 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-05-01 10:45:53.086 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-05-01 10:45:53.108 Current MythTV Schema Version (DBSchemaVer): 1254
2010-05-01 10:45:53.774 Could not open settings file /home/id/.mythtv/mysql.txt for writing
2010-05-01 10:45:53.990 Registering Internal as a media playback plugin.
2010-05-01 10:46:22.125 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2010-05-01 10:46:22.125 **Datenbankschema MythVideo ist veraltet. PrÃ¼fe ob die Datenbank aktualisiert werden kann**.
2010-05-01 10:46:23.126 New DB connection, total: 2
2010-05-01 10:46:23.127 Connected to database 'mythconverg' at host: 192.168.0.1
2010-05-01 10:46:23.130 Waiting for Database Backup to complete.
2010-05-01 10:46:24.134 Waiting for Database Backup to complete.
2010-05-01 10:46:26.173 Waiting for Database Backup to complete.
2010-05-01 10:46:26.173 Timed out waiting.
2010-05-01 10:46:26.177 Database backup script does not exist: /usr/share/mythtv/mythconverg_backup.pl
2010-05-01 10:46:26.182 SG(DB Backups) Error: FindNextDirMostFree: '/data/mythtv/backup' does not exist!
2010-05-01 10:46:26.183 Backing up database to file: '/tmp/mythconverg-1254-20100501104626.sql'
2010-05-01 10:47:32.663 Compressing database backup file.
2010-05-01 10:47:59.063 Database Backup filename: '/tmp/mythconverg-1254-20100501104626.sql.gz'
2010-05-01 10:47:59.063 Database Backup complete.
ICE default IO error handler doing an exit(), pid = 1799, errno = 32

```

The message 
"Datenbankschema MythVideo ist veraltet. PrÃ¼fe ob die Datenbank aktualisiert werden kann" means the MythVideo database is out of date,checking if it can be updaged.

Is there a simple way to force the frontend to update the schema? And what does the error "ICE default IO error" mean?

Regards
Ian Dobson

---

### Post by ian dobson on 2010-05-01
Hi,

Just tried copying the /usr/share/mythtv/mythconverg_backup.pl from the backend to the frontend. It now creates a backup in /tmp but I'm still getting the
ICE default IO error handler doing an exit(), pid = 3844, errno = 32

Someone's got to know what this is.

Regards
Ian Dobson

---

### Post by ian dobson on 2010-05-01
OK Problem solved.

I deleted the .ICEauthority from my home directory and the frontend does the db update.

Regards
Ian Dobson

---

