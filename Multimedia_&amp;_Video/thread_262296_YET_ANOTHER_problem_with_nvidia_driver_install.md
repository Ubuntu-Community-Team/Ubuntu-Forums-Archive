---
title: "YET ANOTHER problem with nvidia driver install"
date: 2006-09-21
forum: Multimedia &amp; Video
---

### Post by el_ricardo on 2006-09-21
ok so i've been trying to install the latest nvidia drivers on my xubuntu machine for 2 days now, with no luck. I've overcome the API mismatch error, with a lot of work, and upon overcoming it thought "ah, thank god thats over" but no, just recieved this error:

```

FATAL: error inserting nvidia (/lib/modules/2.6.15-23-386/kernel/dribers/video/nvidia.ko): Unknown symbol in module, or unknown parameter (see dmesg)

(EE) NVIDIA(0): failed to load the NVIDIA kernel module!
(EE) NVIDIA(0): ***Aborting***
(EE) Screen(s) found, but none habe a usable configuration.

```

so i looked at dmesg:

```

[4294760.76600] nvidia: Unknown parameter 'NVreg_SoftEDIDd'

```

please help!

---

### Post by tseliot on 2006-09-21
How did you install the driver?

Did you use both the installer from Nvidia's website and the driver in the repositories? If so, you might have some problem (driver mismatch)

---

### Post by el_ricardo on 2006-09-21
at first i used nvidia-glx, then i tried using the 8774 run file from nvidia, forgetting to remove the nvidia-glx first, I discovered that this is probably where i went wrong from sifting through the forums and uninstalled the glx drivers, and the nvidia ones, and started over with the RUN file. I edited the linux restricted modules conf file and put "nv" at the bottom as well before i installed the drivers

I'm confused now, hope it wasn't as confusing to read as it was to write lol

<edit>cool, you wrote envy, unfortunatly that didn't work either :( but still thats a good script, i used it on my other machine!

---

### Post by tseliot on 2006-09-21
Ok, let's try to diagnose the error:

Boot with the "nv" driver in your xorg.conf

Then (after Ubuntu has booted) Set the driver to "nvidia" in your /etc/X11/xorg.conf
Log out and Press CTRL+ALT+F1

You will get to the command line (no GUI)
Type:

```
sudo /etc/init.d/gdm stop (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm stop (if you use KDM)
```

Then:
```
startx -- -verbose 5 -logverbose 5
```

You will see several lines with the same error.

Then if you can't get to the command line press CTRL+ALT+F1 or CTRL+C (select NO if it asks you if you want to see the output of the error or something like that)

Then type this in order to copy the output of the error to your home folder:
```
sudo cp /var/log/Xorg.0.log /home/your_username/Xorg.0.log
```
(Of course you have to replace "your_username" with your username)

Access the GNOME or KDE again in the following way:
```
sudo nano /etc/X11/xorg.conf
```
Set the driver back to "nv" instead of "nvidia"
CTRL+O to save
CTRL+X to exit

Then
```
sudo /etc/init.d/gdm restart (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm restart (if you use KDM)
```


Post the content of that file (which you can find under /home/your_username/Xorg.0.log )

---

### Post by el_ricardo on 2006-09-21
OK, contents of Xorg.0.log:

```


X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux ubuntu 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Sep 21 22:38:04 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "nvidia geforce mx440"
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
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,7120 card 109f,3151 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,7121 card 8086,7121 rev 03 class 03,00,00 hdr 00
(II) PCI: 00:1e:0: chip 8086,2418 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,2410 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,2411 card 8086,2411 rev 02 class 01,01,80 hdr 00
(II) PCI: 00:1f:2: chip 8086,2412 card 8086,2412 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,2415 card 109f,3151 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:0d:0: chip 1274,5880 card 1274,2000 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:0e:0: chip 10de,0181 card 3842,b089 rev c1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:30:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf1000000 - 0xf1ffffff (0x1000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI: (0:1:0) Intel Corporation 82810 CGC [Chipset Graphics Controller] rev 3, Mem @ 0xf4000000/26, 0xf0000000/19
(--) PCI:*(1:14:0) nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] rev 193, Mem @ 0xf1000000/24, 0xf8000000/26
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
(II) Active PCI resource ranges:
	[0] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[1] -1	0	0xf1000000 - 0xf1ffffff (0x1000000) MX[B](B)
	[2] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[3] -1	0	0x00001840 - 0x0000187f (0x40) IX[B]
	[4] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[5] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[6] -1	0	0x00001800 - 0x0000180f (0x10) IX[B]
(II) Inactive PCI resource ranges:
	[0] -1	0	0xf0000000 - 0xf007ffff (0x80000) MX[B](B)
	[1] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[1] -1	0	0xf1000000 - 0xf1ffffff (0x1000000) MX[B](B)
	[2] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[3] -1	0	0x00001840 - 0x0000187f (0x40) IX[B]
	[4] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[5] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[6] -1	0	0x00001800 - 0x0000180f (0x10) IX[B]
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xf0000000 - 0xf007ffff (0x80000) MX[B](B)
	[1] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
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
	[4] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[5] -1	0	0xf1000000 - 0xf1ffffff (0x1000000) MX[B](B)
	[6] -1	0	0xf0000000 - 0xf007ffff (0x80000) MX[B](B)
	[7] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[8] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[9] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[10] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[11] -1	0	0x00001840 - 0x0000187f (0x40) IX[B]
	[12] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[13] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[14] -1	0	0x00001800 - 0x0000180f (0x10) IX[B]
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
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8774
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
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8774
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
(II) NVIDIA dlloader X Driver  1.0-8774  Tue Aug  1 20:55:35 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:0e:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Found 1 NVIDIA X Screens
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
	[4] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[5] -1	0	0xf1000000 - 0xf1ffffff (0x1000000) MX[B](B)
	[6] -1	0	0xf0000000 - 0xf007ffff (0x80000) MX[B](B)
	[7] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[8] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[9] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[10] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[11] -1	0	0x00001840 - 0x0000187f (0x40) IX[B]
	[12] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[13] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[14] -1	0	0x00001800 - 0x0000180f (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[5] -1	0	0xf1000000 - 0xf1ffffff (0x1000000) MX[B](B)
	[6] -1	0	0xf0000000 - 0xf007ffff (0x80000) MX[B](B)
	[7] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[8] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[9] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[10] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[14] -1	0	0x00001840 - 0x0000187f (0x40) IX[B]
	[15] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[16] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[17] -1	0	0x00001800 - 0x0000180f (0x10) IX[B]
	[18] 0	0	0x200003b0 - 0x200003bb (0xc) IS[B]
	[19] 0	0	0x200003c0 - 0x200003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(==) NVIDIA(0): Using HW cursor
(**) NVIDIA(0): Enabling RENDER acceleration
(==) NVIDIA(0): Video key set to default value of 0x101fe
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

---

### Post by el_ricardo on 2006-09-21
fixed it - there was a typo in my modprobe config, damned case sensitive config files!

---

