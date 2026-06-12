---
title: "Natty HDMI to HDMI problem after install ok before"
date: 2011-05-26
forum: Multimedia Software
---

### Post by raoulmaher on 2011-05-26
Unfortunately this is my second thread ands its typically Linux strange ( Ubuntu Natty )

I have a HDMI to HDMI cable connecting Laptop to TV - When running Natty installation CD and using trial ( don't install yet ! )  both laptop screen and TV screen echo each other and all is fine !

TV max res is  1920x1080 the Laptop is 1366x768 both about 60hz refresh


When I run XANDR command at end of trial boot when all has settled down I see this (on both screens ! ) :-

ubuntu@ubuntu:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
LVDS-1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768       60.1 +
   1024x768       59.9* 
   800x600        59.9  
   640x480        59.4  
   720x400        59.6  
   640x400        60.0  
   640x350        59.8  
VGA-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 160mm x 90mm
   1920x1080      60.0 +
   1280x1024      60.0  
   1152x864       75.0  
   1280x720       60.0  
   1024x768       60.0* 
   800x600        60.3  
   640x480        60.0  
   720x400        70.1  

But after full install no TV screen at all just laptop displaying and xrandr gives now

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1366 x 768, maximum 1366 x 768
default connected 1366x768+0+0 0mm x 0mm
   1366x768       50.0* 
   1360x768       51.0  
   1024x768       52.0  
   960x540        53.0  
   840x525        54.0  
   800x600        55.0  
   800x512        56.0  
   720x450        57.0  
   700x525        58.0  
   680x384        59.0     60.0  
   640x512        61.0  
   640x480        62.0     63.0  
   576x432        64.0  
   512x384        65.0  
   400x300        66.0  
   320x240        67.0  

Anyone have an idea ?

Is there a trial con-fig somewhere that can be copied or modded?

TRIAL LOG FILE below

[   145.398] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[   145.398] X Protocol Version 11, Revision 0
[   145.398] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[   145.398] Current Operating System: Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[   145.398] Kernel command line: file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity
[   145.398] Build Date: 19 April 2011  03:33:17PM
[   145.398] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[   145.398] Current version of pixman: 0.20.2
[   145.398]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[   145.398] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   145.398] (==) Log file: "/var/log/Xorg.0.log", Time: Thu May 26 14:55:12 2011
[   145.399] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   145.399] (==) No Layout section.  Using the first Screen section.
[   145.399] (==) No screen section available. Using defaults.
[   145.399] (**) |-->Screen "Default Screen Section" (0)
[   145.399] (**) |   |-->Monitor "<default monitor>"
[   145.400] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   145.400] (==) Automatically adding devices
[   145.400] (==) Automatically enabling devices
[   145.400] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   145.400]     Entry deleted from font path.
[   145.400] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   145.400]     Entry deleted from font path.
[   145.400] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   145.400]     Entry deleted from font path.
[   145.400] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   145.400]     Entry deleted from font path.
[   145.400] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   145.400]     Entry deleted from font path.
[   145.400] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[   145.400] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   145.400] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   145.400] (II) Loader magic: 0x81ffde0
[   145.400] (II) Module ABI versions:
[   145.400]     X.Org ANSI C Emulation: 0.4
[   145.400]     X.Org Video Driver: 10.0
[   145.400]     X.Org XInput driver : 12.3
[   145.400]     X.Org Server Extension : 5.0
[   145.401] (--) PCI:*(0:1:0:0) 10de:06e8:103c:360b rev 161, Mem @ 0xd2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00005000/128
[   145.402] (II) Open ACPI successful (/var/run/acpid.socket)
[   145.402] (II) LoadModule: "extmod"
[   145.403] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   145.403] (II) Module extmod: vendor="X.Org Foundation"
[   145.403]     compiled for 1.10.1, module version = 1.0.0
[   145.403]     Module class: X.Org Server Extension
[   145.403]     ABI class: X.Org Server Extension, version 5.0
[   145.403] (II) Loading extension MIT-SCREEN-SAVER
[   145.403] (II) Loading extension XFree86-VidModeExtension
[   145.403] (II) Loading extension XFree86-DGA
[   145.403] (II) Loading extension DPMS
[   145.403] (II) Loading extension XVideo
[   145.403] (II) Loading extension XVideo-MotionCompensation
[   145.403] (II) Loading extension X-Resource
[   145.403] (II) LoadModule: "dbe"
[   145.404] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   145.404] (II) Module dbe: vendor="X.Org Foundation"
[   145.404]     compiled for 1.10.1, module version = 1.0.0
[   145.404]     Module class: X.Org Server Extension
[   145.404]     ABI class: X.Org Server Extension, version 5.0
[   145.404] (II) Loading extension DOUBLE-BUFFER
[   145.404] (II) LoadModule: "glx"
[   145.405] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   145.405] (II) Module glx: vendor="X.Org Foundation"
[   145.405]     compiled for 1.10.1, module version = 1.0.0
[   145.405]     ABI class: X.Org Server Extension, version 5.0
[   145.405] (==) AIGLX enabled
[   145.405] (II) Loading extension GLX
[   145.405] (II) LoadModule: "record"
[   145.406] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   145.406] (II) Module record: vendor="X.Org Foundation"
[   145.406]     compiled for 1.10.1, module version = 1.13.0
[   145.406]     Module class: X.Org Server Extension
[   145.406]     ABI class: X.Org Server Extension, version 5.0
[   145.406] (II) Loading extension RECORD
[   145.406] (II) LoadModule: "dri"
[   145.407] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   145.407] (II) Module dri: vendor="X.Org Foundation"
[   145.407]     compiled for 1.10.1, module version = 1.0.0
[   145.408]     ABI class: X.Org Server Extension, version 5.0
[   145.408] (II) Loading extension XFree86-DRI
[   145.408] (II) LoadModule: "dri2"
[   145.408] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   145.409] (II) Module dri2: vendor="X.Org Foundation"
[   145.409]     compiled for 1.10.1, module version = 1.2.0
[   145.409]     ABI class: X.Org Server Extension, version 5.0
[   145.409] (II) Loading extension DRI2
[   145.409] (==) Matched nvidia as autoconfigured driver 0
[   145.409] (==) Matched nouveau as autoconfigured driver 1
[   145.409] (==) Matched nv as autoconfigured driver 2
[   145.409] (==) Matched vesa as autoconfigured driver 3
[   145.409] (==) Matched fbdev as autoconfigured driver 4
[   145.409] (==) Assigned the driver to the xf86ConfigLayout
[   145.409] (II) LoadModule: "nvidia"
[   145.411] (WW) Warning, couldn't open module nvidia
[   145.411] (II) UnloadModule: "nvidia"
[   145.411] (II) Unloading nvidia
[   145.411] (EE) Failed to load module "nvidia" (module does not exist, 0)
[   145.411] (II) LoadModule: "nouveau"
[   145.411] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   145.412] (II) Module nouveau: vendor="X.Org Foundation"
[   145.412]     compiled for 1.10.0, module version = 0.0.16
[   145.412]     Module class: X.Org Video Driver
[   145.412]     ABI class: X.Org Video Driver, version 10.0
[   145.412] (II) LoadModule: "nv"
[   145.413] (WW) Warning, couldn't open module nv
[   145.413] (II) UnloadModule: "nv"
[   145.413] (II) Unloading nv
[   145.413] (EE) Failed to load module "nv" (module does not exist, 0)
[   145.413] (II) LoadModule: "vesa"
[   145.414] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   145.414] (II) Module vesa: vendor="X.Org Foundation"
[   145.414]     compiled for 1.10.0, module version = 2.3.0
[   145.414]     Module class: X.Org Video Driver
[   145.414]     ABI class: X.Org Video Driver, version 10.0
[   145.414] (II) LoadModule: "fbdev"
[   145.414] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   145.414] (II) Module fbdev: vendor="X.Org Foundation"
[   145.414]     compiled for 1.10.0, module version = 0.4.2
[   145.414]     ABI class: X.Org Video Driver, version 10.0
[   145.414] (II) NOUVEAU driver Date:   Fri Jan 7 13:33:36 2011 +1000
[   145.414] (II) NOUVEAU driver for NVIDIA chipset families :
[   145.414]     RIVA TNT    (NV04)
[   145.414]     RIVA TNT2   (NV05)
[   145.414]     GeForce 256 (NV10)
[   145.414]     GeForce 2   (NV11, NV15)
[   145.415]     GeForce 4MX (NV17, NV18)
[   145.415]     GeForce 3   (NV20)
[   145.415]     GeForce 4Ti (NV25, NV28)
[   145.415]     GeForce FX  (NV3x)
[   145.415]     GeForce 6   (NV4x)
[   145.415]     GeForce 7   (G7x)
[   145.415]     GeForce 8   (G8x)
[   145.415] (II) VESA: driver for VESA chipsets: vesa
[   145.415] (II) FBDEV: driver for framebuffer: fbdev
[   145.415] (++) using VT number 7

[   145.415] drmOpenDevice: node name is /dev/dri/card0
[   145.415] drmOpenDevice: open result is 8, (OK)
[   145.415] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[   145.415] drmOpenDevice: node name is /dev/dri/card0
[   145.415] drmOpenDevice: open result is 8, (OK)
[   145.415] drmOpenByBusid: drmOpenMinor returns 8
[   145.415] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[   145.415] (II) [drm] nouveau interface version: 0.0.16
[   145.415] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   145.415] (WW) Falling back to old probe method for vesa
[   145.415] (WW) Falling back to old probe method for fbdev
[   145.415] (II) Loading sub module "fbdevhw"
[   145.415] (II) LoadModule: "fbdevhw"
[   145.416] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   145.416] (II) Module fbdevhw: vendor="X.Org Foundation"
[   145.416]     compiled for 1.10.1, module version = 0.0.2
[   145.416]     ABI class: X.Org Video Driver, version 10.0
[   145.416] (II) Loading sub module "dri"
[   145.416] (II) LoadModule: "dri"
[   145.417] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   145.417] (II) Module dri: vendor="X.Org Foundation"
[   145.417]     compiled for 1.10.1, module version = 1.0.0
[   145.417]     ABI class: X.Org Server Extension, version 5.0
[   145.417] (II) NOUVEAU(0): Loaded DRI module
[   145.417] drmOpenDevice: node name is /dev/dri/card0
[   145.417] drmOpenDevice: open result is 9, (OK)
[   145.417] drmOpenDevice: node name is /dev/dri/card0
[   145.417] drmOpenDevice: open result is 9, (OK)
[   145.417] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[   145.417] drmOpenDevice: node name is /dev/dri/card0
[   145.417] drmOpenDevice: open result is 9, (OK)
[   145.417] drmOpenByBusid: drmOpenMinor returns 9
[   145.417] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[   145.417] (II) [drm] DRM interface version 1.4
[   145.417] (II) [drm] DRM open master succeeded.
[   145.417] (--) NOUVEAU(0): Chipset: "NVIDIA NV98"
[   145.417] (II) NOUVEAU(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   145.417] (==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
[   145.417] (==) NOUVEAU(0): RGB weight 888
[   145.417] (==) NOUVEAU(0): Default visual is TrueColor
[   145.417] (==) NOUVEAU(0): Using HW cursor
[   145.417] (==) NOUVEAU(0): GLX sync to VBlank disabled.
[   145.525] (II) NOUVEAU(0): Output LVDS-1 has no monitor section
[   145.622] (II) NOUVEAU(0): Output VGA-1 has no monitor section
[   145.829] (II) NOUVEAU(0): Output HDMI-1 has no monitor section
[   145.935] (II) NOUVEAU(0): EDID for output LVDS-1
[   145.935] (II) NOUVEAU(0): Manufacturer: AUO  Model: 10ec  Serial#: 0
[   145.935] (II) NOUVEAU(0): Year: 2008  Week: 1
[   145.935] (II) NOUVEAU(0): EDID Version: 1.3
[   145.935] (II) NOUVEAU(0): Digital Display Input
[   145.935] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[   145.935] (II) NOUVEAU(0): Gamma: 2.20
[   145.935] (II) NOUVEAU(0): No DPMS capabilities specified
[   145.935] (II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   145.935] (II) NOUVEAU(0): First detailed timing is preferred mode
[   145.935] (II) NOUVEAU(0): redX: 0.640 redY: 0.342   greenX: 0.310 greenY: 0.580
[   145.935] (II) NOUVEAU(0): blueX: 0.150 blueY: 0.120   whiteX: 0.313 whiteY: 0.329
[   145.935] (II) NOUVEAU(0): Manufacturer's mask: 0
[   145.935] (II) NOUVEAU(0): Supported detailed timing:
[   145.935] (II) NOUVEAU(0): clock: 72.0 MHz   Image Size:  344 x 193 mm
[   145.935] (II) NOUVEAU(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1486 h_border: 0
[   145.935] (II) NOUVEAU(0): v_active: 768  v_sync: 771  v_sync_end 775 v_blanking: 806 v_border: 0
[   145.935] (II) NOUVEAU(0): Unknown vendor-specific block f
[   145.935] (II) NOUVEAU(0):  AUO
[   145.935] (II) NOUVEAU(0):  B156XW01 V0
[   145.935] (II) NOUVEAU(0): EDID (in hex):
[   145.935] (II) NOUVEAU(0):     00ffffffffffff0006afec1000000000
[   145.935] (II) NOUVEAU(0):     01120103802213780ae6b5a3574f9426
[   145.935] (II) NOUVEAU(0):     1e505400000001010101010101010101
[   145.935] (II) NOUVEAU(0):     010101010101201c5678500026303020
[   145.935] (II) NOUVEAU(0):     340058c1100000180000000f00000000
[   145.935] (II) NOUVEAU(0):     00000000000000000020000000fe0041
[   145.935] (II) NOUVEAU(0):     554f0a202020202020202020000000fe
[   145.935] (II) NOUVEAU(0):     004231353658573031205630200a002a
[   145.935] (II) NOUVEAU(0): EDID vendor "AUO", prod id 4332
[   145.935] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   145.935] (II) NOUVEAU(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1486  768 771 775 806 -hsync -vsync (48.5 kHz)
[   145.936] (II) NOUVEAU(0): Printing probed modes for output LVDS-1
[   145.936] (II) NOUVEAU(0): Modeline "1366x768"x60.1   72.00  1366 1414 1446 1486  768 771 775 806 -hsync -vsync (48.5 kHz)
[   145.936] (II) NOUVEAU(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[   145.936] (II) NOUVEAU(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[   145.936] (II) NOUVEAU(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[   145.936] (II) NOUVEAU(0): Modeline "720x400"x59.6   22.25  720 744 808 896  400 403 413 417 -hsync +vsync (24.8 kHz)
[   145.936] (II) NOUVEAU(0): Modeline "640x400"x60.0   20.00  640 664 720 800  400 403 409 417 -hsync +vsync (25.0 kHz)
[   145.936] (II) NOUVEAU(0): Modeline "640x350"x59.8   17.50  640 664 720 800  350 353 363 366 -hsync +vsync (21.9 kHz)
[   146.033] (II) NOUVEAU(0): EDID for output VGA-1
[   146.239] (II) Quirked EDID physical size to 0x0 cm
[   146.239] (II) NOUVEAU(0): EDID for output HDMI-1
[   146.239] (II) NOUVEAU(0): Manufacturer: GSM  Model: 1  Serial#: 16843009
[   146.239] (II) NOUVEAU(0): Year: 2010  Week: 1
[   146.239] (II) NOUVEAU(0): EDID Version: 1.3
[   146.239] (II) NOUVEAU(0): Digital Display Input
[   146.239] (II) NOUVEAU(0): Indeterminate output size
[   146.239] (II) NOUVEAU(0): Gamma: 2.20
[   146.240] (II) NOUVEAU(0): No DPMS capabilities specified
[   146.240] (II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   146.240] (II) NOUVEAU(0): First detailed timing is preferred mode
[   146.240] (II) NOUVEAU(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
[   146.240] (II) NOUVEAU(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
[   146.240] (II) NOUVEAU(0): Supported established timings:
[   146.240] (II) NOUVEAU(0): 720x400@70Hz
[   146.240] (II) NOUVEAU(0): 640x480@60Hz
[   146.240] (II) NOUVEAU(0): 800x600@60Hz
[   146.240] (II) NOUVEAU(0): 1024x768@60Hz
[   146.240] (II) NOUVEAU(0): Manufacturer's mask: 0
[   146.240] (II) NOUVEAU(0): Supported standard timings:
[   146.240] (II) NOUVEAU(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[   146.240] (II) NOUVEAU(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[   146.240] (II) NOUVEAU(0): Supported detailed timing:
[   146.240] (II) NOUVEAU(0): clock: 148.5 MHz   Image Size:  160 x 90 mm
[   146.240] (II) NOUVEAU(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[   146.240] (II) NOUVEAU(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[   146.240] (II) NOUVEAU(0): Supported detailed timing:
[   146.240] (II) NOUVEAU(0): clock: 74.2 MHz   Image Size:  160 x 90 mm
[   146.240] (II) NOUVEAU(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[   146.240] (II) NOUVEAU(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[   146.240] (II) NOUVEAU(0): Ranges: V min: 58 V max: 62 Hz, H min: 30 H max: 83 kHz, PixClock max 165 MHz
[   146.240] (II) NOUVEAU(0): Monitor name: LG TV
[   146.240] (II) NOUVEAU(0): Supported detailed timing:
[   146.240] (II) NOUVEAU(0): clock: 74.2 MHz   Image Size:  160 x 90 mm
[   146.240] (II) NOUVEAU(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[   146.240] (II) NOUVEAU(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[   146.240] (II) NOUVEAU(0): Supported detailed timing:
[   146.240] (II) NOUVEAU(0): clock: 74.2 MHz   Image Size:  160 x 90 mm
[   146.240] (II) NOUVEAU(0): h_active: 1280  h_sync: 1344  h_sync_end 1472 h_blank_end 1664 h_border: 0
[   146.240] (II) NOUVEAU(0): v_active: 720  v_sync: 723  v_sync_end 728 v_blanking: 732 v_border: 0
[   146.240] (II) NOUVEAU(0): Supported detailed timing:
[   146.240] (II) NOUVEAU(0): clock: 148.5 MHz   Image Size:  160 x 90 mm
[   146.240] (II) NOUVEAU(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[   146.240] (II) NOUVEAU(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[   146.240] (II) NOUVEAU(0): Supported detailed timing:
[   146.240] (II) NOUVEAU(0): clock: 85.5 MHz   Image Size:  160 x 90 mm
[   146.240] (II) NOUVEAU(0): h_active: 1360  h_sync: 1424  h_sync_end 1536 h_blank_end 1792 h_border: 0
[   146.240] (II) NOUVEAU(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 795 v_border: 0
[   146.240] (II) NOUVEAU(0): Number of EDID sections to follow: 1
[   146.240] (II) NOUVEAU(0): EDID (in hex):
[   146.240] (II) NOUVEAU(0):     00ffffffffffff001e6d010001010101
[   146.240] (II) NOUVEAU(0):     01140103801009780aee91a3544c9926
[   146.240] (II) NOUVEAU(0):     0f5054a10800714f8180010101010101
[   146.240] (II) NOUVEAU(0):     010101010101023a801871382d40582c
[   146.240] (II) NOUVEAU(0):     4500a05a0000001e011d007251d01e20
[   146.240] (II) NOUVEAU(0):     6e285500a05a0000001e000000fd003a
[   146.240] (II) NOUVEAU(0):     3e1e5310000a202020202020000000fc
[   146.240] (II) NOUVEAU(0):     004c472054560a2020202020202001d7
[   146.240] (II) NOUVEAU(0): Printing probed modes for output HDMI-1
[   146.240] (II) NOUVEAU(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[   146.240] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   146.240] (II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   146.240] (II) NOUVEAU(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[   146.240] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   146.240] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   146.240] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   146.241] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   146.241] (II) NOUVEAU(0): Output LVDS-1 connected
[   146.241] (II) NOUVEAU(0): Output VGA-1 disconnected
[   146.241] (II) NOUVEAU(0): Output HDMI-1 connected
[   146.241] (II) NOUVEAU(0): Using fuzzy aspect match for initial modes
[   146.241] (II) NOUVEAU(0): Output LVDS-1 using initial mode 1024x768
[   146.241] (II) NOUVEAU(0): Output HDMI-1 using initial mode 1024x768
[   146.241] (II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   146.241] (--) NOUVEAU(0): Virtual size is 1024x768 (pitch 0)
[   146.241] (**) NOUVEAU(0):  Driver mode "1024x768": 63.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 59.9 Hz
[   146.241] (II) NOUVEAU(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[   146.241] (**) NOUVEAU(0):  Driver mode "800x600": 38.2 MHz (scaled from 0.0 MHz), 37.4 kHz, 59.9 Hz
[   146.241] (II) NOUVEAU(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[   146.241] (**) NOUVEAU(0):  Driver mode "640x480": 23.8 MHz (scaled from 0.0 MHz), 29.7 kHz, 59.4 Hz
[   146.241] (II) NOUVEAU(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[   146.241] (**) NOUVEAU(0):  Driver mode "720x400": 22.2 MHz (scaled from 0.0 MHz), 24.8 kHz, 59.6 Hz
[   146.241] (II) NOUVEAU(0): Modeline "720x400"x59.6   22.25  720 744 808 896  400 403 413 417 -hsync +vsync (24.8 kHz)
[   146.241] (**) NOUVEAU(0):  Driver mode "640x400": 20.0 MHz (scaled from 0.0 MHz), 25.0 kHz, 60.0 Hz
[   146.241] (II) NOUVEAU(0): Modeline "640x400"x60.0   20.00  640 664 720 800  400 403 409 417 -hsync +vsync (25.0 kHz)
[   146.241] (**) NOUVEAU(0):  Driver mode "640x350": 17.5 MHz (scaled from 0.0 MHz), 21.9 kHz, 59.8 Hz
[   146.241] (II) NOUVEAU(0): Modeline "640x350"x59.8   17.50  640 664 720 800  350 353 363 366 -hsync +vsync (21.9 kHz)
[   146.241] (**) NOUVEAU(0):  Driver mode "1366x768": 72.0 MHz (scaled from 0.0 MHz), 48.5 kHz, 60.1 Hz
[   146.241] (II) NOUVEAU(0): Modeline "1366x768"x60.1   72.00  1366 1414 1446 1486  768 771 775 806 -hsync -vsync (48.5 kHz)
[   146.241] (**) NOUVEAU(0): Display dimensions: (340, 190) mm
[   146.241] (**) NOUVEAU(0): DPI set to (76, 102)
[   146.241] (II) Loading sub module "fb"
[   146.241] (II) LoadModule: "fb"
[   146.242] (II) Loading /usr/lib/xorg/modules/libfb.so
[   146.242] (II) Module fb: vendor="X.Org Foundation"
[   146.242]     compiled for 1.10.1, module version = 1.0.0
[   146.242]     ABI class: X.Org ANSI C Emulation, version 0.4
[   146.242] (II) Loading sub module "exa"
[   146.242] (II) LoadModule: "exa"
[   146.243] (II) Loading /usr/lib/xorg/modules/libexa.so
[   146.243] (II) Module exa: vendor="X.Org Foundation"
[   146.243]     compiled for 1.10.1, module version = 2.5.0
[   146.243]     ABI class: X.Org Video Driver, version 10.0
[   146.243] (II) Loading sub module "shadowfb"
[   146.243] (II) LoadModule: "shadowfb"
[   146.244] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[   146.244] (II) Module shadowfb: vendor="X.Org Foundation"
[   146.244]     compiled for 1.10.1, module version = 1.0.0
[   146.244]     ABI class: X.Org ANSI C Emulation, version 0.4
[   146.244] (II) UnloadModule: "vesa"
[   146.244] (II) Unloading vesa
[   146.244] (II) UnloadModule: "fbdev"
[   146.244] (II) Unloading fbdev
[   146.244] (II) UnloadModule: "fbdevhw"
[   146.244] (II) Unloading fbdevhw
[   146.244] (--) Depth 24 pixmap format is 32 bpp
[   146.251] (II) NOUVEAU(0): Opened GPU channel 2
[   146.252] (II) NOUVEAU(0): [DRI2] Setup complete
[   146.252] (II) NOUVEAU(0): [DRI2]   DRI driver: nouveau
[   146.252] (II) NOUVEAU(0): GART: 512MiB available
[   146.254] (II) NOUVEAU(0): GART: Allocated 16MiB as a scratch buffer
[   146.254] (II) EXA(0): Driver allocated offscreen pixmaps
[   146.254] (II) EXA(0): Driver registered support for the following operations:
[   146.254] (II)         Solid
[   146.255] (II)         Copy
[   146.255] (II)         Composite (RENDER acceleration)
[   146.255] (II)         UploadToScreen
[   146.255] (II)         DownloadFromScreen
[   146.255] (==) NOUVEAU(0): Backing store disabled
[   146.255] (==) NOUVEAU(0): Silken mouse enabled
[   146.255] (II) NOUVEAU(0): [XvMC] Associated with Nouveau GeForce 8/9 Textured Video.
[   146.255] (II) NOUVEAU(0): [XvMC] Extension initialized.
[   146.255] (==) NOUVEAU(0): DPMS enabled
[   146.255] (II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   146.255] (--) RandR disabled
[   146.255] (II) Initializing built-in extension Generic Event Extension
[   146.255] (II) Initializing built-in extension SHAPE
[   146.255] (II) Initializing built-in extension MIT-SHM
[   146.255] (II) Initializing built-in extension XInputExtension
[   146.255] (II) Initializing built-in extension XTEST
[   146.255] (II) Initializing built-in extension BIG-REQUESTS
[   146.255] (II) Initializing built-in extension SYNC
[   146.255] (II) Initializing built-in extension XKEYBOARD
[   146.255] (II) Initializing built-in extension XC-MISC
[   146.255] (II) Initializing built-in extension SECURITY
[   146.255] (II) Initializing built-in extension XINERAMA
[   146.255] (II) Initializing built-in extension XFIXES
[   146.255] (II) Initializing built-in extension RENDER
[   146.255] (II) Initializing built-in extension RANDR
[   146.255] (II) Initializing built-in extension COMPOSITE
[   146.255] (II) Initializing built-in extension DAMAGE
[   146.255] (II) Initializing built-in extension GESTURE
[   146.269] (II) AIGLX: Trying DRI driver /usr/lib/dri/nouveau_dri.so
[   146.269] (II) AIGLX: dlopen of /usr/lib/dri/nouveau_dri.so failed (/usr/lib/dri/nouveau_dri.so: cannot open shared object file: No such file or directory)
[   146.269] (II) AIGLX: Trying DRI driver /usr/lib/dri-alternates/nouveau_dri.so
[   146.269] (II) AIGLX: dlopen of /usr/lib/dri-alternates/nouveau_dri.so failed (/usr/lib/dri-alternates/nouveau_dri.so: cannot open shared object file: No such file or directory)
[   146.269] (II) AIGLX: Trying DRI driver /usr/lib32/dri/nouveau_dri.so
[   146.269] (II) AIGLX: dlopen of /usr/lib32/dri/nouveau_dri.so failed (/usr/lib32/dri/nouveau_dri.so: cannot open shared object file: No such file or directory)
[   146.269] (II) AIGLX: Trying DRI driver /usr/lib32/dri-alternates/nouveau_dri.so
[   146.269] (II) AIGLX: dlopen of /usr/lib32/dri-alternates/nouveau_dri.so failed (/usr/lib32/dri-alternates/nouveau_dri.so: cannot open shared object file: No such file or directory)
[   146.269] (II) AIGLX: reverting to software rendering
[   146.269] (II) AIGLX: Screen 0 is not DRI capable
[   146.269] (II) AIGLX: Trying DRI driver /usr/lib/dri/swrast_dri.so
[   146.273] (II) AIGLX: Loaded and initialized swrast
[   146.273] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[   146.277] (II) NOUVEAU(0): NVEnterVT is called.
[   146.277] (II) NOUVEAU(0): Setting screen physical size to 270 x 203
[   146.277] resize called 1024 768
[   146.288] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   146.301] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[   146.301] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   146.301] (II) LoadModule: "evdev"
[   146.302] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   146.302] (II) Module evdev: vendor="X.Org Foundation"
[   146.302]     compiled for 1.10.0.902, module version = 2.6.0
[   146.302]     Module class: X.Org XInput Driver
[   146.302]     ABI class: X.Org XInput driver, version 12.3
[   146.302] (II) Using input driver 'evdev' for 'Power Button'
[   146.302] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   146.302] (**) Power Button: always reports core events
[   146.302] (**) Power Button: Device: "/dev/input/event2"
[   146.303] (--) Power Button: Found keys
[   146.303] (II) Power Button: Configuring as keyboard
[   146.303] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[   146.303] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   146.303] (**) Option "xkb_rules" "evdev"
[   146.303] (**) Option "xkb_model" "pc105"
[   146.303] (**) Option "xkb_layout" "us"
[   146.304] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[   146.304] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   146.304] (II) Using input driver 'evdev' for 'Video Bus'
[   146.304] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   146.304] (**) Video Bus: always reports core events
[   146.304] (**) Video Bus: Device: "/dev/input/event4"
[   146.304] (--) Video Bus: Found keys
[   146.304] (II) Video Bus: Configuring as keyboard
[   146.304] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:06/LNXVIDEO:01/input/input4/event4"
[   146.305] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[   146.305] (**) Option "xkb_rules" "evdev"
[   146.305] (**) Option "xkb_model" "pc105"
[   146.305] (**) Option "xkb_layout" "us"
[   146.342] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[   146.342] (II) No input driver/identifier specified (ignoring)
[   146.343] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[   146.343] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[   146.343] (II) Using input driver 'evdev' for 'Sleep Button'
[   146.343] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   146.344] (**) Sleep Button: always reports core events
[   146.344] (**) Sleep Button: Device: "/dev/input/event1"
[   146.344] (--) Sleep Button: Found keys
[   146.344] (II) Sleep Button: Configuring as keyboard
[   146.344] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[   146.344] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[   146.344] (**) Option "xkb_rules" "evdev"
[   146.344] (**) Option "xkb_model" "pc105"
[   146.344] (**) Option "xkb_layout" "us"
[   146.354] (II) config/udev: Adding input device HP Webcam-101 (/dev/input/event6)
[   146.354] (**) HP Webcam-101: Applying InputClass "evdev keyboard catchall"
[   146.355] (II) Using input driver 'evdev' for 'HP Webcam-101'
[   146.355] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   146.355] (**) HP Webcam-101: always reports core events
[   146.355] (**) HP Webcam-101: Device: "/dev/input/event6"
[   146.355] (--) HP Webcam-101: Found keys
[   146.355] (II) HP Webcam-101: Configuring as keyboard
[   146.355] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-5/1-5:1.0/input/input6/event6"
[   146.355] (II) XINPUT: Adding extended input device "HP Webcam-101" (type: KEYBOARD)
[   146.355] (**) Option "xkb_rules" "evdev"
[   146.355] (**) Option "xkb_model" "pc105"
[   146.355] (**) Option "xkb_layout" "us"
[   146.358] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event9)
[   146.358] (II) No input driver/identifier specified (ignoring)
[   146.359] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event10)
[   146.359] (II) No input driver/identifier specified (ignoring)
[   146.360] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event11)
[   146.360] (II) No input driver/identifier specified (ignoring)
[   146.363] (II) config/udev: Adding input device Microsoft  Compact Optical Mouse 500 (/dev/input/event5)
[   146.363] (**) Microsoft  Compact Optical Mouse 500: Applying InputClass "evdev pointer catchall"
[   146.363] (II) Using input driver 'evdev' for 'Microsoft  Compact Optical Mouse 500'
[   146.363] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   146.363] (**) Microsoft  Compact Optical Mouse 500: always reports core events
[   146.363] (**) Microsoft  Compact Optical Mouse 500: Device: "/dev/input/event5"
[   146.363] (--) Microsoft  Compact Optical Mouse 500: Found 3 mouse buttons
[   146.363] (--) Microsoft  Compact Optical Mouse 500: Found scroll wheel(s)
[   146.363] (--) Microsoft  Compact Optical Mouse 500: Found relative axes
[   146.363] (--) Microsoft  Compact Optical Mouse 500: Found x and y relative axes
[   146.363] (II) Microsoft  Compact Optical Mouse 500: Configuring as mouse
[   146.363] (II) Microsoft  Compact Optical Mouse 500: Adding scrollwheel support
[   146.363] (**) Microsoft  Compact Optical Mouse 500: YAxisMapping: buttons 4 and 5
[   146.363] (**) Microsoft  Compact Optical Mouse 500: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   146.363] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.0/input/input9/event5"
[   146.363] (II) XINPUT: Adding extended input device "Microsoft  Compact Optical Mouse 500" (type: MOUSE)
[   146.363] (II) Microsoft  Compact Optical Mouse 500: initialized for relative axes.
[   146.363] (**) Microsoft  Compact Optical Mouse 500: (accel) keeping acceleration scheme 1
[   146.363] (**) Microsoft  Compact Optical Mouse 500: (accel) acceleration profile 0
[   146.363] (**) Microsoft  Compact Optical Mouse 500: (accel) acceleration factor: 2.000
[   146.363] (**) Microsoft  Compact Optical Mouse 500: (accel) acceleration threshold: 4
[   146.364] (II) config/udev: Adding input device Microsoft  Compact Optical Mouse 500 (/dev/input/mouse0)
[   146.364] (II) No input driver/identifier specified (ignoring)
[   146.369] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[   146.369] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   146.369] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   146.369] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   146.369] (**) AT Translated Set 2 keyboard: always reports core events
[   146.369] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[   146.369] (--) AT Translated Set 2 keyboard: Found keys
[   146.369] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[   146.369] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[   146.369] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[   146.369] (**) Option "xkb_rules" "evdev"
[   146.369] (**) Option "xkb_model" "pc105"
[   146.369] (**) Option "xkb_layout" "us"
[   146.370] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event8)
[   146.370] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[   146.370] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[   146.370] (II) LoadModule: "synaptics"
[   146.371] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   146.371] (II) Module synaptics: vendor="X.Org Foundation"
[   146.371]     compiled for 1.10.0.902, module version = 1.3.99
[   146.371]     Module class: X.Org XInput Driver
[   146.371]     ABI class: X.Org XInput driver, version 12.3
[   146.371] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[   146.371] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   146.371] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   146.371] (**) Option "Device" "/dev/input/event8"
[   146.376] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5592
[   146.376] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4916
[   146.376] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[   146.376] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[   146.376] (--) SynPS/2 Synaptics TouchPad: buttons: left right
[   146.384] (--) SynPS/2 Synaptics TouchPad: touchpad found
[   146.384] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   146.388] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input8/event8"
[   146.388] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[   146.388] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[   146.388] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[   146.388] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.037
[   146.388] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[   146.388] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[   146.388] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[   146.388] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[   146.400] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[   146.400] (--) SynPS/2 Synaptics TouchPad: touchpad found
[   146.400] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[   146.400] (II) No input driver/identifier specified (ignoring)
[   146.410] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event7)
[   146.410] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[   146.410] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[   146.410] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   146.410] (**) HP WMI hotkeys: always reports core events
[   146.410] (**) HP WMI hotkeys: Device: "/dev/input/event7"
[   146.410] (--) HP WMI hotkeys: Found keys
[   146.410] (II) HP WMI hotkeys: Configuring as keyboard
[   146.410] (**) Option "config_info" "udev:/sys/devices/virtual/input/input7/event7"
[   146.410] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD)
[   146.410] (**) Option "xkb_rules" "evdev"
[   146.410] (**) Option "xkb_model" "pc105"
[   146.410] (**) Option "xkb_layout" "us"
[   148.480] (II) NOUVEAU(0): EDID vendor "AUO", prod id 4332
[   148.480] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   148.480] (II) NOUVEAU(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1486  768 771 775 806 -hsync -vsync (48.5 kHz)
[   148.784] (II) Quirked EDID physical size to 0x0 cm
[   149.205] (II) NOUVEAU(0): EDID vendor "AUO", prod id 4332
[   149.205] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   149.205] (II) NOUVEAU(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1486  768 771 775 806 -hsync -vsync (48.5 kHz)
[   149.509] (II) Quirked EDID physical size to 0x0 cm
[   149.931] (II) NOUVEAU(0): EDID vendor "AUO", prod id 4332
[   149.931] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   149.931] (II) NOUVEAU(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1486  768 771 775 806 -hsync -vsync (48.5 kHz)
[   150.235] (II) Quirked EDID physical size to 0x0 cm
[   150.655] (II) NOUVEAU(0): EDID vendor "AUO", prod id 4332
[   150.655] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   150.655] (II) NOUVEAU(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1486  768 771 775 806 -hsync -vsync (48.5 kHz)
[   150.959] (II) Quirked EDID physical size to 0x0 cm
[   156.567] (II) NOUVEAU(0): EDID vendor "AUO", prod id 4332
[   156.567] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   156.567] (II) NOUVEAU(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1486  768 771 775 806 -hsync -vsync (48.5 kHz)
[   156.871] (II) Quirked EDID physical size to 0x0 cm
[   158.697] (II) NOUVEAU(0): EDID vendor "AUO", prod id 4332
[   158.697] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   158.697] (II) NOUVEAU(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1486  768 771 775 806 -hsync -vsync (48.5 kHz)
[   159.001] (II) Quirked EDID physical size to 0x0 cm

---

