---
title: "Video lag on fresh ubuntu install. Check details."
date: 2010-11-07
forum: Multimedia Software
---

### Post by Gregg0 on 2010-11-07
I installed ubuntu yesterday and today I've noticed that the video lags a bit after playing the first 5-7 minutes. It lags probably about ~1 second behind which makes the video unwatchable. 

Here are some info's I hope help you determine what could be the cause.
Graphics card is Intel 4500MHD, I have 3 gb of ddr3 and 2,26Ghz.

Free space:
```
free -m
             total       used       free     shared    buffers     cached
Mem:          2956       1820       1136          0        129        929
-/+ buffers/cache:        761       2195
Swap:         7776          0       7776

```


Xorg log:
```
[    21.705] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    21.705] X Protocol Version 11, Revision 0
[    21.705] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    21.705] Current Operating System: Linux Daniel 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686
[    21.705] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=283a33a7-e481-4103-b198-cec497e558f5 ro quiet splash
[    21.705] Build Date: 16 September 2010  05:39:22PM
[    21.705] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[    21.705] Current version of pixman: 0.18.4
[    21.705] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    21.705] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    21.705] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov  7 16:44:41 2010
[    21.766] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    21.793] (==) No Layout section.  Using the first Screen section.
[    21.793] (==) No screen section available. Using defaults.
[    21.793] (**) |-->Screen "Default Screen Section" (0)
[    21.793] (**) |   |-->Monitor "<default monitor>"
[    21.794] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    21.794] (==) Automatically adding devices
[    21.794] (==) Automatically enabling devices
[    21.808] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    21.808] 	Entry deleted from font path.
[    21.830] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    21.830] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    21.830] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    21.830] (II) Loader magic: 0x81f8e00
[    21.830] (II) Module ABI versions:
[    21.830] 	X.Org ANSI C Emulation: 0.4
[    21.830] 	X.Org Video Driver: 8.0
[    21.830] 	X.Org XInput driver : 11.0
[    21.830] 	X.Org Server Extension : 4.0
[    21.831] (--) PCI:*(0:0:2:0) 8086:2a42:104d:903b rev 7, Mem @ 0xd4400000/4194304, 0xc0000000/268435456, I/O @ 0x00006160/8
[    21.831] (--) PCI: (0:0:2:1) 8086:2a43:104d:903b rev 7, Mem @ 0xd7800000/1048576
[    21.831] (II) Open ACPI successful (/var/run/acpid.socket)
[    21.831] (II) LoadModule: "extmod"
[    21.854] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    21.979] (II) Module extmod: vendor="X.Org Foundation"
[    21.979] 	compiled for 1.9.0, module version = 1.0.0
[    21.979] 	Module class: X.Org Server Extension
[    21.979] 	ABI class: X.Org Server Extension, version 4.0
[    21.979] (II) Loading extension MIT-SCREEN-SAVER
[    21.979] (II) Loading extension XFree86-VidModeExtension
[    21.979] (II) Loading extension XFree86-DGA
[    22.009] (II) Loading extension DPMS
[    22.009] (II) Loading extension XVideo
[    22.009] (II) Loading extension XVideo-MotionCompensation
[    22.009] (II) Loading extension X-Resource
[    22.009] (II) LoadModule: "dbe"
[    22.009] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    22.031] (II) Module dbe: vendor="X.Org Foundation"
[    22.031] 	compiled for 1.9.0, module version = 1.0.0
[    22.031] 	Module class: X.Org Server Extension
[    22.031] 	ABI class: X.Org Server Extension, version 4.0
[    22.031] (II) Loading extension DOUBLE-BUFFER
[    22.031] (II) LoadModule: "glx"
[    22.031] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    22.059] (II) Module glx: vendor="X.Org Foundation"
[    22.059] 	compiled for 1.9.0, module version = 1.0.0
[    22.059] 	ABI class: X.Org Server Extension, version 4.0
[    22.060] (==) AIGLX enabled
[    22.060] (II) Loading extension GLX
[    22.060] (II) LoadModule: "record"
[    22.061] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    22.061] (II) Module record: vendor="X.Org Foundation"
[    22.061] 	compiled for 1.9.0, module version = 1.13.0
[    22.061] 	Module class: X.Org Server Extension
[    22.061] 	ABI class: X.Org Server Extension, version 4.0
[    22.061] (II) Loading extension RECORD
[    22.061] (II) LoadModule: "dri"
[    22.062] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    22.063] (II) Module dri: vendor="X.Org Foundation"
[    22.063] 	compiled for 1.9.0, module version = 1.0.0
[    22.063] 	ABI class: X.Org Server Extension, version 4.0
[    22.063] (II) Loading extension XFree86-DRI
[    22.063] (II) LoadModule: "dri2"
[    22.063] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    22.064] (II) Module dri2: vendor="X.Org Foundation"
[    22.064] 	compiled for 1.9.0, module version = 1.2.0
[    22.064] 	ABI class: X.Org Server Extension, version 4.0
[    22.064] (II) Loading extension DRI2
[    22.064] (==) Matched intel as autoconfigured driver 0
[    22.064] (==) Matched vesa as autoconfigured driver 1
[    22.064] (==) Matched fbdev as autoconfigured driver 2
[    22.064] (==) Assigned the driver to the xf86ConfigLayout
[    22.064] (II) LoadModule: "intel"
[    22.064] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    22.078] (II) Module intel: vendor="X.Org Foundation"
[    22.078] 	compiled for 1.9.0, module version = 2.12.0
[    22.078] 	Module class: X.Org Video Driver
[    22.078] 	ABI class: X.Org Video Driver, version 8.0
[    22.078] (II) LoadModule: "vesa"
[    22.078] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    22.084] (II) Module vesa: vendor="X.Org Foundation"
[    22.084] 	compiled for 1.8.99.905, module version = 2.3.0
[    22.084] 	Module class: X.Org Video Driver
[    22.084] 	ABI class: X.Org Video Driver, version 8.0
[    22.084] (II) LoadModule: "fbdev"
[    22.085] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    22.090] (II) Module fbdev: vendor="X.Org Foundation"
[    22.090] 	compiled for 1.8.99.905, module version = 0.4.2
[    22.090] 	ABI class: X.Org Video Driver, version 8.0
[    22.090] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[    22.091] (II) VESA: driver for VESA chipsets: vesa
[    22.091] (II) FBDEV: driver for framebuffer: fbdev
[    22.091] (++) using VT number 7

[    22.091] (WW) Falling back to old probe method for vesa
[    22.091] (WW) Falling back to old probe method for fbdev
[    22.091] (II) Loading sub module "fbdevhw"
[    22.091] (II) LoadModule: "fbdevhw"
[    22.091] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    22.104] (II) Module fbdevhw: vendor="X.Org Foundation"
[    22.104] 	compiled for 1.9.0, module version = 0.0.2
[    22.104] 	ABI class: X.Org Video Driver, version 8.0
[    22.106] drmOpenDevice: node name is /dev/dri/card0
[    22.106] drmOpenDevice: open result is 9, (OK)
[    22.128] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    22.128] drmOpenDevice: node name is /dev/dri/card0
[    22.128] drmOpenDevice: open result is 9, (OK)
[    22.128] drmOpenByBusid: drmOpenMinor returns 9
[    22.128] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    22.128] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    22.128] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    22.128] (==) intel(0): RGB weight 888
[    22.128] (==) intel(0): Default visual is TrueColor
[    22.128] (II) intel(0): Integrated Graphics Chipset: Intel(R) GM45
[    22.128] (--) intel(0): Chipset: "GM45"
[    22.128] (==) intel(0): video overlay key set to 0x101fe
[    22.144] (II) intel(0): Output VGA1 has no monitor section
[    22.144] (II) intel(0): Output LVDS1 has no monitor section
[    22.144] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    22.153] (II) intel(0): Output HDMI1 has no monitor section
[    22.153] (II) intel(0): Output DP1 has no monitor section
[    22.158] (II) intel(0): Output DP2 has no monitor section
[    22.180] (II) intel(0): EDID for output VGA1
[    22.259] (II) intel(0): EDID for output LVDS1
[    22.259] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    22.259] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    22.259] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    22.259] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    22.259] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    22.259] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    22.259] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    22.259] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    22.259] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    22.259] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    22.259] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    22.259] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    22.259] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    22.259] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    22.259] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    22.259] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    22.259] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    22.259] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    22.259] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    22.259] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    22.259] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    22.259] (II) intel(0): Not using default mode "320x175" (doublescan mode not supported)
[    22.259] (II) intel(0): Not using default mode "320x200" (doublescan mode not supported)
[    22.259] (II) intel(0): Not using default mode "360x200" (doublescan mode not supported)
[    22.259] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    22.259] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    22.259] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "1024x768i" (interlace mode not supported)
[    22.260] (II) intel(0): Not using default mode "512x384i" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
[    22.260] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
[    22.260] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[    22.260] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[    22.260] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
[    22.260] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
[    22.260] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
[    22.260] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
[    22.260] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
[    22.260] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "1600x1200" (hsync out of range)
[    22.260] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
[    22.260] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "1792x1344" (hsync out of range)
[    22.260] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
[    22.260] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "1856x1392" (hsync out of range)
[    22.260] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
[    22.260] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "1920x1440" (hsync out of range)
[    22.260] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "416x312" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[    22.260] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
[    22.260] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
[    22.260] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
[    22.260] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    22.260] (II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
[    22.261] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    22.261] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    22.261] (II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
[    22.261] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    22.261] (II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
[    22.261] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    22.261] (II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
[    22.261] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    22.261] (II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
[    22.261] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    22.261] (II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
[    22.261] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    22.261] (II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
[    22.261] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    22.261] (II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
[    22.261] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    22.261] (II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
[    22.261] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    22.261] (II) intel(0): Not using default mode "1920x1440" (hsync out of range)
[    22.261] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    22.261] (II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
[    22.261] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    22.261] (II) intel(0): Not using default mode "2048x1536" (hsync out of range)
[    22.261] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    22.261] (II) intel(0): Not using default mode "2048x1536" (hsync out of range)
[    22.261] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    22.261] (II) intel(0): Printing probed modes for output LVDS1
[    22.261] (II) intel(0): Modeline "1440x900"x60.0   96.31  1440 1504 1536 1760  900 903 906 912 -hsync -vsync (54.7 kHz)
[    22.261] (II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    22.261] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    22.261] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[    22.261] (II) intel(0): Modeline "1152x864"x100.0  143.47  1152 1232 1360 1568  864 865 868 915 -hsync +vsync (91.5 kHz)
[    22.261] (II) intel(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
[    22.261] (II) intel(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
[    22.261] (II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    22.261] (II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
[    22.261] (II) intel(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
[    22.261] (II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[    22.261] (II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[    22.261] (II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    22.261] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    22.261] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    22.261] (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    22.261] (II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[    22.261] (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    22.261] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    22.261] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    22.261] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    22.261] (II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[    22.261] (II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    22.261] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    22.261] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    22.261] (II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
[    22.261] (II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
[    22.261] (II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
[    22.270] (II) intel(0): EDID for output HDMI1
[    22.270] (II) intel(0): EDID for output DP1
[    22.275] (II) intel(0): EDID for output DP2
[    22.275] (II) intel(0): Output VGA1 disconnected
[    22.275] (II) intel(0): Output LVDS1 connected
[    22.275] (II) intel(0): Output HDMI1 disconnected
[    22.275] (II) intel(0): Output DP1 disconnected
[    22.275] (II) intel(0): Output DP2 disconnected
[    22.275] (II) intel(0): Using exact sizes for initial modes
[    22.275] (II) intel(0): Output LVDS1 using initial mode 1440x900
[    22.275] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    22.275] (II) intel(0): Kernel page flipping support detected, but forcibly disabled.
[    22.275] (==) intel(0): DPI set to (96, 96)
[    22.275] (II) Loading sub module "fb"
[    22.275] (II) LoadModule: "fb"
[    22.276] (II) Loading /usr/lib/xorg/modules/libfb.so
[    22.456] (II) Module fb: vendor="X.Org Foundation"
[    22.456] 	compiled for 1.9.0, module version = 1.0.0
[    22.456] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    22.456] (II) UnloadModule: "vesa"
[    22.456] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    22.456] (II) UnloadModule: "fbdev"
[    22.456] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    22.456] (II) UnloadModule: "fbdevhw"
[    22.456] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    22.456] (==) Depth 24 pixmap format is 32 bpp
[    22.456] (II) intel(0): [DRI2] Setup complete
[    22.456] (II) intel(0): [DRI2]   DRI driver: i965
[    22.457] (**) intel(0): Tiling enabled
[    22.457] (**) intel(0): SwapBuffers wait enabled
[    22.457] (==) intel(0): VideoRam: 262144 KB
[    22.457] (II) intel(0): Allocated new frame buffer 1472x900 stride 6144, tiled
[    22.717] (II) UXA(0): Driver registered support for the following operations:
[    22.717] (II)         solid
[    22.717] (II)         copy
[    22.717] (II)         composite (RENDER acceleration)
[    22.717] (II)         put_image
[    22.717] (II)         get_image
[    22.717] (==) intel(0): Backing store disabled
[    22.717] (==) intel(0): Silken mouse enabled
[    22.719] (II) intel(0): Initializing HW Cursor
[    22.752] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    22.756] (==) intel(0): DPMS enabled
[    22.756] (==) intel(0): Intel XvMC decoder enabled
[    22.756] (II) intel(0): Set up textured video
[    22.756] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    22.756] (II) intel(0): direct rendering: DRI2 Enabled
[    22.756] (--) RandR disabled
[    22.756] (II) Initializing built-in extension Generic Event Extension
[    22.756] (II) Initializing built-in extension SHAPE
[    22.756] (II) Initializing built-in extension MIT-SHM
[    22.756] (II) Initializing built-in extension XInputExtension
[    22.756] (II) Initializing built-in extension XTEST
[    22.756] (II) Initializing built-in extension BIG-REQUESTS
[    22.756] (II) Initializing built-in extension SYNC
[    22.756] (II) Initializing built-in extension XKEYBOARD
[    22.756] (II) Initializing built-in extension XC-MISC
[    22.756] (II) Initializing built-in extension SECURITY
[    22.756] (II) Initializing built-in extension XINERAMA
[    22.756] (II) Initializing built-in extension XFIXES
[    22.756] (II) Initializing built-in extension RENDER
[    22.756] (II) Initializing built-in extension RANDR
[    22.756] (II) Initializing built-in extension COMPOSITE
[    22.756] (II) Initializing built-in extension DAMAGE
[    22.756] (II) Initializing built-in extension GESTURE
[    22.994] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    22.995] (II) AIGLX: enabled GLX_INTEL_swap_event
[    22.995] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    22.995] (II) AIGLX: enabled GLX_SGI_make_current_read
[    22.995] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    22.995] (II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
[    22.995] (II) GLX: Initialized DRI2 GL provider for screen 0
[    22.996] (II) intel(0): Setting screen physical size to 380 x 238
[    23.215] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    23.239] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    23.239] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.239] (II) LoadModule: "evdev"
[    23.240] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.294] (II) Module evdev: vendor="X.Org Foundation"
[    23.294] 	compiled for 1.9.0, module version = 2.3.2
[    23.294] 	Module class: X.Org XInput Driver
[    23.294] 	ABI class: X.Org XInput driver, version 11.0
[    23.294] (**) Power Button: always reports core events
[    23.294] (**) Power Button: Device: "/dev/input/event2"
[    23.300] (II) Power Button: Found keys
[    23.300] (II) Power Button: Configuring as keyboard
[    23.300] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    23.300] (**) Option "xkb_rules" "evdev"
[    23.300] (**) Option "xkb_model" "pc105"
[    23.300] (**) Option "xkb_layout" "us"
[    23.301] (II) config/udev: Adding input device Video Bus (/dev/input/event9)
[    23.301] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    23.301] (**) Video Bus: always reports core events
[    23.301] (**) Video Bus: Device: "/dev/input/event9"
[    23.312] (II) Video Bus: Found keys
[    23.312] (II) Video Bus: Configuring as keyboard
[    23.312] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    23.312] (**) Option "xkb_rules" "evdev"
[    23.312] (**) Option "xkb_model" "pc105"
[    23.312] (**) Option "xkb_layout" "us"
[    23.313] (II) config/udev: Adding input device Sony Vaio Keys (/dev/input/event6)
[    23.313] (**) Sony Vaio Keys: Applying InputClass "evdev keyboard catchall"
[    23.313] (**) Sony Vaio Keys: always reports core events
[    23.313] (**) Sony Vaio Keys: Device: "/dev/input/event6"
[    23.324] (II) Sony Vaio Keys: Found keys
[    23.324] (II) Sony Vaio Keys: Configuring as keyboard
[    23.324] (II) XINPUT: Adding extended input device "Sony Vaio Keys" (type: KEYBOARD)
[    23.324] (**) Option "xkb_rules" "evdev"
[    23.324] (**) Option "xkb_model" "pc105"
[    23.324] (**) Option "xkb_layout" "us"
[    23.326] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    23.326] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.326] (**) Power Button: always reports core events
[    23.326] (**) Power Button: Device: "/dev/input/event0"
[    23.336] (II) Power Button: Found keys
[    23.336] (II) Power Button: Configuring as keyboard
[    23.336] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    23.336] (**) Option "xkb_rules" "evdev"
[    23.336] (**) Option "xkb_model" "pc105"
[    23.336] (**) Option "xkb_layout" "us"
[    23.337] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    23.337] (II) No input driver/identifier specified (ignoring)
[    23.338] (II) config/udev: Adding input device UVC Camera (05ca:183f) (/dev/input/event5)
[    23.338] (**) UVC Camera (05ca:183f): Applying InputClass "evdev keyboard catchall"
[    23.338] (**) UVC Camera (05ca:183f): always reports core events
[    23.338] (**) UVC Camera (05ca:183f): Device: "/dev/input/event5"
[    23.348] (II) UVC Camera (05ca:183f): Found keys
[    23.348] (II) UVC Camera (05ca:183f): Configuring as keyboard
[    23.348] (II) XINPUT: Adding extended input device "UVC Camera (05ca:183f)" (type: KEYBOARD)
[    23.348] (**) Option "xkb_rules" "evdev"
[    23.348] (**) Option "xkb_model" "pc105"
[    23.348] (**) Option "xkb_layout" "us"
[    23.350] (II) config/udev: Adding input device Genius Optical Mouse (/dev/input/event4)
[    23.350] (**) Genius Optical Mouse: Applying InputClass "evdev pointer catchall"
[    23.350] (**) Genius Optical Mouse: always reports core events
[    23.350] (**) Genius Optical Mouse: Device: "/dev/input/event4"
[    23.360] (II) Genius Optical Mouse: Found 3 mouse buttons
[    23.360] (II) Genius Optical Mouse: Found scroll wheel(s)
[    23.360] (II) Genius Optical Mouse: Found relative axes
[    23.360] (II) Genius Optical Mouse: Found x and y relative axes
[    23.360] (II) Genius Optical Mouse: Configuring as mouse
[    23.360] (**) Genius Optical Mouse: YAxisMapping: buttons 4 and 5
[    23.360] (**) Genius Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    23.360] (II) XINPUT: Adding extended input device "Genius Optical Mouse" (type: MOUSE)
[    23.360] (II) Genius Optical Mouse: initialized for relative axes.
[    23.360] (II) config/udev: Adding input device Genius Optical Mouse (/dev/input/mouse0)
[    23.360] (II) No input driver/identifier specified (ignoring)
[    23.364] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    23.364] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    23.365] (**) AT Translated Set 2 keyboard: always reports core events
[    23.365] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    23.376] (II) AT Translated Set 2 keyboard: Found keys
[    23.376] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    23.376] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    23.376] (**) Option "xkb_rules" "evdev"
[    23.376] (**) Option "xkb_model" "pc105"
[    23.376] (**) Option "xkb_layout" "us"
[    23.376] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event8)
[    23.376] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    23.376] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    23.376] (II) LoadModule: "synaptics"
[    23.377] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    23.385] (II) Module synaptics: vendor="X.Org Foundation"
[    23.386] 	compiled for 1.9.0, module version = 1.2.2
[    23.386] 	Module class: X.Org XInput Driver
[    23.386] 	ABI class: X.Org XInput driver, version 11.0
[    23.386] (II) Synaptics touchpad driver version 1.2.2
[    23.386] (**) Option "Device" "/dev/input/event8"
[    23.436] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5356
[    23.436] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4440
[    23.436] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    23.436] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    23.436] (II) SynPS/2 Synaptics TouchPad: buttons: left right
[    23.480] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    23.480] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    23.480] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    23.480] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    23.480] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    23.480] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    23.480] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    23.484] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    23.484] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse2)
[    23.484] (II) No input driver/identifier specified (ignoring)
[    23.487] (II) config/udev: Adding input device Sony Vaio Jogdial (/dev/input/event7)
[    23.487] (II) No input driver/identifier specified (ignoring)
[    23.487] (II) config/udev: Adding input device Sony Vaio Jogdial (/dev/input/mouse1)
[    23.487] (II) No input driver/identifier specified (ignoring)
```


```
ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   2892  1608 ?        Ss   16:44   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    16:44   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    16:44   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    16:44   0:00 [migration/0]
root         5  0.0  0.0      0     0 ?        S    16:44   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S    16:44   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S    16:44   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S    16:44   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S    16:44   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        S    16:44   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S    16:44   0:00 [cpuset]
root        12  0.0  0.0      0     0 ?        S    16:44   0:00 [khelper]
root        13  0.0  0.0      0     0 ?        S    16:44   0:00 [netns]
root        14  0.0  0.0      0     0 ?        S    16:44   0:00 [async/mgr]
root        15  0.0  0.0      0     0 ?        S    16:44   0:00 [pm]
root        17  0.0  0.0      0     0 ?        S    16:44   0:00 [sync_supers]
root        18  0.0  0.0      0     0 ?        S    16:44   0:00 [bdi-default]
root        19  0.0  0.0      0     0 ?        S    16:44   0:00 [kintegrityd/0]
root        20  0.0  0.0      0     0 ?        S    16:44   0:00 [kintegrityd/1]
root        21  0.0  0.0      0     0 ?        S    16:44   0:00 [kblockd/0]
root        22  0.0  0.0      0     0 ?        S    16:44   0:00 [kblockd/1]
root        23  0.0  0.0      0     0 ?        S    16:44   0:00 [kacpid]
root        24  0.0  0.0      0     0 ?        S    16:44   0:00 [kacpi_notify]
root        25  0.0  0.0      0     0 ?        S    16:44   0:00 [kacpi_hotplug]
root        26  0.0  0.0      0     0 ?        S    16:44   0:00 [ata_aux]
root        27  0.0  0.0      0     0 ?        S    16:44   0:00 [ata_sff/0]
root        28  0.0  0.0      0     0 ?        S    16:44   0:00 [ata_sff/1]
root        29  0.0  0.0      0     0 ?        S    16:44   0:00 [khubd]
root        30  0.0  0.0      0     0 ?        S    16:44   0:00 [kseriod]
root        31  0.0  0.0      0     0 ?        S    16:44   0:00 [kmmcd]
root        32  0.0  0.0      0     0 ?        S    16:44   0:00 [khungtaskd]
root        33  0.0  0.0      0     0 ?        S    16:44   0:01 [kswapd0]
root        34  0.0  0.0      0     0 ?        SN   16:44   0:00 [ksmd]
root        35  0.0  0.0      0     0 ?        S    16:44   0:00 [aio/0]
root        36  0.0  0.0      0     0 ?        S    16:44   0:00 [aio/1]
root        37  0.0  0.0      0     0 ?        S    16:44   0:00 [ecryptfs-kthrea]
root        38  0.0  0.0      0     0 ?        S    16:44   0:00 [crypto/0]
root        39  0.0  0.0      0     0 ?        S    16:44   0:00 [crypto/1]
root        51  0.0  0.0      0     0 ?        S    16:44   0:00 [scsi_eh_0]
root        52  0.0  0.0      0     0 ?        S    16:44   0:02 [scsi_eh_1]
root        56  0.0  0.0      0     0 ?        S    16:44   0:00 [scsi_eh_2]
root        57  0.0  0.0      0     0 ?        S    16:44   0:00 [scsi_eh_3]
root        61  0.0  0.0      0     0 ?        S    16:44   0:00 [kstriped]
root        62  0.0  0.0      0     0 ?        S    16:44   0:00 [kmpathd/0]
root        63  0.0  0.0      0     0 ?        S    16:44   0:00 [kmpathd/1]
root        64  0.0  0.0      0     0 ?        S    16:44   0:00 [kmpath_handlerd]
root        65  0.0  0.0      0     0 ?        S    16:44   0:00 [ksnapd]
root        66  0.0  0.0      0     0 ?        S    16:44   0:10 [kondemand/0]
root        67  0.0  0.0      0     0 ?        S    16:44   0:08 [kondemand/1]
root        68  0.0  0.0      0     0 ?        S    16:44   0:00 [kconservative/0]
root        69  0.0  0.0      0     0 ?        S    16:44   0:00 [kconservative/1]
root       307  0.0  0.0      0     0 ?        S    16:44   0:03 [jbd2/sda1-8]
root       308  0.0  0.0      0     0 ?        S    16:44   0:00 [ext4-dio-unwrit]
root       309  0.0  0.0      0     0 ?        S    16:44   0:00 [ext4-dio-unwrit]
root       353  0.0  0.0   2396   864 ?        S    16:44   0:00 upstart-udev-bridge --daemon
root       372  0.0  0.0      0     0 ?        S    16:44   0:02 [flush-8:0]
root       373  0.0  0.0   2888  1188 ?        S<s  16:44   0:00 udevd --daemon
root       655  0.0  0.0      0     0 ?        S    16:44   0:00 [cfg80211]
root       658  0.0  0.0      0     0 ?        S    16:44   0:00 [scsi_eh_4]
root       659  0.0  0.0      0     0 ?        S    16:44   0:00 [usb-storage]
root       661  0.0  0.0      0     0 ?        S    16:44   0:00 [scsi_eh_5]
root       662  0.0  0.0      0     0 ?        S    16:44   0:00 [usb-storage]
root       672  0.0  0.0      0     0 ?        S    16:44   0:00 [pccardd]
root       676  0.0  0.0      0     0 ?        S    16:44   0:00 [usbhid_resumer]
root       686  0.0  0.0      0     0 ?        S    16:44   0:00 [kpsmoused]
root       743  0.0  0.0      0     0 ?        S    16:44   0:00 [iwlagn]
root       747  0.0  0.0      0     0 ?        S    16:44   0:03 [phy0]
syslog     820  0.0  0.0  34596  1300 ?        Sl   16:44   0:00 rsyslogd -c4
102        884  0.0  0.0   3588  1856 ?        Ss   16:44   0:01 dbus-daemon --system --fork
avahi      910  0.0  0.0   3016  1312 ?        S    16:44   0:00 avahi-daemon: running [Daniel.local]
avahi      911  0.0  0.0   3016   436 ?        S    16:44   0:00 avahi-daemon: chroot helper
root       933  0.0  0.1  19132  3912 ?        Ssl  16:44   0:00 NetworkManager
root       935  0.0  0.0   4432  2232 ?        S    16:44   0:00 /usr/sbin/modem-manager
root       946  0.0  0.0   1860   540 tty4     Ss+  16:44   0:00 /sbin/getty -8 38400 tty4
root       950  0.0  0.0   1860   548 tty5     Ss+  16:44   0:00 /sbin/getty -8 38400 tty5
root       956  0.0  0.0   4904  2128 ?        S    16:44   0:00 /sbin/wpa_supplicant -u -s
root       959  0.0  0.0   1860   548 tty2     Ss+  16:44   0:00 /sbin/getty -8 38400 tty2
root       960  0.0  0.0   1860   552 tty3     Ss+  16:44   0:00 /sbin/getty -8 38400 tty3
root       962  0.0  0.0   1860   552 tty6     Ss+  16:44   0:00 /sbin/getty -8 38400 tty6
root       964  0.0  0.0   2248  1064 ?        Ss   16:44   0:00 acpid -c /etc/acpi/events -s /var/run
root       976  0.0  0.0   2460   880 ?        Ss   16:44   0:00 cron
daemon     977  0.0  0.0   2320   356 ?        Ss   16:44   0:00 atd
root      1004  0.0  0.0   2300   732 ?        S    16:44   0:00 /sbin/dhclient -d -sf /usr/lib/Networ
root      1027  0.0  0.0      0     0 ?        S    16:44   0:00 [i915]
root      1048  0.0  0.0      0     0 ?        S    16:44   0:00 [l2cap]
root      1080  0.0  0.0      0     0 ?        S<   16:44   0:00 [kslowd000]
root      1081  0.0  0.0      0     0 ?        S<   16:44   0:00 [kslowd001]
root      1088  0.0  0.1  19540  3104 ?        Ssl  16:44   0:00 gdm-binary
root      1094  0.0  0.0      0     0 ?        S    16:44   0:00 [hd-audio0]
root      1099  0.0  0.0      0     0 ?        S<   16:44   0:00 [krfcommd]
root      1125  0.0  0.1  21084  3044 ?        Sl   16:44   0:00 /usr/sbin/console-kit-daemon --no-dae
root      1222  0.0  0.1  21552  3748 ?        Sl   16:44   0:00 /usr/lib/gdm/gdm-simple-slave --displ
root      1229  0.0  0.0   7044  2692 ?        Ss   16:44   0:00 /usr/sbin/cupsd -C /etc/cups/cupsd.co
root      1238  3.6  1.2  67308 38196 tty7     Ss+  16:44   7:32 /usr/bin/X :0 -br -verbose -auth /var
root      1338  0.0  0.0   1860   548 tty1     Ss+  16:44   0:00 /sbin/getty -8 38400 tty1
gdm       1348  0.0  0.0   3460   580 ?        S    16:44   0:00 /usr/bin/dbus-launch --exit-with-sess
root      1366  0.0  0.1  19868  3096 ?        Sl   16:44   0:00 /usr/lib/gdm/gdm-session-worker
root      1373  0.0  0.1   8516  3368 ?        S    16:44   0:00 /usr/lib/upower/upowerd
rtkit     1377  0.0  0.0  22996  1180 ?        SNl  16:44   0:00 /usr/lib/rtkit/rtkit-daemon
root      1381  0.0  0.1   8888  4052 ?        S    16:44   0:00 /usr/lib/policykit-1/polkitd
daniel    1528  0.0  0.0  24984  2332 ?        Sl   16:45   0:00 /usr/bin/gnome-keyring-daemon --daemo
daniel    1547  0.0  0.2  35840  7148 ?        Ssl  16:45   0:00 gnome-session
daniel    1577  0.0  0.0   3352   204 ?        Ss   16:45   0:00 /usr/bin/ssh-agent /usr/bin/dbus-laun
daniel    1580  0.0  0.0   3460   584 ?        S    16:45   0:00 /usr/bin/dbus-launch --exit-with-sess
daniel    1581  0.0  0.0   4744  2172 ?        Ss   16:45   0:01 /bin/dbus-daemon --fork --print-pid 5
daniel    1586  0.0  0.1   9260  4196 ?        S    16:45   0:01 /usr/lib/libgconf2-4/gconfd-2
daniel    1589  0.0  0.3  73376 11432 ?        Sl   16:45   0:01 gnome-power-manager
daniel    1593  0.0  0.3 100212 11256 ?        Ssl  16:45   0:04 /usr/lib/gnome-settings-daemon/gnome-
daniel    1599  0.1  1.3 102968 39416 ?        Sl   16:45   0:16 /usr/lib/notify-osd/notify-osd
daniel    1602  0.0  0.0   7552  2308 ?        S    16:45   0:00 /usr/lib/gvfs/gvfsd
daniel    1609  0.0  0.0  30656  2096 ?        Ssl  16:45   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home
daniel    1614  0.0  0.2  27844  6172 ?        Ss   16:45   0:01 /usr/bin/gnome-screensaver
daniel    1618  1.2  0.1 162144  5716 ?        S<sl 16:45   2:34 /usr/bin/pulseaudio --start --log-tar
daniel    1621  0.0  0.4  73440 12144 ?        Sl   16:45   0:00 /usr/lib/policykit-1-gnome/polkit-gno
daniel    1625  0.0  0.3  71876  9320 ?        Sl   16:45   0:00 bluetooth-applet
daniel    1626  0.1  0.7  85256 22576 ?        Sl   16:45   0:15 gnome-panel
daniel    1628  0.0  0.3  39484  9176 ?        Sl   16:45   0:00 /usr/lib/evolution/2.30/evolution-ala
daniel    1630  0.0  0.1  21708  3316 ?        Sl   16:45   0:00 /usr/lib/pulseaudio/pulse/gconf-helpe
daniel    1635  0.0  0.4 119212 13880 ?        Sl   16:45   0:00 nm-applet --sm-disable
daniel    1637  0.0  0.0   3912   904 ?        S    16:45   0:06 syndaemon -i 0.5 -k
daniel    1643  0.0  0.1  34376  3628 ?        S    16:45   0:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
root      1646  0.0  0.1  16356  3436 ?        Sl   16:45   0:00 /usr/lib/udisks/udisks-daemon
root      1648  0.0  0.0   5616   728 ?        S    16:45   0:03 udisks-daemon: polling /dev/sr0
daniel    1650  0.0  0.1   7804  3032 ?        S    16:45   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :
daniel    1652  0.0  0.0  18012  2228 ?        Sl   16:45   0:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
daniel    1655  0.0  0.0   8192  2200 ?        S    16:45   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-mon
daniel    1657  0.0  0.1  51564  3796 ?        Ssl  16:45   0:00 /usr/lib/bonobo-activation/bonobo-act
daniel    1665  0.1  0.4  77152 14148 ?        Sl   16:45   0:19 /usr/lib/gnome-panel/wnck-applet --oa
daniel    1667  0.0  0.3  74796 11336 ?        Sl   16:45   0:00 /usr/lib/gnome-applets/trashapplet --
daniel    1678  0.0  0.4  84068 13460 ?        Sl   16:45   0:00 /usr/lib/indicator-applet/indicator-a
daniel    1680  0.0  0.2  32044  9000 ?        Sl   16:45   0:04 /usr/lib/gnome-panel/notification-are
daniel    1682  0.0  0.5  83852 15692 ?        Sl   16:45   0:04 /usr/lib/gnome-panel/clock-applet --o
daniel    1683  0.0  0.4  85220 14480 ?        Sl   16:45   0:01 /usr/lib/indicator-applet/indicator-a
daniel    1694  0.0  0.0   7332  2024 ?        S    16:45   0:00 /usr/lib/gvfs/gvfsd-metadata
daniel    1696  0.0  0.1  15732  3624 ?        S    16:45   0:00 /usr/lib/indicator-application/indica
daniel    1699  0.0  0.1  87280  5264 ?        S    16:45   0:00 /usr/lib/indicator-sound/indicator-so
daniel    1701  0.0  0.0   7452  2400 ?        S    16:45   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1
daniel    1705  0.0  0.1  18072  4116 ?        S    16:45   0:00 /usr/lib/indicator-messages/indicator
daniel    1713  0.0  0.1  29032  4868 ?        Sl   16:45   0:00 /usr/lib/indicator-me/indicator-me-se
daniel    1716  0.0  0.1  26932  4904 ?        Sl   16:45   0:00 /usr/lib/indicator-session/indicator-
root      1719  0.0  0.0   3168  1308 ?        Ss   16:45   0:01 /sbin/mount.ntfs /dev/sdb1 /media/Dan
root      1724  0.0  0.0   2892  1036 ?        Ss   16:45   0:00 /sbin/mount.ntfs /dev/sdc1 /media/sup
daniel    1732  0.0  0.2  19124  6688 ?        S    16:45   0:00 /usr/lib/gnome-disk-utility/gdu-notif
daniel    1735  0.0  0.0  22272  2492 ?        Sl   16:45   0:00 /usr/lib/d-conf/dconf-service
daniel    1755  0.0  0.5  32416 15532 ?        S    16:45   0:00 /usr/bin/python /usr/share/system-con
daniel    1778  0.0  0.4  75140 13312 ?        Sl   16:46   0:01 update-notifier
daniel    1787  0.0  0.4  92212 13876 ?        Sl   16:50   0:04 gnome-terminal
daniel    1790  0.0  0.0   2056   704 ?        S    16:50   0:00 gnome-pty-helper
daniel    1791  0.0  0.1   6676  3384 pts/0    Ss   16:50   0:00 bash
daniel    1815  4.1  2.9 419292 89860 ?        Sl   16:51   8:18 /opt/google/chrome/google-chrome
daniel    1818  0.0  0.1  66884  3356 ?        S    16:52   0:03 /opt/google/chrome/google-chrome
daniel    1820  0.0  0.3  91936 11016 ?        S    16:52   0:00 /opt/google/chrome/chrome --type=zygo
daniel    1844  0.0  0.7 125864 21280 ?        Sl   16:52   0:02 /opt/google/chrome/chrome --type=exte
daniel    1847  0.0  0.7 129912 22900 ?        Sl   16:52   0:08 /opt/google/chrome/chrome --type=exte
daniel    1850  0.0  0.6 126560 20860 ?        Sl   16:52   0:06 /opt/google/chrome/chrome --type=exte
daniel    1853  0.1  0.8 131940 26996 ?        Sl   16:52   0:19 /opt/google/chrome/chrome --type=exte
daniel    1856  0.0  0.6 126684 20964 ?        Sl   16:52   0:05 /opt/google/chrome/chrome --type=exte
daniel    1859  0.0  0.7 129240 22816 ?        Sl   16:52   0:02 /opt/google/chrome/chrome --type=exte
daniel    1862  0.0  0.7 126804 22244 ?        Sl   16:52   0:04 /opt/google/chrome/chrome --type=exte
daniel    1865  0.0  0.7 127864 23636 ?        Sl   16:52   0:07 /opt/google/chrome/chrome --type=exte
daniel    1868  0.1  0.7 126888 21452 ?        Sl   16:52   0:14 /opt/google/chrome/chrome --type=exte
daniel    1874  0.1  0.8 133472 26468 ?        Sl   16:52   0:18 /opt/google/chrome/chrome --type=exte
daniel    1877  0.0  0.6 125536 20608 ?        Sl   16:52   0:04 /opt/google/chrome/chrome --type=exte
daniel    1880  0.0  0.6 125128 18828 ?        Sl   16:52   0:01 /opt/google/chrome/chrome --type=exte
daniel    1883  0.0  0.6 125324 18880 ?        Sl   16:52   0:03 /opt/google/chrome/chrome --type=exte
daniel    1886  0.0  0.6 124996 18464 ?        Sl   16:52   0:01 /opt/google/chrome/chrome --type=exte
daniel    1889  0.0  0.6 125772 20356 ?        Sl   16:52   0:04 /opt/google/chrome/chrome --type=exte
daniel    1892  0.0  0.7 126440 22840 ?        Sl   16:52   0:05 /opt/google/chrome/chrome --type=exte
daniel    1895  0.0  0.6 126160 21048 ?        Sl   16:52   0:04 /opt/google/chrome/chrome --type=exte
daniel    1898  0.0  0.6 125716 20128 ?        Sl   16:52   0:04 /opt/google/chrome/chrome --type=exte
daniel    1901  0.0  0.7 125324 21408 ?        Sl   16:52   0:03 /opt/google/chrome/chrome --type=exte
daniel    1904  0.0  0.6 125232 19120 ?        Sl   16:52   0:03 /opt/google/chrome/chrome --type=exte
daniel    1907  0.0  0.6 125192 18824 ?        Sl   16:52   0:03 /opt/google/chrome/chrome --type=exte
daniel    1932  0.0  1.2 148200 38736 ?        SNl  16:52   0:09 /opt/google/chrome/chrome --type=rend
daniel    1935  0.0  1.2 147752 37784 ?        SNl  16:52   0:09 /opt/google/chrome/chrome --type=rend
daniel    1938  0.1  1.6 164276 49684 ?        SNl  16:52   0:12 /opt/google/chrome/chrome --type=rend
daniel    1994  0.0  0.3  75740 10372 ?        Sl   16:52   0:00 /opt/google/chrome/chrome --type=plug
daniel    2162  0.0  0.1  28340  4620 ?        Sl   17:01   0:00 /usr/lib/gvfs/gvfsd-http --spawner :1
root      2175  0.0  0.2  11540  6900 ?        S    17:01   0:00 /usr/bin/python /usr/share/apt-xapian
daniel    2302  0.5  1.4 153320 44012 ?        Sl   17:02   0:57 nautilus
daniel    2325  1.1  1.6 175600 51144 ?        Ssl  17:03   2:15 /home/daniel/.dropbox-dist/dropbox
root      2627  0.0  0.2  13936  8100 ?        S    17:49   0:00 /usr/bin/python /usr/lib/system-servi
root      3462  0.0  0.0   2884  1100 ?        S<   19:13   0:00 udevd --daemon
root      3463  0.0  0.0   2884  1100 ?        S<   19:13   0:00 udevd --daemon
daniel    3589  0.0  0.0   1900   512 ?        Ss   19:20   0:00 /bin/sh -c /usr/bin/compiz-decorator
daniel    3590  0.0  0.3  28436  9856 ?        Sl   19:20   0:00 /usr/bin/gtk-window-decorator
daniel    3594  0.0  0.4 149716 13276 ?        Sl   19:21   0:01 metacity --replace
daniel    3945  0.7  1.5 161568 46784 ?        Sl   19:57   0:06 /opt/google/chrome/chrome --type=rend
daniel    3951  5.8  2.0 178180 63144 ?        Sl   19:58   0:47 /opt/google/chrome/chrome --type=rend
daniel    3969  1.3  1.7 164912 53756 ?        SNl  19:59   0:10 /opt/google/chrome/chrome --type=rend
daniel    3973 16.0  1.6 286220 49528 ?        Sl   19:59   2:00 /opt/google/chrome/chrome --type=plug
root      4033  0.0  0.0   3460   584 pts/0    S    20:07   0:00 dbus-launch --autolaunch=55e746b6ef61
root      4034  0.0  0.0   2760   856 ?        Ss   20:07   0:00 /bin/dbus-daemon --fork --print-pid 5
daniel    4092  0.0  0.0   4592  1096 pts/0    R+   20:12   0:00 ps aux

```

Visual effects are set to "None" and I do have the latest drivers. As you can see from the logs I have plenty memory left, this should not be a problem at all. 
I tried various video players like vlc, gnome player, mplayer and all behaved the same. Sites like youtube lag as well.
I heard there are/were some problems with this specific graphics card but should be fixed by now I think. 

Any help would be really appreciated.

---

