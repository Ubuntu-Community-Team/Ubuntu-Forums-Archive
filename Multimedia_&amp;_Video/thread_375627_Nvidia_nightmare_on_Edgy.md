---
title: "Nvidia nightmare on Edgy"
date: 2007-03-04
forum: Multimedia &amp; Video
---

### Post by zeroblitzt on 2007-03-04
I've been trying all night to get GLX working again, but to no avail.

The most common error I've been getting is:
```
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

```
Note that everything on my system worked like a charm in Dapper!


But anyway, thats not even my main problem. Everytime I boot now, it for some reason doesn't start the X server. It says "no screens found" and "could not load kernel module". Even if I edit the xorg.conf file (I did, and I typed "startx", which is where I am now... x is running fine), when I reboot the error comes back.

I have no idea what to do.

I have an Nvidia Geforce MX 4000 card, and I'm using the legacy driver, as thats the one i've used in Dapper.

---

### Post by r4ik on 2007-03-04
You could try,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck !

---

### Post by zeroblitzt on 2007-03-04
Unfortunately, I already have, and it hasn't helped.

---

### Post by r4ik on 2007-03-04
-

---

### Post by r4ik on 2007-03-04
Sorry,

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FCompiz_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FCompiz_.28NVIDIA.29)

---

### Post by sbergman27 on 2007-03-04
Please post the output of:

dpkg -l | grep -e nvidia -e restricted

uname -a

lsmod | grep nvidia

and the contents of:

/etc/X11/xorg.conf

and

/var/log/Xorg.0.log

Also, if you have installed the driver using nvidia's installer in the past, and are now installing from the repository, this could be causing a problem.

---

### Post by zeroblitzt on 2007-03-04
```
knovak@knova:~$ dpkg -l | grep -e nvidia -e restricted
ii  linux-restricted-modules-2.6.15-26-386 2.6.15.11-4                           Non-free Linux 2.6.15 modules on 386
ii  linux-restricted-modules-2.6.15-27-386 2.6.15.12-1                           Non-free Linux 2.6.15 modules on 386
ii  linux-restricted-modules-2.6.15-28-386 2.6.15.12-28.1                        Non-free Linux 2.6.15 modules on 386
ii  linux-restricted-modules-2.6.17-10-386 2.6.17.7-10.1                         Non-free Linux 2.6.17 modules on 386
ii  linux-restricted-modules-2.6.17-11-386 2.6.17.7-11.2                         Non-free Linux 2.6.17 modules on 386
ii  linux-restricted-modules-386           2.6.17.11                             Restricted Linux modules on 386.
ii  linux-restricted-modules-common        2.6.17.7-11.2                         Non-free Linux 2.6.17 modules helper script
ii  nvidia-glx-legacy                      1.0.7184+2.6.17.5-11                  NVIDIA binary XFree86 4.x/X.Org 'legacy' dri
ii  nvidia-glx-legacy-dev                  1.0.7184+2.6.17.5-11                  NVIDIA binary XFree86 4.x/X.Org 'legacy' dri
ii  nvidia-kernel-common                   20051028+1ubuntu7                     NVIDIA binary kernel module common files
ii  nvidia-settings                        1.0-3ubuntu7                          Tool of configuring the NVIDIA graphics driv
ii  nvidia-xconfig                         1.0+20051122-2                        The NVIDIA X Configuration Tool

```

uname -a:
```
Linux knova 2.6.17-11-386 #2 Thu Feb 1 19:50:13 UTC 2007 i686 GNU/Linux

```

lsmod | grep nvidia:
```
nvidia               3931148  8 
agpgart                33456  2 nvidia,amd_k7_agp

```


My Xorg.conf file: (i cut out the commented out lines near the top to save space)
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```


And finally, my X log:
```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux knova 2.6.17-11-386 #2 Thu Feb 1 19:50:13 UTC 2007 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Mar  4 09:10:22 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/X11/fonts/misc,
	/usr/share/X11/fonts/100dpi/:unscaled,
	/usr/share/X11/fonts/75dpi/:unscaled,
	/usr/share/X11/fonts/Type1,
	/usr/share/X11/fonts/100dpi,
	/usr/share/X11/fonts/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1022,7006 card 0000,0000 rev 25 class 06,00,00 hdr 80
(II) PCI: 00:01:0: chip 1022,7007 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:07:0: chip 1022,7408 card 0000,0000 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:07:1: chip 1022,7409 card 0000,0000 rev 07 class 01,01,8a hdr 00
(II) PCI: 00:07:3: chip 1022,740b card 0000,0000 rev 03 class 06,80,00 hdr 00
(II) PCI: 00:07:4: chip 1022,740c card 0000,0000 rev 06 class 0c,03,10 hdr 00
(II) PCI: 00:08:0: chip 1102,0007 card 1102,100a rev 00 class 04,01,00 hdr 00
(II) PCI: 00:09:0: chip 1105,8300 card 0000,0000 rev 02 class 04,80,00 hdr 00
(II) PCI: 00:0a:0: chip 1317,0985 card 1317,0570 rev 11 class 02,00,00 hdr 00
(II) PCI: 01:05:0: chip 10de,0185 card 1682,2018 rev c1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000e (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xe1ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:7:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:5:0) nVidia Corporation NV18 [GeForce4 MX 4000 AGP 8x] rev 193, Mem @ 0xe0000000/24, 0xd8000000/27
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
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xd7ffffff to 0xcfffffff
(II) PCI Memory resource overlap reduced 0xe3100000 from 0xe3100fff to 0xe30fffff
(II) PCI I/O resource overlap reduced 0x0000e000 from 0x0000e003 to 0x0000dfff
(II) Active PCI resource ranges:
	[0] -1	0	0xe3101000 - 0xe31013ff (0x400) MX[B]
	[1] -1	0	0xe3000000 - 0xe30fffff (0x100000) MX[B]
	[2] -1	0	0xe3102000 - 0xe3102fff (0x1000) MX[B]
	[3] -1	0	0xe3100000 - 0xe30fffff (0x0) MX[B]O
	[4] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[5] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[6] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[7] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[8] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[9] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
(II) Inactive PCI resource ranges:
	[0] -1	0	0x0000e000 - 0x0000dfff (0x0) IX[B]O
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe3101000 - 0xe31013ff (0x400) MX[B]
	[1] -1	0	0xe3000000 - 0xe30fffff (0x100000) MX[B]
	[2] -1	0	0xe3102000 - 0xe3102fff (0x1000) MX[B]
	[3] -1	0	0xe3100000 - 0xe30fffff (0x0) MX[B]O
	[4] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[5] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[6] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[7] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[8] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[9] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0x0000e000 - 0x0000dfff (0x0) IX[B]O
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
	[4] -1	0	0xe3101000 - 0xe31013ff (0x400) MX[B]
	[5] -1	0	0xe3000000 - 0xe30fffff (0x100000) MX[B]
	[6] -1	0	0xe3102000 - 0xe3102fff (0x1000) MX[B]
	[7] -1	0	0xe3100000 - 0xe30fffff (0x0) MX[B]O
	[8] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[9] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[14] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[15] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[16] -1	0	0x0000e000 - 0x0000dfff (0x0) IX[B]O
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
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
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7184
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7184
	Module class: XFree86 Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) NVIDIA dlloader X Driver  1.0-7184  Tue Aug  1 18:40:06 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:05:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe3101000 - 0xe31013ff (0x400) MX[B]
	[5] -1	0	0xe3000000 - 0xe30fffff (0x100000) MX[B]
	[6] -1	0	0xe3102000 - 0xe3102fff (0x1000) MX[B]
	[7] -1	0	0xe3100000 - 0xe30fffff (0x0) MX[B]O
	[8] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[9] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[14] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[15] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[16] -1	0	0x0000e000 - 0x0000dfff (0x0) IX[B]O
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe3101000 - 0xe31013ff (0x400) MX[B]
	[5] -1	0	0xe3000000 - 0xe30fffff (0x100000) MX[B]
	[6] -1	0	0xe3102000 - 0xe3102fff (0x1000) MX[B]
	[7] -1	0	0xe3100000 - 0xe30fffff (0x0) MX[B]O
	[8] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[9] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[17] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[18] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[19] -1	0	0x0000e000 - 0x0000dfff (0x0) IX[B]O
	[20] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[21] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(--) NVIDIA(0): Linear framebuffer at 0xD8000000
(--) NVIDIA(0): MMIO registers at 0xE0000000
(II) NVIDIA(0): NVIDIA GPU detected as: GeForce4 MX 4000
(--) NVIDIA(0): VideoBIOS: 04.18.20.36.02
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(II) NVIDIA(0): Detected AGP rate: 1X
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(II) NVIDIA(0): Connected display device(s): CRT-0
(--) NVIDIA(0): Display device CRT-0: maximum pixel clock at  8 bpp: 350 MHz
(--) NVIDIA(0): Display device CRT-0: maximum pixel clock at 16 bpp: 350 MHz
(--) NVIDIA(0): Display device CRT-0: maximum pixel clock at 32 bpp: 350 MHz
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) NVIDIA(0): Generic Monitor: Using default hsync range of 30.00-70.00 kHz
(II) NVIDIA(0): Generic Monitor: Using default vrefresh range of 50.00-160.00 Hz
(II) NVIDIA(0): Clock range:  12.00 to 350.00 MHz
(WW) (1280x960,Generic Monitor) mode clock 148.5MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1280x960" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x480" (hsync out of range)
(WW) (1280x1024,Generic Monitor) mode clock 135MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(WW) (1280x1024,Generic Monitor) mode clock 157.5MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(WW) (1600x1200,Generic Monitor) mode clock 162MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(WW) (1600x1200,Generic Monitor) mode clock 175.5MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(WW) (1600x1200,Generic Monitor) mode clock 189MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(WW) (1600x1200,Generic Monitor) mode clock 202.5MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(WW) (1600x1200,Generic Monitor) mode clock 229.5MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(WW) (800x600,Generic Monitor) mode clock 114.75MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(WW) (1792x1344,Generic Monitor) mode clock 204.8MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(WW) (1792x1344,Generic Monitor) mode clock 261MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(WW) (896x672,Generic Monitor) mode clock 130.5MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(WW) (1856x1392,Generic Monitor) mode clock 218.3MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(WW) (1856x1392,Generic Monitor) mode clock 288MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(WW) (928x696,Generic Monitor) mode clock 144MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(WW) (1920x1440,Generic Monitor) mode clock 234MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(WW) (960x720,Generic Monitor) mode clock 117MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(WW) (1920x1440,Generic Monitor) mode clock 297MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(WW) (960x720,Generic Monitor) mode clock 148.5MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(WW) (1152x864,Generic Monitor) mode clock 121.5MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1152x864" (hsync out of range)
(II) NVIDIA(0): Not using default mode "576x432" (hsync out of range)
(WW) (1400x1050,Generic Monitor) mode clock 122MHz exceeds DDC maximum 110MHz
(WW) (1400x1050,Generic Monitor) mode clock 151MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(WW) (1400x1050,Generic Monitor) mode clock 155.8MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(WW) (1400x1050,Generic Monitor) mode clock 184MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(WW) (1680x1050,Generic Monitor) mode clock 147.14MHz exceeds DDC maximum 110MHz
(WW) (1920x1200,Generic Monitor) mode clock 193.16MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x600" (hsync out of range)
(WW) (1920x1200,Generic Monitor) mode clock 230MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1920x1200" (hsync out of range)
(WW) (960x600,Generic Monitor) mode clock 115MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "960x600" (hsync out of range)
(WW) (1920x1440,Generic Monitor) mode clock 341.35MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(WW) (960x720,Generic Monitor) mode clock 170.675MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(WW) (2048x1536,Generic Monitor) mode clock 266.95MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(WW) (1024x768,Generic Monitor) mode clock 133.475MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(WW) (2048x1536,Generic Monitor) mode clock 340.48MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(WW) (1024x768,Generic Monitor) mode clock 170.24MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(WW) (2048x1536,Generic Monitor) mode clock 388.04MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(WW) (1024x768,Generic Monitor) mode clock 194.02MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1440x900" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x960" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x800" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1152x864" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x768" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1152x768" (width too large for virtual size)
(WW) NVIDIA(0): Not using mode "840x525" (height 1050 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1024)
(WW) NVIDIA(0): Not using mode "700x525" (height 1050 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1024)
(WW) NVIDIA(0): Not using mode "576x384":
(WW) NVIDIA(0):   horizontal sync start (589) not a multiple of 8
(WW) NVIDIA(0): Not using mode "360x200":
(WW) NVIDIA(0):   horizontal sync start (378) not a multiple of 8
(**) NVIDIA(0): Validated modes for display device CRT-0:
(**) NVIDIA(0):      Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(**) NVIDIA(0):      Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(**) NVIDIA(0):      Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 44.9 MHz, 35.5 kHz, 87.0 Hz (I)
(**) NVIDIA(0):      Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(**) NVIDIA(0):      Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(**) NVIDIA(0):      Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(**) NVIDIA(0):      Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(**) NVIDIA(0):      Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(**) NVIDIA(0):      Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(**) NVIDIA(0):      Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 39.4 MHz, 60.1 kHz, 75.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 22.4 MHz, 35.5 kHz, 86.9 Hz (D)
(**) NVIDIA(0):      Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(++) NVIDIA(0): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B]
	[1] 0	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xe3101000 - 0xe31013ff (0x400) MX[B]
	[7] -1	0	0xe3000000 - 0xe30fffff (0x100000) MX[B]
	[8] -1	0	0xe3102000 - 0xe3102fff (0x1000) MX[B]
	[9] -1	0	0xe3100000 - 0xe30fffff (0x0) MX[B]O
	[10] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[11] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[19] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[20] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[21] -1	0	0x0000e000 - 0x0000dfff (0x0) IX[B]O
	[22] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[23] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1024x768"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
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
(EE) GLX is not supported with the Composite extension
error opening security policy file /usr/lib/xserver/SecurityPolicy
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
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc104)+us" };
    xkb_geometry             { include "pc(pc104)" };
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!

```


I'd like to add, im in X now. My computer, after rebooting, ALWAYS starts in text mode, a popup comes up and tells me the X server couldnt start (no screens found / nvidia kernel module failed to load), so I just do "sudo nvidia-glx-config enable", and usually that lets me start the X server.

---

### Post by sbergman27 on 2007-03-04
The MX 4000 is a geforce4 card, right?

So you should not be using the legacy glx.  You should be using:

 nvidia-glx 1.0.8776+2.6.17.7-11.2

Remove nvidia-glx-legacy 1.0.7184+2.6.17.5-11 and install the correct one and I'll bet it will work.

-Steve

---

### Post by zeroblitzt on 2007-03-04
hmm, thats strange that you say that, because I googled it and it came up as a legacy card, and I've used the legacy driver in the past.


But I'm going to take your word for it. I'll post the results in a few minutes.

---

### Post by sbergman27 on 2007-03-04
I believe there was a GeForce2 MX400.  In fact, I had one back in the day.  But your Xorg log file clearly identifies this as GeForce4.

---

### Post by zeroblitzt on 2007-03-04
Alright, it worked. Thank you.


But now I guess I can put forth my other problem: GLX not working.

For example, when I type "glxgears", I get this as the output:

```
knovak@knova:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

```


Same goes for when I try to run any game.

"load 'glx'" is in my xorg.conf file, so I don't see what the problem is here.


Heres the output of glxinfo:
```
knovak@knova:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x23 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x24 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x25 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x26 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x27 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x28 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x29 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x2a 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x2b 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x2c 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x2d 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x2e 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x2f 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x30 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x31 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x32 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x33 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x34 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x35 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x36 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x37 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x38 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x91 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

```

---

### Post by sbergman27 on 2007-03-04
Oops.  You are right.  Legacy is the proper glx for that chipset.

However, look at this from the log:

(EE) GLX is not supported with the Composite extension

Try putting:

Section "Extensions"
    Option "Composite" "Off"
EndSection

at the end of your xorg.conf 

I believe that Composite is on by default in Edgy.

---

### Post by zeroblitzt on 2007-03-04
Errm, so should I still keep using the driver I'm using now?

---

### Post by sbergman27 on 2007-03-04
No.  Sorry for misleading you.  I did not realize that any of the GeForce4 cards were classified as legacy.   Use the glx that you had originally.

---

### Post by zeroblitzt on 2007-03-04
Well, I switched back to the nvidia-glx-legacy package, and its saying no screens found again.

---

### Post by sbergman27 on 2007-03-04
With Composite turned off?

Post the latest Xorg.0.log and lets see what it says.

---

### Post by zeroblitzt on 2007-03-04
```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux knova 2.6.17-11-386 #2 Thu Feb 1 19:50:13 UTC 2007 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Mar  4 10:15:11 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/X11/fonts/misc,
	/usr/share/X11/fonts/100dpi/:unscaled,
	/usr/share/X11/fonts/75dpi/:unscaled,
	/usr/share/X11/fonts/Type1,
	/usr/share/X11/fonts/100dpi,
	/usr/share/X11/fonts/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is disabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1022,7006 card 0000,0000 rev 25 class 06,00,00 hdr 80
(II) PCI: 00:01:0: chip 1022,7007 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:07:0: chip 1022,7408 card 0000,0000 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:07:1: chip 1022,7409 card 0000,0000 rev 07 class 01,01,8a hdr 00
(II) PCI: 00:07:3: chip 1022,740b card 0000,0000 rev 03 class 06,80,00 hdr 00
(II) PCI: 00:07:4: chip 1022,740c card 0000,0000 rev 06 class 0c,03,10 hdr 00
(II) PCI: 00:08:0: chip 1102,0007 card 1102,100a rev 00 class 04,01,00 hdr 00
(II) PCI: 00:09:0: chip 1105,8300 card 0000,0000 rev 02 class 04,80,00 hdr 00
(II) PCI: 00:0a:0: chip 1317,0985 card 1317,0570 rev 11 class 02,00,00 hdr 00
(II) PCI: 01:05:0: chip 10de,0185 card 1682,2018 rev c1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000e (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xe1ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:7:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:5:0) nVidia Corporation NV18 [GeForce4 MX 4000 AGP 8x] rev 193, Mem @ 0xe0000000/24, 0xd8000000/27
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
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xd7ffffff to 0xcfffffff
(II) PCI Memory resource overlap reduced 0xe3100000 from 0xe3100fff to 0xe30fffff
(II) PCI I/O resource overlap reduced 0x0000e000 from 0x0000e003 to 0x0000dfff
(II) Active PCI resource ranges:
	[0] -1	0	0xe3101000 - 0xe31013ff (0x400) MX[B]
	[1] -1	0	0xe3000000 - 0xe30fffff (0x100000) MX[B]
	[2] -1	0	0xe3102000 - 0xe3102fff (0x1000) MX[B]
	[3] -1	0	0xe3100000 - 0xe30fffff (0x0) MX[B]O
	[4] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[5] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[6] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[7] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[8] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[9] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
(II) Inactive PCI resource ranges:
	[0] -1	0	0x0000e000 - 0x0000dfff (0x0) IX[B]O
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe3101000 - 0xe31013ff (0x400) MX[B]
	[1] -1	0	0xe3000000 - 0xe30fffff (0x100000) MX[B]
	[2] -1	0	0xe3102000 - 0xe3102fff (0x1000) MX[B]
	[3] -1	0	0xe3100000 - 0xe30fffff (0x0) MX[B]O
	[4] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[5] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[6] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[7] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[8] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[9] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0x0000e000 - 0x0000dfff (0x0) IX[B]O
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
	[4] -1	0	0xe3101000 - 0xe31013ff (0x400) MX[B]
	[5] -1	0	0xe3000000 - 0xe30fffff (0x100000) MX[B]
	[6] -1	0	0xe3102000 - 0xe3102fff (0x1000) MX[B]
	[7] -1	0	0xe3100000 - 0xe30fffff (0x0) MX[B]O
	[8] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[9] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[14] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[15] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[16] -1	0	0x0000e000 - 0x0000dfff (0x0) IX[B]O
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
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
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7184
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7184
	Module class: XFree86 Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) NVIDIA dlloader X Driver  1.0-7184  Tue Aug  1 18:40:06 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:05:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe3101000 - 0xe31013ff (0x400) MX[B]
	[5] -1	0	0xe3000000 - 0xe30fffff (0x100000) MX[B]
	[6] -1	0	0xe3102000 - 0xe3102fff (0x1000) MX[B]
	[7] -1	0	0xe3100000 - 0xe30fffff (0x0) MX[B]O
	[8] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[9] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[14] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[15] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[16] -1	0	0x0000e000 - 0x0000dfff (0x0) IX[B]O
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe3101000 - 0xe31013ff (0x400) MX[B]
	[5] -1	0	0xe3000000 - 0xe30fffff (0x100000) MX[B]
	[6] -1	0	0xe3102000 - 0xe3102fff (0x1000) MX[B]
	[7] -1	0	0xe3100000 - 0xe30fffff (0x0) MX[B]O
	[8] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[9] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[17] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[18] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[19] -1	0	0x0000e000 - 0x0000dfff (0x0) IX[B]O
	[20] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[21] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(--) NVIDIA(0): Linear framebuffer at 0xD8000000
(--) NVIDIA(0): MMIO registers at 0xE0000000
(II) NVIDIA(0): NVIDIA GPU detected as: GeForce4 MX 4000
(--) NVIDIA(0): VideoBIOS: 04.18.20.36.02
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(II) NVIDIA(0): Detected AGP rate: 1X
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(II) NVIDIA(0): Connected display device(s): CRT-0
(--) NVIDIA(0): Display device CRT-0: maximum pixel clock at  8 bpp: 350 MHz
(--) NVIDIA(0): Display device CRT-0: maximum pixel clock at 16 bpp: 350 MHz
(--) NVIDIA(0): Display device CRT-0: maximum pixel clock at 32 bpp: 350 MHz
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) NVIDIA(0): Generic Monitor: Using default hsync range of 30.00-70.00 kHz
(II) NVIDIA(0): Generic Monitor: Using default vrefresh range of 50.00-160.00 Hz
(II) NVIDIA(0): Clock range:  12.00 to 350.00 MHz
(WW) (1280x960,Generic Monitor) mode clock 148.5MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1280x960" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x480" (hsync out of range)
(WW) (1280x1024,Generic Monitor) mode clock 135MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(WW) (1280x1024,Generic Monitor) mode clock 157.5MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(WW) (1600x1200,Generic Monitor) mode clock 162MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(WW) (1600x1200,Generic Monitor) mode clock 175.5MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(WW) (1600x1200,Generic Monitor) mode clock 189MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(WW) (1600x1200,Generic Monitor) mode clock 202.5MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(WW) (1600x1200,Generic Monitor) mode clock 229.5MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(WW) (800x600,Generic Monitor) mode clock 114.75MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(WW) (1792x1344,Generic Monitor) mode clock 204.8MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(WW) (1792x1344,Generic Monitor) mode clock 261MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(WW) (896x672,Generic Monitor) mode clock 130.5MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(WW) (1856x1392,Generic Monitor) mode clock 218.3MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(WW) (1856x1392,Generic Monitor) mode clock 288MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(WW) (928x696,Generic Monitor) mode clock 144MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(WW) (1920x1440,Generic Monitor) mode clock 234MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(WW) (960x720,Generic Monitor) mode clock 117MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(WW) (1920x1440,Generic Monitor) mode clock 297MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(WW) (960x720,Generic Monitor) mode clock 148.5MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(WW) (1152x864,Generic Monitor) mode clock 121.5MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1152x864" (hsync out of range)
(II) NVIDIA(0): Not using default mode "576x432" (hsync out of range)
(WW) (1400x1050,Generic Monitor) mode clock 122MHz exceeds DDC maximum 110MHz
(WW) (1400x1050,Generic Monitor) mode clock 151MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(WW) (1400x1050,Generic Monitor) mode clock 155.8MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(WW) (1400x1050,Generic Monitor) mode clock 184MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(WW) (1680x1050,Generic Monitor) mode clock 147.14MHz exceeds DDC maximum 110MHz
(WW) (1920x1200,Generic Monitor) mode clock 193.16MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x600" (hsync out of range)
(WW) (1920x1200,Generic Monitor) mode clock 230MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1920x1200" (hsync out of range)
(WW) (960x600,Generic Monitor) mode clock 115MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "960x600" (hsync out of range)
(WW) (1920x1440,Generic Monitor) mode clock 341.35MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(WW) (960x720,Generic Monitor) mode clock 170.675MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(WW) (2048x1536,Generic Monitor) mode clock 266.95MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(WW) (1024x768,Generic Monitor) mode clock 133.475MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(WW) (2048x1536,Generic Monitor) mode clock 340.48MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(WW) (1024x768,Generic Monitor) mode clock 170.24MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(WW) (2048x1536,Generic Monitor) mode clock 388.04MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(WW) (1024x768,Generic Monitor) mode clock 194.02MHz exceeds DDC maximum 110MHz
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1440x900" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x960" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x800" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1152x864" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x768" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1152x768" (width too large for virtual size)
(WW) NVIDIA(0): Not using mode "840x525" (height 1050 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1024)
(WW) NVIDIA(0): Not using mode "700x525" (height 1050 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1024)
(WW) NVIDIA(0): Not using mode "576x384":
(WW) NVIDIA(0):   horizontal sync start (589) not a multiple of 8
(WW) NVIDIA(0): Not using mode "360x200":
(WW) NVIDIA(0):   horizontal sync start (378) not a multiple of 8
(**) NVIDIA(0): Validated modes for display device CRT-0:
(**) NVIDIA(0):      Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(**) NVIDIA(0):      Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(**) NVIDIA(0):      Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 44.9 MHz, 35.5 kHz, 87.0 Hz (I)
(**) NVIDIA(0):      Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(**) NVIDIA(0):      Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(**) NVIDIA(0):      Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(**) NVIDIA(0):      Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(**) NVIDIA(0):      Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(**) NVIDIA(0):      Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(**) NVIDIA(0):      Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 39.4 MHz, 60.1 kHz, 75.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 22.4 MHz, 35.5 kHz, 86.9 Hz (D)
(**) NVIDIA(0):      Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(++) NVIDIA(0): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B]
	[1] 0	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xe3101000 - 0xe31013ff (0x400) MX[B]
	[7] -1	0	0xe3000000 - 0xe30fffff (0x100000) MX[B]
	[8] -1	0	0xe3102000 - 0xe3102fff (0x1000) MX[B]
	[9] -1	0	0xe3100000 - 0xe30fffff (0x0) MX[B]O
	[10] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[11] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[19] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[20] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[21] -1	0	0x0000e000 - 0x0000dfff (0x0) IX[B]O
	[22] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[23] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1024x768"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
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
error opening security policy file /usr/lib/xserver/SecurityPolicy
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
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc104)+us" };
    xkb_geometry             { include "pc(pc104)" };
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
SetGrabKeysState - disabled
SetGrabKeysState - enabled

```

---

### Post by sbergman27 on 2007-03-04
Yes.  I've seen this before.

You have to get rid of the InputDevice sections that make reference to wacom:


Section "InputDevice"

    # /dev/input/event
    # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

    # /dev/input/event
    # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

    # /dev/input/event
    # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

---

### Post by zeroblitzt on 2007-03-04
Done, I've commented them out.

---

### Post by sbergman27 on 2007-03-04
With those lines commented out, Composite turned off, and using the legacy driver, that should work and get you glx.  If not, post the log again.

---

### Post by zeroblitzt on 2007-03-04
Alright, it worked. Thanks so much!

I figure instead of making a new topic, I may as well just ask here since its sort of related: Since upgrading, my bootsplash doesn't work. Instead of getting that nice black Ubuntu screen + the loading bar, I get the ugly black and white text print out. Is there a way to reinstall the splash screen?

---

### Post by sbergman27 on 2007-03-04
Wonderful!

I had that problem with usplash.  I think that I reinstalled usplash and usplash-theme-ubuntu to get it to work.

-Steve

---

### Post by bgochnauer on 2007-03-09
> **sbergman27 said:**
> With those lines commented out, Composite turned off, and using the legacy driver, that should work and get you glx.  If not, post the log again.

Hey that worked for me too! Got my OpenGL screensaver to work again.

Thanks!!!

(Kubuntu 6.1.0)

---

