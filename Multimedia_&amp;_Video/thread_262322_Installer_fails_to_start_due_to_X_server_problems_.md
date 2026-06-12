---
title: "Installer fails to start due to X server problems on Dell D620"
date: 2006-09-21
forum: Multimedia &amp; Video
---

### Post by aspa on 2006-09-21
i'm trying to install Dapper Drake on a Dell Latitude D620.

when i boot the installation CD (ubuntu-6.06.1-desktop-i386.iso), the installation fails because the X server is unable to start.

Windows Device Manager reports that the display adapter is a Mobile Intel 945GM Express Chipset Family.

here're the error messages issued by the installer:

"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?


X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux ubuntu 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from the config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Sep 21 20:58:36 2006
(==) Using config file: "/etc/X11/xorg.conf"
(WW) I810: No matching Device section for instance (BusID PCI:0:2:1) found
(EE) I810(0): No Video BIOS modes for chosen depth.
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found"


i verified the CD checksum and it checks out ok.


has anyone managed to install Dapper on a Dell Latitude D620?

---

### Post by dragonflyFZX on 2006-10-06
lots of us:

[http://www.ubuntuforums.org/showthread.php?t=160679&highlight=d620](http://www.ubuntuforums.org/showthread.php?t=160679&highlight=d620)

---

### Post by gertmul on 2006-11-18
Use the second option as the cd is loaded. I think it says Run/Install in "safe graphics mode" or similar.

---

