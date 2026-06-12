---
title: "problem with resolution after each restart"
date: 2011-10-07
forum: Multimedia Software
---

### Post by pko76 on 2011-10-07
i have ubuntu 10.04 installed in my pc and i have a new acer 18.5 monitor .the graphic card is nvidia 6600 gt.when i select 1368x768 resolution which is the apropriate for the monitor i have this problem .each next time i switch on my pc and after the loading of ubuntu the resolution has changed to 1024x768.i use the save to x configuration file from the nvidia menu for the 1368x768 resolution but the problem continues

---

### Post by BicyclerBoy on 2011-10-07
Try using a DVI cable.
Post your
/var/log/Xorg.0.log file ..

---

### Post by pko76 on 2011-10-08
> **BicyclerBoy said:**
> Try using a DVI cable.
Post your
/var/log/Xorg.0.log file ..

```
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux kostas-desktop 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:08:37 UTC 2011 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-33-generic root=UUID=e27fd5d7-7485-43ea-aa61-c73894fc84ab ro splash quiet vga=768 quiet splash vt.handoff=7
Build Date: 08 March 2011  08:22:50AM
xorg-server 2:1.7.6-2ubuntu7.6 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Oct  8 20:50:00 2011
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
(II) Loader magic: 0x81f1e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0140:1043:81cf nVidia Corporation NV43 [GeForce 6600 GT] rev 162, Mem @ 0xc0000000/67108864, 0xb0000000/268435456, 0xc4000000/16777216, BIOS @ 0x????????/131072
(--) PCI: (0:5:7:0) 109e:036e:107d:6606 Brooktree Corporation Bt878 Video Capture rev 17, Mem @ 0xc9001000/4096
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
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 10:38:29 PDT 2010
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
(II) NVIDIA dlloader X Driver  195.36.24  Thu Apr 22 09:34:29 PDT 2010
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
(**) NVIDIA(0): Option "MetaModes" "nvidia-auto-select +0+0; 1368x768_60 +0+0; 1360x768_60_0 +0+0; 1360x768 +0+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "CRT-0"
(**) Oct 08 20:50:02 NVIDIA(0): Enabling RENDER acceleration
(II) Oct 08 20:50:02 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Oct 08 20:50:02 NVIDIA(0):     enabled.
(II) Oct 08 20:50:03 NVIDIA(0): NVIDIA GPU GeForce 6600 GT (NV43) at PCI:1:0:0 (GPU-0)
(--) Oct 08 20:50:03 NVIDIA(0): Memory: 262144 kBytes
(--) Oct 08 20:50:03 NVIDIA(0): VideoBIOS: 05.43.02.66.00
(II) Oct 08 20:50:03 NVIDIA(0): Detected PCI Express Link width: 16X
(--) Oct 08 20:50:03 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Oct 08 20:50:03 NVIDIA(0): Connected display device(s) on GeForce 6600 GT at PCI:1:0:0:
(--) Oct 08 20:50:03 NVIDIA(0):     Acer V193HQL (CRT-0)
(--) Oct 08 20:50:03 NVIDIA(0): Acer V193HQL (CRT-0): 400.0 MHz maximum pixel clock
(II) Oct 08 20:50:03 NVIDIA(0): Assigned Display Device: CRT-0
(II) Oct 08 20:50:03 NVIDIA(0): Validated modes:
(II) Oct 08 20:50:03 NVIDIA(0):     "nvidia-auto-select+0+0"
(II) Oct 08 20:50:03 NVIDIA(0):     "1368x768_60+0+0"
(II) Oct 08 20:50:03 NVIDIA(0):     "1360x768_60_0+0+0"
(II) Oct 08 20:50:03 NVIDIA(0):     "1360x768+0+0"
(II) Oct 08 20:50:03 NVIDIA(0): Virtual screen size determined to be 1368 x 768
(--) Oct 08 20:50:03 NVIDIA(0): DPI set to (84, 84); computed from "UseEdidDpi" X config
(--) Oct 08 20:50:03 NVIDIA(0):     option
(==) Oct 08 20:50:03 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) Oct 08 20:50:03 NVIDIA(0): Initialized GPU GART.
(II) Oct 08 20:50:03 NVIDIA(0): Setting mode "nvidia-auto-select+0+0"
(II) Loading extension NV-GLX
(II) Oct 08 20:50:03 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Oct 08 20:50:03 NVIDIA(0): Initialized X Rendering Acceleration
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
(**) Option "xkb_layout" "us,gr"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle"
(II) XKB: reuse xkmfile /var/lib/xkb/server-2156C348D00BE8697CB61D35435664E83FBF50F7.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us,gr"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle"
(II) config/udev: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) (/dev/input/event4)
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Applying InputClass "evdev pointer catchall"
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): always reports core events
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Device: "/dev/input/event4"
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found 3 mouse buttons
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found scroll wheel(s)
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found relative axes
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found x and y relative axes
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Configuring as mouse
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)" (type: MOUSE)
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): initialized for relative axes.
(II) config/udev: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device bttv IR (card=34) (/dev/input/event5)
(**) bttv IR (card=34): Applying InputClass "evdev keyboard catchall"
(**) bttv IR (card=34): always reports core events
(**) bttv IR (card=34): Device: "/dev/input/event5"
(II) bttv IR (card=34): Found keys
(II) bttv IR (card=34): Configuring as keyboard
(II) XINPUT: Adding extended input device "bttv IR (card=34)" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us,gr"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle"
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us,gr"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle"
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
(II) config/udev: Adding input device Mouseemu virtual keyboard (/dev/input/event6)
(**) Mouseemu virtual keyboard: Applying InputClass "evdev keyboard catchall"
(**) Mouseemu virtual keyboard: always reports core events
(**) Mouseemu virtual keyboard: Device: "/dev/input/event6"
(II) Mouseemu virtual keyboard: Found keys
(II) Mouseemu virtual keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Mouseemu virtual keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us,gr"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle"
(II) config/udev: Adding input device Mouseemu virtual mouse (/dev/input/event7)
(**) Mouseemu virtual mouse: Applying InputClass "evdev pointer catchall"
(**) Mouseemu virtual mouse: always reports core events
(**) Mouseemu virtual mouse: Device: "/dev/input/event7"
(II) Mouseemu virtual mouse: Found 3 mouse buttons
(II) Mouseemu virtual mouse: Found scroll wheel(s)
(II) Mouseemu virtual mouse: Found relative axes
(II) Mouseemu virtual mouse: Found x and y relative axes
(II) Mouseemu virtual mouse: Configuring as mouse
(**) Mouseemu virtual mouse: YAxisMapping: buttons 4 and 5
(**) Mouseemu virtual mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Mouseemu virtual mouse" (type: MOUSE)
(II) Mouseemu virtual mouse: initialized for relative axes.
(II) config/udev: Adding input device Mouseemu virtual mouse (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) Oct 08 20:50:22 NVIDIA(0): Setting mode "1024x768"
(II) Oct 08 21:18:09 NVIDIA(0): Setting mode "nvidia-auto-select+0+0"

```

---

### Post by BicyclerBoy on 2011-10-08
That monitor is a 16:9 TV format panel (cheap mass produced), not an ideal good computer monitor.

The nVidia drivers seem to have constantly changing behaviour with the unusual cases..

Not sure what the problem is:
- driver reads the EDID okay
- has validated modes 1368x768 & 1360x768 (real modes)
- at the last minute uses the 1024x768 mode (std 4:3)

The monitor native res of 1366x768 is not a std video mode.

If you use a DVI or DVI-D(single link)-to-HDMI(19pin) cable you may not have any problem.

Can force the right video mode in /etc/X11/xorg.conf file so post that as well...

---

### Post by pko76 on 2011-10-09
> **BicyclerBoy said:**
> That monitor is a 16:9 TV format panel (cheap mass produced), not an ideal good computer monitor.

The nVidia drivers seem to have constantly changing behaviour with the unusual cases..

Not sure what the problem is:
- driver reads the EDID okay
- has validated modes 1368x768 & 1360x768 (real modes)
- at the last minute uses the 1024x768 mode (std 4:3)

The monitor native res of 1366x768 is not a std video mode.

If you use a DVI or DVI-D(single link)-to-HDMI(19pin) cable you may not have any problem.

Can force the right video mode in /etc/X11/xorg.conf file so post that as well...

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Fri Apr  9 10:35:18 UTC 2010

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
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer V193HQL"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6600 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "nvidia-auto-select +0+0; 1368x768_60 +0+0; 1360x768_60_0 +0+0; 1360x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```
i don't think my acer 193hql supports hdmi

---

