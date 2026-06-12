---
title: "&quot;mythtv is already using all available inputs&quot;`"
date: 2008-01-27
forum: Multimedia &amp; Video
---

### Post by nbv4 on 2008-01-27
I've tried EVERYTHING. I completely uninstalled and reinstalled everything having to do with MythTV... I've dumped the database... I've rebooted. No matter what I do, I get this damn error:

"mythtv is already using all available inputs"

What can be the cause of this problem. At this point the only thing I can think of to fix it is to do a complete reinstall of the operating system. I don't really want to do that.


The odd thing is, when I first started trying to get MythTV working, I wasn't getting that error. I could at least get multi-colored gibberish when I clicked on "Watch TV" in the frontend...


here is the output when the frontend is ran:

```
nbv4@nbv4-desktop:~$ mythfrontend
2008-01-27 13:40:05.579 Using runtime prefix = /usr
2008-01-27 13:40:05.594 Gnome-Screensaver support enabled
2008-01-27 13:40:05.595 DPMS is active.
2008-01-27 13:40:05.633 New DB connection, total: 1
2008-01-27 13:40:05.637 Connected to database 'mythconverg' at host: localhost
2008-01-27 13:40:05.638 Total desktop dim: 1680x1050, with 1 screen[s].
2008-01-27 13:40:05.641 Using screen 0, 1680x1050 at 0,0
2008-01-27 13:40:05.648 Current Schema Version: 1160
2008-01-27 13:40:05.648 mythfrontend version: 0.20.20070821-1 www.mythtv.org
2008-01-27 13:40:05.649 Enabled verbose msgs:  important general
2008-01-27 13:40:05.919 Total desktop dim: 1680x1050, with 1 screen[s].
2008-01-27 13:40:05.921 Using screen 0, 1680x1050 at 0,0
2008-01-27 13:40:05.921 Switching to square mode (G.A.N.T.)
2008-01-27 13:40:05.937 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2008-01-27 13:40:06.609 Joystick disabled.
2008-01-27 13:40:07.454 Loading from: /usr/share/mythtv/themes/G.A.N.T./base.xml
2008-01-27 13:40:07.473 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-01-27 13:40:07.511 Registering Internal as a media playback plugin.
2008-01-27 13:40:09.552 New DB connection, total: 2
2008-01-27 13:40:09.553 Connected to database 'mythconverg' at host: localhost
2008-01-27 13:40:09.582 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-01-27 13:40:09.583 Using protocol version 31
2008-01-27 13:40:10.413 TV: Attempting to change from None to None

```

that last line is what's confusing me. Under Input Connections, each option is under "cable". None of them say "None"

---

### Post by nbv4 on 2008-01-27
here are some screenshots of my settings

---

