---
title: "tightvnc not installing"
date: 2009-03-07
forum: Networking &amp; Wireless
---

### Post by SemiGuy on 2009-03-07
Looks like I need some help on this one.  I'm trying to get tightvnc installed on Gutsy so I can get to it from an XP machine.

But, tightvnc does not want to install.  It gets an error from xdebconfigurator every time.  The end of the install script shows:

[INDENT]debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Ronf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
invoke-rc.d: initscript xdebconfigurator, action "start" failed.
dpkg: error processing xdebconfigurator (--configure):
 subprocess post-installation script returned error exit status 1
Setting up tightvncserver (1.2.9-21) ...

Errors were encountered while processing:
 xdebconfigurator
E: Sub-process /usr/bin/dpkg returned an error code (1)[/INDENT]

I've been fighting this one for a week now.  Any help would be appreciated.

SemiGuy

---

### Post by SemiGuy on 2009-03-08
Well, I found the problem, and for posterity: Do not try to install VNC on gOS 2.x!  This is on a cheapy Everex box and the build is busted in several ways.

I fixed the problem by installing the gOS 3.1 version.  Not a bad solution for a control-type PC at a remote location that is also used once in a while for light work.  This version is based on Hardy and works great with tightvncserver.  Very clean build and control.

Cheers.

---

