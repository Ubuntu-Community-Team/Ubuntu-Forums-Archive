---
title: "Video problem when booting Ubuntu USB HDD on a different PC"
date: 2007-06-28
forum: Multimedia &amp; Video
---

### Post by jairo_lopez on 2007-06-28
Hi,

I have Ubuntu installed on a USB HDD. Every time I boot Ubuntu on a different PC  I have to run "sudo dpkg-reconfigure -phigh xserver-xorg", because startx won't work. I get an EE Device not found.

Since I want to be able to switch my Ubuntu USB HDD between two PCs, is there a way to reconfigure automatically the video card?

Thanks 

Jairo

---

### Post by jairo_lopez on 2007-06-28
The error I receive is: 


X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux mylinux 2.6.20-16-386 #2 Thu Jun 7 20:16:13 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun 28 21:46:08 2007
(==) Using config file: "/etc/X11/xorg.conf"
(EE) No devices detected.

Fatal server error:
no screens found

---

