---
title: "Disable target rendering lockmode, setting direcdrawrenderer etc."
date: 2010-12-14
forum: Multimedia Software
---

### Post by morefeo on 2010-12-14
> To get the game running blistering fast (and I mean faster than native windows) **disable target rendering lockmode and set the directdrawrenderer to opengl. **

Then start a separate xwindow like this: startx -- :1 -depth 16 
Run the game in there. Like this, the color conversion is no longer nescesary and RO will run like lightning even in high res :) 

I take this from winehq.org for running a game properly, but I don't know how to do what the bold text says. In addition, while I try to do what second paragraph says, console returns this error:

> X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux zen 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=cd392236-cbbe-4ddc-b645-9b5e7ece43ce ro quiet splash
Build Date: 16 September 2010  06:18:41PM
xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.18.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Tue Dec 14 17:59:53 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(WW) fglrx: No matching Device section for instance (BusID PCI:0@2:0:1) found
(EE) fglrx(0): Given depth (16) is not supported by fglrx driver
(EE) fglrx(0): PreInitVisual failed
(EE) fglrx(0): PreInit failed
SetVBEMode failed
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.1.log" for additional information.

 ddxSigGiveUp: Closing log
giving up.
xinit:  No such file or directory (errno 2):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.


I'm running Ubuntu 10.10 64 bits with fglrx driver, everything works fine (accelerated 3d and compiz).

How do I disable target rendering and set the direct draw renderer? I've search a bit and I didn't find anything.

Edit: Ok, I found fglrx doesn't support depth 16, normal users can't run x sessions and my root can't run wine applications, so that's all.

Any help about the first sentence?

---

