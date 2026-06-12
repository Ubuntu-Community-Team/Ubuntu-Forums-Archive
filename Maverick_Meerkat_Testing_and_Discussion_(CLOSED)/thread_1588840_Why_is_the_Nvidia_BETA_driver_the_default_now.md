---
title: "Why is the Nvidia BETA driver the default now?"
date: 2010-10-05
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by xinix on 2010-10-05
I just did an update and the 260 version of the nvidia driver was installed.  This is a beta version, so why is it being pushed instead of the 253 non-beta version?

This is a problem for me because with mythtv video playback and the  260 driver, the card temp skyrockets and overheats very quickly.

This does not happen with the [S]253[/S] 256.53 version of the driver.

I have switched between driver versions several times, using the same settings and same video to playback.  With the 260 version the card consistently overheats.

I'm using a GT220 card.

---

### Post by Sockerdrickan on 2010-10-05
> **xinix said:**
> I just did an update and the 260 version of the nvidia driver was installed.  This is a beta version, so why is it being pushed instead of the 253 non-beta version?

This is a problem for me because with mythtv video playback and the  260 driver, the card temp skyrockets and overheats very quickly.

This does not happen with the 253 version of the driver.

I have switched between driver versions several times, using the same settings and same video to playback.  With the 260 version the card consistently overheats.

I'm using a GT220 card.
Because there was problem with slow rendering of text in the stable one.

---

### Post by cascade9 on 2010-10-05
I'd rather have slow text rendering than a cooked card...... 

@ xinix- if I were you, I'd do the d/l and manual install of the 253.xx drivers.

---

### Post by xinix on 2010-10-05
> **cascade9 said:**
> I'd rather have slow text rendering than a cooked card...... 

@ xinix- if I were you, I'd do the d/l and manual install of the 253.xx drivers.

I grabbed the 256.xx.debs from a mirror and locked the versions so that updating doesn't replace them.

---

### Post by FuturePilot on 2010-10-05
You should definitely file a bug report on this. There may be others with this problem.

---

### Post by cprofitt on 2010-10-05
Yes, please file a bug -- it is the only way developer will know it is affecting people. The beta was pushed due to folks with the rendering issues (which was more than just text) and the testing they did. I just looked at my machine with nvidia and it is running at 59 C

I am running a Quadro FX 570M

---

### Post by taavikko on 2010-10-05
As it also seems that the beta-driver is incompatible with GF3xx series...

Quite a few bug reports, both nvnews linux section and launchpad.

---

### Post by plun on 2010-10-05
> **taavikko said:**
> As it also seems that the beta-driver is incompatible with GF3xx series...

Quite a few bug reports, both nvnews linux section and launchpad.

Please show me......;)

[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

Also a nvidia bug generated report showing this otherwise it can be FUD-trolls spreading nasty rumors....

[http://www.nvnews.net/vbulletin/showthread.php?t=46678](http://www.nvnews.net/vbulletin/showthread.php?t=46678)

4a

Thanks !

---

### Post by theanswriz42 on 2010-10-05
> **taavikko said:**
> As it also seems that the beta-driver is incompatible with GF3xx series...

Quite a few bug reports, both nvnews linux section and launchpad.

Yup, it blows :(

---

### Post by 23dornot23d on 2010-10-05
Seem's to be ok here now ........ was a few problems a few kernels back for me .... but seems to be ok now.
The temp rarely fluctuates for me but it is normally between .... 56^ to 63^  for this laptop ...... 
My desktop machine usually runs around 10^ degrees cooler though ......

```

[    31.222] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    31.222] X Protocol Version 11, Revision 0
[    31.222] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    31.222] Current Operating System: Linux keith-laptop 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686
[    31.222] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=16f79f1e-44c0-407d-a7e7-ef59fac8b4f2 ro quiet splash
[    31.222] Build Date: 16 September 2010  05:39:22PM
[    31.222] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[    31.225] Current version of pixman: 0.18.4
[    31.225]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    31.225] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    31.226] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct  6 00:21:59 2010
[    31.297] (==) Using config file: "/etc/X11/xorg.conf"
[    31.297] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    31.637] (==) No Layout section.  Using the first Screen section.
[    31.637] (**) |-->Screen "Default Screen" (0)
[    31.637] (**) |   |-->Monitor "<default monitor>"
[    31.637] (==) No device specified for screen "Default Screen".
    Using the first device section listed.
[    31.637] (**) |   |-->Device "Default Device"
[    31.637] (==) No monitor specified for screen "Default Screen".
    Using a default monitor configuration.
[    31.637] (==) Automatically adding devices
[    31.637] (==) Automatically enabling devices
[    31.676] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    31.676]     Entry deleted from font path.
[    31.736] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    31.736] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    31.736] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    31.736] (II) Loader magic: 0x81f8e00
[    31.736] (II) Module ABI versions:
[    31.736]     X.Org ANSI C Emulation: 0.4
[    31.736]     X.Org Video Driver: 8.0
[    31.736]     X.Org XInput driver : 11.0
[    31.736]     X.Org Server Extension : 4.0
[    31.737] (--) PCI:*(0:1:0:0) 10de:06e9:1025:0142 rev 161, Mem @ 0xce000000/16777216, 0xd0000000/268435456, 0xcc000000/33554432, I/O @ 0x00002000/128
[    31.738] (II) Open ACPI successful (/var/run/acpid.socket)
[    31.738] (II) "extmod" will be loaded by default.
[    31.738] (II) "dbe" will be loaded by default.
[    31.738] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    31.738] (II) "record" will be loaded by default.
[    31.738] (II) "dri" will be loaded by default.
[    31.738] (II) "dri2" will be loaded by default.
[    31.738] (II) LoadModule: "glx"
[    31.841] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    35.272] (II) Module glx: vendor="NVIDIA Corporation"
[    36.055]     compiled for 4.0.2, module version = 1.0.0
[    36.055]     Module class: X.Org Server Extension
[    36.055] (II) NVIDIA GLX Module  260.19.06  Mon Sep 13 07:01:31 PDT 2010
[    36.055] (II) Loading extension GLX
[    36.055] (II) LoadModule: "extmod"
[    37.248] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    37.526] (II) Module extmod: vendor="X.Org Foundation"
[    37.526]     compiled for 1.9.0, module version = 1.0.0
[    37.526]     Module class: X.Org Server Extension
[    37.526]     ABI class: X.Org Server Extension, version 4.0
[    37.526] (II) Loading extension MIT-SCREEN-SAVER
[    37.526] (II) Loading extension XFree86-VidModeExtension
[    37.526] (II) Loading extension XFree86-DGA
[    37.555] (II) Loading extension DPMS
[    37.555] (II) Loading extension XVideo
[    37.555] (II) Loading extension XVideo-MotionCompensation
[    37.555] (II) Loading extension X-Resource
[    37.555] (II) LoadModule: "dbe"
[    37.555] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    37.559] (II) Module dbe: vendor="X.Org Foundation"
[    37.559]     compiled for 1.9.0, module version = 1.0.0
[    37.559]     Module class: X.Org Server Extension
[    37.559]     ABI class: X.Org Server Extension, version 4.0
[    37.559] (II) Loading extension DOUBLE-BUFFER
[    37.559] (II) LoadModule: "record"
[    37.559] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    37.884] (II) Module record: vendor="X.Org Foundation"
[    37.884]     compiled for 1.9.0, module version = 1.13.0
[    37.884]     Module class: X.Org Server Extension
[    37.884]     ABI class: X.Org Server Extension, version 4.0
[    37.884] (II) Loading extension RECORD
[    37.884] (II) LoadModule: "dri"
[    37.885] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    37.954] (II) Module dri: vendor="X.Org Foundation"
[    37.955]     compiled for 1.9.0, module version = 1.0.0
[    37.955]     ABI class: X.Org Server Extension, version 4.0
[    37.955] (II) Loading extension XFree86-DRI
[    37.955] (II) LoadModule: "dri2"
[    37.955] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    37.959] (II) Module dri2: vendor="X.Org Foundation"
[    37.959]     compiled for 1.9.0, module version = 1.2.0
[    37.959]     ABI class: X.Org Server Extension, version 4.0
[    37.959] (II) Loading extension DRI2
[    37.959] (II) LoadModule: "nvidia"
[    37.959] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    38.033] (II) Module nvidia: vendor="NVIDIA Corporation"
[    38.033]     compiled for 4.0.2, module version = 1.0.0
[    38.033]     Module class: X.Org Video Driver
[    38.055] (II) NVIDIA dlloader X Driver  260.19.06  Mon Sep 13 06:37:13 PDT 2010
[    38.058] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    38.058] (++) using VT number 7

[    38.209] (II) Loading sub module "fb"
[    38.209] (II) LoadModule: "fb"
[    38.209] (II) Loading /usr/lib/xorg/modules/libfb.so
[    38.283] (II) Module fb: vendor="X.Org Foundation"
[    38.283]     compiled for 1.9.0, module version = 1.0.0
[    38.283]     ABI class: X.Org ANSI C Emulation, version 0.4
[    38.283] (II) Loading sub module "wfb"
[    38.283] (II) LoadModule: "wfb"
[    38.283] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    38.311] (II) Module wfb: vendor="X.Org Foundation"
[    38.311]     compiled for 1.9.0, module version = 1.0.0
[    38.311]     ABI class: X.Org ANSI C Emulation, version 0.4
[    38.311] (II) Loading sub module "ramdac"
[    38.311] (II) LoadModule: "ramdac"
[    38.311] (II) Module "ramdac" already built-in
[    38.423] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[    38.423] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    38.423] (==) NVIDIA(0): RGB weight 888
[    38.423] (==) NVIDIA(0): Default visual is TrueColor
[    38.423] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    38.423] (**) NVIDIA(0): Option "NoLogo" "True"
[    38.426] (**) NVIDIA(0): Enabling RENDER acceleration
[    38.426] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    38.426] (II) NVIDIA(0):     enabled.
[    39.720] (II) NVIDIA(0): NVIDIA GPU GeForce 9300M GS (G98) at PCI:1:0:0 (GPU-0)
[    39.720] (--) NVIDIA(0): Memory: 524288 kBytes
[    39.720] (--) NVIDIA(0): VideoBIOS: 62.98.51.00.06
[    39.720] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    39.720] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    39.720] (--) NVIDIA(0): Connected display device(s) on GeForce 9300M GS at PCI:1:0:0
[    39.720] (--) NVIDIA(0):     AUO (DFP-0)
[    39.720] (--) NVIDIA(0): AUO (DFP-0): 330.0 MHz maximum pixel clock
[    39.720] (--) NVIDIA(0): AUO (DFP-0): Internal Dual Link LVDS
[    39.790] (II) NVIDIA(0): Assigned Display Device: DFP-0
[    39.790] (==) NVIDIA(0): 
[    39.791] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    39.791] (==) NVIDIA(0):     will be used as the requested mode.
[    39.791] (==) NVIDIA(0): 
[    39.791] (II) NVIDIA(0): Validated modes:
[    39.791] (II) NVIDIA(0):     "nvidia-auto-select"
[    39.791] (II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
[    40.841] (--) NVIDIA(0): DPI set to (98, 99); computed from "UseEdidDpi" X config
[    40.841] (--) NVIDIA(0):     option
[    40.879] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    40.879] (--) Depth 24 pixmap format is 32 bpp
[    40.879] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    40.880] (II) NVIDIA(0): Initialized GPU GART.
[    40.884] (II) NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
[    40.884] (II) NVIDIA(0):     enough to receive ACPI hotkey events.
[    40.884] (II) NVIDIA(0): ACPI brightness change hotkey events enabled.
[    40.886] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    41.321] (II) Loading extension NV-GLX
[    41.401] (II) NVIDIA(0): Initialized OpenGL Acceleration
[    41.506] (==) NVIDIA(0): Disabling shared memory pixmaps
[    41.506] (II) NVIDIA(0): Initialized X Rendering Acceleration
[    41.506] (==) NVIDIA(0): Backing store disabled
[    41.506] (==) NVIDIA(0): Silken mouse enabled
[    41.536] (==) NVIDIA(0): DPMS enabled
[    41.536] (II) Loading extension NV-CONTROL
[    41.536] (II) Loading extension XINERAMA
[    41.536] (II) Loading sub module "dri2"
[    41.536] (II) LoadModule: "dri2"
[    41.537] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[    41.537] (II) NVIDIA(0): [DRI2] Setup complete
[    41.537] (==) RandR enabled
[    41.537] (II) Initializing built-in extension Generic Event Extension
[    41.537] (II) Initializing built-in extension SHAPE
[    41.537] (II) Initializing built-in extension MIT-SHM
[    41.537] (II) Initializing built-in extension XInputExtension
[    41.537] (II) Initializing built-in extension XTEST
[    41.537] (II) Initializing built-in extension BIG-REQUESTS
[    41.537] (II) Initializing built-in extension SYNC
[    41.537] (II) Initializing built-in extension XKEYBOARD
[    41.537] (II) Initializing built-in extension XC-MISC
[    41.537] (II) Initializing built-in extension SECURITY
[    41.537] (II) Initializing built-in extension XINERAMA
[    41.537] (II) Initializing built-in extension XFIXES
[    41.537] (II) Initializing built-in extension RENDER
[    41.537] (II) Initializing built-in extension RANDR
[    41.537] (II) Initializing built-in extension COMPOSITE
[    41.537] (II) Initializing built-in extension DAMAGE
[    41.537] (II) Initializing built-in extension GESTURE
[    41.537] (II) Initializing extension GLX
[    41.790] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    41.811] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    41.811] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    41.811] (II) LoadModule: "evdev"
[    41.812] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    41.858] (II) Module evdev: vendor="X.Org Foundation"
[    41.858]     compiled for 1.9.0, module version = 2.3.2
[    41.858]     Module class: X.Org XInput Driver
[    41.858]     ABI class: X.Org XInput driver, version 11.0
[    41.858] (**) Power Button: always reports core events
[    41.858] (**) Power Button: Device: "/dev/input/event3"
[    41.869] (II) Power Button: Found keys
[    41.869] (II) Power Button: Configuring as keyboard
[    41.869] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    41.869] (**) Option "xkb_rules" "evdev"
[    41.869] (**) Option "xkb_model" "pc105"
[    41.869] (**) Option "xkb_layout" "gb"
[    41.871] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[    41.879] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    41.879] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    41.879] (**) Video Bus: always reports core events
[    41.879] (**) Video Bus: Device: "/dev/input/event5"
[    41.893] (II) Video Bus: Found keys
[    41.893] (II) Video Bus: Configuring as keyboard
[    41.893] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    41.893] (**) Option "xkb_rules" "evdev"
[    41.893] (**) Option "xkb_model" "pc105"
[    41.893] (**) Option "xkb_layout" "gb"
[    41.894] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    41.894] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    41.894] (**) Power Button: always reports core events
[    41.894] (**) Power Button: Device: "/dev/input/event1"
[    41.909] (II) Power Button: Found keys
[    41.909] (II) Power Button: Configuring as keyboard
[    41.909] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    41.909] (**) Option "xkb_rules" "evdev"
[    41.909] (**) Option "xkb_model" "pc105"
[    41.909] (**) Option "xkb_layout" "gb"
[    41.910] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    41.910] (II) No input driver/identifier specified (ignoring)
[    41.910] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    41.910] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    41.910] (**) Sleep Button: always reports core events
[    41.910] (**) Sleep Button: Device: "/dev/input/event2"
[    41.921] (II) Sleep Button: Found keys
[    41.921] (II) Sleep Button: Configuring as keyboard
[    41.921] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    41.921] (**) Option "xkb_rules" "evdev"
[    41.921] (**) Option "xkb_model" "pc105"
[    41.921] (**) Option "xkb_layout" "gb"
[    41.927] (II) config/udev: Adding input device Acer Crystal Eye webcam (/dev/input/event8)
[    41.927] (**) Acer Crystal Eye webcam: Applying InputClass "evdev keyboard catchall"
[    41.927] (**) Acer Crystal Eye webcam: always reports core events
[    41.928] (**) Acer Crystal Eye webcam: Device: "/dev/input/event8"
[    41.937] (II) Acer Crystal Eye webcam: Found keys
[    41.937] (II) Acer Crystal Eye webcam: Configuring as keyboard
[    41.937] (II) XINPUT: Adding extended input device "Acer Crystal Eye webcam" (type: KEYBOARD)
[    41.937] (**) Option "xkb_rules" "evdev"
[    41.937] (**) Option "xkb_model" "pc105"
[    41.937] (**) Option "xkb_layout" "gb"
[    41.942] (II) config/udev: Adding input device HID 04d9:048e (/dev/input/event6)
[    41.942] (**) HID 04d9:048e: Applying InputClass "evdev pointer catchall"
[    41.942] (**) HID 04d9:048e: always reports core events
[    41.942] (**) HID 04d9:048e: Device: "/dev/input/event6"
[    41.952] (II) HID 04d9:048e: Found 9 mouse buttons
[    41.952] (II) HID 04d9:048e: Found scroll wheel(s)
[    41.952] (II) HID 04d9:048e: Found relative axes
[    41.952] (II) HID 04d9:048e: Found x and y relative axes
[    41.952] (II) HID 04d9:048e: Configuring as mouse
[    41.952] (**) HID 04d9:048e: YAxisMapping: buttons 4 and 5
[    41.952] (**) HID 04d9:048e: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    41.952] (II) XINPUT: Adding extended input device "HID 04d9:048e" (type: MOUSE)
[    41.952] (II) HID 04d9:048e: initialized for relative axes.
[    41.952] (II) config/udev: Adding input device HID 04d9:048e (/dev/input/mouse0)
[    41.952] (II) No input driver/identifier specified (ignoring)
[    41.953] (II) config/udev: Adding input device UC-LOGIC Tablet WP5540U (/dev/input/event7)
[    41.953] (**) UC-LOGIC Tablet WP5540U: Applying InputClass "evdev pointer catchall"
[    41.953] (**) UC-LOGIC Tablet WP5540U: Applying InputClass "evdev tablet catchall"
[    41.953] (**) UC-LOGIC Tablet WP5540U: always reports core events
[    41.953] (**) UC-LOGIC Tablet WP5540U: Device: "/dev/input/event7"
[    41.964] (II) UC-LOGIC Tablet WP5540U: Found 10 mouse buttons
[    41.964] (II) UC-LOGIC Tablet WP5540U: Found scroll wheel(s)
[    41.964] (II) UC-LOGIC Tablet WP5540U: Found relative axes
[    41.964] (II) UC-LOGIC Tablet WP5540U: Found x and y relative axes
[    41.964] (II) UC-LOGIC Tablet WP5540U: Found absolute axes
[    41.964] (II) evdev-grail: failed to open grail, no gesture support
[    41.964] (II) UC-LOGIC Tablet WP5540U: Found x and y absolute axes
[    41.964] (II) UC-LOGIC Tablet WP5540U: Found absolute tablet.
[    41.964] (II) UC-LOGIC Tablet WP5540U: Configuring as tablet
[    41.964] (**) UC-LOGIC Tablet WP5540U: YAxisMapping: buttons 4 and 5
[    41.964] (**) UC-LOGIC Tablet WP5540U: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    41.964] (II) XINPUT: Adding extended input device "UC-LOGIC Tablet WP5540U" (type: TABLET)
[    41.964] (WW) UC-LOGIC Tablet WP5540U: touchpads, tablets and touchscreens ignore relative axes.
[    41.964] (II) UC-LOGIC Tablet WP5540U: initialized for absolute axes.
[    41.964] (II) config/udev: Adding input device UC-LOGIC Tablet WP5540U (/dev/input/mouse1)
[    41.964] (II) No input driver/identifier specified (ignoring)
[    41.968] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    41.968] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    41.968] (**) AT Translated Set 2 keyboard: always reports core events
[    41.968] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    41.984] (II) AT Translated Set 2 keyboard: Found keys
[    41.984] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    41.984] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    41.984] (**) Option "xkb_rules" "evdev"
[    41.984] (**) Option "xkb_model" "pc105"
[    41.984] (**) Option "xkb_layout" "gb"
[    41.984] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event9)
[    41.984] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    41.984] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    41.984] (II) LoadModule: "synaptics"
[    41.985] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    41.992] (II) Module synaptics: vendor="X.Org Foundation"
[    41.992]     compiled for 1.9.0, module version = 1.2.2
[    41.992]     Module class: X.Org XInput Driver
[    41.992]     ABI class: X.Org XInput driver, version 11.0
[    41.992] (II) Synaptics touchpad driver version 1.2.2
[    41.992] (**) Option "Device" "/dev/input/event9"
[    42.045] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    42.045] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    42.045] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    42.045] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    42.045] (II) SynPS/2 Synaptics TouchPad: buttons: left right
[    42.097] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    42.097] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    42.121] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    42.121] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    42.121] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    42.121] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    42.121] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    42.157] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    42.157] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse2)
[    42.157] (II) No input driver/identifier specified (ignoring)


```[http://img824.imageshack.us/img824/6918/nam14.jpg](http://img824.imageshack.us/img824/6918/nam14.jpg)

---

### Post by efflandt on 2010-10-05
People seem to be shorting some numbers.  Version in 10.10 beta and when I upgraded to RC was 256.53 (not 253).  I also have GT220 and have no issues with 256.53.

When was 260.19.06 added to normal repositories?  Synaptic does not show a specific selection for 256.53 it just says that is my version and current version is 260.19.06.  So it does not look like there is an easy way to go back.  But I am just running 10.10 from a USB hard drive, so as long as my PC does not go up in flames, no great loss.

PS: I guess it is a non-issue for me.  v260 seems to idle close to same temperature as v256, maybe a couple of degrees C warmer under load.  Not sure how to test it, but glxgears was 50% faster with v260.  And in a room at just under 20 C (66 F) it hovered about 40 C playing Hulu Desktop full screen on a 1080p HDTV using real 64-bit flash 10.2 r161.  So 260.19.06 works fine for my GT220.

---

### Post by ktp on 2010-10-05
> **plun said:**
> Please show me......;)

[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

Also a nvidia bug generated report showing this otherwise it can be FUD-trolls spreading nasty rumors....

[http://www.nvnews.net/vbulletin/showthread.php?t=46678](http://www.nvnews.net/vbulletin/showthread.php?t=46678)

4a

Thanks !

I don't know how many total but there are few in this forum and here is example on nvidia forum:

[http://www.nvnews.net/vbulletin/showthread.php?t=155238](http://www.nvnews.net/vbulletin/showthread.php?t=155238)

---

### Post by sdowney717 on 2010-10-05
Right now, I am running at 44 centigrade on the 260 driver which is perfect.
At least it is inline with what all the older drivers ran at.

---

### Post by sdowney717 on 2010-10-05
> I don't know how many total but there are few in this forum and here is example on nvidia forum:

[http://www.nvnews.net/vbulletin/showthread.php?t=155238](http://www.nvnews.net/vbulletin/showthread.php?t=155238)

nothing on that about an **overtemp** issue, just could not get it to work, black screen.

---

### Post by cprofitt on 2010-10-05
Has anyone put in an official bug yet?

---

### Post by cariboo on 2010-10-05
Has anybody that is having a problem run:

```
sudo nvidia-bug-report.sh
```

If so it would be nice if they posted the results here.

---

### Post by ktp on 2010-10-05
> **sdowney717 said:**
> nothing on that about an **overtemp** issue, just could not get it to work, black screen.

That was response-to-response to following post:

> **taavikko said:**
> As it also seems that the beta-driver is incompatible with **GF3xx series**...

Quite a few bug reports, both nvnews linux section and launchpad.

---

### Post by xinix on 2010-10-06
> **cariboo907 said:**
> Has anybody that is having a problem run:

```
sudo nvidia-bug-report.sh
```

If so it would be nice if they posted the results here.

This results in a 6300 line file thats basically a compillation of other logs.  What would be particularly useful?

Here is what I get with the same settings and same video playback with mythtv under both drivers.

```
nvidia-smi --query-gpu-info -a
```


Idle for 15 min:

Driver Version			: 260.19.06

GPU 0:
	Product Name		: GeForce GT 220
	PCI Device/Vendor ID	: a2010de
	PCI Location ID		: 0:5:0
	Display			: Connected
	Temperature		: 63 C
	Fan Speed		: 0%
	Utilization
	    GPU			: 0%
	    Memory		: 5%

After 7 minutes of playback.  Any longer and the system crashes

Driver Version			: 260.19.06

GPU 0:
	Product Name		: GeForce GT 220
	PCI Device/Vendor ID	: a2010de
	PCI Location ID		: 0:5:0
	Display			: Connected
	Temperature		: 109 C
	Fan Speed		: 0%
	Utilization
	    GPU			: 4%
	    Memory		: 13%



With the 256.53 driver I get these numbers.


Idle for 15 min:

GPU 0:
	Product Name		: GeForce GT 220
	PCI ID			: a2010de
	Temperature		: 58 C

During playback temps max out around this point:

GPU 0:
	Product Name		: GeForce GT 220
	PCI ID			: a2010de
	Temperature		: 92 C

---

### Post by cascade9 on 2010-10-06
109C? o.O 

The maximum GPU temp should be 105C. 

[http://www.nvidia.com/object/product_geforce_gt_220_us.html](http://www.nvidia.com/object/product_geforce_gt_220_us.html)

92C with the 256.53 is safe, but still very high. I've got a passive cooled 8600GT and it tends to run at about 55-65C (depending on the ambient temprature) and I dont think I've ever seen it go over 85C, and that was a long game session on a hot day that did that (that is with the 195.36.31 drivers BTW) 

Does your case have minimal airflow? 

Not saying that the hot temps are your fault at all, and from the temps you've posted it seems pretty obvious that the 260.xx drivers do run hotter on your system. I'm just suprised at the generally high temps you are getting.

---

### Post by Cavsfan on 2010-10-06
I guess I am fortunate as I have the 260.19.06 version installed and with room temp at 80-81 I am getting 52-53 celsius no load
and 64 celsius while running SuperTux 2 (I am such a gamer!), so that is not bad considering the room temperature.

I have an nVidia Geforce 9800 GT 512GB and didn't even notice that the 260 was beta.
Installed the 256 version on Lucid and it upgraded to the 260 version with an update. I 
then upgraded to Maverick and the 260 version came along.

So, this is on Lucid and Maverick.

---

### Post by xinix on 2010-10-06
> **cascade9 said:**
> 

92C with the 256.53 is safe, but still very high. I've got a passive cooled 8600GT and it tends to run at about 55-65C (depending on the ambient temprature) and I dont think I've ever seen it go over 85C, and that was a long game session on a hot day that did that (that is with the 195.36.31 drivers BTW) 

Does your case have minimal airflow? .

Air flow isn't ideal but it's there.  This card has always run hot but like you said still safe.  It's certainly hotter than the 6200 that it replaced. Right now I don't have the cover on the case so airflows pretty well, but I get the same readings with the cover on too.

I never really thought that a driver would make such a significant difference in temperatures.  But, at least for me, this seems to be the case.  It would be good to know if others are impacted by this or if it is unique to myself.

What surprises me the most about all this is that it is a beta driver that is slated for a distro release.  It seems like a slippery slope to me.  In the past I've seen the argument that xyz software version couldn't be part of a release because it was beta.  If it is ok in this situation, then why not in others?

---

### Post by cariboo on 2010-10-06
I have 2 systems using the 260 driver and gpu temps are in the low to mid 40°C. the one thing I am concerned about is this error message that is filling up the logs on one system:

```
Oct  6 08:51:57 alexis-maverick kernel: [ 3004.795613] NVRM: os_raise_smp_barrier(), invalid context!
```

---

### Post by Cavsfan on 2010-10-06
As I mentioned on the previous page, I get the beta driver installed on Lucid Lynx via a daily update, so it is not just Maverick....

---

### Post by FuturePilot on 2010-10-06
> **Cavsfan said:**
> As I mentioned on the previous page, I get the beta driver installed on Lucid Lynx via a daily update, so it is not just Maverick....

That's most likely from a PPA. There's no way they would push a beta driver into a stable release.

---

### Post by cascade9 on 2010-10-06
> **xinix said:**
> Air flow isn't ideal but it's there. This card has always run hot but like you said still safe. It's certainly hotter than the 6200 that it replaced. Right now I don't have the cover on the case so airflows pretty well, but I get the same readings with the cover on too.

Not that suprising really, having the sides on can actually be cooler than sides off (and the air can just go round and round in circles with the sides off, with the sides on its in, through, out). 

> **xinix said:**
> I never really thought that a driver would make such a significant difference in temperatures. But, at least for me, this seems to be the case. It would be good to know if others are impacted by this or if it is unique to myself.

One of the beta 195.x drivers was cooking cards (windows and linux). Some error in the fan control IIRC. 

> **xinix said:**
> What surprises me the most about all this is that it is a beta driver that is slated for a distro release. It seems like a slippery slope to me. In the past I've seen the argument that xyz software version couldn't be part of a release because it was beta. If it is ok in this situation, then why not in others?

If Sockerdrickan is right (there was problem with slow rendering of text in the stable driver) I would guess that its about the eyecandy factor. Its also possible that the developers had a look at the bug reports for the 260.xx drivers, saw nothing, and assumed that everything would be fine. 

> **Cavsfan said:**
> As I mentioned on the previous page, I get the beta driver installed on Lucid Lynx via a daily update, so it is not just Maverick....

If you installed the nvidia drivers the way you described here- 

[http://ubuntuforums.org/showthread.php?p=9928751](http://ubuntuforums.org/showthread.php?p=9928751)

then you've updated the drivers youirself, manually, on 10.04. You didnt add a PPA or anything, so there is no way (using the method you described) that you would have updated from 256.xx to 260.xx drivers without manual intervention on 10.04.

---

### Post by Cavsfan on 2010-10-06
> **FuturePilot said:**
> That's most likely from a PPA. There's no way they would push a beta driver into a stable release.


> **cascade9 said:**
> If you installed the nvidia drivers the way you described here- 

[http://ubuntuforums.org/showthread.php?p=9928751](http://ubuntuforums.org/showthread.php?p=9928751)

then you've updated the drivers yourself, manually, on 10.04. You didn't add a PPA or anything, so there is no way (using the method you described) that you would have updated from 256.xx to 260.xx drivers without manual intervention on 10.04.

You are both right I must have added a PPA and didn't notice. 
So, what this thread is about is the beta version is default on Maverick?
In Jaunty, Karmic and Lucid all I ever seen was the 173 and 185 or whatever version in Hardware Drivers for nVidea.
And I am wondering why I do not see Hardware Drivers anywhere.

---

### Post by Cavsfan on 2010-10-06
I just re-installed the 256.53 version and before hand looked for any PPA that might have gotten added and there were none.

I believe that since I installed the driver myself in Lucid that it upgraded to the 260.xx beta version on it's own.

That's my story and I am sticking with it. :wink:

I do not notice any difference at all myself. If it gets upgraded again, I'll leave it.

---

### Post by 23dornot23d on 2010-10-06
> **xinix said:**
> This results in a 6300 line file thats basically a compillation of other logs.  What would be particularly useful?

Here is what I get with the same settings and same video playback with mythtv under both drivers.

```
nvidia-smi --query-gpu-info -a
```Idle for 15 min:

Driver Version            : 260.19.06

GPU 0:
    Product Name        : GeForce GT 220
    PCI Device/Vendor ID    : a2010de
    PCI Location ID        : 0:5:0
    Display            : Connected
    Temperature        : 63 C
    Fan Speed        : 0%
    Utilization
        GPU            : 0%
        Memory        : 5%

After 7 minutes of playback.  Any longer and the system crashes

Driver Version            : 260.19.06

GPU 0:
    Product Name        : GeForce GT 220
    PCI Device/Vendor ID    : a2010de
    PCI Location ID        : 0:5:0
    Display            : Connected
    Temperature        : 109 C
    Fan Speed        : 0%
    Utilization
        GPU            : 4%
        Memory        : 13%



With the 256.53 driver I get these numbers.


Idle for 15 min:

GPU 0:
    Product Name        : GeForce GT 220
    PCI ID            : a2010de
    Temperature        : 58 C

During playback temps max out around this point:

GPU 0:
    Product Name        : GeForce GT 220
    PCI ID            : a2010de
    Temperature        : 92 C


It appears that the fan is not running at max temps , from what you have shown here - even with the older driver 92 C seems pretty high to me ......

Could you possibly post a photograph of the inside of you computer pointing at the graphics card - use a flash  ..... just so we can see what the setup is like .....

As said previously decent air flow through the computer can help keep it cooler ......

To me if the temps are getting that high ..... the fan is not running which ever driver
you are using ....... is there a wire in the way of the fan ...... is the fan connected
to the PCB ...... is the fan spinning at all
Is there plenty of room around the computer for decent airflow .....

Do you run Windows too .... ? ...... ( just wondered if you had a comparison of  temps )

---

### Post by cariboo on 2010-10-06
I have a customer that has a gateway desktop, running vista, since they purchaed it, it's gone through 3 video cards and the ram has been replaced 4 times. They called me earlier this spring because they were tired of having parts replaced, and no real solution. After a bit of testing using an Ubuntu Live CD I determined that there just wasn't enough air flow in the case. 

I replaced the stock case with one of [these]("http://www.thermaltakeusa.com/Product.aspx?C=1390&ID=1819"), it also has a 23CM fan on the side instead of a window. It survived the summer with +40°C temps, the business is located in a quonset hut with no air conditioning, without breaking a sweat. :)

---

### Post by 23dornot23d on 2010-10-06
That sure looks a nice case ..... something like this may solve the users problems too.

But it worries me that the Graphics card fan may not be spinning , but if the case has a
decent throughput of air and the building that its in is cool and the computer is in some
open area ..... it all helps to keep the machine running cooler ...... and as you have pointed out - 
the items in the computer will last longer too .

---

### Post by efflandt on 2010-10-06
It does appear that **xinix** has a fan or other cooling issue.  This is similar video card at 69F (21C) room temperature.

Idle:
**nvidia-smi --query-gpu-info -a**

Driver Version            : 260.19.06

GPU 0:
    Product Name        : GeForce GT 220
    PCI Device/Vendor ID    : a2010de
    PCI Location ID        : 0:1:0
    Display            : Connected
    Temperature        : 34 C
    Fan Speed        : 20%
    Utilization
        GPU            : 0%
        Memory        : 11%


While running glxgears when temperature appeared to stop rising:
[B]nvidia-smi --query-gpu-info -a
[/B] 
Driver Version            : 260.19.06

GPU 0:
    Product Name        : GeForce GT 220
    PCI Device/Vendor ID    : a2010de
    PCI Location ID        : 0:1:0
    Display            : Connected
    Temperature        : 55 C
    Fan Speed        : 30%
    Utilization
        GPU            : 99%
        Memory        : 38%

---

### Post by 23dornot23d on 2010-10-06
Yep Fan speed 20% and 30% ...... 

The OPs is reading 0% in both cases ..... unless the monitor is not working for the OPs machine
but its usually easy to see if the fan is spinning or not ......... if the case is open as the OP says .....

I had a quick look at some of the different 220 cards and there is a separate wire on some for the fan , 
maybe its just got caught and come off .... or there is an obstruction somewhere stopping the fan spinning .

---

### Post by xinix on 2010-10-07
> **23dornot23d said:**
> Yep Fan speed 20% and 30% ...... 

The OPs is reading 0% in both cases ..... unless the monitor is not working for the OPs machine
but its usually easy to see if the fan is spinning or not ......... if the case is open as the OP says .....

I had a quick look at some of the different 220 cards and there is a separate wire on some for the fan , 
maybe its just got caught and come off .... or there is an obstruction somewhere stopping the fan spinning .

The fan is running so I'd guess it's not reading in the monitor.  I don't think the fan has variable speeds so maybe that's why it's not registering.

The high temps are partially solved now.  Since there has been so much concern about the overall high temps, I decided to look into this more seriously.  What I found was that the thermal grease was not applied very well at the factory.  I removed the fan and heatsink to find that the thermal grease was covering only half the chip and was thick.  There wasn't enough contact for heat to leave the chip efficiently.  I cleaned off the stuff that was on there and applied a thin layer of arctic silver.

With the 256.53 driver my idle temps are about 42c and after a couple hours of watching 1080i TV it went up to 80c.  Better than what I was getting before.

With the 260.19.06 driver my idle temps are at about 50c and with 1080i playback they max out at about 88c.  Still higher than the 256 driver but much better than the card cooking temps.

So the properly applied thermal grease makes a huge difference . There still seems to be a difference in the drivers just not as alarming.

Thanks for the help, suggestions and concerns.

---

### Post by cascade9 on 2010-10-07
I'd just guessed that with 0% on both fanspeeds, it was a passive cooled card. Wrong guess. :| 

If you've got a 2wire fan power connector, you will (AFAIK) never get a fanspeed, and some cheaper cards still come with 2 wire fan connectors for the video card. 

> **xinix said:**
> The fan is running so I'd guess it's not reading in the monitor.  I don't think the fan has variable speeds so maybe that's why it's not registering.

The high temps are partially solved now.  Since there has been so much concern about the overall high temps, I decided to look into this more seriously.  What I found was that the thermal grease was not applied very well at the factory.  I removed the fan and heatsink to find that the thermal grease was covering only half the chip and was thick.  There wasn't enough contact for heat to leave the chip efficiently.  I cleaned off the stuff that was on there and applied a thin layer of arctic silver.


I really hate that. Poorly applied thermal paste  is almost useless, and this sounds like one of the worst jobs I'veheard of. Normally they at least get the whole chip covered. 

The last few video cards I've ripped the heatsink of have had at least minor problems with the thermal paste....I'm almost getting to the point of pulling the heatsink off and fixing the thermal paste any and all new video cards (and northbridges on motherboards) I get. The only reason I havent started doing that already is just in case I have to RMA something. 

Good to see your fixed the problem ;)

---

### Post by Cavsfan on 2010-10-07
When I got my PC from NewEgg it only had a couple of slow fans installed and the reviews said that most people added some 
fans. It had several places to add fans and so I purchased about 5-7 fans that spin between 2000 and 2800 RPMs. I 
added 2 to the bottom front to pull air in and a huge one in the back to suck air out. I also replaced the existing fans with more powerful ones.

Also I have to take it apart about every 4-6 months to clean the fans or else it will overheat. In Windows I have 2 programs Core Temp is one 
and I forget the name of the other one, but they display the temp of each of the 4 cores in the bottom right task bar and also the GPU temp. So I have 
5 temp. displayed in 5 different colors letting me know exactly what the temps are running.

I just found this which displays the GPU temp on Ubuntu!!! You have to set the preferences by right clicking on it after you put it on the panel.
[[COLOR=blue]_http://ubuntuforums.org/showpost.php?p=9865764&postcount=13_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=9865764&postcount=13")
And that is just a post on the 2nd page. There is another one on that thread to monitor HD temp. Which I installed too, but not too worried about HD temp.
I installed it and then right clicked on the top panel and clicked add and then Hardware Sensors Monitor! Sweet It even has an option for Fahrenheit as I don't understand Celsius!
My GPU is at 124F and room temp is 79.

EDIT: After I rebooted I now have GPU temp, all 4 core temps and 3 other temps that are coming from my motherboard's temp. monitoring features 
displayed on the top panel! 
Sweet! This is as good as windows core temp and speedfan!

---

### Post by theanswriz42 on 2010-10-07
> **Cavsfan said:**
> When I got my PC from NewEgg it only had a couple of slow fans installed and the reviews said that most people added some 
fans. It had several places to add fans and so I purchased about 5-7 fans that spin between 2000 and 2800 RPMs. I 
added 2 to the bottom front to pull air in and a huge one in the back to suck air out. I also replaced the existing fans with more powerful ones.

Also I have to take it apart about every 4-6 months to clean the fans or else it will overheat. In Windows I have 2 programs Core Temp is one 
and I forget the name of the other one, but they display the temp of each of the 4 cores in the bottom right task bar and also the GPU temp. So I have 
5 temp. displayed in 5 different colors letting me know exactly what the temps are running.

I just found this which displays the GPU temp on Ubuntu!!! You have to set the preferences by right clicking on it after you put it on the panel.
[[COLOR=blue]_http://ubuntuforums.org/showpost.php?p=9865764&postcount=13_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=9865764&postcount=13")
And that is just a post on the 2nd page. There is another one on that thread to monitor HD temp. Which I installed too, but not too worried about HD temp.
I installed it and then right clicked on the top panel and clicked add and then Hardware Sensors Monitor! Sweet It even has an option for Fahrenheit as I don't understand Celsius!
My GPU is at 124F and room temp is 79.

EDIT: After I rebooted I now have GPU temp, all 4 core temps and 3 other temps that are coming from my motherboard's temp. monitoring features 
displayed on the top panel! 
Sweet! This is as good as windows core temp and speedfan!

I use gkrellm which in my opinion has a slightly nicer UI for that stuff.

---

### Post by Cavsfan on 2010-10-07
Thanks! I am checking that out now!

---

### Post by cascade9 on 2010-10-08
> **Cavsfan said:**
> When I got my PC from NewEgg it only had a couple of slow fans installed and the reviews said that most people added some 
fans. It had several places to add fans and so I purchased about 5-7 fans that spin between 2000 and 2800 RPMs. I 
added 2 to the bottom front to pull air in and a huge one in the back to suck air out. I also replaced the existing fans with more powerful ones.

Also I have to take it apart about every 4-6 months to clean the fans or else it will overheat. 

You know, you really dont need 5+ fans unless you are going for MAJOR overclocks. 

Next case you get, find one with a nice filter in front of the intake fans. It makes keeping inside the case a lot easier, and you only have to take the filter out once every now and again, give it a bit of a bash (or even a wash if its really filth, then dry it out). Replace dust filter - job done.

A cheap, dirty filter is to use some old stocking streched over the intake fans. Not as good as a filter can be, but better than having to clean out the case......

---

### Post by Cavsfan on 2010-10-08
> **cascade9 said:**
> You know, you really dont need 5+ fans unless you are going for MAJOR overclocks. 

Next case you get, find one with a nice filter in front of the intake fans. It makes keeping inside the case a lot easier, and you only have to take the filter out once every now and again, give it a bit of a bash (or even a wash if its really filth, then dry it out). Replace dust filter - job done.

A cheap, dirty filter is to use some old stocking streched over the intake fans. Not as good as a filter can be, but better than having to clean out the case......

I believe the fans were necessary in this case. The case has some huge holes like where the top and side 
fans are. But, I agree that more consideration will be placed in how well the case is sealed the next time.

---

### Post by cascade9 on 2010-10-08
> **Cavsfan said:**
> I believe the fans were necessary in this case. The case has some huge holes like where the top and side fans are. But, I agree that more consideration will be placed in how well the case is sealed the next time.

You dont  have to fill all the case fan holes either. ;) 

Lots of people just run with them open and in some cases I do, it all depends on how the air flows in the case. Blocking off the holes is easy, I've used metal, cardboard, plastic, duct tape, electrical tape, silicone (etc) sealants and bluetack (not all at the same time LOL) to fill holes.

---

