---
title: "live tv won't work, but used to in 20.xx"
date: 2008-04-24
forum: Mythbuntu
---

### Post by Afkpuz on 2008-04-24
I just upgraded to mythtv 21.0 and cannot get my pchdtv 5500 to play live TV.  the backend setup successfully scans and adds channels, but when I goto watch live tv, I get the following message:

```
2008-04-24 15:50:47.663 Using runtime prefix = /usr, libdir = /usr/lib
2008-04-24 15:50:47.978 XScreenSaver support enabled
2008-04-24 15:50:47.979 DPMS is active.
2008-04-24 15:50:47.980 Empty LocalHostName.
2008-04-24 15:50:47.980 Using localhost value of Alexander-Grayson
2008-04-24 15:50:47.992 New DB connection, total: 1
2008-04-24 15:50:47.997 Connected to database 'mythconverg' at host: localhost
2008-04-24 15:50:48.000 Closing DB connection named 'DBManager0'
2008-04-24 15:50:48.001 Primary screen 0.
2008-04-24 15:50:48.001 Connected to database 'mythconverg' at host: localhost
2008-04-24 15:50:48.003 Using screen 0, 640x480 at 0,0
2008-04-24 15:50:48.022 New DB connection, total: 2
2008-04-24 15:50:48.023 Connected to database 'mythconverg' at host: localhost
2008-04-24 15:50:48.025 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-04-24 15:50:48.026 Enabled verbose msgs:  important general
2008-04-24 15:50:48.332 Primary screen 0.
2008-04-24 15:50:48.333 Using screen 0, 640x480 at 0,0
2008-04-24 15:50:48.334 Switching to square mode (G.A.N.T)
2008-04-24 15:50:48.364 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2008-04-24 15:50:48.365 lirc_init failed for mythtv, see preceding messages
2008-04-24 15:50:48.365 JoystickMenuClient Error: Joystick disabled - Failed to read /home/alex/.mythtv/joystickmenurc
2008-04-24 15:50:49.084 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2008-04-24 15:50:49.155 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-04-24 15:50:49.225 Registering Internal as a media playback plugin.
2008-04-24 15:50:50.403 Connecting to backend server: 10.107.200.62:6543 (try 1 of 5)
2008-04-24 15:50:50.404 Using protocol version 40
2008-04-24 15:50:50.421 TV: Attempting to change from None to WatchingLiveTV
2008-04-24 15:50:50.422 Using protocol version 40
2008-04-24 15:50:51.479 GetEntryAt(-1) failed.
2008-04-24 15:50:51.481 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2008-04-24 15:50:51.481 TV Error: LiveTV not successfully started
2008-04-24 15:50:51.482 TV Error: LiveTV not successfully started
2008-04-24 15:50:51.523 TV: Deleting TV Chain in destructor
2008-04-24 15:50:51.525 DPMS Deactivated 
2008-04-24 15:50:51.526 DPMS Reactivated.
2008-04-24 15:50:54.798 Deleting UPnP client...
```


This is very frustrating to me as my tuner card worked flawlessly in the last version of mythtv, but this upgrade suddenly doesn't like my card.  can anyone help me?

---

### Post by laga on 2008-04-24
Can you post the backend log?

---

### Post by Afkpuz on 2008-04-24
how to do that?

---

### Post by Afkpuz on 2008-04-26
Ok, it seems that if I sudo killall mythbackend, then restart mythbackend, it works.  I don't know why though.  Anyone got any ideas?

---

### Post by laga on 2008-04-26
Check the link in my signature to find out how to provide the log files.

---

### Post by 7.11brown on 2008-07-30
I have the same problem on my current install.  This is all trying to get my HDHR to play without skipping, or crashing myth :)

I will try a new install (straight mythbuntu) and possibly functionality.

Once I select Watch tv, it will be black for 2-3 seconds, and go back to the menu.  Help?!?

---

### Post by smbm on 2008-08-01
I'm getting the same problems too.

Here is the line in my mythfrontend debug info which is where it starts go awry:

2008-08-01 15:19:06.034 EntryToProgram(0@Thu Jan 1 01:00:00 1970) failed to get pginfo

Is it some kind of time stamp problem?

After that I get this:

2008-08-01 15:12:24.027 TV Error: LiveTV not successfully started
2008-08-01 15:12:24.027 TV Error: LiveTV not successfully started
2008-08-01 15:12:24.035 TV: Deleting TV Chain in destructor
2008-08-01 15:12:24.048 DPMS Deactivated 
2008-08-01 15:12:24.049 DPMS Reactivated.

Anyone? Any ideas?

---

### Post by Afkpuz on 2008-08-01
I'm not sure what the deal was, but it looked like the backend needed to be restarted every boot up.  I've since left that behind and moved onto linuxmce which has mythtv integrated into it.

---

### Post by smbm on 2008-08-03
Anyone else got any ideas?

I've tried restarting the backend to no avail, the same problem still occurs with the same entries in the log file.

---

