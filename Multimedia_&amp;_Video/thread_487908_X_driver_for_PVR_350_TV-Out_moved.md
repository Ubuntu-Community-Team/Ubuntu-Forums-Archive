---
title: "X driver for PVR 350 TV-Out moved?"
date: 2007-06-29
forum: Multimedia &amp; Video
---

### Post by Chuckels550 on 2007-06-29
I am installing Mythtv on Feisty 7.04 and want to use the PVR 350 TV-Out.  I have been following the excellent documentation on Ubuntu site, but the following command gets me a 404 Not Found error:

wget -O ivtvdev_drv.so [http://www.hellion.org.uk/ivtv/debian/ivtvdev_drv.so~i386](http://www.hellion.org.uk/ivtv/debian/ivtvdev_drv.so~i386)

I tried going to his site and downloading from a different directory, but the driver I get won't load -  ELF error.  Does anyone have another location for downloading the ivtvdev_drv.so driver that's more reliable?

I am running kernel 2.6.20-16-generic for Feisty 7.04, AMD athlon 64 3500+, with a Hauppauge WinPVR 350 TV Card and an Asus Nvidia N7600GS Silent graphics card.

Here is the result of starting X:

sudo startx
xauth:  creating new authority file /home/edowd/.serverauth.6208
xauth:  creating new authority file /home/edowd/.Xauthority
xauth:  creating new authority file /home/edowd/.Xauthority

X: warning; process set to priority -1 instead of requested priority 0

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux mythtv-host 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jul  1 10:44:24 2007
(==) Using config file: "/etc/X11/xorg.conf"
dlopen: /usr/lib/xorg/modules/drivers//ivtvdev_drv.so: invalid ELF header
(EE) Failed to load /usr/lib/xorg/modules/drivers//ivtvdev_drv.so
(EE) Failed to load module "ivtvdev" (loader failed, 7)
(EE) No devices detected.

Fatal server error:
no screens found
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 0 requests (0 known processed) with 0 events remaining.


Issue resolved for me after i had someone with more Linux experience go to the www/hellion.uk site and find the X driver, which is really a shared object.

---

