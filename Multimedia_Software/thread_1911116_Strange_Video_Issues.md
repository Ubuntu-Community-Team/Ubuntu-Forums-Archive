---
title: "Strange Video Issues"
date: 2012-01-18
forum: Multimedia Software
---

### Post by gbw88 on 2012-01-18
Sorry if this is retreading on old ground, but I've been searching around and experimenting with fixes like crazy to try to fix this issue, and I've gotten nothing.

I came into an older Power Mac G5 the other day, and given that newer OS X versions are no good on the PPC architecture, I figured it'd make a good Ubuntu box. I figured out most of the graphical issues fairly fast, but now I'm really stumped with the latest (and hopefully final) one. The best way to describe it would be that the screen is dark, but only in some sections. This is also "dynamic"- if you will- and seems to shift around based upon whats onscreen. Upon startup, these "shadows" directly correspond with icons on the sidebar, and under Firefox the entire screen is just dark with random lighter lines.

I know its not the monitor; its on a KVM switch to my Windows rig and the monitor is fine. Its worth noting too that the login/bootup/etc  screens before the desktop don't present this problem. I've tried any number of manual Xorg settings and cleared the PRAM, no luck. If I switch the resolution down from 1440x900 to 1024x768 then the issue also vanishes. The card is a GeForce 6600 LE, so it should be able to do this resolution without an issue...

I'll add relevant info below, and attach some pictures I took to try to show the issue. Sorry if they aren't great quality (phone camera).

```
[    34.061] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    34.061] X Protocol Version 11, Revision 0
[    34.061] Build Operating System: Linux 2.6.35-30-powerpc64-smp ppc Ubuntu
[    34.061] Current Operating System: Linux ppcG5 3.0.0-14-powerpc64-smp #23-Ubuntu SMP Tue Nov 22 01:29:14 UTC 2011 ppc64
[    34.061] Kernel command line: root=UUID=4e654962-ec25-4394-bf00-749de6d69fe5 ro quiet splash 
[    34.061] Build Date: 19 October 2011  06:30:26AM
[    34.061] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[    34.061] Current version of pixman: 0.22.2
[    34.061]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    34.061] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    34.062] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jan 18 09:43:11 2012
[    34.073] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    34.074] (==) No Layout section.  Using the first Screen section.
[    34.074] (==) No screen section available. Using defaults.
[    34.074] (**) |-->Screen "Default Screen Section" (0)
[    34.074] (**) |   |-->Monitor "<default monitor>"
[    34.074] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    34.074] (==) Automatically adding devices
[    34.074] (==) Automatically enabling devices
[    34.074] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    34.074]     Entry deleted from font path.
[    34.074] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    34.074]     Entry deleted from font path.
[    34.074] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    34.074]     Entry deleted from font path.
[    34.074] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    34.075]     Entry deleted from font path.
[    34.075] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    34.075]     Entry deleted from font path.
[    34.075] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    34.075] (==) ModulePath set to "/usr/lib/powerpc-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    34.075] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    34.075] (II) Loader magic: 0x101ddbf0
[    34.075] (II) Module ABI versions:
[    34.075]     X.Org ANSI C Emulation: 0.4
[    34.075]     X.Org Video Driver: 10.0
[    34.075]     X.Org XInput driver : 12.3
[    34.075]     X.Org Server Extension : 5.0
[    34.076] (--) PCI:*(0:10:0:0) 10de:0142:10de:0010 rev 162, Mem @ 0x92000000/16777216, 0x98000000/134217728, 0x91000000/16777216, BIOS @ 0x????????/131072
[    34.076] (II) LoadModule: "extmod"
[    34.079] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    34.079] (II) Module extmod: vendor="X.Org Foundation"
[    34.079]     compiled for 1.10.4, module version = 1.0.0
[    34.079]     Module class: X.Org Server Extension
[    34.079]     ABI class: X.Org Server Extension, version 5.0
[    34.079] (II) Loading extension MIT-SCREEN-SAVER
[    34.079] (II) Loading extension XFree86-VidModeExtension
[    34.079] (II) Loading extension XFree86-DGA
[    34.079] (II) Loading extension DPMS
[    34.080] (II) Loading extension XVideo
[    34.080] (II) Loading extension XVideo-MotionCompensation
[    34.080] (II) Loading extension X-Resource
[    34.080] (II) LoadModule: "dbe"
[    34.080] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    34.080] (II) Module dbe: vendor="X.Org Foundation"
[    34.080]     compiled for 1.10.4, module version = 1.0.0
[    34.080]     Module class: X.Org Server Extension
[    34.080]     ABI class: X.Org Server Extension, version 5.0
[    34.080] (II) Loading extension DOUBLE-BUFFER
[    34.080] (II) LoadModule: "glx"
[    34.081] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    34.081] (II) Module glx: vendor="X.Org Foundation"
[    34.081]     compiled for 1.10.4, module version = 1.0.0
[    34.081]     ABI class: X.Org Server Extension, version 5.0
[    34.081] (==) AIGLX enabled
[    34.081] (II) Loading extension GLX
[    34.081] (II) LoadModule: "record"
[    34.082] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    34.082] (II) Module record: vendor="X.Org Foundation"
[    34.082]     compiled for 1.10.4, module version = 1.13.0
[    34.082]     Module class: X.Org Server Extension
[    34.082]     ABI class: X.Org Server Extension, version 5.0
[    34.082] (II) Loading extension RECORD
[    34.082] (II) LoadModule: "dri"
[    34.082] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    34.082] (II) Module dri: vendor="X.Org Foundation"
[    34.082]     compiled for 1.10.4, module version = 1.0.0
[    34.082]     ABI class: X.Org Server Extension, version 5.0
[    34.083] (II) Loading extension XFree86-DRI
[    34.083] (II) LoadModule: "dri2"
[    34.083] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    34.083] (II) Module dri2: vendor="X.Org Foundation"
[    34.083]     compiled for 1.10.4, module version = 1.2.0
[    34.083]     ABI class: X.Org Server Extension, version 5.0
[    34.083] (II) Loading extension DRI2
[    34.083] (==) Matched nvidia as autoconfigured driver 0
[    34.083] (==) Matched nouveau as autoconfigured driver 1
[    34.083] (==) Matched nv as autoconfigured driver 2
[    34.083] (==) Matched fbdev as autoconfigured driver 3
[    34.083] (==) Assigned the driver to the xf86ConfigLayout
[    34.083] (II) LoadModule: "nvidia"
[    34.086] (WW) Warning, couldn't open module nvidia
[    34.086] (II) UnloadModule: "nvidia"
[    34.086] (II) Unloading nvidia
[    34.086] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    34.086] (II) LoadModule: "nouveau"
[    34.086] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    34.086] (II) Module nouveau: vendor="X.Org Foundation"
[    34.086]     compiled for 1.10.1, module version = 0.0.16
[    34.086]     Module class: X.Org Video Driver
[    34.086]     ABI class: X.Org Video Driver, version 10.0
[    34.086] (II) LoadModule: "nv"
[    34.087] (WW) Warning, couldn't open module nv
[    34.087] (II) UnloadModule: "nv"
[    34.087] (II) Unloading nv
[    34.087] (EE) Failed to load module "nv" (module does not exist, 0)
[    34.087] (II) LoadModule: "fbdev"
[    34.088] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    34.088] (II) Module fbdev: vendor="X.Org Foundation"
[    34.088]     compiled for 1.10.0, module version = 0.4.2
[    34.088]     ABI class: X.Org Video Driver, version 10.0
[    34.088] (II) NOUVEAU driver Date:   Thu Mar 24 02:13:12 2011 +1000
[    34.088] (II) NOUVEAU driver for NVIDIA chipset families :
[    34.088]     RIVA TNT        (NV04)
[    34.088]     RIVA TNT2       (NV05)
[    34.088]     GeForce 256     (NV10)
[    34.088]     GeForce 2       (NV11, NV15)
[    34.088]     GeForce 4MX     (NV17, NV18)
[    34.088]     GeForce 3       (NV20)
[    34.088]     GeForce 4Ti     (NV25, NV28)
[    34.088]     GeForce FX      (NV3x)
[    34.088]     GeForce 6       (NV4x)
[    34.088]     GeForce 7       (G7x)
[    34.089]     GeForce 8       (G8x)
[    34.089]     GeForce GTX 200 (NVA0)
[    34.089]     GeForce GTX 400 (NVC0)
[    34.089] (II) FBDEV: driver for framebuffer: fbdev
[    34.089] (++) using VT number 7

[    34.089] drmOpenDevice: node name is /dev/dri/card0
[    34.089] drmOpenDevice: open result is 9, (OK)
[    34.089] drmOpenByBusid: Searching for BusID pci:0000:0a:00.0
[    34.089] drmOpenDevice: node name is /dev/dri/card0
[    34.089] drmOpenDevice: open result is 9, (OK)
[    34.089] drmOpenByBusid: drmOpenMinor returns 9
[    34.089] drmOpenByBusid: drmGetBusid reports pci:0000:0a:00.0
[    34.089] (II) [drm] nouveau interface version: 0.0.16
[    34.090] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    34.090] (WW) Falling back to old probe method for fbdev
[    34.090] (II) Loading sub module "fbdevhw"
[    34.090] (II) LoadModule: "fbdevhw"
[    34.090] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    34.090] (II) Module fbdevhw: vendor="X.Org Foundation"
[    34.090]     compiled for 1.10.4, module version = 0.0.2
[    34.090]     ABI class: X.Org Video Driver, version 10.0
[    34.091] (II) Loading sub module "dri"
[    34.091] (II) LoadModule: "dri"
[    34.091] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    34.091] (II) Module dri: vendor="X.Org Foundation"
[    34.091]     compiled for 1.10.4, module version = 1.0.0
[    34.091]     ABI class: X.Org Server Extension, version 5.0
[    34.091] (II) NOUVEAU(0): Loaded DRI module
[    34.091] drmOpenDevice: node name is /dev/dri/card0
[    34.091] drmOpenDevice: open result is 10, (OK)
[    34.091] drmOpenDevice: node name is /dev/dri/card0
[    34.091] drmOpenDevice: open result is 10, (OK)
[    34.091] drmOpenByBusid: Searching for BusID pci:0000:0a:00.0
[    34.091] drmOpenDevice: node name is /dev/dri/card0
[    34.091] drmOpenDevice: open result is 10, (OK)
[    34.091] drmOpenByBusid: drmOpenMinor returns 10
[    34.091] drmOpenByBusid: drmGetBusid reports pci:0000:0a:00.0
[    34.091] (II) [drm] DRM interface version 1.4
[    34.092] (II) [drm] DRM open master succeeded.
[    34.092] (--) NOUVEAU(0): Chipset: "NVIDIA NV43"
[    34.092] (II) NOUVEAU(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    34.092] (==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
[    34.092] (==) NOUVEAU(0): RGB weight 888
[    34.092] (==) NOUVEAU(0): Default visual is TrueColor
[    34.092] (==) NOUVEAU(0): Using HW cursor
[    34.092] (==) NOUVEAU(0): GLX sync to VBlank disabled.
[    34.092] (==) NOUVEAU(0): Page flipping enabled
[    34.198] (II) NOUVEAU(0): Output DVI-I-1 has no monitor section
[    34.264] (II) NOUVEAU(0): Output DVI-I-2 has no monitor section
[    34.376] (II) NOUVEAU(0): Output TV-1 has no monitor section
[    34.482] (II) NOUVEAU(0): EDID for output DVI-I-1
[    34.482] (II) NOUVEAU(0): Manufacturer: AOC  Model: 1976  Serial#: 106217
[    34.482] (II) NOUVEAU(0): Year: 2008  Week: 5
[    34.482] (II) NOUVEAU(0): EDID Version: 1.3
[    34.482] (II) NOUVEAU(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    34.482] (II) NOUVEAU(0): Sync:  Separate
[    34.482] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 41  vert.: 26
[    34.482] (II) NOUVEAU(0): Gamma: 2.20
[    34.482] (II) NOUVEAU(0): DPMS capabilities: Off; RGB/Color Display
[    34.482] (II) NOUVEAU(0): First detailed timing is preferred mode
[    34.482] (II) NOUVEAU(0): redX: 0.640 redY: 0.328   greenX: 0.300 greenY: 0.600
[    34.482] (II) NOUVEAU(0): blueX: 0.149 blueY: 0.060   whiteX: 0.312 whiteY: 0.328
[    34.482] (II) NOUVEAU(0): Supported established timings:
[    34.482] (II) NOUVEAU(0): 720x400@70Hz
[    34.482] (II) NOUVEAU(0): 640x480@60Hz
[    34.482] (II) NOUVEAU(0): 640x480@72Hz
[    34.482] (II) NOUVEAU(0): 640x480@75Hz
[    34.482] (II) NOUVEAU(0): 800x600@56Hz
[    34.482] (II) NOUVEAU(0): 800x600@60Hz
[    34.482] (II) NOUVEAU(0): 800x600@72Hz
[    34.482] (II) NOUVEAU(0): 800x600@75Hz
[    34.482] (II) NOUVEAU(0): 1024x768@60Hz
[    34.482] (II) NOUVEAU(0): 1024x768@70Hz
[    34.482] (II) NOUVEAU(0): 1024x768@75Hz
[    34.482] (II) NOUVEAU(0): Manufacturer's mask: 0
[    34.482] (II) NOUVEAU(0): Supported detailed timing:
[    34.482] (II) NOUVEAU(0): clock: 88.8 MHz   Image Size:  410 x 256 mm
[    34.482] (II) NOUVEAU(0): h_active: 1440  h_sync: 1488  h_sync_end 1520 h_blank_end 1600 h_border: 0
[    34.482] (II) NOUVEAU(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 926 v_border: 0
[    34.482] (II) NOUVEAU(0): Supported detailed timing:
[    34.482] (II) NOUVEAU(0): clock: 106.5 MHz   Image Size:  410 x 256 mm
[    34.482] (II) NOUVEAU(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
[    34.482] (II) NOUVEAU(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
[    34.482] (II) NOUVEAU(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 61 kHz, PixClock max 115 MHz
[    34.482] (II) NOUVEAU(0): Monitor name: L19W761
[    34.482] (II) NOUVEAU(0): EDID (in hex):
[    34.482] (II) NOUVEAU(0):     00ffffffffffff0005e37619e99e0100
[    34.482] (II) NOUVEAU(0):     0512010368291a782ace50a3544c9926
[    34.482] (II) NOUVEAU(0):     0f5054afce0001010101010101010101
[    34.482] (II) NOUVEAU(0):     010101010101ab22a0a050841a303020
[    34.482] (II) NOUVEAU(0):     36009a001100001a9a29a0d051842230
[    34.483] (II) NOUVEAU(0):     509836009a001100001c000000fd0038
[    34.483] (II) NOUVEAU(0):     4c1f3d0b000a202020202020000000fc
[    34.483] (II) NOUVEAU(0):     004c3139573736310a20202020200087
[    34.483] (II) NOUVEAU(0): EDID vendor "AOC", prod id 6518
[    34.483] (II) NOUVEAU(0): Using EDID range info for horizontal sync
[    34.483] (II) NOUVEAU(0): Using EDID range info for vertical refresh
[    34.483] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    34.483] (II) NOUVEAU(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    34.483] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    34.483] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    34.483] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    34.483] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    34.483] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    34.483] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    34.483] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    34.483] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    34.483] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    34.483] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    34.483] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    34.483] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    34.483] (II) NOUVEAU(0): Printing probed modes for output DVI-I-1
[    34.483] (II) NOUVEAU(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    34.483] (II) NOUVEAU(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    34.483] (II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[    34.483] (II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    34.483] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    34.483] (II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    34.483] (II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    34.483] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    34.483] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    34.483] (II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
[    34.483] (II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    34.483] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    34.483] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    34.548] (II) NOUVEAU(0): EDID for output DVI-I-2
[    34.660] (II) NOUVEAU(0): EDID for output TV-1
[    34.660] (II) NOUVEAU(0): Output DVI-I-1 connected
[    34.660] (II) NOUVEAU(0): Output DVI-I-2 disconnected
[    34.660] (II) NOUVEAU(0): Output TV-1 disconnected
[    34.660] (II) NOUVEAU(0): Using exact sizes for initial modes
[    34.660] (II) NOUVEAU(0): Output DVI-I-1 using initial mode 1440x900
[    34.660] (II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    34.660] (--) NOUVEAU(0): Virtual size is 1440x900 (pitch 0)
[    34.660] (**) NOUVEAU(0):  Driver mode "1440x900": 88.8 MHz (scaled from 0.0 MHz), 55.5 kHz, 59.9 Hz
[    34.660] (II) NOUVEAU(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    34.660] (**) NOUVEAU(0):  Driver mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 59.9 Hz
[    34.660] (II) NOUVEAU(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    34.660] (**) NOUVEAU(0):  Driver mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.1 kHz, 75.1 Hz
[    34.660] (II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[    34.660] (**) NOUVEAU(0):  Driver mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.1 Hz
[    34.660] (II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    34.660] (**) NOUVEAU(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
[    34.660] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    34.660] (**) NOUVEAU(0):  Driver mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.2 Hz
[    34.660] (II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    34.660] (**) NOUVEAU(0):  Driver mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
[    34.660] (II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    34.660] (**) NOUVEAU(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
[    34.660] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    34.660] (**) NOUVEAU(0):  Driver mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.2 Hz
[    34.660] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    34.660] (**) NOUVEAU(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.8 Hz
[    34.660] (II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
[    34.660] (**) NOUVEAU(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
[    34.660] (II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    34.660] (**) NOUVEAU(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
[    34.660] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    34.660] (**) NOUVEAU(0):  Driver mode "720x400": 28.3 MHz (scaled from 0.0 MHz), 31.5 kHz, 70.1 Hz
[    34.660] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    34.660] (**) NOUVEAU(0): Display dimensions: (410, 260) mm
[    34.660] (**) NOUVEAU(0): DPI set to (89, 87)
[    34.660] (II) Loading sub module "fb"
[    34.660] (II) LoadModule: "fb"
[    34.661] (II) Loading /usr/lib/xorg/modules/libfb.so
[    34.661] (II) Module fb: vendor="X.Org Foundation"
[    34.661]     compiled for 1.10.4, module version = 1.0.0
[    34.661]     ABI class: X.Org ANSI C Emulation, version 0.4
[    34.661] (II) Loading sub module "exa"
[    34.661] (II) LoadModule: "exa"
[    34.662] (II) Loading /usr/lib/xorg/modules/libexa.so
[    34.662] (II) Module exa: vendor="X.Org Foundation"
[    34.662]     compiled for 1.10.4, module version = 2.5.0
[    34.662]     ABI class: X.Org Video Driver, version 10.0
[    34.662] (II) Loading sub module "shadowfb"
[    34.662] (II) LoadModule: "shadowfb"
[    34.663] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[    34.663] (II) Module shadowfb: vendor="X.Org Foundation"
[    34.663]     compiled for 1.10.4, module version = 1.0.0
[    34.663]     ABI class: X.Org ANSI C Emulation, version 0.4
[    34.663] (II) UnloadModule: "fbdev"
[    34.663] (II) Unloading fbdev
[    34.663] (II) UnloadModule: "fbdevhw"
[    34.663] (II) Unloading fbdevhw
[    34.663] (--) Depth 24 pixmap format is 32 bpp
[    34.667] (II) NOUVEAU(0): Opened GPU channel 1
[    34.667] (II) NOUVEAU(0): [DRI2] Setup complete
[    34.667] (II) NOUVEAU(0): [DRI2]   DRI driver: nouveau
[    34.667] (II) NOUVEAU(0): GART: 512MiB available
[    34.679] (II) NOUVEAU(0): GART: Allocated 16MiB as a scratch buffer
[    34.680] (II) EXA(0): Driver allocated offscreen pixmaps
[    34.680] (II) EXA(0): Driver registered support for the following operations:
[    34.680] (II)         Solid
[    34.680] (II)         Copy
[    34.680] (II)         Composite (RENDER acceleration)
[    34.680] (II)         UploadToScreen
[    34.680] (II)         DownloadFromScreen
[    34.680] (==) NOUVEAU(0): Backing store disabled
[    34.680] (==) NOUVEAU(0): Silken mouse enabled
[    34.680] (II) NOUVEAU(0): [XvMC] Associated with NV40 texture adapter.
[    34.680] (II) NOUVEAU(0): [XvMC] Extension initialized.
[    34.680] (==) NOUVEAU(0): DPMS enabled
[    34.680] (II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    34.681] (--) RandR disabled
[    34.681] (II) Initializing built-in extension Generic Event Extension
[    34.681] (II) Initializing built-in extension SHAPE
[    34.681] (II) Initializing built-in extension MIT-SHM
[    34.681] (II) Initializing built-in extension XInputExtension
[    34.681] (II) Initializing built-in extension XTEST
[    34.681] (II) Initializing built-in extension BIG-REQUESTS
[    34.681] (II) Initializing built-in extension SYNC
[    34.681] (II) Initializing built-in extension XKEYBOARD
[    34.681] (II) Initializing built-in extension XC-MISC
[    34.681] (II) Initializing built-in extension SECURITY
[    34.681] (II) Initializing built-in extension XINERAMA
[    34.681] (II) Initializing built-in extension XFIXES
[    34.681] (II) Initializing built-in extension RENDER
[    34.681] (II) Initializing built-in extension RANDR
[    34.681] (II) Initializing built-in extension COMPOSITE
[    34.681] (II) Initializing built-in extension DAMAGE
[    34.681] (II) Initializing built-in extension GESTURE
[    34.711] (II) AIGLX: Trying DRI driver /usr/lib/powerpc-linux-gnu/dri/nouveau_dri.so
[    34.723] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    34.723] (II) AIGLX: enabled GLX_INTEL_swap_event
[    34.723] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    34.723] (II) AIGLX: enabled GLX_SGI_make_current_read
[    34.723] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    34.724] (II) AIGLX: Loaded and initialized nouveau
[    34.724] (II) GLX: Initialized DRI2 GL provider for screen 0
[    34.729] (II) NOUVEAU(0): NVEnterVT is called.
[    34.729] (II) NOUVEAU(0): Setting screen physical size to 381 x 238
[    34.729] resize called 1440 900
[    34.764] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    34.786] (II) config/udev: Adding input device Microsft Microsoft Wireless Desktop Receiver 3.1 (/dev/input/event2)
[    34.786] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: Applying InputClass "evdev keyboard catchall"
[    34.786] (II) LoadModule: "evdev"
[    34.786] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    34.788] (II) Module evdev: vendor="X.Org Foundation"
[    34.788]     compiled for 1.10.2, module version = 2.6.0
[    34.788]     Module class: X.Org XInput Driver
[    34.788]     ABI class: X.Org XInput driver, version 12.3
[    34.788] (II) Using input driver 'evdev' for 'Microsft Microsoft Wireless Desktop Receiver 3.1'
[    34.788] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    34.788] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: always reports core events
[    34.788] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: Device: "/dev/input/event2"
[    34.788] (--) Microsft Microsoft Wireless Desktop Receiver 3.1: Found keys
[    34.788] (II) Microsft Microsoft Wireless Desktop Receiver 3.1: Configuring as keyboard
[    34.788] (**) Option "config_info" "udev:/sys/devices/pci0001:00/0001:00:08.0/0001:01:0b.0/usb2/2-2/2-2.1/2-2.1:1.0/input/input2/event2"
[    34.788] (II) XINPUT: Adding extended input device "Microsft Microsoft Wireless Desktop Receiver 3.1" (type: KEYBOARD)
[    34.788] (**) Option "xkb_rules" "evdev"
[    34.788] (**) Option "xkb_model" "pc105"
[    34.788] (**) Option "xkb_layout" "us"
[    34.790] (II) config/udev: Adding input device Microsft Microsoft Wireless Desktop Receiver 3.1 (/dev/input/event3)
[    34.790] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: Applying InputClass "evdev pointer catchall"
[    34.790] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: Applying InputClass "evdev keyboard catchall"
[    34.790] (II) Using input driver 'evdev' for 'Microsft Microsoft Wireless Desktop Receiver 3.1'
[    34.790] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    34.790] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: always reports core events
[    34.790] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: Device: "/dev/input/event3"
[    34.790] (--) Microsft Microsoft Wireless Desktop Receiver 3.1: Found 9 mouse buttons
[    34.790] (--) Microsft Microsoft Wireless Desktop Receiver 3.1: Found scroll wheel(s)
[    34.790] (--) Microsft Microsoft Wireless Desktop Receiver 3.1: Found relative axes
[    34.790] (--) Microsft Microsoft Wireless Desktop Receiver 3.1: Found x and y relative axes
[    34.790] (--) Microsft Microsoft Wireless Desktop Receiver 3.1: Found absolute axes
[    34.791] (II) evdev-grail: failed to open grail, no gesture support
[    34.791] (--) Microsft Microsoft Wireless Desktop Receiver 3.1: Found keys
[    34.791] (II) Microsft Microsoft Wireless Desktop Receiver 3.1: Configuring as mouse
[    34.791] (II) Microsft Microsoft Wireless Desktop Receiver 3.1: Configuring as keyboard
[    34.791] (II) Microsft Microsoft Wireless Desktop Receiver 3.1: Adding scrollwheel support
[    34.791] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: YAxisMapping: buttons 4 and 5
[    34.791] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    34.791] (**) Option "config_info" "udev:/sys/devices/pci0001:00/0001:00:08.0/0001:01:0b.0/usb2/2-2/2-2.1/2-2.1:1.1/input/input3/event3"
[    34.791] (II) XINPUT: Adding extended input device "Microsft Microsoft Wireless Desktop Receiver 3.1" (type: KEYBOARD)
[    34.791] (**) Option "xkb_rules" "evdev"
[    34.791] (**) Option "xkb_model" "pc105"
[    34.791] (**) Option "xkb_layout" "us"
[    34.791] (II) Microsft Microsoft Wireless Desktop Receiver 3.1: initialized for relative axes.
[    34.791] (WW) Microsft Microsoft Wireless Desktop Receiver 3.1: ignoring absolute axes.
[    34.791] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) keeping acceleration scheme 1
[    34.791] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) acceleration profile 0
[    34.791] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) acceleration factor: 2.000
[    34.792] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) acceleration threshold: 4
[    34.792] (II) config/udev: Adding input device Microsft Microsoft Wireless Desktop Receiver 3.1 (/dev/input/mouse0)
[    34.792] (II) No input driver/identifier specified (ignoring)
[    34.794] (II) config/udev: Adding input device No brand SP02-A1 (/dev/input/event1)
[    34.794] (**) No brand SP02-A1: Applying InputClass "evdev keyboard catchall"
[    34.794] (II) Using input driver 'evdev' for 'No brand SP02-A1'
[    34.794] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    34.794] (**) No brand SP02-A1: always reports core events
[    34.794] (**) No brand SP02-A1: Device: "/dev/input/event1"
[    34.794] (--) No brand SP02-A1: Found keys
[    34.794] (II) No brand SP02-A1: Configuring as keyboard
[    34.794] (**) Option "config_info" "udev:/sys/devices/pci0001:00/0001:00:08.0/0001:01:0b.0/usb2/2-2/2-2.3/2-2.3:1.0/input/input1/event1"
[    34.794] (II) XINPUT: Adding extended input device "No brand SP02-A1" (type: KEYBOARD)
[    34.794] (**) Option "xkb_rules" "evdev"
[    34.794] (**) Option "xkb_model" "pc105"
[    34.794] (**) Option "xkb_layout" "us"
[    34.797] (II) config/udev: Adding input device Logitech NetPlay Keyboard (/dev/input/event0)
[    34.797] (**) Logitech NetPlay Keyboard: Applying InputClass "evdev keyboard catchall"
[    34.797] (II) Using input driver 'evdev' for 'Logitech NetPlay Keyboard'
[    34.797] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    34.797] (**) Logitech NetPlay Keyboard: always reports core events
[    34.797] (**) Logitech NetPlay Keyboard: Device: "/dev/input/event0"
[    34.797] (--) Logitech NetPlay Keyboard: Found keys
[    34.797] (II) Logitech NetPlay Keyboard: Configuring as keyboard
[    34.797] (**) Option "config_info" "udev:/sys/devices/pci0001:00/0001:00:08.0/0001:01:0b.1/usb3/3-1/3-1:1.0/input/input0/event0"
[    34.797] (II) XINPUT: Adding extended input device "Logitech NetPlay Keyboard" (type: KEYBOARD)
[    34.797] (**) Option "xkb_rules" "evdev"
[    34.797] (**) Option "xkb_model" "pc105"
[    34.797] (**) Option "xkb_layout" "us"
[    34.811] (II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event4)
[    34.811] (**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
[    34.811] (II) Using input driver 'evdev' for 'Macintosh mouse button emulation'
[    34.811] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    34.811] (**) Macintosh mouse button emulation: always reports core events
[    34.811] (**) Macintosh mouse button emulation: Device: "/dev/input/event4"
[    34.812] (--) Macintosh mouse button emulation: Found 3 mouse buttons
[    34.812] (--) Macintosh mouse button emulation: Found relative axes
[    34.812] (--) Macintosh mouse button emulation: Found x and y relative axes
[    34.812] (II) Macintosh mouse button emulation: Configuring as mouse
[    34.812] (**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
[    34.812] (**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    34.812] (**) Option "config_info" "udev:/sys/devices/virtual/input/input4/event4"
[    34.812] (II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
[    34.812] (II) Macintosh mouse button emulation: initialized for relative axes.
[    34.812] (**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
[    34.812] (**) Macintosh mouse button emulation: (accel) acceleration profile 0
[    34.812] (**) Macintosh mouse button emulation: (accel) acceleration factor: 2.000
[    34.812] (**) Macintosh mouse button emulation: (accel) acceleration threshold: 4
[    34.812] (II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse1)
[    34.812] (II) No input driver/identifier specified (ignoring)
[    36.202] (II) NOUVEAU(0): EDID vendor "AOC", prod id 6518
[    36.202] (II) NOUVEAU(0): Using hsync ranges from config file
[    36.202] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    36.202] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    36.202] (II) NOUVEAU(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    36.202] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    36.202] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    36.202] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    36.202] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    36.202] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    36.203] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    36.203] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    36.203] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    36.203] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    36.203] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    36.203] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    36.203] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    37.015] (II) NOUVEAU(0): EDID vendor "AOC", prod id 6518
[    37.015] (II) NOUVEAU(0): Using hsync ranges from config file
[    37.015] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    37.015] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    37.015] (II) NOUVEAU(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    37.015] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    37.015] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    37.015] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    37.015] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    37.015] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    37.015] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    37.015] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    37.015] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    37.015] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    37.015] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    37.016] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    37.016] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    39.254] (II) NOUVEAU(0): EDID vendor "AOC", prod id 6518
[    39.255] (II) NOUVEAU(0): Using hsync ranges from config file
[    39.255] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    39.255] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    39.255] (II) NOUVEAU(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    39.255] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    39.255] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    39.255] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    39.255] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    39.255] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    39.255] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    39.255] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    39.255] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    39.255] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    39.255] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    39.255] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    39.255] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    44.199] (II) NOUVEAU(0): EDID vendor "AOC", prod id 6518
[    44.199] (II) NOUVEAU(0): Using hsync ranges from config file
[    44.199] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    44.199] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    44.199] (II) NOUVEAU(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    44.199] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    44.199] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    44.199] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    44.199] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    44.199] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    44.199] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    44.199] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    44.199] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    44.199] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    44.199] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    44.199] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    44.199] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    44.518] resize called 1440 900
[    45.580] (II) NOUVEAU(0): EDID vendor "AOC", prod id 6518
[    45.580] (II) NOUVEAU(0): Using hsync ranges from config file
[    45.580] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    45.580] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    45.580] (II) NOUVEAU(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    45.580] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    45.580] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    45.580] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    45.580] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    45.580] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    45.580] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    45.580] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    45.580] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    45.580] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    45.580] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    45.580] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    45.580] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    46.014] (II) NOUVEAU(0): EDID vendor "AOC", prod id 6518
[    46.014] (II) NOUVEAU(0): Using hsync ranges from config file
[    46.014] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    46.014] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    46.014] (II) NOUVEAU(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    46.014] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    46.014] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    46.014] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    46.014] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    46.015] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    46.015] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    46.015] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    46.015] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    46.015] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    46.015] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    46.015] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    46.015] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    46.197] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[   284.860] (II) config/udev: removing device Logitech NetPlay Keyboard
[   284.860] (II) Logitech NetPlay Keyboard: Close
[   284.861] (II) UnloadModule: "evdev"
[   284.861] (II) Unloading evdev
[  1872.734] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm

``````
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 4096 x 4096
DVI-I-1 connected 1440x900+0+0 (normal left inverted right x axis y axis) 410mm x 256mm
   1440x900       59.9*+   59.9  
   1024x768       75.1     70.1     60.0  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     60.0  
   720x400        70.1  
DVI-I-2 disconnected (normal left inverted right x axis y axis)
TV-1 disconnected (normal left inverted right x axis y axis)
```

Thanks in advance for any help! If theres any other info needed, please just let me know.

---

### Post by Grenage on 2012-01-18
Raw curiosity; does the problem persist if the KVM isn't present?  Does it work when directly connected?

---

### Post by gbw88 on 2012-01-18
The same thing occurred to me (nevermind that I've used the exact same input in the thing for countless other Ubuntu/CentOS/Fedora/etc installs) earlier; your question prompted me to give it a try. With it directly wired and no KVM, its the exact same issue. I'm not sure if that's a good thing or a bad thing (don't have much room for a second monitor anyway), but I guess it can be ruled out.

---

### Post by Grenage on 2012-01-18
It was unlikely, but at least in rules out the switch blocking EDID data (it doesn't look like an EDID issue, but it never hurts).

Looking at the images, I would assume the problem to be one of the folliwng:

Defective monitor - you ruled that out.
Cable - you've probably rules that out.
Defective graphics card - (some will work ok with low-res/low-power graphics, then fail at the desktop).
Drivers - My gut says no, but it can't hurt to try alternative nvidia drivers.  Are you using the open drivers?

How does Linux run from a live CD?

---

### Post by gbw88 on 2012-01-18
I hope its not the hardware... Guess I could try to dig up an old copy of OS X 10.5 to be sure. Ugh...

As far as from live, I used the mini install / cli-expert for 11.10; I have loaded up the latest 12.04 for PPC though- same issue down to the letter. I'm wondering if it may be something in the drivers to be honest. I'm using the nouveau version that comes with 11.10 (since there's no PowerPC support from the official Nvidia drivers). In al honesty this is the first time I've seriously used them all that much, but from what I understand they can be rather difficult when they want to be.

---

### Post by Grenage on 2012-01-19
If you can find a macOS disc, it would certainly narrow it down - probably to hardware;  that would be a plus.

Like you, I tend not to use the open drivers, but I've not seen that kind of distortion caused by anything other than a bad monitor/cable/gfx.  Here's hoping it's not the machine!

---

