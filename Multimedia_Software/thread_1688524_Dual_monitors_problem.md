---
title: "Dual monitors problem"
date: 2011-02-15
forum: Multimedia Software
---

### Post by coldcut on 2011-02-15
Hi boys and girls

I have a tiny problem with my dula-monitor setup.
My main monitor is a 24" Samsung Syncmaster (1920x1080) and my plan was to use my TV(32" Samsung LCD - 1366*768) as an extra monitor to watch movies/shows etc.
I have never tried/had to configure these settings before and I would really appreciate your help.
I have been trying to get it to work with configuring nVidia X server settings but I never get a signal on the TV.

I've tried enabling/disabling Xinerama but that doesn't make any difference. Also the computer sees my TV as 1280x720 but not 1266x768, should I worry about that or can I change that with changing "panning"?
I'll leave you with two screenshot of the NVIDIA X Server Settings for the TV.

Hope you can help a X Server noob :)

---

### Post by coldcut on 2011-02-17
Any ideas penguins?

---

### Post by BicyclerBoy on 2011-02-18
Are you connected by VGA?
VGA is limited to std video modes (& non-native ones) in most TVs.
1280x720 is a std video mode.

Generally the best DFP TV connection is over HDMI/DVI-D.
Your TV may need to be in PC input mode or direct pixel mapping, just-scan, no overscan.

Post your
/var/log/Xorg.0.log
file..

---

### Post by janthonywj on 2011-02-18
I'm not completely sure about conflicts with Nvidia X server software (I'm pretty much a noob) because I had an Intel card when I was dealing with a similar issue, but you can use the xrandr command to fix the problems with the wrong resolution settings being detected. 

You usually need to calculate a modeline or find the proper modeline from the manuals in your product if they are given. I used to have a Samsung 1680x1050 TV where the resolutions detected were much less or different than that so I had to figure out the compatible modeline (which I found from a dell monitor) and create a small script to set the proper display resolution upon boot. It worked like a charm and I think it will solve your issue. There are plenty of resources on how to use xrandr to get what you want from the command line. 

I also found out that sometimes the modes are not detected properly due to the actual VGA cable you are using (assuming this is how you are connected). I was using the cheapest cable I could find at the time, and later I used a nicer cable from another monitor and the monitor was detected correctly.

---

### Post by coldcut on 2011-02-19
Well I'm connecting my TV with HDMI. The strange thing is that my TV-"box" (tv over ethernet) is also only 1280x720.

But here is my /var/log/Xorg.0.log (damn it's long!)

```
cat /var/log/Xorg.0.log
[     7.227] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[     7.227] X Protocol Version 11, Revision 0
[     7.227] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[     7.227] Current Operating System: Linux UNIX-78 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64
[     7.227] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-25-generic root=UUID=7aa1a22d-49b1-4a93-ade7-22f7bc54fe58 ro quiet splash
[     7.227] Build Date: 09 January 2011  12:14:27PM
[     7.227] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
[     7.227] Current version of pixman: 0.18.4
[     7.227] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[     7.227] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     7.227] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Feb 17 00:32:46 2011
[     7.227] (==) Using config file: "/etc/X11/xorg.conf"
[     7.227] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     7.228] (==) No Layout section.  Using the first Screen section.
[     7.228] (**) |-->Screen "Default Screen" (0)
[     7.228] (**) |   |-->Monitor "<default monitor>"
[     7.228] (==) No device specified for screen "Default Screen".
	Using the first device section listed.
[     7.228] (**) |   |-->Device "Default Device"
[     7.228] (==) No monitor specified for screen "Default Screen".
	Using a default monitor configuration.
[     7.228] (==) Automatically adding devices
[     7.228] (==) Automatically enabling devices
[     7.228] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     7.228] 	Entry deleted from font path.
[     7.228] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[     7.228] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     7.228] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[     7.228] (II) Loader magic: 0x7d17a0
[     7.228] (II) Module ABI versions:
[     7.228] 	X.Org ANSI C Emulation: 0.4
[     7.228] 	X.Org Video Driver: 8.0
[     7.228] 	X.Org XInput driver : 11.0
[     7.228] 	X.Org Server Extension : 4.0
[     7.229] (--) PCI:*(0:1:0:0) 10de:0613:0000:0000 rev 162, Mem @ 0xf8000000/16777216, 0xe0000000/268435456, 0xf6000000/33554432, I/O @ 0x0000ef00/128, BIOS @ 0x????????/131072
[     7.229] (II) Open ACPI successful (/var/run/acpid.socket)
[     7.229] (II) "extmod" will be loaded by default.
[     7.229] (II) "dbe" will be loaded by default.
[     7.229] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[     7.229] (II) "record" will be loaded by default.
[     7.229] (II) "dri" will be loaded by default.
[     7.229] (II) "dri2" will be loaded by default.
[     7.229] (II) LoadModule: "glx"
[     7.229] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[     7.236] (II) Module glx: vendor="NVIDIA Corporation"
[     7.236] 	compiled for 4.0.2, module version = 1.0.0
[     7.236] 	Module class: X.Org Server Extension
[     7.236] (II) NVIDIA GLX Module  260.19.06  Mon Sep 13 04:54:41 PDT 2010
[     7.236] (II) Loading extension GLX
[     7.236] (II) LoadModule: "extmod"
[     7.236] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[     7.236] (II) Module extmod: vendor="X.Org Foundation"
[     7.236] 	compiled for 1.9.0, module version = 1.0.0
[     7.236] 	Module class: X.Org Server Extension
[     7.236] 	ABI class: X.Org Server Extension, version 4.0
[     7.236] (II) Loading extension MIT-SCREEN-SAVER
[     7.236] (II) Loading extension XFree86-VidModeExtension
[     7.236] (II) Loading extension XFree86-DGA
[     7.236] (II) Loading extension DPMS
[     7.236] (II) Loading extension XVideo
[     7.236] (II) Loading extension XVideo-MotionCompensation
[     7.236] (II) Loading extension X-Resource
[     7.236] (II) LoadModule: "dbe"
[     7.237] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[     7.237] (II) Module dbe: vendor="X.Org Foundation"
[     7.237] 	compiled for 1.9.0, module version = 1.0.0
[     7.237] 	Module class: X.Org Server Extension
[     7.237] 	ABI class: X.Org Server Extension, version 4.0
[     7.237] (II) Loading extension DOUBLE-BUFFER
[     7.237] (II) LoadModule: "record"
[     7.237] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[     7.237] (II) Module record: vendor="X.Org Foundation"
[     7.237] 	compiled for 1.9.0, module version = 1.13.0
[     7.237] 	Module class: X.Org Server Extension
[     7.237] 	ABI class: X.Org Server Extension, version 4.0
[     7.237] (II) Loading extension RECORD
[     7.237] (II) LoadModule: "dri"
[     7.237] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[     7.237] (II) Module dri: vendor="X.Org Foundation"
[     7.237] 	compiled for 1.9.0, module version = 1.0.0
[     7.237] 	ABI class: X.Org Server Extension, version 4.0
[     7.237] (II) Loading extension XFree86-DRI
[     7.237] (II) LoadModule: "dri2"
[     7.237] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     7.237] (II) Module dri2: vendor="X.Org Foundation"
[     7.238] 	compiled for 1.9.0, module version = 1.2.0
[     7.238] 	ABI class: X.Org Server Extension, version 4.0
[     7.238] (II) Loading extension DRI2
[     7.238] (II) LoadModule: "nvidia"
[     7.238] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[     7.238] (II) Module nvidia: vendor="NVIDIA Corporation"
[     7.238] 	compiled for 4.0.2, module version = 1.0.0
[     7.238] 	Module class: X.Org Video Driver
[     7.238] (II) NVIDIA dlloader X Driver  260.19.06  Mon Sep 13 04:31:43 PDT 2010
[     7.238] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     7.238] (++) using VT number 7

[     7.239] (II) Loading sub module "fb"
[     7.239] (II) LoadModule: "fb"
[     7.240] (II) Loading /usr/lib/xorg/modules/libfb.so
[     7.240] (II) Module fb: vendor="X.Org Foundation"
[     7.240] 	compiled for 1.9.0, module version = 1.0.0
[     7.240] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     7.240] (II) Loading sub module "wfb"
[     7.240] (II) LoadModule: "wfb"
[     7.240] (II) Loading /usr/lib/xorg/modules/libwfb.so
[     7.240] (II) Module wfb: vendor="X.Org Foundation"
[     7.240] 	compiled for 1.9.0, module version = 1.0.0
[     7.240] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     7.240] (II) Loading sub module "ramdac"
[     7.240] (II) LoadModule: "ramdac"
[     7.240] (II) Module "ramdac" already built-in
[     7.240] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
[     7.240] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[     7.240] (==) NVIDIA(0): RGB weight 888
[     7.240] (==) NVIDIA(0): Default visual is TrueColor
[     7.240] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[     7.240] (**) NVIDIA(0): Option "NoLogo" "True"
[     7.241] (**) NVIDIA(0): Enabling RENDER acceleration
[     7.241] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[     7.241] (II) NVIDIA(0):     enabled.
[     8.072] (II) NVIDIA(0): NVIDIA GPU GeForce 9800 GTX+ (G92) at PCI:1:0:0 (GPU-0)
[     8.072] (--) NVIDIA(0): Memory: 524288 kBytes
[     8.072] (--) NVIDIA(0): VideoBIOS: 62.92.62.00.07
[     8.072] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[     8.072] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[     8.072] (--) NVIDIA(0): Connected display device(s) on GeForce 9800 GTX+ at PCI:1:0:0
[     8.072] (--) NVIDIA(0):     Samsung SyncMaster (DFP-0)
[     8.072] (--) NVIDIA(0): Samsung SyncMaster (DFP-0): 330.0 MHz maximum pixel clock
[     8.072] (--) NVIDIA(0): Samsung SyncMaster (DFP-0): Internal Dual Link TMDS
[     8.130] (II) NVIDIA(0): Assigned Display Device: DFP-0
[     8.130] (==) NVIDIA(0): 
[     8.130] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[     8.130] (==) NVIDIA(0):     will be used as the requested mode.
[     8.130] (==) NVIDIA(0): 
[     8.130] (II) NVIDIA(0): Validated modes:
[     8.130] (II) NVIDIA(0):     "nvidia-auto-select"
[     8.130] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[     8.153] (--) NVIDIA(0): DPI set to (92, 91); computed from "UseEdidDpi" X config
[     8.154] (--) NVIDIA(0):     option
[     8.154] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[     8.154] (--) Depth 24 pixmap format is 32 bpp
[     8.154] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[     8.155] (II) NVIDIA(0): Initialized GPU GART.
[     8.161] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[     8.181] (II) Loading extension NV-GLX
[     8.206] (II) NVIDIA(0): Initialized OpenGL Acceleration
[     8.226] (==) NVIDIA(0): Disabling shared memory pixmaps
[     8.226] (II) NVIDIA(0): Initialized X Rendering Acceleration
[     8.226] (==) NVIDIA(0): Backing store disabled
[     8.226] (==) NVIDIA(0): Silken mouse enabled
[     8.229] (==) NVIDIA(0): DPMS enabled
[     8.229] (II) Loading extension NV-CONTROL
[     8.229] (II) Loading extension XINERAMA
[     8.229] (II) Loading sub module "dri2"
[     8.229] (II) LoadModule: "dri2"
[     8.229] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[     8.229] (II) NVIDIA(0): [DRI2] Setup complete
[     8.229] (==) RandR enabled
[     8.229] (II) Initializing built-in extension Generic Event Extension
[     8.229] (II) Initializing built-in extension SHAPE
[     8.229] (II) Initializing built-in extension MIT-SHM
[     8.229] (II) Initializing built-in extension XInputExtension
[     8.229] (II) Initializing built-in extension XTEST
[     8.229] (II) Initializing built-in extension BIG-REQUESTS
[     8.229] (II) Initializing built-in extension SYNC
[     8.229] (II) Initializing built-in extension XKEYBOARD
[     8.229] (II) Initializing built-in extension XC-MISC
[     8.229] (II) Initializing built-in extension SECURITY
[     8.229] (II) Initializing built-in extension XINERAMA
[     8.229] (II) Initializing built-in extension XFIXES
[     8.229] (II) Initializing built-in extension RENDER
[     8.229] (II) Initializing built-in extension RANDR
[     8.229] (II) Initializing built-in extension COMPOSITE
[     8.229] (II) Initializing built-in extension DAMAGE
[     8.229] (II) Initializing built-in extension GESTURE
[     8.229] (II) Initializing extension GLX
[     8.267] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     8.271] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     8.271] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     8.271] (II) LoadModule: "evdev"
[     8.272] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     8.272] (II) Module evdev: vendor="X.Org Foundation"
[     8.272] 	compiled for 1.9.0, module version = 2.3.2
[     8.272] 	Module class: X.Org XInput Driver
[     8.272] 	ABI class: X.Org XInput driver, version 11.0
[     8.272] (**) Power Button: always reports core events
[     8.272] (**) Power Button: Device: "/dev/input/event1"
[     8.311] (II) Power Button: Found keys
[     8.312] (II) Power Button: Configuring as keyboard
[     8.312] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[     8.312] (**) Option "xkb_rules" "evdev"
[     8.312] (**) Option "xkb_model" "pc105"
[     8.312] (**) Option "xkb_layout" "is"
[     8.313] (II) XKB: reuse xkmfile /var/lib/xkb/server-D9380151443324518D30ADFB5F6A52CE088B051E.xkm
[     8.314] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     8.314] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     8.314] (**) Power Button: always reports core events
[     8.314] (**) Power Button: Device: "/dev/input/event0"
[     8.341] (II) Power Button: Found keys
[     8.341] (II) Power Button: Configuring as keyboard
[     8.342] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[     8.342] (**) Option "xkb_rules" "evdev"
[     8.342] (**) Option "xkb_model" "pc105"
[     8.342] (**) Option "xkb_layout" "is"
[     8.343] (II) config/udev: Adding input device KYE Genius USB Wheel Mouse (/dev/input/event2)
[     8.343] (**) KYE Genius USB Wheel Mouse: Applying InputClass "evdev pointer catchall"
[     8.343] (**) KYE Genius USB Wheel Mouse: always reports core events
[     8.343] (**) KYE Genius USB Wheel Mouse: Device: "/dev/input/event2"
[     8.382] (II) KYE Genius USB Wheel Mouse: Found 9 mouse buttons
[     8.382] (II) KYE Genius USB Wheel Mouse: Found scroll wheel(s)
[     8.382] (II) KYE Genius USB Wheel Mouse: Found relative axes
[     8.382] (II) KYE Genius USB Wheel Mouse: Found x and y relative axes
[     8.382] (II) KYE Genius USB Wheel Mouse: Configuring as mouse
[     8.382] (**) KYE Genius USB Wheel Mouse: YAxisMapping: buttons 4 and 5
[     8.382] (**) KYE Genius USB Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     8.382] (II) XINPUT: Adding extended input device "KYE Genius USB Wheel Mouse" (type: MOUSE)
[     8.382] (II) KYE Genius USB Wheel Mouse: initialized for relative axes.
[     8.382] (II) config/udev: Adding input device KYE Genius USB Wheel Mouse (/dev/input/mouse0)
[     8.382] (II) No input driver/identifier specified (ignoring)
[     8.382] (II) config/udev: Adding input device DELL DELL USB Keyboard (/dev/input/event3)
[     8.382] (**) DELL DELL USB Keyboard: Applying InputClass "evdev keyboard catchall"
[     8.382] (**) DELL DELL USB Keyboard: always reports core events
[     8.382] (**) DELL DELL USB Keyboard: Device: "/dev/input/event3"
[     8.421] (II) DELL DELL USB Keyboard: Found keys
[     8.421] (II) DELL DELL USB Keyboard: Configuring as keyboard
[     8.422] (II) XINPUT: Adding extended input device "DELL DELL USB Keyboard" (type: KEYBOARD)
[     8.422] (**) Option "xkb_rules" "evdev"
[     8.422] (**) Option "xkb_model" "pc105"
[     8.422] (**) Option "xkb_layout" "is"
[152363.911] (II) config/udev: removing device KYE Genius USB Wheel Mouse
[152363.916] (II) KYE Genius USB Wheel Mouse: Close
[152363.916] (II) UnloadModule: "evdev"
[152364.390] (II) config/udev: Adding input device KYE Genius USB Wheel Mouse (/dev/input/mouse0)
[152364.390] (II) No input driver/identifier specified (ignoring)
[152364.391] (II) config/udev: Adding input device KYE Genius USB Wheel Mouse (/dev/input/event2)
[152364.391] (**) KYE Genius USB Wheel Mouse: Applying InputClass "evdev pointer catchall"
[152364.391] (**) KYE Genius USB Wheel Mouse: always reports core events
[152364.391] (**) KYE Genius USB Wheel Mouse: Device: "/dev/input/event2"
[152364.432] (II) KYE Genius USB Wheel Mouse: Found 9 mouse buttons
[152364.432] (II) KYE Genius USB Wheel Mouse: Found scroll wheel(s)
[152364.432] (II) KYE Genius USB Wheel Mouse: Found relative axes
[152364.432] (II) KYE Genius USB Wheel Mouse: Found x and y relative axes
[152364.432] (II) KYE Genius USB Wheel Mouse: Configuring as mouse
[152364.432] (**) KYE Genius USB Wheel Mouse: YAxisMapping: buttons 4 and 5
[152364.432] (**) KYE Genius USB Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[152364.432] (II) XINPUT: Adding extended input device "KYE Genius USB Wheel Mouse" (type: MOUSE)
[152364.432] (II) KYE Genius USB Wheel Mouse: initialized for relative axes.
[173931.234] (II) config/udev: removing device KYE Genius USB Wheel Mouse
[173931.240] (II) KYE Genius USB Wheel Mouse: Close
[173931.240] (II) UnloadModule: "evdev"
[173931.733] (II) config/udev: Adding input device KYE Genius USB Wheel Mouse (/dev/input/mouse0)
[173931.733] (II) No input driver/identifier specified (ignoring)
[173931.733] (II) config/udev: Adding input device KYE Genius USB Wheel Mouse (/dev/input/event2)
[173931.733] (**) KYE Genius USB Wheel Mouse: Applying InputClass "evdev pointer catchall"
[173931.734] (**) KYE Genius USB Wheel Mouse: always reports core events
[173931.734] (**) KYE Genius USB Wheel Mouse: Device: "/dev/input/event2"
[173931.762] (II) KYE Genius USB Wheel Mouse: Found 9 mouse buttons
[173931.762] (II) KYE Genius USB Wheel Mouse: Found scroll wheel(s)
[173931.762] (II) KYE Genius USB Wheel Mouse: Found relative axes
[173931.762] (II) KYE Genius USB Wheel Mouse: Found x and y relative axes
[173931.762] (II) KYE Genius USB Wheel Mouse: Configuring as mouse
[173931.762] (**) KYE Genius USB Wheel Mouse: YAxisMapping: buttons 4 and 5
[173931.762] (**) KYE Genius USB Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[173931.762] (II) XINPUT: Adding extended input device "KYE Genius USB Wheel Mouse" (type: MOUSE)
[173931.762] (II) KYE Genius USB Wheel Mouse: initialized for relative axes.
[173933.112] (II) config/udev: removing device KYE Genius USB Wheel Mouse
[173933.114] (II) KYE Genius USB Wheel Mouse: Close
[173933.115] (II) UnloadModule: "evdev"
[173933.601] (II) config/udev: Adding input device KYE Genius USB Wheel Mouse (/dev/input/mouse0)
[173933.601] (II) No input driver/identifier specified (ignoring)
[173933.602] (II) config/udev: Adding input device KYE Genius USB Wheel Mouse (/dev/input/event2)
[173933.602] (**) KYE Genius USB Wheel Mouse: Applying InputClass "evdev pointer catchall"
[173933.602] (**) KYE Genius USB Wheel Mouse: always reports core events
[173933.602] (**) KYE Genius USB Wheel Mouse: Device: "/dev/input/event2"
[173933.640] (II) KYE Genius USB Wheel Mouse: Found 9 mouse buttons
[173933.640] (II) KYE Genius USB Wheel Mouse: Found scroll wheel(s)
[173933.640] (II) KYE Genius USB Wheel Mouse: Found relative axes
[173933.640] (II) KYE Genius USB Wheel Mouse: Found x and y relative axes
[173933.640] (II) KYE Genius USB Wheel Mouse: Configuring as mouse
[173933.640] (**) KYE Genius USB Wheel Mouse: YAxisMapping: buttons 4 and 5
[173933.640] (**) KYE Genius USB Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[173933.640] (II) XINPUT: Adding extended input device "KYE Genius USB Wheel Mouse" (type: MOUSE)
[173933.640] (II) KYE Genius USB Wheel Mouse: initialized for relative axes.
[175561.751] (II) config/udev: removing device KYE Genius USB Wheel Mouse
[175561.755] (II) KYE Genius USB Wheel Mouse: Close
[175561.755] (II) UnloadModule: "evdev"
[175562.241] (II) config/udev: Adding input device KYE Genius USB Wheel Mouse (/dev/input/mouse0)
[175562.241] (II) No input driver/identifier specified (ignoring)
[175562.241] (II) config/udev: Adding input device KYE Genius USB Wheel Mouse (/dev/input/event2)
[175562.241] (**) KYE Genius USB Wheel Mouse: Applying InputClass "evdev pointer catchall"
[175562.242] (**) KYE Genius USB Wheel Mouse: always reports core events
[175562.242] (**) KYE Genius USB Wheel Mouse: Device: "/dev/input/event2"
[175562.290] (II) KYE Genius USB Wheel Mouse: Found 9 mouse buttons
[175562.290] (II) KYE Genius USB Wheel Mouse: Found scroll wheel(s)
[175562.290] (II) KYE Genius USB Wheel Mouse: Found relative axes
[175562.290] (II) KYE Genius USB Wheel Mouse: Found x and y relative axes
[175562.290] (II) KYE Genius USB Wheel Mouse: Configuring as mouse
[175562.290] (**) KYE Genius USB Wheel Mouse: YAxisMapping: buttons 4 and 5
[175562.290] (**) KYE Genius USB Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[175562.290] (II) XINPUT: Adding extended input device "KYE Genius USB Wheel Mouse" (type: MOUSE)
[175562.291] (II) KYE Genius USB Wheel Mouse: initialized for relative axes.
[251396.720] (II) XKB: generating xkmfile /var/lib/xkb/server-107601DC0AF3C6AFDE75B9A15079F36446225766.xkm
```

---

### Post by BicyclerBoy on 2011-02-19
Sorry, needed both monitors connected at X server loading..
Connect, reboot & post results.

I would edit the /etc/X11/xorg.conf & comment out the glx line in modules section & comment out the UseEdidDpi  line..

Some other people seem to have fixed EDID problems with later driver versions.

---

