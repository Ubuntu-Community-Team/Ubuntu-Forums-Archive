---
title: "AGP+PCI .. possible?"
date: 2006-08-09
forum: Multimedia &amp; Video
---

### Post by 67comet on 2006-08-09
I normaly have been running an AGP nVidia FX5200 using dual monitors, xgl, xinerama everything .. and it's been awesome.

Today I came across a PCI (not pci-e) nVidia FX5200 video card, and chucked it in my box. Rebuilt my xorg.conf to include the new monitor, screen, and card. Rebooted, and walla .. I still only have two monitors, one pci and one agp.

Help?

Here is my xorg.conf
```

# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

#Files removed for post

Section "Module"
    Load    "i2c"
    Load    "bitmap"
    Load    "ddc"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "type1"
    Load    "vbe"
EndSection

#Input device removed for post

Section "Device"
    Identifier    "Card0"
    Driver        "nvidia"
    BusID         "PCI:1:0:0"
    Option        "RenderAccel"         "true"
    Option        "AllowGLXWithComposite" "true" 
#    Screen    0
EndSection

Section "Device"
    Identifier    "Card1"
    Driver        "nvidia"
    BusID         "PCI:1:0:0"
    Option        "RenderAccel"         "true"
    Option        "AllowGLXWithComposite" "true" 
#    Screen    1
EndSection

Section "Device"
    Identifier    "Card2"
    Driver        "nvidia"
    BusID         "PCI:2:02:0"
    Option        "RenderAccel"         "true"
    Option        "AllowGLXWithComposite" "true" 
#    Screen    2
EndSection

Section "Monitor"
    Identifier    "Monitor0"
    Option        "DPMS"
EndSection

Section "Monitor"
    Identifier    "Monitor1"
    Option        "DPMS"
EndSection

Section "Monitor"
    Identifier    "Monitor2"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Screen0"
    Device        "Card0"
    Monitor       "Monitor0"
    DefaultDepth  24
    SubSection "Display"
        Depth        16
        Modes        "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier    "Screen1"
    Device        "Card1"
    Monitor       "Monitor1"
    DefaultDepth    24
    SubSection "Display"
        Depth        16
        Modes        "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier    "Screen2"
    Device        "Card2"
    Monitor       "Monitor2"
    DefaultDepth    24
    SubSection "Display"
        Depth        16
        Modes        "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Screen0"
    Screen        "Screen1" LeftOf "Screen0"
    Screen	  "Screen2" RightOf "Screen0"
    Screen	  "Screen1"
    InputDevice   "Generic Keyboard"
    InputDevice   "Configured Mouse"
EndSection

Section "DRI"
    Mode    0666
EndSection

Section "ServerFlags"
        Option "Xinerama" 
EndSection

Section "Extensions"
          Option  "Composite" "Enable"
EndSection

```

Hopefully it's simething silly in my .conf file here.

My log file .. still can't figure out why only two are on .. It sees them all perfectly .. and when I toss the log file, it blinks the third monitor while it checks it out .. I watch the green power light flicker.
```

X Window System Version 7.0.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux JustinsUbuntuBox 2.6.15-26-686 #1 SMP 

Module Loader present

(==) Log file: "/var/log/Xorg.93.log", Time: Thu Aug 10 02:00:56 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Card1"
(**) |-->Screen "Screen1" (2)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Card1"
(**) |-->Screen "Screen2" (3)
(**) |   |-->Monitor "Monitor2"
(**) |   |-->Device "Card2"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "Xinerama"
(**) Xinerama: enabled
(**) Extension "Composite" is enabled
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
(II) PCI: 00:00:0: chip 8086,2560 card 8086,2560 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2561 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24c2 card 107b,5288 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 107b,5288 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 107b,5288 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 107b,5288 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 82 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24c0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24cb card 107b,5288 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24c3 card 107b,5288 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24c5 card 107b,5288 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0322 card 107d,2960 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:02:0: chip 10de,0322 card 0000,0000 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:08:0: chip 8086,1039 card 107b,5288 rev 82 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfa900000 - 0xfc9fffff (0x2100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc2600000 - 0xe26fffff (0x20100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfca00000 - 0xfeafffff (0x2100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xe2700000 - 0xf27fffff (0x10100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI: (1:0:0) nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xfb000000/24, 0xd0000000/28
(--) PCI:*(2:2:0) nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xfd000000/24, 0xe8000000/27, BIOS @ 0xfeae0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf4000000 from 0xf7ffffff to 0xf3ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfeadf000 - 0xfeadffff (0x1000) MX[B]
	[1] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[2] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[3] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[4] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[5] -1	0	0xf4000000 - 0xf3ffffff (0x0) MX[B]O
	[6] -1	0	0xe2700000 - 0xe271ffff (0x20000) MX[B](B)
	[7] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[12] -1	0	0x0000e080 - 0x0000e0bf (0x40) IX[B]
	[13] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[14] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[15] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[16] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[17] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfeadf000 - 0xfeadffff (0x1000) MX[B]
	[1] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[2] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[3] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[4] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[5] -1	0	0xf4000000 - 0xf3ffffff (0x0) MX[B]O
	[6] -1	0	0xe2700000 - 0xe271ffff (0x20000) MX[B](B)
	[7] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[12] -1	0	0x0000e080 - 0x0000e0bf (0x40) IX[B]
	[13] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[14] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[15] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[16] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[17] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
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
	[4] -1	0	0xfeadf000 - 0xfeadffff (0x1000) MX[B]
	[5] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[6] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[7] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[8] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[9] -1	0	0xf4000000 - 0xf3ffffff (0x0) MX[B]O
	[10] -1	0	0xe2700000 - 0xe271ffff (0x20000) MX[B](B)
	[11] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[18] -1	0	0x0000e080 - 0x0000e0bf (0x40) IX[B]
	[19] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[20] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[21] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[22] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[23] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[24] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
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
(II) NVIDIA X Driver  1.0-8762  Mon May 15 13:09:21 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02:02:0
(WW) NVIDIA: More than one matching Device section for instances
	(BusID: PCI:1:0:0) found: Card1
(WW) NVIDIA: More than one matching Device section for instances
	(BusID: PCI:1:0:0) found: Card1
(--) Chipset NVIDIA GPU found
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
	[4] -1	0	0xfeadf000 - 0xfeadffff (0x1000) MX[B]
	[5] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[6] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[7] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[8] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[9] -1	0	0xf4000000 - 0xf3ffffff (0x0) MX[B]O
	[10] -1	0	0xe2700000 - 0xe271ffff (0x20000) MX[B](B)
	[11] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[18] -1	0	0x0000e080 - 0x0000e0bf (0x40) IX[B]
	[19] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[20] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[21] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[22] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[23] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[24] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeadf000 - 0xfeadffff (0x1000) MX[B]
	[5] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[6] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[7] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[8] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[9] -1	0	0xf4000000 - 0xf3ffffff (0x0) MX[B]O
	[10] -1	0	0xe2700000 - 0xe271ffff (0x20000) MX[B](B)
	[11] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[18] -1	0	0x0000e080 - 0x0000e0bf (0x40) IX[B]
	[19] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[20] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[21] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[22] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[23] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[24] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeadf000 - 0xfeadffff (0x1000) MX[B]
	[5] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[6] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[7] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[8] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[9] -1	0	0xf4000000 - 0xf3ffffff (0x0) MX[B]O
	[10] -1	0	0xe2700000 - 0xe271ffff (0x20000) MX[B](B)
	[11] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] 1	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[19] 1	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[20] 1	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[24] -1	0	0x0000e080 - 0x0000e0bf (0x40) IX[B]
	[25] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[26] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[27] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[28] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[29] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[30] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[31] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[32] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
	[33] 1	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 1	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "true"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5200 at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.42.00
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5200 at PCI:1:0:0:
(--) NVIDIA(0):     Compaq S710 (CRT-0)
(--) NVIDIA(0):     Gateway EV700 (CRT-1)
(--) NVIDIA(0):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(0): Compaq S710 (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): Gateway EV700 (CRT-1): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): NVIDIA TV Encoder (TV-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): TV encoder: NVIDIA
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "832x624"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "720x400"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(WW) NVIDIA(0): No size information available in CRT-0's EDID; cannot compute
(WW) NVIDIA(0):     DPI from EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "RenderAccel" "true"
(**) NVIDIA(1): Option "AllowGLXWithComposite" "true"
(**) NVIDIA(1): Enabling RENDER acceleration
(II) NVIDIA(1): NVIDIA GPU GeForce FX 5200 at PCI:2:2:0
(--) NVIDIA(1): VideoRAM: 131072 kBytes
(--) NVIDIA(1): VideoBIOS: 04.34.20.69.00
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(--) NVIDIA(1): Connected display device(s) on GeForce FX 5200 at PCI:2:2:0:
(--) NVIDIA(1):     Sony HMD-A200 (CRT-0)
(--) NVIDIA(1):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(1): Sony HMD-A200 (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(1): NVIDIA TV Encoder (TV-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(1): TV encoder: NVIDIA
(II) NVIDIA(1): Assigned Display Device: CRT-0
(II) NVIDIA(1): Validated modes:
(II) NVIDIA(1):     "1280x1024"
(II) NVIDIA(1):     "1024x768"
(II) NVIDIA(1):     "832x624"
(II) NVIDIA(1):     "800x600"
(II) NVIDIA(1):     "720x400"
(II) NVIDIA(1):     "640x480"
(II) NVIDIA(1): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(1): DPI set to (78, 81); computed from "UseEdidDpi" X config option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) LoadModule: "rac"
(II) Loading /usr/lib/xorg/modules/librac.so
(II) Module rac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) resource ranges after preInit:
	[0] 1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B]
	[1] 1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[2] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[3] 0	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B]
	[4] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xfeadf000 - 0xfeadffff (0x1000) MX[B]
	[9] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[10] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[11] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[12] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[13] -1	0	0xf4000000 - 0xf3ffffff (0x0) MX[B]O
	[14] -1	0	0xe2700000 - 0xe271ffff (0x20000) MX[B](B)
	[15] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[16] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[17] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[22] 1	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[23] 1	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[24] 1	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[25] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[26] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[27] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[28] -1	0	0x0000e080 - 0x0000e0bf (0x40) IX[B]
	[29] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[30] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[31] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[32] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[33] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[34] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
	[37] 1	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[38] 1	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) NVIDIA(1): Setting mode "1280x1024"
(II) NVIDIA(1): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(1): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(1): Backing store disabled
(==) NVIDIA(1): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(1): DPMS enabled
(==) RandR enabled
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
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
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "auto"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "auto"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded

```

Thank you all much,
Justin

P.S. Is it maybe my syntax in the ServerLayout? I'm really unsure how the syntax would go for triple video like this.

---

### Post by 67comet on 2006-08-12
No fellow triple monitor users? (If I had the desk room I would use all 4 of my monitors).

Help?

Justin](*,)

---

### Post by tseliot on 2006-08-13
I haven't tried such a thing before therefore I can't help you.

You can ask here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by isharra on 2006-08-13
```
Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Screen0"
    Screen        [COLOR="Magenta"]"Screen1"[/COLOR] LeftOf "Screen0"
    Screen	  "Screen2" RightOf "Screen0"
    Screen	  [COLOR="Magenta"]"Screen1"[/COLOR]
    InputDevice   "Generic Keyboard"
    InputDevice   "Configured Mouse"
EndSection

```

Don't know if this is the cause but defining things twice can cause all sorts of problems. If the driver doesn't know what you want it has a nasty habit of ignoring both options.

---

### Post by 67comet on 2006-08-20
FINALLY .. I got it .. it was as simple as naming each monitor for where it was going to be displayed, and adding the Screen 0 and Screen 1 on the AGP card's infomation.

Here is my current xorg.conf file. I dis-enabled compiz/XGL for now, but that is the next big hurtle. Thripple monitor support shouldn't be an issue. I had dual's running XGL like clockwork.

Cheers,
Justin

```

# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

############################# Start AGP Analog Head ####################
Section "Device"
	Identifier	"NVIDIA GeForce 6800 Analog"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
#	Option         	"MetaModes"        "1280x1024,1280x1024"
	Screen		0
EndSection

Section "Monitor"
	Identifier	"Gateway Monitor"
	Option		"DPMS"
#	HorizSync	28-64
#	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Center Screen"
	Device		"NVIDIA GeForce 6800 Analog"
	Monitor		"Gateway Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x768" "1024x768"
	EndSubSection
EndSection
########################### Start DVI of AGP Head ######################
Section "Device"
	Identifier	"NVIDIA GeForce 6800 DVI"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"Sony"
	Option		"DPMS"
#	HorizSync	30-70
#	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Left Screen"
	Device		"NVIDIA GeForce 6800 DVI"
	Monitor		"Compaq"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x768" "1024x768"
	EndSubSection
EndSection
############### PCI Card Analog #########################################
Section "Device"
	Identifier	"NVIDIA GeForce 5200 Analog"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
#	Option         	"MetaModes"        "1280x1024,1280x1024"
#	Screen		2
EndSection

Section "Monitor"
	Identifier	"Compaq"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Right Screen"
	Device		"NVIDIA GeForce 5200 Analog"
	Monitor		"Compaq"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x768" "1024x768"
	EndSubSection
EndSection
############### PCI Card DVI #########################################
#Section "Device"
#	Identifier	"NVIDIA GeForce 5200 DVI"
#	Driver		"nvidia"
#	BusID		"PCI:2:0:0"
#EndSection
#
#Section "Monitor"
#	Identifier	"TBD"
#	Option		"DPMS"
#	HorizSync	30-70
#	VertRefresh	50-160
#EndSection
#
#Section "Screen"
#	Identifier	"Extra Screen"
#	Device		"NVIDIA GeForce 5200 DVI"
#	Monitor		"Compaq"
#	DefaultDepth	24
#	SubSection "Display"
#		Depth		24
#		Modes		"1280x1024" "1152x768" "1024x768"
#	EndSubSection
#EndSection
######################################################################

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Center Screen"
	Screen		"Right Screen" RightOf "Center Screen"
	Screen		"Left Screen" LeftOf "Center Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "ServerFlags"
        Option "Xinerama" "on"
EndSection

Section "Extensions"
          Option  "Composite" "Enable"
EndSection

```

---

### Post by Sjun on 2006-11-21
> **67comet said:**
> FINALLY .. I got it .. it was as simple as naming each monitor for where it was going to be displayed, and adding the Screen 0 and Screen 1 on the AGP card's infomation.

Here is my current xorg.conf file. I dis-enabled compiz/XGL for now, but that is the next big hurtle. Thripple monitor support shouldn't be an issue. I had dual's running XGL like clockwork.

Cheers,
Justin
I for myself finally have managed to get two GPU's (+ 2 Screens) working next to each other.

I can move my mouse pointer from the left to the right screen and vice versa, but i can't drag any windows from one screen to the other. :-k 

Is there any option i should have set in xorg.conf?

---

