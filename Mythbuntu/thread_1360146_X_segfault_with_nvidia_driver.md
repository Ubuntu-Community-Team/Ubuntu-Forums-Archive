---
title: "X segfault with nvidia driver"
date: 2009-12-20
forum: Mythbuntu
---

### Post by myth_cougar on 2009-12-20
X server segfaults with message in /var/log/messages:

mythtv kernel: [ 1037.259064] Xorg[2638]: segfault at 878ce000 ip 08ce18f2 sp bfdb2870 error 6 in nvidia_drv.so[89bc000+3c4000]

This is on a fresh install of 9.10 selecting nvidia driver during install and then doing upgrade on packages after being notified there were updates available.

Initial startup is fine, but after navigating around myth menus display often gets corrupted and will sometime lock up dumping me back to the login screen.  The above message was displayed in the log.

System is:
AMD Athlon 64 X2 4850e
Gigabyte GA-MA78GM-S2H
XFX GEFORCE GT220

An earlier fresh install with open source driver appeared to be working fine and I could play videos, but minor tearing evident, so I wanted to use nvidia drivers and vdpau which this card supports. 

I have also disabled composite in xorg.conf but done no other changes.

xorg.conf is:
------------------------------
Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "UseEvents"     "1"
        Option  "DPI"   "100x100"
        Option  "NoLogo"        "1"
EndSection

Section "Extensions"
        Option "Composite" "Disable"
EndSection
-----------------------------------------------------
Xorg.0.log is
-----------------------------------------------------
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux mythtv 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-16-generic root=UUID=4f1dbc77-e54d-443f-ba13-9062462f69fb ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@)
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Dec 20 19:38:16 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen".
        Using the first device section listed.
(**) |   |-->Device "Default Device"
(==) No monitor specified for screen "Default Screen".
        Using a default monitor configuration.
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
(**) Extension "Composite" is disabled
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
        If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.4
        X.Org Video Driver: 5.0
        X.Org XInput driver : 4.0
        X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 9

(--) PCI:*(0:1:0:0) 10de:0a20:1682:294a nVidia Corporation GT200 [GeForce GT 220] rev 162, Mem @ 0xfb000000/16777216, 0xb0000000/268435456, 0xce000000/33554432, I/O @ 0x0000ef00/128, BIOS @ 0x????????/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [4] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]
        [5] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [6] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [7] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [8] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]
        [9] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [10] -1 0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [11] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [12] -1 0       0xffffffff - 0xffffffff (0x1) MX[b]
        [13] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [14] -1 0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [15] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [16] -1 0       0xffffffff - 0xffffffff (0x1) MX[b]
        [17] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [18] -1 0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [19] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [20] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [21] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]
        [22] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [23] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]
        [24] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [25] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]
        [26] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [27] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]
        [28] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [29] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]
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
(II) Module glx: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.0
        Module class: X.Org Server Extension
(II) NVIDIA GLX Module  185.18.36  Fri Aug 14 17:50:12 PDT 2009
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.0
        Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  185.18.36  Fri Aug 14 17:24:40 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
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
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [4] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]
        [5] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [6] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [7] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [8] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]
        [9] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [10] -1 0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [11] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [12] -1 0       0xffffffff - 0xffffffff (0x1) MX[b]
        [13] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [14] -1 0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [15] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [16] -1 0       0xffffffff - 0xffffffff (0x1) MX[b]
        [17] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [18] -1 0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [19] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [20] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [21] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]
        [22] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [23] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]
        [24] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [25] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]
        [26] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [27] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]
        [28] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [29] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]
(II) NVIDIA(0): Creating default Display subsection in Screen section
        "Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "1"
(**) NVIDIA(0): Option "DPI" "100x100"
(**) NVIDIA(0): Option "UseEvents" "1"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): NVIDIA GPU GeForce GT 220 (GT216) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 1048576 kBytes
(--) NVIDIA(0): VideoBIOS: 70.16.2e.00.70
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce GT 220 at PCI:1:0:0:
(--) NVIDIA(0):     HSD HX191D (DFP-0)
(--) NVIDIA(0): HSD HX191D (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): HSD HX191D (DFP-0): Internal Dual Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(==) NVIDIA(0):
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0):
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(**) NVIDIA(0): DPI set to (100, 100); computed from "DPI" X config option
(==) NVIDIA(0): Disabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [4] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]
        [5] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [6] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [7] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [8] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]
        [9] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [10] -1 0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [11] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [12] -1 0       0xffffffff - 0xffffffff (0x1) MX[b]
        [13] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [14] -1 0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [15] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [16] -1 0       0xffffffff - 0xffffffff (0x1) MX[b]
        [17] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [18] -1 0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [19] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [20] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [21] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]
        [22] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [23] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]
        [24] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [25] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]
        [26] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [27] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]
        [28] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [29] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
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
(II) config/hal: Adding input device 2.4G USB RF KeyBoard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
        compiled for 1.6.4, module version = 2.2.5
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 4.0
(**) 2.4G USB RF KeyBoard: always reports core events
(**) 2.4G USB RF KeyBoard: Device: "/dev/input/event5"
(II) 2.4G USB RF KeyBoard: Found keys
(II) 2.4G USB RF KeyBoard: Configuring as keyboard
(II) XINPUT: Adding extended input device "2.4G USB RF KeyBoard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/hal: Adding input device 2.4G USB RF KeyBoard
(**) 2.4G USB RF KeyBoard: always reports core events
(**) 2.4G USB RF KeyBoard: Device: "/dev/input/event3"
(II) 2.4G USB RF KeyBoard: Found keys
(II) 2.4G USB RF KeyBoard: Configuring as keyboard
(II) XINPUT: Adding extended input device "2.4G USB RF KeyBoard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
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
(II) config/hal: Adding input device 2.4G USB RF KeyBoard
(**) 2.4G USB RF KeyBoard: always reports core events
(**) 2.4G USB RF KeyBoard: Device: "/dev/input/event4"
(II) 2.4G USB RF KeyBoard: Found 3 mouse buttons
(II) 2.4G USB RF KeyBoard: Found x and y relative axes
(II) 2.4G USB RF KeyBoard: Found scroll wheel(s)
(II) 2.4G USB RF KeyBoard: Configuring as mouse
(**) 2.4G USB RF KeyBoard: YAxisMapping: buttons 4 and 5
(**) 2.4G USB RF KeyBoard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "2.4G USB RF KeyBoard" (type: MOUSE)
(**) 2.4G USB RF KeyBoard: (accel) keeping acceleration scheme 1
(**) 2.4G USB RF KeyBoard: (accel) filter chain progression: 2.00
(**) 2.4G USB RF KeyBoard: (accel) filter stage 0: 20.00 ms
(**) 2.4G USB RF KeyBoard: (accel) set acceleration profile 0
(II) 2.4G USB RF KeyBoard: initialized for relative axes.
(II) NVIDIA(0): Initialized GPU GART.
-----------------------------------------------------------

---

