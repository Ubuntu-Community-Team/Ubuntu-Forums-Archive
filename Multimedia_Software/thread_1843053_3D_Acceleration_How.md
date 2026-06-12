---
title: "3D Acceleration? How?"
date: 2011-09-12
forum: Multimedia Software
---

### Post by blenderfox on 2011-09-12
I've just installed PlayOnLinux, and the first thing it warned me about is that I don't have 3D acceleration installed. Not that it bothered me, since I was only installing Spotify, and that doesn't require any fancy graphics stuff.

Now, I want to install it, but I haven't a clue how to. One thing I can find out, though is what graphics card I have.

Sysinfo informs me that I have:

```
		Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
		Subsystem: Hewlett-Packard Company Device 30aa

```

I'm not sure where to go next to setup 3D acceleration. Can anyone give me some advice?

---

### Post by Toz on 2011-09-13
Intel drivers are a "work in progress" with respect to Linux. Let's see what driver you actually have installed. Can you post back the contents of **/var/log/Xorg.0.log** - that should tell us what we need to know. Make sure you enclose the contents of the file in code blocks so that is easier to read.

Also, open a terminal window, execute the following command, and post back the average FPS value that displays in the terminal window:
```
glxgears
```

---

### Post by blenderfox on 2011-09-14
glxgears gives the following output:

```
momoko@yukinom:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
312 frames in 5.0 seconds = 62.323 FPS
313 frames in 5.0 seconds = 62.460 FPS
313 frames in 5.0 seconds = 62.445 FPS
313 frames in 5.0 seconds = 62.456 FPS
313 frames in 5.0 seconds = 62.451 FPS
313 frames in 5.0 seconds = 62.449 FPS
313 frames in 5.0 seconds = 62.453 FPS
313 frames in 5.0 seconds = 62.452 FPS
313 frames in 5.0 seconds = 62.450 FPS
313 frames in 5.0 seconds = 62.448 FPS
... (and it goes on)

```

And here's the Xorg log:

```
[    45.782] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    45.782] X Protocol Version 11, Revision 0
[    45.782] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    45.782] Current Operating System: Linux NC6320 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686
[    45.782] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-11-generic root=UUID=0cfafa6d-ad83-407b-9c11-ce38dcf2a9b3 ro vga=758 quiet splash vt.handoff=7
[    45.782] Build Date: 11 August 2011  03:47:56PM
[    45.782] xorg-server 2:1.10.1-1ubuntu1.2 (For technical support please see http://www.ubuntu.com/support) 
[    45.782] Current version of pixman: 0.20.2
[    45.782] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    45.782] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    45.782] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Sep 13 11:33:02 2011
[    45.801] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    46.076] (==) No Layout section.  Using the first Screen section.
[    46.076] (==) No screen section available. Using defaults.
[    46.076] (**) |-->Screen "Default Screen Section" (0)
[    46.076] (**) |   |-->Monitor "<default monitor>"
[    46.076] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    46.076] (==) Automatically adding devices
[    46.076] (==) Automatically enabling devices
[    46.076] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    46.076] 	Entry deleted from font path.
[    46.076] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    46.076] 	Entry deleted from font path.
[    46.076] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    46.076] 	Entry deleted from font path.
[    46.076] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    46.076] 	Entry deleted from font path.
[    46.076] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    46.077] 	Entry deleted from font path.
[    46.077] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    46.077] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    46.077] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    46.077] (II) Loader magic: 0x81ffde0
[    46.077] (II) Module ABI versions:
[    46.077] 	X.Org ANSI C Emulation: 0.4
[    46.077] 	X.Org Video Driver: 10.0
[    46.077] 	X.Org XInput driver : 12.3
[    46.077] 	X.Org Server Extension : 5.0
[    46.078] (--) PCI:*(0:0:2:0) 8086:27a2:103c:30aa rev 3, Mem @ 0xe8400000/524288, 0xd0000000/268435456, 0xe8480000/262144, I/O @ 0x00006000/8
[    46.078] (--) PCI: (0:0:2:1) 8086:27a6:103c:30aa rev 3, Mem @ 0xe8500000/524288
[    46.078] (II) Open ACPI successful (/var/run/acpid.socket)
[    46.078] (II) LoadModule: "extmod"
[    46.084] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    46.257] (II) Module extmod: vendor="X.Org Foundation"
[    46.257] 	compiled for 1.10.1, module version = 1.0.0
[    46.257] 	Module class: X.Org Server Extension
[    46.257] 	ABI class: X.Org Server Extension, version 5.0
[    46.257] (II) Loading extension MIT-SCREEN-SAVER
[    46.257] (II) Loading extension XFree86-VidModeExtension
[    46.257] (II) Loading extension XFree86-DGA
[    46.257] (II) Loading extension DPMS
[    46.257] (II) Loading extension XVideo
[    46.257] (II) Loading extension XVideo-MotionCompensation
[    46.257] (II) Loading extension X-Resource
[    46.257] (II) LoadModule: "dbe"
[    46.257] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    46.262] (II) Module dbe: vendor="X.Org Foundation"
[    46.262] 	compiled for 1.10.1, module version = 1.0.0
[    46.262] 	Module class: X.Org Server Extension
[    46.262] 	ABI class: X.Org Server Extension, version 5.0
[    46.262] (II) Loading extension DOUBLE-BUFFER
[    46.262] (II) LoadModule: "glx"
[    46.263] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    46.284] (II) Module glx: vendor="X.Org Foundation"
[    46.284] 	compiled for 1.10.1, module version = 1.0.0
[    46.285] 	ABI class: X.Org Server Extension, version 5.0
[    46.285] (==) AIGLX enabled
[    46.285] (II) Loading extension GLX
[    46.285] (II) LoadModule: "record"
[    46.285] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    46.306] (II) Module record: vendor="X.Org Foundation"
[    46.306] 	compiled for 1.10.1, module version = 1.13.0
[    46.306] 	Module class: X.Org Server Extension
[    46.306] 	ABI class: X.Org Server Extension, version 5.0
[    46.306] (II) Loading extension RECORD
[    46.306] (II) LoadModule: "dri"
[    46.307] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    46.321] (II) Module dri: vendor="X.Org Foundation"
[    46.321] 	compiled for 1.10.1, module version = 1.0.0
[    46.321] 	ABI class: X.Org Server Extension, version 5.0
[    46.321] (II) Loading extension XFree86-DRI
[    46.321] (II) LoadModule: "dri2"
[    46.321] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    46.535] (II) Module dri2: vendor="X.Org Foundation"
[    46.535] 	compiled for 1.10.1, module version = 1.2.0
[    46.535] 	ABI class: X.Org Server Extension, version 5.0
[    46.535] (II) Loading extension DRI2
[    46.535] (==) Matched intel as autoconfigured driver 0
[    46.535] (==) Matched vesa as autoconfigured driver 1
[    46.535] (==) Matched fbdev as autoconfigured driver 2
[    46.535] (==) Assigned the driver to the xf86ConfigLayout
[    46.535] (II) LoadModule: "intel"
[    46.535] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    46.583] (II) Module intel: vendor="X.Org Foundation"
[    46.583] 	compiled for 1.10.1, module version = 2.14.0
[    46.584] 	Module class: X.Org Video Driver
[    46.584] 	ABI class: X.Org Video Driver, version 10.0
[    46.584] (II) LoadModule: "vesa"
[    46.584] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    46.969] (II) Module vesa: vendor="X.Org Foundation"
[    46.969] 	compiled for 1.10.0, module version = 2.3.0
[    46.969] 	Module class: X.Org Video Driver
[    46.969] 	ABI class: X.Org Video Driver, version 10.0
[    46.969] (II) LoadModule: "fbdev"
[    46.970] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    46.990] (II) Module fbdev: vendor="X.Org Foundation"
[    46.990] 	compiled for 1.10.0, module version = 0.4.2
[    46.990] 	ABI class: X.Org Video Driver, version 10.0
[    46.990] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[    46.991] (II) VESA: driver for VESA chipsets: vesa
[    46.991] (II) FBDEV: driver for framebuffer: fbdev
[    46.991] (++) using VT number 7

[    46.993] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    46.993] (WW) Falling back to old probe method for vesa
[    46.993] (WW) Falling back to old probe method for fbdev
[    46.993] (II) Loading sub module "fbdevhw"
[    46.993] (II) LoadModule: "fbdevhw"
[    46.994] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    47.010] (II) Module fbdevhw: vendor="X.Org Foundation"
[    47.010] 	compiled for 1.10.1, module version = 0.0.2
[    47.010] 	ABI class: X.Org Video Driver, version 10.0
[    47.010] drmOpenDevice: node name is /dev/dri/card0
[    47.010] drmOpenDevice: open result is 9, (OK)
[    47.010] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    47.010] drmOpenDevice: node name is /dev/dri/card0
[    47.010] drmOpenDevice: open result is 9, (OK)
[    47.010] drmOpenByBusid: drmOpenMinor returns 9
[    47.010] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    47.010] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    47.010] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    47.010] (==) intel(0): RGB weight 888
[    47.010] (==) intel(0): Default visual is TrueColor
[    47.010] (II) intel(0): Integrated Graphics Chipset: Intel(R) 945GM
[    47.010] (--) intel(0): Chipset: "945GM"
[    47.011] (**) intel(0): Relaxed fencing disabled
[    47.011] (**) intel(0): Tiling enabled
[    47.011] (**) intel(0): SwapBuffers wait enabled
[    47.011] (==) intel(0): video overlay key set to 0x101fe
[    47.011] (II) intel(0): Output LVDS1 has no monitor section
[    47.011] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    47.040] (II) intel(0): Output VGA1 has no monitor section
[    47.284] (II) intel(0): Output TV1 has no monitor section
[    47.284] (II) intel(0): EDID for output LVDS1
[    47.284] (II) intel(0): Manufacturer: LGP  Model: 1153  Serial#: 0
[    47.284] (II) intel(0): Year: 1990  Week: 0
[    47.284] (II) intel(0): EDID Version: 1.2
[    47.284] (II) intel(0): Digital Display Input
[    47.284] (II) intel(0): Max Image Size [cm]: horiz.: 30  vert.: 23
[    47.284] (II) intel(0): Gamma: 2.20
[    47.284] (II) intel(0): No DPMS capabilities specified
[    47.284] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    47.284] (II) intel(0): First detailed timing is preferred mode
[    47.284] (II) intel(0): redX: 0.590 redY: 0.343   greenX: 0.319 greenY: 0.539
[    47.284] (II) intel(0): blueX: 0.154 blueY: 0.133   whiteX: 0.312 whiteY: 0.328
[    47.284] (II) intel(0): Manufacturer's mask: 0
[    47.284] (II) intel(0): Supported detailed timing:
[    47.284] (II) intel(0): clock: 108.0 MHz   Image Size:  305 x 228 mm
[    47.284] (II) intel(0): h_active: 1400  h_sync: 1432  h_sync_end 1544 h_blank_end 1688 h_border: 0
[    47.284] (II) intel(0): v_active: 1050  v_sync: 1052  v_sync_end 1056 v_blanking: 1066 v_border: 0
[    47.284] (II) intel(0):  LGPhilipsLCD
[    47.284] (II) intel(0):  LP150E06-A3K2
[    47.284] (II) intel(0): EDID (in hex):
[    47.284] (II) intel(0): 	00ffffffffffff0030f0531100000000
[    47.284] (II) intel(0): 	00000102801e17780a3c809757518a27
[    47.284] (II) intel(0): 	22505400000001010101010101010101
[    47.284] (II) intel(0): 	010101010101302a7820511a10402070
[    47.284] (II) intel(0): 	240031e4100000180000000000000000
[    47.284] (II) intel(0): 	00000000000000000000000000fe004c
[    47.284] (II) intel(0): 	475068696c6970734c43440a000000fe
[    47.284] (II) intel(0): 	004c503135304530362d41334b3200e8
[    47.284] (II) intel(0): EDID vendor "LGP", prod id 4435
[    47.284] (II) intel(0): Printing DDC gathered Modelines:
[    47.284] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[    47.285] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    47.285] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    47.285] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    47.285] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    47.285] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    47.285] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    47.285] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    47.285] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    47.285] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    47.285] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    47.285] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    47.285] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    47.285] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    47.285] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    47.285] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    47.285] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    47.285] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    47.285] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    47.285] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    47.285] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    47.285] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    47.285] (II) intel(0): Printing probed modes for output LVDS1
[    47.285] (II) intel(0): Modeline "1400x1050"x60.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[    47.285] (II) intel(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
[    47.285] (II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    47.285] (II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    47.285] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    47.285] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[    47.285] (II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[    47.285] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    47.285] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    47.285] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    47.285] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    47.316] (II) intel(0): EDID for output VGA1
[    47.556] (II) intel(0): EDID for output TV1
[    47.556] (II) intel(0): Output LVDS1 connected
[    47.556] (II) intel(0): Output VGA1 disconnected
[    47.556] (II) intel(0): Output TV1 disconnected
[    47.556] (II) intel(0): Using exact sizes for initial modes
[    47.556] (II) intel(0): Output LVDS1 using initial mode 1400x1050
[    47.556] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    47.556] (II) intel(0): Kernel page flipping support detected, enabling
[    47.556] (**) intel(0): Display dimensions: (300, 230) mm
[    47.556] (**) intel(0): DPI set to (118, 115)
[    47.556] (II) Loading sub module "fb"
[    47.556] (II) LoadModule: "fb"
[    47.556] (II) Loading /usr/lib/xorg/modules/libfb.so
[    47.557] (II) Module fb: vendor="X.Org Foundation"
[    47.557] 	compiled for 1.10.1, module version = 1.0.0
[    47.557] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    47.557] (II) UnloadModule: "vesa"
[    47.557] (II) Unloading vesa
[    47.557] (II) UnloadModule: "fbdev"
[    47.557] (II) Unloading fbdev
[    47.557] (II) UnloadModule: "fbdevhw"
[    47.557] (II) Unloading fbdevhw
[    47.557] (==) Depth 24 pixmap format is 32 bpp
[    47.557] (==) intel(0): VideoRam: 262144 KB
[    47.557] (II) intel(0): [DRI2] Setup complete
[    47.557] (II) intel(0): [DRI2]   DRI driver: i915
[    47.557] (II) intel(0): Allocated new frame buffer 1408x1050 stride 8192, tiled
[    47.557] (II) UXA(0): Driver registered support for the following operations:
[    47.557] (II)         solid
[    47.557] (II)         copy
[    47.557] (II)         composite (RENDER acceleration)
[    47.557] (II)         put_image
[    47.557] (II)         get_image
[    47.557] (==) intel(0): Backing store disabled
[    47.557] (==) intel(0): Silken mouse enabled
[    47.557] (II) intel(0): Initializing HW Cursor
[    47.588] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    47.590] (==) intel(0): DPMS enabled
[    47.590] (==) intel(0): Intel XvMC decoder disabled
[    47.590] (II) intel(0): Set up textured video
[    47.590] (II) intel(0): Set up overlay video
[    47.590] (II) intel(0): direct rendering: DRI2 Enabled
[    47.590] (==) intel(0): hotplug detection: "enabled"
[    47.590] (--) RandR disabled
[    47.590] (II) Initializing built-in extension Generic Event Extension
[    47.590] (II) Initializing built-in extension SHAPE
[    47.590] (II) Initializing built-in extension MIT-SHM
[    47.590] (II) Initializing built-in extension XInputExtension
[    47.590] (II) Initializing built-in extension XTEST
[    47.590] (II) Initializing built-in extension BIG-REQUESTS
[    47.590] (II) Initializing built-in extension SYNC
[    47.590] (II) Initializing built-in extension XKEYBOARD
[    47.590] (II) Initializing built-in extension XC-MISC
[    47.590] (II) Initializing built-in extension SECURITY
[    47.590] (II) Initializing built-in extension XINERAMA
[    47.590] (II) Initializing built-in extension XFIXES
[    47.590] (II) Initializing built-in extension RENDER
[    47.590] (II) Initializing built-in extension RANDR
[    47.590] (II) Initializing built-in extension COMPOSITE
[    47.590] (II) Initializing built-in extension DAMAGE
[    47.590] (II) Initializing built-in extension GESTURE
[    47.603] (II) AIGLX: Trying DRI driver /usr/lib/dri/i915_dri.so
[    47.621] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    47.621] (II) AIGLX: enabled GLX_INTEL_swap_event
[    47.621] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    47.621] (II) AIGLX: enabled GLX_SGI_make_current_read
[    47.621] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    47.621] (II) AIGLX: Loaded and initialized i915
[    47.621] (II) GLX: Initialized DRI2 GL provider for screen 0
[    47.622] (II) intel(0): Setting screen physical size to 370 x 277
[    47.972] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    48.000] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    48.000] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    48.001] (II) LoadModule: "evdev"
[    48.001] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    48.001] (II) Module evdev: vendor="X.Org Foundation"
[    48.001] 	compiled for 1.10.0.902, module version = 2.6.0
[    48.001] 	Module class: X.Org XInput Driver
[    48.001] 	ABI class: X.Org XInput driver, version 12.3
[    48.001] (II) Using input driver 'evdev' for 'Power Button'
[    48.001] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    48.001] (**) Power Button: always reports core events
[    48.002] (**) Power Button: Device: "/dev/input/event2"
[    48.002] (--) Power Button: Found keys
[    48.002] (II) Power Button: Configuring as keyboard
[    48.002] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    48.002] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    48.002] (**) Option "xkb_rules" "evdev"
[    48.002] (**) Option "xkb_model" "pc105"
[    48.002] (**) Option "xkb_layout" "gb"
[    48.005] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[    48.177] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    48.177] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    48.177] (II) Using input driver 'evdev' for 'Video Bus'
[    48.177] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    48.177] (**) Video Bus: always reports core events
[    48.177] (**) Video Bus: Device: "/dev/input/event4"
[    48.196] (--) Video Bus: Found keys
[    48.196] (II) Video Bus: Configuring as keyboard
[    48.196] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input4/event4"
[    48.196] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    48.196] (**) Option "xkb_rules" "evdev"
[    48.196] (**) Option "xkb_model" "pc105"
[    48.196] (**) Option "xkb_layout" "gb"
[    48.202] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    48.202] (II) No input driver/identifier specified (ignoring)
[    48.202] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[    48.202] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    48.202] (II) Using input driver 'evdev' for 'Sleep Button'
[    48.202] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    48.202] (**) Sleep Button: always reports core events
[    48.202] (**) Sleep Button: Device: "/dev/input/event0"
[    48.208] (--) Sleep Button: Found keys
[    48.208] (II) Sleep Button: Configuring as keyboard
[    48.208] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0/event0"
[    48.208] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    48.208] (**) Option "xkb_rules" "evdev"
[    48.208] (**) Option "xkb_model" "pc105"
[    48.208] (**) Option "xkb_layout" "gb"
[    48.218] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    48.218] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    48.218] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    48.218] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    48.218] (**) AT Translated Set 2 keyboard: always reports core events
[    48.218] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    48.224] (--) AT Translated Set 2 keyboard: Found keys
[    48.224] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    48.224] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    48.224] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    48.224] (**) Option "xkb_rules" "evdev"
[    48.224] (**) Option "xkb_model" "pc105"
[    48.224] (**) Option "xkb_layout" "gb"
[    48.225] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[    48.225] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    48.225] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    48.225] (II) LoadModule: "synaptics"
[    48.225] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    48.225] (II) Module synaptics: vendor="X.Org Foundation"
[    48.225] 	compiled for 1.10.1, module version = 1.3.99
[    48.225] 	Module class: X.Org XInput Driver
[    48.225] 	ABI class: X.Org XInput driver, version 12.3
[    48.225] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    48.225] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    48.226] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    48.226] (**) Option "Device" "/dev/input/event6"
[    48.236] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    48.236] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    48.236] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    48.236] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    48.236] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    48.268] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    48.268] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    48.272] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input6/event6"
[    48.272] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    48.272] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    48.272] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    48.272] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[    48.272] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    48.272] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    48.272] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    48.272] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    48.276] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[    48.276] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    48.276] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    48.276] (II) No input driver/identifier specified (ignoring)
[    48.283] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event5)
[    48.283] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    48.283] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[    48.283] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    48.283] (**) HP WMI hotkeys: always reports core events
[    48.283] (**) HP WMI hotkeys: Device: "/dev/input/event5"
[    48.284] (--) HP WMI hotkeys: Found keys
[    48.284] (II) HP WMI hotkeys: Configuring as keyboard
[    48.284] (**) Option "config_info" "udev:/sys/devices/virtual/input/input5/event5"
[    48.284] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD)
[    48.284] (**) Option "xkb_rules" "evdev"
[    48.284] (**) Option "xkb_model" "pc105"
[    48.284] (**) Option "xkb_layout" "gb"
[    50.770] (II) intel(0): EDID vendor "LGP", prod id 4435
[    50.770] (II) intel(0): Printing DDC gathered Modelines:
[    50.770] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[    51.046] (II) intel(0): EDID vendor "LGP", prod id 4435
[    51.046] (II) intel(0): Printing DDC gathered Modelines:
[    51.046] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[    51.358] (II) intel(0): EDID vendor "LGP", prod id 4435
[    51.358] (II) intel(0): Printing DDC gathered Modelines:
[    51.358] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[    51.621] (II) intel(0): EDID vendor "LGP", prod id 4435
[    51.621] (II) intel(0): Printing DDC gathered Modelines:
[    51.621] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[    74.664] (II) intel(0): EDID vendor "LGP", prod id 4435
[    74.664] (II) intel(0): Printing DDC gathered Modelines:
[    74.664] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[    74.967] (II) intel(0): EDID vendor "LGP", prod id 4435
[    74.967] (II) intel(0): Printing DDC gathered Modelines:
[    74.967] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[    75.249] (II) intel(0): EDID vendor "LGP", prod id 4435
[    75.250] (II) intel(0): Printing DDC gathered Modelines:
[    75.250] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[    78.671] (II) intel(0): EDID vendor "LGP", prod id 4435
[    78.671] (II) intel(0): Printing DDC gathered Modelines:
[    78.671] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[    89.164] (II) intel(0): EDID vendor "LGP", prod id 4435
[    94.412] (II) intel(0): Printing DDC gathered Modelines:
[    94.412] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[   206.034] (II) XKB: reuse xkmfile /var/lib/xkb/server-58118CAC4FF2A02B3A940F3A7A58FD5C451401BC.xkm
[  2223.214] (II) intel(0): EDID vendor "LGP", prod id 4435
[  2223.514] (II) intel(0): Printing DDC gathered Modelines:
[  2223.514] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[  2809.358] (II) intel(0): EDID vendor "LGP", prod id 4435
[  2809.590] (II) intel(0): Printing DDC gathered Modelines:
[  2809.590] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[  4488.919] (II) intel(0): EDID vendor "LGP", prod id 4435
[  4489.105] (II) intel(0): Printing DDC gathered Modelines:
[  4489.105] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[  5071.343] (II) XKB: reuse xkmfile /var/lib/xkb/server-58118CAC4FF2A02B3A940F3A7A58FD5C451401BC.xkm
[  5777.166] (II) intel(0): EDID vendor "LGP", prod id 4435
[  5777.451] (II) intel(0): Printing DDC gathered Modelines:
[  5777.451] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[  6087.431] (II) intel(0): EDID vendor "LGP", prod id 4435
[  6087.575] (II) intel(0): Printing DDC gathered Modelines:
[  6087.575] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[  6401.616] (II) intel(0): EDID vendor "LGP", prod id 4435
[  6401.722] (II) intel(0): Printing DDC gathered Modelines:
[  6401.722] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[  6709.157] (II) intel(0): EDID vendor "LGP", prod id 4435
[  6709.217] (II) intel(0): Printing DDC gathered Modelines:
[  6709.217] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[  7203.657] (II) intel(0): EDID vendor "LGP", prod id 4435
[  7203.836] (II) intel(0): Printing DDC gathered Modelines:
[  7203.836] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[  7735.919] (II) intel(0): EDID vendor "LGP", prod id 4435
[  7736.005] (II) intel(0): Printing DDC gathered Modelines:
[  7736.005] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[  7997.049] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
[  7997.204] (II) No input driver/identifier specified (ignoring)
[  7997.205] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event7)
[  7997.205] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[  7997.245] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[  7997.284] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  7998.508] (**) Logitech USB Receiver: always reports core events
[  7998.508] (**) Logitech USB Receiver: Device: "/dev/input/event7"
[  7998.690] (--) Logitech USB Receiver: Found keys
[  7998.690] (II) Logitech USB Receiver: Configuring as keyboard
[  7998.788] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input7/event7"
[  7998.788] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[  7998.788] (**) Option "xkb_rules" "evdev"
[  7998.788] (**) Option "xkb_model" "pc105"
[  7998.788] (**) Option "xkb_layout" "gb"
[  7998.848] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event8)
[  7998.848] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[  7998.848] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[  7998.848] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[  7998.848] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  7998.848] (**) Logitech USB Receiver: always reports core events
[  7998.848] (**) Logitech USB Receiver: Device: "/dev/input/event8"
[  7998.868] (--) Logitech USB Receiver: Found 20 mouse buttons
[  7998.868] (--) Logitech USB Receiver: Found scroll wheel(s)
[  7998.868] (--) Logitech USB Receiver: Found relative axes
[  7998.868] (--) Logitech USB Receiver: Found x and y relative axes
[  7998.868] (--) Logitech USB Receiver: Found keys
[  7998.868] (II) Logitech USB Receiver: Configuring as mouse
[  7998.868] (II) Logitech USB Receiver: Configuring as keyboard
[  7998.868] (II) Logitech USB Receiver: Adding scrollwheel support
[  7998.868] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[  7998.868] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  7998.868] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.1/input/input8/event8"
[  7998.868] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[  7998.868] (**) Option "xkb_rules" "evdev"
[  7998.868] (**) Option "xkb_model" "pc105"
[  7998.868] (**) Option "xkb_layout" "gb"
[  7999.056] (II) Logitech USB Receiver: initialized for relative axes.
[  7999.056] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[  7999.056] (**) Logitech USB Receiver: (accel) acceleration profile 0
[  7999.056] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[  7999.057] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[  8156.314] (II) config/udev: removing device Logitech USB Receiver
[  8156.967] (II) Logitech USB Receiver: Close
[  8157.663] (II) UnloadModule: "evdev"
[  8157.663] (II) Unloading evdev
[  8157.684] (II) config/udev: removing device Logitech USB Receiver
[  8157.685] (II) Logitech USB Receiver: Close
[  8157.685] (II) UnloadModule: "evdev"
[  8157.685] (II) Unloading evdev
[  8212.958] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
[  8212.971] (II) No input driver/identifier specified (ignoring)
[  8212.972] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event7)
[  8212.979] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[  8212.979] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[  8212.993] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  8213.103] (**) Logitech USB Receiver: always reports core events
[  8213.103] (**) Logitech USB Receiver: Device: "/dev/input/event7"
[  8213.128] (--) Logitech USB Receiver: Found keys
[  8213.128] (II) Logitech USB Receiver: Configuring as keyboard
[  8213.152] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input9/event7"
[  8213.152] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[  8213.152] (**) Option "xkb_rules" "evdev"
[  8213.152] (**) Option "xkb_model" "pc105"
[  8213.152] (**) Option "xkb_layout" "gb"
[  8213.153] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event8)
[  8213.153] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[  8213.153] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[  8213.153] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[  8213.153] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  8213.153] (**) Logitech USB Receiver: always reports core events
[  8213.153] (**) Logitech USB Receiver: Device: "/dev/input/event8"
[  8213.168] (--) Logitech USB Receiver: Found 20 mouse buttons
[  8213.168] (--) Logitech USB Receiver: Found scroll wheel(s)
[  8213.168] (--) Logitech USB Receiver: Found relative axes
[  8213.168] (--) Logitech USB Receiver: Found x and y relative axes
[  8213.168] (--) Logitech USB Receiver: Found keys
[  8213.168] (II) Logitech USB Receiver: Configuring as mouse
[  8213.168] (II) Logitech USB Receiver: Configuring as keyboard
[  8213.168] (II) Logitech USB Receiver: Adding scrollwheel support
[  8213.168] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[  8213.168] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  8213.168] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.1/input/input10/event8"
[  8213.168] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[  8213.168] (**) Option "xkb_rules" "evdev"
[  8213.168] (**) Option "xkb_model" "pc105"
[  8213.168] (**) Option "xkb_layout" "gb"
[  8213.168] (II) Logitech USB Receiver: initialized for relative axes.
[  8213.175] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[  8213.175] (**) Logitech USB Receiver: (accel) acceleration profile 0
[  8213.176] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[  8213.176] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[  8464.480] (II) config/udev: removing device Logitech USB Receiver
[  8464.760] (II) Logitech USB Receiver: Close
[  8464.873] (II) UnloadModule: "evdev"
[  8464.873] (II) Unloading evdev
[  8464.875] (II) config/udev: removing device Logitech USB Receiver
[  8464.878] (II) Logitech USB Receiver: Close
[  8464.882] (II) UnloadModule: "evdev"
[  8464.882] (II) Unloading evdev
[  9801.273] (II) intel(0): EDID vendor "LGP", prod id 4435
[  9801.359] (II) intel(0): Printing DDC gathered Modelines:
[  9801.359] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[ 11134.356] (II) intel(0): EDID vendor "LGP", prod id 4435
[ 11134.460] (II) intel(0): Printing DDC gathered Modelines:
[ 11134.461] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[ 11889.116] (II) intel(0): EDID vendor "LGP", prod id 4435
[ 11889.483] (II) intel(0): Printing DDC gathered Modelines:
[ 11889.628] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[ 12736.738] (II) intel(0): EDID vendor "LGP", prod id 4435
[ 12736.974] (II) intel(0): Printing DDC gathered Modelines:
[ 12736.975] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[ 13080.817] (II) intel(0): EDID vendor "LGP", prod id 4435
[ 13080.987] (II) intel(0): Printing DDC gathered Modelines:
[ 13080.987] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[ 13560.317] (II) intel(0): EDID vendor "LGP", prod id 4435
[ 13560.484] (II) intel(0): Printing DDC gathered Modelines:
[ 13560.484] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[ 13897.237] (II) intel(0): EDID vendor "LGP", prod id 4435
[ 13897.385] (II) intel(0): Printing DDC gathered Modelines:
[ 13897.385] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[ 14419.753] (II) intel(0): EDID vendor "LGP", prod id 4435
[ 14419.842] (II) intel(0): Printing DDC gathered Modelines:
[ 14419.842] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[ 15245.134] (II) intel(0): EDID vendor "LGP", prod id 4435
[ 15245.228] (II) intel(0): Printing DDC gathered Modelines:
[ 15245.228] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[ 15735.767] (II) intel(0): EDID vendor "LGP", prod id 4435
[ 15735.880] (II) intel(0): Printing DDC gathered Modelines:
[ 15735.880] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[ 16046.876] (II) intel(0): EDID vendor "LGP", prod id 4435
[ 16047.033] (II) intel(0): Printing DDC gathered Modelines:
[ 16047.033] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[ 16355.423] (II) intel(0): EDID vendor "LGP", prod id 4435
[ 16355.585] (II) intel(0): Printing DDC gathered Modelines:
[ 16355.585] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[ 16663.435] (II) intel(0): EDID vendor "LGP", prod id 4435
[ 16663.593] (II) intel(0): Printing DDC gathered Modelines:
[ 16663.593] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[ 17237.975] (II) XKB: reuse xkmfile /var/lib/xkb/server-58118CAC4FF2A02B3A940F3A7A58FD5C451401BC.xkm
[ 17578.611] (II) intel(0): EDID vendor "LGP", prod id 4435
[ 17578.859] (II) intel(0): Printing DDC gathered Modelines:
[ 17578.859] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[ 17726.078] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
[ 17726.268] (II) No input driver/identifier specified (ignoring)
[ 17726.405] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event8)
[ 17726.405] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[ 17726.405] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[ 17726.475] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[ 17726.503] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 17727.283] (**) Logitech USB Receiver: always reports core events
[ 17727.283] (**) Logitech USB Receiver: Device: "/dev/input/event8"
[ 17727.353] (--) Logitech USB Receiver: Found 20 mouse buttons
[ 17727.353] (--) Logitech USB Receiver: Found scroll wheel(s)
[ 17727.353] (--) Logitech USB Receiver: Found relative axes
[ 17727.353] (--) Logitech USB Receiver: Found x and y relative axes
[ 17727.353] (--) Logitech USB Receiver: Found keys
[ 17727.353] (II) Logitech USB Receiver: Configuring as mouse
[ 17727.353] (II) Logitech USB Receiver: Configuring as keyboard
[ 17727.353] (II) Logitech USB Receiver: Adding scrollwheel support
[ 17727.353] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[ 17727.353] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 17727.419] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.1/input/input12/event8"
[ 17727.419] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[ 17727.419] (**) Option "xkb_rules" "evdev"
[ 17727.419] (**) Option "xkb_model" "pc105"
[ 17727.419] (**) Option "xkb_layout" "gb"
[ 17727.520] (II) Logitech USB Receiver: initialized for relative axes.
[ 17727.521] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[ 17727.521] (**) Logitech USB Receiver: (accel) acceleration profile 0
[ 17727.521] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[ 17727.521] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[ 17727.522] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event7)
[ 17727.522] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[ 17727.523] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[ 17727.523] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 17727.523] (**) Logitech USB Receiver: always reports core events
[ 17727.523] (**) Logitech USB Receiver: Device: "/dev/input/event7"
[ 17727.540] (--) Logitech USB Receiver: Found keys
[ 17727.540] (II) Logitech USB Receiver: Configuring as keyboard
[ 17727.540] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input11/event7"
[ 17727.540] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[ 17727.540] (**) Option "xkb_rules" "evdev"
[ 17727.540] (**) Option "xkb_model" "pc105"
[ 17727.540] (**) Option "xkb_layout" "gb"
[ 22981.092] (II) config/udev: removing device Logitech USB Receiver
[ 22981.447] (II) Logitech USB Receiver: Close
[ 22982.717] (II) UnloadModule: "evdev"
[ 22982.717] (II) Unloading evdev
[ 22983.467] (II) config/udev: removing device Logitech USB Receiver
[ 22983.508] (II) Logitech USB Receiver: Close
[ 22983.708] (II) UnloadModule: "evdev"
[ 22983.708] (II) Unloading evdev
[ 23405.582] (II) XKB: reuse xkmfile /var/lib/xkb/server-58118CAC4FF2A02B3A940F3A7A58FD5C451401BC.xkm
[ 24119.486] (II) intel(0): EDID vendor "LGP", prod id 4435
[ 24119.646] (II) intel(0): Printing DDC gathered Modelines:
[ 24119.646] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[ 24198.583] (II) intel(0): EDID vendor "LGP", prod id 4435
[ 24198.584] (II) intel(0): Printing DDC gathered Modelines:
[ 24198.584] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[ 24320.811] (II) intel(0): EDID vendor "LGP", prod id 4435
[ 24320.836] (II) intel(0): Printing DDC gathered Modelines:
[ 24320.836] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[ 24415.746] (II) intel(0): EDID vendor "LGP", prod id 4435
[ 24415.794] (II) intel(0): Printing DDC gathered Modelines:
[ 24415.794] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[ 24854.512] (II) intel(0): EDID vendor "LGP", prod id 4435
[ 24854.970] (II) intel(0): Printing DDC gathered Modelines:
[ 24854.970] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[ 25616.952] (II) intel(0): EDID vendor "LGP", prod id 4435
[ 25617.037] (II) intel(0): Printing DDC gathered Modelines:
[ 25617.037] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[ 27608.236] (II) intel(0): EDID vendor "LGP", prod id 4435
[ 27608.394] (II) intel(0): Printing DDC gathered Modelines:
[ 27608.394] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[ 30263.183] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
[ 30263.528] (II) No input driver/identifier specified (ignoring)
[ 30263.652] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event7)
[ 30263.652] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[ 30263.724] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[ 30263.763] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 30264.375] (**) Logitech USB Receiver: always reports core events
[ 30264.375] (**) Logitech USB Receiver: Device: "/dev/input/event7"
[ 30264.614] (--) Logitech USB Receiver: Found keys
[ 30264.614] (II) Logitech USB Receiver: Configuring as keyboard
[ 30264.710] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input13/event7"
[ 30264.710] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[ 30264.710] (**) Option "xkb_rules" "evdev"
[ 30264.710] (**) Option "xkb_model" "pc105"
[ 30264.710] (**) Option "xkb_layout" "gb"
[ 30264.790] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event8)
[ 30264.790] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[ 30264.790] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[ 30264.790] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[ 30264.790] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 30264.790] (**) Logitech USB Receiver: always reports core events
[ 30264.790] (**) Logitech USB Receiver: Device: "/dev/input/event8"
[ 30264.804] (--) Logitech USB Receiver: Found 20 mouse buttons
[ 30264.804] (--) Logitech USB Receiver: Found scroll wheel(s)
[ 30264.804] (--) Logitech USB Receiver: Found relative axes
[ 30264.804] (--) Logitech USB Receiver: Found x and y relative axes
[ 30264.804] (--) Logitech USB Receiver: Found keys
[ 30264.804] (II) Logitech USB Receiver: Configuring as mouse
[ 30264.804] (II) Logitech USB Receiver: Configuring as keyboard
[ 30264.804] (II) Logitech USB Receiver: Adding scrollwheel support
[ 30264.804] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[ 30264.804] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 30264.804] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.1/input/input14/event8"
[ 30264.804] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[ 30264.804] (**) Option "xkb_rules" "evdev"
[ 30264.804] (**) Option "xkb_model" "pc105"
[ 30264.804] (**) Option "xkb_layout" "gb"
[ 30264.804] (II) Logitech USB Receiver: initialized for relative axes.
[ 30264.804] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[ 30265.069] (**) Logitech USB Receiver: (accel) acceleration profile 0
[ 30265.069] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[ 30265.069] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[ 36942.094] (II) config/udev: removing device Logitech USB Receiver
[ 36942.240] (II) Logitech USB Receiver: Close
[ 36942.460] (II) UnloadModule: "evdev"
[ 36942.460] (II) Unloading evdev
[ 36942.636] (II) config/udev: removing device Logitech USB Receiver
[ 36942.637] (II) Logitech USB Receiver: Close
[ 36942.906] (II) UnloadModule: "evdev"
[ 36942.906] (II) Unloading evdev
[ 37219.532] (II) XKB: reuse xkmfile /var/lib/xkb/server-58118CAC4FF2A02B3A940F3A7A58FD5C451401BC.xkm
[ 37531.543] (II) intel(0): EDID vendor "LGP", prod id 4435
[ 37531.707] (II) intel(0): Printing DDC gathered Modelines:
[ 37531.708] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[ 39347.412] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
[ 39347.690] (II) No input driver/identifier specified (ignoring)
[ 39347.711] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event8)
[ 39347.711] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[ 39347.711] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[ 39347.742] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[ 39347.742] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 39348.094] (**) Logitech USB Receiver: always reports core events
[ 39348.094] (**) Logitech USB Receiver: Device: "/dev/input/event8"
[ 39348.164] (--) Logitech USB Receiver: Found 20 mouse buttons
[ 39348.164] (--) Logitech USB Receiver: Found scroll wheel(s)
[ 39348.164] (--) Logitech USB Receiver: Found relative axes
[ 39348.164] (--) Logitech USB Receiver: Found x and y relative axes
[ 39348.164] (--) Logitech USB Receiver: Found keys
[ 39348.164] (II) Logitech USB Receiver: Configuring as mouse
[ 39348.164] (II) Logitech USB Receiver: Configuring as keyboard
[ 39348.164] (II) Logitech USB Receiver: Adding scrollwheel support
[ 39348.164] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[ 39348.164] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 39348.190] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.1/input/input16/event8"
[ 39348.190] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[ 39348.190] (**) Option "xkb_rules" "evdev"
[ 39348.190] (**) Option "xkb_model" "pc105"
[ 39348.190] (**) Option "xkb_layout" "gb"
[ 39348.239] (II) Logitech USB Receiver: initialized for relative axes.
[ 39348.239] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[ 39348.239] (**) Logitech USB Receiver: (accel) acceleration profile 0
[ 39348.239] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[ 39348.239] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[ 39348.241] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event7)
[ 39348.241] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[ 39348.241] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[ 39348.241] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 39348.241] (**) Logitech USB Receiver: always reports core events
[ 39348.241] (**) Logitech USB Receiver: Device: "/dev/input/event7"
[ 39348.256] (--) Logitech USB Receiver: Found keys
[ 39348.315] (II) Logitech USB Receiver: Configuring as keyboard
[ 39348.315] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input15/event7"
[ 39348.315] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[ 39348.315] (**) Option "xkb_rules" "evdev"
[ 39348.315] (**) Option "xkb_model" "pc105"
[ 39348.315] (**) Option "xkb_layout" "gb"
[ 42875.648] (II) config/udev: removing device Logitech USB Receiver
[ 42876.103] (II) Logitech USB Receiver: Close
[ 42877.438] (II) UnloadModule: "evdev"
[ 42877.438] (II) Unloading evdev
[ 42878.398] (II) config/udev: removing device Logitech USB Receiver
[ 42878.435] (II) Logitech USB Receiver: Close
[ 42878.851] (II) UnloadModule: "evdev"
[ 42878.851] (II) Unloading evdev
[ 42969.647] (II) AIGLX: Suspending AIGLX clients for VT switch
[ 42975.720] (II) Open ACPI successful (/var/run/acpid.socket)
[ 42976.723] (II) AIGLX: Resuming AIGLX clients after VT switch
[ 42978.652] (II) intel(0): EDID vendor "LGP", prod id 4435
[ 42978.660] (II) intel(0): Printing DDC gathered Modelines:
[ 42978.660] (II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1432 1544 1688  1050 1052 1056 1066 -hsync -vsync (64.0 kHz)
[ 42982.921] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[ 42982.921] (--) SynPS/2 Synaptics TouchPad: touchpad found
[ 43050.990] (II) XKB: reuse xkmfile /var/lib/xkb/server-58118CAC4FF2A02B3A940F3A7A58FD5C451401BC.xkm
```


I can see this:

```
[    46.990] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge

```

---

### Post by Toz on 2011-09-14
> **momokoyukino said:**
> glxgears gives the following output:

```
momoko@yukinom:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
312 frames in 5.0 seconds = 62.323 FPS
313 frames in 5.0 seconds = 62.460 FPS
313 frames in 5.0 seconds = 62.445 FPS
313 frames in 5.0 seconds = 62.456 FPS
313 frames in 5.0 seconds = 62.451 FPS
313 frames in 5.0 seconds = 62.449 FPS
313 frames in 5.0 seconds = 62.453 FPS
313 frames in 5.0 seconds = 62.452 FPS
313 frames in 5.0 seconds = 62.450 FPS
313 frames in 5.0 seconds = 62.448 FPS
... (and it goes on)

```
ugh. My 3-year old laptop with an ATi HD2600 using proprietary drivers gives me around 3000FPS.

> And here's the Xorg log:

Yep, you're using the intel drivers.

EDIT: Just noticed the date on this link - it may not be helpful, but I'll leave the link here anyways. The second link is more recent.
Have a look at this link: [http://www.nixternal.com/intel-945-video-hint/]("http://www.nixternal.com/intel-945-video-hint/"). You might want to try those suggestions to see if you can get a performance boost.

And if that doesn't work, have a look at this link as well: [http://www.linuxquestions.org/questions/linux-hardware-18/increase-fps-in-intel-945gm-gms-943-940gml-express-integrated-814234/]("http://www.linuxquestions.org/questions/linux-hardware-18/increase-fps-in-intel-945gm-gms-943-940gml-express-integrated-814234/")

Please post back your findings - there are a number of posts here about poor intel driver performance. Thanks.

---

### Post by Toz on 2011-09-14
Now this is interesting: [http://forums.freebsd.org/showthread.php?t=24492]("http://forums.freebsd.org/showthread.php?t=24492"). Its from a freebsd forum that talks about up-clocking the intel GMA945/950 chip (apparently its underclocked). There is a linux script listed at the top:

```
#!/bin/sh

case "$1" in
    250) val=31 ;;
    400) val=33 ;;
    200) val=34 ;;
    *)
        echo "Illegal argument! Possible values are: 200, 250, 400." >&2
        exit 1
    ;;
esac

setpci -s 02.0 f0.b=00,60
setpci -s 02.0 f0.b=$val,05
```

If its correct in its assumptions, you should be able to:
```
sudo setpci -s 02.0 f0.b=00,60
sudo setpci -s 02.0 f0.b=<value>,05
```
.....where <value> is one of:
- 31 (for 250MHz)
- 33 (for 400MHz)
- 34 (for 200MHz)

---

### Post by blenderfox on 2011-09-15
Well, the script made no difference to the FPS, no matter which of the three options I choose.

The hint page tells me to edit xorg.conf. I don't have one (probably a result of that article being old.) The only mention I can find on my drive is in:

```
./usr/share/doc/xserver-xorg-video-nouveau/examples/xorg.conf
```

I did, however, find a directory:

```
./usr/share/X11/xorg.conf.d
```

Which contains these files:

```

./usr/share/X11/xorg.conf.d/50-synaptics.conf
./usr/share/X11/xorg.conf.d/51-synaptics-quirks.conf
./usr/share/X11/xorg.conf.d/50-wacom.conf
./usr/share/X11/xorg.conf.d/10-evdev.conf
./usr/share/X11/xorg.conf.d/11-evdev-quirks.conf
./usr/share/X11/xorg.conf.d/50-vmmouse.conf

```

So I figured I should add another one, so I put in 00-intel.conf, with their suggestions, and rebooted. Didn't work, and my display didn't come up with the login screen, so I had to grub into the recovery console, delete that new file I created and reboot.

One thing I did notice. In the xorg.conf change the site is suggesting, it's addressing PCI:0:2:0, and the script is addressing 02.0. Just a thought, are they they the same? Also, what if my card is not in 0:2:0? I did a

```
lspci
```

And I got this extract. There's actually three mentions of the chipset apparently.
```
....
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

....

```

---

### Post by Toz on 2011-09-15
Try the original script with the pci values as:

- 00:02.0 and
- 00:02.1

See if that makes a difference.

---------

As for the xorg.conf part, try it again with the contents of **00-intel.conf** like this:
```
Section "Device"
   Option      "AccelMethod"   "exa"
   Option      "MigrationHeuristic" "greedy"
EndSection
```
...and boot normally and with the **i915.modeset=1** kernel parameter. If you can, post back the contents of "/var/log/Xorg.0.log" after each attempt.

If you can get the system to boot properly with these xorg additions but with no performance boost, the other post I linked suggested using the option **Option      "AccelMethod"   "xaa"** instead of **Option      "AccelMethod"   "exa"**

----------

You also have xorg-edgers ([https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)) available to you. Its the latest xserver build with the latest drivers. However, it hasn't made a difference for the last few people with intel cards that I suggested it to. 

-----------

I'm sorry but I don't have an intel card available to test this in advance.

---

### Post by blenderfox on 2011-09-15
Running with the values as 02.1... tiny improvement (59-60 fps before, 60-62 fps after)
 
Adding the section and reboot, no login screen. Reboot with kernel param from grub screen (on the line starting with "linux", no login screen. Looks like neither worked.
 
I'm not sure, but I think it's with the conf file. Even when I removed everything except "Section" and "EndSection" (i.e. a two line file), it still wouldn't boot. Removing the file completely let's it boot.... /Puzzled

---

### Post by Toz on 2011-09-15
It's possible that your card just doesn't work with those xorg values. 

Try creating an **/etc/X11/xorg.conf** file with the following content:
```
Section "Device"
	Identifier  "Device0"
	Driver      "intel"
        Option      "AccelMethod"   "exa"
        Option      "MigrationHeuristic" "greedy"
EndSection
```
This will override the automatically-detected settings.

Otherwise, it might be that this is the best its going to get. You might still want to try the xorg-edgers version of X.

---

### Post by realzippy on 2011-09-15
> **momokoyukino said:**
> ...I don't have 3D acceleration installed. .

..according to your log file you have 3D acceleration:

```
[    46.262] (II) LoadModule: "glx"
[    46.263] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    46.284] (II) Module glx: vendor="X.Org Foundation"
...............
[    46.306] (II) LoadModule: "dri"
[    46.307] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
...............
[    46.535] (II) Loading extension DRI2
```

Note that when enabling EXA dri2 won't work.

Can you show output from:
```
glxinfo | grep render
```

---

### Post by blenderfox on 2011-09-15
> **realzippy said:**
> Can you show output from:
```
glxinfo | grep render
```

```
momoko@yukinom:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 945GM GEM 20100330 DEVELOPMENT x86/MMX/SSE2

```

That doesn't mean anything to me :P

---

### Post by realzippy on 2011-09-15
This means that 3D/hardware rendering is working.

---

### Post by blenderfox on 2011-09-15
But does it explain why I'm getting such as low framerate? :P

---

### Post by realzippy on 2011-09-15
[I]The framerate should be
approximately the same as the monitor refresh rate....[/I]
which is 60 Hz I guess.
glxgears doesn't tell anything about your framerate when you sync to vblanc...

Open ccsm and disable Sync to VBlank ..

---

### Post by blenderfox on 2011-09-15
> **Toz said:**
> It's possible that your card just doesn't work with those xorg values. 
 
Try creating an **/etc/X11/xorg.conf** file with the following content:
```
Section "Device"
    Identifier  "Device0"
    Driver      "intel"
        Option      "AccelMethod"   "exa"
        Option      "MigrationHeuristic" "greedy"
EndSection
```
This will override the automatically-detected settings.
 
Otherwise, it might be that this is the best its going to get. You might still want to try the xorg-edgers version of X.
 
Creating the xorg.conf let my PC boot, but no improvement. I'll take a look at the edgers.

---

### Post by realzippy on 2011-09-15
...why do you ignore that glxgears is no benchmark since it runs
synchronised to V refresh ?
Again,your hardware acceleration **is** running...
```
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 945GM GEM 20100330 DEVELOPMENT x86/MMX/SSE2
```
Install assaultcube or quake3 demo if you want to get a real 3D benchmark.
Caution with xorg edgers,when I added their ppa just for fun a few days ago,
I wasn't able to boot and had to purge them and re-configure my X server.
Anyway,good luck!

---

### Post by blenderfox on 2011-09-15
Okay, well, let's see how some games handle the settings now.

---

