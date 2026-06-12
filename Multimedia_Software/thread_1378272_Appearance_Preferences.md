---
title: "Appearance Preferences"
date: 2010-01-11
forum: Multimedia Software
---

### Post by qkzoo on 2010-01-11
How come if I bring up the Appearance Preferences dialogue, and select "Normal" or "Extra" it says "Desktop effects could not be enabled."?  My only guess is that it has something to do with the video drivers or something.  I'm new to Linux/Ubuntu, but I saw someone else in another thread post a question and someone asked them for the results of typing "lspci" into the console, so here is what it gave me regarding video before anyone asks me ;)

```

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

```

I have this same issue on another PC I also installed Ubuntu on, but I'll solve this one before tackling that one.

---

### Post by Yellow Pasque on 2010-01-11
Post/pastebin your /var/log/Xorg.0.log

---

### Post by qkzoo on 2010-01-12
Ok, bunch of info here, hope it has what you're looking for!

```


X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux andrew-desktop1 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic root=UUID=03d3f746-7994-46f4-861c-1a838ab8ead5 ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jan 12 09:33:45 2010
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:2562:1028:0160 Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device rev 1, Mem @ 0xe8000000/134217728, 0xfeb80000/524288
(==) Using default built-in configuration (39 lines)
(==) --- Start of built-in configuration ---
    Section "Device"
        Identifier    "Builtin Default intel Device 0"
        Driver    "intel"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default intel Screen 0"
        Device    "Builtin Default intel Device 0"
    EndSection
    Section "Device"
        Identifier    "Builtin Default i810 Device 0"
        Driver    "i810"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default i810 Screen 0"
        Device    "Builtin Default i810 Device 0"
    EndSection
    Section "Device"
        Identifier    "Builtin Default vesa Device 0"
        Driver    "vesa"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default vesa Screen 0"
        Device    "Builtin Default vesa Device 0"
    EndSection
    Section "Device"
        Identifier    "Builtin Default fbdev Device 0"
        Driver    "fbdev"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default fbdev Screen 0"
        Device    "Builtin Default fbdev Device 0"
    EndSection
    Section "ServerLayout"
        Identifier    "Builtin Default Layout"
        Screen    "Builtin Default intel Screen 0"
        Screen    "Builtin Default i810 Screen 0"
        Screen    "Builtin Default vesa Screen 0"
        Screen    "Builtin Default fbdev Screen 0"
    EndSection
(==) --- End of built-in configuration ---
(==) ServerLayout "Builtin Default Layout"
(**) |-->Screen "Builtin Default intel Screen 0" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default intel Device 0"
(==) No monitor specified for screen "Builtin Default intel Screen 0".
    Using a default monitor configuration.
(**) |-->Screen "Builtin Default i810 Screen 0" (1)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default i810 Device 0"
(==) No monitor specified for screen "Builtin Default i810 Screen 0".
    Using a default monitor configuration.
(**) |-->Screen "Builtin Default vesa Screen 0" (2)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default vesa Device 0"
(==) No monitor specified for screen "Builtin Default vesa Screen 0".
    Using a default monitor configuration.
(**) |-->Screen "Builtin Default fbdev Screen 0" (3)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default fbdev Device 0"
(==) No monitor specified for screen "Builtin Default fbdev Screen 0".
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
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
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
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
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
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.9.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "i810"
(WW) Warning, couldn't open module i810
(II) UnloadModule: "i810"
(EE) Failed to load module "i810" (module does not exist, 0)
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.6.3, module version = 2.2.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 0.4.0
    ABI class: X.Org Video Driver, version 5.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 0.0.2
    ABI class: X.Org Video Driver, version 5.0
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): Creating default Display subsection in Screen section
    "Builtin Default intel Screen 0" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 845G
(--) intel(0): Chipset: "845G"
(II) intel(0): Output VGA1 has no monitor section
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: DEL  Model: d005  Serial#: 808744038
(II) intel(0): Year: 2004  Week: 10
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) intel(0): Sync:  Separate
(II) intel(0): Max Image Size [cm]: horiz.: 32  vert.: 24
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): Default color space is primary color space
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.631 redY: 0.328   greenX: 0.275 greenY: 0.600
(II) intel(0): blueX: 0.143 blueY: 0.057   whiteX: 0.283 whiteY: 0.298
(II) intel(0): Supported established timings:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@75Hz
(II) intel(0): 800x600@75Hz
(II) intel(0): 1024x768@75Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) intel(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) intel(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) intel(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 78.8 MHz   Image Size:  310 x 230 mm
(II) intel(0): h_active: 1024  h_sync: 1040  h_sync_end 1136 h_blank_end 1312 h_border: 0
(II) intel(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 800 v_border: 0
(II) intel(0): Serial No: 6418043504TF
(II) intel(0): Monitor name: DELL E773c
(II) intel(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 70 kHz, PixClock max 110 MHz
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0010ac05d066743430
(II) intel(0):     0a0e0103682018782e8aa9a154469924
(II) intel(0):     0e484ca442003159455961598180714f
(II) intel(0):     010101010101c31e0020410020301060
(II) intel(0):     130036e61000001e000000ff00363431
(II) intel(0):     3830343335303454460a000000fc0044
(II) intel(0):     454c4c2045373733630a2020000000fd
(II) intel(0):     0032a01e460b000a202020202020009c
(II) intel(0): EDID vendor "DEL", prod id 53253
(II) intel(0): Using EDID range info for horizontal sync
(II) intel(0): Using EDID range info for vertical refresh
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Output VGA1 connected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output VGA1 using initial mode 1024x768
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(**) intel(0): Display dimensions: (320, 240) mm
(**) intel(0): DPI set to (81, 81)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux//libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) intel(0): [DRI2] Setup complete
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): VideoRam: 131072 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): No memory allocations
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder disabled
(WW) intel(0): Disabling Xv because no adaptors could be initialized.
(II) intel(0): direct rendering: DRI2 Enabled
(--) RandR disabled
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
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) intel(0): Setting screen physical size to 310 x 230
(EE) config/hal: couldn't initialise context: unknown error (null)
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.2.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
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
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event4"
(II) Logitech Optical USB Mouse: Found 3 mouse buttons
(II) Logitech Optical USB Mouse: Found x and y relative axes
(II) Logitech Optical USB Mouse: Found scroll wheel(s)
(II) Logitech Optical USB Mouse: Configuring as mouse
(**) Logitech Optical USB Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
(**) Logitech Optical USB Mouse: (accel) keeping acceleration scheme 1
(**) Logitech Optical USB Mouse: (accel) filter chain progression: 2.00
(**) Logitech Optical USB Mouse: (accel) filter stage 0: 20.00 ms
(**) Logitech Optical USB Mouse: (accel) set acceleration profile 0
(II) Logitech Optical USB Mouse: initialized for relative axes.
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: DEL  Model: d005  Serial#: 808744038
(II) intel(0): Year: 2004  Week: 10
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) intel(0): Sync:  Separate
(II) intel(0): Max Image Size [cm]: horiz.: 32  vert.: 24
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): Default color space is primary color space
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.631 redY: 0.328   greenX: 0.275 greenY: 0.600
(II) intel(0): blueX: 0.143 blueY: 0.057   whiteX: 0.283 whiteY: 0.298
(II) intel(0): Supported established timings:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@75Hz
(II) intel(0): 800x600@75Hz
(II) intel(0): 1024x768@75Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) intel(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) intel(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) intel(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 78.8 MHz   Image Size:  310 x 230 mm
(II) intel(0): h_active: 1024  h_sync: 1040  h_sync_end 1136 h_blank_end 1312 h_border: 0
(II) intel(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 800 v_border: 0
(II) intel(0): Serial No: 6418043504TF
(II) intel(0): Monitor name: DELL E773c
(II) intel(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 70 kHz, PixClock max 110 MHz
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0010ac05d066743430
(II) intel(0):     0a0e0103682018782e8aa9a154469924
(II) intel(0):     0e484ca442003159455961598180714f
(II) intel(0):     010101010101c31e0020410020301060
(II) intel(0):     130036e61000001e000000ff00363431
(II) intel(0):     3830343335303454460a000000fc0044
(II) intel(0):     454c4c2045373733630a2020000000fd
(II) intel(0):     0032a01e460b000a202020202020009c
(II) intel(0): EDID vendor "DEL", prod id 53253
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: DEL  Model: d005  Serial#: 808744038
(II) intel(0): Year: 2004  Week: 10
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) intel(0): Sync:  Separate
(II) intel(0): Max Image Size [cm]: horiz.: 32  vert.: 24
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): Default color space is primary color space
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.631 redY: 0.328   greenX: 0.275 greenY: 0.600
(II) intel(0): blueX: 0.143 blueY: 0.057   whiteX: 0.283 whiteY: 0.298
(II) intel(0): Supported established timings:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@75Hz
(II) intel(0): 800x600@75Hz
(II) intel(0): 1024x768@75Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) intel(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) intel(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) intel(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 78.8 MHz   Image Size:  310 x 230 mm
(II) intel(0): h_active: 1024  h_sync: 1040  h_sync_end 1136 h_blank_end 1312 h_border: 0
(II) intel(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 800 v_border: 0
(II) intel(0): Serial No: 6418043504TF
(II) intel(0): Monitor name: DELL E773c
(II) intel(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 70 kHz, PixClock max 110 MHz
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0010ac05d066743430
(II) intel(0):     0a0e0103682018782e8aa9a154469924
(II) intel(0):     0e484ca442003159455961598180714f
(II) intel(0):     010101010101c31e0020410020301060
(II) intel(0):     130036e61000001e000000ff00363431
(II) intel(0):     3830343335303454460a000000fc0044
(II) intel(0):     454c4c2045373733630a2020000000fd
(II) intel(0):     0032a01e460b000a202020202020009c
(II) intel(0): EDID vendor "DEL", prod id 53253
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: DEL  Model: d005  Serial#: 808744038
(II) intel(0): Year: 2004  Week: 10
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) intel(0): Sync:  Separate
(II) intel(0): Max Image Size [cm]: horiz.: 32  vert.: 24
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): Default color space is primary color space
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.631 redY: 0.328   greenX: 0.275 greenY: 0.600
(II) intel(0): blueX: 0.143 blueY: 0.057   whiteX: 0.283 whiteY: 0.298
(II) intel(0): Supported established timings:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@75Hz
(II) intel(0): 800x600@75Hz
(II) intel(0): 1024x768@75Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) intel(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) intel(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) intel(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 78.8 MHz   Image Size:  310 x 230 mm
(II) intel(0): h_active: 1024  h_sync: 1040  h_sync_end 1136 h_blank_end 1312 h_border: 0
(II) intel(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 800 v_border: 0
(II) intel(0): Serial No: 6418043504TF
(II) intel(0): Monitor name: DELL E773c
(II) intel(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 70 kHz, PixClock max 110 MHz
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0010ac05d066743430
(II) intel(0):     0a0e0103682018782e8aa9a154469924
(II) intel(0):     0e484ca442003159455961598180714f
(II) intel(0):     010101010101c31e0020410020301060
(II) intel(0):     130036e61000001e000000ff00363431
(II) intel(0):     3830343335303454460a000000fc0044
(II) intel(0):     454c4c2045373733630a2020000000fd
(II) intel(0):     0032a01e460b000a202020202020009c
(II) intel(0): EDID vendor "DEL", prod id 53253
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: DEL  Model: d005  Serial#: 808744038
(II) intel(0): Year: 2004  Week: 10
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) intel(0): Sync:  Separate
(II) intel(0): Max Image Size [cm]: horiz.: 32  vert.: 24
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): Default color space is primary color space
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.631 redY: 0.328   greenX: 0.275 greenY: 0.600
(II) intel(0): blueX: 0.143 blueY: 0.057   whiteX: 0.283 whiteY: 0.298
(II) intel(0): Supported established timings:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@75Hz
(II) intel(0): 800x600@75Hz
(II) intel(0): 1024x768@75Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) intel(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) intel(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) intel(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 78.8 MHz   Image Size:  310 x 230 mm
(II) intel(0): h_active: 1024  h_sync: 1040  h_sync_end 1136 h_blank_end 1312 h_border: 0
(II) intel(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 800 v_border: 0
(II) intel(0): Serial No: 6418043504TF
(II) intel(0): Monitor name: DELL E773c
(II) intel(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 70 kHz, PixClock max 110 MHz
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0010ac05d066743430
(II) intel(0):     0a0e0103682018782e8aa9a154469924
(II) intel(0):     0e484ca442003159455961598180714f
(II) intel(0):     010101010101c31e0020410020301060
(II) intel(0):     130036e61000001e000000ff00363431
(II) intel(0):     3830343335303454460a000000fc0044
(II) intel(0):     454c4c2045373733630a2020000000fd
(II) intel(0):     0032a01e460b000a202020202020009c
(II) intel(0): EDID vendor "DEL", prod id 53253
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: DEL  Model: d005  Serial#: 808744038
(II) intel(0): Year: 2004  Week: 10
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) intel(0): Sync:  Separate
(II) intel(0): Max Image Size [cm]: horiz.: 32  vert.: 24
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): Default color space is primary color space
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.631 redY: 0.328   greenX: 0.275 greenY: 0.600
(II) intel(0): blueX: 0.143 blueY: 0.057   whiteX: 0.283 whiteY: 0.298
(II) intel(0): Supported established timings:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@75Hz
(II) intel(0): 800x600@75Hz
(II) intel(0): 1024x768@75Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) intel(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) intel(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) intel(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 78.8 MHz   Image Size:  310 x 230 mm
(II) intel(0): h_active: 1024  h_sync: 1040  h_sync_end 1136 h_blank_end 1312 h_border: 0
(II) intel(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 800 v_border: 0
(II) intel(0): Serial No: 6418043504TF
(II) intel(0): Monitor name: DELL E773c
(II) intel(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 70 kHz, PixClock max 110 MHz
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0010ac05d066743430
(II) intel(0):     0a0e0103682018782e8aa9a154469924
(II) intel(0):     0e484ca442003159455961598180714f
(II) intel(0):     010101010101c31e0020410020301060
(II) intel(0):     130036e61000001e000000ff00363431
(II) intel(0):     3830343335303454460a000000fc0044
(II) intel(0):     454c4c2045373733630a2020000000fd
(II) intel(0):     0032a01e460b000a202020202020009c
(II) intel(0): EDID vendor "DEL", prod id 53253
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: DEL  Model: d005  Serial#: 808744038
(II) intel(0): Year: 2004  Week: 10
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) intel(0): Sync:  Separate
(II) intel(0): Max Image Size [cm]: horiz.: 32  vert.: 24
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): Default color space is primary color space
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.631 redY: 0.328   greenX: 0.275 greenY: 0.600
(II) intel(0): blueX: 0.143 blueY: 0.057   whiteX: 0.283 whiteY: 0.298
(II) intel(0): Supported established timings:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@75Hz
(II) intel(0): 800x600@75Hz
(II) intel(0): 1024x768@75Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) intel(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) intel(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) intel(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 78.8 MHz   Image Size:  310 x 230 mm
(II) intel(0): h_active: 1024  h_sync: 1040  h_sync_end 1136 h_blank_end 1312 h_border: 0
(II) intel(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 800 v_border: 0
(II) intel(0): Serial No: 6418043504TF
(II) intel(0): Monitor name: DELL E773c
(II) intel(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 70 kHz, PixClock max 110 MHz
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0010ac05d066743430
(II) intel(0):     0a0e0103682018782e8aa9a154469924
(II) intel(0):     0e484ca442003159455961598180714f
(II) intel(0):     010101010101c31e0020410020301060
(II) intel(0):     130036e61000001e000000ff00363431
(II) intel(0):     3830343335303454460a000000fc0044
(II) intel(0):     454c4c2045373733630a2020000000fd
(II) intel(0):     0032a01e460b000a202020202020009c
(II) intel(0): EDID vendor "DEL", prod id 53253
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) Open ACPI successful (/var/run/acpid.socket)
(II) AIGLX: Resuming AIGLX clients after VT switch
(II) intel(0): No memory allocations
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) Logitech Optical USB Mouse: Device reopened after 1 attempts.

```

---

