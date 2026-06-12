---
title: "Setup screen data entry in MythTV"
date: 2009-08-18
forum: Mythbuntu
---

### Post by zapstrap on 2009-08-18
I'm running Mythbuntu 9.04 on a 3GHz P4 box. When in the frontend and backend setup menus, many fields that need to be filled in are unreadable in some circumstances. Paging through the general setup menu on the front end, as I look at each screen I can read all text, even in editable fields. If the field takes numbers, like for setting font size for example, I can edit these no problem. OTOH, if the field takes text, like for setting the shutdown command, I can read that it says 'halt', but if I put the focus on the field to edit it, it goes black. The text is there, and if I highlight it, I can see it (white text, black background) but otherwise it's black text, black background. If I want, for example, to change the shutdown command from 'halt' to 'shutdown -h now' I have to select the field, then select the text so I can see it, delete it, then type in the new command without being able to see if it's being entered. After I'm done, I hold the shift key down and press the Home button to highlight what I've typed just to make sure there are no typos.
 
1. Why does editing work for numbers, but not text?
2. How do I fix this so I can read it?
 
I'm comfortable editing files in a shell, so if it's just a simple config file edit, please point me in the right direction.

---

### Post by zapstrap on 2009-09-10
Anyone?

---

### Post by williammanda on 2009-09-10
Post your xorg.conf and Xorg.0.log files.
Thanks

---

### Post by zapstrap on 2009-09-11
Here's the guts of xorg.conf:

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Plasma Screen Lo-Res" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
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
    Identifier     "Monitor1"
    VendorName     "Panasonic"
    ModelName      "Panasonic TH-42PA20U"
    Option         "ExactModeTimingsDVI" "TRUE"
    HorizSync       15.0 - 34.0
    VertRefresh     59.0 - 61.0
    Modeline        "720x480" 27.00 664 715 764 858 436 461 467 525 -hsync -vsync
    #Modeline        "720x480" 27.00 720 736 798 858 480 489 495 525 -hsync -vsync
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "Panasonic"
    ModelName      "Panasonic TH-42PA20U"
    Option         "ExactModeTimingsDVI" "TRUE"
    HorizSync       15.0 - 34.0
    VertRefresh     59.0 - 61.0
    Modeline        "1920x1080" 74.25 1920 2008 2052 2200 1080 1084 1094 1124 +hsync +vsync Interlace
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "UseEvents" "1"
    Option         "DPI" "100x100"
    Option         "NoLogo" "1"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200"
    Option         "NoLogo" "FALSE"
    Option         "UseEDID" "FALSE"
EndSection

Section "Screen"
    Identifier     "Plasma Screen Lo-Res"
    Device         "Device0"
    #Device         "Configured Video Device"
    Monitor        "Monitor1"
    Subsection     "Display"
        Depth      24
        Modes      "720x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Plasma Screen Hi-Res"
    Device         "Device0"
    Monitor        "Monitor2"
    Subsection     "Display"
        Depth      24
        Modes      "1920x1080"
    EndSubSection
EndSection

```

I'm using the lo-res mode, as the TV is 720x480, not high-def.  ...and yes I've been fiddling around with the front/back porch in the modeline.  The TV overscans leaving too much of the desktop off-screen. Expanding the porches fixes it with the unwanted side-effect of buggering the aspect ratio up quite badly.  I've worked around this in vlc and mythtv, but things like flash in a browser do not look right when displayed fullscreen.  Anyway, I digress.

Here's Xorg.0.log:

```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux sigsauer 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep 11 10:46:49 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Plasma Screen Lo-Res" (0)
(**) |   |-->Monitor "Monitor1"
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
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation NV44A [GeForce 6200] rev 161, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf9000000/16777216, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
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
    compiled for 1.6.0, module version = 1.0.0
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
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.44  Mon Mar 23 15:29:02 PST 2009
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  180.44  Mon Mar 23 15:05:32 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "FALSE"
(**) NVIDIA(0): Option "UseEDID" "FALSE"
(**) NVIDIA(0): Option "ExactModeTimingsDVI" "TRUE"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Ignoring EDIDs
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(GPU-0): Not probing EDID on DFP-0.
(II) NVIDIA(0): NVIDIA GPU GeForce 6200 (NV44) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.44.a2.10.40
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6200 at PCI:1:0:0:
(--) NVIDIA(0):     DFP-0
(--) NVIDIA(0): DFP-0: 155.0 MHz maximum pixel clock
(--) NVIDIA(0): DFP-0: Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "720x480"
(II) NVIDIA(0): Virtual screen size determined to be 664 x 436
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Setting mode "720x480"
(II) NVIDIA(0): Built-in logo is bigger than the screen.
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
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
(II) config/hal: Adding input device HOLTEK Wireless 2.4GHz TouchPad Keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.1.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) HOLTEK Wireless 2.4GHz TouchPad Keyboard: always reports core events
(**) HOLTEK Wireless 2.4GHz TouchPad Keyboard: Device: "/dev/input/event4"
(II) HOLTEK Wireless 2.4GHz TouchPad Keyboard: Found 4 mouse buttons
(II) HOLTEK Wireless 2.4GHz TouchPad Keyboard: Found x and y relative axes
(II) HOLTEK Wireless 2.4GHz TouchPad Keyboard: Found keys
(II) HOLTEK Wireless 2.4GHz TouchPad Keyboard: Configuring as mouse
(II) HOLTEK Wireless 2.4GHz TouchPad Keyboard: Configuring as keyboard
(**) HOLTEK Wireless 2.4GHz TouchPad Keyboard: YAxisMapping: buttons 4 and 5
(**) HOLTEK Wireless 2.4GHz TouchPad Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "HOLTEK Wireless 2.4GHz TouchPad Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) HOLTEK Wireless 2.4GHz TouchPad Keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) HOLTEK Wireless 2.4GHz TouchPad Keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "ca"
(**) HOLTEK Wireless 2.4GHz TouchPad Keyboard: xkb_layout: "ca"
(**) Option "xkb_variant" "eng"
(**) HOLTEK Wireless 2.4GHz TouchPad Keyboard: xkb_variant: "eng"
(**) HOLTEK Wireless 2.4GHz TouchPad Keyboard: (accel) keeping acceleration scheme 1
(**) HOLTEK Wireless 2.4GHz TouchPad Keyboard: (accel) filter chain progression: 2.00
(**) HOLTEK Wireless 2.4GHz TouchPad Keyboard: (accel) filter stage 0: 20.00 ms
(**) HOLTEK Wireless 2.4GHz TouchPad Keyboard: (accel) set acceleration profile 0
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
(II) config/hal: Adding input device HOLTEK Wireless 2.4GHz TouchPad Keyboard
(**) HOLTEK Wireless 2.4GHz TouchPad Keyboard: always reports core events
(**) HOLTEK Wireless 2.4GHz TouchPad Keyboard: Device: "/dev/input/event3"
(II) HOLTEK Wireless 2.4GHz TouchPad Keyboard: Found keys
(II) HOLTEK Wireless 2.4GHz TouchPad Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "HOLTEK Wireless 2.4GHz TouchPad Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) HOLTEK Wireless 2.4GHz TouchPad Keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) HOLTEK Wireless 2.4GHz TouchPad Keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "ca"
(**) HOLTEK Wireless 2.4GHz TouchPad Keyboard: xkb_layout: "ca"
(**) Option "xkb_variant" "eng"
(**) HOLTEK Wireless 2.4GHz TouchPad Keyboard: xkb_variant: "eng"

```

---

### Post by johnvarenda on 2009-12-10
hi....
I am new to data entry.
Can anyone explain about Setup screen data entry in MythTV..
Thanks....
..................

[data entry india]("http://www.e-datapro.net")

---

