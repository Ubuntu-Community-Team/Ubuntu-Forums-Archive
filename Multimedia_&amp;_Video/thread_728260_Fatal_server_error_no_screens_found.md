---
title: "Fatal server error: no screens found"
date: 2008-03-18
forum: Multimedia &amp; Video
---

### Post by mabsalon on 2008-03-18
I have installed Ubuntu 7.10 on a SunFire T2000 server with a Matrox G550 video card, connected to a Dell 1900FP monitor. I can't get the gui to work and my monitor is in powersafe mode. When I do a 'startx', I get the following error......PLEASE HELP!! I would really appreciate it. Also, how can i check if the drivers for my graphics card is installed. When I do a 'lspci' it does list the Matrox G550 graphics card using a vga driver


X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux asiaminor 2.6.22-14-sparc64-smp #1 SMP Sun Oct 14 22:55:24 GMT 2007 sparc64
Build Date: 18 January 2008
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Mar 18 16:02:48 2008
(==) Using config file: "/etc/X11/xorg.conf"
(EE) No devices detected.

Fatal server error:
no screens found
XIO:  fatal IO error 54 (Connection reset by peer) on X server ":0.0"
      after 0 requests (0 known processed) with 0 events remaining.

---

### Post by dmitriyp13 on 2008-03-18
Please post your /etc/X11/xorg.conf file.  It sounds like X was misconfigured.

---

### Post by taurus on 2008-03-18
Or you can reconfigure your X server again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by themijs on 2008-03-19
same problem here.
Did you try the cmd?

---

