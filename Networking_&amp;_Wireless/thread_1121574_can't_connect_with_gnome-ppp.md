---
title: "can't connect with gnome-ppp"
date: 2009-04-10
forum: Networking &amp; Wireless
---

### Post by lorebett on 2009-04-10
Hi
I'm using Jaunty beta, and using Gnome for the first time (I've always used KDE); I need to connect with a serial modem and I've tried gnome-ppp.

I've put my user in the "dip" and "dialout" group; gnome-ppp detects my modem, and it dials correctly; the log says that pppd has started, but I see no ppp0 interface if I do /sbin/ifconfig, and indeed I'm not connected to the Internet (and the modem connection dies after less than one minute).

any clue please?

By the way, I still need to run gnome-ppp as root, since chat and pap files can be written only by root.  Shouldn't they be writable also by dip?

thanks in advance
Lorenzo

---

