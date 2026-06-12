---
title: "Nouveau regression in EDID reads."
date: 2012-06-12
forum: Multimedia Software
---

### Post by chowno on 2012-06-12
Hello, I think I am experiencing a regression in the nouveau driver that causes the EDID information to be misread.  In Ubuntu 11.10 and prior the nouveau driver would display correctly at 1920x1080 and only the nvidia driver would need an EDID override to correctly display at that resolution.  Now in 12.04 I am experiencing the same problem with nouveau that I was experiencing with nvidia but I cannot override the EDID reading with a saved version.  I only have up to 1440x900, or 1280x1024 depending on what is considered 'higher', which is not so bad but not what I want.  Any ideas on what to do here?  Thanks!

My system spec:
VGA: GeForce 5200 FX (Connected through DVI)
Monitor: Samsung Syncmaster P2770H

Here is my Xorg.0.log:
```

[   273.103] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[   273.103] X Protocol Version 11, Revision 0
[   273.103] Build Operating System: Linux 2.6.24-31-server i686 Ubuntu
[   273.103] Current Operating System: Linux compy9000 3.2.0-24-generic #39-Ubuntu SMP Mon May 21 16:51:22 UTC 2012 i686
[   273.103] Kernel command line: BOOT_IMAGE=/vmlinuz-3.2.0-24-generic root=UUID=3ca8e93d-f633-42a4-ab4e-dd860e2b11d5 ro quiet splash vt.handoff=7
[   273.103] Build Date: 07 May 2012  11:39:37PM
[   273.103] xorg-server 2:1.11.4-0ubuntu10.2 (For technical support please see http://www.ubuntu.com/support) 
[   273.103] Current version of pixman: 0.24.4
[   273.103] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   273.103] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   273.108] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jun 12 12:14:33 2012
[   273.108] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   273.109] (==) No Layout section.  Using the first Screen section.
[   273.109] (==) No screen section available. Using defaults.
[   273.109] (**) |-->Screen "Default Screen Section" (0)
[   273.109] (**) |   |-->Monitor "<default monitor>"
[   273.109] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[   273.109] (==) Automatically adding devices
[   273.109] (==) Automatically enabling devices
[   273.109] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   273.109] 	Entry deleted from font path.
[   273.109] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   273.109] 	Entry deleted from font path.
[   273.109] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   273.109] 	Entry deleted from font path.
[   273.110] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   273.110] 	Entry deleted from font path.
[   273.110] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   273.110] 	Entry deleted from font path.
[   273.110] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[   273.110] 	Entry deleted from font path.
[   273.110] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[   273.110] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   273.110] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   273.110] (II) Loader magic: 0x7065a0
[   273.110] (II) Module ABI versions:
[   273.110] 	X.Org ANSI C Emulation: 0.4
[   273.110] 	X.Org Video Driver: 11.0
[   273.110] 	X.Org XInput driver : 16.0
[   273.110] 	X.Org Server Extension : 6.0
[   273.110] (--) PCI:*(0:1:0:0) 10de:0322:1458:3103 rev 161, Mem @ 0xe0000000/16777216, 0xd8000000/134217728, BIOS @ 0x????????/131072
[   273.114] (II) Open ACPI successful (/var/run/acpid.socket)
[   273.114] (II) LoadModule: "extmod"
[   273.115] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   273.118] (II) Module extmod: vendor="X.Org Foundation"
[   273.118] 	compiled for 1.11.3, module version = 1.0.0
[   273.118] 	Module class: X.Org Server Extension
[   273.118] 	ABI class: X.Org Server Extension, version 6.0
[   273.118] (II) Loading extension MIT-SCREEN-SAVER
[   273.118] (II) Loading extension XFree86-VidModeExtension
[   273.118] (II) Loading extension XFree86-DGA
[   273.118] (II) Loading extension DPMS
[   273.118] (II) Loading extension XVideo
[   273.118] (II) Loading extension XVideo-MotionCompensation
[   273.118] (II) Loading extension X-Resource
[   273.118] (II) LoadModule: "dbe"
[   273.119] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   273.119] (II) Module dbe: vendor="X.Org Foundation"
[   273.119] 	compiled for 1.11.3, module version = 1.0.0
[   273.119] 	Module class: X.Org Server Extension
[   273.119] 	ABI class: X.Org Server Extension, version 6.0
[   273.119] (II) Loading extension DOUBLE-BUFFER
[   273.119] (II) LoadModule: "glx"
[   273.119] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   273.120] (II) Module glx: vendor="X.Org Foundation"
[   273.120] 	compiled for 1.11.3, module version = 1.0.0
[   273.120] 	ABI class: X.Org Server Extension, version 6.0
[   273.120] (==) AIGLX enabled
[   273.120] (II) Loading extension GLX
[   273.120] (II) LoadModule: "record"
[   273.120] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   273.120] (II) Module record: vendor="X.Org Foundation"
[   273.121] 	compiled for 1.11.3, module version = 1.13.0
[   273.121] 	Module class: X.Org Server Extension
[   273.121] 	ABI class: X.Org Server Extension, version 6.0
[   273.121] (II) Loading extension RECORD
[   273.121] (II) LoadModule: "dri"
[   273.121] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   273.121] (II) Module dri: vendor="X.Org Foundation"
[   273.121] 	compiled for 1.11.3, module version = 1.0.0
[   273.121] 	ABI class: X.Org Server Extension, version 6.0
[   273.121] (II) Loading extension XFree86-DRI
[   273.121] (II) LoadModule: "dri2"
[   273.122] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   273.122] (II) Module dri2: vendor="X.Org Foundation"
[   273.122] 	compiled for 1.11.3, module version = 1.2.0
[   273.122] 	ABI class: X.Org Server Extension, version 6.0
[   273.122] (II) Loading extension DRI2
[   273.122] (==) Matched nvidia as autoconfigured driver 0
[   273.122] (==) Matched nouveau as autoconfigured driver 1
[   273.122] (==) Matched nv as autoconfigured driver 2
[   273.122] (==) Matched vesa as autoconfigured driver 3
[   273.122] (==) Matched fbdev as autoconfigured driver 4
[   273.122] (==) Assigned the driver to the xf86ConfigLayout
[   273.122] (II) LoadModule: "nvidia"
[   273.123] (WW) Warning, couldn't open module nvidia
[   273.123] (II) UnloadModule: "nvidia"
[   273.123] (II) Unloading nvidia
[   273.123] (EE) Failed to load module "nvidia" (module does not exist, 0)
[   273.123] (II) LoadModule: "nouveau"
[   273.131] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   273.132] (II) Module nouveau: vendor="X.Org Foundation"
[   273.132] 	compiled for 1.11.3, module version = 0.0.16
[   273.132] 	Module class: X.Org Video Driver
[   273.132] 	ABI class: X.Org Video Driver, version 11.0
[   273.132] (II) LoadModule: "nv"
[   273.133] (WW) Warning, couldn't open module nv
[   273.133] (II) UnloadModule: "nv"
[   273.133] (II) Unloading nv
[   273.133] (EE) Failed to load module "nv" (module does not exist, 0)
[   273.133] (II) LoadModule: "vesa"
[   273.133] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   273.134] (II) Module vesa: vendor="X.Org Foundation"
[   273.134] 	compiled for 1.11.3, module version = 2.3.0
[   273.134] 	Module class: X.Org Video Driver
[   273.134] 	ABI class: X.Org Video Driver, version 11.0
[   273.134] (II) LoadModule: "fbdev"
[   273.134] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   273.134] (II) Module fbdev: vendor="X.Org Foundation"
[   273.138] 	compiled for 1.11.3, module version = 0.4.2
[   273.138] 	ABI class: X.Org Video Driver, version 11.0
[   273.138] (==) Matched nvidia as autoconfigured driver 0
[   273.138] (==) Matched nouveau as autoconfigured driver 1
[   273.138] (==) Matched nv as autoconfigured driver 2
[   273.138] (==) Matched vesa as autoconfigured driver 3
[   273.138] (==) Matched fbdev as autoconfigured driver 4
[   273.138] (==) Assigned the driver to the xf86ConfigLayout
[   273.138] (II) LoadModule: "nvidia"
[   273.139] (WW) Warning, couldn't open module nvidia
[   273.139] (II) UnloadModule: "nvidia"
[   273.139] (II) Unloading nvidia
[   273.139] (EE) Failed to load module "nvidia" (module does not exist, 0)
[   273.139] (II) LoadModule: "nouveau"
[   273.139] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   273.139] (II) Module nouveau: vendor="X.Org Foundation"
[   273.139] 	compiled for 1.11.3, module version = 0.0.16
[   273.139] 	Module class: X.Org Video Driver
[   273.139] 	ABI class: X.Org Video Driver, version 11.0
[   273.139] (II) UnloadModule: "nouveau"
[   273.140] (II) Unloading nouveau
[   273.145] (II) Failed to load module "nouveau" (already loaded, 0)
[   273.145] (II) LoadModule: "nv"
[   273.146] (WW) Warning, couldn't open module nv
[   273.146] (II) UnloadModule: "nv"
[   273.146] (II) Unloading nv
[   273.146] (EE) Failed to load module "nv" (module does not exist, 0)
[   273.146] (II) LoadModule: "vesa"
[   273.147] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   273.147] (II) Module vesa: vendor="X.Org Foundation"
[   273.147] 	compiled for 1.11.3, module version = 2.3.0
[   273.147] 	Module class: X.Org Video Driver
[   273.147] 	ABI class: X.Org Video Driver, version 11.0
[   273.147] (II) UnloadModule: "vesa"
[   273.147] (II) Unloading vesa
[   273.147] (II) Failed to load module "vesa" (already loaded, 0)
[   273.147] (II) LoadModule: "fbdev"
[   273.147] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   273.147] (II) Module fbdev: vendor="X.Org Foundation"
[   273.147] 	compiled for 1.11.3, module version = 0.4.2
[   273.147] 	ABI class: X.Org Video Driver, version 11.0
[   273.147] (II) UnloadModule: "fbdev"
[   273.147] (II) Unloading fbdev
[   273.147] (II) Failed to load module "fbdev" (already loaded, 0)
[   273.147] (II) NOUVEAU driver Date:   Wed Nov 30 18:56:54 2011 +0100
[   273.147] (II) NOUVEAU driver for NVIDIA chipset families :
[   273.147] 	RIVA TNT        (NV04)
[   273.148] 	RIVA TNT2       (NV05)
[   273.148] 	GeForce 256     (NV10)
[   273.148] 	GeForce 2       (NV11, NV15)
[   273.148] 	GeForce 4MX     (NV17, NV18)
[   273.148] 	GeForce 3       (NV20)
[   273.148] 	GeForce 4Ti     (NV25, NV28)
[   273.148] 	GeForce FX      (NV3x)
[   273.148] 	GeForce 6       (NV4x)
[   273.148] 	GeForce 7       (G7x)
[   273.148] 	GeForce 8       (G8x)
[   273.148] 	GeForce GTX 200 (NVA0)
[   273.148] 	GeForce GTX 400 (NVC0)
[   273.148] (II) VESA: driver for VESA chipsets: vesa
[   273.148] (II) FBDEV: driver for framebuffer: fbdev
[   273.148] (++) using VT number 7

[   273.148] drmOpenDevice: node name is /dev/dri/card0
[   273.148] drmOpenDevice: open result is 8, (OK)
[   273.149] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[   273.149] drmOpenDevice: node name is /dev/dri/card0
[   273.149] drmOpenDevice: open result is 8, (OK)
[   273.149] drmOpenByBusid: drmOpenMinor returns 8
[   273.149] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[   273.149] (II) [drm] nouveau interface version: 0.0.16
[   273.149] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   273.149] (WW) Falling back to old probe method for vesa
[   273.149] (WW) Falling back to old probe method for fbdev
[   273.149] (II) Loading sub module "fbdevhw"
[   273.149] (II) LoadModule: "fbdevhw"
[   273.150] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   273.150] (II) Module fbdevhw: vendor="X.Org Foundation"
[   273.150] 	compiled for 1.11.3, module version = 0.0.2
[   273.150] 	ABI class: X.Org Video Driver, version 11.0
[   273.150] (II) Loading sub module "dri"
[   273.150] (II) LoadModule: "dri"
[   273.150] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   273.150] (II) Module dri: vendor="X.Org Foundation"
[   273.151] 	compiled for 1.11.3, module version = 1.0.0
[   273.151] 	ABI class: X.Org Server Extension, version 6.0
[   273.151] (II) NOUVEAU(0): Loaded DRI module
[   273.151] drmOpenDevice: node name is /dev/dri/card0
[   273.151] drmOpenDevice: open result is 9, (OK)
[   273.151] drmOpenDevice: node name is /dev/dri/card0
[   273.151] drmOpenDevice: open result is 9, (OK)
[   273.151] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[   273.151] drmOpenDevice: node name is /dev/dri/card0
[   273.151] drmOpenDevice: open result is 9, (OK)
[   273.151] drmOpenByBusid: drmOpenMinor returns 9
[   273.151] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[   273.151] (II) [drm] DRM interface version 1.4
[   273.151] (II) [drm] DRM open master succeeded.
[   273.151] (--) NOUVEAU(0): Chipset: "NVIDIA NV34"
[   273.151] (II) NOUVEAU(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[   273.151] (==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
[   273.151] (==) NOUVEAU(0): RGB weight 888
[   273.151] (==) NOUVEAU(0): Default visual is TrueColor
[   273.151] (==) NOUVEAU(0): Using HW cursor
[   273.151] (==) NOUVEAU(0): GLX sync to VBlank disabled.
[   273.151] (==) NOUVEAU(0): Page flipping enabled
[   273.216] (II) NOUVEAU(0): Output VGA-1 has no monitor section
[   273.320] (II) NOUVEAU(0): Output DVI-I-1 has no monitor section
[   273.376] (II) NOUVEAU(0): Output TV-1 has no monitor section
[   273.436] (II) NOUVEAU(0): EDID for output VGA-1
[   273.540] (II) NOUVEAU(0): EDID for output DVI-I-1
[   273.540] (II) NOUVEAU(0): Manufacturer: SAM  Model: 612  Serial#: 1513182516
[   273.540] (II) NOUVEAU(0): Year: 2010  Week: 12
[   273.540] (II) NOUVEAU(0): EDID Version: 1.3
[   273.540] (II) NOUVEAU(0): Digital Display Input
[   273.540] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 60  vert.: 34
[   273.540] (II) NOUVEAU(0): Gamma: 2.20
[   273.540] (II) NOUVEAU(0): DPMS capabilities: Off
[   273.540] (II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   273.540] (II) NOUVEAU(0): First detailed timing is preferred mode
[   273.540] (II) NOUVEAU(0): redX: 0.647 redY: 0.334   greenX: 0.284 greenY: 0.607
[   273.540] (II) NOUVEAU(0): blueX: 0.151 blueY: 0.071   whiteX: 0.312 whiteY: 0.329
[   273.540] (II) NOUVEAU(0): Supported established timings:
[   273.540] (II) NOUVEAU(0): 640x480@60Hz
[   273.540] (II) NOUVEAU(0): 800x600@56Hz
[   273.540] (II) NOUVEAU(0): 800x600@60Hz
[   273.540] (II) NOUVEAU(0): 1024x768@60Hz
[   273.540] (II) NOUVEAU(0): Manufacturer's mask: 0
[   273.540] (II) NOUVEAU(0): Supported standard timings:
[   273.540] (II) NOUVEAU(0): #0: hsize: 1280  vsize 800  refresh: 60  vid: 129
[   273.541] (II) NOUVEAU(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[   273.541] (II) NOUVEAU(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[   273.541] (II) NOUVEAU(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
[   273.541] (II) NOUVEAU(0): #4: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[   273.541] (II) NOUVEAU(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[   273.541] (II) NOUVEAU(0): Supported detailed timing:
[   273.541] (II) NOUVEAU(0): clock: 148.5 MHz   Image Size:  604 x 342 mm
[   273.541] (II) NOUVEAU(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[   273.541] (II) NOUVEAU(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[   273.541] (II) NOUVEAU(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 175 MHz
[B][   273.541] (II) NOUVEAU(0): Monitor name: SyncMaster
[   273.541] (II) NOUVEAU(0): Serial No: HCLZ302459
[   273.541] (II) NOUVEAU(0): EDID (in hex):
[   273.541] (II) NOUVEAU(0): 	00ffffffffffff004c2d12063455315a
[   273.541] (II) NOUVEAU(0): 	0c140103803c22782aeed1a555489b26
[   273.541] (II) NOUVEAU(0): 	1250542308008100814081809500a940
[   273.541] (II) NOUVEAU(0): 	b30001010101023a801871382d40582c
[   273.541] (II) NOUVEAU(0): 	45005c562100001e000000fd00383c1e
[   273.541] (II) NOUVEAU(0): 	5111000a202020202020000000fc0053
[   273.541] (II) NOUVEAU(0): 	796e634d61737465720a2020000000ff
[   273.541] (II) NOUVEAU(0): 	0048434c5a3330323435390a20200043
[   273.541] (II) NOUVEAU(0): Printing probed modes for output DVI-I-1
[   273.541] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)[/B]
[   273.541] (II) NOUVEAU(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[   273.541] (II) NOUVEAU(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   273.541] (II) NOUVEAU(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 +hsync -vsync (49.7 kHz)
[   273.541] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   273.541] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   273.541] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   273.541] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   273.596] (II) NOUVEAU(0): EDID for output TV-1
[   273.596] (II) NOUVEAU(0): Output VGA-1 disconnected
[   273.596] (II) NOUVEAU(0): Output DVI-I-1 connected
[   273.596] (II) NOUVEAU(0): Output TV-1 disconnected
[   273.596] (II) NOUVEAU(0): Using fuzzy aspect match for initial modes
[   273.596] (II) NOUVEAU(0): Output DVI-I-1 using initial mode 1280x960
[   273.596] (II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   273.596] (--) NOUVEAU(0): Virtual size is 1280x960 (pitch 0)
[   273.596] (**) NOUVEAU(0):  Driver mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
[   273.596] (II) NOUVEAU(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   273.596] (**) NOUVEAU(0):  Driver mode "1280x800": 83.5 MHz (scaled from 0.0 MHz), 49.7 kHz, 59.8 Hz
[   273.596] (II) NOUVEAU(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 +hsync -vsync (49.7 kHz)
[   273.596] (**) NOUVEAU(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
[   273.596] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   273.596] (**) NOUVEAU(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
[   273.596] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   273.596] (**) NOUVEAU(0):  Driver mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.2 Hz
[   273.596] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   273.596] (**) NOUVEAU(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
[   273.596] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   273.596] (**) NOUVEAU(0):  Driver mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
[   273.596] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   273.596] (**) NOUVEAU(0):  Driver mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 59.9 Hz
[   273.596] (II) NOUVEAU(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[   273.596] (==) NOUVEAU(0): DPI set to (96, 96)
[   273.596] (II) Loading sub module "fb"
[   273.596] (II) LoadModule: "fb"
[   273.597] (II) Loading /usr/lib/xorg/modules/libfb.so
[   273.597] (II) Module fb: vendor="X.Org Foundation"
[   273.597] 	compiled for 1.11.3, module version = 1.0.0
[   273.597] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   273.597] (II) Loading sub module "exa"
[   273.597] (II) LoadModule: "exa"
[   273.597] (II) Loading /usr/lib/xorg/modules/libexa.so
[   273.597] (II) Module exa: vendor="X.Org Foundation"
[   273.597] 	compiled for 1.11.3, module version = 2.5.0
[   273.597] 	ABI class: X.Org Video Driver, version 11.0
[   273.597] (II) Loading sub module "shadowfb"
[   273.597] (II) LoadModule: "shadowfb"
[   273.598] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[   273.598] (II) Module shadowfb: vendor="X.Org Foundation"
[   273.598] 	compiled for 1.11.3, module version = 1.0.0
[   273.598] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   273.598] (II) UnloadModule: "vesa"
[   273.598] (II) Unloading vesa
[   273.598] (II) UnloadModule: "fbdev"
[   273.598] (II) Unloading fbdev
[   273.598] (II) UnloadModule: "fbdevhw"
[   273.598] (II) Unloading fbdevhw
[   273.598] (--) Depth 24 pixmap format is 32 bpp
[   273.599] (II) NOUVEAU(0): Opened GPU channel 1
[   273.600] (II) NOUVEAU(0): [DRI2] Setup complete
[   273.600] (II) NOUVEAU(0): [DRI2]   DRI driver: nouveau
[   273.600] (II) NOUVEAU(0): [DRI2]   VDPAU driver: nouveau
[   273.600] (II) NOUVEAU(0): GART: 128MiB available
[   273.610] (II) NOUVEAU(0): GART: Allocated 16MiB as a scratch buffer
[   273.610] (II) EXA(0): Driver allocated offscreen pixmaps
[   273.610] (II) EXA(0): Driver registered support for the following operations:
[   273.610] (II)         Solid
[   273.610] (II)         Copy
[   273.610] (II)         Composite (RENDER acceleration)
[   273.610] (II)         UploadToScreen
[   273.610] (II)         DownloadFromScreen
[   273.610] (==) NOUVEAU(0): Backing store disabled
[   273.610] (==) NOUVEAU(0): Silken mouse enabled
[   273.610] (II) NOUVEAU(0): [XvMC] Associated with NV30 texture adapter.
[   273.610] (II) NOUVEAU(0): [XvMC] Extension initialized.
[   273.611] (==) NOUVEAU(0): DPMS enabled
[   273.611] (II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   273.611] (--) RandR disabled
[   273.611] (II) Initializing built-in extension Generic Event Extension
[   273.611] (II) Initializing built-in extension SHAPE
[   273.611] (II) Initializing built-in extension MIT-SHM
[   273.611] (II) Initializing built-in extension XInputExtension
[   273.611] (II) Initializing built-in extension XTEST
[   273.611] (II) Initializing built-in extension BIG-REQUESTS
[   273.611] (II) Initializing built-in extension SYNC
[   273.611] (II) Initializing built-in extension XKEYBOARD
[   273.611] (II) Initializing built-in extension XC-MISC
[   273.611] (II) Initializing built-in extension SECURITY
[   273.611] (II) Initializing built-in extension XINERAMA
[   273.611] (II) Initializing built-in extension XFIXES
[   273.611] (II) Initializing built-in extension RENDER
[   273.611] (II) Initializing built-in extension RANDR
[   273.611] (II) Initializing built-in extension COMPOSITE
[   273.611] (II) Initializing built-in extension DAMAGE
[   273.652] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[   273.652] (II) AIGLX: enabled GLX_INTEL_swap_event
[   273.652] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[   273.652] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[   273.653] (II) AIGLX: Loaded and initialized nouveau
[   273.653] (II) GLX: Initialized DRI2 GL provider for screen 0
[   273.659] (II) NOUVEAU(0): NVEnterVT is called.
[   273.729] (II) NOUVEAU(0): Setting screen physical size to 338 x 253
[   273.729] resize called 1280 960
[   273.746] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   273.752] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   273.752] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   273.752] (II) LoadModule: "evdev"
[   273.752] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   273.753] (II) Module evdev: vendor="X.Org Foundation"
[   273.753] 	compiled for 1.11.3, module version = 2.7.0
[   273.753] 	Module class: X.Org XInput Driver
[   273.753] 	ABI class: X.Org XInput driver, version 16.0
[   273.753] (II) Using input driver 'evdev' for 'Power Button'
[   273.753] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   273.753] (**) Power Button: always reports core events
[   273.753] (**) evdev: Power Button: Device: "/dev/input/event1"
[   273.753] (--) evdev: Power Button: Vendor 0 Product 0x1
[   273.753] (--) evdev: Power Button: Found keys
[   273.753] (II) evdev: Power Button: Configuring as keyboard
[   273.753] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[   273.753] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   273.753] (**) Option "xkb_rules" "evdev"
[   273.753] (**) Option "xkb_model" "pc105"
[   273.753] (**) Option "xkb_layout" "us"
[   273.754] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   273.754] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   273.754] (II) Using input driver 'evdev' for 'Power Button'
[   273.754] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   273.755] (**) Power Button: always reports core events
[   273.755] (**) evdev: Power Button: Device: "/dev/input/event0"
[   273.755] (--) evdev: Power Button: Vendor 0 Product 0x1
[   273.755] (--) evdev: Power Button: Found keys
[   273.755] (II) evdev: Power Button: Configuring as keyboard
[   273.755] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[   273.755] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[   273.755] (**) Option "xkb_rules" "evdev"
[   273.755] (**) Option "xkb_model" "pc105"
[   273.755] (**) Option "xkb_layout" "us"
[   273.756] (II) config/udev: Adding input device WiseGroup.,Ltd TigerGame PS/PS2 Game Controller Adapter (/dev/input/event5)
[   273.756] (II) No input driver specified, ignoring this device.
[   273.756] (II) This device may have been added with another device file.
[   273.757] (II) config/udev: Adding input device WiseGroup.,Ltd TigerGame PS/PS2 Game Controller Adapter (/dev/input/js0)
[   273.757] (II) No input driver specified, ignoring this device.
[   273.757] (II) This device may have been added with another device file.
[   273.757] (II) config/udev: Adding input device WiseGroup.,Ltd TigerGame PS/PS2 Game Controller Adapter (/dev/input/event6)
[   273.757] (II) No input driver specified, ignoring this device.
[   273.757] (II) This device may have been added with another device file.
[   273.758] (II) config/udev: Adding input device WiseGroup.,Ltd TigerGame PS/PS2 Game Controller Adapter (/dev/input/js1)
[   273.758] (II) No input driver specified, ignoring this device.
[   273.758] (II) This device may have been added with another device file.
[   273.758] (II) config/udev: Adding input device Microsft Microsoft Wireless Desktop Receiver 3.1 (/dev/input/event2)
[   273.758] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: Applying InputClass "evdev keyboard catchall"
[   273.758] (II) Using input driver 'evdev' for 'Microsft Microsoft Wireless Desktop Receiver 3.1'
[   273.758] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   273.758] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: always reports core events
[   273.758] (**) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Device: "/dev/input/event2"
[   273.759] (--) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Vendor 0x45e Product 0xf9
[   273.759] (--) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Found keys
[   273.759] (II) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Configuring as keyboard
[   273.759] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:10.0/usb2/2-2/2-2:1.0/input/input2/event2"
[   273.759] (II) XINPUT: Adding extended input device "Microsft Microsoft Wireless Desktop Receiver 3.1" (type: KEYBOARD, id 8)
[   273.759] (**) Option "xkb_rules" "evdev"
[   273.759] (**) Option "xkb_model" "pc105"
[   273.759] (**) Option "xkb_layout" "us"
[   273.760] (II) config/udev: Adding input device Microsft Microsoft Wireless Desktop Receiver 3.1 (/dev/input/event3)
[   273.760] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: Applying InputClass "evdev pointer catchall"
[   273.760] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: Applying InputClass "evdev keyboard catchall"
[   273.760] (II) Using input driver 'evdev' for 'Microsft Microsoft Wireless Desktop Receiver 3.1'
[   273.760] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   273.760] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: always reports core events
[   273.761] (**) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Device: "/dev/input/event3"
[   273.761] (--) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Vendor 0x45e Product 0xf9
[   273.761] (--) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Found 9 mouse buttons
[   273.761] (--) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Found scroll wheel(s)
[   273.761] (--) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Found relative axes
[   273.761] (--) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Found x and y relative axes
[   273.761] (--) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Found absolute axes
[   273.761] (II) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Forcing absolute x/y axes to exist.
[   273.761] (--) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Found keys
[   273.761] (II) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Configuring as mouse
[   273.761] (II) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Configuring as keyboard
[   273.761] (II) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Adding scrollwheel support
[   273.761] (**) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: YAxisMapping: buttons 4 and 5
[   273.761] (**) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   273.761] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:10.0/usb2/2-2/2-2:1.1/input/input3/event3"
[   273.761] (II) XINPUT: Adding extended input device "Microsft Microsoft Wireless Desktop Receiver 3.1" (type: KEYBOARD, id 9)
[   273.761] (**) Option "xkb_rules" "evdev"
[   273.761] (**) Option "xkb_model" "pc105"
[   273.761] (**) Option "xkb_layout" "us"
[   273.762] (II) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: initialized for relative axes.
[   273.762] (WW) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: ignoring absolute axes.
[   273.762] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) keeping acceleration scheme 1
[   273.762] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) acceleration profile 0
[   273.762] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) acceleration factor: 2.000
[   273.762] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) acceleration threshold: 4
[   273.763] (II) config/udev: Adding input device Microsft Microsoft Wireless Desktop Receiver 3.1 (/dev/input/mouse0)
[   273.763] (II) No input driver specified, ignoring this device.
[   273.763] (II) This device may have been added with another device file.
[   273.763] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:400e (/dev/input/event4)
[   273.763] (**) Logitech Unifying Device. Wireless PID:400e: Applying InputClass "evdev pointer catchall"
[   273.763] (**) Logitech Unifying Device. Wireless PID:400e: Applying InputClass "evdev keyboard catchall"
[   273.763] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:400e'
[   273.763] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   273.764] (**) Logitech Unifying Device. Wireless PID:400e: always reports core events
[   273.764] (**) evdev: Logitech Unifying Device. Wireless PID:400e: Device: "/dev/input/event4"
[   273.764] (--) evdev: Logitech Unifying Device. Wireless PID:400e: Vendor 0x46d Product 0xc52b
[   273.764] (--) evdev: Logitech Unifying Device. Wireless PID:400e: Found 20 mouse buttons
[   273.764] (--) evdev: Logitech Unifying Device. Wireless PID:400e: Found scroll wheel(s)
[   273.764] (--) evdev: Logitech Unifying Device. Wireless PID:400e: Found relative axes
[   273.764] (--) evdev: Logitech Unifying Device. Wireless PID:400e: Found x and y relative axes
[   273.764] (--) evdev: Logitech Unifying Device. Wireless PID:400e: Found absolute axes
[   273.764] (II) evdev: Logitech Unifying Device. Wireless PID:400e: Forcing absolute x/y axes to exist.
[   273.764] (--) evdev: Logitech Unifying Device. Wireless PID:400e: Found keys
[   273.764] (II) evdev: Logitech Unifying Device. Wireless PID:400e: Configuring as mouse
[   273.764] (II) evdev: Logitech Unifying Device. Wireless PID:400e: Configuring as keyboard
[   273.764] (II) evdev: Logitech Unifying Device. Wireless PID:400e: Adding scrollwheel support
[   273.764] (**) evdev: Logitech Unifying Device. Wireless PID:400e: YAxisMapping: buttons 4 and 5
[   273.764] (**) evdev: Logitech Unifying Device. Wireless PID:400e: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   273.764] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:10.1/usb3/3-2/3-2:1.2/0003:046D:C52B.0006/input/input4/event4"
[   273.764] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:400e" (type: KEYBOARD, id 10)
[   273.764] (**) Option "xkb_rules" "evdev"
[   273.764] (**) Option "xkb_model" "pc105"
[   273.764] (**) Option "xkb_layout" "us"
[   273.765] (II) evdev: Logitech Unifying Device. Wireless PID:400e: initialized for relative axes.
[   273.765] (WW) evdev: Logitech Unifying Device. Wireless PID:400e: ignoring absolute axes.
[   273.765] (**) Logitech Unifying Device. Wireless PID:400e: (accel) keeping acceleration scheme 1
[   273.765] (**) Logitech Unifying Device. Wireless PID:400e: (accel) acceleration profile 0
[   273.765] (**) Logitech Unifying Device. Wireless PID:400e: (accel) acceleration factor: 2.000
[   273.765] (**) Logitech Unifying Device. Wireless PID:400e: (accel) acceleration threshold: 4
[   273.766] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:400e (/dev/input/mouse1)
[   273.766] (II) No input driver specified, ignoring this device.
[   273.766] (II) This device may have been added with another device file.
[   306.436] (II) NOUVEAU(0): EDID vendor "SAM", prod id 1554
[   306.436] (II) NOUVEAU(0): Using EDID range info for horizontal sync
[   306.436] (II) NOUVEAU(0): Using EDID range info for vertical refresh
[   306.436] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   306.436] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[   306.436] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   306.436] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   306.436] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   306.436] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   306.436] (II) NOUVEAU(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
[   306.436] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   306.436] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   306.436] (II) NOUVEAU(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[   306.436] (II) NOUVEAU(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[   306.436] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[   306.788] (II) NOUVEAU(0): EDID vendor "SAM", prod id 1554
[   306.788] (II) NOUVEAU(0): Using hsync ranges from config file
[   306.788] (II) NOUVEAU(0): Using vrefresh ranges from config file
[   306.788] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   306.788] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[   306.788] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   306.788] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   306.788] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   306.788] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   306.788] (II) NOUVEAU(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
[   306.788] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   306.788] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   306.788] (II) NOUVEAU(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[   306.788] (II) NOUVEAU(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[   306.788] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[   307.488] (II) NOUVEAU(0): EDID vendor "SAM", prod id 1554
[   307.488] (II) NOUVEAU(0): Using hsync ranges from config file
[   307.488] (II) NOUVEAU(0): Using vrefresh ranges from config file
[   307.488] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   307.488] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[   307.488] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   307.488] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   307.488] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   307.488] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   307.488] (II) NOUVEAU(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
[   307.488] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   307.488] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   307.488] (II) NOUVEAU(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[   307.488] (II) NOUVEAU(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[   307.488] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[   307.956] (II) NOUVEAU(0): EDID vendor "SAM", prod id 1554
[   307.956] (II) NOUVEAU(0): Using hsync ranges from config file
[   307.956] (II) NOUVEAU(0): Using vrefresh ranges from config file
[   307.956] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   307.956] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[   307.956] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   307.956] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   307.956] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   307.956] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   307.956] (II) NOUVEAU(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
[   307.956] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   307.956] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   307.956] (II) NOUVEAU(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[   307.956] (II) NOUVEAU(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[   307.956] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[   308.012] resize called 1440 900
[   308.473] (II) NOUVEAU(0): EDID vendor "SAM", prod id 1554
[   308.473] (II) NOUVEAU(0): Using hsync ranges from config file
[   308.473] (II) NOUVEAU(0): Using vrefresh ranges from config file
[   308.473] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   308.473] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[   308.473] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   308.473] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   308.473] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   308.473] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   308.473] (II) NOUVEAU(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
[   308.473] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   308.473] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   308.473] (II) NOUVEAU(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[   308.473] (II) NOUVEAU(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[   308.473] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[   308.970] (II) NOUVEAU(0): EDID vendor "SAM", prod id 1554
[   308.970] (II) NOUVEAU(0): Using hsync ranges from config file
[   308.970] (II) NOUVEAU(0): Using vrefresh ranges from config file
[   308.970] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   308.970] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[   308.970] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   308.970] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   308.970] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   308.970] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   308.970] (II) NOUVEAU(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
[   308.970] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   308.970] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   308.970] (II) NOUVEAU(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[   308.970] (II) NOUVEAU(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[   308.970] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[   309.276] (II) NOUVEAU(0): EDID vendor "SAM", prod id 1554
[   309.276] (II) NOUVEAU(0): Using hsync ranges from config file
[   309.276] (II) NOUVEAU(0): Using vrefresh ranges from config file
[   309.276] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   309.276] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[   309.276] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   309.276] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   309.276] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   309.276] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   309.276] (II) NOUVEAU(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
[   309.276] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   309.276] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   309.276] (II) NOUVEAU(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[   309.276] (II) NOUVEAU(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[   309.276] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[   474.248] (II) NOUVEAU(0): EDID vendor "SAM", prod id 1554
[   474.249] (II) NOUVEAU(0): Using hsync ranges from config file
[   474.249] (II) NOUVEAU(0): Using vrefresh ranges from config file
[   474.249] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   474.249] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[   474.249] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   474.249] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   474.249] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   474.249] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   474.249] (II) NOUVEAU(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
[   474.249] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   474.249] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   474.249] (II) NOUVEAU(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[   474.249] (II) NOUVEAU(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[   474.249] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[  1905.688] (II) NOUVEAU(0): EDID vendor "SAM", prod id 1554
[  1905.689] (II) NOUVEAU(0): Using hsync ranges from config file
[  1905.689] (II) NOUVEAU(0): Using vrefresh ranges from config file
[  1905.689] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[  1905.689] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[  1905.689] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  1905.689] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  1905.689] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  1905.689] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  1905.689] (II) NOUVEAU(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
[  1905.689] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[  1905.689] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  1905.689] (II) NOUVEAU(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[  1905.689] (II) NOUVEAU(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[  1905.689] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)

```

---

### Post by chowno on 2012-06-13
Update: I had some time to try a couple different prior distributions of Ubuntu and I've discovered that the driver regression must have occured prior to 11.10 (don't know what I was thinking - probably since I used to use the nvidia driver) since I saw the same behavior in that distro that I see in 12.04, but now I'm working in 10.10 (through the install DVD) and I have my 1920x1080 resolution...  Here is the Xorg.0.log from the installer DVD. There is a clear difference between the files when the EDID information for my monitor is read out to the log.
```

[    40.929] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    40.930] X Protocol Version 11, Revision 0
[    40.930] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    40.930] Current Operating System: Linux ubuntu 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686
[    40.930] Kernel command line: noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
[    40.930] Build Date: 16 September 2010  05:39:22PM
[    40.930] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[    40.950] Current version of pixman: 0.18.4
[    40.950] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    40.950] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    40.960] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jun 13 23:07:09 2012
[    40.989] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    41.006] (==) No Layout section.  Using the first Screen section.
[    41.006] (==) No screen section available. Using defaults.
[    41.006] (**) |-->Screen "Default Screen Section" (0)
[    41.006] (**) |   |-->Monitor "<default monitor>"
[    41.006] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    41.006] (==) Automatically adding devices
[    41.006] (==) Automatically enabling devices
[    41.035] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    41.035] 	Entry deleted from font path.
[    41.050] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    41.050] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    41.050] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    41.050] (II) Loader magic: 0x81f8e00
[    41.050] (II) Module ABI versions:
[    41.050] 	X.Org ANSI C Emulation: 0.4
[    41.050] 	X.Org Video Driver: 8.0
[    41.050] 	X.Org XInput driver : 11.0
[    41.050] 	X.Org Server Extension : 4.0
[    41.051] (--) PCI:*(0:1:0:0) 10de:0322:1458:3103 rev 161, Mem @ 0xe0000000/16777216, 0xd8000000/134217728, BIOS @ 0x????????/131072
[    41.051] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    41.051] (II) LoadModule: "extmod"
[    41.144] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    41.196] (II) Module extmod: vendor="X.Org Foundation"
[    41.196] 	compiled for 1.9.0, module version = 1.0.0
[    41.196] 	Module class: X.Org Server Extension
[    41.196] 	ABI class: X.Org Server Extension, version 4.0
[    41.196] (II) Loading extension MIT-SCREEN-SAVER
[    41.196] (II) Loading extension XFree86-VidModeExtension
[    41.196] (II) Loading extension XFree86-DGA
[    41.196] (II) Loading extension DPMS
[    41.196] (II) Loading extension XVideo
[    41.196] (II) Loading extension XVideo-MotionCompensation
[    41.196] (II) Loading extension X-Resource
[    41.196] (II) LoadModule: "dbe"
[    41.219] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    41.245] (II) Module dbe: vendor="X.Org Foundation"
[    41.245] 	compiled for 1.9.0, module version = 1.0.0
[    41.245] 	Module class: X.Org Server Extension
[    41.245] 	ABI class: X.Org Server Extension, version 4.0
[    41.245] (II) Loading extension DOUBLE-BUFFER
[    41.245] (II) LoadModule: "glx"
[    41.272] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    41.299] (II) Module glx: vendor="X.Org Foundation"
[    41.299] 	compiled for 1.9.0, module version = 1.0.0
[    41.299] 	ABI class: X.Org Server Extension, version 4.0
[    41.329] (==) AIGLX enabled
[    41.329] (II) Loading extension GLX
[    41.329] (II) LoadModule: "record"
[    41.376] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    41.394] (II) Module record: vendor="X.Org Foundation"
[    41.394] 	compiled for 1.9.0, module version = 1.13.0
[    41.394] 	Module class: X.Org Server Extension
[    41.394] 	ABI class: X.Org Server Extension, version 4.0
[    41.394] (II) Loading extension RECORD
[    41.394] (II) LoadModule: "dri"
[    41.395] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    41.468] (II) Module dri: vendor="X.Org Foundation"
[    41.468] 	compiled for 1.9.0, module version = 1.0.0
[    41.468] 	ABI class: X.Org Server Extension, version 4.0
[    41.468] (II) Loading extension XFree86-DRI
[    41.468] (II) LoadModule: "dri2"
[    41.469] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    41.504] (II) Module dri2: vendor="X.Org Foundation"
[    41.504] 	compiled for 1.9.0, module version = 1.2.0
[    41.504] 	ABI class: X.Org Server Extension, version 4.0
[    41.504] (II) Loading extension DRI2
[    41.504] (==) Matched nouveau as autoconfigured driver 0
[    41.504] (==) Matched nv as autoconfigured driver 1
[    41.504] (==) Matched vesa as autoconfigured driver 2
[    41.504] (==) Matched fbdev as autoconfigured driver 3
[    41.504] (==) Assigned the driver to the xf86ConfigLayout
[    41.504] (II) LoadModule: "nouveau"
[    41.505] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    41.583] (II) Module nouveau: vendor="X.Org Foundation"
[    41.583] 	compiled for 1.8.99.905, module version = 0.0.16
[    41.583] 	Module class: X.Org Video Driver
[    41.583] 	ABI class: X.Org Video Driver, version 8.0
[    41.583] (II) LoadModule: "nv"
[    41.584] (II) Loading /usr/lib/xorg/modules/drivers/nv_drv.so
[    41.623] (II) Module nv: vendor="X.Org Foundation"
[    41.623] 	compiled for 1.8.99.905, module version = 2.1.17
[    41.623] 	Module class: X.Org Video Driver
[    41.623] 	ABI class: X.Org Video Driver, version 8.0
[    41.623] (II) LoadModule: "vesa"
[    41.624] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    41.686] (II) Module vesa: vendor="X.Org Foundation"
[    41.686] 	compiled for 1.8.99.905, module version = 2.3.0
[    41.686] 	Module class: X.Org Video Driver
[    41.686] 	ABI class: X.Org Video Driver, version 8.0
[    41.686] (II) LoadModule: "fbdev"
[    41.757] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    41.769] (II) Module fbdev: vendor="X.Org Foundation"
[    41.769] 	compiled for 1.8.99.905, module version = 0.4.2
[    41.769] 	ABI class: X.Org Video Driver, version 8.0
[    41.769] (II) NOUVEAU driver Date:   Thu Aug 5 00:40:40 2010 +0200
[    41.769] (II) NOUVEAU driver for NVIDIA chipset families :
[    41.769] 	RIVA TNT    (NV04)
[    41.774] 	RIVA TNT2   (NV05)
[    41.774] 	GeForce 256 (NV10)
[    41.774] 	GeForce 2   (NV11, NV15)
[    41.774] 	GeForce 4MX (NV17, NV18)
[    41.774] 	GeForce 3   (NV20)
[    41.774] 	GeForce 4Ti (NV25, NV28)
[    41.774] 	GeForce FX  (NV3x)
[    41.774] 	GeForce 6   (NV4x)
[    41.774] 	GeForce 7   (G7x)
[    41.774] 	GeForce 8   (G8x)
[    41.774] (II) NOUVEAU driver Date:   Thu Aug 5 00:40:40 2010 +0200
[    41.774] (II) NOUVEAU driver for NVIDIA chipset families :
[    41.774] 	RIVA TNT    (NV04)
[    41.775] 	RIVA TNT2   (NV05)
[    41.775] 	GeForce 256 (NV10)
[    41.775] 	GeForce 2   (NV11, NV15)
[    41.775] 	GeForce 4MX (NV17, NV18)
[    41.775] 	GeForce 3   (NV20)
[    41.775] 	GeForce 4Ti (NV25, NV28)
[    41.775] 	GeForce FX  (NV3x)
[    41.775] 	GeForce 6   (NV4x)
[    41.775] 	GeForce 7   (G7x)
[    41.775] 	GeForce 8   (G8x)
[    41.775] (II) VESA: driver for VESA chipsets: vesa
[    41.775] (II) FBDEV: driver for framebuffer: fbdev
[    41.775] (++) using VT number 7

[    41.784] drmOpenDevice: node name is /dev/dri/card0
[    41.784] drmOpenDevice: open result is 7, (OK)
[    41.784] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    41.784] drmOpenDevice: node name is /dev/dri/card0
[    41.784] drmOpenDevice: open result is 7, (OK)
[    41.784] drmOpenByBusid: drmOpenMinor returns 7
[    41.784] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    41.784] (II) [drm] nouveau interface version: 0.0.16
[    41.784] (WW) Falling back to old probe method for vesa
[    41.784] (WW) Falling back to old probe method for fbdev
[    41.784] (II) Loading sub module "fbdevhw"
[    41.784] (II) LoadModule: "fbdevhw"
[    41.819] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    41.828] (II) Module fbdevhw: vendor="X.Org Foundation"
[    41.828] 	compiled for 1.9.0, module version = 0.0.2
[    41.828] 	ABI class: X.Org Video Driver, version 8.0
[    41.828] (II) Loading sub module "dri"
[    41.829] (II) LoadModule: "dri"
[    41.829] (II) Reloading /usr/lib/xorg/modules/extensions/libdri.so
[    41.829] (II) NOUVEAU(0): Loaded DRI module
[    41.829] drmOpenDevice: node name is /dev/dri/card0
[    41.829] drmOpenDevice: open result is 8, (OK)
[    41.829] drmOpenDevice: node name is /dev/dri/card0
[    41.830] drmOpenDevice: open result is 8, (OK)
[    41.830] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    41.830] drmOpenDevice: node name is /dev/dri/card0
[    41.830] drmOpenDevice: open result is 8, (OK)
[    41.830] drmOpenByBusid: drmOpenMinor returns 8
[    41.830] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    41.830] (II) [drm] DRM interface version 1.3
[    41.830] (II) [drm] DRM open master succeeded.
[    41.830] (--) NOUVEAU(0): Chipset: "NVIDIA NV34"
[    41.830] (II) NOUVEAU(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    41.830] (==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
[    41.830] (==) NOUVEAU(0): RGB weight 888
[    41.830] (==) NOUVEAU(0): Default visual is TrueColor
[    41.830] (==) NOUVEAU(0): Using HW cursor
[    41.968] (II) NOUVEAU(0): Output VGA-1 has no monitor section
[    43.090] (II) NOUVEAU(0): Output DVI-I-1 has no monitor section
[    43.144] (II) NOUVEAU(0): Output TV-1 has no monitor section
[    43.216] (II) NOUVEAU(0): EDID for output VGA-1
[    44.152] (II) NOUVEAU(0): EDID for output DVI-I-1
[    44.152] (II) NOUVEAU(0): Manufacturer: SAM  Model: 612  Serial#: 1513182516
[    44.152] (II) NOUVEAU(0): Year: 2010  Week: 12
[    44.152] (II) NOUVEAU(0): EDID Version: 1.3
[    44.152] (II) NOUVEAU(0): Digital Display Input
[    44.152] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 60  vert.: 34
[    44.152] (II) NOUVEAU(0): Gamma: 2.20
[    44.152] (II) NOUVEAU(0): DPMS capabilities: Off
[    44.152] (II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    44.152] (II) NOUVEAU(0): First detailed timing is preferred mode
[    44.152] (II) NOUVEAU(0): redX: 0.647 redY: 0.334   greenX: 0.284 greenY: 0.607
[    44.152] (II) NOUVEAU(0): blueX: 0.151 blueY: 0.071   whiteX: 0.312 whiteY: 0.329
[    44.152] (II) NOUVEAU(0): Supported established timings:
[    44.152] (II) NOUVEAU(0): 640x480@60Hz
[    44.152] (II) NOUVEAU(0): 800x600@56Hz
[    44.152] (II) NOUVEAU(0): 800x600@60Hz
[    44.152] (II) NOUVEAU(0): 1024x768@60Hz
[    44.152] (II) NOUVEAU(0): Manufacturer's mask: 0
[    44.152] (II) NOUVEAU(0): Supported standard timings:
[    44.152] (II) NOUVEAU(0): #0: hsize: 1280  vsize 800  refresh: 60  vid: 129
[    44.152] (II) NOUVEAU(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    44.152] (II) NOUVEAU(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    44.152] (II) NOUVEAU(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    44.152] (II) NOUVEAU(0): #4: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    44.152] (II) NOUVEAU(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    44.152] (II) NOUVEAU(0): Supported detailed timing:
[    44.152] (II) NOUVEAU(0): clock: 148.5 MHz   Image Size:  604 x 342 mm
[    44.152] (II) NOUVEAU(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    44.152] (II) NOUVEAU(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    44.152] (II) NOUVEAU(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 175 MHz
[B][    44.153] (II) NOUVEAU(0): Monitor name: SyncMaster
[    44.153] (II) NOUVEAU(0): Serial No: HCLZ302459
[    44.153] (II) NOUVEAU(0): EDID (in hex):
[    44.153] (II) NOUVEAU(0): 	00ffffffffffff004c2d12063455315a
[    44.153] (II) NOUVEAU(0): 	0c140103803c22782aeed1a555489b26
[    44.153] (II) NOUVEAU(0): 	1250542308008100814081809500a940
[    44.153] (II) NOUVEAU(0): 	b30001010101023a801871382d40582c
[    44.153] (II) NOUVEAU(0): 	45005c562100001e000000fd00383c1e
[    44.153] (II) NOUVEAU(0): 	5111000a202020202020000000fc0053
[    44.153] (II) NOUVEAU(0): 	796e634d61737465720a2020000000ff
[    44.153] (II) NOUVEAU(0): 	0048434c5a3330323435390a20200043
[    44.153] (II) NOUVEAU(0): Printing probed modes for output DVI-I-1
[    44.153] (II) NOUVEAU(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)[/B]
[    44.153] (II) NOUVEAU(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    44.153] (II) NOUVEAU(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    44.153] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    44.153] (II) NOUVEAU(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    44.153] (II) NOUVEAU(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    44.153] (II) NOUVEAU(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 +hsync -vsync (49.7 kHz)
[    44.153] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    44.153] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    44.153] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    44.153] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    44.212] (II) NOUVEAU(0): EDID for output TV-1
[    44.212] (II) NOUVEAU(0): Output VGA-1 disconnected
[    44.212] (II) NOUVEAU(0): Output DVI-I-1 connected
[    44.212] (II) NOUVEAU(0): Output TV-1 disconnected
[    44.212] (II) NOUVEAU(0): Using exact sizes for initial modes
[    44.212] (II) NOUVEAU(0): Output DVI-I-1 using initial mode 1920x1080
[    44.212] (II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    44.212] (--) NOUVEAU(0): Virtual size is 1920x1080 (pitch 1920)
[    44.212] (**) NOUVEAU(0):  Driver mode "1920x1080": 148.5 MHz (scaled from 0.0 MHz), 67.5 kHz, 60.0 Hz
[    44.212] (II) NOUVEAU(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    44.212] (**) NOUVEAU(0):  Driver mode "1600x1200": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
[    44.212] (II) NOUVEAU(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    44.212] (**) NOUVEAU(0):  Driver mode "1680x1050": 146.2 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
[    44.212] (II) NOUVEAU(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    44.212] (**) NOUVEAU(0):  Driver mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
[    44.212] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    44.212] (**) NOUVEAU(0):  Driver mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 59.9 Hz
[    44.212] (II) NOUVEAU(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    44.212] (**) NOUVEAU(0):  Driver mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
[    44.212] (II) NOUVEAU(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    44.212] (**) NOUVEAU(0):  Driver mode "1280x800": 83.5 MHz (scaled from 0.0 MHz), 49.7 kHz, 59.8 Hz
[    44.212] (II) NOUVEAU(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 +hsync -vsync (49.7 kHz)
[    44.212] (**) NOUVEAU(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
[    44.212] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    44.212] (**) NOUVEAU(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
[    44.212] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    44.212] (**) NOUVEAU(0):  Driver mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.2 Hz
[    44.212] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    44.212] (**) NOUVEAU(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
[    44.212] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    44.212] (==) NOUVEAU(0): DPI set to (96, 96)
[    44.212] (II) Loading sub module "fb"
[    44.213] (II) LoadModule: "fb"
[    44.213] (II) Loading /usr/lib/xorg/modules/libfb.so
[    44.234] (II) Module fb: vendor="X.Org Foundation"
[    44.234] 	compiled for 1.9.0, module version = 1.0.0
[    44.234] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    44.234] (II) Loading sub module "exa"
[    44.234] (II) LoadModule: "exa"
[    44.235] (II) Loading /usr/lib/xorg/modules/libexa.so
[    44.271] (II) Module exa: vendor="X.Org Foundation"
[    44.271] 	compiled for 1.9.0, module version = 2.5.0
[    44.271] 	ABI class: X.Org Video Driver, version 8.0
[    44.272] (II) Loading sub module "shadowfb"
[    44.272] (II) LoadModule: "shadowfb"
[    44.299] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[    44.313] (II) Module shadowfb: vendor="X.Org Foundation"
[    44.313] 	compiled for 1.9.0, module version = 1.0.0
[    44.313] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    44.313] (II) UnloadModule: "nv"
[    44.313] (II) Unloading /usr/lib/xorg/modules/drivers/nv_drv.so
[    44.313] (II) UnloadModule: "vesa"
[    44.313] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    44.313] (II) UnloadModule: "fbdev"
[    44.313] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    44.313] (II) UnloadModule: "fbdevhw"
[    44.313] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    44.313] (--) Depth 24 pixmap format is 32 bpp
[    44.315] (II) NOUVEAU(0): Opened GPU channel 1
[    44.315] (II) NOUVEAU(0): [DRI2] Setup complete
[    44.315] (II) NOUVEAU(0): [DRI2]   DRI driver: nouveau
[    44.315] (II) NOUVEAU(0): GART: 128MiB available
[    44.379] (II) NOUVEAU(0): GART: Allocated 16MiB as a scratch buffer
[    44.406] (II) EXA(0): Driver allocated offscreen pixmaps
[    44.406] (II) EXA(0): Driver registered support for the following operations:
[    44.406] (II)         Solid
[    44.406] (II)         Copy
[    44.406] (II)         Composite (RENDER acceleration)
[    44.406] (II)         UploadToScreen
[    44.406] (II)         DownloadFromScreen
[    44.406] (==) NOUVEAU(0): Backing store disabled
[    44.406] (==) NOUVEAU(0): Silken mouse enabled
[    44.406] (II) NOUVEAU(0): [XvMC] Associated with NV30 texture adapter.
[    44.406] (II) NOUVEAU(0): [XvMC] Extension initialized.
[    44.406] (==) NOUVEAU(0): DPMS enabled
[    44.406] (II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    44.407] (--) RandR disabled
[    44.407] (II) Initializing built-in extension Generic Event Extension
[    44.407] (II) Initializing built-in extension SHAPE
[    44.407] (II) Initializing built-in extension MIT-SHM
[    44.407] (II) Initializing built-in extension XInputExtension
[    44.407] (II) Initializing built-in extension XTEST
[    44.407] (II) Initializing built-in extension BIG-REQUESTS
[    44.407] (II) Initializing built-in extension SYNC
[    44.407] (II) Initializing built-in extension XKEYBOARD
[    44.407] (II) Initializing built-in extension XC-MISC
[    44.407] (II) Initializing built-in extension SECURITY
[    44.407] (II) Initializing built-in extension XINERAMA
[    44.407] (II) Initializing built-in extension XFIXES
[    44.407] (II) Initializing built-in extension RENDER
[    44.407] (II) Initializing built-in extension RANDR
[    44.407] (II) Initializing built-in extension COMPOSITE
[    44.407] (II) Initializing built-in extension DAMAGE
[    44.407] (II) Initializing built-in extension GESTURE
[    44.590] (II) AIGLX error: dlopen of /usr/lib/dri/nouveau_dri.so failed (/usr/lib/dri/nouveau_dri.so: cannot open shared object file: No such file or directory)
[    44.590] (II) AIGLX: reverting to software rendering
[    44.590] (II) AIGLX: Screen 0 is not DRI capable
[    44.794] (II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
[    44.794] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    44.881] (II) NOUVEAU(0): NVEnterVT is called.
[    44.882] (II) NOUVEAU(0): Setting screen physical size to 507 x 285
[    44.882] resize called 1920 1080
[    45.371] (II) XKB: generating xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    46.111] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    46.111] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    46.111] (II) LoadModule: "evdev"
[    46.143] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    46.224] (II) Module evdev: vendor="X.Org Foundation"
[    46.224] 	compiled for 1.9.0, module version = 2.3.2
[    46.224] 	Module class: X.Org XInput Driver
[    46.224] 	ABI class: X.Org XInput driver, version 11.0
[    46.224] (**) Power Button: always reports core events
[    46.224] (**) Power Button: Device: "/dev/input/event1"
[    46.224] (II) Power Button: Found keys
[    46.224] (II) Power Button: Configuring as keyboard
[    46.224] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    46.224] (**) Option "xkb_rules" "evdev"
[    46.224] (**) Option "xkb_model" "pc105"
[    46.224] (**) Option "xkb_layout" "us"
[    46.227] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    46.227] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    46.227] (**) Power Button: always reports core events
[    46.227] (**) Power Button: Device: "/dev/input/event0"
[    46.227] (II) Power Button: Found keys
[    46.227] (II) Power Button: Configuring as keyboard
[    46.227] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    46.227] (**) Option "xkb_rules" "evdev"
[    46.227] (**) Option "xkb_model" "pc105"
[    46.227] (**) Option "xkb_layout" "us"
[    46.286] (II) config/udev: Adding input device WiseGroup.,Ltd TigerGame PS/PS2 Game Controller Adapter (/dev/input/event2)
[    46.287] (II) No input driver/identifier specified (ignoring)
[    46.287] (II) config/udev: Adding input device WiseGroup.,Ltd TigerGame PS/PS2 Game Controller Adapter (/dev/input/js0)
[    46.287] (II) No input driver/identifier specified (ignoring)
[    46.288] (II) config/udev: Adding input device Microsft Microsoft Wireless Desktop Receiver 3.1 (/dev/input/event3)
[    46.288] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: Applying InputClass "evdev keyboard catchall"
[    46.288] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: always reports core events
[    46.288] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: Device: "/dev/input/event3"
[    46.288] (II) Microsft Microsoft Wireless Desktop Receiver 3.1: Found keys
[    46.288] (II) Microsft Microsoft Wireless Desktop Receiver 3.1: Configuring as keyboard
[    46.288] (II) XINPUT: Adding extended input device "Microsft Microsoft Wireless Desktop Receiver 3.1" (type: KEYBOARD)
[    46.288] (**) Option "xkb_rules" "evdev"
[    46.288] (**) Option "xkb_model" "pc105"
[    46.288] (**) Option "xkb_layout" "us"
[    46.289] (II) config/udev: Adding input device Microsft Microsoft Wireless Desktop Receiver 3.1 (/dev/input/event4)
[    46.289] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: Applying InputClass "evdev pointer catchall"
[    46.289] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: Applying InputClass "evdev keyboard catchall"
[    46.289] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: always reports core events
[    46.289] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: Device: "/dev/input/event4"
[    46.289] (II) Microsft Microsoft Wireless Desktop Receiver 3.1: Found 9 mouse buttons
[    46.289] (II) Microsft Microsoft Wireless Desktop Receiver 3.1: Found scroll wheel(s)
[    46.289] (II) Microsft Microsoft Wireless Desktop Receiver 3.1: Found relative axes
[    46.289] (II) Microsft Microsoft Wireless Desktop Receiver 3.1: Found x and y relative axes
[    46.289] (II) Microsft Microsoft Wireless Desktop Receiver 3.1: Found absolute axes
[    46.290] (II) evdev-grail: failed to open grail, no gesture support
[    46.290] (II) Microsft Microsoft Wireless Desktop Receiver 3.1: Found keys
[    46.290] (II) Microsft Microsoft Wireless Desktop Receiver 3.1: Configuring as mouse
[    46.290] (II) Microsft Microsoft Wireless Desktop Receiver 3.1: Configuring as keyboard
[    46.290] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: YAxisMapping: buttons 4 and 5
[    46.290] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    46.290] (II) XINPUT: Adding extended input device "Microsft Microsoft Wireless Desktop Receiver 3.1" (type: KEYBOARD)
[    46.290] (**) Option "xkb_rules" "evdev"
[    46.290] (**) Option "xkb_model" "pc105"
[    46.290] (**) Option "xkb_layout" "us"
[    46.290] (II) Microsft Microsoft Wireless Desktop Receiver 3.1: initialized for relative axes.
[    46.290] (WW) Microsft Microsoft Wireless Desktop Receiver 3.1: ignoring absolute axes.
[    46.291] (II) config/udev: Adding input device Microsft Microsoft Wireless Desktop Receiver 3.1 (/dev/input/mouse0)
[    46.291] (II) No input driver/identifier specified (ignoring)
[    53.272] (II) NOUVEAU(0): EDID vendor "SAM", prod id 1554
[    53.272] (II) NOUVEAU(0): Using EDID range info for horizontal sync
[    53.272] (II) NOUVEAU(0): Using EDID range info for vertical refresh
[    53.272] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    53.272] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    53.272] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    53.272] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    53.272] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    53.272] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    53.272] (II) NOUVEAU(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
[    53.272] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    53.272] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    53.272] (II) NOUVEAU(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    53.272] (II) NOUVEAU(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    53.272] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    53.985] (II) NOUVEAU(0): EDID vendor "SAM", prod id 1554
[    53.986] (II) NOUVEAU(0): Using hsync ranges from config file
[    53.986] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    53.986] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    53.986] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    53.986] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    53.986] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    53.986] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    53.986] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    53.986] (II) NOUVEAU(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
[    53.986] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    53.986] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    53.986] (II) NOUVEAU(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    53.986] (II) NOUVEAU(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    53.986] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    54.324] (II) NOUVEAU(0): EDID vendor "SAM", prod id 1554
[    54.324] (II) NOUVEAU(0): Using hsync ranges from config file
[    54.324] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    54.324] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    54.324] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    54.324] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    54.324] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    54.324] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    54.324] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    54.324] (II) NOUVEAU(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
[    54.324] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    54.324] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    54.324] (II) NOUVEAU(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    54.324] (II) NOUVEAU(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    54.324] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    54.648] (II) NOUVEAU(0): EDID vendor "SAM", prod id 1554
[    54.648] (II) NOUVEAU(0): Using hsync ranges from config file
[    54.648] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    54.648] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    54.648] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    54.648] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    54.648] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    54.648] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    54.648] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    54.648] (II) NOUVEAU(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
[    54.648] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    54.648] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    54.648] (II) NOUVEAU(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    54.648] (II) NOUVEAU(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    54.648] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    63.573] (II) NOUVEAU(0): EDID vendor "SAM", prod id 1554
[    63.573] (II) NOUVEAU(0): Using hsync ranges from config file
[    63.573] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    63.573] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    63.573] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    63.573] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    63.573] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    63.573] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    63.573] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    63.573] (II) NOUVEAU(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
[    63.573] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    63.573] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    63.573] (II) NOUVEAU(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    63.573] (II) NOUVEAU(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    63.573] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)

```

---

### Post by chowno on 2012-06-14
Update: So yesterday I did searching on Google and discovered Ubuntu's xrandr page.  In that page I found three ways to make the change in resolution persistent (really this is a bandaid fix)...  After several hours of painful play with the config files in /usr/share/X11/xorg.conf.d I was unsuccessful in trying to force the resolution.  Then I looked into setting the xrandr commands to coerce X into using the 1920x1080 resolution at the initialization of lightdm (a replacement for gdm?) but I cannot find the appropriate config files.  This left me with the last option which was to create a .xprofile in my home directory to include the xrandr --newmode, --addmode, and --output, all seperate xrandr calls, to manually add the resolution to the display and activate it at login time.  It works quite well but I wish I didn't have to do this since it used to work without any problems.  Hope this helps someone else. ;)

P.S. I ordered an ATI R600 class VGA for cheap off of TigerDirect of all places.  According to the status matrix on the radeon's Xorg wiki site this card should have about as much as it is going to get for open source compatibility (including opengl 3.0 and some other newer spec).  Also I will be able cast this terrible 5200FX piece of 'hardware' in to the abyss of retired parts which I would recommend to anyone with that card. B)

Thanks nouveau team for all of your hard work - I'm going to try your competitors now.

---

