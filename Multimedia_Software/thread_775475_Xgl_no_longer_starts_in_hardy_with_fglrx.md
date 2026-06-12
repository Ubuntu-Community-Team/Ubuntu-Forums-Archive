---
title: "Xgl no longer starts in hardy with fglrx"
date: 2008-04-30
forum: Multimedia Software
---

### Post by lesshaste on 2008-04-30
I recently upgraded from Gutsy to Hardy and it has caused a number of problems. One of the more serious is that Xgl won't start anymore.  I get the log in screen but then afterwards a little dialog bog pops but saying to look in .xsession-errors which contains

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Checking for nVidia: not present. 
Starting Xgl with options:  -accel xv:pbuffer -accel glx:pbuffer -nolisten tcp -fullscreen -br +xinerama 
Waiting 10 more seconds for Xgl to start...
xmodmap:  unable to open display ':1'
cannot open display: 
Run '/usr/bin/seahorse-agent --help' to see a full list of available command line options.


If I reboot using the old 2.6.22 kernel Xgl works ok (except 3d acceleration is broken).

The chipset is ATI Technologies Inc RS480 [Radeon Xpress 200G Series].

The full X log from the broken startup attempt is at [http://pastebin.com/f5bcd0619](http://pastebin.com/f5bcd0619)

If any more info would help please let me know.
Raphael

---

