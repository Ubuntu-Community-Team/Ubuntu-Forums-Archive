---
title: "problems running mythtv"
date: 2008-08-03
forum: Multimedia Software
---

### Post by lavy on 2008-08-03
Hy,

I've managed to install mythtv and I typed the setup command: 
sudo mythtv-setup

I entered the main menu and begin the configuration. When I'm trying to access the Capture cards menu it crashes with the following error:

2008-08-03 12:27:00.173 Switching to square mode (G.A.N.T)
2008-08-03 12:27:00.192 Using the Qt painter
mythtv: could not open config file /home/lavinia/.lircrc
mythtv: No such file or directory
2008-08-03 12:27:00.192 Failed to read lirc config /home/lavinia/.lircrc for mythtv
2008-08-03 12:27:00.192 JoystickMenuClient Error: Joystick disabled - Failed to read /home/lavinia/.mythtv/joystickmenurc
2008-08-03 12:27:01.522 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2008-08-03 12:27:01.729 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-08-03 12:27:01.746 No theme dir: /home/lavinia/.mythtv/themes/G.A.N.T
2008-08-03 12:27:09.526 Running tv_find_grabbers.
**mythtv-setup: symbol lookup error: /usr/lib/libmythtv-0.21.so.0: undefined symbol: lstat64**


After that I've tried to access mythtv with the following command:
mythfrontend

so I received the following error (same as before):
2008-08-03 12:29:43.597 Using runtime prefix = /usr
2008-08-03 12:29:43.906 DPMS is active.
2008-08-03 12:29:43.906 Empty LocalHostName.
2008-08-03 12:29:43.906 Using localhost value of lavy
2008-08-03 12:29:43.916 New DB connection, total: 1
2008-08-03 12:29:43.919 Connected to database 'mythconverg' at host: localhost
2008-08-03 12:29:43.920 Closing DB connection named 'DBManager0'
2008-08-03 12:29:43.921 Primary screen 0.
2008-08-03 12:29:43.922 Connected to database 'mythconverg' at host: localhost
2008-08-03 12:29:43.922 Using screen 0, 1920x1200 at 0,0
2008-08-03 12:29:43.929 New DB connection, total: 2
2008-08-03 12:29:43.929 Connected to database 'mythconverg' at host: localhost
2008-08-03 12:29:43.930 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-08-03 12:29:43.930 Enabled verbose msgs:  important general
**mythfrontend: symbol lookup error: mythfrontend: undefined symbol: lstat64**


I should mention that when I type sudo apt-get install, the system shows me that I should remove some packages, mythtv-backend beeing one of them :confused::
lavinia@lavy:~$ sudo apt-get install
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfame-0.9 libpvm3 libx264-57 mythtv-backend transcode
Use 'apt-get autoremove' to remove them.

I use: Ubuntu 8.04, Kde 3.59

Any ideas?
Thanks

---

