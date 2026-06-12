---
title: "feisty problems with installing ati driver"
date: 2007-04-27
forum: Multimedia &amp; Video
---

### Post by yimingwuzere on 2007-04-27
I just installed feisty today and started installing all my basic programs and stuff. I can't get the ATi X800 driver to work though.

Following the guide at wiki.cchtml.com, I tried installing it via manual install since the Ubuntu way doesn't work (shows the following below when checking with fglrxinfo):
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20060815 AGP 1x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 6.5.2

So, I tried the manual way after removing the packages, reconfigure xserver blacklist fglrx module and restart. It all runs OK till the step where I type aticonfig --initial. This is the result:
```
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-1
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0xbfea5a10 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7d43f5b]
aticonfig[0x805bff7]
aticonfig[0x805c2a5]
aticonfig[0x8054528]
aticonfig[0x804985e]
aticonfig[0x80496cb]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7ceeebc]
aticonfig[0x8049601]
======= Memory map: ========
08048000-08067000 r-xp 00000000 08:02 707337     /usr/bin/aticonfig
08067000-0806a000 rw-p 0001e000 08:02 707337     /usr/bin/aticonfig
0806a000-0808b000 rw-p 0806a000 00:00 0          [heap]
b7ccb000-b7ccc000 rw-p b7ccb000 00:00 0 
b7ccc000-b7cce000 r-xp 00000000 08:02 1537386    /lib/tls/i686/cmov/libdl-2.5.so
b7cce000-b7cd0000 rw-p 00001000 08:02 1537386    /lib/tls/i686/cmov/libdl-2.5.so
b7cd0000-b7cd1000 rw-p b7cd0000 00:00 0 
b7cd1000-b7cd5000 r-xp 00000000 08:02 703296     /usr/lib/libXdmcp.so.6.0.0
b7cd5000-b7cd6000 rw-p 00003000 08:02 703296     /usr/lib/libXdmcp.so.6.0.0
b7cd6000-b7cd8000 r-xp 00000000 08:02 703285     /usr/lib/libXau.so.6.0.0
b7cd8000-b7cd9000 rw-p 00001000 08:02 703285     /usr/lib/libXau.so.6.0.0
b7cd9000-b7e14000 r-xp 00000000 08:02 1537380    /lib/tls/i686/cmov/libc-2.5.so
b7e14000-b7e15000 r--p 0013b000 08:02 1537380    /lib/tls/i686/cmov/libc-2.5.so
b7e15000-b7e17000 rw-p 0013c000 08:02 1537380    /lib/tls/i686/cmov/libc-2.5.so
b7e17000-b7e1a000 rw-p b7e17000 00:00 0 
b7e1a000-b7e3f000 r-xp 00000000 08:02 1537388    /lib/tls/i686/cmov/libm-2.5.so
b7e3f000-b7e41000 rw-p 00024000 08:02 1537388    /lib/tls/i686/cmov/libm-2.5.so
b7e41000-b7f2e000 r-xp 00000000 08:02 703279     /usr/lib/libX11.so.6.2.0
b7f2e000-b7f32000 rw-p 000ed000 08:02 703279     /usr/lib/libX11.so.6.2.0
b7f32000-b7f3f000 r-xp 00000000 08:02 703300     /usr/lib/libXext.so.6.4.0
b7f3f000-b7f40000 rw-p 0000d000 08:02 703300     /usr/lib/libXext.so.6.4.0
b7f40000-b7f41000 rw-p b7f40000 00:00 0 
b7f41000-b7f48000 r-xp 00000000 08:02 703322     /usr/lib/libXrender.so.1.3.0
b7f48000-b7f49000 rw-p 00006000 08:02 703322     /usr/lib/libXrender.so.1.3.0
b7f49000-b7f4e000 r-xp 00000000 08:02 703320     /usr/lib/libXrandr.so.2.1.0
b7f4e000-b7f4f000 rw-p 00005000 08:02 703320     /usr/lib/libXrandr.so.2.1.0
b7f4f000-b7f5a000 r-xp 00000000 08:02 1534144    /lib/libgcc_s.so.1
b7f5a000-b7f5b000 rw-p 0000a000 08:02 1534144    /lib/libgcc_s.so.1
b7f5b000-b7f5e000 rw-p b7f5b000 00:00 0 
b7f5e000-b7f77000 r-xp 00000000 08:02 1534101    /lib/ld-2.5.so
b7f77000-b7f79000 rw-p 00019000 08:02 1534101    /lib/ld-2.5.so
bfe91000-bfea7000 rw-p bfe91000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

```

I tried redoing this step by editing 'ati' in the driver section of xorg.conf with 'fglrx', and when that didn't work I used --force. When I use --force then enable video acceleration, I get a similar result as above.

If anything my ATi card is an X800 Pro.

---

### Post by Beliar on 2007-04-27
I have the same problem :(

---

### Post by GriffiN on 2007-04-27
same here, probably (dont know much about it) drivers are broken for feisty?

---

### Post by GriffiN on 2007-04-27
sorry for double post

ive tried almost everyguide out there and they all break my ubuntu

---

### Post by phidia on 2007-04-27
Have you tried the driver(s) at the ati site?

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

---

### Post by GriffiN on 2007-04-27
yep, tried it, and it also broke it, dunno if im doing something wrong or its just that my video card is not supported (x1900 series)

---

### Post by Beliar on 2007-04-27
I was talking about the official ati driver from the website.

---

### Post by GriffiN on 2007-04-27
i was referring to oficial files, with program called envy and other tutorials as well...
could it be that the drivers are not good from the start?

---

### Post by yimingwuzere on 2007-04-28
I managed to get it to work via the driver package, after countless attempts earlier with that and the official driver, no idea why though.

I guess there's a problem with xorg.conf that the driver hates, because the last thing I know before I got it to work was to edit it with reconfigure xserver-xorg, but I changed quite a number of graphic +monitor settings. I guess it didn't do a good option of selecting an ideal option as default?

---

### Post by blitzer on 2007-04-28
Add/Remove under Applications has it listed there.  Select the show drop down bar located in the upper right side.  Select All available applications >  To the left choose Systems Tools:  Look for  ATI binary X.Org driver:

> ATI binary X.Org driver

Video driver for ATI graphics accelerators 
Video driver for the ATI Radeon and FireGL graphics accelerators.
This version of the ATI driver officially supports:
• FireGL: V7350, V7300, V7200, V7100, V5200, V5100, V5000, V3400, V3300, V3200, V3100, X3-256, X3, X2-256, Z1-128, T2-128, X1-128, X1-256p
• FireMV: 2200 (Single card PCI-e configuration)
• Mobility FireGL: V5000, T2
• Mobility Radeon: X1800, X1600, X1400, X1300,[COLOR="Red"] X800[/COLOR], X700, X600, X300, 9800, 9600, 9550, 9500
• Radeon Xpress: 200M series, 1250 IGP, 200 series
• Radeon: X1900, X1800, X1600, X1300, X850, [COLOR="Red"]X800,[/COLOR] X700, X600, X550, X300, 9800, 9700, 9600, 9550, 9500
ATI All-in-Wonder variants of the above cards/chips are also supported, but video capture is not.
This package provides 2D display drivers and hardware accelerated OpenGL.
Version: 7.1.0-8.34.8+2.6.20.5-15.20 (xorg-driver-fglrx)

---

### Post by tamagoji on 2007-05-02
correct me if i'm wrong. but xorg in feisty is the 7.2 version. last version of the proprietary driver is able to work only under 7.1.. that's why i didn't use it. (it gave me problems with that).
anyway,  i have a similar problem with x300. but the installation goes well: it is during the reboot of xorg that the screen freezes (no chance to open a console).
-i tryed with the restricted driver manager
-i tryed with the manual installation both feisty and edgy.
sadly they worked in edgy perfectly, but are bad for feisty!

---

### Post by blitzer on 2007-05-02
This is correct.
> correct me if i'm wrong. but xorg in feisty is the 7.2 version. last version of the proprietary driver is able to work only under 7.1.. that's why i didn't use it. (it gave me problems with that).


The last supported Fglrx for the 9200SE was 8.28 for xorg 7.1 and below.  Thats why I'm not using Fglrx because Ati is not supporting for 7.2:( 

Did you try and set it up using ```
sudo dpkg-reconfigure xserver-xorg
``` and selecting Ati and all the rest default for the Open Source driver ?  This is what I had to do.

The X300 should be able to use the latest Fglrx driver in add remove or the Restricted Drivers Manager.

---

### Post by mats_rickard on 2007-05-02
I am also having problems with my ATI radeon R250 card.

I can not change update freq, it is locked at 60hz...

So I installed the "ATI binary X.Org driver". Nothing happened. Tried to reboot, no change.

I tried this > Did you try and set it up using
Code:

sudo dpkg-reconfigure xserver-xorg.conf



and got error message something like 
The package "xserver-xorg.conf" is not installed and no information is available

Yes, I am a linux newbie, not an experienced sysadmin.
But isn't there a easy-to-understand guide on how to configure ubuntu 7.0.4 for an ATI graphics card??? If so, please let me know.
Why is this simple configuration task so complex?

---

### Post by blitzer on 2007-05-02
Hi mats_rickard,

What do you get and post this back here with```
 glxinfo
``` if nothing then this```
 fglrxinfo
```

---

### Post by blitzer on 2007-05-02
Very sorry mats_rickard,

The code should have been ```
sudo dpkg-reconfigure xserver-xorg
```  and not the sudo dpgk-reconfigure [COLOR="Red"]xserver-xorg.conf[/COLOR]

---

