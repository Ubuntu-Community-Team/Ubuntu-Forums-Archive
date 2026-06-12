---
title: "unable to upgrade dbschema to 1254"
date: 2010-11-26
forum: Mythbuntu
---

### Post by blkbx on 2010-11-26
After using the repo build to upgrade mythtv to .24 I haven't been able to use mythtv. The error is that the db isn't the correct vesion. My frontend log file is below. Can someone tell me how to do this please.
thanks heaps.
Starting mythfrontend.real..
2010-11-26 10:44:43.702 mythfrontend version: branches/release-0-24-fixes [27321] [www.mythtv.org](www.mythtv.org)
2010-11-26 10:44:43.702 Using runtime prefix = /usr
2010-11-26 10:44:43.702 Using configuration directory = /home/tomas/.mythtv
2010-11-26 10:44:43.703 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2010-11-26 10:44:44.404 Empty LocalHostName.
2010-11-26 10:44:44.404 Using localhost value of mythtv-frontend
2010-11-26 10:44:44.405 Testing network connectivity to '192.168.2.5'
2010-11-26 10:44:44.515 New DB connection, total: 1
2010-11-26 10:44:44.780 Connected to database 'mythconverg' at host: 192.168.2.5
2010-11-26 10:44:44.790 Closing DB connection named 'DBManager0'
2010-11-26 10:44:45.041 Connected to database 'mythconverg' at host: 192.168.2.5
2010-11-26 10:44:45.059 Current locale en_NZ
2010-11-26 10:44:45.060 No locale defaults file for en_NZ, skipping
2010-11-26 10:44:45.212 ScreenSaverX11Private: XScreenSaver support enabled
2010-11-26 10:44:45.212 DPMS is disabled.
2010-11-26 10:44:45.228 Desktop video mode: 1920x1080 60.000 Hz
2010-11-26 10:44:45.259 Enabled verbose msgs:  important general
2010-11-26 10:44:45.264 Loading en_us translation for module mythfrontend
2010-11-26 10:44:45.277 LIRC: Successfully initialized '/dev/lircd' using '/home/tomas/.mythtv/lircrc' config
2010-11-26 10:44:45.277 JoystickMenuThread: Joystick disabled - Failed to read /home/tomas/.mythtv/joystickme$
2010-11-26 10:44:45.334 Using Frameless Window
2010-11-26 10:44:45.334 Using Full Screen Window
2010-11-26 10:44:45.338 Using the Qt painter
2010-11-26 10:44:45.659 New DB connection, total: 2
2010-11-26 10:44:45.659 New DB connection, total: 3
2010-11-26 10:44:45.662 Current MythTV Schema Version (DBSchemaVer): 1254
2010-11-26 10:44:45.663 MythTV database schema is old. Waiting to see if DB is being upgraded.
2010-11-26 10:44:45.909 Connected to database 'mythconverg' at host: 192.168.2.5
2010-11-26 10:44:46.161 Connected to database 'mythconverg' at host: 192.168.2.5
2010-11-26 10:44:46.669 Current MythTV Schema Version (DBSchemaVer): 1254
2010-11-26 10:44:47.673 Current MythTV Schema Version (DBSchemaVer): 1254
2010-11-26 10:44:48.678 Current MythTV Schema Version (DBSchemaVer): 1254
2010-11-26 10:44:49.682 Current MythTV Schema Version (DBSchemaVer): 1254
2010-11-26 10:44:50.687 Current MythTV Schema Version (DBSchemaVer): 1254
2010-11-26 10:44:50.687 Timed out waiting.
2010-11-26 10:44:50.688 Not allowed to upgrade the database.
2010-11-26 10:44:53.953 Couldn't upgrade database to new schema, exiting.
2010-11-26 10:44:53.953 Deleting UPnP client..

---

