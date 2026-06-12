---
title: "Ubuntu 11.10 and multible VNC connections"
date: 2012-01-09
forum: Networking &amp; Wireless
---

### Post by JKarppi on 2012-01-09
I have a problem with setting up Ubuntu 11.10 to be run remotely by multible users via multible VNC connection. I have used TightVNC Server version 1.3.9 for this thus it has worked fine earlier with 11.04. With multible users and no need to login locally. 

Connection can be established normaly but I don't have any menus on desctop!


Ubuntu version 11.10 (GNU/Linux 3.0.0-12-generic x86_64)

.vnc/xstartup -file looks like this:
#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
# Fix to make GNOME work
export XKL_XMODMAP_DISABLE=1
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS
exec /etc/X11/Xsession
exec /etc/X11/xinit/xinitrc
gnome-session &

I start the server like this:
vncserver :3

Looks to be started normaly...

New 'X' desktop is myserver:3

Starting applications specified in /home/myfolder/.vnc/xstartup
Log file is /home/myfolder/.vnc/myserver:3.log


When I look the logfile:
09/01/12 10:48:14 Xvnc version TightVNC-1.3.9
09/01/12 10:48:14 Copyright (C) 2000-2007 TightVNC Group
09/01/12 10:48:14 Copyright (C) 1999 AT&T Laboratories Cambridge
09/01/12 10:48:14 All Rights Reserved.
09/01/12 10:48:14 See [http://www.tightvnc.com/](http://www.tightvnc.com/) for information on TightVNC
09/01/12 10:48:14 Desktop name 'X' (myserver:3)
09/01/12 10:48:14 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t
09/01/12 10:48:14 Listening for VNC connections on TCP port 5903
Font directory '/usr/share/fonts/X11/75dpi/' not found - ignoring
Font directory '/usr/share/fonts/X11/100dpi/' not found - ignoring

dmesg will be added by lines:
[423407.641567] gnome-settings-[1579]: segfault at 0 ip 00007fbdb0bb3251 sp 00007ffff2903c20 error 4 in libwacom.so[7fbdb0bb0000+7000]
[423407.720977] compiz[1598]: segfault at 48 ip 00007f09b79814d0 sp 00007fffa8e1fb38 error 4 in libcomposite.so[7f09b7973000+18000]
[423407.771821] gnome-settings-[1601]: segfault at 0 ip 00007fec5e7f0251 sp 00007fff732c5410 error 4 in libwacom.so[7fec5e7ed000+7000]
[423408.230093] compiz[1686]: segfault at 48 ip 00007f58a5faa4d0 sp 00007fff110d9288 error 4 in libcomposite.so[7f58a5f9c000+18000]


Then used the tight vnc viever in W7 to connect  myserver:3
but only blank desctop will be shown.

Do I lack now some fonts or something? At least font server was not runnig at all?

Any help is wellcome! Don't like to fallback to 11.04.

---

