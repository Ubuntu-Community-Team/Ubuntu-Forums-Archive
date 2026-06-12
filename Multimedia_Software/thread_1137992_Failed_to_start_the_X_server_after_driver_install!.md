---
title: "Failed to start the X server after driver install!?"
date: 2009-04-26
forum: Multimedia Software
---

### Post by morbid_bean on 2009-04-26
I installed the drivers for my Ati Radeon 9250 from the official website ([http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.26&lang=English&rev=9.3&ostype=Linux%20x86](http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.26&lang=English&rev=9.3&ostype=Linux%20x86))

Everything works out just fine until it comes to the part where I restart the computer....now ubuntu starts up with this...

"Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly .  Would you like to view the X server output to diagnose the problem?."  <YES>  <NO>

I Picked Yes

```
X.org X server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.624-19-server i686 Ubuntu
Current Operating System: Linux monster 2.6.27-11generic #1 SMP Wed
Apr 1 20:57:48 UTC 2009 i686
Build Date: 09 March 2009 10:48:54AM
xorg-server 2:1.5.2-2ubuntu3.1 (build@rothera.buildd)
             Before reporting problems, check http://wiki.x.org
             to make sure that you have the latest version.
Module Loader present
Markers: (--) Probed, (**) from config file, (==) default setting,
             (++) from command line, (!!) notice, (II informational,
             (WW) warning, (EE error, (NI not implemented, (??) unknown.
(==) Log file: "var/log/Xorg.0.log", Time Sun Apr 26 00:32:19 2009
(==) Using config file: "/etc/X11/xorg.conf"

Backtrace:
0: /usr/bin/x(xf86SigHandler+0x79) [0x80c3019]
1: [0xb7fc0400]
2: /usr/lib/xorg/modules/drivers//radeon_drv.so [0xb7a39c27]
3: /usr/lib/xorg/modules/drivers//radeon_drv.so [0xb7a0755a]
4: /usr/lib/xorg/modules/drivers//radeon_drv.so [0xb7a0a4fc]
5: /usr/bin/X (InitOutput+0x96f) [0x80aac9f]
6: /usr/bin/X (main+0x279) [0x8071b19]
7: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7bc4685]
8: /usr/bin/X [0x8071101]
Saw signal 11.  Server aborting.

```

Then I hit the ok button

"Would you like to view the detailed X server output as well?" <YES> <NO>

Then it shows a ton of detailed stuff....

Whats going on here?!?!:confused::confused::confused:

---

### Post by morbid_bean on 2009-04-26
kept trying to run 

dpkg-reconfigure xserver-xorg
and
sudo dpkg-reconfigure -phigh xserver-xorg
 

But nothing... :( :(

---

### Post by morbid_bean on 2009-04-28
Fresh install of the new ubuntu 9.04 and problem solved!!!!!!!\\:D/

---

