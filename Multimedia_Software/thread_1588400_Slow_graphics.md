---
title: "Slow graphics"
date: 2010-10-04
forum: Multimedia Software
---

### Post by Eragon0605 on 2010-10-04
I have always noticed that when moving windows around, the motion is jerky, effects or no effects enabled. I always thought that that was just how Ubuntu works. Then I got a laptop. It is a cheap $300 thing, and the Windows 7 that came on it was just too slow. I installed Ubuntu 10.04 on it. After installing the proprietary ATI drivers, I noticed something right away. I could turn up the window graphics all the way and it was perfectly smooth. Also, 2D games, which were jerky on my other computer, ran perfectly smoothly on my laptop. My other computer I built myself and have put over $1,500 USD into it. When I run a 3D application on it, Windows or Linux, I have never had any performance issues (only some very new games on Windows run slow if I turn the graphics up all the way). This puzzles me. Why are my 2D graphics in Linux slow? I don't think it's anything hardware-related, as the 3D games run amazingly well. I have tried everything in the NV control panel from over clocking my 2D clock to changing every setting in almost every single combination (I went at it for 3 hours once 0_o). My desktop has an nVidia GTX 260. I have am using the latest proprietary drivers from the nVidia site.

---

### Post by Eragon0605 on 2010-10-05
Bump.

---

### Post by utnubuuser on 2010-10-05
Have you enabled compositing in gconf?

Alt+F2, then type gconf-editor, then scroll to apps, metacity, general, and make sure compositing_manager is enabled
Most desktop apps nowadays require compositing to be enabled in one form or another.

Other than that, it's probably a matter of setting up your driver properly. For that I'd suggest posting the info for it, then wait for someone who has some familiarity with driver/xorg configuration experience.

> lspci -l

---

### Post by .... on 2010-10-05
Which computer are you asking about? Give details on the system you are asking about. We don't care about your other systems....
Post /var/log/Xorg.0.log from the system in question

---

### Post by Eragon0605 on 2010-10-06
Compositing manager wasn't on, but enabling it doesn't help. I am talking about my $1500 computer. Here is my Xorg.0.log file:

```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux dck-desktop 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:26:08 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-25-generic root=UUID=439b4858-aa97-41f9-911d-2017797c141f ro quiet splash
Build Date: 21 July 2010  12:47:34PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct  6 14:03:20 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:05e2:1682:2393 nVidia Corporation GT200 [GeForce GTX 260] rev 161, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000ec00/128, BIOS @ 0x????????/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  256.53  Fri Aug 27 21:28:41 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  256.53  Fri Aug 27 21:05:55 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "1440x900_60 +0+0"
(**) Oct 06 14:03:20 NVIDIA(0): Enabling RENDER acceleration
(II) Oct 06 14:03:20 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Oct 06 14:03:20 NVIDIA(0):     enabled.
(II) Oct 06 14:03:21 NVIDIA(0): NVIDIA GPU GeForce GTX 260 (GT200) at PCI:1:0:0 (GPU-0)
(--) Oct 06 14:03:21 NVIDIA(0): Memory: 917504 kBytes
(--) Oct 06 14:03:21 NVIDIA(0): VideoBIOS: 62.00.50.00.50
(II) Oct 06 14:03:21 NVIDIA(0): Detected PCI Express Link width: 16X
(--) Oct 06 14:03:21 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Oct 06 14:03:21 NVIDIA(0): Connected display device(s) on GeForce GTX 260 at PCI:1:0:0:
(--) Oct 06 14:03:21 NVIDIA(0):     ACI ASUS VH198 (DFP-1)
(--) Oct 06 14:03:21 NVIDIA(0): ACI ASUS VH198 (DFP-1): 330.0 MHz maximum pixel clock
(--) Oct 06 14:03:21 NVIDIA(0): ACI ASUS VH198 (DFP-1): Internal Dual Link TMDS
(II) Oct 06 14:03:22 NVIDIA(0): Assigned Display Device: DFP-1
(II) Oct 06 14:03:22 NVIDIA(0): Validated modes:
(II) Oct 06 14:03:22 NVIDIA(0):     "1440x900_60+0+0"
(II) Oct 06 14:03:22 NVIDIA(0): Virtual screen size determined to be 1440 x 900
(--) Oct 06 14:03:22 NVIDIA(0): DPI set to (89, 87); computed from "UseEdidDpi" X config
(--) Oct 06 14:03:22 NVIDIA(0):     option
(==) Oct 06 14:03:22 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) Oct 06 14:03:22 NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
(II) Oct 06 14:03:22 NVIDIA(0): Initialized GPU GART.
(II) Oct 06 14:03:22 NVIDIA(0): Setting mode "1440x900_60+0+0"
(II) Loading extension NV-GLX
(II) Oct 06 14:03:22 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Oct 06 14:03:22 NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
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
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Microsoft Microsoft Optical Mouse with Tilt Wheel (/dev/input/event4)
(**) Microsoft Microsoft Optical Mouse with Tilt Wheel: Applying InputClass "evdev pointer catchall"
(**) Microsoft Microsoft Optical Mouse with Tilt Wheel: always reports core events
(**) Microsoft Microsoft Optical Mouse with Tilt Wheel: Device: "/dev/input/event4"
(II) Microsoft Microsoft Optical Mouse with Tilt Wheel: Found 9 mouse buttons
(II) Microsoft Microsoft Optical Mouse with Tilt Wheel: Found scroll wheel(s)
(II) Microsoft Microsoft Optical Mouse with Tilt Wheel: Found relative axes
(II) Microsoft Microsoft Optical Mouse with Tilt Wheel: Found x and y relative axes
(II) Microsoft Microsoft Optical Mouse with Tilt Wheel: Configuring as mouse
(**) Microsoft Microsoft Optical Mouse with Tilt Wheel: YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft Optical Mouse with Tilt Wheel: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Microsoft Optical Mouse with Tilt Wheel" (type: MOUSE)
(II) Microsoft Microsoft Optical Mouse with Tilt Wheel: initialized for relative axes.
(II) config/udev: Adding input device Microsoft Microsoft Optical Mouse with Tilt Wheel (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
```

---

### Post by Eragon0605 on 2010-10-07
bump.

---

