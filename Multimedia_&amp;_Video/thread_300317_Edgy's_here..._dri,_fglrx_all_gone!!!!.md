---
title: "Edgy's here... dri, fglrx all gone!!!!"
date: 2006-11-15
forum: Multimedia &amp; Video
---

### Post by jaywhy13 on 2006-11-15
I can't get DRI to start @ all.... I'm exhaused... a wad of info is printed below... please help

jay@s4b:/usr/lib/xorg/modules$ ll dri
lrwxrwxrwx 1 root root 12 2006-10-14 23:56 dri -> /usr/lib/dri


jay@s4b:/usr/lib/xorg/modules$ cat /etc/default/linux-restricted-modules-common
# This file is sourced from the linux-restricted-modules-common init
# script and is used to disable the link-on-boot feature, one module
# at a time. This can be useful if you want to use hand-compiled
# versions of one or more modules, but keep linux-restricted-modules
# installed on your system, or just to disable modules you don't use
# and speed up your boot process by a second or two.
#
# Use a space-separated list of modules you wish to not have linked
# on boot. The following example shows a (condensed) list of all
# modules shipped in the linux-restricted-modules packages:
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables both the nvidia drivers.
# You can also name each module individually, if you prefer a subset.

DISABLED_MODULES="fglrx"




jay@s4b:/usr/lib/xorg/modules$ ls -la /usr/lib/ | grep libGL
-rwxr-xr-x 1 root root 642476 2006-08-18 13:54 FGL.renamed.libGL.so.1.2
lrwxrwxrwx 1 root root 27 2006-11-13 05:30 libGL.so -> /usr/lib/fglrx/libGL.so.1.2
lrwxrwxrwx 1 root root 12 2006-11-13 06:15 libGL.so.1 -> libGL.so.1.2
-rw-r--r-- 1 root root 642552 2006-10-30 23:14 libGL.so.1.2
-rw-r--r-- 1 root root 671844 2006-08-24 00:29 libGLU.a
lrwxrwxrwx 1 root root 11 2006-11-10 09:37 libGLU.so -> libGLU.so.1
lrwxrwxrwx 1 root root 20 2006-11-10 09:37 libGLU.so.1 -> libGLU.so.1.3.060501
-rw-r--r-- 1 root root 483308 2006-08-24 00:29 libGLU.so.1.3.060501


jay@s4b:/usr/lib/xorg/modules$ ll /usr/X11R6/lib/modules/dri
lrwxrwxrwx 1 root root 16 2006-11-13 06:45 /usr/X11R6/lib/modules/dri -> ../../../lib/dri


# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
sbp2
fuse
fglrx



jay@s4b:/usr/lib/xorg/modules$ dpkg -l xorg-drver-fglrx
No packages found matching xorg-drver-fglrx.


jay@s4b:/usr/lib/xorg/modules$ dpkg -l linux-restricted-modules-$(uname -r)
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name Version Description
+++-============================================-============================================-================================================== ================================================== ====
ii linux-restricted-modules-2.6.17-10-386 2.6.17.6-1 Non-free Linux 2.6.17 modules on 386



jay@s4b:/usr/lib/xorg/modules$ cat /var/log/Xorg.0.log | grep fglrx
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
(II) fglrx(0): pEnt->device->identifier=0x81e17a0
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "MOBILITY RADEON X1400 (M54 7145)" (Chipset = 0x7145)
(--) fglrx(0): (PciSubVendor = 0x1028, PciSubDevice = 0x2002)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
(--) fglrx(0): MMIO registers at 0xdfdf0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.12
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: M54P
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR2
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) fglrx(0): Connected Display1: LCD on internal LVDS
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: LPL Model: 0 Serial#: 0
(II) fglrx(0): Year: 2005 Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 37 vert.: 23
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.592 redY: 0.344 greenX: 0.319 greenY: 0.553
(II) fglrx(0): blueX: 0.159 blueY: 0.144 whiteX: 0.312 whiteY: 0.328
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 96.2 MHz Image Size: 367 x 230 mm
(II) fglrx(0): h_active: 1440 h_sync: 1504 h_sync_end 1536 h_blank_end 1760 h_border: 0
(II) fglrx(0): v_active: 900 v_sync: 901 v_sync_end 904 v_blanking: 912 v_border: 0
(II) fglrx(0): YD477171WX2
(II) fglrx(0): &5@Im&#65533;
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000008
(II) fglrx(0): POWERplay version 3. 5 power states available:
(II) fglrx(0): 1. 432/396MHz @ 60Hz [enable load balancing]
(II) fglrx(0): 2. 324/135MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0): 3. 324/135MHz @ 60Hz [low voltage, enable sleep, thermal diode mode]
(II) fglrx(0): 4. 392/252MHz @ 60Hz [enable sleep]
(II) fglrx(0): 5. 392/252MHz @ 60Hz [enable sleep, thermal diode mode]
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0): PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled
(==) fglrx(0): TMDS coherent mode is enabled
(II) fglrx(0): Total of 13 modes found for primary display.
(--) fglrx(0): Virtual size is 1440x900 (pitch 0)
(**) fglrx(0): *Mode "1440x900": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1440x900" 96.21 1440 1504 1536 1760 900 903 904 912 +hsync +vsync
(**) fglrx(0): *Mode "1152x864": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864" 96.21 1152 1504 1536 1760 864 903 904 912 +hsync +vsync
(**) fglrx(0): *Mode "1024x768": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768" 96.21 1024 1504 1536 1760 768 903 904 912 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600" 96.21 800 1504 1536 1760 600 903 904 912 +hsync +vsync
(**) fglrx(0): *Mode "640x480": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480" 96.21 640 1504 1536 1760 480 903 904 912 +hsync +vsync
(**) fglrx(0): Default mode "1280x720": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720" 96.21 1280 1504 1536 1760 720 903 904 912 +hsync +vsync
(**) fglrx(0): Default mode "720x480": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480" 96.21 720 1504 1536 1760 480 903 904 912 +hsync +vsync
(**) fglrx(0): Default mode "640x432": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432" 96.21 640 1504 1536 1760 432 903 904 912 +hsync +vsync
(**) fglrx(0): Default mode "640x400": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400" 96.21 640 1504 1536 1760 400 903 904 912 +hsync +vsync
(**) fglrx(0): Default mode "512x384": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384" 96.21 512 1504 1536 1760 384 903 904 912 +hsync +vsync
(**) fglrx(0): Default mode "400x300": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300" 96.21 400 1504 1536 1760 300 903 904 912 +hsync +vsync
(**) fglrx(0): Default mode "320x240": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240" 96.21 320 1504 1536 1760 240 903 904 912 +hsync +vsync
(**) fglrx(0): Default mode "320x200": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200" 96.21 320 1504 1536 1760 200 903 904 912 +hsync +vsync
(--) fglrx(0): Display dimensions: (370, 230) mm
(--) fglrx(0): DPI set to (98, 99)
(--) fglrx(0): Virtual size is 1440x900 (pitch 1472)
(**) fglrx(0): *Mode "1440x900": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1440x900" 96.21 1440 1504 1536 1760 900 903 904 912 +hsync +vsync
(**) fglrx(0): *Mode "1152x864": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864" 96.21 1152 1504 1536 1760 864 903 904 912 +hsync +vsync
(**) fglrx(0): *Mode "1024x768": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768" 96.21 1024 1504 1536 1760 768 903 904 912 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600" 96.21 800 1504 1536 1760 600 903 904 912 +hsync +vsync
(**) fglrx(0): *Mode "640x480": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480" 96.21 640 1504 1536 1760 480 903 904 912 +hsync +vsync
(**) fglrx(0): Default mode "1280x720": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720" 96.21 1280 1504 1536 1760 720 903 904 912 +hsync +vsync
(**) fglrx(0): Default mode "720x480": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480" 96.21 720 1504 1536 1760 480 903 904 912 +hsync +vsync
(**) fglrx(0): Default mode "640x432": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432" 96.21 640 1504 1536 1760 432 903 904 912 +hsync +vsync
(**) fglrx(0): Default mode "640x400": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400" 96.21 640 1504 1536 1760 400 903 904 912 +hsync +vsync
(**) fglrx(0): Default mode "512x384": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384" 96.21 512 1504 1536 1760 384 903 904 912 +hsync +vsync
(**) fglrx(0): Default mode "400x300": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300" 96.21 400 1504 1536 1760 300 903 904 912 +hsync +vsync
(**) fglrx(0): Default mode "320x240": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240" 96.21 320 1504 1536 1760 240 903 904 912 +hsync +vsync
(**) fglrx(0): Default mode "320x200": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200" 96.21 320 1504 1536 1760 200 903 904 912 +hsync +vsync
(==) fglrx(0): NoAccel = NO
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): cpuSpeedMHz: 0x00000729
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 128 MB
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(II) fglrx(0): UMM Bus area: 0xc0715000 (size=0x078cb000)
(II) fglrx(0): UMM area: 0xc0715000 (size=0x078cb000)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.1.0
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb78ff000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0): Name: fglrx
(II) fglrx(0): Version: 8.29.6
(II) fglrx(0): Date: Sep 19 2006
(II) fglrx(0): Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb78ff000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed! *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO) *
(WW) fglrx(0): * no 3D acceleration available *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x07fe0000
(II) fglrx(0): Splitting WC range: base: 0xc0000000, size: 0x7fe0000
(II) fglrx(0): Splitting WC range: base: 0xc4000000, size: 0x3fe0000
(II) fglrx(0): Splitting WC range: base: 0xc6000000, size: 0x1fe0000
(II) fglrx(0): Splitting WC range: base: 0xc7000000, size: 0xfe0000
(II) fglrx(0): Splitting WC range: base: 0xc7800000, size: 0x7e0000
(II) fglrx(0): Splitting WC range: base: 0xc7c00000, size: 0x3e0000
(II) fglrx(0): Splitting WC range: base: 0xc7e00000, size: 0x1e0000
(II) fglrx(0): Splitting WC range: base: 0xc7f00000, size: 0xe0000
(II) fglrx(0): Splitting WC range: base: 0xc7f80000, size: 0x60000
(==) fglrx(0): Write-combining range (0xc7fc0000,0x20000)
(==) fglrx(0): Write-combining range (0xc7f80000,0x60000)
(==) fglrx(0): Write-combining range (0xc7f00000,0xe0000)
(==) fglrx(0): Write-combining range (0xc7e00000,0x1e0000)
(==) fglrx(0): Write-combining range (0xc7c00000,0x3e0000)
(==) fglrx(0): Write-combining range (0xc7800000,0x7e0000)
(WW) fglrx(0): Failed to set up write-combining range (0xc7000000,0xfe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xc6000000,0x1fe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xc4000000,0x3fe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xc0000000,0x7fe0000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1472,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1472,900) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Using hardware cursor
(II) fglrx(0): Largest offscreen area available: 1472 x 7288
(WW) fglrx(0): Video Overlay not supported on AVIVO based graphics cards. For XVideo support please upgrade to Xorg 6.9 or later and use Option "TexturedVideo".
Edit/Delete Message

---

### Post by jsteve54302 on 2006-11-20
> **jaywhy13 said:**
> I can't get DRI to start @ all.... I'm exhaused... a wad of info is printed below... please help

jay@s4b:/usr/lib/xorg/modules$ ll dri
lrwxrwxrwx 1 root root 12 2006-10-14 23:56 dri -> /usr/lib/dri

This means DRI exists...


> jay@s4b:/usr/lib/xorg/modules$ cat /etc/default/linux-restricted-modules-common
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables both the nvidia drivers.
# You can also name each module individually, if you prefer a subset.

DISABLED_MODULES="fglrx"You'll want to comment this out unless you have another fglrx under a different name - it's telling the kernel not to load the fglrx module, which I think is the exact opposite of what you want.  You need fglrx or some other appropriate driver for DRI to have
any chance of loading.

> jay@s4b:/usr/lib/xorg/modules$ ls -la /usr/lib/ | grep libGL
-rwxr-xr-x 1 root root 642476 2006-08-18 13:54 FGL.renamed.libGL.so.1.2
lrwxrwxrwx 1 root root 27 2006-11-13 05:30 libGL.so -> /usr/lib/fglrx/libGL.so.1.2
lrwxrwxrwx 1 root root 12 2006-11-13 06:15 libGL.so.1 -> libGL.so.1.2
-rw-r--r-- 1 root root 642552 2006-10-30 23:14 libGL.so.1.2
-rw-r--r-- 1 root root 671844 2006-08-24 00:29 libGLU.a
lrwxrwxrwx 1 root root 11 2006-11-10 09:37 libGLU.so -> libGLU.so.1
lrwxrwxrwx 1 root root 20 2006-11-10 09:37 libGLU.so.1 -> libGLU.so.1.3.060501
-rw-r--r-- 1 root root 483308 2006-08-24 00:29 libGLU.so.1.3.060501These show that the GL libraries exist, you still need the fglrx and GLCore modules...  These will install with the xorg-driver-fglrx package.

> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
sbp2
fuse
fglrxThis should work

> jay@s4b:/usr/lib/xorg/modules$ dpkg -l xorg-drver-fglrx
No packages found matching xorg-drver-fglrx.Looks like you dropped the "i" in driver...  Happens to me all the time...
also, try 

```
dpkg -l *fglrx*
```to get every package conatining the string "fglrx" anywhere in its name - there aren't that many, and they all relate to the fglrx driver.

> jay@s4b:/usr/lib/xorg/modules$ dpkg -l linux-restricted-modules-$(uname -r)
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name Version Description
+++-============================================-============================================-================================================== ================================================== ====
ii linux-restricted-modules-2.6.17-10-386 2.6.17.6-1 Non-free Linux 2.6.17 modules on 386You have the non-free (restricted) modules installed...

> jay@s4b:/usr/lib/xorg/modules$ cat /var/log/Xorg.0.log | grep fglrx
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
(II) fglrx(0): pEnt->device->identifier=0x81e17a0
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"fglrx is starting to load.  I had some trouble getting mine to work until I turned on the "OpenGLOverlay" for some reason though...  try

```
gksudo gedit /etc/X11/xorg.conf
```and add the line

```
Option          "OpenGLOverlay"     "on"
```in your "Device" section.

> (WW) fglrx(0): board is an unknown third party board, chipset is supportedThis could, possibly, be bad, but that's unlikely.  On rare occasions, 3rd party manufacturers don't follow the specs too closely, and a board that should work, doesn't...

> (II) fglrx(0): Name: fglrx
(II) fglrx(0): Version: 8.29.6
(II) fglrx(0): Date: Sep 19 2006
(II) fglrx(0): Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not workThis bad - and why fglrx isn't working.  For some reason, your kernel module seems not to have been updated, or else it was using a renamed fglrx modules, or the fglrx module was not loaded.

Actually, it looks like you're using XFree86..  If so, you may want to upgrade to XOrg, if you can...  You might want to search for "xorg upgrade" in the Ubuntu forums and Wiki, and on google...

---

