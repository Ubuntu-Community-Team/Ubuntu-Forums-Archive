---
title: "Mythbuntu low resolution on VGA - nvidia"
date: 2011-02-06
forum: Mythbuntu
---

### Post by davidstoll on 2011-02-06
I had to format and reinstall Mythbuntu and used VGA out as my connection to my HDTV.  I had 1920x1080 before, but now I only get 1024x768 or some other strange resolutions that aren't even comparable with my video card.  The restricted driver is in use "current version".

I've searched around and have seen where people insert things into the xorg.conf file, but I'm not having any luck.  It seems like I need to get a newer driver installed somehow.  However, my HDMI out gets the full 1080p...but I use the HDMI for something else, so I need the VGA for the TV.

Can anyone help me troubleshoot this?
I'm sorry to make another thread about the xorg.conf, but none of the ones I tried helped.

---

### Post by nickrout on 2011-02-06
did you save xorg.conf from your last setup?

What does the X log file say? /var/log/Xorg.0.log

---

### Post by davidstoll on 2011-02-06
> **nickrout said:**
> did you save xorg.conf from your last setup?

What does the X log file say? /var/log/Xorg.0.log

Yes, I do have a copy of it.  I put the copied the file over, but it didn't help.

here is my Xorg.0.log
```
[    15.727] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    15.727] X Protocol Version 11, Revision 0
[    15.727] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[    15.727] Current Operating System: Linux Mythbuntu 2.6.35-25-generic-pae #44-Ubuntu SMP Fri Jan 21 19:01:46 UTC 2011 i686
[    15.727] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-25-generic-pae root=UUID=e1c6cf47-4ed1-404f-84ae-cfa744064ffe ro quiet splash
[    15.727] Build Date: 09 January 2011  12:14:58PM
[    15.727] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
[    15.727] Current version of pixman: 0.18.4
[    15.727] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    15.727] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    15.727] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Feb  6 19:25:24 2011
[    15.727] (==) Using config file: "/etc/X11/xorg.conf"
[    15.727] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    15.728] (==) ServerLayout "Layout0"
[    15.728] (**) |-->Screen "Screen0" (0)
[    15.728] (**) |   |-->Monitor "Monitor0"
[    15.728] (**) |   |-->Device "Device0"
[    15.728] (**) |-->Input Device "Keyboard0"
[    15.728] (**) |-->Input Device "Mouse0"
[    15.728] (**) Option "Xinerama" "0"
[    15.728] (==) Automatically adding devices
[    15.728] (==) Automatically enabling devices
[    15.728] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    15.728] 	Entry deleted from font path.
[    15.728] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    15.728] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    15.728] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    15.728] (WW) Disabling Keyboard0
[    15.728] (WW) Disabling Mouse0
[    15.728] (II) Loader magic: 0x81f9b00
[    15.728] (II) Module ABI versions:
[    15.728] 	X.Org ANSI C Emulation: 0.4
[    15.728] 	X.Org Video Driver: 8.0
[    15.728] 	X.Org XInput driver : 11.0
[    15.728] 	X.Org Server Extension : 4.0
[    15.729] (--) PCI:*(0:1:0:0) 10de:0421:1462:0921 rev 161, Mem @ 0xee000000/16777216, 0xd0000000/268435456, 0xec000000/33554432, I/O @ 0x0000b000/128, BIOS @ 0x????????/131072
[    15.729] (--) PCI: (0:6:8:0) 4444:0016:0070:e807 rev 1, Mem @ 0xe4000000/67108864
[    15.729] (--) PCI: (0:6:9:0) 4444:0016:0070:e817 rev 1, Mem @ 0xe8000000/67108864
[    15.729] (II) Open ACPI successful (/var/run/acpid.socket)
[    15.730] (II) LoadModule: "extmod"
[    15.746] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    15.747] (II) Module extmod: vendor="X.Org Foundation"
[    15.747] 	compiled for 1.9.0, module version = 1.0.0
[    15.747] 	Module class: X.Org Server Extension
[    15.747] 	ABI class: X.Org Server Extension, version 4.0
[    15.747] (II) Loading extension MIT-SCREEN-SAVER
[    15.747] (II) Loading extension XFree86-VidModeExtension
[    15.747] (II) Loading extension XFree86-DGA
[    15.747] (II) Loading extension DPMS
[    15.747] (II) Loading extension XVideo
[    15.747] (II) Loading extension XVideo-MotionCompensation
[    15.747] (II) Loading extension X-Resource
[    15.747] (II) LoadModule: "dbe"
[    15.747] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    15.747] (II) Module dbe: vendor="X.Org Foundation"
[    15.747] 	compiled for 1.9.0, module version = 1.0.0
[    15.747] 	Module class: X.Org Server Extension
[    15.747] 	ABI class: X.Org Server Extension, version 4.0
[    15.747] (II) Loading extension DOUBLE-BUFFER
[    15.747] (II) LoadModule: "glx"
[    15.747] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    15.766] (II) Module glx: vendor="NVIDIA Corporation"
[    15.766] 	compiled for 4.0.2, module version = 1.0.0
[    15.766] 	Module class: X.Org Server Extension
[    15.766] (II) NVIDIA GLX Module  260.19.06  Mon Sep 13 07:01:31 PDT 2010
[    15.766] (II) Loading extension GLX
[    15.766] (II) LoadModule: "record"
[    15.766] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    15.766] (II) Module record: vendor="X.Org Foundation"
[    15.766] 	compiled for 1.9.0, module version = 1.13.0
[    15.766] 	Module class: X.Org Server Extension
[    15.766] 	ABI class: X.Org Server Extension, version 4.0
[    15.766] (II) Loading extension RECORD
[    15.766] (II) LoadModule: "dri"
[    15.767] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    15.767] (II) Module dri: vendor="X.Org Foundation"
[    15.767] 	compiled for 1.9.0, module version = 1.0.0
[    15.767] 	ABI class: X.Org Server Extension, version 4.0
[    15.767] (II) Loading extension XFree86-DRI
[    15.767] (II) LoadModule: "dri2"
[    15.767] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    15.767] (II) Module dri2: vendor="X.Org Foundation"
[    15.767] 	compiled for 1.9.0, module version = 1.2.0
[    15.767] 	ABI class: X.Org Server Extension, version 4.0
[    15.767] (II) Loading extension DRI2
[    15.767] (II) LoadModule: "nvidia"
[    15.767] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    15.767] (II) Module nvidia: vendor="NVIDIA Corporation"
[    15.767] 	compiled for 4.0.2, module version = 1.0.0
[    15.767] 	Module class: X.Org Video Driver
[    15.768] (II) NVIDIA dlloader X Driver  260.19.06  Mon Sep 13 06:37:13 PDT 2010
[    15.768] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    15.768] (++) using VT number 7

[    15.777] (II) Loading sub module "fb"
[    15.778] (II) LoadModule: "fb"
[    15.778] (II) Loading /usr/lib/xorg/modules/libfb.so
[    15.785] (II) Module fb: vendor="X.Org Foundation"
[    15.785] 	compiled for 1.9.0, module version = 1.0.0
[    15.786] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    15.786] (II) Loading sub module "wfb"
[    15.786] (II) LoadModule: "wfb"
[    15.786] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    15.786] (II) Module wfb: vendor="X.Org Foundation"
[    15.786] 	compiled for 1.9.0, module version = 1.0.0
[    15.786] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    15.786] (II) Loading sub module "ramdac"
[    15.786] (II) LoadModule: "ramdac"
[    15.786] (II) Module "ramdac" already built-in
[    15.786] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    15.786] (==) NVIDIA(0): RGB weight 888
[    15.786] (==) NVIDIA(0): Default visual is TrueColor
[    15.786] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    15.786] (**) NVIDIA(0): Option "TwinView" "0"
[    15.786] (**) NVIDIA(0): Option "MetaModes" "CRT: nvidia-auto-select +0+0"
[    15.786] (**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "CRT-0"
[    15.786] (**) NVIDIA(0): Enabling RENDER acceleration
[    15.786] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    15.786] (II) NVIDIA(0):     enabled.
[    16.667] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[    16.728] (II) NVIDIA(0): NVIDIA GPU GeForce 8500 GT (G86) at PCI:1:0:0 (GPU-0)
[    16.728] (--) NVIDIA(0): Memory: 524288 kBytes
[    16.728] (--) NVIDIA(0): VideoBIOS: 60.86.34.00.99
[    16.728] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    16.728] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    16.728] (--) NVIDIA(0): Connected display device(s) on GeForce 8500 GT at PCI:1:0:0
[    16.728] (--) NVIDIA(0):     CRT-0
[    16.728] (--) NVIDIA(0):     SAMSUNG (DFP-1)
[    16.728] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    16.728] (--) NVIDIA(0): SAMSUNG (DFP-1): 165.0 MHz maximum pixel clock
[    16.728] (--) NVIDIA(0): SAMSUNG (DFP-1): Internal Single Link TMDS
[    16.732] (II) NVIDIA(0): Display Device found referenced in MetaMode: CRT-0
[    16.735] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    16.735] (II) NVIDIA(0): Validated modes:
[    16.735] (II) NVIDIA(0):     "CRT:nvidia-auto-select+0+0"
[    16.735] (II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
[    16.765] (WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
[    16.765] (WW) NVIDIA(0):     from CRT-0's EDID.
[    16.765] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    16.765] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    16.765] (--) Depth 24 pixmap format is 32 bpp
[    16.765] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    16.766] (II) NVIDIA(0): Initialized GPU GART.
[    16.774] (II) NVIDIA(0): Setting mode "CRT:nvidia-auto-select+0+0"
[    16.835] (II) Loading extension NV-GLX
[    16.865] (II) NVIDIA(0): Initialized OpenGL Acceleration
[    16.868] (==) NVIDIA(0): Disabling shared memory pixmaps
[    16.868] (II) NVIDIA(0): Initialized X Rendering Acceleration
[    16.868] (==) NVIDIA(0): Backing store disabled
[    16.868] (==) NVIDIA(0): Silken mouse enabled
[    16.884] (**) NVIDIA(0): DPMS enabled
[    16.884] (II) Loading extension NV-CONTROL
[    16.884] (II) Loading extension XINERAMA
[    16.884] (II) Loading sub module "dri2"
[    16.884] (II) LoadModule: "dri2"
[    16.884] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[    16.884] (II) NVIDIA(0): [DRI2] Setup complete
[    16.884] (==) RandR enabled
[    16.884] (II) Initializing built-in extension Generic Event Extension
[    16.884] (II) Initializing built-in extension SHAPE
[    16.884] (II) Initializing built-in extension MIT-SHM
[    16.884] (II) Initializing built-in extension XInputExtension
[    16.884] (II) Initializing built-in extension XTEST
[    16.884] (II) Initializing built-in extension BIG-REQUESTS
[    16.884] (II) Initializing built-in extension SYNC
[    16.884] (II) Initializing built-in extension XKEYBOARD
[    16.884] (II) Initializing built-in extension XC-MISC
[    16.884] (II) Initializing built-in extension SECURITY
[    16.884] (II) Initializing built-in extension XINERAMA
[    16.884] (II) Initializing built-in extension XFIXES
[    16.884] (II) Initializing built-in extension RENDER
[    16.884] (II) Initializing built-in extension RANDR
[    16.884] (II) Initializing built-in extension COMPOSITE
[    16.884] (II) Initializing built-in extension DAMAGE
[    16.884] (II) Initializing built-in extension GESTURE
[    16.887] (II) Initializing extension GLX
[    16.914] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    16.922] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    16.922] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.922] (II) LoadModule: "evdev"
[    16.923] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.923] (II) Module evdev: vendor="X.Org Foundation"
[    16.923] 	compiled for 1.9.0, module version = 2.3.2
[    16.923] 	Module class: X.Org XInput Driver
[    16.923] 	ABI class: X.Org XInput driver, version 11.0
[    16.923] (**) Power Button: always reports core events
[    16.923] (**) Power Button: Device: "/dev/input/event1"
[    16.945] (II) Power Button: Found keys
[    16.945] (II) Power Button: Configuring as keyboard
[    16.945] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    16.945] (**) Option "xkb_rules" "evdev"
[    16.945] (**) Option "xkb_model" "pc105"
[    16.945] (**) Option "xkb_layout" "us"
[    16.946] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    16.946] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.946] (**) Power Button: always reports core events
[    16.946] (**) Power Button: Device: "/dev/input/event0"
[    16.977] (II) Power Button: Found keys
[    16.977] (II) Power Button: Configuring as keyboard
[    16.977] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    16.977] (**) Option "xkb_rules" "evdev"
[    16.977] (**) Option "xkb_model" "pc105"
[    16.977] (**) Option "xkb_layout" "us"
[    16.980] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
[    16.980] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    16.980] (**) Logitech USB Receiver: always reports core events
[    16.980] (**) Logitech USB Receiver: Device: "/dev/input/event2"
[    17.009] (II) Logitech USB Receiver: Found 20 mouse buttons
[    17.009] (II) Logitech USB Receiver: Found scroll wheel(s)
[    17.009] (II) Logitech USB Receiver: Found relative axes
[    17.009] (II) Logitech USB Receiver: Found x and y relative axes
[    17.009] (II) Logitech USB Receiver: Configuring as mouse
[    17.009] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    17.009] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    17.009] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
[    17.009] (II) Logitech USB Receiver: initialized for relative axes.
[    17.010] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    17.010] (II) No input driver/identifier specified (ignoring)
[    17.010] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[    17.010] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    17.010] (**) Logitech USB Receiver: always reports core events
[    17.010] (**) Logitech USB Receiver: Device: "/dev/input/event3"
[    17.041] (II) Logitech USB Receiver: Found 1 mouse buttons
[    17.041] (II) Logitech USB Receiver: Found scroll wheel(s)
[    17.041] (II) Logitech USB Receiver: Found relative axes
[    17.041] (II) Logitech USB Receiver: Found absolute axes
[    17.041] (II) evdev-grail: failed to open grail, no gesture support
[    17.041] (II) Logitech USB Receiver: Found keys
[    17.041] (II) Logitech USB Receiver: Configuring as mouse
[    17.041] (II) Logitech USB Receiver: Configuring as keyboard
[    17.041] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    17.041] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    17.041] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    17.041] (**) Option "xkb_rules" "evdev"
[    17.041] (**) Option "xkb_model" "pc105"
[    17.041] (**) Option "xkb_layout" "us"
[    17.041] (EE) Logitech USB Receiver: failed to initialize for relative axes.
[    17.041] (II) Logitech USB Receiver: initialized for absolute axes.
[    17.042] (II) config/udev: Adding input device Gyration Gyration RF Technology Receiver (/dev/input/event6)
[    17.042] (**) Gyration Gyration RF Technology Receiver: Applying InputClass "evdev keyboard catchall"
[    17.042] (**) Gyration Gyration RF Technology Receiver: always reports core events
[    17.042] (**) Gyration Gyration RF Technology Receiver: Device: "/dev/input/event6"
[    17.073] (II) Gyration Gyration RF Technology Receiver: Found 1 mouse buttons
[    17.073] (II) Gyration Gyration RF Technology Receiver: Found scroll wheel(s)
[    17.073] (II) Gyration Gyration RF Technology Receiver: Found relative axes
[    17.073] (II) Gyration Gyration RF Technology Receiver: Found absolute axes
[    17.073] (II) evdev-grail: failed to open grail, no gesture support
[    17.073] (II) Gyration Gyration RF Technology Receiver: Found keys
[    17.073] (II) Gyration Gyration RF Technology Receiver: Configuring as mouse
[    17.073] (II) Gyration Gyration RF Technology Receiver: Configuring as keyboard
[    17.073] (**) Gyration Gyration RF Technology Receiver: YAxisMapping: buttons 4 and 5
[    17.073] (**) Gyration Gyration RF Technology Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    17.073] (II) XINPUT: Adding extended input device "Gyration Gyration RF Technology Receiver" (type: KEYBOARD)
[    17.073] (**) Option "xkb_rules" "evdev"
[    17.073] (**) Option "xkb_model" "pc105"
[    17.073] (**) Option "xkb_layout" "us"
[    17.073] (EE) Gyration Gyration RF Technology Receiver: failed to initialize for relative axes.
[    17.073] (II) Gyration Gyration RF Technology Receiver: initialized for absolute axes.
[    17.074] (II) config/udev: Adding input device Gyration Gyration RF Technology Receiver (/dev/input/event7)
[    17.074] (**) Gyration Gyration RF Technology Receiver: Applying InputClass "evdev pointer catchall"
[    17.074] (**) Gyration Gyration RF Technology Receiver: Applying InputClass "evdev keyboard catchall"
[    17.074] (**) Gyration Gyration RF Technology Receiver: always reports core events
[    17.074] (**) Gyration Gyration RF Technology Receiver: Device: "/dev/input/event7"
[    17.105] (II) Gyration Gyration RF Technology Receiver: Found 9 mouse buttons
[    17.105] (II) Gyration Gyration RF Technology Receiver: Found scroll wheel(s)
[    17.105] (II) Gyration Gyration RF Technology Receiver: Found relative axes
[    17.105] (II) Gyration Gyration RF Technology Receiver: Found x and y relative axes
[    17.105] (II) Gyration Gyration RF Technology Receiver: Found absolute axes
[    17.105] (II) evdev-grail: failed to open grail, no gesture support
[    17.105] (II) Gyration Gyration RF Technology Receiver: Found keys
[    17.105] (II) Gyration Gyration RF Technology Receiver: Configuring as mouse
[    17.105] (II) Gyration Gyration RF Technology Receiver: Configuring as keyboard
[    17.105] (**) Gyration Gyration RF Technology Receiver: YAxisMapping: buttons 4 and 5
[    17.105] (**) Gyration Gyration RF Technology Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    17.105] (II) XINPUT: Adding extended input device "Gyration Gyration RF Technology Receiver" (type: KEYBOARD)
[    17.105] (**) Option "xkb_rules" "evdev"
[    17.105] (**) Option "xkb_model" "pc105"
[    17.105] (**) Option "xkb_layout" "us"
[    17.105] (II) Gyration Gyration RF Technology Receiver: initialized for relative axes.
[    17.105] (WW) Gyration Gyration RF Technology Receiver: ignoring absolute axes.
[    17.106] (II) config/udev: Adding input device Gyration Gyration RF Technology Receiver (/dev/input/mouse2)
[    17.106] (II) No input driver/identifier specified (ignoring)
[    17.106] (II) config/udev: Adding input device iMON Remote (15c2:ffdc) (/dev/input/event5)
[    17.106] (**) iMON Remote (15c2:ffdc): Applying InputClass "evdev pointer catchall"
[    17.106] (**) iMON Remote (15c2:ffdc): Applying InputClass "evdev keyboard catchall"
[    17.106] (**) iMON Remote (15c2:ffdc): always reports core events
[    17.106] (**) iMON Remote (15c2:ffdc): Device: "/dev/input/event5"
[    17.137] (II) iMON Remote (15c2:ffdc): Found 3 mouse buttons
[    17.137] (II) iMON Remote (15c2:ffdc): Found scroll wheel(s)
[    17.137] (II) iMON Remote (15c2:ffdc): Found relative axes
[    17.137] (II) iMON Remote (15c2:ffdc): Found x and y relative axes
[    17.137] (II) iMON Remote (15c2:ffdc): Found keys
[    17.137] (II) iMON Remote (15c2:ffdc): Configuring as mouse
[    17.137] (II) iMON Remote (15c2:ffdc): Configuring as keyboard
[    17.137] (**) iMON Remote (15c2:ffdc): YAxisMapping: buttons 4 and 5
[    17.137] (**) iMON Remote (15c2:ffdc): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    17.137] (II) XINPUT: Adding extended input device "iMON Remote (15c2:ffdc)" (type: KEYBOARD)
[    17.137] (**) Option "xkb_rules" "evdev"
[    17.137] (**) Option "xkb_model" "pc105"
[    17.137] (**) Option "xkb_layout" "us"
[    17.137] (II) iMON Remote (15c2:ffdc): initialized for relative axes.
[    17.138] (II) config/udev: Adding input device iMON Remote (15c2:ffdc) (/dev/input/mouse1)
[    17.138] (II) No input driver/identifier specified (ignoring)
[    17.144] (II) config/udev: Adding input device Media Center Ed. eHome Infrared Remote Transceiver (1784:0001) (/dev/input/event4)
[    17.144] (**) Media Center Ed. eHome Infrared Remote Transceiver (1784:0001): Applying InputClass "evdev keyboard catchall"
[    17.144] (**) Media Center Ed. eHome Infrared Remote Transceiver (1784:0001): always reports core events
[    17.144] (**) Media Center Ed. eHome Infrared Remote Transceiver (1784:0001): Device: "/dev/input/event4"
[    17.169] (II) Media Center Ed. eHome Infrared Remote Transceiver (1784:0001): Found keys
[    17.169] (II) Media Center Ed. eHome Infrared Remote Transceiver (1784:0001): Configuring as keyboard
[    17.169] (II) XINPUT: Adding extended input device "Media Center Ed. eHome Infrared Remote Transceiver (1784:0001)" (type: KEYBOARD)
[    17.169] (**) Option "xkb_rules" "evdev"
[    17.169] (**) Option "xkb_model" "pc105"
[    17.169] (**) Option "xkb_layout" "us"
```

---

### Post by nickrout on 2011-02-06
> [    16.728] (--) NVIDIA(0): Connected display device(s) on GeForce 8500 GT at PCI:1:0:0
[    16.728] (--) NVIDIA(0):     CRT-0
[    16.728] (--) NVIDIA(0):     SAMSUNG (DFP-1)
[    16.728] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    16.728] (--) NVIDIA(0): SAMSUNG (DFP-1): 165.0 MHz maximum pixel clock
[    16.728] (--) NVIDIA(0): SAMSUNG (DFP-1): Internal Single Link TMDS
[    16.732] (II) NVIDIA(0): Display Device found referenced in MetaMode: CRT-0
[    16.735] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    16.735] (II) NVIDIA(0): Validated modes:
[    16.735] (II) NVIDIA(0):     "CRT:nvidia-auto-select+0+0"
[    16.735] (II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
[    16.765] (WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
[    16.765] (WW) NVIDIA(0):     from CRT-0's EDID.
[    16.765] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    16.765] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    16.765] (--) Depth 24 pixmap format is 32 bpp
[    16.765] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    16.766] (II) NVIDIA(0): Initialized GPU GART.
[    16.774] (II) NVIDIA(0): Setting mode "CRT:nvidia-auto-select+0+0"


Is this really a CRT? (You say it is HD, most HD tvs are not crt).

The TV is not providing EDID info so you will need to find out its horizontal synch and vertical refresh rates and put them in xorg.conf.

---

### Post by davidstoll on 2011-02-06
> **nickrout said:**
> Is this really a CRT? (You say it is HD, most HD tvs are not crt).

The TV is not providing EDID info so you will need to find out its horizontal synch and vertical refresh rates and put them in xorg.conf.

haha, yeah, I have no idea why it says crt.

It's a 42 inch lcd HD 1080p flat screen.

How do I find this info...if my old xorg.conf doesn't make it work, it seems like a driver issue or something else..but I really have no idea.

---

### Post by nickrout on 2011-02-06
> **davidstoll said:**
> haha, yeah, I have no idea why it says crt.

It's a 42 inch lcd HD 1080p flat screen.

How do I find this info...if my old xorg.conf doesn't make it work, it seems like a driver issue or something else..but I really have no idea.

Actually it refers to DFP in subsequent lines, "Digital Flat Panel" so it probably is detecting that right.

Look up your TV manual to see what the h-sync and v-refresh are, then lines in the monitor section of xorg.conf like:

```
HorizSync    30-107
VertRefresh  48-120

```

Then restart X ```
/etc/init.d/gdm restart
```

---

### Post by davidstoll on 2011-02-06
> **nickrout said:**
> Actually it refers to DFP in subsequent lines, "Digital Flat Panel" so it probably is detecting that right.

Look up your TV manual to see what the h-sync and v-refresh are, then lines in the monitor section of xorg.conf like:

```
HorizSync    30-107
VertRefresh  48-120

```

Then restart X ```
/etc/init.d/gdm restart
```


[http://a248.e.akamai.net/pix.crutchfield.com/Manuals/305/305LN40750.PDF](http://a248.e.akamai.net/pix.crutchfield.com/Manuals/305/305LN40750.PDF)

This is all I could find in the manual...
see attached screen shot from manual

This just seems really strange that I have to do all this.  I am very appreciative of you help, but why would I need to do all this when I didn't before...hmmmm

---

### Post by BicyclerBoy on 2011-02-08
You don't need to get those numbers exactly right.
The numbers are used for mode validation which is currently failing due to EDID not reading.
Seems this is coming a more common problem..
 
Place this line into the screen section for CRT-0 in the /etc/X11/xorg.conf file
Option "UseEDID" "FALSE"

(need X server restart)

It is a CRT because it is connected via wired port VGA.
The driver will allow all the standard internal video modes..pick the required mode with nvidia-settings program & save this to xorg.conf.

---

### Post by davidstoll on 2011-02-09
> **BicyclerBoy said:**
> You don't need to get those numbers exactly right.
The numbers are used for mode validation which is currently failing due to EDID not reading.
Seems this is coming a more common problem..
 
Place this line into the screen section for CRT-0 in the /etc/X11/xorg.conf file
Option "UseEDID" "FALSE"

(need X server restart)

It is a CRT because it is connected via wired port VGA.
The driver will allow all the standard internal video modes..pick the required mode with nvidia-settings program & save this to xorg.conf.

I was getting ready to make a go of the suggestions above, but (I guess due in part to a couple of reboots), the resolution all of a sudden just went to full 1080p...huh?

No need to kick a dead horse at this point, but similar issue have happened to me before, so at least I'll have this thread in the future and I can try those things above.

Thanks so much for everyones help!

:)

---

