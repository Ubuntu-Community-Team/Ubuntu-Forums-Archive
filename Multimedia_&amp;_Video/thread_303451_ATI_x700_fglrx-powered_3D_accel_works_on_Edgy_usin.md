---
title: "ATI x700 fglrx-powered 3D accel works on Edgy using kernel *-386 but not *-generic!"
date: 2006-11-20
forum: Multimedia &amp; Video
---

### Post by LevTermen on 2006-11-20
Reported as launchpad bug #72555:
[https://launchpad.net/distros/ubuntu/+bug/72555](https://launchpad.net/distros/ubuntu/+bug/72555)

ATI x700 fglrx-powered 3D accel works on Edgy using kernel *-386 but not *-generic

A fully working 3D accel seems pretty hard to achieve using an ATI x700 GPU with the fglrx drivers under Edgy Eft.

Testing hardware and software: ASUS A6VA laptop powered with a PCIx ATI x700 GPU and a Pentium M CPU, with Edgy Eft installed and kernel 2.6.17-10-3-*.

I couldn't have it to work using standard packaged kernel 2.6.17-10-generic. The whole computer was slowed down. When launching an app from the Gnome dock, I could the see the shadow of the future window bear as a colored frame of the launcher icon and morph towards the frame of the actual window, the morphing being a translated homothecy.

Note: packages linux-restricted-modules-$(uname -r) and xorg-driver-fglrx were properly (re)installed during the whole Edgy install process. Plus, I didn't use the following commands but tweaked properly the /etc/X11/xorg.conf file:
```
$ sudo depmod -a
$ sudo aticonfig --initial
```

Then, I reminded having arrived to the same caveat back in the Dapper days, when I tried to install a kernel *-586 or *-686 instead of the working *-386, but without properly refreshing the drivers. So I decided to install now in Edgy kernel 2.6.17-10-3-386.

It works now!

------------------------------------------------------------------------------
Modifications of /etc/X11/xorg.conf based on the standard fglrx configuration:
```
# (...)
Section "Module"
 Load "bitmap"
 Load "dbe"
 Load "ddc"
 Load "dri"
 SubSection "extmod"
  Option "omit xfree86-dga"
 EndSubSection
 Load "freetype"
 Load "glx"
 Load "int10"
 Load "record"
 Load "type1"
 Load "v4l"
 Load "vbe"
EndSection
# (...)
Section "Device"
 Identifier "Generic Video Card"
 Driver "fglrx"
 BusID "PCI:1:0:0"
EndSection
# (...)
Section "Monitor"
 Identifier "Generic Monitor"
 Option "DPMS"
 HorizSync 30-85 # using the 4/3 resolution that is...
 VertRefresh 50-80 # ...just above the screen's max 1280x800
EndSection
# (...)
Section "Extensions"
 Option "Composite" "0" # "Disable" works as well
EndSection
```

------------------------------------------------------------------------------
Notice: no required mention of any of the following options:
```
# (...)
Section "Device"
 # (...)
 Option "BusType" "PCIE" # as used in Dapper
 # (...)
EndSection
# (...)
Section "Device
 # (...)
 Option "DPMS"
 #Option "MonitorLayout" "LVDS, NONE" # as used in Dapper
 Option "MonitorLayout" "LVDS, AUTO" # as recommended in Edgy
 # (...)
EndSection
```

------------------------------------------------------------------------------
```
$ dmesg | grep fglrx
fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[fglrx] Maximum main memory to use for locked dma buffers: 1899 MBytes.
[fglrx] module loaded - fglrx 8.28.8 [Aug 17 2006] on minor 0
[fglrx] total GART = 134217728
[fglrx] free GART = 118226944
[fglrx] max single GART = 118226944
[fglrx] total LFB = 127889408
[fglrx] free LFB = 119697408
[fglrx] max single LFB = 119697408
[fglrx] total Inv = 0
[fglrx] free Inv = 0
[fglrx] max single Inv = 0
[fglrx] total TIM = 0
```

------------------------------------------------------------------------------
Still persistent but harmless here:

```
$ cat /var/log/Xorg.0.log | grep "(EE)"
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
```

------------------------------------------------------------------------------
```
$ cat /var/log/Xorg.0.log | grep "(II)" | grep "fglrx" > XorgIIfglrx
```
(see bug page)

------------------------------------------------------------------------------

Bottom-line: finding the diffs from the config files of both kernel flavors might help track the problem.

I can post the misc error messages using the same /etc/X11/xorg.conf but kernel *-generic instead by request.

---

### Post by TurkVU on 2006-11-20
Looks like this be my problem - is there an easy way to change my kernel? Sorry, new to linux.

---

### Post by kosmic on 2006-11-20
Just enable "restricted" repos in synaptic or /etc/apt/sources.lst

and in a terminal type (only one command)

sudo apt-get install linux-686
or
sudo apt-get install linux-k7 (for atlhon processor, AMD single processor)
or
sudo apt-get install linux-686-smp (Intel dual processors)
or
sudo apt-get install linux-k7-smp (AMD dual processors)

---

### Post by TurkVU on 2006-11-20
Thanks, but after I do that how do I boot into the given kernel? The item doesn't show up automatically in my grub menu.lst...do I need to add it?

---

### Post by TurkVU on 2006-11-20
Ugh - got the other kernal working...but didn't help my xgl issues.](*,)

---

### Post by blaow on 2006-12-07
I am having the same problem.

Hardware: ATI x1400, intel core duo.

I got the generic kernel for SMP but with it I lose 3D accel, so now I must choose between 3D accel or losing one of my cores.  

I tried reinstalling fglrx and a bunch of other stuff, no luck.  
Here is the output from fglrxinfo and when I try to modprobe fglrx:

```

fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
```


```
sudo modprobe fglrx
FATAL: Error running install command for fglrx
```

---

