---
title: "How to run multi-head without a desktop?"
date: 2009-03-10
forum: Multimedia Software
---

### Post by Frank H. Baker on 2009-03-10
I am developing a program that needs two screens in a three screen
multihead (two nvidia 8400 GPUs) system for writing graphics.  I use
Xlib/gdm to write to the screens and want the root windows to
otherwise have a uniform background.  Currently they have
desktop adornments: a menu bar at the top and a task bar at the bottom,
but they show my chosen background and my graphics as intended.  I am
looking for suggestions on how I can prevent the adornments from being
displayed.  I assume they are being added by a desktop manager, though
it is not apparent to me where it is informed to handle screens 2 and 3.
I do want a desktop on the console screen but otherwise would not have
it messing with the auxiliary screens.

I am running Ubuntu 8.04 with the metacity window manager and a Gnome
desktop.  I get the same treatment of screens 2 and 3 if I boot with gdm
or I come up on a terminal and execute startx.  My graphics hardware is
a pair of Nvidia 8400 GPUs, console and second monitor attached to one
and the third monitor on the second gpu.

I'd be glad to provide more information on my system if desired.
I show below a relevant segment of the output from ps ax.

Many thanks for any help.
Frank Baker

 ...
 5942 tty1     S+     0:00 /bin/bash /usr/bin/startx
 5959 tty1     S+     0:00 xinit /etc/X11/xinit/xinitrc -- /etc/X11/xinit/xserverrc -auth /tmp/serverauth.DeUITr5949
 5960 tty7     SLs+   3:51 /usr/bin/X11/X -nolisten tcp
 5969 tty1     S      0:00 /usr/bin/ck-launch-session /usr/bin/seahorse-agent --execute x-session-manager
 5999 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/ck-launch-session /usr/bin/seahorse-agent --execute x-session-manager
 6002 tty1     Sl     0:03 x-session-manager
 6050 ?        Ss     0:00 /usr/bin/seahorse-agent --execute x-session-manager
 6069 tty1     SL     0:00 /usr/bin/gnome-keyring-daemon
 6078 ?        Ss     0:00 dbus-daemon --fork --print-address 19 --print-pid 21 --session
 6081 tty1     Sl     0:02 gnome-settings-daemon
 6089 tty1     Sl     0:12 /usr/bin/pulseaudio --log-target=syslog
 6092 tty1     S      0:00 /usr/lib/pulseaudio/pulse/gconf-helper
 6101 tty1     S      0:26 /usr/bin/metacity --sm-client-id=default0
 6104 tty1     S      0:28 gnome-panel --sm-client-id default1
 6107 tty1     Sl     0:06 nautilus --no-default-window --sm-client-id default2
 6117 ?        Ss     0:34 gnome-screensaver

---

