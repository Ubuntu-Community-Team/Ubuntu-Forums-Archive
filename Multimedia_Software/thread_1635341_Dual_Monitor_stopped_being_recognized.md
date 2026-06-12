---
title: "Dual Monitor stopped being recognized"
date: 2010-12-01
forum: Multimedia Software
---

### Post by UncleAelfrich on 2010-12-01
I am running Ubuntu 10.10 on a Dell Vostro 3700 laptop with an I3 processor and the Intel Arrandale integrated video. I have run two different monitors, an Epson projector, and a Pioneer Elite Kuro Plasma as a second monitor to my laptop's screen. All have worked.

However, on two occasions now, the main monitor that I use as a dual monitor is failing to be recognized by my laptop. The monitor is a Dell 2007 FPb that usually runs at a 1600x1200 resolution. I connect to this monitor via my laptop's HDMI port to the monitor's DVI port.

Yesterday I used my laptop with my Epson projector which connects via the laptop's VGA port. Today I have been unable to get the laptop to display the monitor. The monitor recognizes that the DVI connection is present, then it reports "Entering power save" and goes to sleep.

This happened one time before, and after a few days, my laptop suddenly started recognizing the Dell monitor again. I have a sneaky suspicion that the xorg or xrandr file isn't returning a mode that the monitor can display, or something like that.

Here is my xorg.0.log file:
[HTML][    14.134] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    14.134] X Protocol Version 11, Revision 0
[    14.134] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    14.134] Current Operating System: Linux bigdaddylaptop.magnetgeek 2.6.35-23-generic-pae #40-Ubuntu SMP Wed Nov 17 22:32:51 UTC 2010 i686
[    14.134] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-23-generic-pae root=UUID=74a1e611-ba80-4ff9-9aec-4657ef4e39ae ro quiet splash
[    14.134] Build Date: 16 September 2010  05:39:22PM
[    14.134] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    14.134] Current version of pixman: 0.18.4
[    14.134] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    14.134] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.134] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec  1 14:03:29 2010
[    14.296] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.299] (==) No Layout section.  Using the first Screen section.
[    14.299] (==) No screen section available. Using defaults.
[    14.299] (**) |-->Screen "Default Screen Section" (0)
[    14.299] (**) |   |-->Monitor "<default monitor>"
[    14.299] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    14.299] (==) Automatically adding devices
[    14.299] (==) Automatically enabling devices
[    14.300] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.300] 	Entry deleted from font path.
[    14.300] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    14.300] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    14.300] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    14.300] (II) Loader magic: 0x81f8e00
[    14.300] (II) Module ABI versions:
[    14.300] 	X.Org ANSI C Emulation: 0.4
[    14.300] 	X.Org Video Driver: 8.0
[    14.300] 	X.Org XInput driver : 11.0
[    14.300] 	X.Org Server Extension : 4.0
[    14.301] (--) PCI:*(0:0:2:0) 8086:0046:1028:0442 rev 18, Mem @ 0xfac00000/4194304, 0xc0000000/268435456, I/O @ 0x0000f080/8
[    14.301] (II) Open ACPI successful (/var/run/acpid.socket)
[    14.301] (II) LoadModule: "extmod"
[    14.473] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    14.473] (II) Module extmod: vendor="X.Org Foundation"
[    14.473] 	compiled for 1.9.0, module version = 1.0.0
[    14.473] 	Module class: X.Org Server Extension
[    14.473] 	ABI class: X.Org Server Extension, version 4.0
[    14.473] (II) Loading extension MIT-SCREEN-SAVER
[    14.473] (II) Loading extension XFree86-VidModeExtension
[    14.473] (II) Loading extension XFree86-DGA
[    14.473] (II) Loading extension DPMS
[    14.473] (II) Loading extension XVideo
[    14.473] (II) Loading extension XVideo-MotionCompensation
[    14.473] (II) Loading extension X-Resource
[    14.473] (II) LoadModule: "dbe"
[    14.473] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    14.474] (II) Module dbe: vendor="X.Org Foundation"
[    14.474] 	compiled for 1.9.0, module version = 1.0.0
[    14.474] 	Module class: X.Org Server Extension
[    14.474] 	ABI class: X.Org Server Extension, version 4.0
[    14.474] (II) Loading extension DOUBLE-BUFFER
[    14.474] (II) LoadModule: "glx"
[    14.474] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    14.474] (II) Module glx: vendor="X.Org Foundation"
[    14.474] 	compiled for 1.9.0, module version = 1.0.0
[    14.474] 	ABI class: X.Org Server Extension, version 4.0
[    14.474] (==) AIGLX enabled
[    14.474] (II) Loading extension GLX
[    14.474] (II) LoadModule: "record"
[    14.474] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    14.474] (II) Module record: vendor="X.Org Foundation"
[    14.474] 	compiled for 1.9.0, module version = 1.13.0
[    14.474] 	Module class: X.Org Server Extension
[    14.474] 	ABI class: X.Org Server Extension, version 4.0
[    14.474] (II) Loading extension RECORD
[    14.474] (II) LoadModule: "dri"
[    14.474] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    14.474] (II) Module dri: vendor="X.Org Foundation"
[    14.474] 	compiled for 1.9.0, module version = 1.0.0
[    14.475] 	ABI class: X.Org Server Extension, version 4.0
[    14.475] (II) Loading extension XFree86-DRI
[    14.475] (II) LoadModule: "dri2"
[    14.475] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    14.475] (II) Module dri2: vendor="X.Org Foundation"
[    14.475] 	compiled for 1.9.0, module version = 1.2.0
[    14.475] 	ABI class: X.Org Server Extension, version 4.0
[    14.475] (II) Loading extension DRI2
[    14.475] (==) Matched intel as autoconfigured driver 0
[    14.475] (==) Matched vesa as autoconfigured driver 1
[    14.475] (==) Matched fbdev as autoconfigured driver 2
[    14.475] (==) Assigned the driver to the xf86ConfigLayout
[    14.475] (II) LoadModule: "intel"
[    14.475] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    14.475] (II) Module intel: vendor="X.Org Foundation"
[    14.475] 	compiled for 1.9.0, module version = 2.12.0
[    14.475] 	Module class: X.Org Video Driver
[    14.475] 	ABI class: X.Org Video Driver, version 8.0
[    14.475] (II) LoadModule: "vesa"
[    14.476] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    14.476] (II) Module vesa: vendor="X.Org Foundation"
[    14.476] 	compiled for 1.8.99.905, module version = 2.3.0
[    14.476] 	Module class: X.Org Video Driver
[    14.476] 	ABI class: X.Org Video Driver, version 8.0
[    14.476] (II) LoadModule: "fbdev"
[    14.476] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    14.476] (II) Module fbdev: vendor="X.Org Foundation"
[    14.476] 	compiled for 1.8.99.905, module version = 0.4.2
[    14.476] 	ABI class: X.Org Video Driver, version 8.0
[    14.476] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[    14.477] (II) VESA: driver for VESA chipsets: vesa
[    14.477] (II) FBDEV: driver for framebuffer: fbdev
[    14.477] (++) using VT number 7

[    14.477] (WW) Falling back to old probe method for vesa
[    14.477] (WW) Falling back to old probe method for fbdev
[    14.477] (II) Loading sub module "fbdevhw"
[    14.477] (II) LoadModule: "fbdevhw"
[    14.477] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    14.477] (II) Module fbdevhw: vendor="X.Org Foundation"
[    14.477] 	compiled for 1.9.0, module version = 0.0.2
[    14.477] 	ABI class: X.Org Video Driver, version 8.0
[    14.479] drmOpenDevice: node name is /dev/dri/card0
[    14.479] drmOpenDevice: open result is 9, (OK)
[    14.480] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    14.480] drmOpenDevice: node name is /dev/dri/card0
[    14.480] drmOpenDevice: open result is 9, (OK)
[    14.480] drmOpenByBusid: drmOpenMinor returns 9
[    14.480] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    14.480] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    14.480] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    14.480] (==) intel(0): RGB weight 888
[    14.480] (==) intel(0): Default visual is TrueColor
[    14.480] (II) intel(0): Integrated Graphics Chipset: Intel(R) Arrandale
[    14.480] (--) intel(0): Chipset: "Arrandale"
[    14.480] (==) intel(0): video overlay key set to 0x101fe
[    14.497] (II) intel(0): Output VGA1 has no monitor section
[    14.497] (II) intel(0): Output LVDS1 has no monitor section
[    14.497] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    14.515] (II) intel(0): EDID for output VGA1
[    14.515] (II) intel(0): EDID for output LVDS1
[    14.515] (II) intel(0): Manufacturer: LGD  Model: 288  Serial#: 0
[    14.515] (II) intel(0): Year: 2009  Week: 0
[    14.515] (II) intel(0): EDID Version: 1.3
[    14.515] (II) intel(0): Digital Display Input
[    14.515] (II) intel(0): Max Image Size [cm]: horiz.: 38  vert.: 21
[    14.515] (II) intel(0): Gamma: 2.20
[    14.515] (II) intel(0): No DPMS capabilities specified
[    14.515] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    14.515] (II) intel(0): First detailed timing is preferred mode
[    14.515] (II) intel(0): redX: 0.618 redY: 0.348   greenX: 0.312 greenY: 0.598
[    14.515] (II) intel(0): blueX: 0.150 blueY: 0.110   whiteX: 0.313 whiteY: 0.329
[    14.515] (II) intel(0): Manufacturer's mask: 0
[    14.515] (II) intel(0): Supported detailed timing:
[    14.515] (II) intel(0): clock: 97.8 MHz   Image Size:  382 x 215 mm
[    14.515] (II) intel(0): h_active: 1600  h_sync: 1648  h_sync_end 1696 h_blank_end 1784 h_border: 0
[    14.515] (II) intel(0): v_active: 900  v_sync: 902  v_sync_end 905 v_blanking: 912 v_border: 0
[    14.515] (II) intel(0): Supported detailed timing:
[    14.515] (II) intel(0): clock: 97.8 MHz   Image Size:  382 x 215 mm
[    14.515] (II) intel(0): h_active: 1600  h_sync: 1648  h_sync_end 1696 h_blank_end 1784 h_border: 0
[    14.515] (II) intel(0): v_active: 900  v_sync: 902  v_sync_end 905 v_blanking: 912 v_border: 0
[    14.515] (II) intel(0):  84FGP173WD1
[    14.515] (II) intel(0): Unknown vendor-specific block 0
[    14.515] (II) intel(0): EDID (in hex):
[    14.515] (II) intel(0): 	00ffffffffffff0030e4880200000000
[    14.515] (II) intel(0): 	00130103902615780a4c959e594f9926
[    14.515] (II) intel(0): 	1c505400000001010101010101010101
[    14.515] (II) intel(0): 	0101010101012f2640b860840c303030
[    14.515] (II) intel(0): 	23007ed71000001a2f2640b860840c30
[    14.515] (II) intel(0): 	303023007ed71000001a000000fe0038
[    14.515] (II) intel(0): 	34464750143137335744310a00000000
[    14.515] (II) intel(0): 	000059012d0100000002010a202000cf
[    14.515] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    14.515] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    14.515] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    14.515] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    14.515] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    14.515] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    14.515] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    14.515] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    14.516] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    14.516] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    14.516] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    14.516] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    14.516] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    14.516] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    14.516] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    14.516] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    14.516] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    14.516] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    14.516] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    14.516] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    14.516] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    14.516] (II) intel(0): Printing probed modes for output LVDS1
[    14.516] (II) intel(0): Modeline "1600x900"x60.1   97.75  1600 1648 1696 1784  900 902 905 912 +hsync -vsync (54.8 kHz)
[    14.516] (II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    14.516] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    14.516] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[    14.516] (II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[    14.516] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    14.516] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    14.516] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    14.516] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    14.516] (II) intel(0): Output VGA1 disconnected
[    14.516] (II) intel(0): Output LVDS1 connected
[    14.516] (II) intel(0): Using exact sizes for initial modes
[    14.516] (II) intel(0): Output LVDS1 using initial mode 1600x900
[    14.516] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    14.516] (II) intel(0): Kernel page flipping support detected, but forcibly disabled.
[    14.516] (==) intel(0): DPI set to (96, 96)
[    14.516] (II) Loading sub module "fb"
[    14.516] (II) LoadModule: "fb"
[    14.516] (II) Loading /usr/lib/xorg/modules/libfb.so
[    14.516] (II) Module fb: vendor="X.Org Foundation"
[    14.516] 	compiled for 1.9.0, module version = 1.0.0
[    14.516] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    14.516] (II) UnloadModule: "vesa"
[    14.516] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    14.516] (II) UnloadModule: "fbdev"
[    14.516] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    14.516] (II) UnloadModule: "fbdevhw"
[    14.516] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    14.516] (==) Depth 24 pixmap format is 32 bpp
[    14.516] (II) intel(0): [DRI2] Setup complete
[    14.516] (II) intel(0): [DRI2]   DRI driver: i965
[    14.516] (**) intel(0): Tiling enabled
[    14.516] (**) intel(0): SwapBuffers wait enabled
[    14.516] (==) intel(0): VideoRam: 262144 KB
[    14.516] (II) intel(0): Allocated new frame buffer 1600x900 stride 6656, tiled
[    14.524] (II) UXA(0): Driver registered support for the following operations:
[    14.524] (II)         solid
[    14.524] (II)         copy
[    14.524] (II)         composite (RENDER acceleration)
[    14.525] (II)         put_image
[    14.525] (II)         get_image
[    14.525] (==) intel(0): Backing store disabled
[    14.525] (==) intel(0): Silken mouse enabled
[    14.525] (II) intel(0): Initializing HW Cursor
[    14.561] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    14.562] (==) intel(0): DPMS enabled
[    14.562] (==) intel(0): Intel XvMC decoder enabled
[    14.562] (II) intel(0): Set up textured video
[    14.562] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    14.562] (II) intel(0): direct rendering: DRI2 Enabled
[    14.562] (--) RandR disabled
[    14.562] (II) Initializing built-in extension Generic Event Extension
[    14.562] (II) Initializing built-in extension SHAPE
[    14.562] (II) Initializing built-in extension MIT-SHM
[    14.562] (II) Initializing built-in extension XInputExtension
[    14.562] (II) Initializing built-in extension XTEST
[    14.562] (II) Initializing built-in extension BIG-REQUESTS
[    14.562] (II) Initializing built-in extension SYNC
[    14.562] (II) Initializing built-in extension XKEYBOARD
[    14.562] (II) Initializing built-in extension XC-MISC
[    14.562] (II) Initializing built-in extension SECURITY
[    14.562] (II) Initializing built-in extension XINERAMA
[    14.562] (II) Initializing built-in extension XFIXES
[    14.562] (II) Initializing built-in extension RENDER
[    14.562] (II) Initializing built-in extension RANDR
[    14.562] (II) Initializing built-in extension COMPOSITE
[    14.562] (II) Initializing built-in extension DAMAGE
[    14.562] (II) Initializing built-in extension GESTURE
[    14.575] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    14.575] (II) AIGLX: enabled GLX_INTEL_swap_event
[    14.575] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    14.575] (II) AIGLX: enabled GLX_SGI_make_current_read
[    14.575] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    14.576] (II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
[    14.576] (II) GLX: Initialized DRI2 GL provider for screen 0
[    14.576] (II) intel(0): Setting screen physical size to 423 x 238
[    14.595] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    14.603] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    14.603] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    14.603] (II) LoadModule: "evdev"
[    14.603] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.603] (II) Module evdev: vendor="X.Org Foundation"
[    14.603] 	compiled for 1.9.0, module version = 2.3.2
[    14.603] 	Module class: X.Org XInput Driver
[    14.603] 	ABI class: X.Org XInput driver, version 11.0
[    14.603] (**) Power Button: always reports core events
[    14.603] (**) Power Button: Device: "/dev/input/event3"
[    14.612] (II) Power Button: Found keys
[    14.612] (II) Power Button: Configuring as keyboard
[    14.612] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    14.612] (**) Option "xkb_rules" "evdev"
[    14.612] (**) Option "xkb_model" "pc105"
[    14.612] (**) Option "xkb_layout" "us"
[    14.613] (II) config/udev: Adding input device Video Bus (/dev/input/event10)
[    14.613] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    14.613] (**) Video Bus: always reports core events
[    14.613] (**) Video Bus: Device: "/dev/input/event10"
[    14.625] (II) Video Bus: Found keys
[    14.625] (II) Video Bus: Configuring as keyboard
[    14.625] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    14.625] (**) Option "xkb_rules" "evdev"
[    14.625] (**) Option "xkb_model" "pc105"
[    14.625] (**) Option "xkb_layout" "us"
[    14.627] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    14.627] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    14.627] (**) Power Button: always reports core events
[    14.627] (**) Power Button: Device: "/dev/input/event0"
[    14.649] (II) Power Button: Found keys
[    14.649] (II) Power Button: Configuring as keyboard
[    14.649] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    14.649] (**) Option "xkb_rules" "evdev"
[    14.649] (**) Option "xkb_model" "pc105"
[    14.649] (**) Option "xkb_layout" "us"
[    14.650] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    14.650] (II) No input driver/identifier specified (ignoring)
[    14.650] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    14.650] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    14.650] (**) Sleep Button: always reports core events
[    14.650] (**) Sleep Button: Device: "/dev/input/event2"
[    14.661] (II) Sleep Button: Found keys
[    14.661] (II) Sleep Button: Configuring as keyboard
[    14.661] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    14.661] (**) Option "xkb_rules" "evdev"
[    14.661] (**) Option "xkb_model" "pc105"
[    14.661] (**) Option "xkb_layout" "us"
[    14.663] (II) config/udev: Adding input device HID 413c:8161 (/dev/input/event6)
[    14.663] (**) HID 413c:8161: Applying InputClass "evdev keyboard catchall"
[    14.663] (**) HID 413c:8161: always reports core events
[    14.663] (**) HID 413c:8161: Device: "/dev/input/event6"
[    14.677] (II) HID 413c:8161: Found keys
[    14.677] (II) HID 413c:8161: Configuring as keyboard
[    14.677] (II) XINPUT: Adding extended input device "HID 413c:8161" (type: KEYBOARD)
[    14.677] (**) Option "xkb_rules" "evdev"
[    14.677] (**) Option "xkb_model" "pc105"
[    14.677] (**) Option "xkb_layout" "us"
[    14.679] (II) config/udev: Adding input device HDA Intel Mic at Ext Front Jack (/dev/input/event11)
[    14.679] (II) No input driver/identifier specified (ignoring)
[    14.679] (II) config/udev: Adding input device HDA Intel HP Out at Ext Front Jack (/dev/input/event12)
[    14.679] (II) No input driver/identifier specified (ignoring)
[    14.680] (II) config/udev: Adding input device Microsoft Microsoft® SideWinder™ X5 Mouse (/dev/input/event5)
[    14.680] (**) Microsoft Microsoft® SideWinder™ X5 Mouse: Applying InputClass "evdev pointer catchall"
[    14.680] (**) Microsoft Microsoft® SideWinder™ X5 Mouse: Applying InputClass "evdev keyboard catchall"
[    14.681] (**) Microsoft Microsoft® SideWinder™ X5 Mouse: always reports core events
[    14.681] (**) Microsoft Microsoft® SideWinder™ X5 Mouse: Device: "/dev/input/event5"
[    14.696] (II) Microsoft Microsoft® SideWinder™ X5 Mouse: Found 9 mouse buttons
[    14.696] (II) Microsoft Microsoft® SideWinder™ X5 Mouse: Found scroll wheel(s)
[    14.696] (II) Microsoft Microsoft® SideWinder™ X5 Mouse: Found relative axes
[    14.696] (II) Microsoft Microsoft® SideWinder™ X5 Mouse: Found x and y relative axes
[    14.696] (II) Microsoft Microsoft® SideWinder™ X5 Mouse: Found absolute axes
[    14.696] (II) evdev-grail: failed to open grail, no gesture support
[    14.696] (II) Microsoft Microsoft® SideWinder™ X5 Mouse: Found x and y absolute axes
[    14.696] (II) Microsoft Microsoft® SideWinder™ X5 Mouse: Found keys
[    14.696] (II) Microsoft Microsoft® SideWinder™ X5 Mouse: Configuring as mouse
[    14.696] (II) Microsoft Microsoft® SideWinder™ X5 Mouse: Configuring as keyboard
[    14.696] (**) Microsoft Microsoft® SideWinder™ X5 Mouse: YAxisMapping: buttons 4 and 5
[    14.696] (**) Microsoft Microsoft® SideWinder™ X5 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    14.696] (II) XINPUT: Adding extended input device "Microsoft Microsoft® SideWinder™ X5 Mouse" (type: KEYBOARD)
[    14.696] (**) Option "xkb_rules" "evdev"
[    14.696] (**) Option "xkb_model" "pc105"
[    14.696] (**) Option "xkb_layout" "us"
[    14.697] (II) Microsoft Microsoft® SideWinder™ X5 Mouse: initialized for relative axes.
[    14.697] (WW) Microsoft Microsoft® SideWinder™ X5 Mouse: ignoring absolute axes.
[    14.697] (II) config/udev: Adding input device Microsoft Microsoft® SideWinder™ X5 Mouse (/dev/input/js0)
[    14.697] (II) No input driver/identifier specified (ignoring)
[    14.697] (II) config/udev: Adding input device Microsoft Microsoft® SideWinder™ X5 Mouse (/dev/input/mouse0)
[    14.697] (II) No input driver/identifier specified (ignoring)
[    14.698] (II) config/udev: Adding input device Laptop_Integrated_Webcam_2M (/dev/input/event8)
[    14.698] (**) Laptop_Integrated_Webcam_2M: Applying InputClass "evdev keyboard catchall"
[    14.698] (**) Laptop_Integrated_Webcam_2M: always reports core events
[    14.698] (**) Laptop_Integrated_Webcam_2M: Device: "/dev/input/event8"
[    14.708] (II) Laptop_Integrated_Webcam_2M: Found keys
[    14.708] (II) Laptop_Integrated_Webcam_2M: Configuring as keyboard
[    14.708] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_2M" (type: KEYBOARD)
[    14.708] (**) Option "xkb_rules" "evdev"
[    14.708] (**) Option "xkb_model" "pc105"
[    14.708] (**) Option "xkb_layout" "us"
[    14.710] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    14.710] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    14.710] (**) AT Translated Set 2 keyboard: always reports core events
[    14.710] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    14.724] (II) AT Translated Set 2 keyboard: Found keys
[    14.724] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    14.724] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    14.724] (**) Option "xkb_rules" "evdev"
[    14.724] (**) Option "xkb_model" "pc105"
[    14.724] (**) Option "xkb_layout" "us"
[    14.725] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event9)
[    14.725] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    14.725] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    14.725] (II) LoadModule: "synaptics"
[    14.725] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    14.725] (II) Module synaptics: vendor="X.Org Foundation"
[    14.725] 	compiled for 1.9.0, module version = 1.2.2
[    14.725] 	Module class: X.Org XInput Driver
[    14.725] 	ABI class: X.Org XInput driver, version 11.0
[    14.725] (II) Synaptics touchpad driver version 1.2.2
[    14.725] (**) Option "Device" "/dev/input/event9"
[    14.844] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5650
[    14.844] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4710
[    14.844] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    14.844] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    14.844] (II) SynPS/2 Synaptics TouchPad: buttons: left right
[    14.976] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    14.987] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    15.021] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    15.021] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    15.021] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    15.021] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    15.021] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    15.097] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    15.097] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    15.097] (II) No input driver/identifier specified (ignoring)
[    15.100] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event7)
[    15.100] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    15.100] (**) Dell WMI hotkeys: always reports core events
[    15.100] (**) Dell WMI hotkeys: Device: "/dev/input/event7"
[    15.133] (II) Dell WMI hotkeys: Found keys
[    15.133] (II) Dell WMI hotkeys: Configuring as keyboard
[    15.133] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
[    15.133] (**) Option "xkb_rules" "evdev"
[    15.133] (**) Option "xkb_model" "pc105"
[    15.133] (**) Option "xkb_layout" "us"
[    16.152] (II) intel(0): EDID vendor "LGD", prod id 648
[    16.152] (II) intel(0): Printing DDC gathered Modelines:
[    16.152] (II) intel(0): Modeline "1600x900"x0.0   97.75  1600 1648 1696 1784  900 902 905 912 +hsync -vsync (54.8 kHz)
[    16.170] (II) intel(0): EDID vendor "LGD", prod id 648
[    16.170] (II) intel(0): Printing DDC gathered Modelines:
[    16.170] (II) intel(0): Modeline "1600x900"x0.0   97.75  1600 1648 1696 1784  900 902 905 912 +hsync -vsync (54.8 kHz)
[    16.201] (II) intel(0): EDID vendor "LGD", prod id 648
[    16.201] (II) intel(0): Printing DDC gathered Modelines:
[    16.201] (II) intel(0): Modeline "1600x900"x0.0   97.75  1600 1648 1696 1784  900 902 905 912 +hsync -vsync (54.8 kHz)
[    16.219] (II) intel(0): EDID vendor "LGD", prod id 648
[    16.219] (II) intel(0): Printing DDC gathered Modelines:
[    16.219] (II) intel(0): Modeline "1600x900"x0.0   97.75  1600 1648 1696 1784  900 902 905 912 +hsync -vsync (54.8 kHz)
[    22.634] (II) intel(0): EDID vendor "LGD", prod id 648
[    22.634] (II) intel(0): Printing DDC gathered Modelines:
[    22.634] (II) intel(0): Modeline "1600x900"x0.0   97.75  1600 1648 1696 1784  900 902 905 912 +hsync -vsync (54.8 kHz)
[    22.673] (II) intel(0): EDID vendor "LGD", prod id 648
[    22.673] (II) intel(0): Printing DDC gathered Modelines:
[    22.673] (II) intel(0): Modeline "1600x900"x0.0   97.75  1600 1648 1696 1784  900 902 905 912 +hsync -vsync (54.8 kHz)
[    22.691] (II) intel(0): EDID vendor "LGD", prod id 648
[    22.691] (II) intel(0): Printing DDC gathered Modelines:
[    22.691] (II) intel(0): Modeline "1600x900"x0.0   97.75  1600 1648 1696 1784  900 902 905 912 +hsync -vsync (54.8 kHz)
[    23.170] (II) intel(0): EDID vendor "LGD", prod id 648
[    23.171] (II) intel(0): Printing DDC gathered Modelines:
[    23.171] (II) intel(0): Modeline "1600x900"x0.0   97.75  1600 1648 1696 1784  900 902 905 912 +hsync -vsync (54.8 kHz)
[    28.495] (II) intel(0): EDID vendor "LGD", prod id 648
[    28.495] (II) intel(0): Printing DDC gathered Modelines:
[    28.495] (II) intel(0): Modeline "1600x900"x0.0   97.75  1600 1648 1696 1784  900 902 905 912 +hsync -vsync (54.8 kHz)
[   964.000] (II) XKB: reuse xkmfile /var/lib/xkb/server-81EC4871279DB1D73113D19E789F270C19322F52.xkm
[  1380.744] (II) intel(0): EDID vendor "LGD", prod id 648
[  1380.744] (II) intel(0): Printing DDC gathered Modelines:
[  1380.744] (II) intel(0): Modeline "1600x900"x0.0   97.75  1600 1648 1696 1784  900 902 905 912 +hsync -vsync (54.8 kHz)hore
[  4242.108] (II) intel(0): EDID vendor "LGD", prod id 648
[  4242.108] (II) intel(0): Printing DDC gathered Modelines:
[  4242.108] (II) intel(0): Modeline "1600x900"x0.0   97.75  1600 1648 1696 1784  900 902 905 912 +hsync -vsync (54.8 kHz)[/HTML]

and here is the output for xrandr -q
> sudo xrandr -q -v
xrandr program version       1.3.3
Screen 0: minimum 320 x 200, current 1600 x 900, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1600x900+0+0 (normal left inverted right x axis y axis) 382mm x 215mm
   1600x900       60.1*+
   1440x900       59.9  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  


I would appreciate any help folks can give me.

---

### Post by UncleAelfrich on 2010-12-02
More information.

This morning I used my laptop with my Pioneer Elite Kuro display. Here is the xrandr output from that.

[HTML]xrandr program version       1.3.3 
Screen 0: minimum 320 x 200, current 3520 x 1080, maximum 8192 x 8192 
VGA1 disconnected (normal left inverted right x axis y axis) 
LVDS1 connected 1600x900+0+0 (normal left inverted right x axis y axis) 382mm x 215mm 
   1600x900       60.1*+ 
   1440x900       59.9  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
HDMI1 connected 1920x1080+1600+0 (normal left inverted right x axis y axis) 1102mm x 620mm 
   1920x1080      60.0*+ 
   1280x1024      60.0  
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3  
   720x480        59.9  
   640x480        60.0  
DP1 disconnected (normal left inverted right x axis y axis) [/HTML]

However, when I connected my laptop to my Dell flatscreen monitor at work, I got this output again
[HTML]xrandr program version       1.3.3
Screen 0: minimum 320 x 200, current 1600 x 900, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1600x900+0+0 (normal left inverted right x axis y axis) 382mm x 215mm
   1600x900       60.1*+
   1440x900       59.9  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
~$ xrandr --output HDMI1 --auto
warning: output HDMI1 not found; ignoring
~$ xrandr --output DP1 --auto
warning: output DP1 not found; ignoring[/HTML]

---

### Post by UncleAelfrich on 2010-12-02
This is a follow-up in case other people find the same problem.

this morning I used my Epson projector, shut down the laptop while the projector was still plugged in. Then I booted up my laptop with the Dell Monitor connected. It recognized the Dell Monitor.

[HTML]Screen 0: minimum 320 x 200, current 3200 x 1200, maximum 8192 x 8192 
VGA1 disconnected (normal left inverted right x axis y axis) 
LVDS1 connected 1600x900+0+300 (normal left inverted right x axis y axis) 382mm x 215mm 
   1600x900       60.1*+ 
   1440x900       59.9  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
HDMI1 connected 1600x1200+1600+0 (normal left inverted right x axis y axis) 367mm x 275mm 
   1600x1200      60.0*+ 
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
DP1 disconnected (normal left inverted right x axis y axis) [/HTML]

Why it works now, I really don't know.

---

