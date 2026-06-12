---
title: "Mythtv Freshinstall - Errors when loading already"
date: 2009-08-31
forum: Multimedia Software
---

### Post by isaidi on 2009-08-31
Just did a fresh install of mythbuntu 9.04, then ran update..

I didn't check for errors before the update, 
But while I was troubleshooting a visualization bug, I noticed now I get the following warnings and errors. Should I worry about any of this ?

Seems like the Theme not found error is fairly common too... I tried 
dpkg-reconfigure mythtv-common but didn't work


```

2009-08-31 01:30:43.592 Using runtime prefix = /usr
2009-08-31 01:30:44.114 XScreenSaver support enabled
2009-08-31 01:30:44.115 DPMS is disabled.
2009-08-31 01:30:44.115 Empty LocalHostName.
2009-08-31 01:30:44.115 Using localhost value of [REMOVED]
2009-08-31 01:30:44.120 New DB connection, total: 1
2009-08-31 01:30:44.128 Connected to database 'mythconverg' at host: localhost
2009-08-31 01:30:44.129 Closing DB connection named 'DBManager0'
2009-08-31 01:30:44.131 Primary screen 0.
2009-08-31 01:30:44.131 Connected to database 'mythconverg' at host: localhost
2009-08-31 01:30:44.132 Using screen 0, 1360x768 at 0,0
2009-08-31 01:30:44.137 New DB connection, total: 2
2009-08-31 01:30:44.138 Connected to database 'mythconverg' at host: localhost
2009-08-31 01:30:44.142 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-08-31 01:30:44.142 Enabled verbose msgs:  important general
2009-08-31 01:30:44.424 No theme dir: /home/abe/.mythtv/themes/metallurgy-wide
2009-08-31 01:30:44.425 Primary screen 0.
2009-08-31 01:30:44.425 Using screen 0, 1360x768 at 0,0
2009-08-31 01:30:44.425 No theme dir: /home/abe/.mythtv/themes/metallurgy-wide
2009-08-31 01:30:44.426 Switching to wide mode (metallurgy-wide)
2009-08-31 01:30:44.442 Using the OpenGL painter
2009-08-31 01:30:44.442 JoystickMenuClient Error: Joystick disabled - Failed to read /home/abe/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2009-08-31 01:30:44.443 lirc_init failed for mythtv, see preceding messages
2009-08-31 01:30:44.980 Loading from: /usr/share/mythtv/themes/metallurgy-wide/base.xml
2009-08-31 01:30:44.988 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-08-31 01:30:45.011 Registering Internal as a media playback plugin.
2009-08-31 01:30:45.055 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-08-31 01:30:45.072 Failed to run 'cdrecord --scanbus'
2009-08-31 01:30:45.075 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-08-31 01:30:45.079 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-08-31 01:30:45.095 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-08-31 01:30:45.124 No theme dir: /home/abe/.mythtv/themes/metallurgy-wide
2009-08-31 01:30:45.298 Using NV NPOT texture extension

```

---

