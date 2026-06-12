---
title: "nVidia + geForce 6600GT= Black  screen"
date: 2006-07-26
forum: Multimedia &amp; Video
---

### Post by Wolfhurt on 2006-07-26
Ih all

I have this computer:
> AMD 3000+
1.5Go of RAM
Asus K8N
geForce 6600GT

Dual screen with 2CRT
Mutsubishi Diamond pro 920 (secondary screen : DVI output videocard -> DVI/VGA adaptator -> screen cord VGA)
    HorizSync    30 - 108
    VertRefresh    50 - 140
NEC FP955 (primary screen : in VGA)
    HorizSync    30 - 110
    VertRefresh    55 - 160

and my old A3 WACOM RS232 Tablet (i think it cant work on linux eheh)


What I done:
- I use Dapper amd64 sources, 
- I tested with 64_generic and K8 kernel+modules
- I have done some tests to install nvidia-glx and change Driver "nvidia" or use nvidia-glx-config  just after installing ubuntu.
- I have search the  vert and horizontal frequencies in  nec & mutsubishi website
- I tested the option on xorg.conf to put dvi on
- I tested with 1 screen alone , and 2 screens

- With the nv drivers, my system freeze after 5 minuts, I can move the mouse but i cant use the keyboard ( ALT+IMPR+...)


When X begin with driver "nvidia"=
+ The screen is black
+ The beginning's sound starts (I think more later the usually when the screen is working with driver "nv"), 
+ The screen goes on inactive mode (blinking orange led) before or after the begining's sound ...

Since 4 nights I'm ](*,) on this problem

Thanks to help me !

Here is my xorg.conf=
```

Section "ServerLayout"
    Identifier    "Dual"
    Screen        "Screen0"
#    Screen    0    "Screen0" 0 0
#    Screen    1    "Screen1" LeftOf "Screen0"
    InputDevice    "Mouse0" "Corepointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
    Option        "Xinerama"    "off"
    Option        "Clone" "on"
EndSection

Section "Files"
    FontPath    "/usr/share/X11/fonts/misc"
    FontPath    "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/Type1"
    FontPath    "/usr/share/X11/fonts/100dpi"
    FontPath    "/usr/share/X11/fonts/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load    "i2c"
    Load    "bitmap"
    Load    "ddc"
#    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "type1"
    Load    "vbe"
EndSection

Section "InputDevice"
    Identifier    "Keyboard0"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "fr"
    Option        "XkbVariant"    "latin9"
EndSection

Section "InputDevice"
    Identifier    "Mouse0"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "Monitor"
    Identifier    "Monitor0"
    VendorName    "NEC"
    ModelName    "FP955"
    HorizSync    30 - 110
    VertRefresh    55 - 160
#    Option        "DPMS"
EndSection

Section "Monitor"
    Identifier    "Monitor1"
    VendorName    "Mitsubishi"
    ModelName    "DiamondPro920"
    HorizSync    30 - 108
    VertRefresh    50 - 140
#    Option        "DPMS"
EndSection


Section "Device"
    Identifier    "Videocard0"
    Driver        "nvidia"
    VendorName    "nVidia"
    BoardName    "nVidia  Corporation NV43 [GeForce 6800 GT]"
    BusID        "PCI:1:0:0"
    Screen    0
EndSection

Section "Device"
    Identifier    "Videocard1"
    Driver        "nvidia"
    VendorName    "nVidia"
    BoardName    "nVidia  Corporation NV43 [GeForce 6800 GT]"
    BusID        "PCI:1:0:0"
    Screen    1
EndSection

Section "Screen"
    Identifier    "Screen0"
    Device        "VideoCard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection "Display"
        Viewport    0 0
        Depth        24
        Modes        "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier    "Screen1"
    Device        "VideoCard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    SubSection "Display"
        Viewport    0 0
        Depth        24
        Modes        "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

#Section "DRI"
#    Mode    0666
#EndSection

```

---

### Post by tseliot on 2006-07-26
boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

Type:
```
reboot
```

Then see if the computer freezes again. Test it for a day so as to make sure that the graphic driver was the problem (instead of another hardware incompatibility).

Then try my guide:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

---

### Post by Wolfhurt on 2006-07-26
```

uname -r
>2.6.15-23-amd64-generic

```

For the vesa drivers, if i just change my xorg.conf with driver "vesa" or "vesafb" i have : can't load module xxx not found
but yes sure with dpkg-reconfigure xserver-xorg it s ok and very stable but very slow

===========================================
When i apt-get nvidia-glx it install me nvidia-glx_1.0.8762+2.6.15.11-3_amd64

```
apt-get nvidia-glx 
>[...]
>Suggested packages:
>    nvidia-kernel-source
>[...]   
```

but i cant apt-get nvidia-kernel-source 
```
Package nvidia-kernel-source is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
```


I just tested with the ubuntu X86 instead of AMD64, if exactly the same thing 

I have nothing against vesa but ... a little slow  for my graphical use ...

help me pls

---

### Post by tseliot on 2006-07-26
> **Wolfhurt said:**
> but i cant apt-get nvidia-kernel-source 
```
Package nvidia-kernel-source is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
```


I just tested with the ubuntu X86 instead of AMD64, if exactly the same thing 

I have nothing against vesa but ... a little slow  for my graphical use ...

help me pls

Please do ONLY what my guide suggests.

The warning you saw wasn't really a warning and you don't need that package.

---

### Post by Wolfhurt on 2006-07-27
ih, 

i just reinstall my system and test the METHOD 1 , and the result is always my problem 

i'm impressed of lots of people how have problems to configure there hardware video with Linux... 

there are some WW :
```

[...]
(WW) NVIDIA(0): Unable to read EDID for display device CRT-1
[...]
(WW) NVIDIA(0): WAIT (2, 6, 0x8000, 0x00000000, 0x00000508, 0)
(WW) NVIDIA(0): WAIT (1, 6, 0x8000, 0x00000000, 0x00000508, 0)
(II) NVIDIA(0): Setting mode "1600x1200"
(WW) NVIDIA(0): WAIT (2, 1, 0x8000, 0x00000000, 0x000005a8, 0)
(WW) NVIDIA(0): WAIT (1, 1, 0x8000, 0x00000000, 0x000005a8, 0)
[...]
(WW) NVIDIA(0): WAIT (2, 3, 0x8000, 0x00000000, 0x00000aec, 0)
(WW) NVIDIA(0): WAIT (1, 3, 0x8000, 0x00000000, 0x00000aec, 0)
(WW) NVIDIA(0): WAIT (2, 6, 0x8000, 0x00000000, 0x00000b1c, 0)
(WW) NVIDIA(0): WAIT (1, 6, 0x8000, 0x00000000, 0x00000b1c, 0)
[...]
error opening security policy file /etc/X11/xserver/SecurityPolicy
[...]

```

if this errors mean something, thanks !


here is the X log :

```

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 x86_64
Current Operating System: Linux xcom 2.6.15-26-amd64-k8 #1 SMP PREEMPT Mon Jul 17 19:55:58 UTC 2006 x86_64
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jul 27 19:54:21 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "NEC FP955"
(**) |   |-->Device "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,00e1 card 1043,813f rev a1 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 10de,00e0 card 1043,813f rev a2 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,00e4 card 1043,813f rev a1 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,00e7 card 1043,813f rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,00e7 card 1043,813f rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,00e8 card 1043,813f rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:05:0: chip 10de,00df card 1043,80a7 rev a2 class 06,80,00 hdr 00
(II) PCI: 00:06:0: chip 10de,00ea card 1043,812a rev a1 class 04,01,00 hdr 00
(II) PCI: 00:08:0: chip 10de,00e5 card 1043,813f rev a2 class 01,01,8a hdr 00
(II) PCI: 00:0a:0: chip 10de,00e3 card 1043,813f rev a2 class 01,01,85 hdr 00
(II) PCI: 00:0b:0: chip 10de,00e2 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,00ed card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,00f1 card 0000,0000 rev a2 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:11:0), (0,1,1), BCTRL: 0x000b (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfaa00000 - 0xfeafffff (0x4100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xca900000 - 0xea8fffff (0x20000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:14:0), (0,2,2), BCTRL: 0x0003 (VGA_EN is cleared)
(--) PCI:*(1:0:0) nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] rev 162, Mem @ 0xfd000000/24, 0xd0000000/28, 0xfc000000/24, BIOS @ 0xfeae0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf0000000 from 0xf7ffffff to 0xefffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfebfb000 - 0xfebfbfff (0x1000) MX[B]
	[1] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[2] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[3] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[4] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[5] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[6] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[7] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[9] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[11] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[12] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[13] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[14] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[15] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[16] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[17] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[19] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[20] -1	0	0x00005040 - 0x0000507f (0x40) IX[B]
	[21] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[22] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfebfb000 - 0xfebfbfff (0x1000) MX[B]
	[1] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[2] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[3] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[4] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[5] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[6] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[7] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[9] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[11] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[12] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[13] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[14] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[15] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[16] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[17] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[19] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[20] -1	0	0x00005040 - 0x0000507f (0x40) IX[B]
	[21] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[22] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebfb000 - 0xfebfbfff (0x1000) MX[B]
	[5] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[6] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[7] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[8] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[9] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[10] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[11] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[17] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[18] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[19] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[20] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[21] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[22] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B]
	[24] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[25] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[26] -1	0	0x00005040 - 0x0000507f (0x40) IX[B]
	[27] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[28] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
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
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.0.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8762
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8762
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) NVIDIA X Driver  1.0-8762  Mon May 15 14:01:11 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebfb000 - 0xfebfbfff (0x1000) MX[B]
	[5] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[6] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[7] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[8] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[9] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[10] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[11] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[17] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[18] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[19] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[20] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[21] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[22] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B]
	[24] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[25] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[26] -1	0	0x00005040 - 0x0000507f (0x40) IX[B]
	[27] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[28] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebfb000 - 0xfebfbfff (0x1000) MX[B]
	[5] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[6] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[7] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[8] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[9] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[10] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[11] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[20] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[21] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[22] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[23] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[24] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[25] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[26] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B]
	[27] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[28] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[29] -1	0	0x00005040 - 0x0000507f (0x40) IX[B]
	[30] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[31] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(WW) NVIDIA(0): Unable to read EDID for display device CRT-1
(II) NVIDIA(0): NVIDIA GPU GeForce Go 6600 at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 05.43.02.80.00
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce Go 6600 at PCI:1:0:0:
(--) NVIDIA(0):     NEC FP955 (CRT-0)
(--) NVIDIA(0):     CRT-1
(--) NVIDIA(0): NEC FP955 (CRT-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1600x1200"
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1280x960"
(II) NVIDIA(0):     "1152x864"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "832x624"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "720x400"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200
(--) NVIDIA(0): DPI set to (87, 92); computed from "UseEdidDpi" X config option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfebfb000 - 0xfebfbfff (0x1000) MX[B]
	[8] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[9] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[10] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[11] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[12] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[13] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[14] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[23] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[24] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[25] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[26] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[27] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[28] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[29] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B]
	[30] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[31] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[32] -1	0	0x00005040 - 0x0000507f (0x40) IX[B]
	[33] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[34] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(WW) NVIDIA(0): WAIT (2, 6, 0x8000, 0x00000000, 0x00000508, 0)
(WW) NVIDIA(0): WAIT (1, 6, 0x8000, 0x00000000, 0x00000508, 0)
(II) NVIDIA(0): Setting mode "1600x1200"
(WW) NVIDIA(0): WAIT (2, 1, 0x8000, 0x00000000, 0x000005a8, 0)
(WW) NVIDIA(0): WAIT (1, 1, 0x8000, 0x00000000, 0x000005a8, 0)
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): WAIT (2, 3, 0x8000, 0x00000000, 0x00000aec, 0)
(WW) NVIDIA(0): WAIT (1, 3, 0x8000, 0x00000000, 0x00000aec, 0)
(WW) NVIDIA(0): WAIT (2, 6, 0x8000, 0x00000000, 0x00000b1c, 0)
(WW) NVIDIA(0): WAIT (1, 6, 0x8000, 0x00000000, 0x00000b1c, 0)
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
error opening security policy file /etc/X11/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "fr"
(**) Generic Keyboard: XkbLayout: "fr"
(**) Option "XkbVariant" "latin9"
(**) Generic Keyboard: XkbVariant: "latin9"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded

```

---

### Post by tseliot on 2006-07-27
Try asking here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by RJARRRPCGP on 2006-07-27
> **Wolfhurt said:**
> 
but i cant apt-get nvidia-kernel-source 
```
Package nvidia-kernel-source is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
```



Please update the list by typing the following:

```
sudo apt-get update
```

---

