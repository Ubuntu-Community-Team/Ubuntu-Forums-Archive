---
title: "poor graphics performance on ati 9800 pro"
date: 2007-03-01
forum: Multimedia &amp; Video
---

### Post by mr.v. on 2007-03-01
Hi all--

I just got a new computer, P4 1.9 GHz, 512MB of RDRAM, and an ATI 9800pro videocard. The video performance is pretty bad overall. Things like scrolling and new windows opening are pretty sluggish. Also, although I know glxgears isn't a benchmark, it's only giving me ~530 fps.

I've pretty much always used NVidia cards before and I've never had any linux driver issues. However, with this computer I was using the X "ati" driver for a while but I want 3D acceleration for OpenGL stuff and it was fairly slow too. Using the "radeon" driver hard-locks the computer after a bit of use so that's out. So I installed the proprietary "fglrx" driver just from the synaptic package manager but it's unacceptably slow too.

Currently I'm using Ubuntu 6.10, kernel 2.6.17-11-generic and have the linux-restricted-modules-2.6.17-11-generic restricted modules installed as well as the xorg-driver-fglrx 7.1.0-8.28.8+2.6.17.7-11.1

I've ensured that the xorg.conf file is using **Driver "fglrx"** and turned the Composite module off with **Option "Composite" "Disable" ** under **Section "Extensions"**

I do have direct rendering as reported by glxinfo...here's the relevant glxinfo
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
...
client glx vendor string: ATI
client glx version string: 1.3
...
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.6011 (8.28.8)
```

Here's my question...I don't have Load "glcore" anywhere in my xorg.conf but my Xorg.0.log reports it being loaded. Should I disable it somehow? And if so how? I thought simply not having **Load "glcore"** wouldn't load it. In this version of X do I have to specifically disable it somehow?

and here's some of Xorg.0.log
```

(--) PCI:*(1:0:0) ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] rev 0, Mem @ 0xf0000000/27, 0xff8f0000/16, I/O @ 0xec0
0/8, BIOS @ 0x80000000/17
(--) PCI: (1:0:1) ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary) rev 0, Mem @ 0xe8000000/27, 0xff8e0000/16
...
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
...
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
...
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
...(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
...
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
        compiled for 7.1.0, module version = 8.28.8
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 1.0
...
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.28.8
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.28g1                           
(II) ATI Proprietary Linux Driver Build Date: Aug 17 2006 09:28:12
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.28.1.1.2.3-driver-lnx-x86-x86_64-287161
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset RADEON 9800 PRO (R350 4E48) found
...
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
```

There's lots more but I don't want to completely stop someone from viewing...
other things that are relevant is the output of the following
```
:~$ lsmod | grep -i 'video\|agpgart\|drm\|fglrx'
```
produces the following output ```
fglrx                 406988  8 
video                  17540  0 
agpgart                34888  2 fglrx,intel_agp
```

so any ideas what I need to do to get this thing to run faster?

Thanks for the help!

---

### Post by doobydave on 2007-03-02
Cant really help you a lot but reakon i have same problem.
[http://ubuntuforums.org/showthread.php?t=255929&page=82](http://ubuntuforums.org/showthread.php?t=255929&page=82)

Have been messing around for over a week now.... The frustrATIon!!

---

