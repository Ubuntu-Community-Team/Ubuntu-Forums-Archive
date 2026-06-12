---
title: "Two monitors with two video cards 10.10"
date: 2010-12-12
forum: Multimedia Software
---

### Post by robbie d on 2010-12-12
Hi people,
I've sort of posted bits of information about my problem, but now I think I have enough information to get some help.
I built a 2 video card (PCI-E) desktop machine about a year ago. Setup dual boot xp and Ubuntu. Was running Jaunty and Karmic fine on two screens (separate x screens and then xinerama) until Lucid. I could not get both screens to work.
If I do lspci, Both cards are found along with the relevant PCI address. 
My xorg.conf file contains both monitors and both video cards, but under server layout, only one monitor is referenced.
Can someone please help me sort out my conf file.
I eventually want to populate this pc with 4 monitors but at this stage having 2 working would be great.
Cheers
Rob

---

### Post by tjones00 on 2010-12-13
We would need to know what driver and cards you're using. Also if you could post the following it would help.

xorg.conf      /etc/X11/xorg.conf

Xorg.0.log     /var/log/Xorg.0.log

lsmod might help as well so we can determine what driver really is in use and there are no conflicts.

---

### Post by robbie d on 2010-12-13
using the latest nvidia drivers 260.19.21

two 9500GT 1gig cards
__________________________________________________________________________
**Xorg.conf:**

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath      "/usr/lib/xorg/modules"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath        "built-ins"
EndSection

Section "Module"
    Load           "extmod"
    Load           "dbe"
    Load           "glx"
    Load           "dri2"
    Load           "record"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/input/mice"
    Option         "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Monitor Vendor"
    ModelName      "Monitor Model"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Monitor Vendor"
    ModelName      "Monitor Model"
EndSection

Section "Device"

        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "HWcursor"           	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "UseFBDev"           	# [<bool>]
        #Option     "Rotate"             	# [<str>]
        #Option     "VideoKey"           	# <i>
        #Option     "FlatPanel"          	# [<bool>]
        #Option     "FPDither"           	# [<bool>]
        #Option     "CrtcNumber"         	# <i>
        #Option     "FPScale"            	# [<bool>]
        #Option     "FPTweak"            	# <i>
        #Option     "DualHead"           	# [<bool>]
    Identifier     "Card0"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"

        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "HWcursor"           	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "UseFBDev"           	# [<bool>]
        #Option     "Rotate"             	# [<str>]
        #Option     "VideoKey"           	# <i>
        #Option     "FlatPanel"          	# [<bool>]
        #Option     "FPDither"           	# [<bool>]
        #Option     "CrtcNumber"         	# <i>
        #Option     "FPScale"            	# [<bool>]
        #Option     "FPTweak"            	# <i>
        #Option     "DualHead"           	# [<bool>]
    Identifier     "Card1"
    Driver         "nvidia"
    BusID          "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Card0"
    Monitor        "Monitor0"
    SubSection     "Display"
        Viewport    0 0
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       4
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       8
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       15
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       16
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Card1"
    Monitor        "Monitor1"
    SubSection     "Display"
        Viewport    0 0
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       4
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       8
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       15
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       16
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       24
    EndSubSection
EndSection
________________________________________________________________```
__________
[   225.517] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[   225.518] X Protocol Version 11, Revision 0
[   225.518] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[   225.518] Current Operating System: Linux megabox-desktop 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686
[   225.518] Kernel command line: root=UUID=17cd22de-d4d4-40ad-8e1b-81b0460d6081 ro quiet splash 
[   225.518] Build Date: 23 November 2010  09:54:06PM
[   225.519] xorg-server 2:1.9.0-0ubuntu7.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[   225.519] Current version of pixman: 0.18.4
[   225.519] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[   225.519] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   225.520] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Dec 13 17:25:27 2010
[   225.521] (==) Using config file: "/etc/X11/xorg.conf"
[   225.521] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   225.522] (==) ServerLayout "X.org Configured"
[   225.522] (**) |-->Screen "Screen0" (0)
[   225.522] (**) |   |-->Monitor "Monitor0"
[   225.523] (**) |   |-->Device "Card0"
[   225.523] (**) |-->Screen "Screen1" (1)
[   225.523] (**) |   |-->Monitor "Monitor1"
[   225.523] (**) |   |-->Device "Card1"
[   225.523] (**) |-->Input Device "Mouse0"
[   225.523] (**) |-->Input Device "Keyboard0"
[   225.523] (==) Automatically adding devices
[   225.523] (==) Automatically enabling devices
[   225.524] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   225.524] 	Entry deleted from font path.
[   225.524] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   225.524] 	Entry deleted from font path.
[   225.524] (**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[   225.524] (**) ModulePath set to "/usr/lib/xorg/modules"
[   225.524] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[   225.524] (WW) Disabling Mouse0
[   225.524] (WW) Disabling Keyboard0
[   225.524] (II) Loader magic: 0x81f8e00
[   225.524] (II) Module ABI versions:
[   225.524] 	X.Org ANSI C Emulation: 0.4
[   225.524] 	X.Org Video Driver: 8.0
[   225.524] 	X.Org XInput driver : 11.0
[   225.524] 	X.Org Server Extension : 4.0
[   225.525] (--) PCI:*(0:1:0:0) 10de:0640:1043:829a rev 161, Mem @ 0xf7000000/16777216, 0xc0000000/268435456, 0xf4000000/33554432, I/O @ 0x0000bc00/128, BIOS @ 0x????????/524288
[   225.525] (--) PCI: (0:2:0:0) 10de:0640:1043:829a rev 161, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/524288
[   225.525] (II) Open ACPI successful (/var/run/acpid.socket)
[   225.525] (II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
[   225.525] (II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
[   225.525] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[   225.525] (II) "record" will be loaded. This was enabled by default and also specified in the config file.
[   225.525] (II) "dri" will be loaded by default.
[   225.525] (II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
[   225.525] (II) LoadModule: "extmod"
[   225.526] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   225.526] (II) Module extmod: vendor="X.Org Foundation"
[   225.526] 	compiled for 1.9.0, module version = 1.0.0
[   225.526] 	Module class: X.Org Server Extension
[   225.526] 	ABI class: X.Org Server Extension, version 4.0
[   225.526] (II) Loading extension MIT-SCREEN-SAVER
[   225.526] (II) Loading extension XFree86-VidModeExtension
[   225.526] (II) Loading extension XFree86-DGA
[   225.526] (II) Loading extension DPMS
[   225.526] (II) Loading extension XVideo
[   225.526] (II) Loading extension XVideo-MotionCompensation
[   225.526] (II) Loading extension X-Resource
[   225.526] (II) LoadModule: "dbe"
[   225.526] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   225.526] (II) Module dbe: vendor="X.Org Foundation"
[   225.526] 	compiled for 1.9.0, module version = 1.0.0
[   225.526] 	Module class: X.Org Server Extension
[   225.526] 	ABI class: X.Org Server Extension, version 4.0
[   225.526] (II) Loading extension DOUBLE-BUFFER
[   225.526] (II) LoadModule: "glx"
[   225.526] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   225.540] (II) Module glx: vendor="NVIDIA Corporation"
[   225.540] 	compiled for 4.0.2, module version = 1.0.0
[   225.540] 	Module class: X.Org Server Extension
[   225.540] (II) NVIDIA GLX Module  260.19.21  Thu Nov  4 20:52:05 PDT 2010
[   225.540] (II) Loading extension GLX
[   225.540] (II) LoadModule: "dri2"
[   225.540] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   225.540] (II) Module dri2: vendor="X.Org Foundation"
[   225.540] 	compiled for 1.9.0, module version = 1.2.0
[   225.540] 	ABI class: X.Org Server Extension, version 4.0
[   225.540] (II) Loading extension DRI2
[   225.540] (II) LoadModule: "record"
[   225.540] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   225.540] (II) Module record: vendor="X.Org Foundation"
[   225.540] 	compiled for 1.9.0, module version = 1.13.0
[   225.540] 	Module class: X.Org Server Extension
[   225.540] 	ABI class: X.Org Server Extension, version 4.0
[   225.540] (II) Loading extension RECORD
[   225.540] (II) LoadModule: "dri"
[   225.541] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   225.541] (II) Module dri: vendor="X.Org Foundation"
[   225.541] 	compiled for 1.9.0, module version = 1.0.0
[   225.541] 	ABI class: X.Org Server Extension, version 4.0
[   225.541] (II) Loading extension XFree86-DRI
[   225.541] (II) LoadModule: "nvidia"
[   225.541] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[   225.541] (II) Module nvidia: vendor="NVIDIA Corporation"
[   225.541] 	compiled for 4.0.2, module version = 1.0.0
[   225.541] 	Module class: X.Org Video Driver
[   225.970] (II) NVIDIA dlloader X Driver  260.19.21  Thu Nov  4 20:26:43 PDT 2010
[   225.970] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   225.970] (--) using VT number 8

[   225.981] (II) Loading sub module "fb"
[   225.981] (II) LoadModule: "fb"
[   225.982] (II) Loading /usr/lib/xorg/modules/libfb.so
[   225.982] (II) Module fb: vendor="X.Org Foundation"
[   225.982] 	compiled for 1.9.0, module version = 1.0.0
[   225.982] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   225.982] (II) Loading sub module "wfb"
[   225.982] (II) LoadModule: "wfb"
[   225.983] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   225.983] (II) Module wfb: vendor="X.Org Foundation"
[   225.983] 	compiled for 1.9.0, module version = 1.0.0
[   225.983] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   225.983] (II) Loading sub module "ramdac"
[   225.983] (II) LoadModule: "ramdac"
[   225.983] (II) Module "ramdac" already built-in
[   225.984] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[   225.984] (==) NVIDIA(0): RGB weight 888
[   225.984] (==) NVIDIA(0): Default visual is TrueColor
[   225.984] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   225.984] (**) NVIDIA(0): Enabling RENDER acceleration
[   225.984] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[   225.984] (II) NVIDIA(0):     enabled.
[   227.588] (II) NVIDIA(0): NVIDIA GPU GeForce 9500 GT (G96) at PCI:1:0:0 (GPU-0)
[   227.588] (--) NVIDIA(0): Memory: 1048576 kBytes
[   227.588] (--) NVIDIA(0): VideoBIOS: 62.94.4b.00.00
[   227.588] (II) NVIDIA(0): Detected PCI Express Link width: 8X
[   227.588] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[   227.588] (--) NVIDIA(0): Connected display device(s) on GeForce 9500 GT at PCI:1:0:0
[   227.588] (--) NVIDIA(0):     Acer AL2216W (CRT-1)
[   227.588] (--) NVIDIA(0): Acer AL2216W (CRT-1): 400.0 MHz maximum pixel clock
[   227.643] (II) NVIDIA(0): Assigned Display Device: CRT-1
[   227.643] (==) NVIDIA(0): 
[   227.643] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[   227.643] (==) NVIDIA(0):     will be used as the requested mode.
[   227.643] (==) NVIDIA(0): 
[   227.643] (II) NVIDIA(0): Validated modes:
[   227.643] (II) NVIDIA(0):     "nvidia-auto-select"
[   227.643] (II) NVIDIA(0): Virtual screen size determined to be 1680 x 1050
[   227.670] (--) NVIDIA(0): DPI set to (90, 88); computed from "UseEdidDpi" X config
[   227.670] (--) NVIDIA(0):     option
[   227.670] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[   227.670] (==) NVIDIA(1): Depth 24, (==) framebuffer bpp 32
[   227.670] (==) NVIDIA(1): RGB weight 888
[   227.670] (==) NVIDIA(1): Default visual is TrueColor
[   227.670] (==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
[   227.670] (**) NVIDIA(1): Enabling RENDER acceleration
[   228.717] (EE) NVIDIA(1): Failed to initialize the NVIDIA GPU at PCI:2:0:0.  Please
[   228.717] (EE) NVIDIA(1):     check your system's kernel log for additional error
[   228.717] (EE) NVIDIA(1):     messages and refer to Chapter 8: Common Problems in the
[   228.717] (EE) NVIDIA(1):     README for additional information.
[   228.717] (EE) NVIDIA(1): Failed to initialize the NVIDIA graphics device!
[   228.717] (II) UnloadModule: "nvidia"
[   228.717] (II) UnloadModule: "wfb"
[   228.717] (II) UnloadModule: "fb"
[   228.717] (--) Depth 24 pixmap format is 32 bpp
[   228.718] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[   228.861] (EE) NVIDIA(GPU-1): Failed to initialize the NVIDIA GPU at PCI:2:0:0.  Please
[   228.861] (EE) NVIDIA(GPU-1):     check your system's kernel log for additional error
[   228.861] (EE) NVIDIA(GPU-1):     messages and refer to Chapter 8: Common Problems in the
[   228.861] (EE) NVIDIA(GPU-1):     README for additional information.
[   228.861] (EE) NVIDIA(GPU-1): Failed to initialize the NVIDIA graphics device!
[   228.863] (II) NVIDIA(0): Initialized GPU GART.
[   228.872] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[   228.907] (II) Loading extension NV-GLX
[   228.923] (II) NVIDIA(0): Initialized OpenGL Acceleration
[   228.928] (==) NVIDIA(0): Disabling shared memory pixmaps
[   228.928] (II) NVIDIA(0): Initialized X Rendering Acceleration
[   228.928] (==) NVIDIA(0): Backing store disabled
[   228.928] (==) NVIDIA(0): Silken mouse enabled
[   228.941] (==) NVIDIA(0): DPMS enabled
[   228.941] (II) Loading extension NV-CONTROL
[   228.942] (II) Loading extension XINERAMA
[   228.942] (II) Loading sub module "dri2"
[   228.942] (II) LoadModule: "dri2"
[   228.942] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[   228.942] (II) NVIDIA(0): [DRI2] Setup complete
[   228.942] (==) RandR enabled
[   228.942] (II) Initializing built-in extension Generic Event Extension
[   228.942] (II) Initializing built-in extension SHAPE
[   228.942] (II) Initializing built-in extension MIT-SHM
[   228.942] (II) Initializing built-in extension XInputExtension
[   228.942] (II) Initializing built-in extension XTEST
[   228.942] (II) Initializing built-in extension BIG-REQUESTS
[   228.942] (II) Initializing built-in extension SYNC
[   228.942] (II) Initializing built-in extension XKEYBOARD
[   228.942] (II) Initializing built-in extension XC-MISC
[   228.942] (II) Initializing built-in extension SECURITY
[   228.942] (II) Initializing built-in extension XINERAMA
[   228.942] (II) Initializing built-in extension XFIXES
[   228.942] (II) Initializing built-in extension RENDER
[   228.942] (II) Initializing built-in extension RANDR
[   228.942] (II) Initializing built-in extension COMPOSITE
[   228.942] (II) Initializing built-in extension DAMAGE
[   228.942] (II) Initializing built-in extension GESTURE
[   228.944] (II) Initializing extension GLX
[   228.985] (II) XKB: generating xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   229.021] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   229.021] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   229.021] (II) LoadModule: "evdev"
[   229.022] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   229.022] (II) Module evdev: vendor="X.Org Foundation"
[   229.022] 	compiled for 1.9.0, module version = 2.3.2
[   229.022] 	Module class: X.Org XInput Driver
[   229.022] 	ABI class: X.Org XInput driver, version 11.0
[   229.022] (**) Power Button: always reports core events
[   229.022] (**) Power Button: Device: "/dev/input/event1"
[   229.056] (II) Power Button: Found keys
[   229.056] (II) Power Button: Configuring as keyboard
[   229.056] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   229.056] (**) Option "xkb_rules" "evdev"
[   229.056] (**) Option "xkb_model" "pc105"
[   229.056] (**) Option "xkb_layout" "us"
[   229.060] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   229.060] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   229.060] (**) Power Button: always reports core events
[   229.060] (**) Power Button: Device: "/dev/input/event0"
[   229.088] (II) Power Button: Found keys
[   229.088] (II) Power Button: Configuring as keyboard
[   229.088] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   229.088] (**) Option "xkb_rules" "evdev"
[   229.088] (**) Option "xkb_model" "pc105"
[   229.088] (**) Option "xkb_layout" "us"
[   229.095] (II) config/udev: Adding input device Logitech G500 (/dev/input/event2)
[   229.095] (**) Logitech G500: Applying InputClass "evdev pointer catchall"
[   229.095] (**) Logitech G500: always reports core events
[   229.095] (**) Logitech G500: Device: "/dev/input/event2"
[   229.132] (II) Logitech G500: Found 20 mouse buttons
[   229.132] (II) Logitech G500: Found scroll wheel(s)
[   229.132] (II) Logitech G500: Found relative axes
[   229.132] (II) Logitech G500: Found x and y relative axes
[   229.132] (II) Logitech G500: Configuring as mouse
[   229.132] (**) Logitech G500: YAxisMapping: buttons 4 and 5
[   229.132] (**) Logitech G500: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   229.132] (II) XINPUT: Adding extended input device "Logitech G500" (type: MOUSE)
[   229.132] (II) Logitech G500: initialized for relative axes.
[   229.133] (II) config/udev: Adding input device Logitech G500 (/dev/input/mouse0)
[   229.133] (II) No input driver/identifier specified (ignoring)
[   229.134] (II) config/udev: Adding input device Logitech G500 (/dev/input/event3)
[   229.134] (**) Logitech G500: Applying InputClass "evdev keyboard catchall"
[   229.134] (**) Logitech G500: always reports core events
[   229.134] (**) Logitech G500: Device: "/dev/input/event3"
[   229.164] (II) Logitech G500: Found 1 mouse buttons
[   229.164] (II) Logitech G500: Found scroll wheel(s)
[   229.164] (II) Logitech G500: Found relative axes
[   229.164] (II) Logitech G500: Found absolute axes
[   229.164] (II) evdev-grail: failed to open grail, no gesture support
[   229.164] (II) Logitech G500: Found keys
[   229.164] (II) Logitech G500: Configuring as mouse
[   229.164] (II) Logitech G500: Configuring as keyboard
[   229.164] (**) Logitech G500: YAxisMapping: buttons 4 and 5
[   229.164] (**) Logitech G500: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   229.164] (II) XINPUT: Adding extended input device "Logitech G500" (type: KEYBOARD)
[   229.164] (**) Option "xkb_rules" "evdev"
[   229.165] (**) Option "xkb_model" "pc105"
[   229.165] (**) Option "xkb_layout" "us"
[   229.165] (EE) Logitech G500: failed to initialize for relative axes.
[   229.165] (II) Logitech G500: initialized for absolute axes.
[   229.167] (II) config/udev: Adding input device Apple, Inc Apple Keyboard (/dev/input/event4)
[   229.167] (**) Apple, Inc Apple Keyboard: Applying InputClass "evdev keyboard catchall"
[   229.167] (**) Apple, Inc Apple Keyboard: always reports core events
[   229.167] (**) Apple, Inc Apple Keyboard: Device: "/dev/input/event4"
[   229.196] (II) Apple, Inc Apple Keyboard: Found keys
[   229.196] (II) Apple, Inc Apple Keyboard: Configuring as keyboard
[   229.196] (II) XINPUT: Adding extended input device "Apple, Inc Apple Keyboard" (type: KEYBOARD)
[   229.196] (**) Option "xkb_rules" "evdev"
[   229.196] (**) Option "xkb_model" "pc105"
[   229.196] (**) Option "xkb_layout" "us"
[   229.198] (II) config/udev: Adding input device Apple, Inc Apple Keyboard (/dev/input/event5)
[   229.198] (**) Apple, Inc Apple Keyboard: Applying InputClass "evdev keyboard catchall"
[   229.198] (**) Apple, Inc Apple Keyboard: always reports core events
[   229.198] (**) Apple, Inc Apple Keyboard: Device: "/dev/input/event5"
[   229.228] (II) Apple, Inc Apple Keyboard: Found keys
[   229.228] (II) Apple, Inc Apple Keyboard: Configuring as keyboard
[   229.228] (II) XINPUT: Adding extended input device "Apple, Inc Apple Keyboard" (type: KEYBOARD)
[   229.228] (**) Option "xkb_rules" "evdev"
[   229.228] (**) Option "xkb_model" "pc105"
[   229.228] (**) Option "xkb_layout" "us"
__________________________________________________________________________
Module                  Size  Used by
nvidia               9330125  48 
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_via      51755  1 
snd_hda_intel          22107  3 
snd_hda_codec          87552  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  3 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                  8767  0 
asus_atk0110           11423  0 
psmouse                59033  0 
k10temp                 2607  0 
snd                    49038  14 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               4022  0 
soundcore                880  1 snd
agpgart                32011  1 nvidia
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
i2c_piix4               8635  0 
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
hid_apple               4523  0 
usbhid                 36882  0 
hid                    67742  2 hid_apple,usbhid
floppy                 54311  0 
firewire_ohci          21042  0 
pata_atiixp             3288  1 
ahci                   19198  2 
firewire_core          46643  1 firewire_ohci
libahci                21664  1 ahci
crc_itu_t               1383  1 firewire_core
atl1e                  29332  0
```

---

### Post by tjones00 on 2010-12-13
In xorg.conf the ServerLayout section is missing

Option   "Xinerama" "1"

If that doesn't work first I would try using a generic xorg.conf generated using the nvidia tools.

I run 4 monitors from 2 nvidia cards and my xorg.conf is as follows. I simply use the nvidia-settings to help setup multiples since it's such a headache.

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@yellow)  Fri Apr  9 11:51:21 UTC 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 1920 1024
    Screen      1  "Screen1" LeftOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen0"
    Screen      3  "Screen3" Above "Screen1"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "1"
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
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     50.0 - 63.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor3"
    VendorName     "Unknown"
    ModelName      "Mitsubishi RDT178S"
    HorizSync       31.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     50.0 - 63.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     50.0 - 63.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GT"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device3"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GT"
    BusID          "PCI:2:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GT"
    BusID          "PCI:2:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen3"
    Device         "Device3"
    Monitor        "Monitor3"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
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
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
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
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```To generate and try one like mine is pretty simple.

Backup your current xorg.conf

Shutdown X

Ctrl+Alt+f2 to switch to a terminal

```

sudo service gdm stop
```remove the xorg.conf  

```
sudo rm /etc/X11/xorg.conf 
```or back it up at this point by moving it.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.original
```use the nvidia-xconfig to generate a new clean xorg.conf.

```
sudo nvidia-xconfig -a

```Restart X (sudo service gdm start) or reboot with the new xorg.conf

Setup your monitors.

```
sudo nvidia-settings
```Position your monitors using the gui and make sure Xinerama and separate X screens are enabled. Save and restart X or reboot.

Then you can continue modifying if there are some other settings you wish to enable/disable.

If that doesn't work the only other thing I see is in your Xorg.0.log

> [   228.717] (EE) NVIDIA(1): Failed to initialize the NVIDIA GPU at PCI:2:0:0.  Please
 [   228.717] (EE) NVIDIA(1):     check your system's kernel log for additional error
 [   228.717] (EE) NVIDIA(1):     messages and refer to Chapter 8: Common Problems in the
 [   228.717] (EE) NVIDIA(1):     README for additional information.
 [   228.717] (EE) NVIDIA(1): Failed to initialize the NVIDIA graphics device!Look at dmesg and try to find the errors there. this can  be found in /var/log/ or you can just use System > Adminstration  > Log File Viewer. 

You can also post your dmesg here and I'll take a look at it.

---

### Post by robbie d on 2010-12-13
thanks for your help, still no joy on this one, here is the file:
```

  0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-24-generic (buildd@vernadsky) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 (Ubuntu 2.6.35-24.42-generic 2.6.35.8)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfe90000 (usable)
[    0.000000]  BIOS-e820: 00000000bfe90000 - 00000000bfea8000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfea8000 - 00000000bfed0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfed0000 - 00000000bff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0xbfe90 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000140000000 aka 5120M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000c0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bfe90000 (usable)
[    0.000000]  modified: 00000000bfe90000 - 00000000bfea8000 (ACPI data)
[    0.000000]  modified: 00000000bfea8000 - 00000000bfed0000 (ACPI NVS)
[    0.000000]  modified: 00000000bfed0000 - 00000000bff00000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
[    0.000000] RAMDISK: 375ae000 - 37ff0000
[    0.000000] Allocated new RAMDISK: 009a7000 - 013e840a
[    0.000000] Move RAMDISK from 00000000375ae000 - 0000000037fef409 to 009a7000 - 013e8409
[    0.000000] ACPI: RSDP 000fb8b0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT bfe90000 0003C (v01 042409 RSDT1024 20090424 MSFT 00000097)
[    0.000000] ACPI: FACP bfe90200 00084 (v01 042409 FACP1024 20090424 MSFT 00000097)
[    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20100428/tbfadt-557)
[    0.000000] ACPI: DSDT bfe90440 0E2BF (v01  A1152 A1152000 00000000 INTL 20060113)
[    0.000000] ACPI: FACS bfea8000 00040
[    0.000000] ACPI: APIC bfe90390 0006C (v01 042409 APIC1024 20090424 MSFT 00000097)
[    0.000000] ACPI: MCFG bfe90400 0003C (v01 042409 OEMMCFG  20090424 MSFT 00000097)
[    0.000000] ACPI: OEMB bfea8040 00072 (v01 042409 OEMB1024 20090424 MSFT 00000097)
[    0.000000] ACPI: HPET bfe9f440 00038 (v01 042409 OEMHPET  20090424 MSFT 00000097)
[    0.000000] ACPI: SSDT bfe9f480 0088C (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2182MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000bfe90
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bfe90
[    0.000000] On node 0 totalpages: 785951
[    0.000000] free_area_init_node: node 0, pgdat c07ffd00, node_mem_map c13ea200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4366 pages used for memmap
[    0.000000]   HighMem zone: 554372 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e6000
[    0.000000] PM: Registered nosave memory: 00000000000e6000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at bff00000 (gap: bff00000:40000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2c00000 s36416 r0 d20928 u1048576
[    0.000000] pcpu-alloc: s36416 r0 d20928 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 779809
[    0.000000] Kernel command line: root=UUID=17cd22de-d4d4-40ad-8e1b-81b0460d6081 ro quiet splash 
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 15720960 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (50 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a2adc]   TEXT DATA BSS
[    0.000000]   #3 [00009a3000 - 00009a622c]             BRK
[    0.000000]   #4 [00000ff790 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000ff780 - 00000ff790]    MP-table mpf
[    0.000000]   #6 [000009fc00 - 00000f1160]   BIOS reserved
[    0.000000]   #7 [00000f130c - 00000ff780]   BIOS reserved
[    0.000000]   #8 [00000f1160 - 00000f130c]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #10 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #11 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #12 [00009a7000 - 00013e9000]     NEW RAMDISK
[    0.000000]   #13 [00013e9000 - 00013ea000]         BOOTMEM
[    0.000000]   #14 [00013ea000 - 0002bea000]         BOOTMEM
[    0.000000]   #15 [0002bea000 - 0002bea004]         BOOTMEM
[    0.000000]   #16 [0002bea040 - 0002bea100]         BOOTMEM
[    0.000000]   #17 [0002bea100 - 0002bea154]         BOOTMEM
[    0.000000]   #18 [0002bea180 - 0002bed180]         BOOTMEM
[    0.000000]   #19 [0002bed180 - 0002bed250]         BOOTMEM
[    0.000000]   #20 [0002bed280 - 0002bf9280]         BOOTMEM
[    0.000000]   #21 [0002bf9280 - 0002bf92a5]         BOOTMEM
[    0.000000]   #22 [0002bf92c0 - 0002bf92e7]         BOOTMEM
[    0.000000]   #23 [0002bf9300 - 0002bf9418]         BOOTMEM
[    0.000000]   #24 [0002bf9440 - 0002bf9480]         BOOTMEM
[    0.000000]   #25 [0002bf9480 - 0002bf94c0]         BOOTMEM
[    0.000000]   #26 [0002bf94c0 - 0002bf9500]         BOOTMEM
[    0.000000]   #27 [0002bf9500 - 0002bf9540]         BOOTMEM
[    0.000000]   #28 [0002bf9540 - 0002bf9580]         BOOTMEM
[    0.000000]   #29 [0002bf9580 - 0002bf95c0]         BOOTMEM
[    0.000000]   #30 [0002bf95c0 - 0002bf9600]         BOOTMEM
[    0.000000]   #31 [0002bf9600 - 0002bf9640]         BOOTMEM
[    0.000000]   #32 [0002bf9640 - 0002bf9680]         BOOTMEM
[    0.000000]   #33 [0002bf9680 - 0002bf9690]         BOOTMEM
[    0.000000]   #34 [0002bf96c0 - 0002bf9700]         BOOTMEM
[    0.000000]   #35 [0002bf9700 - 0002bf9740]         BOOTMEM
[    0.000000]   #36 [0002c00000 - 0002c0e000]         BOOTMEM
[    0.000000]   #37 [0002d00000 - 0002d0e000]         BOOTMEM
[    0.000000]   #38 [0002e00000 - 0002e0e000]         BOOTMEM
[    0.000000]   #39 [0002f00000 - 0002f0e000]         BOOTMEM
[    0.000000]   #40 [0002bfb740 - 0002bfb744]         BOOTMEM
[    0.000000]   #41 [0002bfb780 - 0002bfb784]         BOOTMEM
[    0.000000]   #42 [0002bfb7c0 - 0002bfb7d0]         BOOTMEM
[    0.000000]   #43 [0002bfb800 - 0002bfb810]         BOOTMEM
[    0.000000]   #44 [0002bfb840 - 0002bfb8e0]         BOOTMEM
[    0.000000]   #45 [0002bfb900 - 0002bfb948]         BOOTMEM
[    0.000000]   #46 [0002bfb980 - 0002bff980]         BOOTMEM
[    0.000000]   #47 [0002c0e000 - 0002c8e000]         BOOTMEM
[    0.000000]   #48 [0002c8e000 - 0002cce000]         BOOTMEM
[    0.000000]   #49 [0002f0e000 - 0003e0c200]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (000377fe:000bfe90)
[    0.000000] Memory: 3083404k/3144256k available (4931k kernel code, 60400k reserved, 2333k data, 688k init, 2234952k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0819000 - 0xc08c5000   ( 688 kB)
[    0.000000]       .data : 0xc05d0ebe - 0xc08184e8   (2333 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05d0ebe   (4931 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] 	Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3210.222 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 6420.44 BogoMIPS (lpj=12840888)
[    0.004008] pid_max: default: 32768 minimum: 301
[    0.004023] Security Framework initialized
[    0.004035] AppArmor: AppArmor initialized
[    0.004037] Yama: becoming mindful.
[    0.004079] Mount-cache hash table entries: 512
[    0.004162] Initializing cgroup subsys ns
[    0.004165] Initializing cgroup subsys cpuacct
[    0.004168] Initializing cgroup subsys memory
[    0.004175] Initializing cgroup subsys devices
[    0.004177] Initializing cgroup subsys freezer
[    0.004179] Initializing cgroup subsys net_cls
[    0.004196] CPU: Physical Processor ID: 0
[    0.004197] CPU: Processor Core ID: 0
[    0.004199] mce: CPU supports 6 MCE banks
[    0.004207] using C1E aware idle routine
[    0.004211] Performance Events: AMD PMU driver.
[    0.004216] ... version:                0
[    0.004217] ... bit width:              48
[    0.004219] ... generic registers:      4
[    0.004220] ... value mask:             0000ffffffffffff
[    0.004222] ... max period:             00007fffffffffff
[    0.004224] ... fixed-purpose events:   0
[    0.004225] ... event mask:             000000000000000f
[    0.008680] ACPI: Core revision 20100428
[    0.020006] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.020010] ftrace: allocating 21756 entries in 43 pages
[    0.024044] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024340] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.066730] CPU0: AMD Phenom(tm) II X4 955 Processor stepping 02
[    0.068000] Booting Node   0, Processors  #1
[    0.008000] Initializing CPU#1
[    0.156038]  #2
[    0.008000] Initializing CPU#2
[    0.248034]  #3 Ok.
[    0.008000] Initializing CPU#3
[    0.340004] Brought up 4 CPUs
[    0.340006] Total of 4 processors activated (25685.44 BogoMIPS).
[    0.341752] devtmpfs: initialized
[    0.341752] regulator: core version 0.5
[    0.341752] Time:  9:48:59  Date: 12/13/10
[    0.341752] NET: Registered protocol family 16
[    0.341752] EISA bus registered
[    0.341752] node 0 link 0: io port [1000, ffffff]
[    0.341752] TOM: 00000000c0000000 aka 3072M
[    0.341752] Fam 10h mmconf [e0000000, efffffff]
[    0.341752] node 0 link 0: mmio [a0000, bffff]
[    0.341752] node 0 link 0: mmio [c0000000, dfffffff]
[    0.341752] node 0 link 0: mmio [e0000000, efffffff] ==> none
[    0.341752] node 0 link 0: mmio [f0000000, ffefffff]
[    0.341752] TOM2: 0000000140000000 aka 5120M
[    0.341752] bus: [00, 07] on node 0 link 0
[    0.341752] bus: 00 index 0 [io  0x0000-0xffff]
[    0.341752] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.341752] bus: 00 index 2 [mem 0xc0000000-0xdfffffff]
[    0.341752] bus: 00 index 3 [mem 0xf0000000-0xffffffff]
[    0.341752] ACPI: bus type pci registered
[    0.341752] Trying to unpack rootfs image as initramfs...
[    0.341752] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.341752] PCI: not using MMCONFIG
[    0.341752] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[    0.341752] PCI: Using configuration type 1 for base access
[    0.341752] PCI: Using configuration type 1 for extended access
[    0.341752] mtrr: your CPUs had inconsistent fixed MTRR settings
[    0.341752] mtrr: probably your BIOS does not setup all CPUs.
[    0.341752] mtrr: corrected configuration.
[    0.344027] bio: create slab <bio-0> at 0
[    0.344965] ACPI: EC: Look up EC in DSDT
[    0.346732] ACPI: Executed 3 blocks of module-level executable AML code
[    0.430675] ACPI: Interpreter enabled
[    0.430679] ACPI: (supports S0 S1 S3 S4 S5)
[    0.430698] ACPI: Using IOAPIC for interrupt routing
[    0.430742] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.432599] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.432601] PCI: Using MMCONFIG for extended config space
[    0.438788] ACPI Warning: Incorrect checksum in table [OEMB] - 0xED, should be 0xE4 (20100428/tbutils-314)
[    0.438888] ACPI: No dock devices found.
[    0.438890] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.439019] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.439262] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.439264] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.439265] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.439267] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.439269] pci_root PNP0A03:00: host bridge window [mem 0xbff00000-0xdfffffff]
[    0.439271] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfebfffff]
[    0.439333] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.439335] pci 0000:00:02.0: PME# disabled
[    0.439363] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.439365] pci 0000:00:03.0: PME# disabled
[    0.439396] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.439398] pci 0000:00:06.0: PME# disabled
[    0.439425] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.439427] pci 0000:00:07.0: PME# disabled
[    0.439467] pci 0000:00:11.0: reg 10: [io  0xa000-0xa007]
[    0.439473] pci 0000:00:11.0: reg 14: [io  0x9000-0x9003]
[    0.439479] pci 0000:00:11.0: reg 18: [io  0x8000-0x8007]
[    0.439484] pci 0000:00:11.0: reg 1c: [io  0x7000-0x7003]
[    0.439490] pci 0000:00:11.0: reg 20: [io  0x6000-0x600f]
[    0.439496] pci 0000:00:11.0: reg 24: [mem 0xf3fffc00-0xf3ffffff]
[    0.439512] pci 0000:00:11.0: set SATA to AHCI mode
[    0.439551] pci 0000:00:12.0: reg 10: [mem 0xf3ffd000-0xf3ffdfff]
[    0.439598] pci 0000:00:12.1: reg 10: [mem 0xf3ffe000-0xf3ffefff]
[    0.439657] pci 0000:00:12.2: reg 10: [mem 0xf3fff800-0xf3fff8ff]
[    0.439704] pci 0000:00:12.2: supports D1 D2
[    0.439705] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.439709] pci 0000:00:12.2: PME# disabled
[    0.439735] pci 0000:00:13.0: reg 10: [mem 0xf3ffb000-0xf3ffbfff]
[    0.439782] pci 0000:00:13.1: reg 10: [mem 0xf3ffc000-0xf3ffcfff]
[    0.439841] pci 0000:00:13.2: reg 10: [mem 0xf3fff400-0xf3fff4ff]
[    0.439888] pci 0000:00:13.2: supports D1 D2
[    0.439889] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.439892] pci 0000:00:13.2: PME# disabled
[    0.440001] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    0.440007] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    0.440013] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.440018] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.440024] pci 0000:00:14.1: reg 20: [io  0xff00-0xff0f]
[    0.440079] pci 0000:00:14.2: reg 10: [mem 0xf3ff4000-0xf3ff7fff 64bit]
[    0.440117] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.440121] pci 0000:00:14.2: PME# disabled
[    0.440213] pci 0000:00:14.5: reg 10: [mem 0xf3ffa000-0xf3ffafff]
[    0.440343] pci 0000:01:00.0: reg 10: [mem 0xf7000000-0xf7ffffff]
[    0.440351] pci 0000:01:00.0: reg 14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.440359] pci 0000:01:00.0: reg 1c: [mem 0xf4000000-0xf5ffffff 64bit]
[    0.440364] pci 0000:01:00.0: reg 24: [io  0xbc00-0xbc7f]
[    0.440369] pci 0000:01:00.0: reg 30: [mem 0xf6f80000-0xf6ffffff pref]
[    0.448015] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.448019] pci 0000:00:02.0:   bridge window [io  0xb000-0xbfff]
[    0.448022] pci 0000:00:02.0:   bridge window [mem 0xf4000000-0xf7ffffff]
[    0.448025] pci 0000:00:02.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.448064] pci 0000:02:00.0: reg 10: [mem 0xfa000000-0xfaffffff]
[    0.448073] pci 0000:02:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.448081] pci 0000:02:00.0: reg 1c: [mem 0xf8000000-0xf9ffffff 64bit]
[    0.448085] pci 0000:02:00.0: reg 24: [io  0xcc00-0xcc7f]
[    0.448090] pci 0000:02:00.0: reg 30: [mem 0xfbd80000-0xfbdfffff pref]
[    0.456014] pci 0000:00:03.0: PCI bridge to [bus 02-02]
[    0.456019] pci 0000:00:03.0:   bridge window [io  0xc000-0xcfff]
[    0.456021] pci 0000:00:03.0:   bridge window [mem 0xf8000000-0xfbdfffff]
[    0.456024] pci 0000:00:03.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.456075] pci 0000:03:00.0: reg 10: [mem 0xfbec0000-0xfbefffff 64bit]
[    0.456081] pci 0000:03:00.0: reg 18: [io  0xdc00-0xdc7f]
[    0.456131] pci 0000:03:00.0: PME# supported from D3hot D3cold
[    0.456134] pci 0000:03:00.0: PME# disabled
[    0.456153] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.456159] pci 0000:00:06.0: PCI bridge to [bus 03-03]
[    0.456162] pci 0000:00:06.0:   bridge window [io  0xd000-0xdfff]
[    0.456164] pci 0000:00:06.0:   bridge window [mem 0xfbe00000-0xfbefffff]
[    0.456167] pci 0000:00:06.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.456229] pci 0000:04:00.0: reg 10: [mem 0xfbfff800-0xfbffffff 64bit]
[    0.456238] pci 0000:04:00.0: reg 18: [io  0xe800-0xe8ff]
[    0.456311] pci 0000:04:00.0: supports D2
[    0.456312] pci 0000:04:00.0: PME# supported from D2 D3hot D3cold
[    0.456317] pci 0000:04:00.0: PME# disabled
[    0.464021] pci 0000:00:07.0: PCI bridge to [bus 04-04]
[    0.464025] pci 0000:00:07.0:   bridge window [io  0xe000-0xefff]
[    0.464027] pci 0000:00:07.0:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.464030] pci 0000:00:07.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.464090] pci 0000:00:14.4: PCI bridge to [bus 05-05] (subtractive decode)
[    0.464094] pci 0000:00:14.4:   bridge window [io  0xf000-0x0000] (disabled)
[    0.464097] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.464101] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.464103] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.464104] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.464106] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.464108] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.464110] pci 0000:00:14.4:   bridge window [mem 0xbff00000-0xdfffffff] (subtractive decode)
[    0.464114] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.464127] pci_bus 0000:00: on NUMA node 0
[    0.464134] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.464315] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.464358] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE3._PRT]
[    0.464405] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE6._PRT]
[    0.464445] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
[    0.464509] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.468254] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 *7 10 11 12 14 15)
[    0.468340] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 *10 11 12 14 15)
[    0.468423] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 12 14 15)
[    0.468505] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 10 *11 12 14 15)
[    0.468587] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.468669] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.468751] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 10 *11 12 14 15)
[    0.468832] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.468863] HEST: Table is not found!
[    0.468916] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.468920] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=none,locks=none
[    0.468922] vgaarb: loaded
[    0.469017] SCSI subsystem initialized
[    0.469029] libata version 3.00 loaded.
[    0.469029] usbcore: registered new interface driver usbfs
[    0.469029] usbcore: registered new interface driver hub
[    0.469029] usbcore: registered new device driver usb
[    0.469029] ACPI: WMI: Mapper loaded
[    0.469029] PCI: Using ACPI for IRQ routing
[    0.469029] PCI: pci_cache_line_size set to 64 bytes
[    0.469029] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.469029] reserve RAM buffer: 00000000bfe90000 - 00000000bfffffff 
[    0.469029] NetLabel: Initializing
[    0.469029] NetLabel:  domain hash size = 128
[    0.469029] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.469029] NetLabel:  unlabeled traffic allowed by default
[    0.469029] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.469029] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.470268] Switching to clocksource tsc
[    0.473112] AppArmor: AppArmor Filesystem Enabled
[    0.473119] pnp: PnP ACPI init
[    0.473127] ACPI: bus type pnp registered
[    0.476472] pnp: PnP ACPI: found 14 devices
[    0.476473] ACPI: ACPI bus type pnp unregistered
[    0.476475] PnPBIOS: Disabled by ACPI PNP
[    0.476484] system 00:07: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.476486] system 00:07: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.476489] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.476491] system 00:08: [io  0x040b] has been reserved
[    0.476493] system 00:08: [io  0x04d6] has been reserved
[    0.476495] system 00:08: [io  0x0c00-0x0c01] has been reserved
[    0.476496] system 00:08: [io  0x0c14] has been reserved
[    0.476498] system 00:08: [io  0x0c50-0x0c51] has been reserved
[    0.476499] system 00:08: [io  0x0c52] has been reserved
[    0.476501] system 00:08: [io  0x0c6c] has been reserved
[    0.476502] system 00:08: [io  0x0c6f] has been reserved
[    0.476504] system 00:08: [io  0x0cd0-0x0cd1] has been reserved
[    0.476506] system 00:08: [io  0x0cd2-0x0cd3] has been reserved
[    0.476507] system 00:08: [io  0x0cd4-0x0cd5] has been reserved
[    0.476509] system 00:08: [io  0x0cd6-0x0cd7] has been reserved
[    0.476511] system 00:08: [io  0x0cd8-0x0cdf] has been reserved
[    0.476512] system 00:08: [io  0x0b00-0x0b3f] has been reserved
[    0.476514] system 00:08: [io  0x0800-0x089f] has been reserved
[    0.476516] system 00:08: [io  0x0b00-0x0b0f] has been reserved
[    0.476517] system 00:08: [io  0x0b20-0x0b3f] has been reserved
[    0.476519] system 00:08: [io  0x0900-0x090f] has been reserved
[    0.476521] system 00:08: [io  0x0910-0x091f] has been reserved
[    0.476522] system 00:08: [io  0xfe00-0xfefe] has been reserved
[    0.476525] system 00:08: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.476526] system 00:08: [mem 0xfec10000-0xfec1001f] has been reserved
[    0.476530] system 00:0b: [io  0x0230-0x023f] has been reserved
[    0.476533] system 00:0b: [io  0x0290-0x029f] has been reserved
[    0.476534] system 00:0b: [io  0x0f40-0x0f4f] has been reserved
[    0.476536] system 00:0b: [io  0x0a30-0x0a3f] has been reserved
[    0.476539] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
[    0.476543] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.476545] system 00:0d: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.476546] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.476548] system 00:0d: [mem 0x00100000-0xbfefffff] could not be reserved
[    0.476550] system 00:0d: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.511828] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.511830] pci 0000:00:02.0:   bridge window [io  0xb000-0xbfff]
[    0.511833] pci 0000:00:02.0:   bridge window [mem 0xf4000000-0xf7ffffff]
[    0.511836] pci 0000:00:02.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.511838] pci 0000:00:03.0: PCI bridge to [bus 02-02]
[    0.511840] pci 0000:00:03.0:   bridge window [io  0xc000-0xcfff]
[    0.511843] pci 0000:00:03.0:   bridge window [mem 0xf8000000-0xfbdfffff]
[    0.511845] pci 0000:00:03.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.511848] pci 0000:00:06.0: PCI bridge to [bus 03-03]
[    0.511849] pci 0000:00:06.0:   bridge window [io  0xd000-0xdfff]
[    0.511852] pci 0000:00:06.0:   bridge window [mem 0xfbe00000-0xfbefffff]
[    0.511854] pci 0000:00:06.0:   bridge window [mem pref disabled]
[    0.511856] pci 0000:00:07.0: PCI bridge to [bus 04-04]
[    0.511858] pci 0000:00:07.0:   bridge window [io  0xe000-0xefff]
[    0.511860] pci 0000:00:07.0:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.511862] pci 0000:00:07.0:   bridge window [mem pref disabled]
[    0.511865] pci 0000:00:14.4: PCI bridge to [bus 05-05]
[    0.511866] pci 0000:00:14.4:   bridge window [io  disabled]
[    0.511870] pci 0000:00:14.4:   bridge window [mem disabled]
[    0.511873] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    0.511884]   alloc irq_desc for 18 on node -1
[    0.511885]   alloc kstat_irqs on node -1
[    0.511889] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.511892] pci 0000:00:02.0: setting latency timer to 64
[    0.511896]   alloc irq_desc for 19 on node -1
[    0.511897]   alloc kstat_irqs on node -1
[    0.511900] pci 0000:00:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.511902] pci 0000:00:03.0: setting latency timer to 64
[    0.511906] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.511908] pci 0000:00:06.0: setting latency timer to 64
[    0.511912] pci 0000:00:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.511914] pci 0000:00:07.0: setting latency timer to 64
[    0.511920] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.511922] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.511924] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.511925] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.511927] pci_bus 0000:00: resource 8 [mem 0xbff00000-0xdfffffff]
[    0.511928] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.511930] pci_bus 0000:01: resource 0 [io  0xb000-0xbfff]
[    0.511932] pci_bus 0000:01: resource 1 [mem 0xf4000000-0xf7ffffff]
[    0.511933] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.511935] pci_bus 0000:02: resource 0 [io  0xc000-0xcfff]
[    0.511937] pci_bus 0000:02: resource 1 [mem 0xf8000000-0xfbdfffff]
[    0.511938] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.511940] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
[    0.511941] pci_bus 0000:03: resource 1 [mem 0xfbe00000-0xfbefffff]
[    0.511943] pci_bus 0000:04: resource 0 [io  0xe000-0xefff]
[    0.511945] pci_bus 0000:04: resource 1 [mem 0xfbf00000-0xfbffffff]
[    0.511946] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
[    0.511948] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
[    0.511949] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
[    0.511951] pci_bus 0000:05: resource 7 [mem 0x000d0000-0x000dffff]
[    0.511952] pci_bus 0000:05: resource 8 [mem 0xbff00000-0xdfffffff]
[    0.511954] pci_bus 0000:05: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.511978] NET: Registered protocol family 2
[    0.512018] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.512162] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.512526] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.512698] TCP: Hash tables configured (established 131072 bind 65536)
[    0.512699] TCP reno registered
[    0.512701] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.512707] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.512755] NET: Registered protocol family 1
[    0.546101] Freeing initrd memory: 10504k freed
[    0.616376] pci 0000:01:00.0: Boot video device
[    0.616395] PCI: CLS 64 bytes, default 64
[    0.616610] cpufreq-nforce2: No nForce2 chipset.
[    0.616625] Scanning for low memory corruption every 60 seconds
[    0.616690] audit: initializing netlink socket (disabled)
[    0.616698] type=2000 audit(1292233739.616:1): initialized
[    0.623032] highmem bounce pool size: 64 pages
[    0.623035] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.623900] VFS: Disk quotas dquot_6.5.2
[    0.623934] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.624272] fuse init (API version 7.14)
[    0.624321] msgmni has been set to 1677
[    0.626031] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.626034] io scheduler noop registered
[    0.626035] io scheduler deadline registered
[    0.626044] io scheduler cfq registered (default)
[    0.626113] pcieport 0000:00:02.0: setting latency timer to 64
[    0.626130]   alloc irq_desc for 40 on node -1
[    0.626131]   alloc kstat_irqs on node -1
[    0.626137] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    0.626173] pcieport 0000:00:03.0: setting latency timer to 64
[    0.626188]   alloc irq_desc for 41 on node -1
[    0.626189]   alloc kstat_irqs on node -1
[    0.626192] pcieport 0000:00:03.0: irq 41 for MSI/MSI-X
[    0.626224] pcieport 0000:00:06.0: setting latency timer to 64
[    0.626239]   alloc irq_desc for 42 on node -1
[    0.626240]   alloc kstat_irqs on node -1
[    0.626243] pcieport 0000:00:06.0: irq 42 for MSI/MSI-X
[    0.626276] pcieport 0000:00:07.0: setting latency timer to 64
[    0.626291]   alloc irq_desc for 43 on node -1
[    0.626292]   alloc kstat_irqs on node -1
[    0.626295] pcieport 0000:00:07.0: irq 43 for MSI/MSI-X
[    0.626338] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.626351] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.626464] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.626473] ACPI: Power Button [PWRB]
[    0.626499] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.626501] ACPI: Power Button [PWRF]
[    0.626721] ACPI: acpi_idle registered with cpuidle
[    0.628818] ERST: Table is not found!
[    0.628849] isapnp: Scanning for PnP cards...
[    0.628945] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.629044] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.629286] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.629914] brd: module loaded
[    0.630191] loop: module loaded
[    0.630306]   alloc irq_desc for 16 on node -1
[    0.630307]   alloc kstat_irqs on node -1
[    0.630312] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.630332] pata_acpi 0000:00:14.1: setting latency timer to 64
[    0.630503] Fixed MDIO Bus: probed
[    0.630522] PPP generic driver version 2.4.2
[    0.630541] tun: Universal TUN/TAP device driver, 1.6
[    0.630542] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.630580] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.630592]   alloc irq_desc for 17 on node -1
[    0.630593]   alloc kstat_irqs on node -1
[    0.630596] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.630606] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    0.630624] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    0.630640] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    0.630651] ehci_hcd 0000:00:12.2: debug port 1
[    0.630669] ehci_hcd 0000:00:12.2: irq 17, io mem 0xf3fff800
[    0.640242] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    0.640321] hub 1-0:1.0: USB hub found
[    0.640324] hub 1-0:1.0: 6 ports detected
[    0.640380] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.640390] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.640409] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    0.640422] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    0.640433] ehci_hcd 0000:00:13.2: debug port 1
[    0.640452] ehci_hcd 0000:00:13.2: irq 19, io mem 0xf3fff400
[    0.652244] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.652313] hub 2-0:1.0: USB hub found
[    0.652316] hub 2-0:1.0: 6 ports detected
[    0.652369] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.652380] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.652390] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    0.652410] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    0.652430] ohci_hcd 0000:00:12.0: irq 16, io mem 0xf3ffd000
[    0.712310] hub 3-0:1.0: USB hub found
[    0.712315] hub 3-0:1.0: 3 ports detected
[    0.712363] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.712372] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    0.712390] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    0.712402] ohci_hcd 0000:00:12.1: irq 16, io mem 0xf3ffe000
[    0.772322] hub 4-0:1.0: USB hub found
[    0.772327] hub 4-0:1.0: 3 ports detected
[    0.772375] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.772385] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.772402] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    0.772421] ohci_hcd 0000:00:13.0: irq 18, io mem 0xf3ffb000
[    0.832324] hub 5-0:1.0: USB hub found
[    0.832329] hub 5-0:1.0: 3 ports detected
[    0.832378] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.832387] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.832408] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    0.832420] ohci_hcd 0000:00:13.1: irq 18, io mem 0xf3ffc000
[    0.892338] hub 6-0:1.0: USB hub found
[    0.892343] hub 6-0:1.0: 3 ports detected
[    0.892395] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.892405] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    0.892423] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    0.892435] ohci_hcd 0000:00:14.5: irq 18, io mem 0xf3ffa000
[    0.952346] hub 7-0:1.0: USB hub found
[    0.952351] hub 7-0:1.0: 2 ports detected
[    0.952393] uhci_hcd: USB Universal Host Controller Interface driver
[    0.952444] PNP: No PS/2 controller found. Probing ports directly.
[    0.952802] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.952811] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.952870] mice: PS/2 mouse device common for all mice
[    0.952933] rtc_cmos 00:03: RTC can wake from S4
[    0.952954] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.952976] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.953037] device-mapper: uevent: version 1.0.3
[    0.953110] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    0.953195] device-mapper: multipath: version 1.1.1 loaded
[    0.953197] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.953269] EISA: Probing bus 0 at eisa.0
[    0.953271] EISA: Cannot allocate resource for mainboard
[    0.953272] Cannot allocate resource for EISA slot 1
[    0.953273] Cannot allocate resource for EISA slot 2
[    0.953274] Cannot allocate resource for EISA slot 3
[    0.953276] Cannot allocate resource for EISA slot 4
[    0.953277] Cannot allocate resource for EISA slot 5
[    0.953278] Cannot allocate resource for EISA slot 6
[    0.953279] Cannot allocate resource for EISA slot 7
[    0.953280] Cannot allocate resource for EISA slot 8
[    0.953281] EISA: Detected 0 cards.
[    0.953398] cpuidle: using governor ladder
[    0.953399] cpuidle: using governor menu
[    0.953571] TCP cubic registered
[    0.953644] NET: Registered protocol family 10
[    0.953860] lo: Disabled Privacy Extensions
[    0.953993] NET: Registered protocol family 17
[    0.954025] powernow-k8: Found 1 AMD Phenom(tm) II X4 955 Processor (4 cpu cores) (version 2.20.00)
[    0.954053] powernow-k8:    0 : pstate 0 (3200 MHz)
[    0.954054] powernow-k8:    1 : pstate 1 (2500 MHz)
[    0.954055] powernow-k8:    2 : pstate 2 (2100 MHz)
[    0.954056] powernow-k8:    3 : pstate 3 (800 MHz)
[    0.982857] isapnp: No Plug & Play device found
[    0.982947] Using IPI No-Shortcut mode
[    0.982999] PM: Resume from disk failed.
[    0.983005] registered taskstats version 1
[    0.983210]   Magic number: 6:753:828
[    0.983273] rtc_cmos 00:03: setting system clock to 2010-12-13 09:49:00 UTC (1292233740)
[    0.983275] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.983276] EDD information not available.
[    0.983319] Freeing unused kernel memory: 688k freed
[    0.983524] Write protecting the kernel text: 4932k
[    0.983548] Write protecting the kernel read-only data: 1980k
[    0.993279] udev[98]: starting version 163
[    1.005835] ATL1E 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.005845] ATL1E 0000:03:00.0: setting latency timer to 64
[    1.011060] scsi0 : pata_atiixp
[    1.016393] scsi1 : pata_atiixp
[    1.017356] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.017358] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.017931] ahci 0000:00:11.0: version 3.0
[    1.017947]   alloc irq_desc for 22 on node -1
[    1.017948]   alloc kstat_irqs on node -1
[    1.017953] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.018047] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.018050] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.018411] scsi2 : ahci
[    1.019636] scsi3 : ahci
[    1.019685] scsi4 : ahci
[    1.020173] scsi5 : ahci
[    1.020266] ata3: SATA max UDMA/133 irq_stat 0x00400000, PHY RDY changed irq 22
[    1.020270] ata4: SATA max UDMA/133 abar m1024@0xf3fffc00 port 0xf3fffd80 irq 22
[    1.020272] ata5: SATA max UDMA/133 abar m1024@0xf3fffc00 port 0xf3fffe00 irq 22
[    1.020275] ata6: SATA max UDMA/133 abar m1024@0xf3fffc00 port 0xf3fffe80 irq 22
[    1.033086] Floppy drive(s): fd0 is 1.44M
[    1.048523] usb 1-5: new high speed USB device using ehci_hcd and address 3
[    1.052274] FDC 0 is a post-1991 82077
[    1.172455] ata1.00: ATAPI: ASUS    DRW-22B2S, 1.01, max UDMA/66
[    1.188409] ata1.00: configured for UDMA/66
[    1.190107] scsi 0:0:0:0: CD-ROM            ASUS     DRW-22B2S        1.01 PQ: 0 ANSI: 5
[    1.192399] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.192401] Uniform CD-ROM driver Revision: 3.20
[    1.192458] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.192505] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.192885] hub 1-5:1.0: USB hub found
[    1.192995] hub 1-5:1.0: 3 ports detected
[    1.341529] ata5: SATA link down (SStatus 0 SControl 300)
[    1.341556] ata6: SATA link down (SStatus 0 SControl 300)
[    1.341581] ata4: SATA link down (SStatus 0 SControl 300)
[    1.456029] usb 4-1: new full speed USB device using ohci_hcd and address 2
[    1.655270] usbcore: registered new interface driver hiddev
[    1.660614] input: Logitech G500 as /devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1:1.0/input/input2
[    1.660664] generic-usb 0003:046D:C068.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech G500] on usb-0000:00:12.1-1/input0
[    1.672574] input: Logitech G500 as /devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1:1.1/input/input3
[    1.672640] generic-usb 0003:046D:C068.0002: input,hiddev96,hidraw1: USB HID v1.11 Keyboard [Logitech G500] on usb-0000:00:12.1-1/input1
[    1.672654] usbcore: registered new interface driver usbhid
[    1.672655] usbhid: USB HID core driver
[    1.706053] usb 1-5.2: new low speed USB device using ehci_hcd and address 4
[    1.809327] input: Apple, Inc Apple Keyboard as /devices/pci0000:00/0000:00:12.2/usb1/1-5/1-5.2/1-5.2:1.0/input/input4
[    1.809374] apple 0003:05AC:0220.0003: input,hidraw2: USB HID v1.11 Keyboard [Apple, Inc Apple Keyboard] on usb-0000:00:12.2-5.2/input0
[    1.812335] input: Apple, Inc Apple Keyboard as /devices/pci0000:00/0000:00:12.2/usb1/1-5/1-5.2/1-5.2:1.1/input/input5
[    1.812378] apple 0003:05AC:0220.0004: input,hidraw3: USB HID v1.11 Device [Apple, Inc Apple Keyboard] on usb-0000:00:12.2-5.2/input1
[    1.916023] ata3: softreset failed (device not ready)
[    1.916027] ata3: applying SB600 PMP SRST workaround and retrying
[    2.088039] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.089118] ata3.00: ATA-8: ST31000528AS, CC37, max UDMA/133
[    2.089120] ata3.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.090381] ata3.00: configured for UDMA/133
[    2.104110] scsi 2:0:0:0: Direct-Access     ATA      ST31000528AS     CC37 PQ: 0 ANSI: 5
[    2.104209] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.104225] sd 2:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.104322] sd 2:0:0:0: [sda] Write Protect is off
[    2.104325] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.104348] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.104474]  sda: sda1 sda2 sda3 < sda5 >
[    2.141800] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.145838] firewire_ohci 0000:04:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.145845] firewire_ohci 0000:04:00.0: setting latency timer to 64
[    2.241520] firewire_ohci: Added fw-ohci device 0000:04:00.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x1
[    2.452841] EXT3-fs: barriers not enabled
[    2.459991] kjournald starting.  Commit interval 5 seconds
[    2.460092] EXT3-fs (sda1): mounted filesystem with ordered data mode
[    2.732086] firewire_core: created device fw0: GUID 001e8c0001e667a2, S400
[   18.644565] udev[386]: starting version 163
[   18.667874] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SOR1 [??? 0x00000b00-0x00000b0f flags 0x31]
[   18.667877] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   18.688731] Linux agpgart interface v0.103
[   18.704819] lp: driver loaded but no devices found
[   18.715326] nvidia: module license 'NVIDIA' taints kernel.
[   18.715330] Disabling lock debugging due to kernel taint
[   18.743479] Adding 9068656k swap on /dev/sda5.  Priority:-1 extents:1 across:9068656k 
[   18.781213] type=1400 audit(1292233758.293:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=742 comm="apparmor_parser"
[   18.781398] type=1400 audit(1292233758.293:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=742 comm="apparmor_parser"
[   18.781512] type=1400 audit(1292233758.297:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=742 comm="apparmor_parser"
[   18.799650] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.142246] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   19.142253] nvidia 0000:01:00.0: setting latency timer to 64
[   19.142257] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   19.142259] vgaarb: transferring owner from PCI:0000:01:00.0 to PCI:0000:02:00.0
[   19.142346] nvidia 0000:02:00.0: enabling device (0000 -> 0003)
[   19.142351] nvidia 0000:02:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   19.142355] nvidia 0000:02:00.0: setting latency timer to 64
[   19.142360] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=none
[   19.142455] NVRM: loading NVIDIA UNIX x86 Kernel Module  260.19.21  Thu Nov  4 20:24:24 PDT 2010
[   20.915308] EXT3-fs (sda1): warning: maximal mount count reached, running e2fsck is recommended
[   20.915591] EXT3-fs (sda1): using internal journal
[   21.056615]   alloc irq_desc for 44 on node -1
[   21.056617]   alloc kstat_irqs on node -1
[   21.056629] ATL1E 0000:03:00.0: irq 44 for MSI/MSI-X
[   21.056739] ATL1E 0000:03:00.0: eth0: NIC Link is Up <1000 Mbps Full Duplex>
[   21.056810] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.056936] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   21.059030] type=1400 audit(1292233760.573:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1041 comm="apparmor_parser"
[   21.059218] type=1400 audit(1292233760.573:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1041 comm="apparmor_parser"
[   21.059322] type=1400 audit(1292233760.573:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1041 comm="apparmor_parser"
[   21.060717] type=1400 audit(1292233760.573:8): apparmor="STATUS" operation="profile_load" name="/usr/bin/freshclam" pid=1085 comm="apparmor_parser"
[   21.061699] type=1400 audit(1292233760.577:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1087 comm="apparmor_parser"
[   21.061935] type=1400 audit(1292233760.577:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1087 comm="apparmor_parser"
[   21.062077] type=1400 audit(1292233760.577:11): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1030 comm="apparmor_parser"
[   21.100205] ppdev: user-space parallel port driver
[   21.239116] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   21.239119] apm: disabled - APM is not SMP safe.
```

---

### Post by tjones00 on 2010-12-13
Ok I don't see anything unusual in dmesg the kernel appears to see the second card and set it up properly. I've left mine below so you can compare for yourself. The vbox stuff at the end is just because I have virtualbox installed in linux.

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-26-generic (buildd@allspice) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #48-Ubuntu SMP Wed Nov 24 10:14:11 UTC 2010 (Ubuntu 2.6.32-26.48-generic 2.6.32.24+drm33.11)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-2.6.32-26-generic root=UUID=8ed7cf0e-16e9-4eb7-bc47-73ac92952b93 ro quiet splash nomodeset video=uvesafb:mode_option=1920x1200-24,mtrr=3,scroll=ywrap
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bff90000 (usable)
[    0.000000]  BIOS-e820: 00000000bff90000 - 00000000bff9e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bff9e000 - 00000000bffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bffe0000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffc00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000240000000 (usable)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x240000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask E00000000 write-back
[    0.000000]   1 base 200000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000c0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbff90 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bff90000 (usable)
[    0.000000]  modified: 00000000bff90000 - 00000000bff9e000 (ACPI data)
[    0.000000]  modified: 00000000bff9e000 - 00000000bffe0000 (ACPI NVS)
[    0.000000]  modified: 00000000bffe0000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffc00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000240000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000bff90000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 00bfe00000 page 2M
[    0.000000]  00bfe00000 - 00bff90000 page 4k
[    0.000000] kernel direct mapping tables up to bff90000 @ 10000-15000
[    0.000000] init_memory_mapping: 0000000100000000-0000000240000000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0100000000 - 0240000000 page 2M
[    0.000000] kernel direct mapping tables up to 240000000 @ 13000-1d000
[    0.000000] RAMDISK: 377ec000 - 37fef44f
[    0.000000] ACPI: RSDP 00000000000f9970 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 00000000bff90000 0003C (v01 7512MS A7512300 20090309 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000bff90200 00084 (v01 7512MS A7512300 20090309 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000bff90440 05B6D (v01  A7512 A7512300 00000300 INTL 20051117)
[    0.000000] ACPI: FACS 00000000bff9e000 00040
[    0.000000] ACPI: APIC 00000000bff90390 0006C (v01 7512MS A7512300 20090309 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000bff90400 0003C (v01 7512MS OEMMCFG  20090309 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000bff9e040 00072 (v01 7512MS A7512300 20090309 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000bff98440 00038 (v01 7512MS OEMHPET  20090309 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000bff9e9c0 00A7C (v01 DpgPmm    CpuPm 00000012 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000240000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000240000000
[    0.000000]   NODE_DATA [0000000000018000 - 000000000001cfff]
[    0.000000]   bootmap [000000000001d000 -  0000000000064fff] pages 48
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0240000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 0001a2fa64]    TEXT DATA BSS ==> [0001000000 - 0001a2fa64]
[    0.000000]   #3 [00377ec000 - 0037fef44f]          RAMDISK ==> [00377ec000 - 0037fef44f]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [0001a30000 - 0001a301ad]              BRK ==> [0001a30000 - 0001a301ad]
[    0.000000]   #6 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]
[    0.000000]   #7 [0000013000 - 0000018000]          PGTABLE ==> [0000013000 - 0000018000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000]  [ffffea0000000000-ffffea0007dfffff] PMD -> [ffff880028600000-ffff88002f5fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00240000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bff90
[    0.000000]     0: 0x00100000 -> 0x00240000
[    0.000000] On node 0 totalpages: 2096927
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 107 pages reserved
[    0.000000]   DMA zone: 3820 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 767944 pages, LIFO batch:31
[    0.000000]   Normal zone: 17920 pages used for memmap
[    0.000000]   Normal zone: 1292800 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bff90000 - 00000000bff9e000
[    0.000000] PM: Registered nosave memory: 00000000bff9e000 - 00000000bffe0000
[    0.000000] PM: Registered nosave memory: 00000000bffe0000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffc00000
[    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u524288
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2064564
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.32-26-generic root=UUID=8ed7cf0e-16e9-4eb7-bc47-73ac92952b93 ro quiet splash nomodeset video=uvesafb:mode_option=1920x1200-24,mtrr=3,scroll=ywrap
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
[    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
[    0.000000] Memory: 8187608k/9437184k available (5421k kernel code, 1049476k absent, 200100k reserved, 2980k data, 876k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:4352 nr_irqs:440
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 83886080 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2673.830 MHz processor.
[    0.000006] Calibrating delay loop (skipped), value calculated using timer frequency.. 5347.66 BogoMIPS (lpj=26738300)
[    0.000026] Security Framework initialized
[    0.000042] AppArmor: AppArmor initialized
[    0.000620] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.012246] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.013617] Mount-cache hash table entries: 256
[    0.013739] Initializing cgroup subsys ns
[    0.013743] Initializing cgroup subsys cpuacct
[    0.013746] Initializing cgroup subsys memory
[    0.013752] Initializing cgroup subsys devices
[    0.013754] Initializing cgroup subsys freezer
[    0.013755] Initializing cgroup subsys net_cls
[    0.013772] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.013774] CPU: L2 cache: 3072K
[    0.013777] CPU 0/0x0 -> Node 0
[    0.013779] CPU: Physical Processor ID: 0
[    0.013780] CPU: Processor Core ID: 0
[    0.013783] mce: CPU supports 6 MCE banks
[    0.013789] CPU0: Thermal monitoring enabled (TM2)
[    0.013793] using mwait in idle threads.
[    0.013794] Performance Events: Core2 events, Intel PMU driver.
[    0.013799] ... version:                2
[    0.013800] ... bit width:              40
[    0.013802] ... generic registers:      2
[    0.013803] ... value mask:             000000ffffffffff
[    0.013804] ... max period:             000000007fffffff
[    0.013806] ... fixed-purpose events:   3
[    0.013807] ... event mask:             0000000700000003
[    0.015955] ACPI: Core revision 20090903
[    0.023384] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.023388] ftrace: allocating 22543 entries in 89 pages
[    0.030045] Setting APIC routing to flat
[    0.030320] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.131498] CPU0: Intel(R) Core(TM)2 Quad CPU    Q9400  @ 2.66GHz stepping 0a
[    0.140000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 3072K
[    0.010000] CPU 1/0x1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.010000] CPU1: Thermal monitoring enabled (TM2)
[    0.290052] CPU1: Intel(R) Core(TM)2 Quad CPU    Q9400  @ 2.66GHz stepping 0a
[    0.290057] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.300095] Booting processor 2 APIC 0x2 ip 0x6000
[    0.010000] Initializing CPU#2
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 3072K
[    0.010000] CPU 2/0x2 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 2
[    0.010000] CPU2: Thermal monitoring enabled (TM2)
[    0.460055] CPU2: Intel(R) Core(TM)2 Quad CPU    Q9400  @ 2.66GHz stepping 0a
[    0.460060] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.470059] Booting processor 3 APIC 0x3 ip 0x6000
[    0.010000] Initializing CPU#3
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 3072K
[    0.010000] CPU 3/0x3 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 3
[    0.010000] CPU3: Thermal monitoring enabled (TM2)
[    0.630087] CPU3: Intel(R) Core(TM)2 Quad CPU    Q9400  @ 2.66GHz stepping 0a
[    0.630093] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.640010] Brought up 4 CPUs
[    0.640012] Total of 4 processors activated (21387.48 BogoMIPS).
[    0.641433] CPU0 attaching sched-domain:
[    0.641435]  domain 0: span 0-1 level MC
[    0.641437]   groups: 0 1
[    0.641441]   domain 1: span 0-3 level CPU
[    0.641442]    groups: 0-1 (cpu_power = 2048) 2-3 (cpu_power = 2048)
[    0.641448] CPU1 attaching sched-domain:
[    0.641450]  domain 0: span 0-1 level MC
[    0.641451]   groups: 1 0
[    0.641454]   domain 1: span 0-3 level CPU
[    0.641456]    groups: 0-1 (cpu_power = 2048) 2-3 (cpu_power = 2048)
[    0.641460] CPU2 attaching sched-domain:
[    0.641462]  domain 0: span 2-3 level MC
[    0.641463]   groups: 2 3
[    0.641466]   domain 1: span 0-3 level CPU
[    0.641468]    groups: 2-3 (cpu_power = 2048) 0-1 (cpu_power = 2048)
[    0.641472] CPU3 attaching sched-domain:
[    0.641474]  domain 0: span 2-3 level MC
[    0.641475]   groups: 3 2
[    0.641478]   domain 1: span 0-3 level CPU
[    0.641480]    groups: 2-3 (cpu_power = 2048) 0-1 (cpu_power = 2048)
[    0.641583] devtmpfs: initialized
[    0.641583] regulator: core version 0.5
[    0.641583] Time: 16:09:49  Date: 12/13/10
[    0.641583] NET: Registered protocol family 16
[    0.641583] Trying to unpack rootfs image as initramfs...
[    0.641583] ACPI: bus type pci registered
[    0.641583] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.641583] PCI: Not using MMCONFIG.
[    0.641583] PCI: Using configuration type 1 for base access
[    0.641583] bio: create slab <bio-0> at 0
[    0.641583] ACPI: EC: Look up EC in DSDT
[    0.642343] ACPI: Executed 1 blocks of module-level executable AML code
[    0.646339] ACPI: Interpreter enabled
[    0.646341] ACPI: (supports S0 S1 S4 S5)
[    0.646356] ACPI: Using IOAPIC for interrupt routing
[    0.646397] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.651158] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.657437] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.662666] ACPI: No dock devices found.
[    0.662785] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.662864] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.662866] pci 0000:00:01.0: PME# disabled
[    0.662904] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.662906] pci 0000:00:06.0: PME# disabled
[    0.662960] pci 0000:00:1a.0: reg 20 io port: [0xbc00-0xbc1f]
[    0.663017] pci 0000:00:1a.1: reg 20 io port: [0xb880-0xb89f]
[    0.663074] pci 0000:00:1a.2: reg 20 io port: [0xb800-0xb81f]
[    0.663132] pci 0000:00:1a.7: reg 10 32bit mmio: [0xf5fffc00-0xf5ffffff]
[    0.663178] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.663182] pci 0000:00:1a.7: PME# disabled
[    0.663214] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf5ff8000-0xf5ffbfff]
[    0.663248] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.663251] pci 0000:00:1b.0: PME# disabled
[    0.663300] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.663303] pci 0000:00:1c.0: PME# disabled
[    0.663360] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.663364] pci 0000:00:1c.5: PME# disabled
[    0.663408] pci 0000:00:1d.0: reg 20 io port: [0xb480-0xb49f]
[    0.663464] pci 0000:00:1d.1: reg 20 io port: [0xb400-0xb41f]
[    0.663521] pci 0000:00:1d.2: reg 20 io port: [0xb080-0xb09f]
[    0.663584] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf5fff800-0xf5fffbff]
[    0.663628] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.663631] pci 0000:00:1d.7: PME# disabled
[    0.663730] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.663733] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.663736] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0a00 (mask 00ff)
[    0.663739] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0a00 (mask 0017)
[    0.663742] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 4700 (mask 00ff)
[    0.663784] pci 0000:00:1f.2: reg 10 io port: [0xb000-0xb007]
[    0.663789] pci 0000:00:1f.2: reg 14 io port: [0xac00-0xac03]
[    0.663793] pci 0000:00:1f.2: reg 18 io port: [0xa880-0xa887]
[    0.663798] pci 0000:00:1f.2: reg 1c io port: [0xa800-0xa803]
[    0.663802] pci 0000:00:1f.2: reg 20 io port: [0xa480-0xa48f]
[    0.663807] pci 0000:00:1f.2: reg 24 io port: [0xa400-0xa40f]
[    0.663845] pci 0000:00:1f.3: reg 10 64bit mmio: [0xf5fff400-0xf5fff4ff]
[    0.663856] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.663891] pci 0000:00:1f.5: reg 10 io port: [0xa000-0xa007]
[    0.663896] pci 0000:00:1f.5: reg 14 io port: [0x9c00-0x9c03]
[    0.663901] pci 0000:00:1f.5: reg 18 io port: [0x9880-0x9887]
[    0.663905] pci 0000:00:1f.5: reg 1c io port: [0x9800-0x9803]
[    0.663909] pci 0000:00:1f.5: reg 20 io port: [0x9480-0x948f]
[    0.663914] pci 0000:00:1f.5: reg 24 io port: [0x9400-0x940f]
[    0.663961] pci 0000:01:00.0: reg 10 32bit mmio: [0xf9000000-0xf9ffffff]
[    0.663968] pci 0000:01:00.0: reg 14 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.663975] pci 0000:01:00.0: reg 1c 64bit mmio: [0xf6000000-0xf7ffffff]
[    0.663980] pci 0000:01:00.0: reg 24 io port: [0xcc00-0xcc7f]
[    0.663984] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.664036] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
[    0.664038] pci 0000:00:01.0: bridge 32bit mmio: [0xf6000000-0xf9ffffff]
[    0.664041] pci 0000:00:01.0: bridge 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.664063] pci 0000:02:00.0: reg 10 32bit mmio: [0xfd000000-0xfdffffff]
[    0.664070] pci 0000:02:00.0: reg 14 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.664077] pci 0000:02:00.0: reg 1c 64bit mmio: [0xfa000000-0xfbffffff]
[    0.664082] pci 0000:02:00.0: reg 24 io port: [0xdc00-0xdc7f]
[    0.664086] pci 0000:02:00.0: reg 30 32bit mmio pref: [0xfeae0000-0xfeafffff]
[    0.664134] pci 0000:00:06.0: bridge io port: [0xd000-0xdfff]
[    0.664136] pci 0000:00:06.0: bridge 32bit mmio: [0xfa000000-0xfeafffff]
[    0.664139] pci 0000:00:06.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.664215] pci 0000:04:00.0: reg 10 io port: [0xe800-0xe8ff]
[    0.664233] pci 0000:04:00.0: reg 18 64bit mmio: [0xfebff000-0xfebfffff]
[    0.664246] pci 0000:04:00.0: reg 20 64bit mmio pref: [0xf4ff0000-0xf4ffffff]
[    0.664253] pci 0000:04:00.0: reg 30 32bit mmio pref: [0xfebc0000-0xfebdffff]
[    0.664288] pci 0000:04:00.0: supports D1 D2
[    0.664289] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.664293] pci 0000:04:00.0: PME# disabled
[    0.664340] pci 0000:00:1c.5: bridge io port: [0xe000-0xefff]
[    0.664343] pci 0000:00:1c.5: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.664348] pci 0000:00:1c.5: bridge 64bit mmio pref: [0xf4f00000-0xf4ffffff]
[    0.664387] pci 0000:00:1e.0: transparent bridge
[    0.664409] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.664521] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.664606] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.664666] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.668222] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
[    0.668309] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[    0.668391] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12 *14 15)
[    0.668476] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 *11 12 14 15)
[    0.668561] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
[    0.668646] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12 14 *15)
[    0.668730] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 6 7 10 11 12 14 15)
[    0.668815] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 6 *7 10 11 12 14 15)
[    0.668903] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.668907] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=none,locks=none
[    0.668909] vgaarb: loaded
[    0.668985] SCSI subsystem initialized
[    0.668993] libata version 3.00 loaded.
[    0.668993] usbcore: registered new interface driver usbfs
[    0.668993] usbcore: registered new interface driver hub
[    0.668993] usbcore: registered new device driver usb
[    0.668993] ACPI: WMI: Mapper loaded
[    0.668993] PCI: Using ACPI for IRQ routing
[    0.668993] NetLabel: Initializing
[    0.668993] NetLabel:  domain hash size = 128
[    0.668993] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.668993] NetLabel:  unlabeled traffic allowed by default
[    0.668993] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.668993] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.690176] Switching to clocksource tsc
[    0.691576] AppArmor: AppArmor Filesystem Enabled
[    0.691594] pnp: PnP ACPI init
[    0.691610] ACPI: bus type pnp registered
[    0.693481] pnp: PnP ACPI: found 12 devices
[    0.693483] ACPI: ACPI bus type pnp unregistered
[    0.693493] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.693495] system 00:01: iomem range 0xfed90000-0xfed93fff has been reserved
[    0.693501] system 00:06: ioport range 0xa00-0xadf has been reserved
[    0.693503] system 00:06: ioport range 0xae0-0xaef has been reserved
[    0.693507] system 00:07: ioport range 0x4c0-0x4ff has been reserved
[    0.693509] system 00:07: ioport range 0x800-0x87f has been reserved
[    0.693511] system 00:07: ioport range 0x480-0x4bf has been reserved
[    0.693514] system 00:07: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.693516] system 00:07: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.693518] system 00:07: iomem range 0xfed45000-0xfed89fff has been reserved
[    0.693520] system 00:07: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.693522] system 00:07: iomem range 0xfed40000-0xfed8ffff could not be reserved
[    0.693526] system 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.693529] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.693533] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
[    0.693537] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.693539] system 00:0b: iomem range 0xc0000-0xcffff has been reserved
[    0.693541] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[    0.693543] system 00:0b: iomem range 0x100000-0xbfffffff could not be reserved
[    0.693545] system 00:0b: iomem range 0xfed90000-0xffffffff could not be reserved
[    0.698230] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.698233] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.698236] pci 0000:00:01.0:   MEM window: 0xf6000000-0xf9ffffff
[    0.698238] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    0.698242] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02
[    0.698244] pci 0000:00:06.0:   IO window: 0xd000-0xdfff
[    0.698247] pci 0000:00:06.0:   MEM window: 0xfa000000-0xfeafffff
[    0.698249] pci 0000:00:06.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.698253] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:03
[    0.698255] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
[    0.698259] pci 0000:00:1c.0:   MEM window: 0xf0000000-0xf01fffff
[    0.698263] pci 0000:00:1c.0:   PREFETCH window: 0x000000f0200000-0x000000f03fffff
[    0.698268] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:04
[    0.698270] pci 0000:00:1c.5:   IO window: 0xe000-0xefff
[    0.698274] pci 0000:00:1c.5:   MEM window: 0xfeb00000-0xfebfffff
[    0.698277] pci 0000:00:1c.5:   PREFETCH window: 0x000000f4f00000-0x000000f4ffffff
[    0.698282] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.698283] pci 0000:00:1e.0:   IO window: disabled
[    0.698287] pci 0000:00:1e.0:   MEM window: disabled
[    0.698289] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.698301]   alloc irq_desc for 16 on node -1
[    0.698302]   alloc kstat_irqs on node -1
[    0.698307] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.698311] pci 0000:00:01.0: setting latency timer to 64
[    0.698315] pci 0000:00:06.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.698318] pci 0000:00:06.0: setting latency timer to 64
[    0.698324] pci 0000:00:1c.0: enabling device (0104 -> 0107)
[    0.698326]   alloc irq_desc for 17 on node -1
[    0.698327]   alloc kstat_irqs on node -1
[    0.698330] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.698333] pci 0000:00:1c.0: setting latency timer to 64
[    0.698340] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.698343] pci 0000:00:1c.5: setting latency timer to 64
[    0.698349] pci 0000:00:1e.0: setting latency timer to 64
[    0.698352] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.698354] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.698356] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    0.698358] pci_bus 0000:01: resource 1 mem: [0xf6000000-0xf9ffffff]
[    0.698360] pci_bus 0000:01: resource 2 pref mem [0xc0000000-0xcfffffff]
[    0.698361] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.698363] pci_bus 0000:02: resource 1 mem: [0xfa000000-0xfeafffff]
[    0.698365] pci_bus 0000:02: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.698367] pci_bus 0000:03: resource 0 io:  [0x1000-0x1fff]
[    0.698368] pci_bus 0000:03: resource 1 mem: [0xf0000000-0xf01fffff]
[    0.698370] pci_bus 0000:03: resource 2 pref mem [0xf0200000-0xf03fffff]
[    0.698372] pci_bus 0000:04: resource 0 io:  [0xe000-0xefff]
[    0.698374] pci_bus 0000:04: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.698376] pci_bus 0000:04: resource 2 pref mem [0xf4f00000-0xf4ffffff]
[    0.698377] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
[    0.698379] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.698410] NET: Registered protocol family 2
[    0.698616] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.699853] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.702839] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.703201] TCP: Hash tables configured (established 524288 bind 65536)
[    0.703203] TCP reno registered
[    0.703312] NET: Registered protocol family 1
[    0.703457] pci 0000:01:00.0: Boot video device
[    0.703709] Scanning for low memory corruption every 60 seconds
[    0.703815] audit: initializing netlink socket (disabled)
[    0.703824] type=2000 audit(1292256589.699:1): initialized
[    0.711406] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.712508] VFS: Disk quotas dquot_6.5.2
[    0.712547] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.712989] fuse init (API version 7.13)
[    0.713048] msgmni has been set to 15991
[    0.713255] alg: No test for stdrng (krng)
[    0.713297] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.713299] io scheduler noop registered
[    0.713301] io scheduler anticipatory registered
[    0.713302] io scheduler deadline registered
[    0.713328] io scheduler cfq registered (default)
[    0.713431]   alloc irq_desc for 24 on node -1
[    0.713433]   alloc kstat_irqs on node -1
[    0.713440] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.713444] pcieport 0000:00:01.0: setting latency timer to 64
[    0.713507]   alloc irq_desc for 25 on node -1
[    0.713508]   alloc kstat_irqs on node -1
[    0.713512] pcieport 0000:00:06.0: irq 25 for MSI/MSI-X
[    0.713516] pcieport 0000:00:06.0: setting latency timer to 64
[    0.713587]   alloc irq_desc for 26 on node -1
[    0.713588]   alloc kstat_irqs on node -1
[    0.713594] pcieport 0000:00:1c.0: irq 26 for MSI/MSI-X
[    0.713599] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.713687]   alloc irq_desc for 27 on node -1
[    0.713689]   alloc kstat_irqs on node -1
[    0.713694] pcieport 0000:00:1c.5: irq 27 for MSI/MSI-X
[    0.713700] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.713764] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.713826] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.713912] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.713915] ACPI: Power Button [PWRB]
[    0.713950] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.713951] ACPI: Power Button [PWRF]
[    0.714502] ACPI: SSDT 00000000bff9e0c0 00235 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    0.714713] processor LNXCPU:00: registered as cooling_device0
[    0.715025] ACPI: SSDT 00000000bff9e300 00235 (v01 DpgPmm  P002Ist 00000012 INTL 20051117)
[    0.715227] processor LNXCPU:01: registered as cooling_device1
[    0.715546] ACPI: SSDT 00000000bff9e540 00235 (v01 DpgPmm  P003Ist 00000012 INTL 20051117)
[    0.715744] processor LNXCPU:02: registered as cooling_device2
[    0.716059] ACPI: SSDT 00000000bff9e780 00235 (v01 DpgPmm  P004Ist 00000012 INTL 20051117)
[    0.716259] processor LNXCPU:03: registered as cooling_device3
[    0.718503] Linux agpgart interface v0.103
[    0.718527] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.719471] brd: module loaded
[    0.719850] loop: module loaded
[    0.719910] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.719979] ata_piix 0000:00:1f.2: version 2.13
[    0.719992]   alloc irq_desc for 19 on node -1
[    0.719993]   alloc kstat_irqs on node -1
[    0.719999] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.720002] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.720036] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.720089] scsi0 : ata_piix
[    0.720144] scsi1 : ata_piix
[    0.721259] ata1: SATA max UDMA/133 cmd 0xb000 ctl 0xac00 bmdma 0xa480 irq 19
[    0.721264] ata2: SATA max UDMA/133 cmd 0xa880 ctl 0xa800 bmdma 0xa488 irq 19
[    0.721286] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.721299] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    0.721347] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.721380] scsi2 : ata_piix
[    0.721421] scsi3 : ata_piix
[    0.722323] ata3: SATA max UDMA/133 cmd 0xa000 ctl 0x9c00 bmdma 0x9480 irq 19
[    0.722326] ata4: SATA max UDMA/133 cmd 0x9880 ctl 0x9800 bmdma 0x9488 irq 19
[    0.722592] Fixed MDIO Bus: probed
[    0.722616] PPP generic driver version 2.4.2
[    0.722644] tun: Universal TUN/TAP device driver, 1.6
[    0.722646] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.722706] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.722719]   alloc irq_desc for 18 on node -1
[    0.722721]   alloc kstat_irqs on node -1
[    0.722724] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.722743] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.722746] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.722769] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.722790] ehci_hcd 0000:00:1a.7: debug port 1
[    0.726673] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.726685] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf5fffc00
[    0.749566] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.749664] usb usb1: configuration #1 chosen from 1 choice
[    0.749688] hub 1-0:1.0: USB hub found
[    0.749697] hub 1-0:1.0: 6 ports detected
[    0.749753]   alloc irq_desc for 23 on node -1
[    0.749754]   alloc kstat_irqs on node -1
[    0.749760] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.749779] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.749781] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.749810] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.749830] ehci_hcd 0000:00:1d.7: debug port 1
[    0.753710] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.753726] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf5fff800
[    0.769562] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.769663] usb usb2: configuration #1 chosen from 1 choice
[    0.769685] hub 2-0:1.0: USB hub found
[    0.769692] hub 2-0:1.0: 6 ports detected
[    0.769745] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.769759] uhci_hcd: USB Universal Host Controller Interface driver
[    0.769793] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.769800] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.769803] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.769830] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.769861] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000bc00
[    0.769924] usb usb3: configuration #1 chosen from 1 choice
[    0.769942] hub 3-0:1.0: USB hub found
[    0.769947] hub 3-0:1.0: 2 ports detected
[    0.769983]   alloc irq_desc for 21 on node -1
[    0.769984]   alloc kstat_irqs on node -1
[    0.769989] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.769993] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.769996] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.770019] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.770044] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000b880
[    0.770107] usb usb4: configuration #1 chosen from 1 choice
[    0.770125] hub 4-0:1.0: USB hub found
[    0.770129] hub 4-0:1.0: 2 ports detected
[    0.770162] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.770167] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.770169] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.770196] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.770219] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000b800
[    0.770278] usb usb5: configuration #1 chosen from 1 choice
[    0.770302] hub 5-0:1.0: USB hub found
[    0.770306] hub 5-0:1.0: 2 ports detected
[    0.770339] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.770343] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.770345] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.770371] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.770391] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000b480
[    0.770449] usb usb6: configuration #1 chosen from 1 choice
[    0.770469] hub 6-0:1.0: USB hub found
[    0.770473] hub 6-0:1.0: 2 ports detected
[    0.770505] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.770510] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.770513] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.770535] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.770554] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b400
[    0.770621] usb usb7: configuration #1 chosen from 1 choice
[    0.770639] hub 7-0:1.0: USB hub found
[    0.770645] hub 7-0:1.0: 2 ports detected
[    0.770678] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.770682] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.770684] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.770712] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.770732] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b080
[    0.770793] usb usb8: configuration #1 chosen from 1 choice
[    0.770811] hub 8-0:1.0: USB hub found
[    0.770815] hub 8-0:1.0: 2 ports detected
[    0.770884] PNP: No PS/2 controller found. Probing ports directly.
[    0.773239] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.773244] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.773321] mice: PS/2 mouse device common for all mice
[    0.773394] rtc_cmos 00:03: RTC can wake from S4
[    0.773423] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.773443] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.773544] device-mapper: uevent: version 1.0.3
[    0.773611] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.773690] device-mapper: multipath: version 1.1.0 loaded
[    0.773692] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.773849] cpuidle: using governor ladder
[    0.773851] cpuidle: using governor menu
[    0.774095] TCP cubic registered
[    0.774200] NET: Registered protocol family 10
[    0.774525] lo: Disabled Privacy Extensions
[    0.774729] NET: Registered protocol family 17
[    0.775618] PM: Resume from disk failed.
[    0.775626] registered taskstats version 1
[    0.775944]   Magic number: 6:327:186
[    0.776012] rtc_cmos 00:03: setting system clock to 2010-12-13 16:09:49 UTC (1292256589)
[    0.776014] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.776016] EDD information not available.
[    0.786547] Freeing initrd memory: 8205k freed
[    1.070640] ata4: SATA link down (SStatus 0 SControl 300)
[    1.081252] ata3: SATA link down (SStatus 0 SControl 300)
[    1.420007] usb 5-2: new low speed USB device using uhci_hcd and address 2
[    1.420649] ata2.00: SATA link down (SStatus 0 SControl 300)
[    1.420660] ata2.01: SATA link down (SStatus 0 SControl 300)
[    1.560051] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.560062] ata1.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.603125] usb 5-2: configuration #1 chosen from 1 choice
[    1.612915] ata1.00: ATA-7: WDC WD5000AAKS-00TMA0, 12.01C01, max UDMA/133
[    1.612918] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.612937] ata1.01: ATA-7: Patriot Warp V2 32GB SSD, 02.10104, max UDMA/133
[    1.612940] ata1.01: 62533296 sectors, multi 1: LBA48 
[    1.654641] ata1.00: configured for UDMA/133
[    1.692679] ata1.01: configured for UDMA/133
[    1.692766] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 12.0 PQ: 0 ANSI: 5
[    1.692855] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.692881] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.692935] scsi 0:0:1:0: Direct-Access     ATA      Patriot Warp V2  02.1 PQ: 0 ANSI: 5
[    1.692942] sd 0:0:0:0: [sda] Write Protect is off
[    1.692950] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.692975] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.693063] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    1.693104] sd 0:0:1:0: [sdb] 62533296 512-byte logical blocks: (32.0 GB/29.8 GiB)
[    1.693140] sd 0:0:1:0: [sdb] Write Protect is off
[    1.693142] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.693158]  sda:
[    1.693165] sd 0:0:1:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    1.699594]  sda1 sda2
[    1.699758] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.699817]  sdb: sdb1 sdb2 sdb3
[    1.762338] sd 0:0:1:0: [sdb] Attached SCSI disk
[    1.762355] Freeing unused kernel memory: 876k freed
[    1.762533] Write protecting the kernel read-only data: 7696k
[    1.775704] udev: starting version 151
[    1.802369] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.802389] r8169 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.802427] r8169 0000:04:00.0: setting latency timer to 64
[    1.802467]   alloc irq_desc for 28 on node -1
[    1.802469]   alloc kstat_irqs on node -1
[    1.802480] r8169 0000:04:00.0: irq 28 for MSI/MSI-X
[    1.802925] eth0: RTL8168c/8111c at 0xffffc90000c64000, 00:21:85:1c:20:de, XID 1c4000c0 IRQ 28
[    1.811223] usbcore: registered new interface driver hiddev
[    1.824280] input: Kensington      Kensington USB/PS2 Orbit as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input3
[    1.824414] generic-usb 0003:047D:1022.0001: input,hidraw0: USB HID v1.10 Mouse [Kensington      Kensington USB/PS2 Orbit] on usb-0000:00:1a.2-2/input0
[    1.824440] usbcore: registered new interface driver usbhid
[    1.824468] usbhid: v2.6:USB HID core driver
[    1.860568] uvesafb: NVIDIA Corporation, G92 Board - 03930024, Chip Rev   , OEM: NVIDIA, VBE v3.0
[    1.883793] usb 6-2: new full speed USB device using uhci_hcd and address 2
[    1.961407] uvesafb: VBIOS/hardware supports DDC2 transfers
[    2.041578] uvesafb: monitor limits: vf = 63 Hz, hf = 81 kHz, clk = 170 MHz
[    2.041688] uvesafb: scrolling: redraw
[    2.042061] mtrr: type mismatch for f7000000,800000 old: write-back new: write-combining
[    2.042064] mtrr: type mismatch for f7000000,400000 old: write-back new: write-combining
[    2.042067] mtrr: type mismatch for f7000000,200000 old: write-back new: write-combining
[    2.042069] mtrr: type mismatch for f7000000,100000 old: write-back new: write-combining
[    2.042072] mtrr: type mismatch for f7000000,80000 old: write-back new: write-combining
[    2.042074] mtrr: type mismatch for f7000000,40000 old: write-back new: write-combining
[    2.042077] mtrr: type mismatch for f7000000,20000 old: write-back new: write-combining
[    2.042079] mtrr: type mismatch for f7000000,10000 old: write-back new: write-combining
[    2.042082] mtrr: type mismatch for f7000000,8000 old: write-back new: write-combining
[    2.042084] mtrr: type mismatch for f7000000,4000 old: write-back new: write-combining
[    2.042087] mtrr: type mismatch for f7000000,2000 old: write-back new: write-combining
[    2.042089] mtrr: type mismatch for f7000000,1000 old: write-back new: write-combining
[    2.042143] uvesafb: framebuffer at 0xf7000000, mapped to 0xffffc90011800000, using 14336k, total 14336k
[    2.042145] fb0: VESA VGA frame buffer device
[    2.051154] EXT4-fs (sdb2): mounted filesystem with ordered data mode
[    2.055240] usb 6-2: configuration #1 chosen from 1 choice
[    2.059016] hub 6-2:1.0: USB hub found
[    2.060177] hub 6-2:1.0: 4 ports detected
[    2.341121] usb 6-2.1: new low speed USB device using uhci_hcd and address 3
[    2.477174] usb 6-2.1: configuration #1 chosen from 1 choice
[    2.494300] input: G15 Gaming Keyboard as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2.1/6-2.1:1.0/input/input4
[    2.494365] generic-usb 0003:046D:C226.0002: input,hidraw1: USB HID v1.10 Keyboard [G15 Gaming Keyboard] on usb-0000:00:1d.0-2.1/input0
[    2.529116] input: G15 Gaming Keyboard as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2.1/6-2.1:1.1/input/input5
[    2.529206] generic-usb 0003:046D:C226.0003: input,hiddev96,hidraw2: USB HID v1.10 Device [G15 Gaming Keyboard] on usb-0000:00:1d.0-2.1/input1
[    2.614067] usb 6-2.4: new full speed USB device using uhci_hcd and address 4
[    2.754124] usb 6-2.4: configuration #1 chosen from 1 choice
[    2.777120] input: G15 GamePanel LCD as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2.4/6-2.4:1.0/input/input6
[    2.777212] generic-usb 0003:046D:C227.0004: input,hiddev97,hidraw3: USB HID v1.11 Keypad [G15 GamePanel LCD] on usb-0000:00:1d.0-2.4/input0
[    4.458172] udev: starting version 151
[    4.466582] lp: driver loaded but no devices found
[    4.481430] vga16fb: initializing
[    4.481434] vga16fb: mapped to 0xffff8800000a0000
[    4.481437] vga16fb: not registering due to another framebuffer present
[    4.575915] nvidia: module license 'NVIDIA' taints kernel.
[    4.575918] Disabling lock debugging due to kernel taint
[    4.576040] type=1505 audit(1292285393.293:2):  operation="profile_load" pid=644 name="/sbin/dhclient3"
[    4.576559] type=1505 audit(1292285393.293:3):  operation="profile_load" pid=644 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    4.576826] type=1505 audit(1292285393.293:4):  operation="profile_load" pid=644 name="/usr/lib/connman/scripts/dhclient-script"
[    4.633359] EXT4-fs (sdb1): mounted filesystem with ordered data mode
[    4.989235]   alloc irq_desc for 22 on node -1
[    4.989237]   alloc kstat_irqs on node -1
[    4.989243] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    4.989569] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    5.108134] hda_codec: ALC888: BIOS auto-probing.
[    5.109466] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input7
[    5.133822] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.133833] nvidia 0000:01:00.0: setting latency timer to 64
[    5.133841] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    5.133843] vgaarb: transferring owner from PCI:0000:01:00.0 to PCI:0000:02:00.0
[    5.133980] nvidia 0000:02:00.0: enabling device (0000 -> 0003)
[    5.133983] nvidia 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.133988] nvidia 0000:02:00.0: setting latency timer to 64
[    5.133997] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=none
[    5.134111] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.24  Thu Apr 22 19:10:14 PDT 2010
[    5.526002] Console: switching to colour frame buffer device 240x75
[    5.608973] r8169: eth0: link up
[    5.608986] r8169: eth0: link up
[    5.666409] type=1505 audit(1292285394.385:5):  operation="profile_load" pid=850 name="/usr/share/gdm/guest-session/Xsession"
[    5.667715] type=1505 audit(1292285394.385:6):  operation="profile_replace" pid=851 name="/sbin/dhclient3"
[    5.668229] type=1505 audit(1292285394.385:7):  operation="profile_replace" pid=851 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    5.668502] type=1505 audit(1292285394.385:8):  operation="profile_replace" pid=851 name="/usr/lib/connman/scripts/dhclient-script"
[    5.671240] type=1505 audit(1292285394.395:9):  operation="profile_load" pid=854 name="/usr/bin/evince"
[    5.677702] type=1505 audit(1292285394.395:10):  operation="profile_load" pid=854 name="/usr/bin/evince-previewer"
[    5.807853] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[    5.807856] vboxdrv: Successfully done.
[    5.807857] vboxdrv: Found 4 processor cores.
[    5.807931] VBoxDrv: dbg - g_abExecMemory=ffffffffa0d62a20
[    5.807971] vboxdrv: fAsync=0 offMin=0x488 offMax=0x17a0
[    5.808260] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[    5.808262] vboxdrv: Successfully loaded version 3.1.6_OSE (interface 0x00100001).
```I assume you haven't done any partial xorg.conf mods in /usr/share/X11/xorg.conf.d/ the system created ones are fine but if you've placed any there yourself remove them.

So this all leads is back to xorg.conf and perhaps the nvidia driver itself. dmesg should contain any driver errors so a clean dmesg is pointing to the xorg.conf more than the driver itself.

I'd try an older/different driver and a new xorg.conf generated via nvidia-xconfig/nvidia-settings (make sure it's new and not merged) with each driver you try. Keep looking at the new Xorg.0.log each time you try out a driver.

[http://linux.die.net/man/1/nvidia-xconfig](http://linux.die.net/man/1/nvidia-xconfig) nvidia-xconfig options for your reference.

I usually just use nvidia-xconfig -a which is the same as --enable-all-gpus.

You could also check /var/log/kern.log for errors.

Here is mine so you have a reverence just look for nvidia or pci entries.

```
Dec 12 18:20:03 brawndo-PC kernel: [ 3062.948009] npviewer.bin[1941]: segfault at 418 ip 00000000f6062c86 sp 00000000ffa48588 error 6 in libflashplayer.so[f5e13000+b2e000]
Dec 12 18:21:33 brawndo-PC kernel: [ 3153.225819] npviewer.bin[2361]: segfault at 0 ip 00000000f61dced1 sp 00000000ffacfdd0 error 4 in libflashplayer.so[f5e3d000+b2e000]
Dec 12 23:25:32 brawndo-PC kernel: [21392.703929] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
Dec 12 23:47:57 brawndo-PC kernel: [22737.033084] npviewer.bin[2433]: segfault at e9367004 ip 00000000f640df7c sp 00000000ffd3a7b0 error 4 in libflashplayer.so[f5dd4000+b2e000]
Dec 12 23:48:11 brawndo-PC kernel: [22751.031442] npviewer.bin[4234]: segfault at f587704c ip 00000000f61f1ee7 sp 00000000ffc1efb0 error 4 in libflashplayer.so[f5e52000+b2e000]
Dec 13 00:04:33 brawndo-PC kernel: [23733.336152] npviewer.bin[4307]: segfault at ee9d99a0 ip 00000000ee9d99a0 sp 00000000ffbce6dc error 15
Dec 13 00:07:52 brawndo-PC kernel: [23932.550949] npviewer.bin[4797]: segfault at 0 ip 00000000f61f7ed1 sp 00000000ffa3e800 error 4 in libflashplayer.so[f5e58000+b2e000]
Dec 13 00:10:03 brawndo-PC kernel: [24062.943236] npviewer.bin[4898]: segfault at 0 ip 00000000f623ded1 sp 00000000ffa819d0 error 4 in libflashplayer.so[f5e9e000+b2e000]
Dec 13 00:16:04 brawndo-PC kernel: [24424.453950] npviewer.bin[5094]: segfault at 418 ip 00000000f6047c86 sp 00000000ffd93218 error 6 in libflashplayer.so[f5df8000+b2e000]
Dec 13 00:21:34 brawndo-PC kernel: [24754.133050] npviewer.bin[5497]: segfault at f592204c ip 00000000f617aee7 sp 00000000ffac24c0 error 4 in libflashplayer.so[f5ddb000+b2e000]
Dec 13 00:22:29 brawndo-PC kernel: [24809.283242] npviewer.bin[5812]: segfault at 418 ip 00000000f60cbc86 sp 00000000ffb46f88 error 6 in libflashplayer.so[f5e7c000+b2e000]
Dec 13 00:24:09 brawndo-PC kernel: [24908.808571] npviewer.bin[5883]: segfault at 0 ip 00000000f61cded1 sp 00000000ffc45bc0 error 4 in libflashplayer.so[f5e2e000+b2e000]
Dec 13 00:25:14 brawndo-PC kernel: [24974.616642] npviewer.bin[6009]: segfault at 418 ip 00000000f6078c86 sp 00000000ffdbc238 error 6 in libflashplayer.so[f5e29000+b2e000]
Dec 13 00:42:48 brawndo-PC kernel: [26028.691858] npviewer.bin[6079]: segfault at 0 ip 00000000f61e9ed1 sp 00000000ffb688f0 error 4 in libflashplayer.so[f5e4a000+b2e000]
Dec 13 16:09:54 brawndo-PC kernel: imklog 4.2.0, log source = /proc/kmsg started.
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] Initializing cgroup subsys cpu
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] Linux version 2.6.32-26-generic (buildd@allspice) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #48-Ubuntu SMP Wed Nov 24 10:14:11 UTC 2010 (Ubuntu 2.6.32-26.48-generic 2.6.32.24+drm33.11)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] Command line: BOOT_IMAGE=/vmlinuz-2.6.32-26-generic root=UUID=8ed7cf0e-16e9-4eb7-bc47-73ac92952b93 ro quiet splash nomodeset video=uvesafb:mode_option=1920x1200-24,mtrr=3,scroll=ywrap
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] KERNEL supported cpus:
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]   Intel GenuineIntel
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]   AMD AuthenticAMD
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]   Centaur CentaurHauls
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] BIOS-provided physical RAM map:
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bff90000 (usable)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]  BIOS-e820: 00000000bff90000 - 00000000bff9e000 (ACPI data)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]  BIOS-e820: 00000000bff9e000 - 00000000bffe0000 (ACPI NVS)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]  BIOS-e820: 00000000bffe0000 - 00000000c0000000 (reserved)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]  BIOS-e820: 00000000ffc00000 - 0000000100000000 (reserved)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000240000000 (usable)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] DMI present.
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] last_pfn = 0x240000 max_arch_pfn = 0x400000000
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] MTRR default type: uncachable
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] MTRR fixed ranges enabled:
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]   00000-9FFFF write-back
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]   A0000-BFFFF uncachable
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]   C0000-CFFFF write-protect
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]   D0000-DFFFF uncachable
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]   E0000-EFFFF write-through
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]   F0000-FFFFF write-protect
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] MTRR variable ranges enabled:
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]   0 base 000000000 mask E00000000 write-back
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]   1 base 200000000 mask FC0000000 write-back
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]   3 disabled
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]   4 disabled
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]   5 disabled
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]   6 disabled
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]   7 disabled
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] e820 update range: 00000000c0000000 - 0000000100000000 (usable) ==> (reserved)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] last_pfn = 0xbff90 max_arch_pfn = 0x400000000
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] Scanning 0 areas for low memory corruption
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] modified physical RAM map:
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]  modified: 0000000000100000 - 00000000bff90000 (usable)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]  modified: 00000000bff90000 - 00000000bff9e000 (ACPI data)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]  modified: 00000000bff9e000 - 00000000bffe0000 (ACPI NVS)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]  modified: 00000000bffe0000 - 00000000c0000000 (reserved)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]  modified: 00000000ffc00000 - 0000000100000000 (reserved)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]  modified: 0000000100000000 - 0000000240000000 (usable)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] initial memory mapped : 0 - 20000000
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000bff90000
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] NX (Execute Disable) protection: active
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]  0000000000 - 00bfe00000 page 2M
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]  00bfe00000 - 00bff90000 page 4k
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] kernel direct mapping tables up to bff90000 @ 10000-15000
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000240000000
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] NX (Execute Disable) protection: active
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]  0100000000 - 0240000000 page 2M
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] kernel direct mapping tables up to 240000000 @ 13000-1d000
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] RAMDISK: 377ec000 - 37fef44f
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] ACPI: RSDP 00000000000f9970 00014 (v00 ACPIAM)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] ACPI: RSDT 00000000bff90000 0003C (v01 7512MS A7512300 20090309 MSFT 00000097)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] ACPI: FACP 00000000bff90200 00084 (v01 7512MS A7512300 20090309 MSFT 00000097)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] ACPI: DSDT 00000000bff90440 05B6D (v01  A7512 A7512300 00000300 INTL 20051117)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] ACPI: FACS 00000000bff9e000 00040
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] ACPI: APIC 00000000bff90390 0006C (v01 7512MS A7512300 20090309 MSFT 00000097)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] ACPI: MCFG 00000000bff90400 0003C (v01 7512MS OEMMCFG  20090309 MSFT 00000097)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] ACPI: OEMB 00000000bff9e040 00072 (v01 7512MS A7512300 20090309 MSFT 00000097)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] ACPI: HPET 00000000bff98440 00038 (v01 7512MS OEMHPET  20090309 MSFT 00000097)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] ACPI: SSDT 00000000bff9e9c0 00A7C (v01 DpgPmm    CpuPm 00000012 INTL 20051117)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] No NUMA configuration found
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] Faking a node at 0000000000000000-0000000240000000
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000240000000
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]   NODE_DATA [0000000000018000 - 000000000001cfff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]   bootmap [000000000001d000 -  0000000000064fff] pages 48
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0240000000]
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]   #2 [0001000000 - 0001a2fa64]    TEXT DATA BSS ==> [0001000000 - 0001a2fa64]
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]   #3 [00377ec000 - 0037fef44f]          RAMDISK ==> [00377ec000 - 0037fef44f]
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]   #5 [0001a30000 - 0001a301ad]              BRK ==> [0001a30000 - 0001a301ad]
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]   #6 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]   #7 [0000013000 - 0000018000]          PGTABLE ==> [0000013000 - 0000018000]
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]  [ffffea0000000000-ffffea0007dfffff] PMD -> [ffff880028600000-ffff88002f5fffff] on node 0
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] Zone PFN ranges:
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]   Normal   0x00100000 -> 0x00240000
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] Movable zone start PFN for each node
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] early_node_map[3] active PFN ranges
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]     0: 0x00000100 -> 0x000bff90
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]     0: 0x00100000 -> 0x00240000
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] On node 0 totalpages: 2096927
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]   DMA zone: 107 pages reserved
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]   DMA zone: 3820 pages, LIFO batch:0
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]   DMA32 zone: 14280 pages used for memmap
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]   DMA32 zone: 767944 pages, LIFO batch:31
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]   Normal zone: 17920 pages used for memmap
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000]   Normal zone: 1292800 pages, LIFO batch:31
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] ACPI: IRQ0 used by override.
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] ACPI: IRQ2 used by override.
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] ACPI: IRQ9 used by override.
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] nr_irqs_gsi: 24
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] PM: Registered nosave memory: 00000000bff90000 - 00000000bff9e000
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] PM: Registered nosave memory: 00000000bff9e000 - 00000000bffe0000
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] PM: Registered nosave memory: 00000000bffe0000 - 00000000c0000000
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000fee00000
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffc00000
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 0000000100000000
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ee00000)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u524288
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] pcpu-alloc: s91544 r8192 d23144 u524288 alloc=1*2097152
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2064564
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] Policy zone: Normal
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.32-26-generic root=UUID=8ed7cf0e-16e9-4eb7-bc47-73ac92952b93 ro quiet splash nomodeset video=uvesafb:mode_option=1920x1200-24,mtrr=3,scroll=ywrap
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] Initializing CPU#0
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] Checking aperture...
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] No AGP bridge found
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] Memory: 8187608k/9437184k available (5421k kernel code, 1049476k absent, 200100k reserved, 2980k data, 876k init)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] Hierarchical RCU implementation.
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] NR_IRQS:4352 nr_irqs:440
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] Console: colour VGA+ 80x25
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] console [tty0] enabled
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] allocated 83886080 bytes of page_cgroup
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] hpet clockevent registered
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] Fast TSC calibration using PIT
Dec 13 16:09:54 brawndo-PC kernel: [    0.000000] Detected 2673.830 MHz processor.
Dec 13 16:09:54 brawndo-PC kernel: [    0.000006] Calibrating delay loop (skipped), value calculated using timer frequency.. 5347.66 BogoMIPS (lpj=26738300)
Dec 13 16:09:54 brawndo-PC kernel: [    0.000026] Security Framework initialized
Dec 13 16:09:54 brawndo-PC kernel: [    0.000042] AppArmor: AppArmor initialized
Dec 13 16:09:54 brawndo-PC kernel: [    0.000620] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Dec 13 16:09:54 brawndo-PC kernel: [    0.012246] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Dec 13 16:09:54 brawndo-PC kernel: [    0.013617] Mount-cache hash table entries: 256
Dec 13 16:09:54 brawndo-PC kernel: [    0.013739] Initializing cgroup subsys ns
Dec 13 16:09:54 brawndo-PC kernel: [    0.013743] Initializing cgroup subsys cpuacct
Dec 13 16:09:54 brawndo-PC kernel: [    0.013746] Initializing cgroup subsys memory
Dec 13 16:09:54 brawndo-PC kernel: [    0.013752] Initializing cgroup subsys devices
Dec 13 16:09:54 brawndo-PC kernel: [    0.013754] Initializing cgroup subsys freezer
Dec 13 16:09:54 brawndo-PC kernel: [    0.013755] Initializing cgroup subsys net_cls
Dec 13 16:09:54 brawndo-PC kernel: [    0.013772] CPU: L1 I cache: 32K, L1 D cache: 32K
Dec 13 16:09:54 brawndo-PC kernel: [    0.013774] CPU: L2 cache: 3072K
Dec 13 16:09:54 brawndo-PC kernel: [    0.013777] CPU 0/0x0 -> Node 0
Dec 13 16:09:54 brawndo-PC kernel: [    0.013779] CPU: Physical Processor ID: 0
Dec 13 16:09:54 brawndo-PC kernel: [    0.013780] CPU: Processor Core ID: 0
Dec 13 16:09:54 brawndo-PC kernel: [    0.013783] mce: CPU supports 6 MCE banks
Dec 13 16:09:54 brawndo-PC kernel: [    0.013789] CPU0: Thermal monitoring enabled (TM2)
Dec 13 16:09:54 brawndo-PC kernel: [    0.013793] using mwait in idle threads.
Dec 13 16:09:54 brawndo-PC kernel: [    0.013794] Performance Events: Core2 events, Intel PMU driver.
Dec 13 16:09:54 brawndo-PC kernel: [    0.013799] ... version:                2
Dec 13 16:09:54 brawndo-PC kernel: [    0.013800] ... bit width:              40
Dec 13 16:09:54 brawndo-PC kernel: [    0.013802] ... generic registers:      2
Dec 13 16:09:54 brawndo-PC kernel: [    0.013803] ... value mask:             000000ffffffffff
Dec 13 16:09:54 brawndo-PC kernel: [    0.013804] ... max period:             000000007fffffff
Dec 13 16:09:54 brawndo-PC kernel: [    0.013806] ... fixed-purpose events:   3
Dec 13 16:09:54 brawndo-PC kernel: [    0.013807] ... event mask:             0000000700000003
Dec 13 16:09:54 brawndo-PC kernel: [    0.015955] ACPI: Core revision 20090903
Dec 13 16:09:54 brawndo-PC kernel: [    0.023384] ftrace: converting mcount calls to 0f 1f 44 00 00
Dec 13 16:09:54 brawndo-PC kernel: [    0.023388] ftrace: allocating 22543 entries in 89 pages
Dec 13 16:09:54 brawndo-PC kernel: [    0.030045] Setting APIC routing to flat
Dec 13 16:09:54 brawndo-PC kernel: [    0.030320] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec 13 16:09:54 brawndo-PC kernel: [    0.131498] CPU0: Intel(R) Core(TM)2 Quad CPU    Q9400  @ 2.66GHz stepping 0a
Dec 13 16:09:54 brawndo-PC kernel: [    0.140000] Booting processor 1 APIC 0x1 ip 0x6000
Dec 13 16:09:54 brawndo-PC kernel: [    0.010000] Initializing CPU#1
Dec 13 16:09:54 brawndo-PC kernel: [    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
Dec 13 16:09:54 brawndo-PC kernel: [    0.010000] CPU: L2 cache: 3072K
Dec 13 16:09:54 brawndo-PC kernel: [    0.010000] CPU 1/0x1 -> Node 0
Dec 13 16:09:54 brawndo-PC kernel: [    0.010000] CPU: Physical Processor ID: 0
Dec 13 16:09:54 brawndo-PC kernel: [    0.010000] CPU: Processor Core ID: 1
Dec 13 16:09:54 brawndo-PC kernel: [    0.010000] CPU1: Thermal monitoring enabled (TM2)
Dec 13 16:09:54 brawndo-PC kernel: [    0.290052] CPU1: Intel(R) Core(TM)2 Quad CPU    Q9400  @ 2.66GHz stepping 0a
Dec 13 16:09:54 brawndo-PC kernel: [    0.290057] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Dec 13 16:09:54 brawndo-PC kernel: [    0.300095] Booting processor 2 APIC 0x2 ip 0x6000
Dec 13 16:09:54 brawndo-PC kernel: [    0.010000] Initializing CPU#2
Dec 13 16:09:54 brawndo-PC kernel: [    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
Dec 13 16:09:54 brawndo-PC kernel: [    0.010000] CPU: L2 cache: 3072K
Dec 13 16:09:54 brawndo-PC kernel: [    0.010000] CPU 2/0x2 -> Node 0
Dec 13 16:09:54 brawndo-PC kernel: [    0.010000] CPU: Physical Processor ID: 0
Dec 13 16:09:54 brawndo-PC kernel: [    0.010000] CPU: Processor Core ID: 2
Dec 13 16:09:54 brawndo-PC kernel: [    0.010000] CPU2: Thermal monitoring enabled (TM2)
Dec 13 16:09:54 brawndo-PC kernel: [    0.460055] CPU2: Intel(R) Core(TM)2 Quad CPU    Q9400  @ 2.66GHz stepping 0a
Dec 13 16:09:54 brawndo-PC kernel: [    0.460060] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
Dec 13 16:09:54 brawndo-PC kernel: [    0.470059] Booting processor 3 APIC 0x3 ip 0x6000
Dec 13 16:09:54 brawndo-PC kernel: [    0.010000] Initializing CPU#3
Dec 13 16:09:54 brawndo-PC kernel: [    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
Dec 13 16:09:54 brawndo-PC kernel: [    0.010000] CPU: L2 cache: 3072K
Dec 13 16:09:54 brawndo-PC kernel: [    0.010000] CPU 3/0x3 -> Node 0
Dec 13 16:09:54 brawndo-PC kernel: [    0.010000] CPU: Physical Processor ID: 0
Dec 13 16:09:54 brawndo-PC kernel: [    0.010000] CPU: Processor Core ID: 3
Dec 13 16:09:54 brawndo-PC kernel: [    0.010000] CPU3: Thermal monitoring enabled (TM2)
Dec 13 16:09:54 brawndo-PC kernel: [    0.630087] CPU3: Intel(R) Core(TM)2 Quad CPU    Q9400  @ 2.66GHz stepping 0a
Dec 13 16:09:54 brawndo-PC kernel: [    0.630093] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
Dec 13 16:09:54 brawndo-PC kernel: [    0.640010] Brought up 4 CPUs
Dec 13 16:09:54 brawndo-PC kernel: [    0.640012] Total of 4 processors activated (21387.48 BogoMIPS).
Dec 13 16:09:54 brawndo-PC kernel: [    0.641433] CPU0 attaching sched-domain:
Dec 13 16:09:54 brawndo-PC kernel: [    0.641435]  domain 0: span 0-1 level MC
Dec 13 16:09:54 brawndo-PC kernel: [    0.641437]   groups: 0 1
Dec 13 16:09:54 brawndo-PC kernel: [    0.641441]   domain 1: span 0-3 level CPU
Dec 13 16:09:54 brawndo-PC kernel: [    0.641442]    groups: 0-1 (cpu_power = 2048) 2-3 (cpu_power = 2048)
Dec 13 16:09:54 brawndo-PC kernel: [    0.641448] CPU1 attaching sched-domain:
Dec 13 16:09:54 brawndo-PC kernel: [    0.641450]  domain 0: span 0-1 level MC
Dec 13 16:09:54 brawndo-PC kernel: [    0.641451]   groups: 1 0
Dec 13 16:09:54 brawndo-PC kernel: [    0.641454]   domain 1: span 0-3 level CPU
Dec 13 16:09:54 brawndo-PC kernel: [    0.641456]    groups: 0-1 (cpu_power = 2048) 2-3 (cpu_power = 2048)
Dec 13 16:09:54 brawndo-PC kernel: [    0.641460] CPU2 attaching sched-domain:
Dec 13 16:09:54 brawndo-PC kernel: [    0.641462]  domain 0: span 2-3 level MC
Dec 13 16:09:54 brawndo-PC kernel: [    0.641463]   groups: 2 3
Dec 13 16:09:54 brawndo-PC kernel: [    0.641466]   domain 1: span 0-3 level CPU
Dec 13 16:09:54 brawndo-PC kernel: [    0.641468]    groups: 2-3 (cpu_power = 2048) 0-1 (cpu_power = 2048)
Dec 13 16:09:54 brawndo-PC kernel: [    0.641472] CPU3 attaching sched-domain:
Dec 13 16:09:54 brawndo-PC kernel: [    0.641474]  domain 0: span 2-3 level MC
Dec 13 16:09:54 brawndo-PC kernel: [    0.641475]   groups: 3 2
Dec 13 16:09:54 brawndo-PC kernel: [    0.641478]   domain 1: span 0-3 level CPU
Dec 13 16:09:54 brawndo-PC kernel: [    0.641480]    groups: 2-3 (cpu_power = 2048) 0-1 (cpu_power = 2048)
Dec 13 16:09:54 brawndo-PC kernel: [    0.641583] devtmpfs: initialized
Dec 13 16:09:54 brawndo-PC kernel: [    0.641583] regulator: core version 0.5
Dec 13 16:09:54 brawndo-PC kernel: [    0.641583] Time: 16:09:49  Date: 12/13/10
Dec 13 16:09:54 brawndo-PC kernel: [    0.641583] NET: Registered protocol family 16
Dec 13 16:09:54 brawndo-PC kernel: [    0.641583] Trying to unpack rootfs image as initramfs...
Dec 13 16:09:54 brawndo-PC kernel: [    0.641583] ACPI: bus type pci registered
Dec 13 16:09:54 brawndo-PC kernel: [    0.641583] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Dec 13 16:09:54 brawndo-PC kernel: [    0.641583] PCI: Not using MMCONFIG.
Dec 13 16:09:54 brawndo-PC kernel: [    0.641583] PCI: Using configuration type 1 for base access
Dec 13 16:09:54 brawndo-PC kernel: [    0.641583] bio: create slab <bio-0> at 0
Dec 13 16:09:54 brawndo-PC kernel: [    0.641583] ACPI: EC: Look up EC in DSDT
Dec 13 16:09:54 brawndo-PC kernel: [    0.642343] ACPI: Executed 1 blocks of module-level executable AML code
Dec 13 16:09:54 brawndo-PC kernel: [    0.646339] ACPI: Interpreter enabled
Dec 13 16:09:54 brawndo-PC kernel: [    0.646341] ACPI: (supports S0 S1 S4 S5)
Dec 13 16:09:54 brawndo-PC kernel: [    0.646356] ACPI: Using IOAPIC for interrupt routing
Dec 13 16:09:54 brawndo-PC kernel: [    0.646397] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Dec 13 16:09:54 brawndo-PC kernel: [    0.651158] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
Dec 13 16:09:54 brawndo-PC kernel: [    0.657437] PCI: Using MMCONFIG at e0000000 - efffffff
Dec 13 16:09:54 brawndo-PC kernel: [    0.662666] ACPI: No dock devices found.
Dec 13 16:09:54 brawndo-PC kernel: [    0.662785] ACPI: PCI Root Bridge [PCI0] (0000:00)
Dec 13 16:09:54 brawndo-PC kernel: [    0.662864] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Dec 13 16:09:54 brawndo-PC kernel: [    0.662866] pci 0000:00:01.0: PME# disabled
Dec 13 16:09:54 brawndo-PC kernel: [    0.662904] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
Dec 13 16:09:54 brawndo-PC kernel: [    0.662906] pci 0000:00:06.0: PME# disabled
Dec 13 16:09:54 brawndo-PC kernel: [    0.662960] pci 0000:00:1a.0: reg 20 io port: [0xbc00-0xbc1f]
Dec 13 16:09:54 brawndo-PC kernel: [    0.663017] pci 0000:00:1a.1: reg 20 io port: [0xb880-0xb89f]
Dec 13 16:09:54 brawndo-PC kernel: [    0.663074] pci 0000:00:1a.2: reg 20 io port: [0xb800-0xb81f]
Dec 13 16:09:54 brawndo-PC kernel: [    0.663132] pci 0000:00:1a.7: reg 10 32bit mmio: [0xf5fffc00-0xf5ffffff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.663178] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Dec 13 16:09:54 brawndo-PC kernel: [    0.663182] pci 0000:00:1a.7: PME# disabled
Dec 13 16:09:54 brawndo-PC kernel: [    0.663214] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf5ff8000-0xf5ffbfff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.663248] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Dec 13 16:09:54 brawndo-PC kernel: [    0.663251] pci 0000:00:1b.0: PME# disabled
Dec 13 16:09:54 brawndo-PC kernel: [    0.663300] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Dec 13 16:09:54 brawndo-PC kernel: [    0.663303] pci 0000:00:1c.0: PME# disabled
Dec 13 16:09:54 brawndo-PC kernel: [    0.663360] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
Dec 13 16:09:54 brawndo-PC kernel: [    0.663364] pci 0000:00:1c.5: PME# disabled
Dec 13 16:09:54 brawndo-PC kernel: [    0.663408] pci 0000:00:1d.0: reg 20 io port: [0xb480-0xb49f]
Dec 13 16:09:54 brawndo-PC kernel: [    0.663464] pci 0000:00:1d.1: reg 20 io port: [0xb400-0xb41f]
Dec 13 16:09:54 brawndo-PC kernel: [    0.663521] pci 0000:00:1d.2: reg 20 io port: [0xb080-0xb09f]
Dec 13 16:09:54 brawndo-PC kernel: [    0.663584] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf5fff800-0xf5fffbff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.663628] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Dec 13 16:09:54 brawndo-PC kernel: [    0.663631] pci 0000:00:1d.7: PME# disabled
Dec 13 16:09:54 brawndo-PC kernel: [    0.663730] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
Dec 13 16:09:54 brawndo-PC kernel: [    0.663733] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
Dec 13 16:09:54 brawndo-PC kernel: [    0.663736] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0a00 (mask 00ff)
Dec 13 16:09:54 brawndo-PC kernel: [    0.663739] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0a00 (mask 0017)
Dec 13 16:09:54 brawndo-PC kernel: [    0.663742] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 4700 (mask 00ff)
Dec 13 16:09:54 brawndo-PC kernel: [    0.663784] pci 0000:00:1f.2: reg 10 io port: [0xb000-0xb007]
Dec 13 16:09:54 brawndo-PC kernel: [    0.663789] pci 0000:00:1f.2: reg 14 io port: [0xac00-0xac03]
Dec 13 16:09:54 brawndo-PC kernel: [    0.663793] pci 0000:00:1f.2: reg 18 io port: [0xa880-0xa887]
Dec 13 16:09:54 brawndo-PC kernel: [    0.663798] pci 0000:00:1f.2: reg 1c io port: [0xa800-0xa803]
Dec 13 16:09:54 brawndo-PC kernel: [    0.663802] pci 0000:00:1f.2: reg 20 io port: [0xa480-0xa48f]
Dec 13 16:09:54 brawndo-PC kernel: [    0.663807] pci 0000:00:1f.2: reg 24 io port: [0xa400-0xa40f]
Dec 13 16:09:54 brawndo-PC kernel: [    0.663845] pci 0000:00:1f.3: reg 10 64bit mmio: [0xf5fff400-0xf5fff4ff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.663856] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
Dec 13 16:09:54 brawndo-PC kernel: [    0.663891] pci 0000:00:1f.5: reg 10 io port: [0xa000-0xa007]
Dec 13 16:09:54 brawndo-PC kernel: [    0.663896] pci 0000:00:1f.5: reg 14 io port: [0x9c00-0x9c03]
Dec 13 16:09:54 brawndo-PC kernel: [    0.663901] pci 0000:00:1f.5: reg 18 io port: [0x9880-0x9887]
Dec 13 16:09:54 brawndo-PC kernel: [    0.663905] pci 0000:00:1f.5: reg 1c io port: [0x9800-0x9803]
Dec 13 16:09:54 brawndo-PC kernel: [    0.663909] pci 0000:00:1f.5: reg 20 io port: [0x9480-0x948f]
Dec 13 16:09:54 brawndo-PC kernel: [    0.663914] pci 0000:00:1f.5: reg 24 io port: [0x9400-0x940f]
Dec 13 16:09:54 brawndo-PC kernel: [    0.663961] pci 0000:01:00.0: reg 10 32bit mmio: [0xf9000000-0xf9ffffff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.663968] pci 0000:01:00.0: reg 14 64bit mmio pref: [0xc0000000-0xcfffffff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.663975] pci 0000:01:00.0: reg 1c 64bit mmio: [0xf6000000-0xf7ffffff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.663980] pci 0000:01:00.0: reg 24 io port: [0xcc00-0xcc7f]
Dec 13 16:09:54 brawndo-PC kernel: [    0.663984] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.664036] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.664038] pci 0000:00:01.0: bridge 32bit mmio: [0xf6000000-0xf9ffffff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.664041] pci 0000:00:01.0: bridge 64bit mmio pref: [0xc0000000-0xcfffffff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.664063] pci 0000:02:00.0: reg 10 32bit mmio: [0xfd000000-0xfdffffff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.664070] pci 0000:02:00.0: reg 14 64bit mmio pref: [0xd0000000-0xdfffffff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.664077] pci 0000:02:00.0: reg 1c 64bit mmio: [0xfa000000-0xfbffffff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.664082] pci 0000:02:00.0: reg 24 io port: [0xdc00-0xdc7f]
Dec 13 16:09:54 brawndo-PC kernel: [    0.664086] pci 0000:02:00.0: reg 30 32bit mmio pref: [0xfeae0000-0xfeafffff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.664134] pci 0000:00:06.0: bridge io port: [0xd000-0xdfff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.664136] pci 0000:00:06.0: bridge 32bit mmio: [0xfa000000-0xfeafffff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.664139] pci 0000:00:06.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.664215] pci 0000:04:00.0: reg 10 io port: [0xe800-0xe8ff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.664233] pci 0000:04:00.0: reg 18 64bit mmio: [0xfebff000-0xfebfffff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.664246] pci 0000:04:00.0: reg 20 64bit mmio pref: [0xf4ff0000-0xf4ffffff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.664253] pci 0000:04:00.0: reg 30 32bit mmio pref: [0xfebc0000-0xfebdffff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.664288] pci 0000:04:00.0: supports D1 D2
Dec 13 16:09:54 brawndo-PC kernel: [    0.664289] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 13 16:09:54 brawndo-PC kernel: [    0.664293] pci 0000:04:00.0: PME# disabled
Dec 13 16:09:54 brawndo-PC kernel: [    0.664340] pci 0000:00:1c.5: bridge io port: [0xe000-0xefff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.664343] pci 0000:00:1c.5: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.664348] pci 0000:00:1c.5: bridge 64bit mmio pref: [0xf4f00000-0xf4ffffff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.664387] pci 0000:00:1e.0: transparent bridge
Dec 13 16:09:54 brawndo-PC kernel: [    0.664409] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Dec 13 16:09:54 brawndo-PC kernel: [    0.664521] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Dec 13 16:09:54 brawndo-PC kernel: [    0.664606] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
Dec 13 16:09:54 brawndo-PC kernel: [    0.664666] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
Dec 13 16:09:54 brawndo-PC kernel: [    0.668222] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
Dec 13 16:09:54 brawndo-PC kernel: [    0.668309] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
Dec 13 16:09:54 brawndo-PC kernel: [    0.668391] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12 *14 15)
Dec 13 16:09:54 brawndo-PC kernel: [    0.668476] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 *11 12 14 15)
Dec 13 16:09:54 brawndo-PC kernel: [    0.668561] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
Dec 13 16:09:54 brawndo-PC kernel: [    0.668646] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12 14 *15)
Dec 13 16:09:54 brawndo-PC kernel: [    0.668730] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 6 7 10 11 12 14 15)
Dec 13 16:09:54 brawndo-PC kernel: [    0.668815] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 6 *7 10 11 12 14 15)
Dec 13 16:09:54 brawndo-PC kernel: [    0.668903] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Dec 13 16:09:54 brawndo-PC kernel: [    0.668907] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=none,locks=none
Dec 13 16:09:54 brawndo-PC kernel: [    0.668909] vgaarb: loaded
Dec 13 16:09:54 brawndo-PC kernel: [    0.668985] SCSI subsystem initialized
Dec 13 16:09:54 brawndo-PC kernel: [    0.668993] libata version 3.00 loaded.
Dec 13 16:09:54 brawndo-PC kernel: [    0.668993] usbcore: registered new interface driver usbfs
Dec 13 16:09:54 brawndo-PC kernel: [    0.668993] usbcore: registered new interface driver hub
Dec 13 16:09:54 brawndo-PC kernel: [    0.668993] usbcore: registered new device driver usb
Dec 13 16:09:54 brawndo-PC kernel: [    0.668993] ACPI: WMI: Mapper loaded
Dec 13 16:09:54 brawndo-PC kernel: [    0.668993] PCI: Using ACPI for IRQ routing
Dec 13 16:09:54 brawndo-PC kernel: [    0.668993] NetLabel: Initializing
Dec 13 16:09:54 brawndo-PC kernel: [    0.668993] NetLabel:  domain hash size = 128
Dec 13 16:09:54 brawndo-PC kernel: [    0.668993] NetLabel:  protocols = UNLABELED CIPSOv4
Dec 13 16:09:54 brawndo-PC kernel: [    0.668993] NetLabel:  unlabeled traffic allowed by default
Dec 13 16:09:54 brawndo-PC kernel: [    0.668993] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Dec 13 16:09:54 brawndo-PC kernel: [    0.668993] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
Dec 13 16:09:54 brawndo-PC kernel: [    0.690176] Switching to clocksource tsc
Dec 13 16:09:54 brawndo-PC kernel: [    0.691576] AppArmor: AppArmor Filesystem Enabled
Dec 13 16:09:54 brawndo-PC kernel: [    0.691594] pnp: PnP ACPI init
Dec 13 16:09:54 brawndo-PC kernel: [    0.691610] ACPI: bus type pnp registered
Dec 13 16:09:54 brawndo-PC kernel: [    0.693481] pnp: PnP ACPI: found 12 devices
Dec 13 16:09:54 brawndo-PC kernel: [    0.693483] ACPI: ACPI bus type pnp unregistered
Dec 13 16:09:54 brawndo-PC kernel: [    0.693493] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
Dec 13 16:09:54 brawndo-PC kernel: [    0.693495] system 00:01: iomem range 0xfed90000-0xfed93fff has been reserved
Dec 13 16:09:54 brawndo-PC kernel: [    0.693501] system 00:06: ioport range 0xa00-0xadf has been reserved
Dec 13 16:09:54 brawndo-PC kernel: [    0.693503] system 00:06: ioport range 0xae0-0xaef has been reserved
Dec 13 16:09:54 brawndo-PC kernel: [    0.693507] system 00:07: ioport range 0x4c0-0x4ff has been reserved
Dec 13 16:09:54 brawndo-PC kernel: [    0.693509] system 00:07: ioport range 0x800-0x87f has been reserved
Dec 13 16:09:54 brawndo-PC kernel: [    0.693511] system 00:07: ioport range 0x480-0x4bf has been reserved
Dec 13 16:09:54 brawndo-PC kernel: [    0.693514] system 00:07: iomem range 0xfed1c000-0xfed1ffff has been reserved
Dec 13 16:09:54 brawndo-PC kernel: [    0.693516] system 00:07: iomem range 0xfed20000-0xfed3ffff has been reserved
Dec 13 16:09:54 brawndo-PC kernel: [    0.693518] system 00:07: iomem range 0xfed45000-0xfed89fff has been reserved
Dec 13 16:09:54 brawndo-PC kernel: [    0.693520] system 00:07: iomem range 0xfed20000-0xfed3ffff has been reserved
Dec 13 16:09:54 brawndo-PC kernel: [    0.693522] system 00:07: iomem range 0xfed40000-0xfed8ffff could not be reserved
Dec 13 16:09:54 brawndo-PC kernel: [    0.693526] system 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved
Dec 13 16:09:54 brawndo-PC kernel: [    0.693529] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
Dec 13 16:09:54 brawndo-PC kernel: [    0.693533] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
Dec 13 16:09:54 brawndo-PC kernel: [    0.693537] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
Dec 13 16:09:54 brawndo-PC kernel: [    0.693539] system 00:0b: iomem range 0xc0000-0xcffff has been reserved
Dec 13 16:09:54 brawndo-PC kernel: [    0.693541] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
Dec 13 16:09:54 brawndo-PC kernel: [    0.693543] system 00:0b: iomem range 0x100000-0xbfffffff could not be reserved
Dec 13 16:09:54 brawndo-PC kernel: [    0.693545] system 00:0b: iomem range 0xfed90000-0xffffffff could not be reserved
Dec 13 16:09:54 brawndo-PC kernel: [    0.698230] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Dec 13 16:09:54 brawndo-PC kernel: [    0.698233] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
Dec 13 16:09:54 brawndo-PC kernel: [    0.698236] pci 0000:00:01.0:   MEM window: 0xf6000000-0xf9ffffff
Dec 13 16:09:54 brawndo-PC kernel: [    0.698238] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
Dec 13 16:09:54 brawndo-PC kernel: [    0.698242] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02
Dec 13 16:09:54 brawndo-PC kernel: [    0.698244] pci 0000:00:06.0:   IO window: 0xd000-0xdfff
Dec 13 16:09:54 brawndo-PC kernel: [    0.698247] pci 0000:00:06.0:   MEM window: 0xfa000000-0xfeafffff
Dec 13 16:09:54 brawndo-PC kernel: [    0.698249] pci 0000:00:06.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
Dec 13 16:09:54 brawndo-PC kernel: [    0.698253] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:03
Dec 13 16:09:54 brawndo-PC kernel: [    0.698255] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
Dec 13 16:09:54 brawndo-PC kernel: [    0.698259] pci 0000:00:1c.0:   MEM window: 0xf0000000-0xf01fffff
Dec 13 16:09:54 brawndo-PC kernel: [    0.698263] pci 0000:00:1c.0:   PREFETCH window: 0x000000f0200000-0x000000f03fffff
Dec 13 16:09:54 brawndo-PC kernel: [    0.698268] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:04
Dec 13 16:09:54 brawndo-PC kernel: [    0.698270] pci 0000:00:1c.5:   IO window: 0xe000-0xefff
Dec 13 16:09:54 brawndo-PC kernel: [    0.698274] pci 0000:00:1c.5:   MEM window: 0xfeb00000-0xfebfffff
Dec 13 16:09:54 brawndo-PC kernel: [    0.698277] pci 0000:00:1c.5:   PREFETCH window: 0x000000f4f00000-0x000000f4ffffff
Dec 13 16:09:54 brawndo-PC kernel: [    0.698282] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
Dec 13 16:09:54 brawndo-PC kernel: [    0.698283] pci 0000:00:1e.0:   IO window: disabled
Dec 13 16:09:54 brawndo-PC kernel: [    0.698287] pci 0000:00:1e.0:   MEM window: disabled
Dec 13 16:09:54 brawndo-PC kernel: [    0.698289] pci 0000:00:1e.0:   PREFETCH window: disabled
Dec 13 16:09:54 brawndo-PC kernel: [    0.698301]   alloc irq_desc for 16 on node -1
Dec 13 16:09:54 brawndo-PC kernel: [    0.698302]   alloc kstat_irqs on node -1
Dec 13 16:09:54 brawndo-PC kernel: [    0.698307] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 13 16:09:54 brawndo-PC kernel: [    0.698311] pci 0000:00:01.0: setting latency timer to 64
Dec 13 16:09:54 brawndo-PC kernel: [    0.698315] pci 0000:00:06.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 13 16:09:54 brawndo-PC kernel: [    0.698318] pci 0000:00:06.0: setting latency timer to 64
Dec 13 16:09:54 brawndo-PC kernel: [    0.698324] pci 0000:00:1c.0: enabling device (0104 -> 0107)
Dec 13 16:09:54 brawndo-PC kernel: [    0.698326]   alloc irq_desc for 17 on node -1
Dec 13 16:09:54 brawndo-PC kernel: [    0.698327]   alloc kstat_irqs on node -1
Dec 13 16:09:54 brawndo-PC kernel: [    0.698330] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec 13 16:09:54 brawndo-PC kernel: [    0.698333] pci 0000:00:1c.0: setting latency timer to 64
Dec 13 16:09:54 brawndo-PC kernel: [    0.698340] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Dec 13 16:09:54 brawndo-PC kernel: [    0.698343] pci 0000:00:1c.5: setting latency timer to 64
Dec 13 16:09:54 brawndo-PC kernel: [    0.698349] pci 0000:00:1e.0: setting latency timer to 64
Dec 13 16:09:54 brawndo-PC kernel: [    0.698352] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.698354] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.698356] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.698358] pci_bus 0000:01: resource 1 mem: [0xf6000000-0xf9ffffff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.698360] pci_bus 0000:01: resource 2 pref mem [0xc0000000-0xcfffffff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.698361] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.698363] pci_bus 0000:02: resource 1 mem: [0xfa000000-0xfeafffff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.698365] pci_bus 0000:02: resource 2 pref mem [0xd0000000-0xdfffffff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.698367] pci_bus 0000:03: resource 0 io:  [0x1000-0x1fff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.698368] pci_bus 0000:03: resource 1 mem: [0xf0000000-0xf01fffff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.698370] pci_bus 0000:03: resource 2 pref mem [0xf0200000-0xf03fffff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.698372] pci_bus 0000:04: resource 0 io:  [0xe000-0xefff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.698374] pci_bus 0000:04: resource 1 mem: [0xfeb00000-0xfebfffff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.698376] pci_bus 0000:04: resource 2 pref mem [0xf4f00000-0xf4ffffff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.698377] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.698379] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffffffffffff]
Dec 13 16:09:54 brawndo-PC kernel: [    0.698410] NET: Registered protocol family 2
Dec 13 16:09:54 brawndo-PC kernel: [    0.698616] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
Dec 13 16:09:54 brawndo-PC kernel: [    0.699853] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Dec 13 16:09:54 brawndo-PC kernel: [    0.702839] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Dec 13 16:09:54 brawndo-PC kernel: [    0.703201] TCP: Hash tables configured (established 524288 bind 65536)
Dec 13 16:09:54 brawndo-PC kernel: [    0.703203] TCP reno registered
Dec 13 16:09:54 brawndo-PC kernel: [    0.703312] NET: Registered protocol family 1
Dec 13 16:09:54 brawndo-PC kernel: [    0.703457] pci 0000:01:00.0: Boot video device
Dec 13 16:09:54 brawndo-PC kernel: [    0.703709] Scanning for low memory corruption every 60 seconds
Dec 13 16:09:54 brawndo-PC kernel: [    0.703815] audit: initializing netlink socket (disabled)
Dec 13 16:09:54 brawndo-PC kernel: [    0.703824] type=2000 audit(1292256589.699:1): initialized
Dec 13 16:09:54 brawndo-PC kernel: [    0.711406] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Dec 13 16:09:54 brawndo-PC kernel: [    0.712508] VFS: Disk quotas dquot_6.5.2
Dec 13 16:09:54 brawndo-PC kernel: [    0.712547] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Dec 13 16:09:54 brawndo-PC kernel: [    0.712989] fuse init (API version 7.13)
Dec 13 16:09:54 brawndo-PC kernel: [    0.713048] msgmni has been set to 15991
Dec 13 16:09:54 brawndo-PC kernel: [    0.713255] alg: No test for stdrng (krng)
Dec 13 16:09:54 brawndo-PC kernel: [    0.713297] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Dec 13 16:09:54 brawndo-PC kernel: [    0.713299] io scheduler noop registered
Dec 13 16:09:54 brawndo-PC kernel: [    0.713301] io scheduler anticipatory registered
Dec 13 16:09:54 brawndo-PC kernel: [    0.713302] io scheduler deadline registered
Dec 13 16:09:54 brawndo-PC kernel: [    0.713328] io scheduler cfq registered (default)
Dec 13 16:09:54 brawndo-PC kernel: [    0.713431]   alloc irq_desc for 24 on node -1
Dec 13 16:09:54 brawndo-PC kernel: [    0.713433]   alloc kstat_irqs on node -1
Dec 13 16:09:54 brawndo-PC kernel: [    0.713440] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
Dec 13 16:09:54 brawndo-PC kernel: [    0.713444] pcieport 0000:00:01.0: setting latency timer to 64
Dec 13 16:09:54 brawndo-PC kernel: [    0.713507]   alloc irq_desc for 25 on node -1
Dec 13 16:09:54 brawndo-PC kernel: [    0.713508]   alloc kstat_irqs on node -1
Dec 13 16:09:54 brawndo-PC kernel: [    0.713512] pcieport 0000:00:06.0: irq 25 for MSI/MSI-X
Dec 13 16:09:54 brawndo-PC kernel: [    0.713516] pcieport 0000:00:06.0: setting latency timer to 64
Dec 13 16:09:54 brawndo-PC kernel: [    0.713587]   alloc irq_desc for 26 on node -1
Dec 13 16:09:54 brawndo-PC kernel: [    0.713588]   alloc kstat_irqs on node -1
Dec 13 16:09:54 brawndo-PC kernel: [    0.713594] pcieport 0000:00:1c.0: irq 26 for MSI/MSI-X
Dec 13 16:09:54 brawndo-PC kernel: [    0.713599] pcieport 0000:00:1c.0: setting latency timer to 64
Dec 13 16:09:54 brawndo-PC kernel: [    0.713687]   alloc irq_desc for 27 on node -1
Dec 13 16:09:54 brawndo-PC kernel: [    0.713689]   alloc kstat_irqs on node -1
Dec 13 16:09:54 brawndo-PC kernel: [    0.713694] pcieport 0000:00:1c.5: irq 27 for MSI/MSI-X
Dec 13 16:09:54 brawndo-PC kernel: [    0.713700] pcieport 0000:00:1c.5: setting latency timer to 64
Dec 13 16:09:54 brawndo-PC kernel: [    0.713764] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 13 16:09:54 brawndo-PC kernel: [    0.713826] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Dec 13 16:09:54 brawndo-PC kernel: [    0.713912] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Dec 13 16:09:54 brawndo-PC kernel: [    0.713915] ACPI: Power Button [PWRB]
Dec 13 16:09:54 brawndo-PC kernel: [    0.713950] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Dec 13 16:09:54 brawndo-PC kernel: [    0.713951] ACPI: Power Button [PWRF]
Dec 13 16:09:54 brawndo-PC kernel: [    0.714502] ACPI: SSDT 00000000bff9e0c0 00235 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
Dec 13 16:09:54 brawndo-PC kernel: [    0.714713] processor LNXCPU:00: registered as cooling_device0
Dec 13 16:09:54 brawndo-PC kernel: [    0.715025] ACPI: SSDT 00000000bff9e300 00235 (v01 DpgPmm  P002Ist 00000012 INTL 20051117)
Dec 13 16:09:54 brawndo-PC kernel: [    0.715227] processor LNXCPU:01: registered as cooling_device1
Dec 13 16:09:54 brawndo-PC kernel: [    0.715546] ACPI: SSDT 00000000bff9e540 00235 (v01 DpgPmm  P003Ist 00000012 INTL 20051117)
Dec 13 16:09:54 brawndo-PC kernel: [    0.715744] processor LNXCPU:02: registered as cooling_device2
Dec 13 16:09:54 brawndo-PC kernel: [    0.716059] ACPI: SSDT 00000000bff9e780 00235 (v01 DpgPmm  P004Ist 00000012 INTL 20051117)
Dec 13 16:09:54 brawndo-PC kernel: [    0.716259] processor LNXCPU:03: registered as cooling_device3
Dec 13 16:09:54 brawndo-PC kernel: [    0.718503] Linux agpgart interface v0.103
Dec 13 16:09:54 brawndo-PC kernel: [    0.718527] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Dec 13 16:09:54 brawndo-PC kernel: [    0.719471] brd: module loaded
Dec 13 16:09:54 brawndo-PC kernel: [    0.719850] loop: module loaded
Dec 13 16:09:54 brawndo-PC kernel: [    0.719910] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Dec 13 16:09:54 brawndo-PC kernel: [    0.719979] ata_piix 0000:00:1f.2: version 2.13
Dec 13 16:09:54 brawndo-PC kernel: [    0.719992]   alloc irq_desc for 19 on node -1
Dec 13 16:09:54 brawndo-PC kernel: [    0.719993]   alloc kstat_irqs on node -1
Dec 13 16:09:54 brawndo-PC kernel: [    0.719999] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Dec 13 16:09:54 brawndo-PC kernel: [    0.720002] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Dec 13 16:09:54 brawndo-PC kernel: [    0.720036] ata_piix 0000:00:1f.2: setting latency timer to 64
Dec 13 16:09:54 brawndo-PC kernel: [    0.720089] scsi0 : ata_piix
Dec 13 16:09:54 brawndo-PC kernel: [    0.720144] scsi1 : ata_piix
Dec 13 16:09:54 brawndo-PC kernel: [    0.721259] ata1: SATA max UDMA/133 cmd 0xb000 ctl 0xac00 bmdma 0xa480 irq 19
Dec 13 16:09:54 brawndo-PC kernel: [    0.721264] ata2: SATA max UDMA/133 cmd 0xa880 ctl 0xa800 bmdma 0xa488 irq 19
Dec 13 16:09:54 brawndo-PC kernel: [    0.721286] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Dec 13 16:09:54 brawndo-PC kernel: [    0.721299] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
Dec 13 16:09:54 brawndo-PC kernel: [    0.721347] ata_piix 0000:00:1f.5: setting latency timer to 64
Dec 13 16:09:54 brawndo-PC kernel: [    0.721380] scsi2 : ata_piix
Dec 13 16:09:54 brawndo-PC kernel: [    0.721421] scsi3 : ata_piix
Dec 13 16:09:54 brawndo-PC kernel: [    0.722323] ata3: SATA max UDMA/133 cmd 0xa000 ctl 0x9c00 bmdma 0x9480 irq 19
Dec 13 16:09:54 brawndo-PC kernel: [    0.722326] ata4: SATA max UDMA/133 cmd 0x9880 ctl 0x9800 bmdma 0x9488 irq 19
Dec 13 16:09:54 brawndo-PC kernel: [    0.722592] Fixed MDIO Bus: probed
Dec 13 16:09:54 brawndo-PC kernel: [    0.722616] PPP generic driver version 2.4.2
Dec 13 16:09:54 brawndo-PC kernel: [    0.722644] tun: Universal TUN/TAP device driver, 1.6
Dec 13 16:09:54 brawndo-PC kernel: [    0.722646] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Dec 13 16:09:54 brawndo-PC kernel: [    0.722706] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Dec 13 16:09:54 brawndo-PC kernel: [    0.722719]   alloc irq_desc for 18 on node -1
Dec 13 16:09:54 brawndo-PC kernel: [    0.722721]   alloc kstat_irqs on node -1
Dec 13 16:09:54 brawndo-PC kernel: [    0.722724] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Dec 13 16:09:54 brawndo-PC kernel: [    0.722743] ehci_hcd 0000:00:1a.7: setting latency timer to 64
Dec 13 16:09:54 brawndo-PC kernel: [    0.722746] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Dec 13 16:09:54 brawndo-PC kernel: [    0.722769] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Dec 13 16:09:54 brawndo-PC kernel: [    0.722790] ehci_hcd 0000:00:1a.7: debug port 1
Dec 13 16:09:54 brawndo-PC kernel: [    0.726673] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
Dec 13 16:09:54 brawndo-PC kernel: [    0.726685] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf5fffc00
Dec 13 16:09:54 brawndo-PC kernel: [    0.749566] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Dec 13 16:09:54 brawndo-PC kernel: [    0.749664] usb usb1: configuration #1 chosen from 1 choice
Dec 13 16:09:54 brawndo-PC kernel: [    0.749688] hub 1-0:1.0: USB hub found
Dec 13 16:09:54 brawndo-PC kernel: [    0.749697] hub 1-0:1.0: 6 ports detected
Dec 13 16:09:54 brawndo-PC kernel: [    0.749753]   alloc irq_desc for 23 on node -1
Dec 13 16:09:54 brawndo-PC kernel: [    0.749754]   alloc kstat_irqs on node -1
Dec 13 16:09:54 brawndo-PC kernel: [    0.749760] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Dec 13 16:09:54 brawndo-PC kernel: [    0.749779] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Dec 13 16:09:54 brawndo-PC kernel: [    0.749781] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Dec 13 16:09:54 brawndo-PC kernel: [    0.749810] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Dec 13 16:09:54 brawndo-PC kernel: [    0.749830] ehci_hcd 0000:00:1d.7: debug port 1
Dec 13 16:09:54 brawndo-PC kernel: [    0.753710] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Dec 13 16:09:54 brawndo-PC kernel: [    0.753726] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf5fff800
Dec 13 16:09:54 brawndo-PC kernel: [    0.769562] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Dec 13 16:09:54 brawndo-PC kernel: [    0.769663] usb usb2: configuration #1 chosen from 1 choice
Dec 13 16:09:54 brawndo-PC kernel: [    0.769685] hub 2-0:1.0: USB hub found
Dec 13 16:09:54 brawndo-PC kernel: [    0.769692] hub 2-0:1.0: 6 ports detected
Dec 13 16:09:54 brawndo-PC kernel: [    0.769745] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Dec 13 16:09:54 brawndo-PC kernel: [    0.769759] uhci_hcd: USB Universal Host Controller Interface driver
Dec 13 16:09:54 brawndo-PC kernel: [    0.769793] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 13 16:09:54 brawndo-PC kernel: [    0.769800] uhci_hcd 0000:00:1a.0: setting latency timer to 64
Dec 13 16:09:54 brawndo-PC kernel: [    0.769803] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Dec 13 16:09:54 brawndo-PC kernel: [    0.769830] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Dec 13 16:09:54 brawndo-PC kernel: [    0.769861] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000bc00
Dec 13 16:09:54 brawndo-PC kernel: [    0.769924] usb usb3: configuration #1 chosen from 1 choice
Dec 13 16:09:54 brawndo-PC kernel: [    0.769942] hub 3-0:1.0: USB hub found
Dec 13 16:09:54 brawndo-PC kernel: [    0.769947] hub 3-0:1.0: 2 ports detected
Dec 13 16:09:54 brawndo-PC kernel: [    0.769983]   alloc irq_desc for 21 on node -1
Dec 13 16:09:54 brawndo-PC kernel: [    0.769984]   alloc kstat_irqs on node -1
Dec 13 16:09:54 brawndo-PC kernel: [    0.769989] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Dec 13 16:09:54 brawndo-PC kernel: [    0.769993] uhci_hcd 0000:00:1a.1: setting latency timer to 64
Dec 13 16:09:54 brawndo-PC kernel: [    0.769996] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Dec 13 16:09:54 brawndo-PC kernel: [    0.770019] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Dec 13 16:09:54 brawndo-PC kernel: [    0.770044] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000b880
Dec 13 16:09:54 brawndo-PC kernel: [    0.770107] usb usb4: configuration #1 chosen from 1 choice
Dec 13 16:09:54 brawndo-PC kernel: [    0.770125] hub 4-0:1.0: USB hub found
Dec 13 16:09:54 brawndo-PC kernel: [    0.770129] hub 4-0:1.0: 2 ports detected
Dec 13 16:09:54 brawndo-PC kernel: [    0.770162] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Dec 13 16:09:54 brawndo-PC kernel: [    0.770167] uhci_hcd 0000:00:1a.2: setting latency timer to 64
Dec 13 16:09:54 brawndo-PC kernel: [    0.770169] uhci_hcd 0000:00:1a.2: UHCI Host Controller
Dec 13 16:09:54 brawndo-PC kernel: [    0.770196] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
Dec 13 16:09:54 brawndo-PC kernel: [    0.770219] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000b800
Dec 13 16:09:54 brawndo-PC kernel: [    0.770278] usb usb5: configuration #1 chosen from 1 choice
Dec 13 16:09:54 brawndo-PC kernel: [    0.770302] hub 5-0:1.0: USB hub found
Dec 13 16:09:54 brawndo-PC kernel: [    0.770306] hub 5-0:1.0: 2 ports detected
Dec 13 16:09:54 brawndo-PC kernel: [    0.770339] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Dec 13 16:09:54 brawndo-PC kernel: [    0.770343] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Dec 13 16:09:54 brawndo-PC kernel: [    0.770345] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Dec 13 16:09:54 brawndo-PC kernel: [    0.770371] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
Dec 13 16:09:54 brawndo-PC kernel: [    0.770391] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000b480
Dec 13 16:09:54 brawndo-PC kernel: [    0.770449] usb usb6: configuration #1 chosen from 1 choice
Dec 13 16:09:54 brawndo-PC kernel: [    0.770469] hub 6-0:1.0: USB hub found
Dec 13 16:09:54 brawndo-PC kernel: [    0.770473] hub 6-0:1.0: 2 ports detected
Dec 13 16:09:54 brawndo-PC kernel: [    0.770505] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Dec 13 16:09:54 brawndo-PC kernel: [    0.770510] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Dec 13 16:09:54 brawndo-PC kernel: [    0.770513] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Dec 13 16:09:54 brawndo-PC kernel: [    0.770535] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
Dec 13 16:09:54 brawndo-PC kernel: [    0.770554] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b400
Dec 13 16:09:54 brawndo-PC kernel: [    0.770621] usb usb7: configuration #1 chosen from 1 choice
Dec 13 16:09:54 brawndo-PC kernel: [    0.770639] hub 7-0:1.0: USB hub found
Dec 13 16:09:54 brawndo-PC kernel: [    0.770645] hub 7-0:1.0: 2 ports detected
Dec 13 16:09:54 brawndo-PC kernel: [    0.770678] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Dec 13 16:09:54 brawndo-PC kernel: [    0.770682] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Dec 13 16:09:54 brawndo-PC kernel: [    0.770684] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Dec 13 16:09:54 brawndo-PC kernel: [    0.770712] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
Dec 13 16:09:54 brawndo-PC kernel: [    0.770732] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b080
Dec 13 16:09:54 brawndo-PC kernel: [    0.770793] usb usb8: configuration #1 chosen from 1 choice
Dec 13 16:09:54 brawndo-PC kernel: [    0.770811] hub 8-0:1.0: USB hub found
Dec 13 16:09:54 brawndo-PC kernel: [    0.770815] hub 8-0:1.0: 2 ports detected
Dec 13 16:09:54 brawndo-PC kernel: [    0.770884] PNP: No PS/2 controller found. Probing ports directly.
Dec 13 16:09:54 brawndo-PC kernel: [    0.773239] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 13 16:09:54 brawndo-PC kernel: [    0.773244] serio: i8042 AUX port at 0x60,0x64 irq 12
Dec 13 16:09:54 brawndo-PC kernel: [    0.773321] mice: PS/2 mouse device common for all mice
Dec 13 16:09:54 brawndo-PC kernel: [    0.773394] rtc_cmos 00:03: RTC can wake from S4
Dec 13 16:09:54 brawndo-PC kernel: [    0.773423] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Dec 13 16:09:54 brawndo-PC kernel: [    0.773443] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Dec 13 16:09:54 brawndo-PC kernel: [    0.773544] device-mapper: uevent: version 1.0.3
Dec 13 16:09:54 brawndo-PC kernel: [    0.773611] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Dec 13 16:09:54 brawndo-PC kernel: [    0.773690] device-mapper: multipath: version 1.1.0 loaded
Dec 13 16:09:54 brawndo-PC kernel: [    0.773692] device-mapper: multipath round-robin: version 1.0.0 loaded
Dec 13 16:09:54 brawndo-PC kernel: [    0.773849] cpuidle: using governor ladder
Dec 13 16:09:54 brawndo-PC kernel: [    0.773851] cpuidle: using governor menu
Dec 13 16:09:54 brawndo-PC kernel: [    0.774095] TCP cubic registered
Dec 13 16:09:54 brawndo-PC kernel: [    0.774200] NET: Registered protocol family 10
Dec 13 16:09:54 brawndo-PC kernel: [    0.774525] lo: Disabled Privacy Extensions
Dec 13 16:09:54 brawndo-PC kernel: [    0.774729] NET: Registered protocol family 17
Dec 13 16:09:54 brawndo-PC kernel: [    0.775618] PM: Resume from disk failed.
Dec 13 16:09:54 brawndo-PC kernel: [    0.775626] registered taskstats version 1
Dec 13 16:09:54 brawndo-PC kernel: [    0.775944]   Magic number: 6:327:186
Dec 13 16:09:54 brawndo-PC kernel: [    0.776012] rtc_cmos 00:03: setting system clock to 2010-12-13 16:09:49 UTC (1292256589)
Dec 13 16:09:54 brawndo-PC kernel: [    0.776014] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec 13 16:09:54 brawndo-PC kernel: [    0.776016] EDD information not available.
Dec 13 16:09:54 brawndo-PC kernel: [    0.786547] Freeing initrd memory: 8205k freed
Dec 13 16:09:54 brawndo-PC kernel: [    1.070640] ata4: SATA link down (SStatus 0 SControl 300)
Dec 13 16:09:54 brawndo-PC kernel: [    1.081252] ata3: SATA link down (SStatus 0 SControl 300)
Dec 13 16:09:54 brawndo-PC kernel: [    1.420007] usb 5-2: new low speed USB device using uhci_hcd and address 2
Dec 13 16:09:54 brawndo-PC kernel: [    1.420649] ata2.00: SATA link down (SStatus 0 SControl 300)
Dec 13 16:09:54 brawndo-PC kernel: [    1.420660] ata2.01: SATA link down (SStatus 0 SControl 300)
Dec 13 16:09:54 brawndo-PC kernel: [    1.560051] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec 13 16:09:54 brawndo-PC kernel: [    1.560062] ata1.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec 13 16:09:54 brawndo-PC kernel: [    1.603125] usb 5-2: configuration #1 chosen from 1 choice
Dec 13 16:09:54 brawndo-PC kernel: [    1.612915] ata1.00: ATA-7: WDC WD5000AAKS-00TMA0, 12.01C01, max UDMA/133
Dec 13 16:09:54 brawndo-PC kernel: [    1.612918] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Dec 13 16:09:54 brawndo-PC kernel: [    1.612937] ata1.01: ATA-7: Patriot Warp V2 32GB SSD, 02.10104, max UDMA/133
Dec 13 16:09:54 brawndo-PC kernel: [    1.612940] ata1.01: 62533296 sectors, multi 1: LBA48 
Dec 13 16:09:54 brawndo-PC kernel: [    1.654641] ata1.00: configured for UDMA/133
Dec 13 16:09:54 brawndo-PC kernel: [    1.692679] ata1.01: configured for UDMA/133
Dec 13 16:09:54 brawndo-PC kernel: [    1.692766] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 12.0 PQ: 0 ANSI: 5
Dec 13 16:09:54 brawndo-PC kernel: [    1.692855] sd 0:0:0:0: Attached scsi generic sg0 type 0
Dec 13 16:09:54 brawndo-PC kernel: [    1.692881] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Dec 13 16:09:54 brawndo-PC kernel: [    1.692935] scsi 0:0:1:0: Direct-Access     ATA      Patriot Warp V2  02.1 PQ: 0 ANSI: 5
Dec 13 16:09:54 brawndo-PC kernel: [    1.692942] sd 0:0:0:0: [sda] Write Protect is off
Dec 13 16:09:54 brawndo-PC kernel: [    1.692950] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 13 16:09:54 brawndo-PC kernel: [    1.692975] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 13 16:09:54 brawndo-PC kernel: [    1.693063] sd 0:0:1:0: Attached scsi generic sg1 type 0
Dec 13 16:09:54 brawndo-PC kernel: [    1.693104] sd 0:0:1:0: [sdb] 62533296 512-byte logical blocks: (32.0 GB/29.8 GiB)
Dec 13 16:09:54 brawndo-PC kernel: [    1.693140] sd 0:0:1:0: [sdb] Write Protect is off
Dec 13 16:09:54 brawndo-PC kernel: [    1.693142] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Dec 13 16:09:54 brawndo-PC kernel: [    1.693158]  sda:
Dec 13 16:09:54 brawndo-PC kernel: [    1.693165] sd 0:0:1:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Dec 13 16:09:54 brawndo-PC kernel: [    1.699594]  sda1 sda2
Dec 13 16:09:54 brawndo-PC kernel: [    1.699758] sd 0:0:0:0: [sda] Attached SCSI disk
Dec 13 16:09:54 brawndo-PC kernel: [    1.699817]  sdb: sdb1 sdb2 sdb3
Dec 13 16:09:54 brawndo-PC kernel: [    1.762338] sd 0:0:1:0: [sdb] Attached SCSI disk
Dec 13 16:09:54 brawndo-PC kernel: [    1.762355] Freeing unused kernel memory: 876k freed
Dec 13 16:09:54 brawndo-PC kernel: [    1.762533] Write protecting the kernel read-only data: 7696k
Dec 13 16:09:54 brawndo-PC kernel: [    1.775704] udev: starting version 151
Dec 13 16:09:54 brawndo-PC kernel: [    1.802369] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Dec 13 16:09:54 brawndo-PC kernel: [    1.802389] r8169 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec 13 16:09:54 brawndo-PC kernel: [    1.802427] r8169 0000:04:00.0: setting latency timer to 64
Dec 13 16:09:54 brawndo-PC kernel: [    1.802467]   alloc irq_desc for 28 on node -1
Dec 13 16:09:54 brawndo-PC kernel: [    1.802469]   alloc kstat_irqs on node -1
Dec 13 16:09:54 brawndo-PC kernel: [    1.802480] r8169 0000:04:00.0: irq 28 for MSI/MSI-X
Dec 13 16:09:54 brawndo-PC kernel: [    1.802925] eth0: RTL8168c/8111c at 0xffffc90000c64000, 00:21:85:1c:20:de, XID 1c4000c0 IRQ 28
Dec 13 16:09:54 brawndo-PC kernel: [    1.811223] usbcore: registered new interface driver hiddev
Dec 13 16:09:54 brawndo-PC kernel: [    1.824280] input: Kensington      Kensington USB/PS2 Orbit as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input3
Dec 13 16:09:54 brawndo-PC kernel: [    1.824414] generic-usb 0003:047D:1022.0001: input,hidraw0: USB HID v1.10 Mouse [Kensington      Kensington USB/PS2 Orbit] on usb-0000:00:1a.2-2/input0
Dec 13 16:09:54 brawndo-PC kernel: [    1.824440] usbcore: registered new interface driver usbhid
Dec 13 16:09:54 brawndo-PC kernel: [    1.824468] usbhid: v2.6:USB HID core driver
Dec 13 16:09:54 brawndo-PC kernel: [    1.860568] uvesafb: NVIDIA Corporation, G92 Board - 03930024, Chip Rev   , OEM: NVIDIA, VBE v3.0
Dec 13 16:09:54 brawndo-PC kernel: [    1.883793] usb 6-2: new full speed USB device using uhci_hcd and address 2
Dec 13 16:09:54 brawndo-PC kernel: [    1.961407] uvesafb: VBIOS/hardware supports DDC2 transfers
Dec 13 16:09:54 brawndo-PC kernel: [    2.041578] uvesafb: monitor limits: vf = 63 Hz, hf = 81 kHz, clk = 170 MHz
Dec 13 16:09:54 brawndo-PC kernel: [    2.041688] uvesafb: scrolling: redraw
Dec 13 16:09:54 brawndo-PC kernel: [    2.042061] mtrr: type mismatch for f7000000,800000 old: write-back new: write-combining
Dec 13 16:09:54 brawndo-PC kernel: [    2.042064] mtrr: type mismatch for f7000000,400000 old: write-back new: write-combining
Dec 13 16:09:54 brawndo-PC kernel: [    2.042067] mtrr: type mismatch for f7000000,200000 old: write-back new: write-combining
Dec 13 16:09:54 brawndo-PC kernel: [    2.042069] mtrr: type mismatch for f7000000,100000 old: write-back new: write-combining
Dec 13 16:09:54 brawndo-PC kernel: [    2.042072] mtrr: type mismatch for f7000000,80000 old: write-back new: write-combining
Dec 13 16:09:54 brawndo-PC kernel: [    2.042074] mtrr: type mismatch for f7000000,40000 old: write-back new: write-combining
Dec 13 16:09:54 brawndo-PC kernel: [    2.042077] mtrr: type mismatch for f7000000,20000 old: write-back new: write-combining
Dec 13 16:09:54 brawndo-PC kernel: [    2.042079] mtrr: type mismatch for f7000000,10000 old: write-back new: write-combining
Dec 13 16:09:54 brawndo-PC kernel: [    2.042082] mtrr: type mismatch for f7000000,8000 old: write-back new: write-combining
Dec 13 16:09:54 brawndo-PC kernel: [    2.042084] mtrr: type mismatch for f7000000,4000 old: write-back new: write-combining
Dec 13 16:09:54 brawndo-PC kernel: [    2.042087] mtrr: type mismatch for f7000000,2000 old: write-back new: write-combining
Dec 13 16:09:54 brawndo-PC kernel: [    2.042089] mtrr: type mismatch for f7000000,1000 old: write-back new: write-combining
Dec 13 16:09:54 brawndo-PC kernel: [    2.042143] uvesafb: framebuffer at 0xf7000000, mapped to 0xffffc90011800000, using 14336k, total 14336k
Dec 13 16:09:54 brawndo-PC kernel: [    2.042145] fb0: VESA VGA frame buffer device
Dec 13 16:09:54 brawndo-PC kernel: [    2.051154] EXT4-fs (sdb2): mounted filesystem with ordered data mode
Dec 13 16:09:54 brawndo-PC kernel: [    2.055240] usb 6-2: configuration #1 chosen from 1 choice
Dec 13 16:09:54 brawndo-PC kernel: [    2.059016] hub 6-2:1.0: USB hub found
Dec 13 16:09:54 brawndo-PC kernel: [    2.060177] hub 6-2:1.0: 4 ports detected
Dec 13 16:09:54 brawndo-PC kernel: [    2.341121] usb 6-2.1: new low speed USB device using uhci_hcd and address 3
Dec 13 16:09:54 brawndo-PC kernel: [    2.477174] usb 6-2.1: configuration #1 chosen from 1 choice
Dec 13 16:09:54 brawndo-PC kernel: [    2.494300] input: G15 Gaming Keyboard as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2.1/6-2.1:1.0/input/input4
Dec 13 16:09:54 brawndo-PC kernel: [    2.494365] generic-usb 0003:046D:C226.0002: input,hidraw1: USB HID v1.10 Keyboard [G15 Gaming Keyboard] on usb-0000:00:1d.0-2.1/input0
Dec 13 16:09:54 brawndo-PC kernel: [    2.529116] input: G15 Gaming Keyboard as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2.1/6-2.1:1.1/input/input5
Dec 13 16:09:54 brawndo-PC kernel: [    2.529206] generic-usb 0003:046D:C226.0003: input,hiddev96,hidraw2: USB HID v1.10 Device [G15 Gaming Keyboard] on usb-0000:00:1d.0-2.1/input1
Dec 13 16:09:54 brawndo-PC kernel: [    2.614067] usb 6-2.4: new full speed USB device using uhci_hcd and address 4
Dec 13 16:09:54 brawndo-PC kernel: [    2.754124] usb 6-2.4: configuration #1 chosen from 1 choice
Dec 13 16:09:54 brawndo-PC kernel: [    2.777120] input: G15 GamePanel LCD as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2.4/6-2.4:1.0/input/input6
Dec 13 16:09:54 brawndo-PC kernel: [    2.777212] generic-usb 0003:046D:C227.0004: input,hiddev97,hidraw3: USB HID v1.11 Keypad [G15 GamePanel LCD] on usb-0000:00:1d.0-2.4/input0
Dec 13 16:09:54 brawndo-PC kernel: [    4.458172] udev: starting version 151
Dec 13 16:09:54 brawndo-PC kernel: [    4.466582] lp: driver loaded but no devices found
Dec 13 16:09:54 brawndo-PC kernel: [    4.481430] vga16fb: initializing
Dec 13 16:09:54 brawndo-PC kernel: [    4.481434] vga16fb: mapped to 0xffff8800000a0000
Dec 13 16:09:54 brawndo-PC kernel: [    4.481437] vga16fb: not registering due to another framebuffer present
Dec 13 16:09:54 brawndo-PC kernel: [    4.575915] nvidia: module license 'NVIDIA' taints kernel.
Dec 13 16:09:54 brawndo-PC kernel: [    4.575918] Disabling lock debugging due to kernel taint
Dec 13 16:09:54 brawndo-PC kernel: [    4.576040] type=1505 audit(1292285393.293:2):  operation="profile_load" pid=644 name="/sbin/dhclient3"
Dec 13 16:09:54 brawndo-PC kernel: [    4.576559] type=1505 audit(1292285393.293:3):  operation="profile_load" pid=644 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Dec 13 16:09:54 brawndo-PC kernel: [    4.576826] type=1505 audit(1292285393.293:4):  operation="profile_load" pid=644 name="/usr/lib/connman/scripts/dhclient-script"
Dec 13 16:09:54 brawndo-PC kernel: [    4.633359] EXT4-fs (sdb1): mounted filesystem with ordered data mode
Dec 13 16:09:54 brawndo-PC kernel: [    4.989235]   alloc irq_desc for 22 on node -1
Dec 13 16:09:54 brawndo-PC kernel: [    4.989237]   alloc kstat_irqs on node -1
Dec 13 16:09:54 brawndo-PC kernel: [    4.989243] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Dec 13 16:09:54 brawndo-PC kernel: [    4.989569] HDA Intel 0000:00:1b.0: setting latency timer to 64
Dec 13 16:09:54 brawndo-PC kernel: [    5.108134] hda_codec: ALC888: BIOS auto-probing.
Dec 13 16:09:54 brawndo-PC kernel: [    5.109466] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input7
Dec 13 16:09:54 brawndo-PC kernel: [    5.133822] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 13 16:09:54 brawndo-PC kernel: [    5.133833] nvidia 0000:01:00.0: setting latency timer to 64
Dec 13 16:09:54 brawndo-PC kernel: [    5.133841] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Dec 13 16:09:54 brawndo-PC kernel: [    5.133843] vgaarb: transferring owner from PCI:0000:01:00.0 to PCI:0000:02:00.0
Dec 13 16:09:54 brawndo-PC kernel: [    5.133980] nvidia 0000:02:00.0: enabling device (0000 -> 0003)
Dec 13 16:09:54 brawndo-PC kernel: [    5.133983] nvidia 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 13 16:09:54 brawndo-PC kernel: [    5.133988] nvidia 0000:02:00.0: setting latency timer to 64
Dec 13 16:09:54 brawndo-PC kernel: [    5.133997] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=none
Dec 13 16:09:54 brawndo-PC kernel: [    5.134111] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.24  Thu Apr 22 19:10:14 PDT 2010
Dec 13 16:09:54 brawndo-PC kernel: [    5.526002] Console: switching to colour frame buffer device 240x75
Dec 13 16:09:54 brawndo-PC kernel: [    5.608973] r8169: eth0: link up
Dec 13 16:09:54 brawndo-PC kernel: [    5.608986] r8169: eth0: link up
Dec 13 16:09:54 brawndo-PC kernel: [    5.666409] type=1505 audit(1292285394.385:5):  operation="profile_load" pid=850 name="/usr/share/gdm/guest-session/Xsession"
Dec 13 16:09:54 brawndo-PC kernel: [    5.667715] type=1505 audit(1292285394.385:6):  operation="profile_replace" pid=851 name="/sbin/dhclient3"
Dec 13 16:09:54 brawndo-PC kernel: [    5.668229] type=1505 audit(1292285394.385:7):  operation="profile_replace" pid=851 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Dec 13 16:09:54 brawndo-PC kernel: [    5.668502] type=1505 audit(1292285394.385:8):  operation="profile_replace" pid=851 name="/usr/lib/connman/scripts/dhclient-script"
Dec 13 16:09:54 brawndo-PC kernel: [    5.671240] type=1505 audit(1292285394.395:9):  operation="profile_load" pid=854 name="/usr/bin/evince"
Dec 13 16:09:54 brawndo-PC kernel: [    5.677702] type=1505 audit(1292285394.395:10):  operation="profile_load" pid=854 name="/usr/bin/evince-previewer"
Dec 13 16:09:54 brawndo-PC kernel: [    5.807853] vboxdrv: Trying to deactivate the NMI watchdog permanently...
Dec 13 16:09:54 brawndo-PC kernel: [    5.807856] vboxdrv: Successfully done.
Dec 13 16:09:54 brawndo-PC kernel: [    5.807857] vboxdrv: Found 4 processor cores.
Dec 13 16:09:54 brawndo-PC kernel: [    5.807931] VBoxDrv: dbg - g_abExecMemory=ffffffffa0d62a20
Dec 13 16:09:54 brawndo-PC kernel: [    5.807971] vboxdrv: fAsync=0 offMin=0x488 offMax=0x17a0
Dec 13 16:09:54 brawndo-PC kernel: [    5.808260] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Dec 13 16:09:54 brawndo-PC kernel: [    5.808262] vboxdrv: Successfully loaded version 3.1.6_OSE (interface 0x00100001).
Dec 13 16:09:54 brawndo-PC kernel: [    5.833285] ppdev: user-space parallel port driver
Dec 13 16:10:04 brawndo-PC kernel: [   15.740045] eth0: no IPv6 routers present
```
If you do find errors the easiest thing to do is try a different kernel.

---

### Post by robbie d on 2010-12-15
I ran the nvidia-xconfig --enable-all-gpus this morning, and when I ran sudo nvidia-settings, I got the following:

Xlib:  extension "RANDR" missing on display ":0.0".

ERROR: Cannot open display 'megabox-desktop:0.0'.


ERROR: Unable to assign attribute CursorShadow specified on line 24 of
       configuration file '/home/megabox/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 25 of
       configuration file '/home/megabox/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 26 of
       configuration file '/home/megabox/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 27 of
       configuration file '/home/megabox/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 28 of
       configuration file '/home/megabox/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 29 of
       configuration file '/home/megabox/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 30 of
       configuration file '/home/megabox/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 31 of
       configuration file '/home/megabox/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAniso specified on line 32 of
       configuration file '/home/megabox/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAA specified on line 33 of configuration
       file '/home/megabox/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 34 of
       configuration file '/home/megabox/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 35 of
       configuration file '/home/megabox/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 36 of
       configuration file '/home/megabox/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line 37 of
       configuration file '/home/megabox/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute OpenGLImageSettings specified on line 38 of
       configuration file '/home/megabox/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppEnhanced specified on line 39 of
       configuration file '/home/megabox/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedBrightness specified on line 40 of
       configuration file '/home/megabox/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 41 of
       configuration file '/home/megabox/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 42 of
       configuration file '/home/megabox/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedContrast specified on line 43 of
       configuration file '/home/megabox/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenContrast specified on line 44 of
       configuration file '/home/megabox/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueContrast specified on line 45 of
       configuration file '/home/megabox/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedGamma specified on line 46 of
       configuration file '/home/megabox/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenGamma specified on line 47 of
       configuration file '/home/megabox/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueGamma specified on line 48 of
       configuration file '/home/megabox/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute DigitalVibrance specified on line 49 of
       configuration file '/home/megabox/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute OverscanCompensation specified on line 50 of
       configuration file '/home/megabox/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureBrightness specified on line 51
       of configuration file '/home/megabox/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureContrast specified on line 52 of
       configuration file '/home/megabox/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureHue specified on line 53 of
       configuration file '/home/megabox/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSaturation specified on line 54
       of configuration file '/home/megabox/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on line
       55 of configuration file '/home/megabox/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 56 of
       configuration file '/home/megabox/.nvidia-settings-rc' (no Display
       connection).

---

### Post by tjones00 on 2010-12-15
Well this is good news since .nvidia-settings-rc has nothing to do with multiple cards.


So you generated the new xorg.conf from the commandline with X server shutdown then restarted X ("sudo service gdm start" or rebooted) to a desktop environment and ran sudo nvidia-settings from a terminal within the desktop environment correct?

nvidia-settings will not run without X server being up. The "No Display Connection" error to me is suggesting the X server is not running.

.nvida-settings-rc contains info about powermizer etc. and if this makes any sense is the "settings" for nvidia-settings

[http://linux.die.net/man/1/nvidia-settings](http://linux.die.net/man/1/nvidia-settings)

If you are recieving this error while running nvidia-settings from a terminal within a desktop environment (x server is running) try the following.

```
sudo nvidia-settings -n
```this should bypass .nvida-settings-rc and hopefully load some defaults

Once in nvidia-settings be sure to position the monitors and save the xorg.conf under "X Server Display Configuration".

Then look at "nvidia-settings Configuration" in the nvidia-settings gui this is what generates the .nvidia-settings-rc play with some of the settings and "Save Current Configuration" this should overwrite the current one that is giving you issues. If it doesn't overwrite the file backup and delete .nvidia-settings-rc then run nvidia-settings normally and it should pick up some defaults.

For example I have Enable ToolTips, Display Status Bar Slider Text Entries Show "Really Quit?" Dialog all checked. Thermal Monitor (GPU0) PowerMizer Monitor (GPU 0) Thermal Monitor (GPU 1) PowerMizer Monitor (GPU 1) all checked.

```
#
# /home/brawndo/.nvidia-settings-rc
#
# Configuration file for nvidia-settings - the NVIDIA X Server Settings utility
# Generated on Mon Dec 13 01:41:09 2010
#

# ConfigProperties:

RcFileLocale = C
ToolTips = Yes
DisplayStatusBar = Yes
SliderTextEntries = Yes
IncludeDisplayNameInConfigFile = No
ShowQuitDialog = Yes
Timer = PowerMizer_Monitor_(GPU_1),Yes,1000
Timer = Thermal_Monitor_(GPU_1),Yes,1000
Timer = PowerMizer_Monitor_(GPU_0),Yes,1000
Timer = Thermal_Monitor_(GPU_0),Yes,1000

# Attributes:

0/CursorShadow=0
0/CursorShadowAlpha=64
0/CursorShadowRed=0
0/CursorShadowGreen=0
0/CursorShadowBlue=0
0/CursorShadowXOffset=4
0/CursorShadowYOffset=2
0/SyncToVBlank=0
0/LogAniso=0
0/FSAA=0
0/TextureSharpen=0
0/AllowFlipping=1
0/FSAAAppControlled=1
0/LogAnisoAppControlled=1
0/OpenGLImageSettings=1
0/FSAAAppEnhanced=0
0/RedBrightness=0.000000
0/GreenBrightness=0.000000
0/BlueBrightness=0.000000
0/RedContrast=0.000000
0/GreenContrast=0.000000
0/BlueContrast=0.000000
0/RedGamma=1.000000
0/GreenGamma=1.000000
0/BlueGamma=1.000000
0/DigitalVibrance[DFP-0]=0
0/GPUScaling[DFP-0]=131073
0/XVideoTextureBrightness=0
0/XVideoTextureContrast=0
0/XVideoTextureHue=0
0/XVideoTextureSaturation=0
0/XVideoTextureSyncToVBlank=1
0/XVideoSyncToDisplay=65536
```

---

### Post by robbie d on 2010-12-15
Well I swapped the card identities over, so I know it recognises the other card, and now that monitor is my primary.
Interesting problem now, the other display is not on, but is not showing 'no signal' and going to sleep.

---

### Post by tjones00 on 2010-12-15
Sounds like it's now active but just not being used.

So did you get nvidia-settings running enable Xinerama and setup both monitors as separate X screens under "X Server Display Configuration"?

If it's still not working after that post the new xorg.conf and Xorg.0.log and maybe we can figure out whats missing.

I'm pretty sure there isn't anything wrong with your kernel, driver, or hardware.

---

### Post by robbie d on 2010-12-15
yes, but the system detects it no further than that. Only one screen appears in the nvidia settings tool, and doing a nvidia-settings -query all gpus only shows one gpu as active. Same with the -query screens

---

### Post by tjones00 on 2010-12-16
What does your xorg.conf look like now after making the new one via nvidia-xconfig --enable-all-gpus?

If I do the following

ctrl+alt+f2

```
sudo service gdm stop

sudo rm /etc/X11/xorg.conf

sudo nvidia-xconfig --enable-all-gpus

sudo service gdm start
```

I receive a desktop with only two monitors active (only the primary head on each card) each with their own X session (full desktop). 

My new xorg.conf looks like this. Yours should look pretty much identical except for the card names and monitor specs.

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Thu Apr 22 20:35:23 PDT 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GT"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GT"
    BusID          "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by robbie d on 2010-12-17
After blowing away xorg.conf and using the commands, I get:
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 260.19.21  (buildmeister@builder103.nvidia.com)  Thu Nov  4 20:57:26 PDT 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9500 GT"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9500 GT"
    BusID          "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```
and yes I finally worked out the code tags :)

---

### Post by tjones00 on 2010-12-17
Ok cool now that we've established that you have a nvidia generated xorg.conf that should use both monitors and both cards.

What type of behavior do you experience now when booting to a full desktop with that xorg.conf?

If both monitors are not active at this point please post the new Xorg.0.log.

---

### Post by robbie d on 2010-12-17
ok, it's back to using my left monitor (graphic card one) with the right one still off.
Here are the results of Xorg.0.log:
```

[    20.407] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    20.407] X Protocol Version 11, Revision 0
[    20.407] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    20.407] Current Operating System: Linux megabox-desktop 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686
[    20.407] Kernel command line: root=UUID=17cd22de-d4d4-40ad-8e1b-81b0460d6081 ro quiet splash 
[    20.407] Build Date: 23 November 2010  09:54:06PM
[    20.407] xorg-server 2:1.9.0-0ubuntu7.1 (For technical support please see http://www.ubuntu.com/support) 
[    20.407] Current version of pixman: 0.18.4
[    20.407] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    20.407] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    20.407] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Dec 18 06:33:21 2010
[    20.407] (==) Using config file: "/etc/X11/xorg.conf"
[    20.407] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    20.407] (==) ServerLayout "Layout0"
[    20.407] (**) |-->Screen "Screen0" (0)
[    20.407] (**) |   |-->Monitor "Monitor0"
[    20.408] (**) |   |-->Device "Device0"
[    20.408] (**) |-->Input Device "Keyboard0"
[    20.408] (**) |-->Input Device "Mouse0"
[    20.408] (**) Option "Xinerama" "0"
[    20.408] (==) Automatically adding devices
[    20.408] (==) Automatically enabling devices
[    20.408] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    20.408] 	Entry deleted from font path.
[    20.408] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    20.408] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    20.408] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    20.408] (WW) Disabling Keyboard0
[    20.408] (WW) Disabling Mouse0
[    20.408] (II) Loader magic: 0x81f8e00
[    20.408] (II) Module ABI versions:
[    20.408] 	X.Org ANSI C Emulation: 0.4
[    20.408] 	X.Org Video Driver: 8.0
[    20.408] 	X.Org XInput driver : 11.0
[    20.408] 	X.Org Server Extension : 4.0
[    20.409] (--) PCI:*(0:1:0:0) 10de:0640:1043:829a rev 161, Mem @ 0xf7000000/16777216, 0xc0000000/268435456, 0xf4000000/33554432, I/O @ 0x0000bc00/128, BIOS @ 0x????????/524288
[    20.409] (--) PCI: (0:2:0:0) 10de:0640:1043:829a rev 161, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/524288
[    20.409] (II) Open ACPI successful (/var/run/acpid.socket)
[    20.409] (II) LoadModule: "extmod"
[    20.470] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    20.478] (II) Module extmod: vendor="X.Org Foundation"
[    20.478] 	compiled for 1.9.0, module version = 1.0.0
[    20.478] 	Module class: X.Org Server Extension
[    20.478] 	ABI class: X.Org Server Extension, version 4.0
[    20.478] (II) Loading extension MIT-SCREEN-SAVER
[    20.478] (II) Loading extension XFree86-VidModeExtension
[    20.478] (II) Loading extension XFree86-DGA
[    20.478] (II) Loading extension DPMS
[    20.478] (II) Loading extension XVideo
[    20.478] (II) Loading extension XVideo-MotionCompensation
[    20.478] (II) Loading extension X-Resource
[    20.478] (II) LoadModule: "dbe"
[    20.478] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    20.478] (II) Module dbe: vendor="X.Org Foundation"
[    20.478] 	compiled for 1.9.0, module version = 1.0.0
[    20.478] 	Module class: X.Org Server Extension
[    20.478] 	ABI class: X.Org Server Extension, version 4.0
[    20.478] (II) Loading extension DOUBLE-BUFFER
[    20.478] (II) LoadModule: "glx"
[    20.478] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    20.492] (II) Module glx: vendor="NVIDIA Corporation"
[    20.492] 	compiled for 4.0.2, module version = 1.0.0
[    20.492] 	Module class: X.Org Server Extension
[    20.492] (II) NVIDIA GLX Module  260.19.21  Thu Nov  4 20:52:05 PDT 2010
[    20.492] (II) Loading extension GLX
[    20.492] (II) LoadModule: "record"
[    20.492] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    20.492] (II) Module record: vendor="X.Org Foundation"
[    20.492] 	compiled for 1.9.0, module version = 1.13.0
[    20.492] 	Module class: X.Org Server Extension
[    20.492] 	ABI class: X.Org Server Extension, version 4.0
[    20.492] (II) Loading extension RECORD
[    20.492] (II) LoadModule: "dri"
[    20.492] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    20.492] (II) Module dri: vendor="X.Org Foundation"
[    20.492] 	compiled for 1.9.0, module version = 1.0.0
[    20.492] 	ABI class: X.Org Server Extension, version 4.0
[    20.492] (II) Loading extension XFree86-DRI
[    20.492] (II) LoadModule: "dri2"
[    20.493] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    20.493] (II) Module dri2: vendor="X.Org Foundation"
[    20.493] 	compiled for 1.9.0, module version = 1.2.0
[    20.493] 	ABI class: X.Org Server Extension, version 4.0
[    20.493] (II) Loading extension DRI2
[    20.493] (II) LoadModule: "nvidia"
[    20.493] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    20.493] (II) Module nvidia: vendor="NVIDIA Corporation"
[    20.493] 	compiled for 4.0.2, module version = 1.0.0
[    20.493] 	Module class: X.Org Video Driver
[    20.493] (II) NVIDIA dlloader X Driver  260.19.21  Thu Nov  4 20:26:43 PDT 2010
[    20.493] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    20.493] (++) using VT number 7

[    20.494] (II) Loading sub module "fb"
[    20.494] (II) LoadModule: "fb"
[    20.495] (II) Loading /usr/lib/xorg/modules/libfb.so
[    20.495] (II) Module fb: vendor="X.Org Foundation"
[    20.495] 	compiled for 1.9.0, module version = 1.0.0
[    20.495] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    20.495] (II) Loading sub module "wfb"
[    20.495] (II) LoadModule: "wfb"
[    20.495] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    20.495] (II) Module wfb: vendor="X.Org Foundation"
[    20.495] 	compiled for 1.9.0, module version = 1.0.0
[    20.495] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    20.495] (II) Loading sub module "ramdac"
[    20.495] (II) LoadModule: "ramdac"
[    20.495] (II) Module "ramdac" already built-in
[    20.495] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    20.495] (==) NVIDIA(0): RGB weight 888
[    20.495] (==) NVIDIA(0): Default visual is TrueColor
[    20.495] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    20.495] (**) NVIDIA(0): Option "TwinView" "0"
[    20.495] (**) NVIDIA(0): Option "MetaModes" "nvidia-auto-select +0+0"
[    20.495] (**) NVIDIA(0): Enabling RENDER acceleration
[    20.495] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    20.495] (II) NVIDIA(0):     enabled.
[    21.987] (II) NVIDIA(0): NVIDIA GPU GeForce 9500 GT (G96) at PCI:1:0:0 (GPU-0)
[    21.987] (--) NVIDIA(0): Memory: 1048576 kBytes
[    21.987] (--) NVIDIA(0): VideoBIOS: 62.94.4b.00.00
[    21.987] (II) NVIDIA(0): Detected PCI Express Link width: 8X
[    21.987] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    21.987] (--) NVIDIA(0): Connected display device(s) on GeForce 9500 GT at PCI:1:0:0
[    21.987] (--) NVIDIA(0):     Acer AL2216W (CRT-1)
[    21.987] (--) NVIDIA(0): Acer AL2216W (CRT-1): 400.0 MHz maximum pixel clock
[    22.032] (II) NVIDIA(0): Assigned Display Device: CRT-1
[    22.032] (II) NVIDIA(0): Validated modes:
[    22.032] (II) NVIDIA(0):     "nvidia-auto-select+0+0"
[    22.032] (II) NVIDIA(0): Virtual screen size determined to be 1680 x 1050
[    22.055] (--) NVIDIA(0): DPI set to (90, 88); computed from "UseEdidDpi" X config
[    22.055] (--) NVIDIA(0):     option
[    22.055] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    22.055] (--) Depth 24 pixmap format is 32 bpp
[    22.055] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    22.931] (EE) NVIDIA(GPU-1): Failed to initialize the NVIDIA GPU at PCI:2:0:0.  Please
[    22.931] (EE) NVIDIA(GPU-1):     check your system's kernel log for additional error
[    22.931] (EE) NVIDIA(GPU-1):     messages and refer to Chapter 8: Common Problems in the
[    22.931] (EE) NVIDIA(GPU-1):     README for additional information.
[    22.931] (EE) NVIDIA(GPU-1): Failed to initialize the NVIDIA graphics device!
[    22.933] (II) NVIDIA(0): Initialized GPU GART.
[    22.939] (II) NVIDIA(0): Setting mode "nvidia-auto-select+0+0"
[    22.992] (II) Loading extension NV-GLX
[    23.011] (II) NVIDIA(0): Initialized OpenGL Acceleration
[    23.016] (==) NVIDIA(0): Disabling shared memory pixmaps
[    23.016] (II) NVIDIA(0): Initialized X Rendering Acceleration
[    23.016] (==) NVIDIA(0): Backing store disabled
[    23.016] (==) NVIDIA(0): Silken mouse enabled
[    23.031] (**) NVIDIA(0): DPMS enabled
[    23.031] (II) Loading extension NV-CONTROL
[    23.032] (II) Loading extension XINERAMA
[    23.032] (II) Loading sub module "dri2"
[    23.032] (II) LoadModule: "dri2"
[    23.032] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[    23.032] (II) NVIDIA(0): [DRI2] Setup complete
[    23.032] (==) RandR enabled
[    23.032] (II) Initializing built-in extension Generic Event Extension
[    23.032] (II) Initializing built-in extension SHAPE
[    23.032] (II) Initializing built-in extension MIT-SHM
[    23.032] (II) Initializing built-in extension XInputExtension
[    23.032] (II) Initializing built-in extension XTEST
[    23.032] (II) Initializing built-in extension BIG-REQUESTS
[    23.032] (II) Initializing built-in extension SYNC
[    23.032] (II) Initializing built-in extension XKEYBOARD
[    23.032] (II) Initializing built-in extension XC-MISC
[    23.032] (II) Initializing built-in extension SECURITY
[    23.032] (II) Initializing built-in extension XINERAMA
[    23.032] (II) Initializing built-in extension XFIXES
[    23.032] (II) Initializing built-in extension RENDER
[    23.032] (II) Initializing built-in extension RANDR
[    23.032] (II) Initializing built-in extension COMPOSITE
[    23.032] (II) Initializing built-in extension DAMAGE
[    23.032] (II) Initializing built-in extension GESTURE
[    23.034] (II) Initializing extension GLX
[    23.060] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    23.065] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    23.065] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.065] (II) LoadModule: "evdev"
[    23.065] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.065] (II) Module evdev: vendor="X.Org Foundation"
[    23.065] 	compiled for 1.9.0, module version = 2.3.2
[    23.065] 	Module class: X.Org XInput Driver
[    23.065] 	ABI class: X.Org XInput driver, version 11.0
[    23.065] (**) Power Button: always reports core events
[    23.065] (**) Power Button: Device: "/dev/input/event1"
[    23.093] (II) Power Button: Found keys
[    23.093] (II) Power Button: Configuring as keyboard
[    23.093] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    23.093] (**) Option "xkb_rules" "evdev"
[    23.093] (**) Option "xkb_model" "pc105"
[    23.093] (**) Option "xkb_layout" "us"
[    23.094] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    23.094] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.094] (**) Power Button: always reports core events
[    23.094] (**) Power Button: Device: "/dev/input/event0"
[    23.125] (II) Power Button: Found keys
[    23.125] (II) Power Button: Configuring as keyboard
[    23.125] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    23.125] (**) Option "xkb_rules" "evdev"
[    23.125] (**) Option "xkb_model" "pc105"
[    23.125] (**) Option "xkb_layout" "us"
[    23.127] (II) config/udev: Adding input device Logitech G500 (/dev/input/event2)
[    23.127] (**) Logitech G500: Applying InputClass "evdev pointer catchall"
[    23.127] (**) Logitech G500: always reports core events
[    23.127] (**) Logitech G500: Device: "/dev/input/event2"
[    23.157] (II) Logitech G500: Found 20 mouse buttons
[    23.157] (II) Logitech G500: Found scroll wheel(s)
[    23.157] (II) Logitech G500: Found relative axes
[    23.157] (II) Logitech G500: Found x and y relative axes
[    23.157] (II) Logitech G500: Configuring as mouse
[    23.157] (**) Logitech G500: YAxisMapping: buttons 4 and 5
[    23.157] (**) Logitech G500: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    23.157] (II) XINPUT: Adding extended input device "Logitech G500" (type: MOUSE)
[    23.157] (II) Logitech G500: initialized for relative axes.
[    23.157] (II) config/udev: Adding input device Logitech G500 (/dev/input/mouse0)
[    23.157] (II) No input driver/identifier specified (ignoring)
[    23.158] (II) config/udev: Adding input device Logitech G500 (/dev/input/event3)
[    23.158] (**) Logitech G500: Applying InputClass "evdev keyboard catchall"
[    23.158] (**) Logitech G500: always reports core events
[    23.158] (**) Logitech G500: Device: "/dev/input/event3"
[    23.189] (II) Logitech G500: Found 1 mouse buttons
[    23.189] (II) Logitech G500: Found scroll wheel(s)
[    23.189] (II) Logitech G500: Found relative axes
[    23.189] (II) Logitech G500: Found absolute axes
[    23.189] (II) evdev-grail: failed to open grail, no gesture support
[    23.189] (II) Logitech G500: Found keys
[    23.189] (II) Logitech G500: Configuring as mouse
[    23.189] (II) Logitech G500: Configuring as keyboard
[    23.189] (**) Logitech G500: YAxisMapping: buttons 4 and 5
[    23.189] (**) Logitech G500: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    23.189] (II) XINPUT: Adding extended input device "Logitech G500" (type: KEYBOARD)
[    23.189] (**) Option "xkb_rules" "evdev"
[    23.189] (**) Option "xkb_model" "pc105"
[    23.189] (**) Option "xkb_layout" "us"
[    23.189] (EE) Logitech G500: failed to initialize for relative axes.
[    23.189] (II) Logitech G500: initialized for absolute axes.
[    23.190] (II) config/udev: Adding input device Apple, Inc Apple Keyboard (/dev/input/event4)
[    23.190] (**) Apple, Inc Apple Keyboard: Applying InputClass "evdev keyboard catchall"
[    23.190] (**) Apple, Inc Apple Keyboard: always reports core events
[    23.190] (**) Apple, Inc Apple Keyboard: Device: "/dev/input/event4"
[    23.221] (II) Apple, Inc Apple Keyboard: Found keys
[    23.221] (II) Apple, Inc Apple Keyboard: Configuring as keyboard
[    23.221] (II) XINPUT: Adding extended input device "Apple, Inc Apple Keyboard" (type: KEYBOARD)
[    23.221] (**) Option "xkb_rules" "evdev"
[    23.221] (**) Option "xkb_model" "pc105"
[    23.221] (**) Option "xkb_layout" "us"
[    23.221] (II) config/udev: Adding input device Apple, Inc Apple Keyboard (/dev/input/event5)
[    23.221] (**) Apple, Inc Apple Keyboard: Applying InputClass "evdev keyboard catchall"
[    23.221] (**) Apple, Inc Apple Keyboard: always reports core events
[    23.221] (**) Apple, Inc Apple Keyboard: Device: "/dev/input/event5"
[    23.253] (II) Apple, Inc Apple Keyboard: Found keys
[    23.253] (II) Apple, Inc Apple Keyboard: Configuring as keyboard
[    23.253] (II) XINPUT: Adding extended input device "Apple, Inc Apple Keyboard" (type: KEYBOARD)
[    23.253] (**) Option "xkb_rules" "evdev"
[    23.253] (**) Option "xkb_model" "pc105"
[    23.253] (**) Option "xkb_layout" "us"
[    23.566] (II) NVIDIA(0): Setting mode "1280x1024"
[    93.476] (II) NVIDIA(0): Setting mode "CRT-1:1680x1050@1680x1050+0+0"

```

---

### Post by tjones00 on 2010-12-17
Bleh.

[    22.931] (EE) NVIDIA(GPU-1): Failed to initialize the NVIDIA GPU at PCI:2:0:0.  Please
[    22.931] (EE) NVIDIA(GPU-1):     check your system's kernel log for additional error
[    22.931] (EE) NVIDIA(GPU-1):     messages and refer to Chapter 8: Common Problems in the
[    22.931] (EE) NVIDIA(GPU-1):     README for additional information.


Without going into too much detail as to why tell me what happens when you do this.



Option 1) At the grub boot menu edit the default image (press e) and do the following.

replace:

quiet splash 

with: 

nomodeset

Then boot. Did that fix it?

If not try replacing "quiet splash" with:

nomodeset noplymouth

Did that fix it?



Option 2) Take the 2nd card out of the computer boot up linux then shutdown. Now put the 2nd card back in and boot again.

Did that fix it?

---

### Post by robbie d on 2010-12-18
Tried all of these, to no avail.
The grub boot only had 'quiet' in there, so changed that to 'nomodeset' rebooted, didn't work, tried 'nomodeset noplymouth'. Rebooted, didn't work.
It was interesting to note that each time I went in to edit the grub boot, my previous changes were gone.
Then I took card #2 out of the computer, Rebooted. Shut down and reinserted, no change.
Then I took card #2 out again, rebooted, generated new xorg and shut down.
reinserted card, rebooted, generate new xorg, no change.

Could this be a product of many upgrades? I'm pretty sure this pc started with 9.04 then upgraded to 9.10, and at that stage both monitors were ok. Then 10.04 and now 10.10 where both monitors haven't worked at all (only monitor 1).

---

### Post by tjones00 on 2010-12-18
Editing the kernel boot parameters at the grub boot menu is just a temporary thing. If one of those parameters worked we would have needed to update grub to make it stick.

So they are not suppose to last don't worry.



Ok bad news yeah none of that worked.

With 10.04 and 10.10 there was a lot of work done with KMS (kernel mode setting) that tries to get you to a desktop (x environment) faster and plymouth was introduced with 10.04 replacing usplash (plymouth does mess with graphic settings before the x server is loaded).

That is why we tried nomodeset (turns off kms) and noplymouth. Usually those two parameters can clear up any graphics issues with ubuntu 10.04 or 10.10.

At this point I think you may be correct about the upgrades. My current build wasn't an upgrade and it works. Hopefully someone reading this thread who has experience with dual nvidia cards can shed some light as to upgrading from 9 to 10 vs a fresh install of 10.

To my knowledge the biggest graphical config changes from 9 to 10 were kms and plymouth hand off to x server.

As ugly as it sounds I'd suggest a clean install of 10.10. If you do go ahead with a reinstall try using the Nvidia proprietary drivers provided by Ubuntu via Hardware drivers before getting the lastest from Nvidia.

---

### Post by robbie d on 2010-12-19
It seems a pain, as any OS re-install is, but like windoze, it's good to start afresh rather than upgading.
Thanks for all your help, I'll give a new install a go and see what happens. Just a question, this is a modern quad core desktop, are there any advantages to 64 over 32 bit? I only have 4Gb of ram in this machine, and was running 32 bit before.

---

### Post by tjones00 on 2010-12-19
64b is faster (only noticeable in heavy computing) than 32b but requires more ram and creates more headaches in my opinion.

Most software is written for 32b. Sometimes when running 64b Ubuntu you'll have to hack around some 32b dependencies (libs) for specific software. I remember having do do this on my last 64b install I can't remember what software though.

64b should be fine with 4GB of ram. Generally I like to use 32b or 32b server pae due to stability and dependencies. If you plan on running any virtual machines or ramdisks or a ssd no swap system I'd stick to the 32b to keep more of the ram clear.

I decided I'll give 10.10 32b a fresh install (currently using 10.04 32b)as well over the next couple days and see if it gives me issues setting up the 2 cards. It was about time for me to upgrade anyway. After major headaches when moving from 9.10 to 10.04 I was putting it off. I'll post my experience here for you.

---

### Post by robbie d on 2010-12-19
Thanks for that, most of my stuff is light computing, model aircraft design, not too heavy.
I'll check my system and see what else I need to clean off it tonight, being dual boot, and having NAS I have plenty of places to shift stuff. I'm not looking forward to fixing the boot mechanism, but hopefully that will be easy with 10.10 I will be interested to hear your results.

---

### Post by robbie d on 2010-12-20
Well we have success. I reinstalled and all is well :)
setup xinerama and all. :)
Thanks for all the help. The new installer works a charm too, didn't kill my xp partition either :)

---

### Post by tjones00 on 2010-12-20
Good to hear I just completed my install and setup and was about to post the results for you.

No issues on my end. 

To recap for anybody trying to setup 2 nvidia cards and multiple displays.

Do a clean install of 10.10 (the lesson of this thread).

Install the Nvidia drivers via System > Administration > Additional Drivers or Hardware Drivers.

reboot

Once the desktop is loaded (1 display active) press. Ctrl+Alt+f2 and login

type
```

sudo service gdm stop

sudo rm /etc/X11/xorg.conf

sudo nvidia-xconfig --enable-all-gpus

sudo service gdm start
```Once the desktop is loaded again you should have 2 displays active each with their own X session.

Open a terminal via Applications > Accessories > Terminal and type

```
sudo nvidia-settings
```Under "X Server Display Configuration" setup your display locations configure the displays for separate X screens and enable Xinerama. Press "Save to X Configuration File" and reboot.

---

### Post by robbie d on 2010-12-20
Excellent. I'm not sure which modules became corrupted during the upgrades but everything worked for me. I didn't even need to create a new xorg.conf, both monitors appeared in the Nvidia-settings tool straight away. Even played Urban Terror for a while to make sure it was all working as it should be.

---

### Post by BicyclerBoy on 2010-12-21
The problem could just have been missing Device sections in the xorg.conf.

Xorg website X11R6 defining docs.
Each used video head of each video card must have a separate device section, so you needed 4.
Your driver re-install might have fixed the xorg.conf file.

---

### Post by robbie d on 2010-12-21
I'm currently only running 2 monitors,  but just in case i'll post up my current xorg.conf to see if there is any difference.
I was using the ubuntu supplied drivers until last week, when I decided to have another crack at getting the two monitors running (after not bothering with ubuntu for 6 months due to the problem). It will be interesting to see what happens when I add a third and fourth monitor in the new year.

---

### Post by tjones00 on 2010-12-21
His original xorg.conf had 2 device sections and the proper pci call for each card. The nvidia generated one that failed on his install also had a proper setup.

Whatever it was it wasn't his xorg.conf. The nvidia generated one he's using now failed on the other system and they should look pretty much identical at this point. His failed xorg.confs are in this thread if you want to take a look.

Honestly I have no idea his xorg.conf and dmesg looked fine. His Xorg.0.log was worthless except for the generic error that pointed to the Ubuntu manual hardware troubleshooting section which is pretty much marshmellow-fluff for video cards.

Part of me wants to say something went wrong with the x server updating during the 9 to 10 system upgrade. Perhaps purging and reinstalling x would have fixed it but that would have taken out half his system anyway. Might as well do a reinstall at that point.

---

### Post by tjones00 on 2010-12-22
So today when I started my computer the displays on the 2nd card stopped working. I looked at my Xorg.0.log and it gave the same generic error robbie_d had.

I pulled up my kern.log and started sifting through it and behold.

```

Dec 21 02:14:34 brawndo-PC kernel: [    2.103340] input: G15 Gaming Keyboard as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1.1/6-1.1:1.0/input/input3
Dec 21 02:14:34 brawndo-PC kernel: [    2.103414] generic-usb 0003:046D:C226.0002: input,hidraw1: USB HID v1.10 Keyboard [G15 Gaming Keyboard] on usb-0000:00:1d.0-1.1/input0
Dec 21 02:14:34 brawndo-PC kernel: [    2.132312] [drm] Initialized drm 1.1.0 20060810
Dec 21 02:14:34 brawndo-PC kernel: [    2.138891] input: G15 Gaming Keyboard as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1.1/6-1.1:1.1/input/input4
Dec 21 02:14:34 brawndo-PC kernel: [    2.139008] generic-usb 0003:046D:C226.0003: input,hiddev96,hidraw2: USB HID v1.10 Device [G15 Gaming Keyboard] on usb-0000:00:1d.0-1.1/input1
Dec 21 02:14:34 brawndo-PC kernel: [    2.146555] EXT4-fs (sdb2): re-mounted. Opts: errors=remount-ro
Dec 21 02:14:34 brawndo-PC kernel: [    2.149028] lp: driver loaded but no devices found
Dec 21 02:14:34 brawndo-PC kernel: [    2.214830] usb 6-1.4: new full speed USB device using uhci_hcd and address 4
Dec 21 02:14:34 brawndo-PC kernel: [    2.268800] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 21 02:14:34 brawndo-PC kernel: [    2.268806] nouveau 0000:01:00.0: setting latency timer to 64
Dec 21 02:14:34 brawndo-PC kernel: [    2.270656] [drm] nouveau 0000:01:00.0: Detected an NV50 generation card (0x092280a2)
Dec 21 02:14:34 brawndo-PC kernel: [    2.273311] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
Dec 21 02:14:34 brawndo-PC kernel: [    2.273931] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
Dec 21 02:14:34 brawndo-PC kernel: [    2.328451] [drm] nouveau 0000:01:00.0: ... appears to be valid
Dec 21 02:14:34 brawndo-PC kernel: [    2.328455] [drm] nouveau 0000:01:00.0: BIT BIOS found
Dec 21 02:14:34 brawndo-PC kernel: [    2.328457] [drm] nouveau 0000:01:00.0: Bios version 62.92.49.00
Dec 21 02:14:34 brawndo-PC kernel: [    2.328460] [drm] nouveau 0000:01:00.0: TMDS table revision 2.0 not currently supported
Dec 21 02:14:34 brawndo-PC kernel: [    2.328463] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 4.0
Dec 21 02:14:34 brawndo-PC kernel: [    2.328465] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 02000300 00000028
Dec 21 02:14:34 brawndo-PC kernel: [    2.328467] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 01000302 00020030
Dec 21 02:14:34 brawndo-PC kernel: [    2.328469] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 04011310 00000028
Dec 21 02:14:34 brawndo-PC kernel: [    2.328471] [drm] nouveau 0000:01:00.0: Raw DCB entry 3: 02011312 00020030
Dec 21 02:14:34 brawndo-PC kernel: [    2.328473] [drm] nouveau 0000:01:00.0: Raw DCB entry 4: 010223f1 00c0c080
Dec 21 02:14:34 brawndo-PC kernel: [    2.328475] [drm] nouveau 0000:01:00.0: DCB connector table: VHER 0x40 5 16 4
Dec 21 02:14:34 brawndo-PC kernel: [    2.328478] [drm] nouveau 0000:01:00.0:   0: 0x00001030: type 0x30 idx 0 tag 0x07
Dec 21 02:14:34 brawndo-PC kernel: [    2.328480] [drm] nouveau 0000:01:00.0:   1: 0x00002130: type 0x30 idx 1 tag 0x08
Dec 21 02:14:34 brawndo-PC kernel: [    2.328482] [drm] nouveau 0000:01:00.0:   2: 0x00000210: type 0x10 idx 2 tag 0xff
Dec 21 02:14:34 brawndo-PC kernel: [    2.328484] [drm] nouveau 0000:01:00.0:   3: 0x00000211: type 0x11 idx 3 tag 0xff
Dec 21 02:14:34 brawndo-PC kernel: [    2.328486] [drm] nouveau 0000:01:00.0:   4: 0x00000213: type 0x13 idx 4 tag 0xff
Dec 21 02:14:34 brawndo-PC kernel: [    2.328493] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xC44E
Dec 21 02:14:34 brawndo-PC kernel: [    2.373945] input: G15 GamePanel LCD as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1.4/6-1.4:1.0/input/input5
Dec 21 02:14:34 brawndo-PC kernel: [    2.374038] generic-usb 0003:046D:C227.0004: input,hiddev97,hidraw3: USB HID v1.11 Keypad [G15 GamePanel LCD] on usb-0000:00:1d.0-1.4/input0
Dec 21 02:14:34 brawndo-PC kernel: [    2.381619] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xC98C
Dec 21 02:14:34 brawndo-PC kernel: [    2.397505] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xD718
Dec 21 02:14:34 brawndo-PC kernel: [    2.397512] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xD816
Dec 21 02:14:34 brawndo-PC kernel: [    2.401204]   alloc irq_desc for 22 on node -1
Dec 21 02:14:34 brawndo-PC kernel: [    2.401206]   alloc kstat_irqs on node -1
Dec 21 02:14:34 brawndo-PC kernel: [    2.401212] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Dec 21 02:14:34 brawndo-PC kernel: [    2.401243]   alloc irq_desc for 45 on node -1
Dec 21 02:14:34 brawndo-PC kernel: [    2.401245]   alloc kstat_irqs on node -1
Dec 21 02:14:34 brawndo-PC kernel: [    2.401252] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
Dec 21 02:14:34 brawndo-PC kernel: [    2.401275] HDA Intel 0000:00:1b.0: setting latency timer to 64
Dec 21 02:14:34 brawndo-PC kernel: [    2.405572] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xDA64
Dec 21 02:14:34 brawndo-PC kernel: [    2.405574] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table at offset 0xDAC9
Dec 21 02:14:34 brawndo-PC kernel: [    2.428408] [drm] nouveau 0000:01:00.0: 0xDAC9: Condition still not met after 20ms, skipping following opcodes
Dec 21 02:14:34 brawndo-PC kernel: [    2.428415] [drm] nouveau 0000:01:00.0: 0xB66C: parsing output script 0
Dec 21 02:14:34 brawndo-PC kernel: [    2.428418] [drm] nouveau 0000:01:00.0: 0xB66C: parsing output script 0
Dec 21 02:14:34 brawndo-PC kernel: [    2.428420] [drm] nouveau 0000:01:00.0: 0xA296: parsing output script 0
Dec 21 02:14:34 brawndo-PC kernel: [    2.428426] [drm] nouveau 0000:01:00.0: Detected 512MiB VRAM
Dec 21 02:14:34 brawndo-PC kernel: [    2.459985] type=1400 audit(1292926474.469:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=631 comm="apparmor_parser"
Dec 21 02:14:34 brawndo-PC kernel: [    2.460086] type=1400 audit(1292926474.473:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=631 comm="apparmor_parser"
Dec 21 02:14:34 brawndo-PC kernel: [    2.460165] type=1400 audit(1292926474.473:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=631 comm="apparmor_parser"
Dec 21 02:14:34 brawndo-PC kernel: [    2.510712] [TTM] Zone  kernel: Available graphics memory: 429822 kiB.
Dec 21 02:14:34 brawndo-PC kernel: [    2.510715] [TTM] Zone highmem: Available graphics memory: 1547810 kiB.
Dec 21 02:14:34 brawndo-PC kernel: [    2.510717] [TTM] Initializing pool allocator.
Dec 21 02:14:34 brawndo-PC kernel: [    2.525869] [drm] nouveau 0000:01:00.0: 512 MiB GART (aperture)
Dec 21 02:14:34 brawndo-PC kernel: [    2.525876] mtrr: type mismatch for c0000000,10000000 old: write-back new: write-combining
Dec 21 02:14:34 brawndo-PC kernel: [    2.526063] [drm] nouveau 0000:01:00.0: Allocating FIFO number 1
Dec 21 02:14:34 brawndo-PC kernel: [    2.529688] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 1
Dec 21 02:14:34 brawndo-PC kernel: [    2.530170] [drm] nouveau 0000:01:00.0: Detected a DAC output
Dec 21 02:14:34 brawndo-PC kernel: [    2.530172] [drm] nouveau 0000:01:00.0: Detected a TMDS output
Dec 21 02:14:34 brawndo-PC kernel: [    2.530174] [drm] nouveau 0000:01:00.0: Detected a DAC output
Dec 21 02:14:34 brawndo-PC kernel: [    2.530176] [drm] nouveau 0000:01:00.0: Detected a TMDS output
Dec 21 02:14:34 brawndo-PC kernel: [    2.530178] [drm] nouveau 0000:01:00.0: DCB encoder 1 unknown
Dec 21 02:14:34 brawndo-PC kernel: [    2.530180] [drm] nouveau 0000:01:00.0: Detected a DVI-I connector
Dec 21 02:14:34 brawndo-PC kernel: [    2.530313] [drm] nouveau 0000:01:00.0: Detected a DVI-I connector
Dec 21 02:14:34 brawndo-PC kernel: [    2.530419] [drm] nouveau 0000:01:00.0: Detected a TV connector
Dec 21 02:14:34 brawndo-PC kernel: [    2.530448] [drm] nouveau 0000:01:00.0:   no encoders, ignoring
Dec 21 02:14:34 brawndo-PC kernel: [    2.571484] hda_codec: ALC888: BIOS auto-probing.
Dec 21 02:14:34 brawndo-PC kernel: [    2.870587] [drm] nouveau 0000:01:00.0: allocated 1920x1200 fb: 0x40250000, bo f4926800
Dec 21 02:14:34 brawndo-PC kernel: [    2.872596] [drm] nouveau 0000:01:00.0: 0xB670: parsing output script 1
Dec 21 02:14:34 brawndo-PC kernel: [    2.872608] [drm] nouveau 0000:01:00.0: 0xB671: parsing output script 2
Dec 21 02:14:34 brawndo-PC kernel: [    2.872625] [drm] nouveau 0000:01:00.0: 0xB4B7: parsing clock script 0
Dec 21 02:14:34 brawndo-PC kernel: [    2.873480] Console: switching to colour frame buffer device 160x64
Dec 21 02:14:34 brawndo-PC kernel: [    2.875120] fb0: nouveaufb frame buffer device
Dec 21 02:14:34 brawndo-PC kernel: [    2.875121] drm: registered panic notifier
Dec 21 02:14:34 brawndo-PC kernel: [    2.875124] Slow work thread pool: Starting up
Dec 21 02:14:34 brawndo-PC kernel: [    2.875179] Slow work thread pool: Ready
Dec 21 02:14:34 brawndo-PC kernel: [    2.875185] [drm] Initialized nouveau 0.0.16 20090420 for 0000:01:00.0 on minor 0
Dec 21 02:14:34 brawndo-PC kernel: [    2.875206] nouveau 0000:02:00.0: enabling device (0000 -> 0003)
Dec 21 02:14:34 brawndo-PC kernel: [    2.875212] nouveau 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 21 02:14:34 brawndo-PC kernel: [    2.875217] nouveau 0000:02:00.0: setting latency timer to 64
Dec 21 02:14:34 brawndo-PC kernel: [    2.877279] [drm] nouveau 0000:02:00.0: Detected an NV50 generation card (0x092280a2)
Dec 21 02:14:34 brawndo-PC kernel: [    2.879759] vmap allocation for size 33558528 failed: use vmalloc=<size> to increase size.
Dec 21 02:14:34 brawndo-PC kernel: [    2.881020] [drm] nouveau 0000:02:00.0: Failed to PRAMIN BAR
Dec 21 02:14:34 brawndo-PC kernel: [    2.881267] nouveau 0000:02:00.0: PCI INT A disabled
Dec 21 02:14:34 brawndo-PC kernel: [    2.881273] nouveau: probe of 0000:02:00.0 failed with error -12
Dec 21 02:14:34 brawndo-PC kernel: [    2.892434] [drm] nouveau 0000:01:00.0: 0x120F: parsing clock script 0
Dec 21 02:14:35 brawndo-PC kernel: [    3.077050] type=1400 audit(1292926475.089:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1021 comm="apparmor_parser"
Dec 21 02:14:35 brawndo-PC kernel: [    3.077594] type=1400 audit(1292926475.089:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1021 comm="apparmor_parser"
Dec 21 02:14:35 brawndo-PC kernel: [    3.077890] type=1400 audit(1292926475.089:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1021 comm="apparmor_parser"
Dec 21 02:14:35 brawndo-PC kernel: [    3.153527] ppdev: user-space parallel port driver
Dec 21 02:14:35 brawndo-PC kernel: [    3.216886] type=1400 audit(1292926475.229:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1025 comm="apparmor_parser"
Dec 21 02:14:35 brawndo-PC kernel: [    3.482356] type=1400 audit(1292926475.493:9): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1020 comm="apparmor_parser"
Dec 21 02:14:35 brawndo-PC kernel: [    3.889091] r8169 0000:04:00.0: eth0: link down
Dec 21 02:14:35 brawndo-PC kernel: [    3.889098] r8169 0000:04:00.0: eth0: link down
Dec 21 02:14:35 brawndo-PC kernel: [    3.889251] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 21 02:14:36 brawndo-PC kernel: [    4.415909] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Dec 21 02:14:36 brawndo-PC kernel: [    4.415912] vgaarb: transferring owner from PCI:0000:01:00.0 to PCI:0000:02:00.0
Dec 21 02:14:36 brawndo-PC kernel: [    4.477053] r8169 0000:04:00.0: eth0: link up
Dec 21 02:14:36 brawndo-PC kernel: [    4.477197] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Dec 21 02:14:37 brawndo-PC kernel: [    5.760280] EXT4-fs (sdb2): re-mounted. Opts: errors=remount-ro,commit=0
Dec 21 02:14:37 brawndo-PC kernel: [    5.763184] EXT4-fs (sdb1): re-mounted. Opts: commit=0
Dec 21 02:14:38 brawndo-PC kernel: [    6.680771] audit_printk_skb: 6 callbacks suppressed
Dec 21 02:14:38 brawndo-PC kernel: [    6.680774] type=1400 audit(1292926478.693:12): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1022 comm="apparmor_parser"
Dec 21 02:14:38 brawndo-PC kernel: [    6.681773] type=1400 audit(1292926478.693:13): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=1022 comm="apparmor_parser"
Dec 21 02:14:38 brawndo-PC kernel: [    6.682487] type=1400 audit(1292926478.693:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=1022 comm="apparmor_parser"
Dec 21 02:14:47 brawndo-PC kernel: [   15.472005] eth0: no IPv6 routers present
Dec 21 02:17:52 brawndo-PC kernel: [  200.158467] nvidia: module license 'NVIDIA' taints kernel.
Dec 21 02:17:52 brawndo-PC kernel: [  200.158470] Disabling lock debugging due to kernel taint
Dec 21 02:17:53 brawndo-PC kernel: [  201.013122] nvidia 0000:02:00.0: enabling device (0000 -> 0003)
Dec 21 02:17:53 brawndo-PC kernel: [  201.013130] nvidia 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 21 02:17:53 brawndo-PC kernel: [  201.013139] nvidia 0000:02:00.0: setting latency timer to 64
Dec 21 02:17:53 brawndo-PC kernel: [  201.013146] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=none
Dec 21 02:17:53 brawndo-PC kernel: [  201.013269] NVRM: The NVIDIA probe routine was not called for 1 device(s).
Dec 21 02:17:53 brawndo-PC kernel: [  201.013271] NVRM: This can occur when a driver such as nouveau, rivafb,
Dec 21 02:17:53 brawndo-PC kernel: [  201.013273] NVRM: nvidiafb, or rivatv was loaded and obtained ownership of
Dec 21 02:17:53 brawndo-PC kernel: [  201.013274] NVRM: the NVIDIA device(s).
Dec 21 02:17:53 brawndo-PC kernel: [  201.013277] NVRM: Try unloading the conflicting kernel module (and/or
Dec 21 02:17:53 brawndo-PC kernel: [  201.013278] NVRM: reconfigure your kernel without the conflicting
Dec 21 02:17:53 brawndo-PC kernel: [  201.013279] NVRM: driver(s)), then try loading the NVIDIA kernel module
Dec 21 02:17:53 brawndo-PC kernel: [  201.013280] NVRM: again.
Dec 21 02:17:53 brawndo-PC kernel: [  201.013283] NVRM: loading NVIDIA UNIX x86 Kernel Module  260.19.06  Mon Sep 13 06:35:06 PDT 2010
Dec 21 02:18:14 brawndo-PC kernel: Kernel logging (proc) stopped.
```Figured it out it has nothing to do with nouveau still hanging around even though it shouldn't be there. The issue was vmalloc when using 2 nvidia cards and the current 10.10 32b kernel. I guess this kernel and nvidia driver requires more vm when using 2 nvidia cards.

[http://www.mythtv.org/wiki/Common_Problem:_vmalloc_too_small](http://www.mythtv.org/wiki/Common_Problem:_vmalloc_too_small)

For Ubuntu 10.10 edit the following.

sudo gedit /etc/default/grub

Find the line GRUB_CMDLINE_LINUX= and start with 192M.

GRUB_CMDLINE_LINUX="vmalloc=192M"

save the file and update grub

sudo update-grub2

reboot and check nvidia-settings to make sure it sees both of your cards. Or look at kern.log for the vmalloc error.

If 192M is not enough keep adding more 64M at a time until there is enough to load both cards.

---

### Post by robbie d on 2011-03-02
I can't believe I didn't see the reply. Both screens didn't always start, so I will make this change and test it, now that I have a third monitor things will become interesting.
I used separate X-screens for the two monitors I now have running off one card, as none of the instant messaging programs worked with the GUI that is needed for xinerama (forgive my lack of techspeak, i'm still a peng-noob).

---

### Post by robbie d on 2011-03-17
Follow up to previous message. After repeated cold boots, all three screens work every time. Having some issues with my mouse in urban terror, but one issue at a time.

---

