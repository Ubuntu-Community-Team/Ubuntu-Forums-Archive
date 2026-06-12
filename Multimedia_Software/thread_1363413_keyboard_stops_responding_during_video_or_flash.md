---
title: "keyboard stops responding during video or flash"
date: 2009-12-24
forum: Multimedia Software
---

### Post by leeko on 2009-12-24
Hi all, 

I originally posted this in the Mythbuntu forum, but I believe it's not just mythtv that's affected. Hoping someone in the main forum can shed some light :)

I'm running mythbuntu 9.10 on a zotac ionitx motherboard with integrated geforce 9400M video. The CPU is a dual core atom 330, and the system is fully updated.

Whenever I watch TV or play a recording, the keyboard and mouse (logitech mk300 wireless) partially stops responding for a couple of minutes. I say partially, because myth doesn't respond to keypresses but I'm able to alt-tab out of myth ok. It keeps playing in the background, and the video runs smoothly.

When I'm in another application (with video running), the keypresses are only variably picked up, and occasionally repeat multiple times. Also, the mouse movements are jerky and mouseclicks register only sometimes. It almost seems like the CPU load is maxed out, but top shows it running only at ~30%. When video isn't running, the keyboard/mouse works fine.

I've also noticed this happens when playing flash video (e.g. youtube) in a browser, so it's not limited to myth. It also happens on the gmail webpage (flash ads?). I've read that the dual-core atom (and this mobo in particular) is more than capable of HD-video, and I'm only trying to play SD-video at present.

I tried updating the gfx drivers (nvidia 185.x to 190.x), but the problem persists. I changed mythtv's (and nvidia-xconfig) settings to use openGL sync, and added the "UseEvents" option to xorg.conf. I'd say things got slightly better, but it's still borderline unusable. 

I've included my xorg.0.log below, in the hope that it makes sense to someone - I wasn't able to see any obvious problems. Can anyone help me troubleshoot this further?

```

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux LeekoMythFE 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-16-generic root=UUID=3fee537f-6dd0-41a3-a4a7-b8770f78f7ae ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 23 09:49:24 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:3:0:0) 10de:087d:19da:a108 nVidia Corporation ION VGA rev 177, Mem @ 0xfb000000/16777216, 0xe0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000ec00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[b]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[b]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[b]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[b]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[b]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[b]
(WW) "dri2" will not be loaded unless you've specified it to be loaded elsewhere.
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded even though the default is to disable it.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  190.53  Tue Dec  8 20:47:42 PST 2009
(II) Loading extension GLX
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  190.53  Tue Dec  8 19:16:02 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 03@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[b]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[b]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[b]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[b]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[b]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[b]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "UseEvents" "True"
(**) Dec 23 09:49:28 NVIDIA(0): Enabling RENDER acceleration
(II) Dec 23 09:49:28 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Dec 23 09:49:28 NVIDIA(0):     enabled.
(II) Dec 23 09:49:30 NVIDIA(0): NVIDIA GPU ION (C79) at PCI:3:0:0 (GPU-0)
(--) Dec 23 09:49:30 NVIDIA(0): Memory: 524288 kBytes
(--) Dec 23 09:49:30 NVIDIA(0): VideoBIOS: 62.79.65.00.00
(--) Dec 23 09:49:30 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Dec 23 09:49:30 NVIDIA(0): Connected display device(s) on ION at PCI:3:0:0:
(--) Dec 23 09:49:30 NVIDIA(0):     PLX PHD5039NUS (DFP-0)
(--) Dec 23 09:49:30 NVIDIA(0): PLX PHD5039NUS (DFP-0): 330.0 MHz maximum pixel clock
(--) Dec 23 09:49:30 NVIDIA(0): PLX PHD5039NUS (DFP-0): Internal Dual Link TMDS
(II) Dec 23 09:49:30 NVIDIA(0): Assigned Display Device: DFP-0
(==) Dec 23 09:49:30 NVIDIA(0): 
(==) Dec 23 09:49:30 NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) Dec 23 09:49:30 NVIDIA(0):     will be used as the requested mode.
(==) Dec 23 09:49:30 NVIDIA(0): 
(II) Dec 23 09:49:30 NVIDIA(0): Validated modes:
(II) Dec 23 09:49:30 NVIDIA(0):     "nvidia-auto-select"
(II) Dec 23 09:49:30 NVIDIA(0): Virtual screen size determined to be 1366 x 768
(--) Dec 23 09:49:30 NVIDIA(0): DPI set to (31, 34); computed from "UseEdidDpi" X config
(--) Dec 23 09:49:30 NVIDIA(0):     option
(==) Dec 23 09:49:30 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[b]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[b]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[b]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[b]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[b]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[b]
(II) Dec 23 09:49:30 NVIDIA(0): Initialized GPU GART.
(II) Dec 23 09:49:30 NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) Dec 23 09:49:30 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Dec 23 09:49:30 NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
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
(II) Initializing extension GLX
(II) config/hal: Adding input device Logitech USB Receiver
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event4"
(II) Logitech USB Receiver: Found 12 mouse buttons
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as mouse
(II) Logitech USB Receiver: Configuring as keyboard
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
(**) Logitech USB Receiver: (accel) filter chain progression: 2.00
(**) Logitech USB Receiver: (accel) filter stage 0: 20.00 ms
(**) Logitech USB Receiver: (accel) set acceleration profile 0
(II) Logitech USB Receiver: initialized for relative axes.
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event3"
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
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
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
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

```

Thanks in advance,

Lee

---

### Post by master_kernel on 2010-01-23
Wow, just about the same problem here. There's something in mythbackend that's interfering with xorg - after I ran sudo killall mythbackend the buttons on my keyboard that were not responding before started responding again. Thanks for the tip!

---

