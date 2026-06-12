---
title: "No video from HDMI to Bose A/V Receiver - HDCP problem?"
date: 2010-03-27
forum: Mythbuntu
---

### Post by mal on 2010-03-27
I have a mythtv frontend running on an Intel DG43GT mother board with Intel GMA X4500 graphics.  The video output from the HDMI port works when connected to a Samsung HDTV television, but when I connect to the Bose A/V Receiver, it refuses to display 1920x1080 video.

I can manually select 640x480 resolution using xrandr from a remote login and it displays correctly.  However, as soon as I change to 1920x1080 the Bose displays a "No Video Signal" message and the screen goes blank.

Below is the contents of Xorg.0.log that is produced when I boot up with the Bose system connected.

```

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux 001cc0ee24c7 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686
Kernel command line: ro initrd=initrd.img quiet splash BOOT_IMAGE=vmlinuz 
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Mar 27 12:04:35 2010
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 2

(--) PCI:*(0:0:2:0) 8086:2e22:8086:0028 Intel Corporation 4 Series Chipset Integrated Graphics Controller rev 3, Mem @ 0xd0000000/4194304, 0xc0000000/268435456, I/O @ 0x0000f1a0/8
(==) Using default built-in configuration (39 lines)
(==) --- Start of built-in configuration ---
	Section "Device"
		Identifier	"Builtin Default intel Device 0"
		Driver	"intel"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default intel Screen 0"
		Device	"Builtin Default intel Device 0"
	EndSection
	Section "Device"
		Identifier	"Builtin Default i810 Device 0"
		Driver	"i810"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default i810 Screen 0"
		Device	"Builtin Default i810 Device 0"
	EndSection
	Section "Device"
		Identifier	"Builtin Default vesa Device 0"
		Driver	"vesa"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default vesa Screen 0"
		Device	"Builtin Default vesa Device 0"
	EndSection
	Section "Device"
		Identifier	"Builtin Default fbdev Device 0"
		Driver	"fbdev"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default fbdev Screen 0"
		Device	"Builtin Default fbdev Device 0"
	EndSection
	Section "ServerLayout"
		Identifier	"Builtin Default Layout"
		Screen	"Builtin Default intel Screen 0"
		Screen	"Builtin Default i810 Screen 0"
		Screen	"Builtin Default vesa Screen 0"
		Screen	"Builtin Default fbdev Screen 0"
	EndSection
(==) --- End of built-in configuration ---
(==) ServerLayout "Builtin Default Layout"
(**) |-->Screen "Builtin Default intel Screen 0" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default intel Device 0"
(==) No monitor specified for screen "Builtin Default intel Screen 0".
	Using a default monitor configuration.
(**) |-->Screen "Builtin Default i810 Screen 0" (1)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default i810 Device 0"
(==) No monitor specified for screen "Builtin Default i810 Screen 0".
	Using a default monitor configuration.
(**) |-->Screen "Builtin Default vesa Screen 0" (2)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default vesa Device 0"
(==) No monitor specified for screen "Builtin Default vesa Screen 0".
	Using a default monitor configuration.
(**) |-->Screen "Builtin Default fbdev Screen 0" (3)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default fbdev Device 0"
(==) No monitor specified for screen "Builtin Default fbdev Screen 0".
	Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/Type1" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.9.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "i810"
(WW) Warning, couldn't open module i810
(II) UnloadModule: "i810"
(EE) Failed to load module "i810" (module does not exist, 0)
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 2.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.4.0
	ABI class: X.Org Video Driver, version 5.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 0.0.2
	ABI class: X.Org Video Driver, version 5.0
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): Creating default Display subsection in Screen section
	"Builtin Default intel Screen 0" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) G45/G43
(--) intel(0): Chipset: "G45/G43"
(II) intel(0): Output VGA1 has no monitor section
(II) intel(0): Output HDMI1 has no monitor section
(II) intel(0): Output DP1 has no monitor section
(II) intel(0): Output HDMI2 has no monitor section
(II) intel(0): Output DP2 has no monitor section
(II) intel(0): EDID for output VGA1
(II) Quirked EDID physical size to 2x1 cm
(II) Quirked timing size to 20x10 mm
(II) Quirked timing size to 20x10 mm
(II) intel(0): EDID for output HDMI1
(II) intel(0): Manufacturer: BSE  Model: a156  Serial#: 0
(II) intel(0): Year: 2006  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 2  vert.: 1
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 148.5 MHz   Image Size:  20 x 10 mm
(II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 148.5 MHz   Image Size:  20 x 10 mm
(II) intel(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
(II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) intel(0): Monitor name: LS_V20/30
(II) intel(0): Ranges: V min: 48 V max: 62 Hz, H min: 14 H max: 68 kHz, PixClock max 150 MHz
(II) intel(0): Number of EDID sections to follow: 1
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff000a6556a100000000
(II) intel(0): 	00100103801009780aee91a3544c9926
(II) intel(0): 	0f505420000001010101010101010101
(II) intel(0): 	010101010101023a801871382d40582c
(II) intel(0): 	450010090000001e023a80d072382d40
(II) intel(0): 	102c458010090000001e000000fc004c
(II) intel(0): 	535f5632302f33300a202020000000fd
(II) intel(0): 	00303e0e440f000a2020202020200103
(II) intel(0): Printing probed modes for output HDMI1
(II) intel(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output DP1
(II) intel(0): EDID for output HDMI2
(II) intel(0): EDID for output DP2
(II) intel(0): Output VGA1 disconnected
(II) intel(0): Output HDMI1 connected
(II) intel(0): Output DP1 disconnected
(II) intel(0): Output HDMI2 disconnected
(II) intel(0): Output DP2 disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output HDMI1 using initial mode 1920x1080
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux//libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) intel(0): [DRI2] Setup complete
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): No memory allocations
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder disabled
(II) intel(0): Set up textured video
(II) intel(0): direct rendering: DRI2 Enabled
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) intel(0): Setting screen physical size to 20 x 10
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Sleep Button
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event1"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event6"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event2"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device USB Wheel Mouse
(**) USB Wheel Mouse: always reports core events
(**) USB Wheel Mouse: Device: "/dev/input/event5"
(II) USB Wheel Mouse: Found 3 mouse buttons
(II) USB Wheel Mouse: Found x and y relative axes
(II) USB Wheel Mouse: Found scroll wheel(s)
(II) USB Wheel Mouse: Configuring as mouse
(**) USB Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) USB Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "USB Wheel Mouse" (type: MOUSE)
(**) USB Wheel Mouse: (accel) keeping acceleration scheme 1
(**) USB Wheel Mouse: (accel) filter chain progression: 2.00
(**) USB Wheel Mouse: (accel) filter stage 0: 20.00 ms
(**) USB Wheel Mouse: (accel) set acceleration profile 0
(II) USB Wheel Mouse: initialized for relative axes.
(II) intel(0): EDID for output VGA1
(II) Quirked EDID physical size to 2x1 cm
(II) Quirked timing size to 20x10 mm
(II) Quirked timing size to 20x10 mm
(II) intel(0): EDID for output HDMI1
(II) intel(0): Manufacturer: BSE  Model: a156  Serial#: 0
(II) intel(0): Year: 2006  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 2  vert.: 1
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 148.5 MHz   Image Size:  20 x 10 mm
(II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 148.5 MHz   Image Size:  20 x 10 mm
(II) intel(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
(II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) intel(0): Monitor name: LS_V20/30
(II) intel(0): Ranges: V min: 48 V max: 62 Hz, H min: 14 H max: 68 kHz, PixClock max 150 MHz
(II) intel(0): Number of EDID sections to follow: 1
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff000a6556a100000000
(II) intel(0): 	00100103801009780aee91a3544c9926
(II) intel(0): 	0f505420000001010101010101010101
(II) intel(0): 	010101010101023a801871382d40582c
(II) intel(0): 	450010090000001e023a80d072382d40
(II) intel(0): 	102c458010090000001e000000fc004c
(II) intel(0): 	535f5632302f33300a202020000000fd
(II) intel(0): 	00303e0e440f000a2020202020200103
(II) intel(0): EDID vendor "BSE", prod id 41302
(II) intel(0): Using EDID range info for horizontal sync
(II) intel(0): Using EDID range info for vertical refresh
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Printing probed modes for output HDMI1
(II) intel(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output DP1
(II) intel(0): EDID for output HDMI2
(II) intel(0): EDID for output DP2
(II) intel(0): EDID for output VGA1
(II) Quirked EDID physical size to 2x1 cm
(II) Quirked timing size to 20x10 mm
(II) Quirked timing size to 20x10 mm
(II) intel(0): EDID for output HDMI1
(II) intel(0): Manufacturer: BSE  Model: a156  Serial#: 0
(II) intel(0): Year: 2006  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 2  vert.: 1
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 148.5 MHz   Image Size:  20 x 10 mm
(II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 148.5 MHz   Image Size:  20 x 10 mm
(II) intel(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
(II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) intel(0): Monitor name: LS_V20/30
(II) intel(0): Ranges: V min: 48 V max: 62 Hz, H min: 14 H max: 68 kHz, PixClock max 150 MHz
(II) intel(0): Number of EDID sections to follow: 1
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff000a6556a100000000
(II) intel(0): 	00100103801009780aee91a3544c9926
(II) intel(0): 	0f505420000001010101010101010101
(II) intel(0): 	010101010101023a801871382d40582c
(II) intel(0): 	450010090000001e023a80d072382d40
(II) intel(0): 	102c458010090000001e000000fc004c
(II) intel(0): 	535f5632302f33300a202020000000fd
(II) intel(0): 	00303e0e440f000a2020202020200103
(II) intel(0): EDID vendor "BSE", prod id 41302
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Printing probed modes for output HDMI1
(II) intel(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output DP1
(II) intel(0): EDID for output HDMI2
(II) intel(0): EDID for output DP2
```

I can't see any obvious problem here except for some strange screen dimension values, but the Samsung TV also displays odd dimensions, so I don't think this is the problem.

Given that the problem occurs with the high definition signal, I suspect that HDCP is blocking the video output.

I really welcome any suggestions on how I can further investigate this.

The TV is wall-mounted, so I need to connect through the Bose system to avoid having to run another HDMI cable through the wall.

Any help greatly appreciated.

Mal

---

### Post by nickrout on 2010-03-27
I suspect the Bose is not giving correct edid info to the video card. Plug the computer straight into the TV, download the edid and use nvidia'a UseEDID setting to point it to the edid file you got firect from the TV. Then plug back in thru the bose.

---

### Post by mal on 2010-03-27
> **nickrout said:**
> I suspect the Bose is not giving correct edid info to the video card. Plug the computer straight into the TV, download the edid and use nvidia'a UseEDID setting to point it to the edid file you got firect from the TV. Then plug back in thru the bose.

Nickrout,

Thanks for the suggestion.  The only problem is that I have Intel graphics, so I don't know if there is an equivalent to nvidia's UseEDID setting.  However, I'll research a bit further to see if I can find something similar.

Regards,

Mal

---

### Post by nickrout on 2010-03-28
sorry i don't know why i thought nvidia, must have been someone else!

OK try this. Run while attached directly. OPen a terminal and run ```
xvidtune
```

In the xvidtune window click "show" and your currrent modeline will appear in the terminal like this:

> nick@dell:~$ xvidtune 
Vendor: (null), Model: (null)
Num hsync: 1, Num vsync: 1
hsync range 0:  49.79 -  49.79
vsync range 0:  59.99 -  59.99
"1280x800"     72.10   1280 1296 1344 1448    800  802  804  830 -hsync -vsync



Try using the shown modeline in your xorg.conf.

You may have to use the hsync and vsync figures in xorg.conf too.

---

### Post by mal on 2010-03-28
nickrout,

When I connect directly to the TV, xvidtune gives:

```
Vendor: (null), Model: (null)
Num hsync: 1, Num vsync: 1
hsync range 0:  26.00 -  81.00
vsync range 0:  24.00 -  75.00
"1920x1080"   148.50   1920 2008 2052 2200   1080 1084 1089 1125 +hsync +vsync
```

and when I boot up connected to the Bose system, "xvidtune -show" gives:

```
"1920x1080"   148.50   1920 2008 2052 2200   1080 1084 1089 1125 +hsync +vsync
```

(Note that I have to use command line mode from a remote login because I can't see the video output.)

So, it appears that the driver is correctly identifying an appropriate modeline from the information supplied by the Bose system.

It still looks like a problem with HDCP not allowing the graphics subsystem to send out HD video.

Mal

---

### Post by mal on 2010-03-28
After a bit more research, it seems that there is an issue with Intel drivers and HDMI outputs.  See the following links:

[http://software.intel.com/en-us/blogs/2008/04/22/hdcp-hdmi-repeaters-and-you-well-me-anyway/]("http://software.intel.com/en-us/blogs/2008/04/22/hdcp-hdmi-repeaters-and-you-well-me-anyway/")

[http://en.wikipedia.org/wiki/HDCP_Repeater_bit]("http://en.wikipedia.org/wiki/HDCP_Repeater_bit")

I am starting to think that I will just have to cable directly to the TV and bypass the A/V receiver.  This is far from ideal!

Alternatively, I will try a later version of the Intel driver, maybe using Lucid, to see if they have fixed this design flaw.

I'm still keen to hear if anyone has any further suggestions.

Thanks,

Mal

---

### Post by nickrout on 2010-03-28
hdcp is irrelevant. endpoints are not obliged to negotiate it. However, some content sources will only work if it has
been negotiated. But that's entirely a content choice, nothing to do with getting the OS to display a desktop or the myth frontend.

---

### Post by mal on 2010-03-28
> **nickrout said:**
> hdcp is irrelevant. endpoints are not obliged to negotiate it. However, some content sources will only work if it has
been negotiated. But that's entirely a content choice, nothing to do with getting the OS to display a desktop or the myth frontend.

nickrout,

This is also my understanding or how HDCP is supposed to work, although the articles I linked to above don't really make it clear whether an HDCP handshake failure will only block protected content, or if it will block all content.

It is strange that it works OK at 640x480 resolution, but fails when I select either of the 1920x1080 modes that the Bose system reports as acceptable.

In any case, if it is not a problem with HDCP, I still don't know why I can't get it to work.

Another bit if interesting information is that X and mythtv seem to be running OK even when there is no video getting through to the TV, so the userland software seems to think that all is well.

Thanks for your help with this.

Regards,

Mal

---

### Post by nickrout on 2010-03-28
dunno what to recommend next. I assume the cables ARE all right?? Many a time I couldn't get networking to work, only to find an unplugged cable. Check and recheck they are all plugged in and that the bose is set to thr tight input. Sounds silly I know, but never underestimate the obvious!

---

### Post by mal on 2010-03-28
The cables work fine at 640x480 resolution.  The cable from the PC to the Bose is HDMI 1.3 high speed compliant.  The cable from the Bose to the TV is the one that was supplied by Samsung and it works fine when connected directly from the PC to the TV.

I've ordered a new HDMI cable to run in parallel with the existing cable through the wall to the TV (a job I'm not looking forward to!!).  This tends to defeat the purpose of the A/V receiver, but will at least get things running.

As an alternative, I might even try plugging in an Nvidia card with HDMI/DVI output to see how it works.

Mal

---

### Post by mal on 2010-04-12
I can now add some further information to this thread.

I gave up on the machine with the Intel graphics and decided to put together a new MythTV frontend using an Atom 330 / Nvidia ION combination.  The motherboard I chose was a "Point of View ION-MB330-1" purchased from [Umart Online]("http://umart.com.au/") for AUD$225 and an Antec ISK300-65 mini-itx case (AUD$95).  This is working well with full HD video capability and it outputs full resolution video on HDMI through the Bose A/V receiver with no problems.

It seems clear to me that the Intel graphics chipset and/or its linux driver is defective with respect to HDMI and HDCP.

Mal

---

### Post by nickrout on 2010-04-12
It has nothing to do with HDCP!!

---

### Post by mal on 2010-04-15
> **nickrout said:**
> It has nothing to do with HDCP!!

nickrout,

I agree that this _should not_ be related to HDCP  because it is only meant to block _protected content_ from being sent to non-compliant devices.

However, the fact remains that the Intel graphics on my DG43GT motherboard would not send any HD video on the HDMI output when connected to a Bose A/V receiver.  On the other hand, the Nvidia ION graphics chip-set works as expected and happily sends my MythTV video through the A/V receiver.

Until now, I have been happy to use motherboards with Intel graphics, but will probably stick with Nvidia from now on to avoid these HDMI problems.

Regards,

Mal

---

### Post by dibuntux on 2010-04-15
IF it can be of any help, my system is connects (see below) via DVI to HDMI cable to a Denon AVR1610 ampli then HDMI to HDMI to my Optoma HD700 projector.
If I forget to turn the ampli ON at the same time as the PC, the projector would not get the signal - i.e., turning the ampli on after boot will not get a lock - it will just lock to the HDMI switch at 640x480 with no signal.
So, the SVGA card (nVidia) has to find the HDMI switch on the ampli at boot; after boot you can turn the ampli OFF & ON again and the lock will still be there.

Hope it helps.

Mythbuntu 9.10 AMD64
Gigabyte GA-M720 2GB DDR2-800
Athlon X2 4800+
Nvidia 9500GT 1GB
WD Sata2 CaviarGreen
Skystar 2 DVB-s
HVR1110 DVB-t

---

### Post by mal on 2010-04-16
dibuntux,

Thanks for the contribution.

I can add that, at one stage, when I had my MythTV frontend running on the machine with the Intel graphics chipset and connected directly to the Samsung TV, I paused a recorded show and turned off the television.  When I turned the TV back on to resume watching the recording, I could not get a video signal.  It appears that the system was not able to renegotiate an HDMI connection.  I had to reboot the frontend to get it working again.

I have not yet tried this with the Nvidia ION machine.

Mal

---

### Post by n1wil on 2011-04-25
I too am having this problem on the same system with Intel graphics.  Rebooting the system gets video back, but if I switch sources (from the MythDVR to my PS3) on the ONKYO receiver and then back to the MythDVR, I cannot get video to re-establish on my screen.  Royal PITA!  

Rebooting is the only way to get video restored on the HDMI input.  Stupid!

Using Ubuntu 10.4 and installed both MythTV frontend and backend packages.

---

