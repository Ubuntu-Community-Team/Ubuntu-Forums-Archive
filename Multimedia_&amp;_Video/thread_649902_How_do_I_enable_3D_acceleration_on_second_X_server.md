---
title: "How do I enable 3D acceleration on second X server?"
date: 2007-12-25
forum: Multimedia &amp; Video
---

### Post by Dreamlocked on 2007-12-25
Hello.

With the latest ATI drivers, I am finally able to start a parallel X server using the sudo X or xinit commands (with previous drivers, the computer would hang), and can easily access it with <CTRL> + <ALT> + F9.

However, on said X server, I am unable to run programs that require 3D acceleration, I just get a blank window and on certain occasions, I have to do a hard reboot. Normal applications (open office) work fine.

This is the output I get upon starting the X server :

```

me@dreamlocked:~$ sudo X :3 -ac

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux dreamlocked 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686
Build Date: 29 September 2007
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.3.log", Time: Tue Dec 25 23:00:59 2007
(==) Using config file: "/etc/X11/xorg.conf"

(II) Module already built-in
(II) Module already built-in
(EE) fglrx(0): [agp] Failed to remmap MC AGP aperture base!
[atiddx] ASYNCIO init succeed!
Atom 4, CARD32 4, unsigned long 4
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
Synaptics DeviceInit called
SynapticsCtrl called.
Synaptics DeviceOn called
Synaptics DeviceOff called

```

It might be interesting to note that the line 
```

(EE) fglrx(0): [agp] Failed to remmap MC AGP aperture base!

```
... can also be found in my /var/log/Xorg.0.log file, which is the log file for my main display. And as I can use 3D acceleration on my main Display, it probably isn't the problem.


I attached the xorg.conf.

System specs :
OS : Xubuntu Gutsy (7.10).
Processor : Pentium M 1.6 GHz.
Graphics : ATI Mobility Radeon 9700, 128Mb
RAM : 256 + 1024

---

