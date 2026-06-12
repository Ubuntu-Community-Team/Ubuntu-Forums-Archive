---
title: "Dual Nvidia cards"
date: 2009-02-14
forum: Multimedia Software
---

### Post by sibernet on 2009-02-14
I have a GeForce 9400 GT and a NV34 GeForce FX 5200, I've been playing with trying to get them to work together. Is it possible to get a newer nvidia and a older nvidia card to work together? Now both cards with work on their own in the same system. Currently running 177 nvidia drivers. Thanks for any help.

Current xorg.conf:
Section "Device"
	Identifier     "Device0"
	VendorName     "NVIDIA Corporation"
	BoardName      "GeForce 9400 GT"
	BusID		"PCI:1:0:0"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Device"
	Identifier	"Device1"
	BusID		"PCI:5:4:0"
	Driver          "nvidia"
EndSection

Section "Monitor"
	Identifier     "Monitor0"
	VendorName     "Unknown"
	ModelName      "DELL2407WFPHC"
	HorizSync       30.0 - 83.0
	VertRefresh     56.0 - 76.0
EndSection

Section "Monitor"
	Identifier     "Monitor1"
EndSection

Section "Screen"
	Identifier     "Screen0"
	Device         "Device0"
	Monitor        "Monitor0"
	DefaultDepth    24
	Option         "TwinView" "1"
	Option         "metamodes" "DFP-0: nvidia-auto-select +1920+0, DFP-1: nvidia-auto-select +0+0"
	SubSection "Display"
		Depth       24
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen1"
	Monitor		"Monitor1"
	Device		"Device1"
EndSection

Section "Module"
	Load           "glx"
EndSection

Section "ServerLayout"
	Identifier     "Layout0"
	Screen      0  "Screen0" 0 0
	Screen      1 "Screen1" RightOf "Screen1"

EndSection



Section "ServerFlags"
	Option         "Xinerama" "0"
EndSection


And last xorg.log:
X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux Rketcham 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64
Build Date: 24 October 2008  09:06:49AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@crested.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.2.log", Time: Sat Feb 14 16:35:27 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Device1"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7b7320
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(--) using VT number 9

(--) PCI:*(0@1:0:0) nVidia Corporation unknown chipset (0x0641) rev 161, Mem @ 0xee000000/16777216, 0xd0000000/268435456, 0xec000000/33554432, I/O @ 0x0000dc80/128, BIOS @ 0x????????/524288
(--) PCI: (0@5:4:0) nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xea000000/16777216, 0xe0000000/134217728, BIOS @ 0x????????/131072
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  177.82  Tue Nov  4 17:15:47 PST 2008
(II) Loading extension GLX
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
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
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"

(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  177.82  Tue Nov  4 16:56:15 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"

(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(WW) NVIDIA(0): The NVIDIA GeForce FX 5200 GPU installed in this system is
(WW) NVIDIA(0):     supported through the NVIDIA 173.14.xx Legacy drivers.
(WW) NVIDIA(0):     Please visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for
(WW) NVIDIA(0):     more information.  The 177.82 NVIDIA driver will ignore
(WW) NVIDIA(0):     this GPU.  Continuing probe... 
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "MetaModes" "DFP-0: nvidia-auto-select +1920+0, DFP-1: nvidia-auto-select +0+0"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 9400 GT (G96) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 1048576 kBytes
(--) NVIDIA(0): VideoBIOS: 62.94.29.00.40
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 9400 GT at PCI:1:0:0:
(--) NVIDIA(0):     DELL2407WFPHC (DFP-0)
(--) NVIDIA(0):     DELL 2408WFP (DFP-1)
(--) NVIDIA(0): DELL2407WFPHC (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): DELL2407WFPHC (DFP-0): Internal Dual Link TMDS
(--) NVIDIA(0): DELL 2408WFP (DFP-1): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): DELL 2408WFP (DFP-1): Internal Dual Link TMDS
(**) NVIDIA(0): TwinView enabled
(II) NVIDIA(0): Display Devices found referenced in MetaMode: DFP-0, DFP-1
(II) NVIDIA(0): Assigned Display Devices: DFP-0, DFP-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):    
(II) NVIDIA(0):     "DFP-0:nvidia-auto-select+1920+0,DFP-1:nvidia-auto-select+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 3840 x 1200
(--) NVIDIA(0): DPI set to (93, 92); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode
(II) NVIDIA(0):     "DFP-0:nvidia-auto-select+1920+0,DFP-1:nvidia-auto-select+0+0"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Dell Dell USB Keyboard
(**) Dell Dell USB Keyboard: always reports core events
(**) Dell Dell USB Keyboard: Device: "/dev/input/event4"
(II) Dell Dell USB Keyboard: Found keys
(II) Dell Dell USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Dell Dell USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Dell Dell USB Keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Dell Dell USB Keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Dell Dell USB Keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Dell Dell USB Keyboard
(**) Dell Dell USB Keyboard: always reports core events
(**) Dell Dell USB Keyboard: Device: "/dev/input/event3"
(II) Dell Dell USB Keyboard: Found keys
(II) Dell Dell USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Dell Dell USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Dell Dell USB Keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Dell Dell USB Keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Dell Dell USB Keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event2"
(II) Logitech USB Receiver: Found 1 mouse buttons
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Logitech USB Receiver: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Logitech USB Receiver: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Logitech USB Receiver: xkb_layout: "us"
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event1"
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found 16 mouse buttons
(II) Logitech USB Receiver: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
AUDIT: Sat Feb 14 16:35:29 2009: 6921 X: client 1 rejected from local host ( uid=0 gid=0 pid=6916 )
AUDIT: Sat Feb 14 16:35:31 2009: 6921 X: client 1 rejected from local host ( uid=0 gid=0 pid=6916 )
AUDIT: Sat Feb 14 16:39:25 2009: 6921 X: client 1 rejected from local host ( uid=0 gid=0 pid=6916 )
AUDIT: Sat Feb 14 16:39:27 2009: 6921 X: client 1 rejected from local host ( uid=0 gid=0 pid=6916 )
(II) Logitech USB Receiver: Close
(II) UnloadModule: "evdev"
(II) Logitech USB Receiver: Close
(II) UnloadModule: "evdev"
(II) Dell Dell USB Keyboard: Close
(II) UnloadModule: "evdev"
(II) Dell Dell USB Keyboard: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"

---

### Post by sibernet on 2009-02-19
Ok I kept doing some research and I pretty much couldn't find anything on doing this and I assume it is pretty much impossible to run a older card with a new card. I ended up downgrading to 173 drivers and tossing the 9400 and putting in a 8600. It took a little time but I got that working correctly

Now my last problem is that when I got the third screen working my panels stretch across both big monitors. I know about the turning off the expand but then the panel is stuck in the middle of two browsers. If I take out the thrid screen the monitors work the way i like with the panels staying on each monitor and being able to move windows between them. Anyone got any ideas on that?

Now my config looks like


Section "ServerLayout"
	Identifier     "Layout0"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	 	
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 2408WFP"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Monitor"
	Identifier     "Monitor1"
	VendorName     "Unknown"
	HorizSync       30.0 - 83.0
	VertRefresh     56.0 - 76.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"Device1"
	BusID		"PCI:5:4:0"
#	screen		1
	Driver		"nvidia"
#	Option		"NoLogo"	"True"
#	Option	        "NoInt10" "Yes"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1920+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"Device1"
	Monitor		"Monitor1"
	DefaultDepth    24
	SubSection 	"Display"
			Viewport 0 0
			Depth 24
			Modes "1280x1024"
	EndSubSection
EndSection

---

