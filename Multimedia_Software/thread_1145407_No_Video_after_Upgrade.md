---
title: "No Video after Upgrade"
date: 2009-05-01
forum: Multimedia Software
---

### Post by tobey1 on 2009-05-01
I just upgraded to version 9 and I no longer have video.  My monitor only shows Out of Range.  Any thoughts/Help?

---

### Post by overdrank on 2009-05-01
> **tobey1 said:**
> I just upgraded to version 9 and I no longer have video.  My monitor only shows Out of Range.  Any thoughts/Help?

Hi and are you still using the ```
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc 3D Rage Pro AGP 1X/2X 
``` from your previous thread?
Have you tried booting into recovery mode and using the xfix option?

---

### Post by tobey1 on 2009-05-01
That is the same controller.  WHen I try the xfix, It only sets up the keyboard.  Does nothing with the Monitor/video at all during the xfix.

Any idea on how to re-install?  I created a CD form the ISO, but my PC is not reading the CD for install.

---

### Post by tobey1 on 2009-05-04
I tried these commands 
- sudo apt-get update
- sudo apt-get dist-upgrade
- sudo dpkg-reconfigure -phigh xserver-xorg
- sudo dpkg-reconfigure xserver-xorg (Note, never get an option to configure Video, only Keyboard)


and then startx and get this:

~# startx

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux joe-desktop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd)
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon May  4 22:53:38 2009
(==) Using config file: "/etc/X11/xorg.conf"


Backtrace:
0: /usr/bin/X11/X(xorg_backtrace+0x3b) [0x813518b]
1: /usr/bin/X11/X(xf86SigHandler+0x55) [0x80c7be5]
2: [0xb80b3400]
3: /usr/lib/xorg/modules/extensions//libdri.so(DRIScreenInit+0xd0) [0xb79cc570]
4: /usr/lib/xorg/modules/drivers//mach64_drv.so(ATIDRIScreenInit+0x2b9) [0xb799e309]
5: /usr/lib/xorg/modules/drivers//mach64_drv.so(ATIScreenInit+0x1ef) [0xb799a11f]
6: /usr/bin/X11/X(AddScreen+0x19d) [0x8071a1d]
7: /usr/bin/X11/X(InitOutput+0x206) [0x80afb06]
8: /usr/bin/X11/X(main+0x1e1) [0x8072111]
9: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7c85775]
10: /usr/bin/X11/X [0x80717a1]
Saw signal 11.  Server aborting.
 ddxSigGiveUp: Closing log
 ddxSigGiveUp: re-raising 11
giving up.
xinit:  Connection refused (errno 111):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.


Any ideas?

xorg.conf for reference:
[I]
Section "Device"
        Identifier      "Configured Video Device"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection[/I]

---

