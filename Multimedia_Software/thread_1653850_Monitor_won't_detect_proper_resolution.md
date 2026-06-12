---
title: "Monitor won't detect proper resolution"
date: 2010-12-27
forum: Multimedia Software
---

### Post by zintinio on 2010-12-27
This has been happening with the majority of screens I try to plug into, but the proprietary nvidia driver never detects the correct resolutions -__- the open-source driver works perfectly with a little xrandr magic, but I'd like to have some 3D acceleration going on. I'm using the desktop version of Nvidia ION and ubuntu 10.10, with the current nvidia driver (from the repositories). The native resolution is 1440x900 @60 Hz. Any thoughts on this? Again, the nouveau driver is great but I'd like to have VDPAU and the like working.

Xorg.0.log
```

[    17.521] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    17.522] X Protocol Version 11, Revision 0
[    17.522] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[    17.522] Current Operating System: Linux Se7en-Linux 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 11:55:36 UTC 2010 x86_64
[    17.522] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-23-generic root=UUID=702f4b18-9673-456c-b5bb-2bc8e90f234d ro quiet splash
[    17.522] Build Date: 16 September 2010  06:18:41PM
[    17.522] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[    17.522] Current version of pixman: 0.18.4
[    17.522] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    17.522] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    17.522] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Dec 27 13:22:34 2010
[    17.523] (==) Using config file: "/etc/X11/xorg.conf"
[    17.523] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    17.807] (==) ServerLayout "Layout0"
[    17.807] (**) |-->Screen "Screen0" (0)
[    17.807] (**) |   |-->Monitor "Monitor0"
[    17.808] (**) |   |-->Device "Device0"
[    17.808] (**) |-->Input Device "Keyboard0"
[    17.808] (**) |-->Input Device "Mouse0"
[    17.808] (**) Option "Xinerama" "0"
[    17.808] (==) Automatically adding devices
[    17.808] (==) Automatically enabling devices
[    17.808] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    17.808] 	Entry deleted from font path.
[    17.809] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    17.809] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    17.809] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    17.809] (WW) Disabling Keyboard0
[    17.809] (WW) Disabling Mouse0
[    17.809] (II) Loader magic: 0x7d0200
[    17.809] (II) Module ABI versions:
[    17.809] 	X.Org ANSI C Emulation: 0.4
[    17.809] 	X.Org Video Driver: 8.0
[    17.809] 	X.Org XInput driver : 11.0
[    17.809] 	X.Org Server Extension : 4.0
[    17.812] (--) PCI:*(0:3:0:0) 10de:087d:19da:a108 rev 177, Mem @ 0xfb000000/16777216, 0xe0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000ec00/128, BIOS @ 0x????????/131072
[    17.812] (II) Open ACPI successful (/var/run/acpid.socket)
[    17.812] (II) LoadModule: "extmod"
[    17.828] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    17.834] (II) Module extmod: vendor="X.Org Foundation"
[    17.834] 	compiled for 1.9.0, module version = 1.0.0
[    17.834] 	Module class: X.Org Server Extension
[    17.834] 	ABI class: X.Org Server Extension, version 4.0
[    17.834] (II) Loading extension MIT-SCREEN-SAVER
[    17.834] (II) Loading extension XFree86-VidModeExtension
[    17.834] (II) Loading extension XFree86-DGA
[    17.834] (II) Loading extension DPMS
[    17.834] (II) Loading extension XVideo
[    17.834] (II) Loading extension XVideo-MotionCompensation
[    17.834] (II) Loading extension X-Resource
[    17.834] (II) LoadModule: "dbe"
[    17.835] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    17.836] (II) Module dbe: vendor="X.Org Foundation"
[    17.836] 	compiled for 1.9.0, module version = 1.0.0
[    17.836] 	Module class: X.Org Server Extension
[    17.836] 	ABI class: X.Org Server Extension, version 4.0
[    17.836] (II) Loading extension DOUBLE-BUFFER
[    17.836] (II) LoadModule: "glx"
[    17.836] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    18.679] (II) Module glx: vendor="NVIDIA Corporation"
[    18.681] 	compiled for 4.0.2, module version = 1.0.0
[    18.681] 	Module class: X.Org Server Extension
[    18.681] (II) NVIDIA GLX Module  260.19.06  Mon Sep 13 04:54:41 PDT 2010
[    18.681] (II) Loading extension GLX
[    18.681] (II) LoadModule: "record"
[    18.682] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    18.682] (II) Module record: vendor="X.Org Foundation"
[    18.682] 	compiled for 1.9.0, module version = 1.13.0
[    18.682] 	Module class: X.Org Server Extension
[    18.683] 	ABI class: X.Org Server Extension, version 4.0
[    18.683] (II) Loading extension RECORD
[    18.683] (II) LoadModule: "dri"
[    18.683] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    18.684] (II) Module dri: vendor="X.Org Foundation"
[    18.684] 	compiled for 1.9.0, module version = 1.0.0
[    18.684] 	ABI class: X.Org Server Extension, version 4.0
[    18.684] (II) Loading extension XFree86-DRI
[    18.684] (II) LoadModule: "dri2"
[    18.685] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    18.685] (II) Module dri2: vendor="X.Org Foundation"
[    18.685] 	compiled for 1.9.0, module version = 1.2.0
[    18.685] 	ABI class: X.Org Server Extension, version 4.0
[    18.686] (II) Loading extension DRI2
[    18.686] (II) LoadModule: "nvidia"
[    18.686] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    18.738] (II) Module nvidia: vendor="NVIDIA Corporation"
[    18.740] 	compiled for 4.0.2, module version = 1.0.0
[    18.740] 	Module class: X.Org Video Driver
[    18.774] (II) NVIDIA dlloader X Driver  260.19.06  Mon Sep 13 04:31:43 PDT 2010
[    18.774] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    18.774] (++) using VT number 7

[    18.776] (II) Loading sub module "fb"
[    18.776] (II) LoadModule: "fb"
[    18.777] (II) Loading /usr/lib/xorg/modules/libfb.so
[    18.778] (II) Module fb: vendor="X.Org Foundation"
[    18.778] 	compiled for 1.9.0, module version = 1.0.0
[    18.778] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    18.778] (II) Loading sub module "wfb"
[    18.778] (II) LoadModule: "wfb"
[    18.779] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    18.779] (II) Module wfb: vendor="X.Org Foundation"
[    18.779] 	compiled for 1.9.0, module version = 1.0.0
[    18.779] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    18.779] (II) Loading sub module "ramdac"
[    18.779] (II) LoadModule: "ramdac"
[    18.779] (II) Module "ramdac" already built-in
[    18.795] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    18.795] (==) NVIDIA(0): RGB weight 888
[    18.795] (==) NVIDIA(0): Default visual is TrueColor
[    18.795] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    18.796] (**) NVIDIA(0): Option "TwinView" "0"
[    18.796] (**) NVIDIA(0): Option "MetaModes" "1440x900 +0+0"
[    18.796] (**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "CRT-0"
[    18.797] (**) NVIDIA(0): Enabling RENDER acceleration
[    18.797] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    18.797] (II) NVIDIA(0):     enabled.
[    19.537] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[    19.540] (II) NVIDIA(0): NVIDIA GPU ION (C79) at PCI:3:0:0 (GPU-0)
[    19.541] (--) NVIDIA(0): Memory: 524288 kBytes
[    19.541] (--) NVIDIA(0): VideoBIOS: 62.79.65.00.00
[    19.541] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    19.541] (--) NVIDIA(0): Connected display device(s) on ION at PCI:3:0:0
[    19.541] (--) NVIDIA(0):     CRT-0
[    19.541] (--) NVIDIA(0): CRT-0: 300.0 MHz maximum pixel clock
[    19.556] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    19.556] (WW) NVIDIA(0): No valid modes for "1440x900+0+0"; removing.
[    19.556] (WW) NVIDIA(0): 
[    19.556] (WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
[    19.556] (WW) NVIDIA(0):     "nvidia-auto-select".
[    19.556] (WW) NVIDIA(0): 
[    19.556] (II) NVIDIA(0): Validated modes:
[    19.557] (II) NVIDIA(0):     "nvidia-auto-select"
[    19.557] (II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
[    19.580] (WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
[    19.580] (WW) NVIDIA(0):     from CRT-0's EDID.
[    19.580] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    19.580] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    19.580] (--) Depth 24 pixmap format is 32 bpp
[    19.580] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    19.581] (II) NVIDIA(0): Initialized GPU GART.
[    19.587] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    19.664] (II) Loading extension NV-GLX
[    19.722] (II) NVIDIA(0): Initialized OpenGL Acceleration
[    19.726] (==) NVIDIA(0): Disabling shared memory pixmaps
[    19.726] (II) NVIDIA(0): Initialized X Rendering Acceleration
[    19.726] (==) NVIDIA(0): Backing store disabled
[    19.726] (==) NVIDIA(0): Silken mouse enabled
[    19.740] (**) NVIDIA(0): DPMS enabled
[    19.740] (II) Loading extension NV-CONTROL
[    19.741] (II) Loading extension XINERAMA
[    19.741] (II) Loading sub module "dri2"
[    19.742] (II) LoadModule: "dri2"
[    19.743] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[    19.743] (II) NVIDIA(0): [DRI2] Setup complete
[    19.743] (==) RandR enabled
[    19.743] (II) Initializing built-in extension Generic Event Extension
[    19.743] (II) Initializing built-in extension SHAPE
[    19.743] (II) Initializing built-in extension MIT-SHM
[    19.743] (II) Initializing built-in extension XInputExtension
[    19.743] (II) Initializing built-in extension XTEST
[    19.743] (II) Initializing built-in extension BIG-REQUESTS
[    19.743] (II) Initializing built-in extension SYNC
[    19.743] (II) Initializing built-in extension XKEYBOARD
[    19.743] (II) Initializing built-in extension XC-MISC
[    19.743] (II) Initializing built-in extension SECURITY
[    19.743] (II) Initializing built-in extension XINERAMA
[    19.743] (II) Initializing built-in extension XFIXES
[    19.743] (II) Initializing built-in extension RENDER
[    19.743] (II) Initializing built-in extension RANDR
[    19.743] (II) Initializing built-in extension COMPOSITE
[    19.743] (II) Initializing built-in extension DAMAGE
[    19.743] (II) Initializing built-in extension GESTURE
[    19.751] (II) Initializing extension GLX
[    19.972] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    20.000] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    20.000] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.000] (II) LoadModule: "evdev"
[    20.000] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.001] (II) Module evdev: vendor="X.Org Foundation"
[    20.001] 	compiled for 1.9.0, module version = 2.3.2
[    20.001] 	Module class: X.Org XInput Driver
[    20.001] 	ABI class: X.Org XInput driver, version 11.0
[    20.001] (**) Power Button: always reports core events
[    20.002] (**) Power Button: Device: "/dev/input/event1"
[    20.060] (II) Power Button: Found keys
[    20.060] (II) Power Button: Configuring as keyboard
[    20.060] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    20.060] (**) Option "xkb_rules" "evdev"
[    20.060] (**) Option "xkb_model" "pc105"
[    20.060] (**) Option "xkb_layout" "us"
[    20.065] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    20.065] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.065] (**) Power Button: always reports core events
[    20.065] (**) Power Button: Device: "/dev/input/event0"
[    20.140] (II) Power Button: Found keys
[    20.140] (II) Power Button: Configuring as keyboard
[    20.140] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    20.140] (**) Option "xkb_rules" "evdev"
[    20.140] (**) Option "xkb_model" "pc105"
[    20.140] (**) Option "xkb_layout" "us"
[    20.146] (II) config/udev: Adding input device  USB OPTICAL MOUSE (/dev/input/event3)
[    20.146] (**)  USB OPTICAL MOUSE: Applying InputClass "evdev pointer catchall"
[    20.146] (**)  USB OPTICAL MOUSE: always reports core events
[    20.146] (**)  USB OPTICAL MOUSE: Device: "/dev/input/event3"
[    20.220] (II)  USB OPTICAL MOUSE: Found 3 mouse buttons
[    20.220] (II)  USB OPTICAL MOUSE: Found scroll wheel(s)
[    20.220] (II)  USB OPTICAL MOUSE: Found relative axes
[    20.220] (II)  USB OPTICAL MOUSE: Found x and y relative axes
[    20.220] (II)  USB OPTICAL MOUSE: Configuring as mouse
[    20.220] (**)  USB OPTICAL MOUSE: YAxisMapping: buttons 4 and 5
[    20.220] (**)  USB OPTICAL MOUSE: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    20.220] (II) XINPUT: Adding extended input device " USB OPTICAL MOUSE" (type: MOUSE)
[    20.220] (II)  USB OPTICAL MOUSE: initialized for relative axes.
[    20.222] (II) config/udev: Adding input device  USB OPTICAL MOUSE (/dev/input/mouse0)
[    20.222] (II) No input driver/identifier specified (ignoring)
[    20.225] (II) config/udev: Adding input device HP USB Webcam (/dev/input/event4)
[    20.225] (**) HP USB Webcam: Applying InputClass "evdev keyboard catchall"
[    20.225] (**) HP USB Webcam: always reports core events
[    20.225] (**) HP USB Webcam: Device: "/dev/input/event4"
[    20.300] (II) HP USB Webcam: Found keys
[    20.300] (II) HP USB Webcam: Configuring as keyboard
[    20.300] (II) XINPUT: Adding extended input device "HP USB Webcam" (type: KEYBOARD)
[    20.300] (**) Option "xkb_rules" "evdev"
[    20.300] (**) Option "xkb_model" "pc105"
[    20.300] (**) Option "xkb_layout" "us"
[    20.311] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    20.311] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    20.311] (**) AT Translated Set 2 keyboard: always reports core events
[    20.311] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    20.380] (II) AT Translated Set 2 keyboard: Found keys
[    20.380] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    20.380] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    20.380] (**) Option "xkb_rules" "evdev"
[    20.380] (**) Option "xkb_model" "pc105"
[    20.380] (**) Option "xkb_layout" "us"
[    75.199] (II) NVIDIA(0): Setting mode "CRT-0:1360x768@1360x768+0+0"
[    85.451] (II) NVIDIA(0): Setting mode "CRT-0:1152x864@1152x864+0+0"
[   129.831] (II) NVIDIA(0): Setting mode "CRT-0:1360x768@1360x768+0+0"
[   135.315] (II) NVIDIA(0): Setting mode "CRT-0:1152x864@1152x864+0+0"
[   241.620] (II) NVIDIA(0): Setting mode "CRT-0:1360x768@1360x768+0+0"
[   270.905] (II) NVIDIA(0): Setting mode "CRT-0:1360x768@1440x900+0+0"

```
and here is my xorg.conf
```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 260.19.06  (buildd@yellow)  Mon Oct  4 15:59:51 UTC 2010


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
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

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: builtin, VertRefresh source: builtin
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "ION"
EndSection

Section "Screen"

# Removed Option "metamodes" "1440x900 +0+0"
# Removed Option "metamodes" "1360x768 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1360x768 @1440x900 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by VonSpyder on 2010-12-27
you havent installed new drivers for your card recently have you?

---

### Post by zintinio on 2010-12-27
Just today actually.

---

### Post by tjones00 on 2010-12-27
Xorg.0.log stats it cannot gather an edid. This information is provided by your monitor upon probe and lists the resolutions/frequencies hardware specs etc.

Solution, gather an edid.bin from a configuration where the monitor is working properly and use this file with the "customEDID" option in your xorg.conf.

I see you're trying to use custom metamodes the Xorg.0.log is saying it doesn't like them. You could try a modeline in place of an edid, I've never tried metamodes before.

```
[    18.797] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    18.797] (II) NVIDIA(0):     enabled.
[    19.537] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[    19.540] (II) NVIDIA(0): NVIDIA GPU ION (C79) at PCI:3:0:0 (GPU-0)
[    19.541] (--) NVIDIA(0): Memory: 524288 kBytes
[    19.541] (--) NVIDIA(0): VideoBIOS: 62.79.65.00.00
[    19.541] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    19.541] (--) NVIDIA(0): Connected display device(s) on ION at PCI:3:0:0
[    19.541] (--) NVIDIA(0):     CRT-0
[    19.541] (--) NVIDIA(0): CRT-0: 300.0 MHz maximum pixel clock
[    19.556] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    19.556] (WW) NVIDIA(0): No valid modes for "1440x900+0+0"; removing.
[    19.556] (WW) NVIDIA(0): 
[    19.556] (WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
[    19.556] (WW) NVIDIA(0):     "nvidia-auto-select".
[    19.556] (WW) NVIDIA(0): 
[    19.556] (II) NVIDIA(0): Validated modes:
[    19.557] (II) NVIDIA(0):     "nvidia-auto-select"
[    19.557] (II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
[    19.580] (WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
[    19.580] (WW) NVIDIA(0):     from CRT-0's EDID.
[    19.580] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    19.580] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
```Easiest way to get a working edid.bin is sadly to load windows if you have it and grab it from the registry using a 3rd party tool. In linux the easy way is to use nvidia-settings to grab an edid.bin but that depends on your nvidia driver that apparently is having problems getting an edid anyway.

Maybe someone can inform us as to how to gather an edid.bin in linux when the nouveau driver is being used.

---

### Post by VonSpyder on 2010-12-27
yeah I did that once with my ATI card and had this same thing happen.

Try setting a different driver if one is available. hopefully one of them will work. If not youll have to do what I did to fix the problem...

---

### Post by zintinio on 2010-12-28
> **tjones00 said:**
> Xorg.0.log stats it cannot gather an edid. This information is provided by your monitor upon probe and lists the resolutions/frequencies hardware specs etc.

Solution, gather an edid.bin from a configuration where the monitor is working properly and use this file with the "customEDID" option in your xorg.conf.

I see you're trying to use custom metamodes the Xorg.0.log is saying it doesn't like them. You could try a modeline in place of an edid, I've never tried metamodes before.

```
[    18.797] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    18.797] (II) NVIDIA(0):     enabled.
[    19.537] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[    19.540] (II) NVIDIA(0): NVIDIA GPU ION (C79) at PCI:3:0:0 (GPU-0)
[    19.541] (--) NVIDIA(0): Memory: 524288 kBytes
[    19.541] (--) NVIDIA(0): VideoBIOS: 62.79.65.00.00
[    19.541] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    19.541] (--) NVIDIA(0): Connected display device(s) on ION at PCI:3:0:0
[    19.541] (--) NVIDIA(0):     CRT-0
[    19.541] (--) NVIDIA(0): CRT-0: 300.0 MHz maximum pixel clock
[    19.556] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    19.556] (WW) NVIDIA(0): No valid modes for "1440x900+0+0"; removing.
[    19.556] (WW) NVIDIA(0): 
[    19.556] (WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
[    19.556] (WW) NVIDIA(0):     "nvidia-auto-select".
[    19.556] (WW) NVIDIA(0): 
[    19.556] (II) NVIDIA(0): Validated modes:
[    19.557] (II) NVIDIA(0):     "nvidia-auto-select"
[    19.557] (II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
[    19.580] (WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
[    19.580] (WW) NVIDIA(0):     from CRT-0's EDID.
[    19.580] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    19.580] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
```Easiest way to get a working edid.bin is sadly to load windows if you have it and grab it from the registry using a 3rd party tool. In linux the easy way is to use nvidia-settings to grab an edid.bin but that depends on your nvidia driver that apparently is having problems getting an edid anyway.

Maybe someone can inform us as to how to gather an edid.bin in linux when the nouveau driver is being used.

Well, I'll try that actually. I have windows 7 on a small partition, although I rarely use it. I'd still like to find a linux solution for this however. The only problem is that now most of the monitors I use have problems with the driver. As I said, nouveau always works fine, it's the proprietary driver that gets me into this mess >.<

---

### Post by zintinio on 2010-12-28
[http://ubuntuforums.org/archive/index.php/t-884211.html](http://ubuntuforums.org/archive/index.php/t-884211.html)
This looks like it might work.
The problem IS my EDID, on running "sudo get-edid | parse-edid" I get the output:
```

parse-edid: parse-edid version 2.0.0
get-edid: get-edid version 2.0.0

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
	Function supported
	Call successful

	VBE version 300
	VBE string at 0x11100 "NVIDIA"

VBE/DDC service about to be called
	Report DDC capabilities

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
	Function supported
	Call successful

	Monitor and video card combination does not support DDC1 transfers
	Monitor and video card combination does not support DDC2 transfers
	0 seconds per 128 byte EDID block transfer
	Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
	Read EDID

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
	Function supported
	Call failed

The EDID data should not be trusted as the VBE call failed
Error: output block unchanged
parse-edid: IO error reading EDID

```
I got my EDID info from the windows registry. I hate to be completely helpless...but what now? I think I should save it as EDID.bin, but here is the code: 
```

"EDID"=hex:00,ff,ff,ff,ff,ff,ff,00,10,ac,12,40,44,45,44,43,13,10,01,03,0e,22,\
  1b,81,ee,e0,e5,a4,56,45,9a,23,15,50,54,a5,4b,00,71,4f,81,80,01,01,01,01,01,\
  01,01,01,01,01,01,01,30,2a,00,98,51,00,2a,40,30,70,13,00,52,0e,11,00,00,1e,\
  00,00,00,ff,00,43,43,32,38,30,36,35,38,43,44,45,44,0a,00,00,00,fc,00,44,45,\
  4c,4c,20,31,37,30,37,46,50,0a,20,00,00,00,fd,00,38,4c,1e,51,0e,00,0a,20,20,\
  20,20,20,20,00,71


```

---

### Post by BicyclerBoy on 2010-12-28
I don't know how to use the windows registry data hex.

You could try specify the modes directly without EDID/DDC file by adding
(in the appropriate screen section of xorg.conf)
[PHP]
    Option         "ModeValidation" "AllowInterlacedModes"
    Option         "UseEDID" "FALSE"
    Option         "UseDisplayDevice" "CRT-0"
[/PHP]

metamodes should look like this, no @ symbol AFAIK
(in the screen section of xorg.conf)
[PHP]
    Option         "metamodes" "CRT:1920x1080i60 +0+0; CRT:2048x1152i50 +0+0; CRT:1280x720p60 +0+0; CRT:1024x576p50 +0+0; CRT:848x480p60 +0+0"
[/PHP]

---

### Post by BicyclerBoy on 2010-12-28
To read the DDC EDID I2C eeprom from display over VGA or DVI:

for windoze/shell there is:

get-edid.exe
parse-edid.exe

for windoze gui:
winI2C DDC lite      used it many years ago..

These could output a usable file format..

---

### Post by zintinio on 2010-12-28
> **BicyclerBoy said:**
> 
metamodes should look like this, no @ symbol AFAIK
(in the screen section of xorg.conf)
[PHP]
    Option         "metamodes" "CRT:1920x1080i60 +0+0; CRT:2048x1152i50 +0+0; CRT:1280x720p60 +0+0; CRT:1024x576p50 +0+0; CRT:848x480p60 +0+0"
[/PHP]
The @ in the code was an attempt to change my panning resolution.

---

### Post by tjones00 on 2010-12-29
If your monitor has a VGA connection you can attempt to use it with the VGA then run nvidia-settings and get a working edid.bin from there. This worked for some people with corrupt edid.

Post # 10, #12 in this thread. When they mention Nvidia X Server Settings that's nvidia-settings.

[http://ubuntuforums.org/showthread.php?t=883938](http://ubuntuforums.org/showthread.php?t=883938)


I'm still interested in a way of getting a working edid.bin in linux while using nouveau since it seems a lot of people are having edid/resolution issues lately.

---

### Post by zintinio on 2011-01-04
It IS connected over VGA

---

### Post by tjones00 on 2011-01-04
Do you have an alternate connection you could try? (DVI/HDMI)

Random googles for me still haven't found a way to gather an edid in linux without using the nvidia driver and nvidia-settings/xconfig.

Maybe there is a way to gather it with xrandr while using the nouveau driver?

This thread might be of interest.

[http://forums.opensuse.org/english/get-technical-help-here/hardware/443968-graphics-issue-w-11-2-nvidia-unable-get-full-resolution-1680x1050.html](http://forums.opensuse.org/english/get-technical-help-here/hardware/443968-graphics-issue-w-11-2-nvidia-unable-get-full-resolution-1680x1050.html)

Although they resorted to finding an edid.bin online.

I think tinkering with the following in nvidia-xconfig might be worth a shot.
> 
  -E FILE, --extract-edids-from-file=FILE
      Extract any raw EDID byte blocks contained in the specified X log file
      LOG; raw EDID bytes are printed by the NVIDIA X driver to the X log as
      hexidecimal when verbose logging is enabled with the "-logverbose 6" X
      server commandline option.  Any extracted EDIDs are then written as
      binary data to individual files.  These files can later be used by the
      NVIDIA X driver through the "CustomEDID" X configuration option.Maybe there is a way to make nouveau behave the same in the Xorg.0.log with the -logverbose 6 X server commandline option then you could try using that Xorg.0.log to generate a edid.bin with nvidia-xconfig.


nvidia-xconfig -A (advanced help)


```

nvidia-xconfig:  version 260.19.06  (buildmeister@builder101)  Mon Sep 13
07:06:38 PDT 2010
  The NVIDIA X Configuration Tool.

  This program is used to manipulate X configuration files, specifically to
  enable NVIDIA X driver functionality.

  Copyright (C) 2005 - 2010 NVIDIA Corporation.


  In its normal operation, nvidia-xconfig finds the system X configuration file
  (or generates a new X configuration if it cannot find the system file), makes
  sure the configuration is usable by the NVIDIA X driver, applies any updates
  requested on the commandline, and writes the new configuration to file.

  Please see the NVIDIA README for a description of NVIDIA X configuration file
  options.

nvidia-xconfig [options]

  -c XCONFIG, --xconfig=XCONFIG
      Use XCONFIG as the input X config file; if this option is not specified,
      then the same search path used by the X server will be used to find the X
      configuration file.

  -o OUTPUT-XCONFIG, --output-xconfig=OUTPUT-XCONFIG
      Use OUTPUT-XCONFIG as the output X configuration file; if this option is
      not specified, then the input X configuration filename will also be used
      as the output X configuration filename.

  -s, --silent
      Run silently; no messages will be printed to stdout, except for warning
      and error messages to stderr.

  -t, --tree
      Read the X configuration file, print to stdout the X configuration data
      in a tree format, and exit.

  -v, --version
      Print the nvidia-xconfig version and exit.

  -h, --help
      Print usage information for the common commandline options and exit.

  -A, --advanced-help
      Print usage information for the common commandline options as well as the
      advanced options, and then exit.

  --acpid-socket-path=ACPID-SOCKET-PATH, --no-acpid-socket-path
      Set this option to specify an alternate path to the Linux ACPI daemon
      (acpid)'s socket, which the NVIDIA X driver will use to connect to
      acpid.

  --add-argb-glx-visuals, --no-add-argb-glx-visuals
      Enables or disables support for OpenGL rendering into 32-bit ARGB windows
      and pixmaps.

  --allow-glx-with-composite, --no-allow-glx-with-composite
      Enable or disable the "AllowGLXWithComposite" X configuration option.

  --bandwidth-test, --no-bandwidth-test
      Disable or enable the "NoBandWidthTest" X configuration option.

  --busid=BUSID, --no-busid
      This option writes the specified BusID to the device section of the X
      configuration file.  If there are multiple device sections, then it adds
      the BusID field to each of them.  To add the BusID to only a specific
      device or screen section, use the '--device' or '--screen' options.

  --preserve-busid, --no-preserve-busid
      By default, nvidia-xconfig preserves the existing BusID in the X
      configuration file only if there are multiple X screens configured for
      the X server.  Use '--preserve-busid' or '--no-preserve-busid' to force
      the BusID to be preserved or not preserved, overriding the default
      behavior.

  --cool-bits=COOL-BITS, --no-cool-bits
      Enable or disable the "Coolbits" X configuration option.  Setting this
      option will enable support in the NV-CONTROL X extension for manipulating
      GPU clock and GPU fan control settings. Default value is 0.  For fan
      control set it to 4.  WARNING: this may cause system damage and void
      warranties.

  --composite, --no-composite
      Enable or disable the "Composite" X extension.

  --connected-monitor=CONNECTED-MONITOR, --no-connected-monitor
      Enable or disable the  "ConnectedMonitor" X configuration option; setting
      this option forces the X driver to behave as if the specified display
      devices are connected to the GPU.

  --connect-to-acpid, --no-connect-to-acpid
      Enable or disable the "ConnectToAcpid" X configuration option.  If this
      option is set, the NVIDIA X driver will attempt to connect to the Linux
      ACPI daemon (acpid).  Set this option to off to prevent the X driver from
      attempting to connect to acpid.

  --constant-dpi, --no-constant-dpi
      Enable or disable the "ConstantDPI" X configuration option, which
      controls whether the NVIDIA X driver maintains a constant dots per inch
      (DPI) value by recomputing the reported size in millimeters of the X
      screen when XRandR changes the size in pixels of the X screen.

  --custom-edid=CUSTOM-EDID, --no-custom-edid
      Enable or disable the  "CustomEDID" X configuration option; setting this
      option forces the X driver to use the EDID specified.This option is a
      semicolon-separated list of pairs of display device names and filename
      pairs; e.g "CRT-0:\tmp\edid.bin". Note that a display device name must
      always be specified even if only one EDID is specified. 

  --dac-8bit, --no-dac-8bit
      Most Quadro parts by default use a 10 bit color look up table (LUT) by
      default; setting this option to TRUE forces these graphics chips to use
      an 8 bit (LUT).

  -d DEPTH, --depth=DEPTH
      Set the default depth to DEPTH; valid values for DEPTH are 8, 15, 16, 24,
      and 30.

  --device=DEVICE
      The nvidia-xconfig utility operates on one or more devices in the X
      configuration file.  If this option is specified, the device named DEVICE
      in the X configuration file will be used.  If this option is not
      specified, all the devices within the X configuration file will be used.

  --disable-glx-root-clipping, --no-disable-glx-root-clipping
      Disable or enable clipping OpenGL rendering to the root window via the
      "DisableGLXRootClipping" X configuration option.

  --damage-events, --no-damage-events
      Use OS-level events to notify the X server when a direct-rendering client
      has performed rendering that needs to be composited to the screen. 
      Improves performance when using GLX with the composite extension.

  --dynamic-twinview, --no-dynamic-twinview
      Enable or disable support for dynamically configuring TwinView.

  --preserve-driver-name
      By default nvidia-xconfig changes the  display  driver  to "nvidia" for
      all configured X screens; this option preserves the existing driver name
      of each X screen.

  --enable-acpi-hotkeys, --no-enable-acpi-hotkeys
      The "EnableACPIHotkeys" option can be specified to override the NVIDIA X
      driver's default decision to enable or disable ACPI display change hotkey
      events.

  -a, --enable-all-gpus
      Configure an X screen on every GPU in the system.

  --exact-mode-timings-dvi, --no-exact-mode-timings-dvi
      Forces the initialization of the X server with the exact timings
      specified in the ModeLine.

  -E FILE, --extract-edids-from-file=FILE
      Extract any raw EDID byte blocks contained in the specified X log file
      LOG; raw EDID bytes are printed by the NVIDIA X driver to the X log as
      hexidecimal when verbose logging is enabled with the "-logverbose 6" X
      server commandline option.  Any extracted EDIDs are then written as
      binary data to individual files.  These files can later be used by the
      NVIDIA X driver through the "CustomEDID" X configuration option.

  --extract-edids-output-file=FILENAME
      When the '--extract-edids-from-file' option is used, nvidia-xconfig
      writes any extracted EDID to a file, typically "edid.bin" in the current
      directory.  Use this option to specify an alternate filename.  Note that
      nvidia-xconfig, if necessary, will append a unique number to the EDID
      filename, to avoid overwriting existing files (e.g., "edid.bin.1" if
      "edid.bin" already exists).

  --flatpanel-properties=FLATPANEL-PROPERTIES, --no-flatpanel-properties
      Set the flat panel properties. The supported properties are: 'scaling',
      'dithering' & 'ditheringmode'.  Please see the NVIDIA README 'Appendix B.
      X Config Options' for more details on the possible values and syntax.

  --flip, --no-flip
      Enable or disable OpenGL flipping

  --force-generate
      Force generation of a new X config file, ignoring any existing system X
      config file.  This is not typically recommended, as things like the mouse
      protocol, keyboard layout, font paths, etc, are setup by your Unix
      distribution.  While nvidia-xconfig can attempt to infer these values, it
      is best to use your Unix distribution's X config file for the basis of
      anything that nvidia-xconfig creates.

  --force-stereo-flipping, --no-force-stereo-flipping
      Normally, stereo flipping is only performed when a stereo drawable is
      visible. This option forces stereo flipping even when no stereo drawables
      are visible.

  --handle-special-keys=WHEN, --no-handle-special-keys
      Specify when the X server should use the builtin keyboard handler to
      process special key combinations (such as Ctrl+Alt+Backspace); see the X
      configuration man page for details.  The value of WHEN can be 'Always',
      'Never', or 'WhenNeeded'.

  --include-implicit-metamodes, --no-include-implicit-metamodes
      Enable or disable the "IncludeImplicitMetaModes" X configuration option.

  --keyboard=KEYBOARD
      When generating a new X configuration file (which happens when no system
      X configuration file can be found, or the '--force-generate' option is
      specified), use KEYBOARD as the keyboard type, rather than attempting to
      probe the system for the keyboard type.  For a list of possible keyboard
      types, see the '--keyboard-list' option.

  --keyboard-driver=DRIVER
      In most cases nvidia-xconfig can automatically determine the correct
      keyboard driver to use (either 'kbd' or 'keyboard'). Use this option to
      override what nvidia-xconfig detects. Typically, if you are using an
      X.Org X server, use 'kdb'; if you are using an XFree86 X server, use
      'keyboard'.

  --keyboard-list
      Print to stdout the available keyboard types recognized by the
      '--keyboard' option, and then exit.

  --layout=LAYOUT
      The nvidia-xconfig utility operates on a Server Layout within the X
      configuration file.  If this option is specified, the layout named LAYOUT
      in the X configuration file will be used.  If this option is not
      specified, the first Server Layout in the X configuration file is used.

  --logo, --no-logo
      Disable or enable the "NoLogo" X configuration option.

  --logo-path=PATH, --no-logo-path
      Set the path to the PNG file to be used as the logo splash screen at X
      server startup.

  --mode=MODE
      Add the specified mode to the mode list.

  --mode-debug, --no-mode-debug
      Enable or disable the "ModeDebug" X configuration option; when enabled,
      this option causes the X driver to print verbose details about mode
      validation to the X log file.

  --mode-list=MODELIST
      Remove all existing modes from the X configuration's modelist and add the
      one(s) specified in the MODELIST string.

  --remove-mode=MODE
      Remove the specified mode from the mode list.

  --metamodes=METAMODES
      Add the MetaMode X configuration option with the value METAMODES which
      will replace any existing MetaMode option already in the X configuration
      file.

  --mouse=MOUSE
      When generating a new X configuration file (which happens when no system
      X configuration file can be found, or the '--force-generate' option is
      specified), use MOUSE as the mouse type, rather than attempting to probe
      the system for the mouse type.  For a list of possible mouse types, see
      the '--mouse-list' option.

  --mouse-list
      Print to stdout the available mouse types recognized by the '--mouse'
      option, and then exit.

  --multigpu=MULTIGPU, --no-multigpu
      Enable or disable MultiGPU.  Valid values for MULTIGPU are 'Off', 'On',
      'Auto', 'AFR', 'SFR', 'AA'.

  --multisample-compatibility, --no-multisample-compatibility
      Enable or disable the use of separate front and back multisample
      buffers.

  --nvagp=NVAGP, --no-nvagp
      Set the NvAGP X config option value.  Possible values are 0 (no AGP), 1
      (NVIDIA's AGP), 2 (AGPGART), 3 (try AGPGART, then try NVIDIA's AGP);
      these values can also be specified as 'none', 'nvagp', 'agpgart', or
      'any'.

  --nvidia-cfg-path=PATH
      The nvidia-cfg library is used to communicate with the NVIDIA kernel
      module to query basic properties of every GPU in the system.  This
      library is typically only used by nvidia-xconfig when configuring
      multiple X screens.  This option tells nvidia-xconfig where to look for
      this library (in case it cannot find it on its own).  This option should
      normally not be needed.

  --only-one-x-screen
      Disable all but one X screen.

  --overlay, --no-overlay
      Enable or disable the "Overlay" X configuration option.

  --cioverlay, --no-cioverlay
      Enable or disable the color index overlay.

  --overlay-default-visual, --no-overlay-default-visual
      Enable or disable the "OverlayDefaultVisual" X configuration option.

  --transparent-index=INDEX, --no-transparent-index
      Pixel to use as transparent when using color index overlays.  Valid
      values for TRANSPARENT-INDEX are 0-255.

  -T, --post-tree
      Like the '--tree' option, but goes through the full process of applying
      any user requested updates to the X configuration, before printing the
      final configuration to stdout in a tree format.  Effectively, this option
      just causes the configuration to be printed to stdout as a tree instead
      of writing the results to file.

  --power-connector-check, --no-power-connector-check
      Disable or enable the "NoPowerConnectorCheck" X configuration option.

  --probe-all-gpus, --no-probe-all-gpus
      Disable or enable the "ProbeAllGpus" X configuration option.

  --query-gpu-info
      Print information about all recognized NVIDIA GPUs in the system.

  --randr-rotation, --no-randr-rotation
      Enable or disable the "RandRRotation" X configuration option.

  --registry-dwords=REGISTRY-DWORDS, --no-registry-dwords
      Enable or disable the "RegistryDwords" X configuration option.

  --render-accel, --no-render-accel
      Enable or disable the "RenderAccel" X configuration option.

  --render-extension, --no-render-extension
      Disable or enable the "NoRenderExtension" X configuration option.

  --rotate=ROTATE, --no-rotate
      Enable or disable the "Rotate" X configuration option.  Valid values for
      ROTATE are 'normal', 'left', 'CCW', 'inverted', 'right', and 'CW'. 
      Rotation can be disabled 

  --screen=SCREEN
      The nvidia-xconfig utility operates on one or more screens within a
      Server Layout in the X configuration file.  If this option is specified,
      the screen named SCREEN in the X configuration file will be used.  If
      this option is not specified, all screens within the selected Server
      Layout in the X configuration file will be used used.

  --separate-x-screens, --no-separate-x-screens
      A GPU that supports multiple simultaneous display devices can either
      drive these display devices in TwinView, or as separate X screens.  When
      the '--separate-x-screens' option is specified, each GPU on which an X
      screen is currently configured will be updated to have two X screens
      configured.  The '--no-separate-x-screens' option will remove the second
      configured X screen on each GPU.  Please see the NVIDIA README
      description of "Separate X Screens on One GPU" for further details.

  --sli=SLI, --no-sli
      Enable or disable SLI.  Valid values for SLI are 'Off', 'On', 'Auto',
      'AFR', 'SFR', 'AA', 'AFRofAA', 'Mosaic'.

  --stereo=STEREO, --no-stereo
      Enable or disable the stereo mode.  Valid values for STEREO are: 0
      (Disabled), 1 (DDC glasses), 2 (Blueline glasses), 3 (Onboard stereo), 4
      (TwinView clone mode stereo), 5 (SeeReal digital flat panel), 6 (Sharp3D
      digital flat panel), 7 (Arisawa/Hyundai/Zalman/Pavione/Miracube), 8 (3D
      DLP), 9 (3D DLP INV), 10 (NVIDIA 3D VISION).

  --thermal-configuration-check, --no-thermal-configuration-check
      Disable or enable the "ThermalConfigurationCheck" X configuration
      option.

  --tv-standard=TV-STANDARD, --no-tv-standard
      Enable or disable the "TVStandard" X configuration option. Valid values
      for "TVStandard" are: "PAL-B", "PAL-D", "PAL-G", "PAL-H", "PAL-I",
      "PAL-K1", "PAL-M", "PAL-N", "PAL-NC", "NTSC-J", "NTSC-M", "HD480i",
      "HD480p", "HD720p", "HD1080i", "HD1080p", "HD576i", "HD576p".

  --tv-out-format=TV-OUT-FORMAT, --no-tv-out-format
      Enable or disable the "TVOutFormat" X configuration option. Valid values
      for "TVOutFormat" are: "SVIDEO" and "COMPOSITE".

  --tv-over-scan=TV-OVER-SCAN, --no-tv-over-scan
      Enable or disable the "TVOverScan" X configuration option. Valid values
      are decimal values in the range 1.0 and 0.0.

  --twinview, --no-twinview
      Enable or disable TwinView.

  --twinview-orientation=ORIENTATION, --no-twinview-orientation
      Specify the TwinViewOrientation.  Valid values for ORIENTATION are:
      "RightOf" (the default), "LeftOf", "Above", "Below", or "Clone".

  --twinview-xinerama-info, --no-twinview-xinerama-info
      Prohibits providing Xinerama information when in TwinView.

  --twinview-xinerama-info-order=TWINVIEW-XINERAMA-INFO-ORDER,
  --no-twinview-xinerama-info-order
      Enable or disable the "TwinViewXineramaInfoOrder" X configuration option.
      TWINVIEW-XINERAMA-INFO-ORDER is a comma-separated list of display device
      names that describe the order in which TwinViewXineramaInfo should be
      reported.  E.g., "CRT, DFP, TV".

  --ubb, --no-ubb
      Enable or disable the "UBB" X configuration option.

  --use-edid, --no-use-edid
      Enable or disable use of the EDID (Extended Display Identification Data)
      from your display device(s).  The EDID will be used for driver operations
      such as building lists of available modes, determining valid frequency
      ranges, and computing the DPI (Dots Per Inch).  This option defaults to
      TRUE (the NVIDIA X driver will use the EDID, when available).  It is NOT
      recommended that you use this option to globally disable use of the EDID;
      instead, use '--no-use-edid-freqs' or '--no-use-edid-dpi' to disable
      specific uses of the EDID.

  --use-edid-dpi, --no-use-edid-dpi
      Enable or disable use of the physical size information in the display
      device's EDID, if any, to compute the DPI (Dots Per Inch) of the X
      screen.  This option defaults to TRUE (the NVIDIA X driver uses the
      EDID's physical size, when available, to compute the DPI).

  --use-edid-freqs, --no-use-edid-freqs
      Enable or disable use of the HorizSync and VertRefresh ranges given in a
      display device's EDID, if any.  EDID provided range information will
      override the HorizSync and VertRefresh ranges specified in the Monitor
      section.  This option defaults to TRUE (the NVIDIA X driver will use
      frequency information from the EDID, when available).

  --use-int10-module, --no-use-int10-module
      Enable use of the X Int10 module to soft-boot all secondary cards, rather
      than POSTing the cards through the NVIDIA kernel module.

  --use-display-device=DISPLAY-DEVICE, --no-use-display-device
      Force the X driver to use the display device specified.

  --use-events, --no-use-events
      Enable or disable "UseEvents" X configuration option. Setting this option
      will enable the X driver to use the system events in some cases when it
      is waiting for the hardware. With this option X driver sets an event
      handler and waits for the hardware through the poll() system call. This
      option defaults to FALSE.

  --virtual=WIDTHxHEIGHT, --no-virtual
      Specify the virtual screen resolution.

  --x-prefix=X-PREFIX
      The X installation prefix; the default is /usr/X11R6/.  Only under rare
      circumstances should this option be needed.

  --xinerama, --no-xinerama
      Enable or disable Xinerama.

  --xvmc-uses-textures, --no-xvmc-uses-textures
      Forces XvMC to use the 3D engine for XvMCPutSurface requests rather than
      the video overlay.

  --color-space=COLORSPACE, --no-color-space
      Enable or disable the "ColorSpace" X configuration option. Valid values
      for "COLORSPACE" are: "RGB" and "YCbCr444".

  --color-range=COLORRANGE, --no-color-range
      Sets the "ColorRange" X configuration option. Valid values for
      "COLORRANGE" are: "Full" and "Limited".

```

---

### Post by tjones00 on 2011-01-04
Ok this might work IF you are using a 32b system. If you are using 64b this won't work.

sudo apt-get install read-edid

Or install read-edid via Synaptic Package Manager.

Installs a package that has two programs get-edid and parse-edid.

man for get-edid/parse-edid


```
get-edid(1)                                                        get-edid(1)
NAME
       get-edid,  parse-edid - read-edid tools to retrieve and interpret moni&#8208;
       tor specifications using the VESA VBE DDC protocol

SYNOPSIS
       get-edid | parse-edid
       get-edid > filename
       parse-edid < filename

DESCRIPTION
       The read-edid utility comprises two tools: get-edid and parse-edid.

       get-edid uses Linux's vm86(2) system call to enter  virtual  8086  mode
       and  perform  Data  Display Channel (DDC) transfers using the VESA BIOS
       Extensions (VBE) to retrieve information from monitors, including iden&#8208;
       tification  strings,  supported sync ranges, available video modes, and
       video mode parameters.  Such information is often useful for  configur&#8208;
       ing X Window System servers such as XFree86.

       The  data obtained by get-edid is in a binary format, so the parse-edid
       command is available to interpret  it  and  generate  a  human-readable
       block  of  text  information  that  can  also be included in an XFree86
       XF86Config file.

       It is customary to invoke get-edid and parse-edid together in  a  pipe&#8208;
       line.

       get-edid  and  parse-edid  accept  no options, recognize no environment
       variables, read no input files, and create no output files.

AUTHOR
       get-edid and parse-edid were written by John  Fremlin,  Dan  Hugo,  and
       Martin  Kavalec,  using the LRMI (Linux Real-Mode Interface) library by
       Josh Vanderhoof.  This manual page was  written  by  Branden  Robinson,
       originally for Debian GNU/Linux.

SEE ALSO
       vm86(2)

       John              Fremlin's              read-edid              website
       &#10216;http://john.fremlin.de/programs/linux/read-edid/&#10217; at http://john.frem&#8208;
       lin.de/programs/linux/read-edid/

Debian GNU/Linux                  2002-10-03                       get-edid(1)

```


First check that get-edid can gather a proper resolution. This should be independent of any active display driver.

```
sudo get-edid | parse-edid
```

If that looks fine (parse-edid will display resolutions) you can use get-edid to create an edid.bin binary file.
```

sudo get-edit > edid.bin
```

Now use that file with CustomEDID in xorg.conf.


If the results of parse-edid don't look good try uninstalling nvidia and check get-edid | parse-edid with nouveau running and see if it looks any different. If it looks good with nouveau grab the edid.bin with get-edid.

---

### Post by zintinio on 2011-01-08
Sounds like a plan. I'll do it later tonight.

---

### Post by BicyclerBoy on 2011-01-08
Your edid dat can be parsed..
cat edid.text | parse-edid

The errors & output is attached
The EDID data is incomplete, should be way bigger...

This linux forum requires that you use dos file name extensions !


If all else fails..this should work.

If you want to try to stop mode validating against the EDID then :
edit /etc/X11/xorg.conf

Code:

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "ModeValidation" "NoEdidModes"
    Option         "ModeValidation" "AllowInterlacedModes"
    Option         "UseEDID" "FALSE"
    Option         "UseDisplayDevice" "CRT-0"
    Option "TVStandard" "HD1080p"
    SubSection     "Display"
        Depth       24
        Modes      "HD1080p"
    EndSubSection
EndSection

This assumes your TV is 1080p capable..
"HD720p" "HD1080i" are valid built-in TV video modes.

The"DFP-0" may not match the wired ports of your video card, may need "CRT-1".
You may need to try these commands as well:
Option "IgnoreEDID" "True" # not used anymore ?
Option "ConnectedMonitor" "DFP-0" # not recommended as overwrite scan

Please note the attached edid.txt is complete rubbish ..

---

### Post by BicyclerBoy on 2011-01-08
There is a newer version with i2c support code for newer video cards..

[http://www.polypux.org/projects/read-edid/](http://www.polypux.org/projects/read-edid/)

download read-edid-i2c.tar.gz

Does not work, think need kernel space module i2c interface

---

