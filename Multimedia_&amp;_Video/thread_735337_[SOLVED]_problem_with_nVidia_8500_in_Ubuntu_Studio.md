---
title: "[SOLVED] problem with nVidia 8500 in Ubuntu Studio 8.04 beta"
date: 2008-03-25
forum: Multimedia &amp; Video
---

### Post by sorin.stirbu on 2008-03-25
hey guys ... some days ago I have dled the new beta [the ubuntu studio one] from hardy and installed it ... all the things went nice and easy but I have some problems with my nVidia 8500GT top driver.

It goes like this:
#1 - I've installed the driver in the simple way [the restricted drivers in the System section of the menu]
#2 - I've installed the driver from synaptic
#3 - I've installed the driver from command line
#4 - I've installed the driver with Envy

...they all had the same result: a big black screen after boot...

I read the Sticky: **HOWTO: Install the NVIDIA driver on ANY stable version of Ubuntu** but nothing ussefull found... 

do you have any ideea about this ??? can anyone help me ???

Thank you in advance !!

---

### Post by sorin.stirbu on 2008-03-29
nobody ? :(

---

### Post by bhaverkamp on 2008-04-07
Same problem here.

Fridays updates nuked my computer. No luck getting it working.

I have tried going back to Gutsy and things are no better there.

I am stuck. The best I can get is 640x480.

This sucks!

---

### Post by Plasma_NZ on 2008-04-07
Ok... not entirely sure if this may help...

I run 2 8500 GT's  with 4 screens..

this is how i installed my drivers...

I went to nvidia and downloaded the linux driver.. then followed these directions

```
1. In ubuntu press "ctrl + alt + F1"
2. Login to your user account (not root)
3. sudo /etc/init.d/gdm stop
4. cd /home/account_name/Desktop - or where u downloaded the driver 2
5. sudo sh NVIDIA_DRIVER_PACKAGE_NAME
6. Follow directions from installer
7. once done... type "startx" to boot back into GUI 
8. in terminal type "sudo nvidia-settings" and configure accordingly to your liking..
```

Good Luck..

---

### Post by sorin.stirbu on 2008-04-08
I tried the directions that u gave me but it end up with an error:

```
Error:
Unable to find the kernel source tree for the currently running kernel. 
Please make sure you have installed the kernel source files for your kernel
and that they are properly configured.
```

---

### Post by jecker on 2008-04-09
Can you post the /var/log/Xorg.0.log logs?

---

### Post by sorin.stirbu on 2008-04-09
I could but it is very big...1125 lines :|

---

### Post by jecker on 2008-04-10
Please zip the log file and post it. Also have you tried to install the driver from restricted drivers in Ubuntu?

---

### Post by sorin.stirbu on 2008-04-10
> **sorin.stirbu said:**
> 
#1 - I've installed the driver in the simple way [the restricted drivers in the System section of the menu]
#2 - I've installed the driver from synaptic
#3 - I've installed the driver from command line
#4 - I've installed the driver with Envy


i'll zip it as soon as I get home [@ work right know]

---

### Post by haggus on 2008-04-10
> **sorin.stirbu said:**
> I tried the directions that u gave me but it end up with an error:

```
Error:
Unable to find the kernel source tree for the currently running kernel. 
Please make sure you have installed the kernel source files for your kernel
and that they are properly configured.
```
 Use Synaptic package manager and search linux. Then look for linux-headers that match your linux-kernel which can be found using uname -r then you should compile nvidia without errors.

---

### Post by sorin.stirbu on 2008-04-11
ok....done that...it runs....but at reboot the same black screen :( ... 

question: i saw that my kernel is 2.6.24-15-rt ..... what's with the "rt" ???

about this problem ... I decided that I'll reinstall Ubuntu...when it is released...maybe the problem is fixed until then .....10x for the help...

---

### Post by rocketman768 on 2008-04-11
The rt is for "realtime" b/c audio recording programs need to run as close to real time as possible. Please post the /var/log/Xorg.0.log so we can review it. Basically, you are looking for any lines that start with "(EE)".

---

### Post by sorin.stirbu on 2008-04-11
the log :
```



This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu7)
Current Operating System: Linux overdrive 2.6.24-15-rt #1 SMP PREEMPT RT Tue Apr 8 02:25:55 UTC 2008 i686
Build Date: 09 April 2008  12:39:59PM
 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Apr 11 11:21:15 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "<default pointer>"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
    Using the default mouse configuration.
(==) The core keyboard device wasn't specified explicitly in the layout.
    Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.3
    X.Org Video Driver: 2.0
    X.Org XInput driver : 2.0
    X.Org Server Extension : 0.3
    X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2580 card 17f2,2580 rev 04 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2581 card 0000,0000 rev 04 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,2658 card 17f2,2658 rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2659 card 17f2,2659 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,265a card 17f2,265a rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,265b card 17f2,265b rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,265c card 17f2,265c rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev d3 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2640 card 17f2,2640 rev 03 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,2651 card 17f2,2651 rev 03 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,266a card 17f2,266a rev 03 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0421 card 1043,8256 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:00:0: chip 1106,3106 card 17f2,1402 rev 8b class 02,00,00 hdr 00
(II) PCI: 02:04:0: chip 1106,3038 card 1106,3038 rev 62 class 0c,03,00 hdr 80
(II) PCI: 02:04:1: chip 1106,3038 card 1106,3038 rev 62 class 0c,03,00 hdr 80
(II) PCI: 02:04:2: chip 1106,3104 card 1106,3104 rev 65 class 0c,03,20 hdr 80
(II) PCI: 02:05:0: chip 1106,3038 card 1106,3038 rev 61 class 0c,03,00 hdr 80
(II) PCI: 02:05:1: chip 1106,3038 card 1106,3038 rev 61 class 0c,03,00 hdr 80
(II) PCI: 02:05:2: chip 1106,3104 card 1106,3104 rev 63 class 0c,03,20 hdr 80
(II) PCI: 02:0a:0: chip 1102,0002 card 1102,8064 rev 07 class 04,01,00 hdr 80
(II) PCI: 02:0a:1: chip 1102,7002 card 1102,0020 rev 07 class 09,80,00 hdr 80
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
    [0] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
    [0] -1    0    0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
    [0] -1    0    0xfb000000 - 0xfcffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
    [0] -1    0    0xb0000000 - 0xcfffffff (0x20000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
    [0] -1    0    0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
    [0] -1    0    0xfde00000 - 0xfdefffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
    [0] -1    0    0xfdd00000 - 0xfddfffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation GeForce 8500 GT rev 161, Mem @ 0xfb000000/24, 0xb0000000/28, 0xce000000/0, I/O @ 0xdf00/7
(II) Addressable bus resource ranges are
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
    [1] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
    [0] -1    0    0xfdefd000 - 0xfdefd0ff (0x100) MX[B]
    [1] -1    0    0xfdefe000 - 0xfdefe0ff (0x100) MX[B]
    [2] -1    0    0xfdeff000 - 0xfdeff0ff (0x100) MX[B]
    [3] -1    0    0xfdfff000 - 0xfdfff3ff (0x400) MX[B]
    [4] -1    0    0xce000000 - 0xce000000 (0x1) MX[B](B)
    [5] -1    0    0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
    [6] -1    0    0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
    [7] -1    0    0x0000e900 - 0x0000e907 (0x8) IX[B]
    [8] -1    0    0x0000ea00 - 0x0000ea1f (0x20) IX[B]
    [9] -1    0    0x0000eb00 - 0x0000eb1f (0x20) IX[B]
    [10] -1    0    0x0000ec00 - 0x0000ec1f (0x20) IX[B]
    [11] -1    0    0x0000ed00 - 0x0000ed1f (0x20) IX[B]
    [12] -1    0    0x0000ee00 - 0x0000ee1f (0x20) IX[B]
    [13] -1    0    0x0000ef00 - 0x0000efff (0x100) IX[B]
    [14] -1    0    0x00000500 - 0x0000051f (0x20) IX[B]
    [15] -1    0    0x0000fb00 - 0x0000fb0f (0x10) IX[B]
    [16] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[B]
    [17] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[B]
    [18] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[B]
    [19] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[B]
    [20] -1    0    0x0000fc00 - 0x0000fc1f (0x20) IX[B]
    [21] -1    0    0x0000fd00 - 0x0000fd1f (0x20) IX[B]
    [22] -1    0    0x0000fe00 - 0x0000fe1f (0x20) IX[B]
    [23] -1    0    0x0000ff00 - 0x0000ff1f (0x20) IX[B]
    [24] -1    0    0x0000df00 - 0x0000df7f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
    [0] -1    0    0xfdefd000 - 0xfdefd0ff (0x100) MX[B]
    [1] -1    0    0xfdefe000 - 0xfdefe0ff (0x100) MX[B]
    [2] -1    0    0xfdeff000 - 0xfdeff0ff (0x100) MX[B]
    [3] -1    0    0xfdfff000 - 0xfdfff3ff (0x400) MX[B]
    [4] -1    0    0xce000000 - 0xce000000 (0x1) MX[B](B)
    [5] -1    0    0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
    [6] -1    0    0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
    [7] -1    0    0x0000e900 - 0x0000e907 (0x8) IX[B]
    [8] -1    0    0x0000ea00 - 0x0000ea1f (0x20) IX[B]
    [9] -1    0    0x0000eb00 - 0x0000eb1f (0x20) IX[B]
    [10] -1    0    0x0000ec00 - 0x0000ec1f (0x20) IX[B]
    [11] -1    0    0x0000ed00 - 0x0000ed1f (0x20) IX[B]
    [12] -1    0    0x0000ee00 - 0x0000ee1f (0x20) IX[B]
    [13] -1    0    0x0000ef00 - 0x0000efff (0x100) IX[B]
    [14] -1    0    0x00000500 - 0x0000051f (0x20) IX[B]
    [15] -1    0    0x0000fb00 - 0x0000fb0f (0x10) IX[B]
    [16] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[B]
    [17] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[B]
    [18] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[B]
    [19] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[B]
    [20] -1    0    0x0000fc00 - 0x0000fc1f (0x20) IX[B]
    [21] -1    0    0x0000fd00 - 0x0000fd1f (0x20) IX[B]
    [22] -1    0    0x0000fe00 - 0x0000fe1f (0x20) IX[B]
    [23] -1    0    0x0000ff00 - 0x0000ff1f (0x20) IX[B]
    [24] -1    0    0x0000df00 - 0x0000df7f (0x80) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xfdefd000 - 0xfdefd0ff (0x100) MX[B]
    [5] -1    0    0xfdefe000 - 0xfdefe0ff (0x100) MX[B]
    [6] -1    0    0xfdeff000 - 0xfdeff0ff (0x100) MX[B]
    [7] -1    0    0xfdfff000 - 0xfdfff3ff (0x400) MX[B]
    [8] -1    0    0xce000000 - 0xce000000 (0x1) MX[B](B)
    [9] -1    0    0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
    [10] -1    0    0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
    [11] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [12] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [13] -1    0    0x0000e900 - 0x0000e907 (0x8) IX[B]
    [14] -1    0    0x0000ea00 - 0x0000ea1f (0x20) IX[B]
    [15] -1    0    0x0000eb00 - 0x0000eb1f (0x20) IX[B]
    [16] -1    0    0x0000ec00 - 0x0000ec1f (0x20) IX[B]
    [17] -1    0    0x0000ed00 - 0x0000ed1f (0x20) IX[B]
    [18] -1    0    0x0000ee00 - 0x0000ee1f (0x20) IX[B]
    [19] -1    0    0x0000ef00 - 0x0000efff (0x100) IX[B]
    [20] -1    0    0x00000500 - 0x0000051f (0x20) IX[B]
    [21] -1    0    0x0000fb00 - 0x0000fb0f (0x10) IX[B]
    [22] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[B]
    [23] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[B]
    [24] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[B]
    [25] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[B]
    [26] -1    0    0x0000fc00 - 0x0000fc1f (0x20) IX[B]
    [27] -1    0    0x0000fd00 - 0x0000fd1f (0x20) IX[B]
    [28] -1    0    0x0000fe00 - 0x0000fe1f (0x20) IX[B]
    [29] -1    0    0x0000ff00 - 0x0000ff1f (0x20) IX[B]
    [30] -1    0    0x0000df00 - 0x0000df7f (0x80) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  169.12  Thu Feb 14 18:45:56 PST 2008
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
    compiled for 1.4.0.90, module version = 2.1.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) Matched nv from file name nv.ids in autoconfig
(==) Matched nv for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 2.1.8
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
    compiled for 1.4.0, module version = 1.2.3
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
    compiled for 1.4.0, module version = 1.2.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 2.0
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
    Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
    Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
    GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
    GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
    Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
    GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
    GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
    GeForce4 440 Go 64M, Quadro NVS, Quadro4 500 GoGL,
    GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
    GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
    GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
    Quadro4 NVS 280 SD, Quadro4 380 XGL, Quadro NVS 50 PCI,
    GeForce4 448 Go, GeForce4 MX Integrated GPU, GeForce3,
    GeForce3 Ti 200, GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600,
    GeForce4 Ti 4400, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
    Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
    GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
    Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
    GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
    GeForce FX 5600 Ultra, GeForce FX 5600, GeForce FX 5600XT,
    GeForce FX Go5600, GeForce FX Go5650, Quadro FX Go700,
    GeForce FX 5200, GeForce FX 5200 Ultra, GeForce FX 5200,
    GeForce FX 5200LE, GeForce FX Go5200, GeForce FX Go5250,
    GeForce FX 5500, GeForce FX 5100, GeForce FX Go5200 32M/64M,
    Quadro NVS 55/280 PCI, Quadro FX 500/600 PCI,
    GeForce FX Go53xx Series, GeForce FX Go5100, GeForce FX 5900 Ultra,
    GeForce FX 5900, GeForce FX 5900XT, GeForce FX 5950 Ultra,
    GeForce FX 5900ZT, Quadro FX 3000, Quadro FX 700,
    GeForce FX 5700 Ultra, GeForce FX 5700, GeForce FX 5700LE,
    GeForce FX 5700VE, GeForce FX Go5700, GeForce FX Go5700,
    Quadro FX Go1000, Quadro FX 1100, GeForce 6800 Ultra, GeForce 6800,
    GeForce 6800 LE, GeForce 6800 XE, GeForce 6800 XT, GeForce 6800 GT,
    GeForce 6800 GT, GeForce 6800 GS, GeForce 6800 XT, Quadro FX 4000,
    GeForce 6800 GS, GeForce 6800, GeForce 6800 LE, GeForce 6800 XT,
    GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400,
    Quadro FX 3450/4000 SDI, Quadro FX 1400, GeForce 6600 GT,
    GeForce 6600, GeForce 6600 LE, GeForce 6600 VE, GeForce Go 6600,
    GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL,
    GeForce Go 6600, GeForce Go 6600 GT, Quadro FX 550, Quadro FX 550,
    Quadro FX 540, GeForce 6200, GeForce 6500,
    GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
    GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
    GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 6800,
    GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200,
    GeForce 6200 A-LE, GeForce 7800 GTX, GeForce 7800 GTX,
    GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI, GeForce Go 7800,
    GeForce Go 7800 GTX, Quadro FX 4500, GeForce 7300 LE,
    GeForce 7300 SE, GeForce Go 7200, GeForce Go 7300, GeForce Go 7400,
    GeForce Go 7400 GS, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M,
    GeForce 7500 LE, Quadro FX 350, GeForce 7300 GS, GeForce 7600 GT,
    GeForce 7600 GS, GeForce 7300 GT, GeForce 7600 LE, GeForce 7300 GT,
    GeForce Go 7700, GeForce Go 7600, GeForce Go 7600 GT,
    Quadro NVS 300M, GeForce Go 7900 SE, Quadro FX 550M, Quadro FX 560,
    GeForce 7900 GTX, GeForce 7900 GT, GeForce 7900 GS,
    GeForce Go 7900 GS, GeForce Go 7900 GTX, Quadro FX 2500M,
    Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500, Quadro FX 1500,
    Quadro FX 4500 X2, GeForce 6150, GeForce 6150 LE, GeForce 6100,
    GeForce Go 6150, GeForce Go 6100, GeForce 8800 GTX, GeForce 8800 GTS,
    GeForce 8800 Ultra, Quadro FX 5600, Quadro FX 4600, GeForce 8600 GTS,
    GeForce 8600 GT, GeForce 8600 GT, GeForce 8400 GS, GeForce 8600M GT,
    GeForce 8700M GT, Quadro FX 370, Quadro NVS 320M, Quadro FX 570M,
    Quadro FX 1600M, Quadro FX 570, Quadro FX 1700, GeForce 8500 GT,
    GeForce 8400 GS, GeForce 8300 GS, GeForce 8400 GS, GeForce 8600M GS,
    GeForce 8400M GT, GeForce 8400M GS, GeForce 8400M G, Quadro NVS 140M,
    Quadro NVS 130M, Quadro NVS 135M, Quadro FX 360M, Quadro NVS 290,
    GeForce 8800 GT, GeForce 8800 GS, GeForce 8800 GS, GeForce 8800 GT,
    Quadro FX 3700, GeForce 9600 GT, GeForce 8400 GS
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset GeForce 8500 GT found
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xfdefd000 - 0xfdefd0ff (0x100) MX[B]
    [5] -1    0    0xfdefe000 - 0xfdefe0ff (0x100) MX[B]
    [6] -1    0    0xfdeff000 - 0xfdeff0ff (0x100) MX[B]
    [7] -1    0    0xfdfff000 - 0xfdfff3ff (0x400) MX[B]
    [8] -1    0    0xce000000 - 0xce000000 (0x1) MX[B](B)
    [9] -1    0    0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
    [10] -1    0    0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
    [11] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [12] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [13] -1    0    0x0000e900 - 0x0000e907 (0x8) IX[B]
    [14] -1    0    0x0000ea00 - 0x0000ea1f (0x20) IX[B]
    [15] -1    0    0x0000eb00 - 0x0000eb1f (0x20) IX[B]
    [16] -1    0    0x0000ec00 - 0x0000ec1f (0x20) IX[B]
    [17] -1    0    0x0000ed00 - 0x0000ed1f (0x20) IX[B]
    [18] -1    0    0x0000ee00 - 0x0000ee1f (0x20) IX[B]
    [19] -1    0    0x0000ef00 - 0x0000efff (0x100) IX[B]
    [20] -1    0    0x00000500 - 0x0000051f (0x20) IX[B]
    [21] -1    0    0x0000fb00 - 0x0000fb0f (0x10) IX[B]
    [22] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[B]
    [23] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[B]
    [24] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[B]
    [25] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[B]
    [26] -1    0    0x0000fc00 - 0x0000fc1f (0x20) IX[B]
    [27] -1    0    0x0000fd00 - 0x0000fd1f (0x20) IX[B]
    [28] -1    0    0x0000fe00 - 0x0000fe1f (0x20) IX[B]
    [29] -1    0    0x0000ff00 - 0x0000ff1f (0x20) IX[B]
    [30] -1    0    0x0000df00 - 0x0000df7f (0x80) IX[B](B)
(WW) ****INVALID MEM ALLOCATION**** b: 0xce000000 e: 0xce000000 correcting
(II) window:
    [0] -1    0    0xfb000000 - 0xfcffffff (0x2000000) MX[B]
(II) resSize:
(II) window fixed:
    [0] -1    0    0xfb000000 - 0xfcffffff (0x2000000) MX[B]
(II) resource ranges after probing:
    [0] -1    0    0xfb000000 - 0xfb000000 (0x1) MX[B](B)
    [1] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [2] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [3] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [4] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [5] -1    0    0xfdefd000 - 0xfdefd0ff (0x100) MX[B]
    [6] -1    0    0xfdefe000 - 0xfdefe0ff (0x100) MX[B]
    [7] -1    0    0xfdeff000 - 0xfdeff0ff (0x100) MX[B]
    [8] -1    0    0xfdfff000 - 0xfdfff3ff (0x400) MX[B]
    [9] -1    0    0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
    [10] -1    0    0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
    [11] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B]
    [12] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
    [13] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B]
    [14] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [15] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [16] -1    0    0x0000e900 - 0x0000e907 (0x8) IX[B]
    [17] -1    0    0x0000ea00 - 0x0000ea1f (0x20) IX[B]
    [18] -1    0    0x0000eb00 - 0x0000eb1f (0x20) IX[B]
    [19] -1    0    0x0000ec00 - 0x0000ec1f (0x20) IX[B]
    [20] -1    0    0x0000ed00 - 0x0000ed1f (0x20) IX[B]
    [21] -1    0    0x0000ee00 - 0x0000ee1f (0x20) IX[B]
    [22] -1    0    0x0000ef00 - 0x0000efff (0x100) IX[B]
    [23] -1    0    0x00000500 - 0x0000051f (0x20) IX[B]
    [24] -1    0    0x0000fb00 - 0x0000fb0f (0x10) IX[B]
    [25] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[B]
    [26] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[B]
    [27] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[B]
    [28] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[B]
    [29] -1    0    0x0000fc00 - 0x0000fc1f (0x20) IX[B]
    [30] -1    0    0x0000fd00 - 0x0000fd1f (0x20) IX[B]
    [31] -1    0    0x0000fe00 - 0x0000fe1f (0x20) IX[B]
    [32] -1    0    0x0000ff00 - 0x0000ff1f (0x20) IX[B]
    [33] -1    0    0x0000df00 - 0x0000df7f (0x80) IX[B](B)
    [34] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B]
    [35] 0    0    0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Video Driver, version 2.0
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Console is VGA mode 0x3
(II) NV(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(==) NV(0): Depth 24, (==) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(==) NV(0): Using hardware cursor
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): MMIO registers mapped at 0xb5ea0000
(--) NV(0): Total video RAM: 256.0 MB
(--) NV(0):       BAR1 size: 256.0 MB
(--) NV(0):   Mapped memory: 255.0 MB
(II) NV(0): Linear framebuffer mapped at 0xa5fa0000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(--) NV(0): Connector map:
(--) NV(0):   Bus 0 -> DAC1
(--) NV(0):   Bus 1 -> DAC2
(--) NV(0):   Bus 1 -> SOR1
(--) NV(0): Load detection: 340
(II) NV(0): I2C bus "I2C0" initialized.
(II) NV(0): Output VGA1 using monitor section Configured Monitor
(II) NV(0): I2C bus "I2C1" initialized.
(II) NV(0): Output VGA2 has no monitor section
(II) NV(0): Output DVI1 has no monitor section
(II) NV(0): Probing for EDID on I2C bus 0...
(II) NV(0): I2C device "I2C0:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "I2C0:ddc2" removed.
(II) NV(0):   ... none found
(--) NV(0): Trying load detection on VGA1 ... nothing.
(II) NV(0): Probing for EDID on I2C bus 1...
(II) NV(0): I2C device "I2C1:ddc2" registered at address 0xA0.
(--) NV(0): DDC detected a DFP:
(II) NV(0): Manufacturer: ACI  Model: 22a2  Serial#: 16843009
(II) NV(0): Year: 2007  Week: 37
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max H-Image Size [cm]: horiz.: 47  vert.: 30
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): Default color space is primary color space
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.609
(II) NV(0): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.330
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@67Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@56Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 832x624@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NV(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) NV(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) NV(0): #4: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) NV(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 146.2 MHz   Image Size:  473 x 296 mm
(II) NV(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) NV(0): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 81 kHz, PixClock max 170 MHz
(II) NV(0): Monitor name: VW222
(II) NV(0): Serial No: 79LMQS011829
(II) NV(0): EDID (in hex):
(II) NV(0):     00ffffffffffff000469a22201010101
(II) NV(0):     25110103802f1e78eec4f6a3574a9c23
(II) NV(0):     114f54bfef00714f818081409500a940
(II) NV(0):     b3000101010121399030621a274068b0
(II) NV(0):     3600d9281100001c000000fd00384b1f
(II) NV(0):     5111000a202020202020000000fc0056
(II) NV(0):     573232320a20202020202020000000ff
(II) NV(0):     0037394c4d51533031313832390a0036
(--) NV(0): Trying load detection on VGA2 ... nothing.
(II) NV(0): EDID vendor "ACI", prod id 8866
(II) NV(0): Output VGA1 disconnected
(II) NV(0): Output VGA2 disconnected
(II) NV(0): Output DVI1 connected
(II) NV(0): Output DVI1 using initial mode 1680x1050
(--) NV(0): Virtual size is 1680x1680 (pitch 1792)
(**) NV(0):  Driver mode "1680x1050": 146.2 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) NV(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(**) NV(0):  Driver mode "1600x1200": 161.0 MHz (scaled from 0.0 MHz), 74.5 kHz, 59.9 Hz
(II) NV(0): Modeline "1600x1200"x59.9  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync (74.5 kHz)
(**) NV(0):  Driver mode "1680x1050": 146.2 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) NV(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(**) NV(0):  Driver mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) NV(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(**) NV(0):  Driver mode "1280x1024": 109.0 MHz (scaled from 0.0 MHz), 63.7 kHz, 59.9 Hz
(II) NV(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(**) NV(0):  Driver mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 59.9 Hz
(II) NV(0): Modeline "1440x900"x59.9  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(**) NV(0):  Driver mode "1280x960": 101.2 MHz (scaled from 0.0 MHz), 59.7 kHz, 59.9 Hz
(II) NV(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(**) NV(0):  Driver mode "1152x864": 104.0 MHz (scaled from 0.0 MHz), 67.7 kHz, 74.8 Hz
(II) NV(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(**) NV(0):  Driver mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.1 kHz, 75.1 Hz
(II) NV(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(**) NV(0):  Driver mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.1 Hz
(II) NV(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) NV(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) NV(0):  Driver mode "832x624": 57.3 MHz (scaled from 0.0 MHz), 49.7 kHz, 74.6 Hz
(II) NV(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) NV(0):  Driver mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.2 Hz
(II) NV(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) NV(0):  Driver mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) NV(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) NV(0):  Driver mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) NV(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) NV(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.8 Hz
(II) NV(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(**) NV(0):  Driver mode "640x480": 30.2 MHz (scaled from 0.0 MHz), 35.0 kHz, 66.7 Hz
(II) NV(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(**) NV(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) NV(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NV(0):  Driver mode "720x400": 28.3 MHz (scaled from 0.0 MHz), 31.5 kHz, 70.1 Hz
(II) NV(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(==) NV(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.2.0
    ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] 0    0    0xfb000000 - 0xfb000000 (0x1) MX[B]
    [1] 0    0    0xb0000000 - 0xbfffffff (0x10000000) MX[B]
    [2] 0    0    0xfb000000 - 0xfbffffff (0x1000000) MX[B]
    [3] -1    0    0xfb000000 - 0xfb000000 (0x1) MX[B](B)
    [4] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [8] -1    0    0xfdefd000 - 0xfdefd0ff (0x100) MX[B]
    [9] -1    0    0xfdefe000 - 0xfdefe0ff (0x100) MX[B]
    [10] -1    0    0xfdeff000 - 0xfdeff0ff (0x100) MX[B]
    [11] -1    0    0xfdfff000 - 0xfdfff3ff (0x400) MX[B]
    [12] -1    0    0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
    [13] -1    0    0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
    [14] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
    [15] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
    [16] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
    [17] 0    0    0x0000df00 - 0x0000df7f (0x80) IX[B]
    [18] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [19] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [20] -1    0    0x0000e900 - 0x0000e907 (0x8) IX[B]
    [21] -1    0    0x0000ea00 - 0x0000ea1f (0x20) IX[B]
    [22] -1    0    0x0000eb00 - 0x0000eb1f (0x20) IX[B]
    [23] -1    0    0x0000ec00 - 0x0000ec1f (0x20) IX[B]
    [24] -1    0    0x0000ed00 - 0x0000ed1f (0x20) IX[B]
    [25] -1    0    0x0000ee00 - 0x0000ee1f (0x20) IX[B]
    [26] -1    0    0x0000ef00 - 0x0000efff (0x100) IX[B]
    [27] -1    0    0x00000500 - 0x0000051f (0x20) IX[B]
    [28] -1    0    0x0000fb00 - 0x0000fb0f (0x10) IX[B]
    [29] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[B]
    [30] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[B]
    [31] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[B]
    [32] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[B]
    [33] -1    0    0x0000fc00 - 0x0000fc1f (0x20) IX[B]
    [34] -1    0    0x0000fd00 - 0x0000fd1f (0x20) IX[B]
    [35] -1    0    0x0000fe00 - 0x0000fe1f (0x20) IX[B]
    [36] -1    0    0x0000ff00 - 0x0000ff1f (0x20) IX[B]
    [37] -1    0    0x0000df00 - 0x0000df7f (0x80) IX[B](B)
    [38] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
    [39] 0    0    0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(--) NV(0): 212.51 MB available for offscreen pixmaps
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    8x8 mono pattern filled rectangles
    Indirect CPU to Screen color expansion
    Solid Lines
    Scanline Image Writes
    Offscreen Pixmaps
    Setting up tile and stipple cache:
        32 128x128 slots
        32 256x256 slots
        16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(II) NV(0): DPMS enabled
(II) NV(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(II) NV(0): Setting screen physical size to 473 x 296
(WW) <default pointer>: No Device specified, looking for one...
(II) <default pointer>: Setting Device option to "/dev/input/mice"
(--) <default pointer>: Device: "/dev/input/mice"
(==) <default pointer>: Protocol: "Auto"
(**) Option "CorePointer"
(**) <default pointer>: always reports core events
(==) <default pointer>: Emulate3Buttons, Emulate3Timeout: 50
(**) <default pointer>: ZAxisMapping: buttons 4 and 5
(**) <default pointer>: Buttons: 9
(**) <default pointer>: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (<default pointer>)
(II) XINPUT: Adding extended input device "<default pointer>" (type: MOUSE)
(--) <default pointer>: PnP-detected protocol: "ExplorerPS/2"
(II) <default pointer>: ps2EnableDataReporting: succeeded
(II) NV(0): Probing for EDID on I2C bus 0...
(II) NV(0): I2C device "I2C0:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "I2C0:ddc2" removed.
(II) NV(0):   ... none found
(--) NV(0): Trying load detection on VGA1 ... nothing.
(II) NV(0): Probing for EDID on I2C bus 1...
(--) NV(0): DDC detected a DFP:
(II) NV(0): Manufacturer: ACI  Model: 22a2  Serial#: 16843009
(II) NV(0): Year: 2007  Week: 37
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max H-Image Size [cm]: horiz.: 47  vert.: 30
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): Default color space is primary color space
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.609
(II) NV(0): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.330
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@67Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@56Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 832x624@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NV(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) NV(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) NV(0): #4: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) NV(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 146.2 MHz   Image Size:  473 x 296 mm
(II) NV(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) NV(0): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 81 kHz, PixClock max 170 MHz
(II) NV(0): Monitor name: VW222
(II) NV(0): Serial No: 79LMQS011829
(II) NV(0): EDID (in hex):
(II) NV(0):     00ffffffffffff000469a22201010101
(II) NV(0):     25110103802f1e78eec4f6a3574a9c23
(II) NV(0):     114f54bfef00714f818081409500a940
(II) NV(0):     b3000101010121399030621a274068b0
(II) NV(0):     3600d9281100001c000000fd00384b1f
(II) NV(0):     5111000a202020202020000000fc0056
(II) NV(0):     573232320a20202020202020000000ff
(II) NV(0):     0037394c4d51533031313832390a0036
(--) NV(0): Trying load detection on VGA2 ... nothing.
(II) NV(0): EDID vendor "ACI", prod id 8866
(II) NV(0): Using EDID range info for horizontal sync
(II) NV(0): Using EDID range info for vertical refresh
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) NV(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) NV(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) NV(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NV(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NV(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NV(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) NV(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) NV(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) NV(0): Modeline "1440x900"x59.9  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) NV(0): Modeline "1600x1200"x59.9  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync (74.5 kHz)
(II) NV(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) NV(0): EDID vendor "ACI", prod id 8866
(II) NV(0): Probing for EDID on I2C bus 0...
(II) NV(0): I2C device "I2C0:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "I2C0:ddc2" removed.
(II) NV(0):   ... none found
(--) NV(0): Trying load detection on VGA1 ... nothing.
(II) NV(0): Probing for EDID on I2C bus 1...
(--) NV(0): DDC detected a DFP:
(II) NV(0): Manufacturer: ACI  Model: 22a2  Serial#: 16843009
(II) NV(0): Year: 2007  Week: 37
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max H-Image Size [cm]: horiz.: 47  vert.: 30
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): Default color space is primary color space
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.609
(II) NV(0): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.330
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@67Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@56Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 832x624@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NV(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) NV(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) NV(0): #4: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) NV(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 146.2 MHz   Image Size:  473 x 296 mm
(II) NV(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) NV(0): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 81 kHz, PixClock max 170 MHz
(II) NV(0): Monitor name: VW222
(II) NV(0): Serial No: 79LMQS011829
(II) NV(0): EDID (in hex):
(II) NV(0):     00ffffffffffff000469a22201010101
(II) NV(0):     25110103802f1e78eec4f6a3574a9c23
(II) NV(0):     114f54bfef00714f818081409500a940
(II) NV(0):     b3000101010121399030621a274068b0
(II) NV(0):     3600d9281100001c000000fd00384b1f
(II) NV(0):     5111000a202020202020000000fc0056
(II) NV(0):     573232320a20202020202020000000ff
(II) NV(0):     0037394c4d51533031313832390a0036
(--) NV(0): Trying load detection on VGA2 ... nothing.
(II) NV(0): EDID vendor "ACI", prod id 8866
(II) NV(0): Using hsync ranges from config file
(II) NV(0): Using vrefresh ranges from config file
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) NV(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) NV(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) NV(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NV(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NV(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NV(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) NV(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) NV(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) NV(0): Modeline "1440x900"x59.9  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) NV(0): Modeline "1600x1200"x59.9  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync (74.5 kHz)
(II) NV(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) NV(0): EDID vendor "ACI", prod id 8866
(II) NV(0): Probing for EDID on I2C bus 0...
(II) NV(0): I2C device "I2C0:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "I2C0:ddc2" removed.
(II) NV(0):   ... none found
(--) NV(0): Trying load detection on VGA1 ... nothing.
(II) NV(0): Probing for EDID on I2C bus 1...
(--) NV(0): DDC detected a DFP:
(II) NV(0): Manufacturer: ACI  Model: 22a2  Serial#: 16843009
(II) NV(0): Year: 2007  Week: 37
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max H-Image Size [cm]: horiz.: 47  vert.: 30
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): Default color space is primary color space
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.609
(II) NV(0): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.330
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@67Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@56Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 832x624@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NV(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) NV(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) NV(0): #4: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) NV(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 146.2 MHz   Image Size:  473 x 296 mm
(II) NV(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) NV(0): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 81 kHz, PixClock max 170 MHz
(II) NV(0): Monitor name: VW222
(II) NV(0): Serial No: 79LMQS011829
(II) NV(0): EDID (in hex):
(II) NV(0):     00ffffffffffff000469a22201010101
(II) NV(0):     25110103802f1e78eec4f6a3574a9c23
(II) NV(0):     114f54bfef00714f818081409500a940
(II) NV(0):     b3000101010121399030621a274068b0
(II) NV(0):     3600d9281100001c000000fd00384b1f
(II) NV(0):     5111000a202020202020000000fc0056
(II) NV(0):     573232320a20202020202020000000ff
(II) NV(0):     0037394c4d51533031313832390a0036
(--) NV(0): Trying load detection on VGA2 ... nothing.
(II) NV(0): EDID vendor "ACI", prod id 8866
(II) NV(0): Using hsync ranges from config file
(II) NV(0): Using vrefresh ranges from config file
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) NV(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) NV(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) NV(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NV(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NV(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NV(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) NV(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) NV(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) NV(0): Modeline "1440x900"x59.9  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) NV(0): Modeline "1600x1200"x59.9  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync (74.5 kHz)
(II) NV(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) NV(0): EDID vendor "ACI", prod id 8866
(II) NV(0): Probing for EDID on I2C bus 0...
(II) NV(0): I2C device "I2C0:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "I2C0:ddc2" removed.
(II) NV(0):   ... none found
(--) NV(0): Trying load detection on VGA1 ... nothing.
(II) NV(0): Probing for EDID on I2C bus 1...
(--) NV(0): DDC detected a DFP:
(II) NV(0): Manufacturer: ACI  Model: 22a2  Serial#: 16843009
(II) NV(0): Year: 2007  Week: 37
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max H-Image Size [cm]: horiz.: 47  vert.: 30
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): Default color space is primary color space
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.609
(II) NV(0): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.330
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@67Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@56Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 832x624@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NV(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) NV(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) NV(0): #4: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) NV(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 146.2 MHz   Image Size:  473 x 296 mm
(II) NV(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) NV(0): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 81 kHz, PixClock max 170 MHz
(II) NV(0): Monitor name: VW222
(II) NV(0): Serial No: 79LMQS011829
(II) NV(0): EDID (in hex):
(II) NV(0):     00ffffffffffff000469a22201010101
(II) NV(0):     25110103802f1e78eec4f6a3574a9c23
(II) NV(0):     114f54bfef00714f818081409500a940
(II) NV(0):     b3000101010121399030621a274068b0
(II) NV(0):     3600d9281100001c000000fd00384b1f
(II) NV(0):     5111000a202020202020000000fc0056
(II) NV(0):     573232320a20202020202020000000ff
(II) NV(0):     0037394c4d51533031313832390a0036
(--) NV(0): Trying load detection on VGA2 ... nothing.
(II) NV(0): EDID vendor "ACI", prod id 8866
(II) NV(0): Using hsync ranges from config file
(II) NV(0): Using vrefresh ranges from config file
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) NV(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) NV(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) NV(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NV(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NV(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NV(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) NV(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) NV(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) NV(0): Modeline "1440x900"x59.9  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) NV(0): Modeline "1600x1200"x59.9  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync (74.5 kHz)
(II) NV(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) NV(0): EDID vendor "ACI", prod id 8866
(II) NV(0): Probing for EDID on I2C bus 0...
(II) NV(0): I2C device "I2C0:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "I2C0:ddc2" removed.
(II) NV(0):   ... none found
(--) NV(0): Trying load detection on VGA1 ... nothing.
(II) NV(0): Probing for EDID on I2C bus 1...
(--) NV(0): DDC detected a DFP:
(II) NV(0): Manufacturer: ACI  Model: 22a2  Serial#: 16843009
(II) NV(0): Year: 2007  Week: 37
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max H-Image Size [cm]: horiz.: 47  vert.: 30
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): Default color space is primary color space
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.609
(II) NV(0): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.330
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@67Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@56Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 832x624@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NV(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) NV(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) NV(0): #4: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) NV(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 146.2 MHz   Image Size:  473 x 296 mm
(II) NV(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) NV(0): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 81 kHz, PixClock max 170 MHz
(II) NV(0): Monitor name: VW222
(II) NV(0): Serial No: 79LMQS011829
(II) NV(0): EDID (in hex):
(II) NV(0):     00ffffffffffff000469a22201010101
(II) NV(0):     25110103802f1e78eec4f6a3574a9c23
(II) NV(0):     114f54bfef00714f818081409500a940
(II) NV(0):     b3000101010121399030621a274068b0
(II) NV(0):     3600d9281100001c000000fd00384b1f
(II) NV(0):     5111000a202020202020000000fc0056
(II) NV(0):     573232320a20202020202020000000ff
(II) NV(0):     0037394c4d51533031313832390a0036
(--) NV(0): Trying load detection on VGA2 ... nothing.
(II) NV(0): EDID vendor "ACI", prod id 8866
(II) NV(0): Using hsync ranges from config file
(II) NV(0): Using vrefresh ranges from config file
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) NV(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) NV(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) NV(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NV(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NV(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NV(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) NV(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) NV(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) NV(0): Modeline "1440x900"x59.9  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) NV(0): Modeline "1600x1200"x59.9  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync (74.5 kHz)
(II) NV(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) NV(0): EDID vendor "ACI", prod id 8866
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled
(II) 3rd Button detected: disabling emulate3Button


```

could not fin those with EE as you said........

---

### Post by sorin.stirbu on 2008-04-15
an update on the situation:

After some system updates I decided to try again installing the nVidia Driver from restricted Drivers section. The same result [black screen]. After booting in Recovery Mode and "Try to fix X" .... at reboot the screen looks OK but.......in the Restricted drivers the nVidia driver is IN USE but the small box is unchecked + the nVidia Setiings prompts me an error. Screens below:


[[IMG]http://img528.imageshack.us/img528/18/screenshotrz7.th.png[/IMG]](http://img528.imageshack.us/my.php?image=screenshotrz7.png)[[IMG]http://img528.imageshack.us/img528/658/screenshot1om8.th.png[/IMG]](http://img528.imageshack.us/my.php?image=screenshot1om8.png)

---

### Post by rocketman768 on 2008-04-17
> **sorin.stirbu said:**
> 

could not fin those with EE as you said........

First, it appears as though it's loading the nv driver instead of the nvidia driver. Also, you _do_ have an (EE) line which says that it failed to load glx b/c it couldn't find a compatible nvidia driver. So, either your driver isn't set to nvidia in xorg.conf, or that setting is getting ignored.

If it's nv instead of nvidia, you can automatically change that by running "sudo nvidia-xconfig" and then doing a ctrl-alt-backspace to restart X.

---

### Post by sorin.stirbu on 2008-04-17
> **rocketman768 said:**
> First, it appears as though it's loading the nv driver instead of the nvidia driver. Also, you _do_ have an (EE) line which says that it failed to load glx b/c it couldn't find a compatible nvidia driver. So, either your driver isn't set to nvidia in xorg.conf, or that setting is getting ignored.

If it's nv instead of nvidia, you can automatically change that by running "sudo nvidia-xconfig" and then doing a ctrl-alt-backspace to restart X.

check out the second screenshot....that is the error displayed at runiing "sudo nvidia-xconfig" so I cannot acces that and cheange "nv" to "nvidia"

question: isn't a method of changing that manualy in xorg.conf ???...without using the "sduo nvidia-xconfig" command ???

---

### Post by rocketman768 on 2008-04-18
> question: isn't a method of changing that manualy in xorg.conf ???...without using the "sduo nvidia-xconfig" command ???

Yeah, learn to use "vi" real quick and at the prompt, type "sudo vi /etc/X11/xorg.conf" and you'll be editing that file. You want to find the line that says 'Driver "nv"' and change it to 'Driver "nvidia"' and remove any lines that start with "Load".

Quick run-down of vi (if you don't already know)

h - move cursor left
j - move cursor down
k - move cursor up
l - move cursor right

i - insert mode (you can now enter text)
<esc> - get out of insert mode
x - delete the character at the cursor
dd - delete the whole line the cursor is on
:w - save the file
:q - quit

---

### Post by sorin.stirbu on 2008-04-18
> **rocketman768 said:**
> Yeah, learn to use "vi" real quick and at the prompt, type "sudo vi /etc/X11/xorg.conf" and you'll be editing that file. You want to find the line that says 'Driver "nv"' and change it to 'Driver "nvidia"' and remove any lines that start with "Load".

Quick run-down of vi (if you don't already know)

h - move cursor left
j - move cursor down
k - move cursor up
l - move cursor right

i - insert mode (you can now enter text)
<esc> - get out of insert mode
x - delete the character at the cursor
dd - delete the whole line the cursor is on
:w - save the file
:q - quit

isn't it simpler to use "sudo gedit /etc/X11/xorg.conf" ? :)...10x for letting me know what to modify....i'll be back with some info on the results ;)

---

### Post by rocketman768 on 2008-04-19
> **sorin.stirbu said:**
> isn't it simpler to use "sudo gedit /etc/X11/xorg.conf" ? :)...10x for letting me know what to modify....i'll be back with some info on the results ;)

Haha, sure. I just figured you were stuck in the command prompt. I used to have problems with the nvidia driver back in the day, and that's what forced me to learn vi. It's always good to know how to use it in case you can't get to any other text editor like gedit.

---

### Post by marce on 2008-04-22
Im having exactly the same problems with UbuntuStudio 8.04rc and the nvidia propietary driver. I activated it in ubuntu, also installed trough Envyng several times, but no luck, when the nvidia drivers are activated a blank screen hangs before the log-in window.
The UbuntuStudio ALSO uses the realtime kernel. Maybe is some issue between nvidia propietary and realtime kernels?

Any tip is apreciated.

Edit: i See the thread is SOLVED, but how it was solved? i cant found the info

---

### Post by gary_emms on 2008-04-22
I don't know wether this helps as my problem was that I had a maximum refresh rate of 50 hz. However I did an automatic reconfiguration using 'sudo dpkg-reconfigure -phigh xserver-xorg' which fixed the problem. Unfortunately it also reset my keyboard to 'US' but this is a simple fix.

Gaz

---

### Post by sorin.stirbu on 2008-04-22
> **rocketman768 said:**
> Haha, sure. I just figured you were stuck in the command prompt. I used to have problems with the nvidia driver back in the day, and that's what forced me to learn vi. It's always good to know how to use it in case you can't get to any other text editor like gedit.
I solved it .. this is what you have tot do: before installing the nVidia driver [you choose the way you want to do it] change the " Driver 'nv' " in xorg.conf with " Driver 'nvidia' ".
It worked for me :)

---

### Post by marce on 2008-04-22
for the records, i solved the issue following this procedure:

[http://ubuntuforums.org/showthread.php?p=4767614#post4767614](http://ubuntuforums.org/showthread.php?p=4767614#post4767614)

---

### Post by interzoneuk on 2008-04-24
Can I just point out to people who use vi.

To actually get a sane workable version of vi in Ubuntu (i.e where the arrow keys work,etc) try

sudo apt-get install vim

then try vi

---

### Post by interzoneuk on 2008-04-24
Also if people are still having issue with nvidia cards and refresh rates please try my post - [http://ubuntuforums.org/showthread.php?p=4784403#post4784403](http://ubuntuforums.org/showthread.php?p=4784403#post4784403)

---

### Post by besson3c on 2008-04-27
I'm still only getting 800x600 with my Geforce 8500 GT under Hardy 64 bit.

I've tried installing the latest driver manually, via Envy, I've tried looking in nvidia-settings for additional resolution options, all to no avail.

How do I get my 1920x1080 back? This stinks :(

---

### Post by besson3c on 2008-04-27
I've also tried the nvidia-xconfig tool.

Would anybody like to see my xorg logs?

---

### Post by besson3c on 2008-04-27
I've also tried the nvidia-xconfig tool and setting the display modes manually in my xorg.conf.

Here is my Xorg.0.log:

```
(II) NVIDIA(0): NVIDIA GPU GeForce 8500 GT (G86) at PCI:2:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 60.86.34.00.75
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 8500 GT at PCI:2:0:0:
(--) NVIDIA(0):     DFP-0
(--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
(--) NVIDIA(0): DFP-0: Internal Dual Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(WW) NVIDIA(0): Unable to get display device DFP-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from DFP-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xdfffd000 - 0xdfffd0ff (0x100) MX[B]
        [5] -1  0       0xdfffe000 - 0xdfffe0ff (0x100) MX[B]
        [6] -1  0       0xdffff000 - 0xdffff7ff (0x800) MX[B]
        [7] -1  0       0xc8000000 - 0xc7ffffff (0x0) MX[B]O
        [8] -1  0       0xda000000 - 0xdbffffff (0x2000000) MX[B](B)
        [9] -1  0       0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
        [10] -1 0       0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
        [11] -1 0       0xd4000000 - 0xd7ffffff (0x4000000) MX[B](B)
        [12] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [13] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [14] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [15] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [16] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [17] -1 0       0x0000f000 - 0x0000f0ff (0x100) IX[B]
        [18] -1 0       0x0000f500 - 0x0000f51f (0x20) IX[B]
        [19] -1 0       0x0000f600 - 0x0000f61f (0x20) IX[B]
        [20] -1 0       0x0000f700 - 0x0000f71f (0x20) IX[B]
        [21] -1 0       0x0000f800 - 0x0000f81f (0x20) IX[B]
        [22] -1 0       0x0000f900 - 0x0000f90f (0x10) IX[B]
        [23] -1 0       0x0000f200 - 0x0000f2ff (0x100) IX[B]
        [24] -1 0       0x0000fa00 - 0x0000fa0f (0x10) IX[B]
        [25] -1 0       0x0000fb00 - 0x0000fb03 (0x4) IX[B]
        [26] -1 0       0x0000fc00 - 0x0000fc07 (0x8) IX[B]
        [27] -1 0       0x0000fd00 - 0x0000fd03 (0x4) IX[B]
        [28] -1 0       0x0000fe00 - 0x0000fe07 (0x8) IX[B]
        [29] -1 0       0x0000ff00 - 0x0000ff7f (0x80) IX[B]
        [30] -1 0       0x0000ef00 - 0x0000ef7f (0x80) IX[B](B)
        [31] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [32] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Setting vga for screen 0.
```

---

### Post by sorin.stirbu on 2008-04-27
you won't manage to install it .... i've been doing that for some time and the only thing that I have managed is to appear in Restricted drivers as IN USE [but that small box is unchecked] so actually is NOT IN USE ...... [I even fooled my self]

it seems that Ubuntu 8.04 LTS is incompatible with nVidia proprietary drivers .... and I am very sure of it.....I'm not the only one having this problem ...the only thing available for us is to wait until it is fixed :)

to bad....I had big expectations for 8.04 .. but it seems like it started with a bad impression  for the nVidia users [I hate my self for changing my ATI videocard some 3 months ago..... :( !!! ]

---

### Post by besson3c on 2008-04-27
Is downgrading back to Gutsy without a wipe/reinstall an option? If so, how is this done? The instructions look a little scary. For that matter, has anybody tested whether this problem exists under a clean install of Hardy?

---

### Post by besson3c on 2008-04-28
I finally got my resolution back after a lot of work by uninstalling the Restricted Driver, the Envy driver, rebooting, and installing the beta NVidia driver by hand.

However, the solution of installing the beta driver is temporary at best, since some apps such as Wine don't recognize the presence of OpenGL acceleration this way. Please do post a workaround to this if you know of one! :)

---

### Post by ubunyou on 2008-05-04
Doesn't sound like this thread should be solved as most people seem to only suggest work-arounds, thx for the workaround btw ...

I am having similar trouble with my GeForce8500 GT.
I can't get nvidia to work. 
The nv driver works fine, no compiz or ccsm though :(

I have tried the following techniques which are discussed as solutions on various threads:
-tried the open source (and legacy) drivers through synaptec
-tried installing the drivers package from nvidia which completes but still launches into "low-res" mode upon re-boot. 
-tried EnvyNG using every driver option available


The nvidia driver that is installed using the nvidia-glx-new package worked with compiz and ccsm effects packages with the Hardy development packages up until about a month ago.
One build it just stopped working. Now, once I have install nvidia-glx-new:
1) the Administration > Hardware Drivers doesn't show any restricted drivers.

2) I can't load the nvidia driver
kyle@kyle-ubuntu:~$ sudo modprobe -a nvidia
WARNING: Error running install command for nvidia

noticed this in /var/log/Xorg.0.log
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

NOTE: To get desktop back, without effects, edit /etc/X11/xorg.conf and change nvidia to nv
Any ideas when the nvidia driver will be fixed for the new kernel?

---

### Post by tylerjwilk on 2008-05-05
Make sure that another kernel version did not get installed some how. For example i installed virtualbox with the wrong modules and it installed and then defaulted to the linux-386 kernel instead of linux-generic.

So when ur computer boots hold down ESC at the grub menu and then see if u have multiple kernels installed, i recommend using generic if its there.

If that solves the problem remove the linux 386 kernel thru apt (ie: synaptic)

hope that helps

if u do remove 386 and it asks what to do with menu.lst use maintainers

---

