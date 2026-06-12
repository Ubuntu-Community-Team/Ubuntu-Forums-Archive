---
title: "[Lucid] Nvidia Driver issue with upgrade"
date: 2010-05-06
forum: Multimedia Software
---

### Post by richardsonh on 2010-05-06
Good Evening collective conscious,

I have been struck with a strange issue, and I can't seem to fix it. 

I was running 9.10, with 3 monitors, using the nvidia drivers, and it was a champ. I decided tonight that I was going to attempt an upgrade to Lucid, and it went remarkable smooth. Minus a little issue with the 3 monitor setup.

The center and right monitor work like a champ, while the left monitor works, it's not usable. The mouse will go from the far right monitor to the center monitor without issue, however when I try to go from the center monitor to the left monitor, you can see the mouse flap back and forth between the two monitors, and as soon as you hit a key on the keyboard, X dies, and starts back up. I am using the exact same xorg config settings as I was before, and nothing has changed, besides the backup. 

I am going to include my lspci, xorg conf, and the xorg log. If anyone has any ideas I would really appreciate it.

Xorg Log

```
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux ubuntu 2.6.32-22-generic-pae #33-Ubuntu SMP Wed Apr 28 14:57:29 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic-pae root=/dev/sda1 loop=/ubuntu/disks/root.disk ro quiet splash
Build Date: 23 April 2010  05:11:50PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu May  6 02:23:05 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Device1"
(**) |-->Screen "Screen2" (2)
(**) |   |-->Monitor "Monitor2"
(**) |   |-->Device "Device2"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "1"
(==) Automatically adding devices
(==) Automatically enabling devices
(**) Xinerama: enabled
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
(--) using VT number 8

(--) PCI: (0:1:0:0) 10de:06e0:10de:060c nVidia Corporation G98 [GeForce 9300 GE] rev 161, Mem @ 0xfc000000/16777216, 0xc0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000dc80/128, BIOS @ 0x????????/131072
(--) PCI:*(0:5:0:0) 10de:06e4:196e:05cf nVidia Corporation G98 [GeForce 8400 GS] rev 161, Mem @ 0xf8000000/16777216, 0xd0000000/268435456, 0xf6000000/33554432, I/O @ 0x0000cc80/128, BIOS @ 0x????????/131072
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
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.15  Thu Mar 11 23:39:48 PST 2010
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
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.15  Thu Mar 11 22:01:49 PST 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 05@00:00:0
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
(**) NVIDIA(0): Option "MetaModes" "nvidia-auto-select +0+0"
(**) May 06 02:23:05 NVIDIA(0): Enabling RENDER acceleration
(II) May 06 02:23:05 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) May 06 02:23:05 NVIDIA(0):     enabled.
(II) May 06 02:23:05 NVIDIA(0): NVIDIA GPU GeForce 8400 GS (G98) at PCI:5:0:0 (GPU-0)
(--) May 06 02:23:05 NVIDIA(0): Memory: 524288 kBytes
(--) May 06 02:23:05 NVIDIA(0): VideoBIOS: 62.98.20.00.51
(II) May 06 02:23:05 NVIDIA(0): Detected PCI Express Link width: 1X
(--) May 06 02:23:05 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) May 06 02:23:05 NVIDIA(0): Connected display device(s) on GeForce 8400 GS at PCI:5:0:0:
(--) May 06 02:23:05 NVIDIA(0):     DELL S2309W (DFP-0)
(--) May 06 02:23:05 NVIDIA(0): DELL S2309W (DFP-0): 330.0 MHz maximum pixel clock
(--) May 06 02:23:05 NVIDIA(0): DELL S2309W (DFP-0): Internal Dual Link TMDS
(II) May 06 02:23:06 NVIDIA(0): Assigned Display Device: DFP-0
(II) May 06 02:23:06 NVIDIA(0): Validated modes:
(II) May 06 02:23:06 NVIDIA(0):     "nvidia-auto-select+0+0"
(II) May 06 02:23:06 NVIDIA(0): Virtual screen size determined to be 1920 x 1080
(--) May 06 02:23:06 NVIDIA(0): DPI set to (95, 94); computed from "UseEdidDpi" X config
(--) May 06 02:23:06 NVIDIA(0):     option
(==) May 06 02:23:06 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "TwinView" "0"
(**) NVIDIA(1): Option "MetaModes" "CRT-0: nvidia-auto-select +0+0"
(**) NVIDIA(1): Option "TwinViewXineramaInfoOrder" "CRT-0"
(**) May 06 02:23:06 NVIDIA(1): Enabling RENDER acceleration
(II) May 06 02:23:06 NVIDIA(1): NVIDIA GPU GeForce 9300 GE (G98) at PCI:1:0:0 (GPU-1)
(--) May 06 02:23:06 NVIDIA(1): Memory: 524288 kBytes
(--) May 06 02:23:06 NVIDIA(1): VideoBIOS: 62.98.42.00.06
(II) May 06 02:23:06 NVIDIA(1): Detected PCI Express Link width: 16X
(--) May 06 02:23:06 NVIDIA(1): Interlaced video modes are supported on this GPU
(--) May 06 02:23:06 NVIDIA(1): Connected display device(s) on GeForce 9300 GE at PCI:1:0:0:
(--) May 06 02:23:06 NVIDIA(1):     DELL E177FP (CRT-0)
(--) May 06 02:23:06 NVIDIA(1):     Proview (CRT-1)
(--) May 06 02:23:06 NVIDIA(1): DELL E177FP (CRT-0): 400.0 MHz maximum pixel clock
(--) May 06 02:23:06 NVIDIA(1): Proview (CRT-1): 400.0 MHz maximum pixel clock
(II) May 06 02:23:06 NVIDIA(1): Display Device found referenced in MetaMode: CRT-0
(II) May 06 02:23:06 NVIDIA(1): Assigned Display Device: CRT-0
(II) May 06 02:23:06 NVIDIA(1): Validated modes:
(II) May 06 02:23:06 NVIDIA(1):     "CRT-0:nvidia-auto-select+0+0"
(II) May 06 02:23:06 NVIDIA(1): Virtual screen size determined to be 1280 x 1024
(--) May 06 02:23:06 NVIDIA(1): DPI set to (95, 96); computed from "UseEdidDpi" X config
(--) May 06 02:23:06 NVIDIA(1):     option
(==) May 06 02:23:06 NVIDIA(1): Enabling 32-bit ARGB GLX visuals.
(**) NVIDIA(2): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(2): RGB weight 888
(==) NVIDIA(2): Default visual is TrueColor
(==) NVIDIA(2): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(2): Option "TwinView" "0"
(**) NVIDIA(2): Option "MetaModes" "CRT-1: nvidia-auto-select +0+0"
(**) May 06 02:23:06 NVIDIA(2): Enabling RENDER acceleration
(II) May 06 02:23:06 NVIDIA(2): NVIDIA GPU GeForce 9300 GE (G98) at PCI:1:0:0 (GPU-1)
(--) May 06 02:23:06 NVIDIA(2): Memory: 524288 kBytes
(--) May 06 02:23:06 NVIDIA(2): VideoBIOS: 62.98.42.00.06
(II) May 06 02:23:06 NVIDIA(2): Detected PCI Express Link width: 16X
(--) May 06 02:23:06 NVIDIA(2): Interlaced video modes are supported on this GPU
(--) May 06 02:23:06 NVIDIA(2): Connected display device(s) on GeForce 9300 GE at PCI:1:0:0:
(--) May 06 02:23:06 NVIDIA(2):     DELL E177FP (CRT-0)
(--) May 06 02:23:06 NVIDIA(2):     Proview (CRT-1)
(--) May 06 02:23:06 NVIDIA(2): DELL E177FP (CRT-0): 400.0 MHz maximum pixel clock
(--) May 06 02:23:06 NVIDIA(2): Proview (CRT-1): 400.0 MHz maximum pixel clock
(II) May 06 02:23:06 NVIDIA(2): Display Device found referenced in MetaMode: CRT-1
(WW) May 06 02:23:06 NVIDIA(2): The EDID for Proview (CRT-1) contradicts itself: mode
(WW) May 06 02:23:06 NVIDIA(2):     "800x600" is specified in the EDID; however, the EDID's
(WW) May 06 02:23:06 NVIDIA(2):     valid VertRefresh range (60.000-75.000 Hz) would exclude
(WW) May 06 02:23:06 NVIDIA(2):     this mode's VertRefresh (56.2 Hz); ignoring VertRefresh
(WW) May 06 02:23:06 NVIDIA(2):     check for mode "800x600".
(II) May 06 02:23:06 NVIDIA(2): Assigned Display Device: CRT-1
(II) May 06 02:23:06 NVIDIA(2): Validated modes:
(II) May 06 02:23:06 NVIDIA(2):     "CRT-1:nvidia-auto-select+0+0"
(II) May 06 02:23:06 NVIDIA(2): Virtual screen size determined to be 1280 x 1024
(--) May 06 02:23:06 NVIDIA(2): DPI set to (95, 96); computed from "UseEdidDpi" X config
(--) May 06 02:23:06 NVIDIA(2):     option
(==) May 06 02:23:06 NVIDIA(2): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) May 06 02:23:06 NVIDIA: Using 768.00 MB of virtual memory for indirect framebuffer
(II) May 06 02:23:06 NVIDIA:     access.
(II) May 06 02:23:06 NVIDIA(0): Initialized GPU GART.
(II) May 06 02:23:06 NVIDIA(0): Setting mode "nvidia-auto-select+0+0"
(II) Loading extension NV-GLX
(II) May 06 02:23:06 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) May 06 02:23:06 NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) May 06 02:23:06 NVIDIA(1): Initialized GPU GART.
(II) May 06 02:23:06 NVIDIA(1): Setting mode "CRT-0:nvidia-auto-select+0+0"
(II) May 06 02:23:06 NVIDIA(1): Initialized OpenGL Acceleration
(==) NVIDIA(1): Disabling shared memory pixmaps
(II) May 06 02:23:06 NVIDIA(1): Initialized X Rendering Acceleration
(==) NVIDIA(1): Backing store disabled
(==) NVIDIA(1): Silken mouse enabled
(==) NVIDIA(1): DPMS enabled
(==) RandR enabled
(II) May 06 02:23:06 NVIDIA(2): Initialized GPU GART.
(II) May 06 02:23:06 NVIDIA(2): Setting mode "CRT-1:nvidia-auto-select+0+0"
(II) May 06 02:23:07 NVIDIA(2): Initialized OpenGL Acceleration
(==) NVIDIA(2): Disabling shared memory pixmaps
(II) May 06 02:23:07 NVIDIA(2): Initialized X Rendering Acceleration
(==) NVIDIA(2): Backing store disabled
(==) NVIDIA(2): Silken mouse enabled
(==) NVIDIA(2): DPMS enabled
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
(II) config/udev: Adding input device Microsoft Comfort Curve Keyboard 2000 (/dev/input/event3)
(**) Microsoft Comfort Curve Keyboard 2000: Applying InputClass "evdev keyboard catchall"
(**) Microsoft Comfort Curve Keyboard 2000: always reports core events
(**) Microsoft Comfort Curve Keyboard 2000: Device: "/dev/input/event3"
(II) Microsoft Comfort Curve Keyboard 2000: Found keys
(II) Microsoft Comfort Curve Keyboard 2000: Configuring as keyboard
(II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 2000" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Microsoft Comfort Curve Keyboard 2000 (/dev/input/event4)
(**) Microsoft Comfort Curve Keyboard 2000: Applying InputClass "evdev keyboard catchall"
(**) Microsoft Comfort Curve Keyboard 2000: always reports core events
(**) Microsoft Comfort Curve Keyboard 2000: Device: "/dev/input/event4"
(II) Microsoft Comfort Curve Keyboard 2000: Found 1 mouse buttons
(II) Microsoft Comfort Curve Keyboard 2000: Found scroll wheel(s)
(II) Microsoft Comfort Curve Keyboard 2000: Found relative axes
(II) Microsoft Comfort Curve Keyboard 2000: Found absolute axes
(II) Microsoft Comfort Curve Keyboard 2000: Found keys
(II) Microsoft Comfort Curve Keyboard 2000: Configuring as mouse
(II) Microsoft Comfort Curve Keyboard 2000: Configuring as keyboard
(**) Microsoft Comfort Curve Keyboard 2000: YAxisMapping: buttons 4 and 5
(**) Microsoft Comfort Curve Keyboard 2000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 2000" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(EE) Microsoft Comfort Curve Keyboard 2000: failed to initialize for relative axes.
(II) Microsoft Comfort Curve Keyboard 2000: initialized for absolute axes.
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event5)
(**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event5"
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event6)
(**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
(**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event6"
(II) Logitech USB Receiver: Found 12 mouse buttons
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found relative axes
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found absolute axes
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as mouse
(II) Logitech USB Receiver: Configuring as keyboard
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) Logitech USB Receiver: initialized for relative axes.
(WW) Logitech USB Receiver: ignoring absolute axes.
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event7)
(II) No input driver/identifier specified (ignoring)
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


LSPCI


```
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:03.0 Communication controller: Intel Corporation 4 Series Chipset HECI Controller (rev 03)
00:03.2 IDE interface: Intel Corporation 4 Series Chipset PT IDER Controller (rev 03)
00:03.3 Serial controller: Intel Corporation 4 Series Chipset Serial KT Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82567LM-3 Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a2)
00:1f.0 ISA bridge: Intel Corporation 82801JD (ICH10D) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801JD/DO (ICH10 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 9300 GE] (rev a1)
04:02.0 PCI bridge: PLX Technology, Inc. PEX8112 x1 Lane PCI Express-to-PCI Bridge (rev aa)
05:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)
```


Xorg.conf

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Fri Apr  9 10:35:18 UTC 2010

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Fri Aug 14 17:54:58 PDT 2009
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice"
#
#    # generated from default
#    Identifier     "Mouse0"
#    Driver         "mouse"
#    Option         "Protocol" "auto"
#    Option         "Device" "/dev/psaux"
#    Option         "Emulate3Buttons" "no"
#    Option         "ZAxisMapping" "4 5"
#EndSection
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice"
#
#    # generated from default
#    Identifier     "Keyboard0"
#    Driver         "kbd"
#EndSection

Section "ServerLayout"

# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#    InputDevice    "Keyboard0" "CoreKeyboard"
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#    InputDevice    "Mouse0" "CorePointer"
    Identifier     "Layout0"
    Screen      0  "Screen0" RightOf "Screen1"
    Screen      1  "Screen1" 0 0
    Screen      2  "Screen2" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "1"
EndSection

Section "Files"
EndSection

Section "ServerFlags"

# Removed Option "Xinerama" "0"
    Option         "Xinerama" "1"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL S2309W"
    HorizSync       30.0 - 83.0
    VertRefresh     50.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DELL E177FP"
    HorizSync       31.0 - 80.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "Proview"
    HorizSync       30.0 - 80.0
    VertRefresh     60.0 - 75.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:5:0:0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9300 GE"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9300 GE"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Device2"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by richardsonh on 2010-05-07
I just got back into work, and attempted a driver downgrade but without much luck. Does anyone have any ideas?

Harry

---

### Post by johansson.seb on 2010-05-08
Yes, this bug is a pain in the...

Have a look at [Bug #563100]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/563100").

> According to the Xorg people working with the bug, in Xinerama mode - event coordinates are relative to the primary secreen - Screen 0. But, in the version of Xorg that now is in use with Lucid (1.7.6) event coordinates are unsigned integers.

With unsigned integers, negative coordinates can not be represented, thus xorg can not function with screens above or to the left of Screen 0. So, if you can, let your upper-left screen be Screen 0.

The xorg people have a patch that seems to be working (simply changing back to signed ints). I hope that this will make it into an updated ubuntu Lucid package soon.

> As Daniel Dadap wrote, this seems to correspond to the Xorg bug:
[https://bugs.freedesktop.org/show_bug.cgi?id=24986](https://bugs.freedesktop.org/show_bug.cgi?id=24986)

---

### Post by richardsonh on 2010-05-11
Thank you so much, that answers the questions.

Harry Richardson

---

