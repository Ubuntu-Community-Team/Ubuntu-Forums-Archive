---
title: "Help getting HDMI to work"
date: 2010-11-30
forum: Multimedia Software
---

### Post by Alessandro74 on 2010-11-30
Hi Folks,
Having no end of trouble getting HDMI to work on my myth frontend setup.
The PC running Mythbuntu 9.10 is an Acer Revo R3610, and my TV is a
Polaroid TLU-01911CU (appears as ProView TLU-01911CU in Nvidia XServer
Config. I am using the NIVIDA drivers on mythbuntu for the HD playback,
however it won't display at 1440x900 as it should !
Seems the TV is giving out nonsense info about the resolutions it
supports! Keeps defaulting back to 640 x 480

My logs:

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
Current Operating System: Linux myth-frontend 2.6.32-25-generic
#45-Ubuntu SMP Sat Oct 16 19:48:22 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-25-generic
root=UUID=50f6570e-9b7f-401d-b302-5519b7ec28da ro quiet splash
Build Date: 10 November 2010  11:25:26AM
xorg-server 2:1.7.6-2ubuntu7.4 (For technical support please see
[http://www.ubuntu.com/support](http://www.ubuntu.com/support))
Current version of pixman: 0.16.4
       Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
       to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
       (++) from command line, (!!) notice, (II) informational,
       (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov 29 22:21:16 2010
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
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or
'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x81f1b20
(II) Module ABI versions:
       X.Org ANSI C Emulation: 0.4
       X.Org Video Driver: 6.0
       X.Org XInput driver : 7.0
       X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI: (0:0:3:5) 10de:0aa3:1025:0222 nVidia Corporation MCP79
Co-processor rev 177, Mem @ 0xfae80000/524288
(--) PCI:*(0:3:0:0) 10de:087d:1025:0222 nVidia Corporation ION VGA rev
177, Mem @ 0xfb000000/16777216, 0xe0000000/268435456,
0xf8000000/33554432, I/O @ 0x0000ec00/128, BIOS @ 0x????????/131072
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
(**) NVIDIA(0): Option "UseEDID" "False"
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "DPI" "96 x 96"
(**) Nov 29 22:21:16 NVIDIA(0): Enabling RENDER acceleration
(**) Nov 29 22:21:16 NVIDIA(0): Ignoring EDIDs
(II) Nov 29 22:21:16 NVIDIA(0): Support for GLX with the Damage and
Composite X extensions is
(II) Nov 29 22:21:16 NVIDIA(0):     enabled.
(II) Nov 29 22:21:17 NVIDIA(GPU-0): Not probing EDID on DFP-0.
(II) Nov 29 22:21:17 NVIDIA(0): NVIDIA GPU ION (C79) at PCI:3:0:0 (GPU-0)
(--) Nov 29 22:21:17 NVIDIA(0): Memory: 524288 kBytes
(--) Nov 29 22:21:17 NVIDIA(0): VideoBIOS: 62.79.6c.00.01
(--) Nov 29 22:21:17 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Nov 29 22:21:17 NVIDIA(0): Connected display device(s) on ION at PCI:3:0:0:
(--) Nov 29 22:21:17 NVIDIA(0):     DFP-0
(--) Nov 29 22:21:17 NVIDIA(0): DFP-0: 165.0 MHz maximum pixel clock
(--) Nov 29 22:21:17 NVIDIA(0): DFP-0: Internal Single Link TMDS
(II) Nov 29 22:21:17 NVIDIA(0): Assigned Display Device: DFP-0
(WW) Nov 29 22:21:17 NVIDIA(0): No valid modes for "1440x900"; removing.
(WW) Nov 29 22:21:17 NVIDIA(0):
(WW) Nov 29 22:21:17 NVIDIA(0): Unable to validate any modes; falling
back to the default mode
(WW) Nov 29 22:21:17 NVIDIA(0):     "nvidia-auto-select".
(WW) Nov 29 22:21:17 NVIDIA(0):
(II) Nov 29 22:21:17 NVIDIA(0): Validated modes:
(II) Nov 29 22:21:17 NVIDIA(0):     "nvidia-auto-select"
(II) Nov 29 22:21:17 NVIDIA(0): Virtual screen size determined to be 640 x 480
(**) Nov 29 22:21:17 NVIDIA(0): DPI set to (96, 96); computed from
"DPI" X config option
(==) Nov 29 22:21:17 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) Nov 29 22:21:17 NVIDIA: Using 768.00 MB of virtual memory for
indirect memory access.
(II) Nov 29 22:21:17 NVIDIA(0): Initialized GPU GART.
(II) Nov 29 22:21:17 NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Nov 29 22:21:17 NVIDIA(0): Built-in logo is bigger than the screen.
(II) Loading extension NV-GLX
(II) Nov 29 22:21:17 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Nov 29 22:21:17 NVIDIA(0): Initialized X Rendering Acceleration
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
(II) XKB: reuse xkmfile
/var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
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
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) XKB: reuse xkmfile
/var/lib/xkb/server-C1F82522E3F958F13C2D6D2C62551E135092F235.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device Logitech USB Optical Mouse
(/dev/input/event3)
(**) Logitech USB Optical Mouse: Applying InputClass "evdev pointer catchall"
(**) Logitech USB Optical Mouse: always reports core events
(**) Logitech USB Optical Mouse: Device: "/dev/input/event3"
(II) Logitech USB Optical Mouse: Found 12 mouse buttons
(II) Logitech USB Optical Mouse: Found scroll wheel(s)
(II) Logitech USB Optical Mouse: Found relative axes
(II) Logitech USB Optical Mouse: Found x and y relative axes
(II) Logitech USB Optical Mouse: Configuring as mouse
(**) Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB Optical Mouse: EmulateWheelButton: 4,
EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Optical Mouse"
(type: MOUSE)
(II) Logitech USB Optical Mouse: initialized for relative axes.
(II) config/udev: Adding input device Logitech USB Optical Mouse
(/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Chicony USB Keyboard (/dev/input/event4)
(**) Chicony USB Keyboard: Applying InputClass "evdev keyboard catchall"
(**) Chicony USB Keyboard: always reports core events
(**) Chicony USB Keyboard: Device: "/dev/input/event4"
(II) Chicony USB Keyboard: Found keys
(II) Chicony USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Chicony USB Keyboard"
(type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device Chicony USB Keyboard (/dev/input/event5)
(**) Chicony USB Keyboard: Applying InputClass "evdev keyboard catchall"
(**) Chicony USB Keyboard: always reports core events
(**) Chicony USB Keyboard: Device: "/dev/input/event5"
(II) Chicony USB Keyboard: Found keys
(II) Chicony USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Chicony USB Keyboard"
(type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event6)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation
(/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev
pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4,
EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button
emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation
(/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) Nov 29 22:21:19 NVIDIA(0): Setting mode "640x480_73"


My Xorg conf is as follows:

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Fri Apr  9 10:35:18 UTC 2010

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder75)  Thu Apr 22
11:44:23 PDT 2010

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
   Identifier     "Monitor0"
   VendorName     "Unknown"
   ModelName      "Proview TLU-01911CU"
   HorizSync       31.0 - 60.0
   VertRefresh     60.0 - 75.0
   Option         "DPMS"
   Option         "DPI" "96 x 96"
   # 1440x900 59.89 Hz (CVT 1.30MA) hsync: 55.93 kHz; pclk: 106.50 MHz
#    Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903
909 934 -hsync +vsync
EndSection

Section "Device"
   Identifier     "Device0"
   Driver         "nvidia"
   VendorName     "NVIDIA Corporation"
   BoardName      "ION"
   Option         "UseEDID" "False"
EndSection

Section "Screen"
   Identifier     "Screen0"
   Device         "Device0"
   Monitor        "Monitor0"
   DefaultDepth    24
   Option         "TwinView" "0"
   SubSection     "Display"
       Depth       24
       Modes      "1440x900"
   EndSubSection
EndSection


I found this link
[http://www.linuxquestions.org/questions/linux-software-2/xorg-conf-and-1440x900-resolution-254587/](http://www.linuxquestions.org/questions/linux-software-2/xorg-conf-and-1440x900-resolution-254587/)
seems to be almost same TV as mine, but it didn't work ( towards end of the post)

Just hoping someone can help me work out the modeline required to get
this TV to work in HDMI for the mythfrontend! I have it commented out
in my xorg conf:
# 1440x900 59.89 Hz (CVT 1.30MA) hsync: 55.93 kHz; pclk: 106.50 MHz
#    Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903
909 934 -hsync +vsync
I need to try and work out the correct values to use I guess!


Any advice would be greatly appreciated !

THANKS FOLKS!
Alessandro

---

