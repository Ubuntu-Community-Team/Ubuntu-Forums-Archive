---
title: "StartX fails with no errors?"
date: 2011-03-20
forum: Multimedia Software
---

### Post by fowie on 2011-03-20
I'm running XBMCLive, but this appears to be an xorg issue, not an XBMC issue.  Suddenly after a system upgrade I can't get my X server to start.  I dutifully checked the Xorg.0.log but I don't see any errors at all.  It looks as if it should start working, and then it just quits back to TTY7.  I've tried using start xbmc-live and just startx and get the same log either way.  I've reinstalled nvidia-current (my box is a Zotac ZBOX with next-gen Nvidia ION) and installing the 260.19.44 drivers from Nvidia's website, but get the same log either way.  Any help on what to try next would be appreciated.

Xorg.0.log:
```


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux XBMCLive 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:21 UTC 2011 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-30-generic root=UUID=e1a7a600-d076-4c66-a370-54ae5477b5d9 ro quiet splash xbmc=autostart,nodiskmount,setvolume loglevel=0 video=vesafb
Build Date: 10 December 2010  05:53:04PM
xorg-server 2:1.7.6-2ubuntu7.5 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Mar 20 07:41:54 2011
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
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
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(**) Extension "Composite" is disabled
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(--) using VT number 7

(--) PCI:*(0:3:0:0) 10de:0a64:174b:3100 nVidia Corporation GT218 [ION] rev 162, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xce000000/33554432, I/O @ 0x0000ec00/128, BIOS @ 0x????????/524288
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
(II) NVIDIA GLX Module  260.19.44  Sun Feb 27 21:47:21 PST 2011
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
(II) NVIDIA dlloader X Driver  260.19.44  Sun Feb 27 21:31:52 PST 2011
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 03@00:00:0
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
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "HWcursor" "Off"
(**) NVIDIA(0): Option "FlatPanelProperties" "Scaling = Native"
(**) NVIDIA(0): Option "DynamicTwinView" "False"
(**) Mar 20 07:41:54 NVIDIA(0): Enabling RENDER acceleration
(II) Mar 20 07:41:55 NVIDIA(0): NVIDIA GPU ION (GT218) at PCI:3:0:0 (GPU-0)
(--) Mar 20 07:41:55 NVIDIA(0): Memory: 524288 kBytes
(--) Mar 20 07:41:55 NVIDIA(0): VideoBIOS: 70.18.45.00.00
(II) Mar 20 07:41:55 NVIDIA(0): Detected PCI Express Link width: 1X
(--) Mar 20 07:41:55 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Mar 20 07:41:55 NVIDIA(0): Connected display device(s) on ION at PCI:3:0:0
(--) Mar 20 07:41:55 NVIDIA(0):     SHARP HDMI (DFP-0)
(--) Mar 20 07:41:55 NVIDIA(0): SHARP HDMI (DFP-0): 330.0 MHz maximum pixel clock
(--) Mar 20 07:41:55 NVIDIA(0): SHARP HDMI (DFP-0): Internal Dual Link TMDS
(WW) Mar 20 07:41:55 NVIDIA(0): The EDID for SHARP HDMI (DFP-0) contradicts itself: mode
(WW) Mar 20 07:41:55 NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
(WW) Mar 20 07:41:55 NVIDIA(0):     valid VertRefresh range (55.000-76.000 Hz) would exclude
(WW) Mar 20 07:41:55 NVIDIA(0):     this mode's VertRefresh (24.0 Hz); ignoring VertRefresh
(WW) Mar 20 07:41:55 NVIDIA(0):     check for mode "1920x1080".
(WW) Mar 20 07:41:55 NVIDIA(0): The EDID for SHARP HDMI (DFP-0) contradicts itself: mode
(WW) Mar 20 07:41:55 NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
(WW) Mar 20 07:41:55 NVIDIA(0):     valid VertRefresh range (55.000-76.000 Hz) would exclude
(WW) Mar 20 07:41:55 NVIDIA(0):     this mode's VertRefresh (24.0 Hz); ignoring VertRefresh
(WW) Mar 20 07:41:55 NVIDIA(0):     check for mode "1920x1080".
(II) Mar 20 07:41:55 NVIDIA(0): Assigned Display Device: DFP-0
(==) Mar 20 07:41:55 NVIDIA(0): 
(==) Mar 20 07:41:55 NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) Mar 20 07:41:55 NVIDIA(0):     will be used as the requested mode.
(==) Mar 20 07:41:55 NVIDIA(0): 
(II) Mar 20 07:41:55 NVIDIA(0): Validated modes:
(II) Mar 20 07:41:55 NVIDIA(0):     "nvidia-auto-select"
(II) Mar 20 07:41:55 NVIDIA(0): Virtual screen size determined to be 1920 x 1080
(--) Mar 20 07:41:55 NVIDIA(0): DPI set to (59, 59); computed from "UseEdidDpi" X config
(--) Mar 20 07:41:55 NVIDIA(0):     option
(==) Mar 20 07:41:55 NVIDIA(0): Disabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) Mar 20 07:41:55 NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
(II) Mar 20 07:41:55 NVIDIA(0): Initialized GPU GART.
(II) Mar 20 07:41:55 NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) Mar 20 07:41:55 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Mar 20 07:41:55 NVIDIA(0): Initialized X Rendering Acceleration
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
(II) XKB: reuse xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
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
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event5)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device   USB Keyboard (/dev/input/event3)
(**)   USB Keyboard: Applying InputClass "evdev keyboard catchall"
(**)   USB Keyboard: always reports core events
(**)   USB Keyboard: Device: "/dev/input/event3"
(II)   USB Keyboard: Found keys
(II)   USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device   USB Keyboard (/dev/input/event4)
(**)   USB Keyboard: Applying InputClass "evdev keyboard catchall"
(**)   USB Keyboard: always reports core events
(**)   USB Keyboard: Device: "/dev/input/event4"
(II)   USB Keyboard: Found keys
(II)   USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD)
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
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II)   USB Keyboard: Close
(II) UnloadModule: "evdev"
(II)   USB Keyboard: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
 ddxSigGiveUp: Closing log

```

A little more info.  xinit will run ok, and give me the little white box (I think it's an xterm, but I can't see the top left corner to tell for sure).  But startx just crashes?

---

### Post by fowie on 2011-03-20
Well, solved it myself.  Actually it was an xbmc problem.  Even running startx will execute your $HOME/.xsession file, which was running /usr/bin/xbmc --standalone, and that's what was crashing.  FYI, don't move the .xbmc/userdata folder somewhere (say, a removable drive) that isn't mounted before xbmc starts, or you'll get some major problems like this.

---

