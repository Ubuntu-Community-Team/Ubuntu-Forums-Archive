---
title: "resolution issues"
date: 2010-04-18
forum: Multimedia Software
---

### Post by 007casper on 2010-04-18
I have a 30" apple cinema display.  The monitor handles up to 2560 x 1600 pixels which is the optimum resolution for this monitor.  I found out that most apple monitors have nvidia graphic card.

The monitor is hooked up to a motherboard Intel BOXDG45FC.  This motherboard has Onboard Video Chipset Intel GMA 4500.  However, using KDE interface I dont get beyond 1280x800 resolution for the monitor.

How can I get the maximum resolution for the monitor?

---

### Post by Untitled_No4 on 2010-04-19
Hi, 

I don't know anything about Intel graphic cards, but it might be that the the graphic card doesn't support the optimal resolution of the screen. It's still worth trying a few things.

Open Konsole (Alt + F2 then type Konsole and Enter) and type
```
xrandr
```

This should give you a list of available modes for your screen. For instance, mine is something like that:
> LVDS connected 1680x1050+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1680x1050      60.1*+   50.1  
   1400x1050      60.0  
   1280x1024      59.9  
   1440x900       59.9

If xrandr lists your desired resolution then you need to change the mode in xrandr. You'll have to note your monitor identifier from the output you will get above (in my example is LVDS) and your desired mode (2560x1600). If we use the identifier of my monitor the command you need to run is:
```
xrandr --output LVDS --mode 2560x1600
```

If xrandr does not find your resolution then things will be getting trickier. The first step is to confirm that your video card can handle such a high resolution. If it does, post back and we'll sort it out.

---

### Post by 007casper on 2010-08-27
> 
xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 641mm x 401mm 
1280x800       59.9* 
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)

xrandr gives me a slightly different output.

does this mean it could handle 8192 by 8192?

The 1280 by 800 is much better on 10.4 kubuntu.  However, this is weird.  The monitor is hooked up to a dvi, not hdmi1.  It also showed as hdmi on 9.04.

I am tempted to do 
xrandr --output Screen 0 --mode 2560x1600

I only hesitate, cause it is showing hdmi1 while it is hooked up to dvi.  Why would it show hdmi1?
I have two dvi output, and one hdmi on the motherboard.

How can I resolve the resolution issue?  Thank you.

---

### Post by 007casper on 2010-08-27
xrandr --output Screen 0 --mode 2560x1600

is this the right command?  And I was wondering how come it shows up hdmi1 even though it is hooked up to dvi.

Thank you.

---

### Post by Untitled_No4 on 2010-08-28
Hi,

In xrandr terminology "screen" is the display area (your desktop area) rather than the monitor. Your monitor is seems to be HDMI1 (despite it being DVI), so your command should be:
```
xrandr --output HDMI1 --mode 2560x1600
```

Since this mode is not listed the supported modes in your xrandr output I doubt if it will work. If it doesn't work, please post the output for the above command, if any, check if you have an xorg.conf file (/etc/X11/xorg.conf) and post its contents and also the contents of /var/log/Xorg.0.log since I think it might be an issue with your video card.

(p.s. I've set a subscription to this thread so I'll spot it when you reply).

---

### Post by 007casper on 2010-08-30
> xrandr --output HDMI1 --mode 2560x1600
xrandr: cannot find mode 2560x1600

I dont have xorg.conf file over at /etc/X11/xorg.conf

here is the Xorg.0.log
> 
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux thunder 2.6.32-24-server #41-Ubuntu SMP Thu Aug 19 02:47:08 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-server root=UUID=18ff0d20-28a6-405e-b186-cbbbb2c301ff ro quiet splash
Build Date: 21 July 2010  01:03:39PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Aug 29 20:21:20 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:2e12:8086:1004 Intel Corporation 4 Series Chipset Integrated Graphics Controller rev 3, Mem @ 0xd0000000/4194304, 0xc0000000/268435456, I/O @ 0x0000f220/8
(--) PCI: (0:0:2:1) 8086:2e13:8086:1004 Intel Corporation 4 Series Chipset Integrated Graphics Controller rev 3, Mem @ 0xd0400000/1048576
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
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
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
(==) Matched intel as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.9.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.4.1
	ABI class: X.Org Video Driver, version 6.0
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
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) Q45/Q43
(--) intel(0): Chipset: "Q45/Q43"
(II) intel(0): Output VGA1 has no monitor section
(II) intel(0): Output HDMI1 has no monitor section
(II) intel(0): Output DP1 has no monitor section
(II) intel(0): Output HDMI2 has no monitor section
(II) intel(0): Output DP2 has no monitor section
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output HDMI1
(II) intel(0): Manufacturer: APP  Model: 9221  Serial#: 33555277
(II) intel(0): Year: 2007  Week: 42
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 64  vert.: 40
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing not preferred mode in violation of standard!
(II) intel(0): redX: 0.640 redY: 0.343   greenX: 0.292 greenY: 0.611
(II) intel(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 71.0 MHz   Image Size:  641 x 401 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 268.0 MHz   Image Size:  641 x 401 mm
(II) intel(0): h_active: 2560  h_sync: 2608  h_sync_end 2640 h_blank_end 2720 h_border: 0
(II) intel(0): v_active: 1600  v_sync: 1603  v_sync_end 1609 v_blanking: 1646 v_border: 0
(II) intel(0): Serial No: CY7420QVXMP
(II) intel(0): Monitor name: Cinema HD
(II) intel(0): Number of EDID sections to follow: 1
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff00061021924d030002
(II) intel(0): 	2a1101038040287828fe85a3574a9c25
(II) intel(0): 	13505400000001010101010101010101
(II) intel(0): 	010101010101bc1b00a0502017303020
(II) intel(0): 	360081912100001ab06800a0a0402e60
(II) intel(0): 	3020360081912100001a000000ff0043
(II) intel(0): 	59373432305156584d500a00000000fc
(II) intel(0): 	0043696e656d612048440a00000001cd
(II) intel(0): Printing probed modes for output HDMI1
(II) intel(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
(II) intel(0): EDID for output DP1
(II) intel(0): EDID for output HDMI2
(II) intel(0): EDID for output DP2
(II) intel(0): Output VGA1 disconnected
(II) intel(0): Output HDMI1 connected
(II) intel(0): Output DP1 disconnected
(II) intel(0): Output HDMI2 disconnected
(II) intel(0): Output DP2 disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output HDMI1 using initial mode 1280x800
(II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(II) intel(0): [DRI2] Setup complete
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): VideoRam: 262144 KB
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
(==) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder disabled
(II) intel(0): Set up textured video
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
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) intel(0): Setting screen physical size to 338 x 211
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event2)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event2"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us,il"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle,lv3:ralt_switch,grp_led:scroll"
(II) XKB: reuse xkmfile /var/lib/xkb/server-D8FA2687F4CC47E114B5901F69BFCF7056C05E17.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us,il"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle,lv3:ralt_switch,grp_led:scroll"
(II) config/udev: Adding input device Sleep Button (/dev/input/event0)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event0"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us,il"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle,lv3:ralt_switch,grp_led:scroll"
(II) config/udev: Adding input device Dell Dell USB Keyboard (/dev/input/event4)
(**) Dell Dell USB Keyboard: Applying InputClass "evdev keyboard catchall"
(**) Dell Dell USB Keyboard: always reports core events
(**) Dell Dell USB Keyboard: Device: "/dev/input/event4"
(II) Dell Dell USB Keyboard: Found keys
(II) Dell Dell USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Dell Dell USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us,il"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle,lv3:ralt_switch,grp_led:scroll"
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event5)
(**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event5"
(II) Logitech USB Receiver: Found 20 mouse buttons
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found relative axes
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Configuring as mouse
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
(II) Logitech USB Receiver: initialized for relative axes.
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event6)
(**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event6"
(II) Logitech USB Receiver: Found 1 mouse buttons
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found relative axes
(II) Logitech USB Receiver: Found absolute axes
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as mouse
(II) Logitech USB Receiver: Configuring as keyboard
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us,il"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle,lv3:ralt_switch,grp_led:scroll"
(EE) Logitech USB Receiver: failed to initialize for relative axes.
(II) Logitech USB Receiver: initialized for absolute axes.
(II) config/udev: Adding input device Wacom Intuos 6x8 (/dev/input/event7)
(**) Wacom Intuos 6x8: Applying InputClass "evdev tablet catchall"
(**) Wacom Intuos 6x8: Applying InputClass "Wacom class"
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.10.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Option "Device" "/dev/input/event7"
(II) Wacom Intuos 6x8: type not specified, assuming 'stylus'.
(II) Wacom Intuos 6x8: other types will be automatically added.
(**) Wacom Intuos 6x8: always reports core events
(II) Wacom Intuos 6x8: hotplugging dependent devices.
(**) Option "Device" "/dev/input/event7"
(**) Wacom Intuos 6x8 eraser: always reports core events
(II) XINPUT: Adding extended input device "Wacom Intuos 6x8 eraser" (type: ERASER)
(--) Wacom Intuos 6x8 eraser: using pressure threshold of 61 for button 1
(--) Wacom Intuos 6x8 eraser: Wacom USB Intuos1 tablet speed=38400 maxX=20320 maxY=16240 maxZ=1023 resX=2540 resY=2540  tilt=enabled
(--) Wacom Intuos 6x8 eraser: top X=0 top Y=0 bottom X=20320 bottom Y=16240 resol X=2540 resol Y=2540
(**) Option "Device" "/dev/input/event7"
(**) Wacom Intuos 6x8 cursor: always reports core events
(II) XINPUT: Adding extended input device "Wacom Intuos 6x8 cursor" (type: CURSOR)
(--) Wacom Intuos 6x8 cursor: top X=0 top Y=0 bottom X=20320 bottom Y=16240 resol X=2540 resol Y=2540
(II) Wacom Intuos 6x8: hotplugging completed.
(II) XINPUT: Adding extended input device "Wacom Intuos 6x8" (type: STYLUS)
(--) Wacom Intuos 6x8: top X=0 top Y=0 bottom X=20320 bottom Y=16240 resol X=2540 resol Y=2540
(II) config/udev: Adding input device Wacom Intuos 6x8 (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event8)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event3)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
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
(II) intel(0): EDID vendor "APP", prod id 37409
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "2560x1600"x0.0  268.00  2560 2608 2640 2720  1600 1603 1609 1646 +hsync -vsync (98.5 kHz)
(II) intel(0): EDID vendor "APP", prod id 37409
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "2560x1600"x0.0  268.00  2560 2608 2640 2720  1600 1603 1609 1646 +hsync -vsync (98.5 kHz)
(II) intel(0): EDID vendor "APP", prod id 37409
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "2560x1600"x0.0  268.00  2560 2608 2640 2720  1600 1603 1609 1646 +hsync -vsync (98.5 kHz)
(II) intel(0): EDID vendor "APP", prod id 37409
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "2560x1600"x0.0  268.00  2560 2608 2640 2720  1600 1603 1609 1646 +hsync -vsync (98.5 kHz)
(II) intel(0): EDID vendor "APP", prod id 37409
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "2560x1600"x0.0  268.00  2560 2608 2640 2720  1600 1603 1609 1646 +hsync -vsync (98.5 kHz)
(II) intel(0): EDID vendor "APP", prod id 37409
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "2560x1600"x0.0  268.00  2560 2608 2640 2720  1600 1603 1609 1646 +hsync -vsync (98.5 kHz)

please, advise.

---

### Post by 007casper on 2010-08-31
bump

---

### Post by 007casper on 2010-08-31
I have two lines indicating 
(II) intel(0): Modeline "1280x800"x0.0 71.00 1280 1328 1360 1440 800 803 809 823 +hsync -vsync (49.3 kHz)
 (II) intel(0): Modeline "2560x1600"x0.0 268.00 2560 2608 2640 2720 1600 1603 1609 1646 +hsync -vsync (98.5 kHz)

I would love to have the maximum resolution.
I dont have xorg.conf file by default.  I am using motherboard's Onboard Video Chipset Intel GMA 4500.

I have been looking for a driver for Intel GMA 4500, hoping that will fix the issue.

Please, advise.  Thank you.

---

### Post by 007casper on 2010-09-01
I am looking all around trying to bring up my monitor resolution to its capacity.  Some of these links are outdated, and it doesnt apply to 10.4
Maybe the answer is in front of me, and I dont see it.  Any advice will be awesome.  Thank you so much.  Here are the links I have found.

[http://ubuntuforums.org/showthread.php?t=928668](http://ubuntuforums.org/showthread.php?t=928668)
Intel GMA 4500

[http://ubuntuforums.org/showthread.php?t=963386&highlight=Intel+GMA+4500](http://ubuntuforums.org/showthread.php?t=963386&highlight=Intel+GMA+4500)

took me too
[https://bugs.freedesktop.org/show_bug.cgi?id=17292](https://bugs.freedesktop.org/show_bug.cgi?id=17292)
posts 122/123 and summarized on 145 

[http://forum.notebookreview.com/sony/318862-ubuntu-sony-vaio-sr.html](http://forum.notebookreview.com/sony/318862-ubuntu-sony-vaio-sr.html)
[http://melchiorre.wordpress.com/2008/07/31/driver-intel-240-deb-package/](http://melchiorre.wordpress.com/2008/07/31/driver-intel-240-deb-package/)

---

### Post by Untitled_No4 on 2010-09-02
Okay, this might be your problem:
```
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
```

Vesa is the basic graphic driver in Linux and that might be why xrandr doesn't see the other modes for the intel cards.

Perhaps loading the Intel card specifically will help. So you will need to create an /etc/X11/xorg.conf file with the following contents:
```
Section "Device"
	Driver      "intel"
EndSection
```

reboot you computer, run xrandr and see what modes you get now. Let me know how it works (For some reason the subscription on the thread didn't work so I set it again).

EDIT:
If your computer fails to start X after the reboot then log in to recovery mode and just delete this xorg.conf file.

---

### Post by 007casper on 2010-09-02
first I tried to create the xorg.conf file without going to sudo mode.  And the terminal just acted up.  When I got out from the file, I did ls on /etc/X11

It showed xorg.conf.failsafe

I removed that file.  And recreated from scratch with sudo.  I only added these lines 
```
Section "Device"
	Driver      "intel"
EndSection
```

then shutdown computer.  I restart it, and didnt watch the screen.  I came back, and saw 
> (process 357):GLib-WARNING**:getpwuid-r():failed due to unknown user id (0)

then, I turned it off the computer, it showed the splash page and turned off.  

I booted again, it seemed like it was going to start, then I got a message checking disk, then the screen went black and again gave me a similar message as above, however the process number was different.
> (process 329):GLib-WARNING**:getpwuid-r():failed due to unknown user id (0)

this time I didnt get anything like checking disk, it doesnt give me any other option.  It is just black screen with that message.

I shut down.  Turned off the computer, waited a bit.  I plugged it back, and turn it on.

This time I got different process number 342
> (process 342):GLib-WARNING**:getpwuid-r():failed due to unknown user id (0)

:(

>>If your computer fails to start X after the reboot then log in to >>recovery mode and just delete this xorg.conf file.

It doesnt give me an option to go to recovery mode.

I am ready for the next step.  I really need that intel vgrx card to sync in.  I really appreciate your help.

I think I got a similar message earlier today for the first time I started the computer.  I didnt think much of it.  I turned it off, and reboot, and it was good to go.  I dont think it has to do with xorg.conf, however this time it doesnt reboot at all.

---

### Post by Untitled_No4 on 2010-09-02
I don't think this error is related to your resolution problem or the new xorg.conf. You probably notice this error now since your xserver doesn't start. There's some information about this error at [http://ubuntuforums.org/showthread.php?t=1443231](http://ubuntuforums.org/showthread.php?t=1443231) and the linked bug report. Perhaps the information at [http://allaboutfedora.blogspot.com/2009/02/f10-how-to-fix-getpwuidr-failure.html](http://allaboutfedora.blogspot.com/2009/02/f10-how-to-fix-getpwuidr-failure.html) will also help.

------------------------------------------

Your details say that you're running Kubuntu Jaunty. Is that correct? If so, is there a specific reason why? If I remember correctly there was a bug with the intel drivers around that time for most distributions. Can you try and boot from a Lucid live CD and see if you get your desired resolution? This might be the easiest thing to do, and I'd do that before continuing with the rest of the post.

------------------------------------------

Anwyay, to log in to recovery mode you have to press shift when grub is loading, basically after the bios boot process has finished and before Ubuntu loads. This should give you a menu with an option(s) for recovery mode. After Ubuntu load you will be presented with another menu and you have to choose going into shell (something along those lines), but you don't need networking.

If you have set up a root password you will have to enter it, otherwise it will go directly into command line. There you have to type
```
sudo rm /etc/X11/xorg.conf
```
to remove the xorg.conf file. Then let the system create a new configuration file by typing:
```
X -configure
```
this should create an xorg.conf.new file under /root. It will then ask you if you want to test the file but I'd skip this since it never worked for me. Then reboot your comptuer by typing
```
reoot
```

You should now be able to log into Kubuntu as normal. Now post the contents of /root/xorg.conf.new here before you do anything with it, so we can see what it contains first.

------------------------------------------

If you can't get to the recovery console you will have to boot into a liveCD/USB and delete your xorg.conf file there. The xorg.conf file will not be under /etc/X11 because the system is from the live CD. You will either have to use dolphin and find the partition where the system is installed and go to etc/X11 under that partition and delete the file.

You can also mount the partition from the command line, but you will have to know what partition it is. Assuming it is sda1 (the most probably if you don't dual boot), the sequence of commands should be:
```
sudo mount /dev/sda1 /mnt
sudo mv /mnt/etc/X11/xorg.conf /mnt/etc/X11/xorg.bak
```
this would rename the file rather than delete it since I don't want to break other installations if you have any. 

You will then still have to regenerate an xorg.conf.new file. To do that, reboot your system to your Kubuntu installation, but when you get to the log in screen do not log in but rather press alt  + ctrl + F1. This should get you into a virtual terminal, and log in there. Then run:
```
sudo init 1
sudo X -configure
```
The first command should shut your xserver down. The second should create the xorg.conf.new file. If you log in as your user it will create the file in your home directory. Reboot the system and then post the contents of the file.

---

### Post by 007casper on 2010-09-02
It was really hard to get to the console.  It constantly acts like it is going to start, and then it gives me the error -GLib-WARNING**:getpwuid-r():failed due to unknown user id (0) - Thank you for the link.  

I am using Kubuntu 10.4 Lucid Lynx.  I was using Jaunty and then did an upgrade to 10.4.  If it is any help, I am using server edition, with kde interface 64 bit.

shift didnt work. I tried F2.  The system got stuck on a black screen.  Restart the computer.  Then, hold DEL button down, I got a window.  I chose low graphics mode in one session.  Then got a warning.

Ubuntu is running in low graphics mode
The following error was encountered. You may need to update your configuration to solve this.

(EE)Problem parsing the config file
(EE)Error parsing the config file

Then, got an option to pick 'exit to console', login to the terminal.  cd /etc/X11, then ls 
Even though, I deleted the xorg.conf.failsafe, there was a file called xorg.conf.failsafe.  

cat xorg.conf.failsafe```

Section "Device"
	Identifier "Configured Video Device"
	Driver	   "fbdev"
EndSection

Section "Monitor"
	Identifier "Configured Monitor"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Monitor "configured Monitor"
	Device "Configured Video Device"
EndSection
```

checked xorg.conf file same as ever
```

Section "Device"
	Driver "intel"
EndSection
```

removed both files - sudo rm /etc/X11/xorg.conf, sudo rm /etc/X11/xorg.conf.failsafe

dont know if this would help, but under X11 I have these files
app-defaults, default-display-manager, rgb.txt, xinit, Xreset.d, Xsession, Xsession.options, Xwrapper.config, cursors, fonts, X, Xreset, Xresources, Xsession.d, XvMCConfig

while I was at /etc/X11 sudo X -configure, then sudo reboot. I got the GLib-WARNING message.  Reboot, once again, this time I was able to login.  root doesnt have xorg.conf.new

/root files are
.aptitude
.bashrc
.config
.dbus
.debtags
.gconf
.gconfd
.gnome2
.kde
.profile
.recently-used.xbel

do you think creating sudo X -configure while at path /etc/X11 was the problem.  However, I do have xorg.conf.new under home
/home/me/xorg.conf.new

```

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "extmod"
	Load  "glx"
	Load  "record"
	Load  "dri2"
	Load  "dri"
	Load  "dbe"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "4 Series Chipset Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


```

I checked /etc/X11
there is xorg.conf.failsafe again
/etc/X11$ cat xorg.conf.failsafe
cat xorg.conf.failsafe
```

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "fbdev"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

should I change fbdev to intel over at xorg.conf.failsafe?  Ready for the next step.  

By the way, tried so many times to boot from a flashdisk in the begining, it just wouldnt pick up the flash disk.  It kept giving me GLib warning.,and it will get stuck.  I created ubuntu 10.4 server 64bit edition.  If I can get better resolution, it will be awesome. Because right now it looks really silly with big fonts, and icons on a big screen.

The other thing is that I cant get into bios.  That warning creeps up.  It is getting worse since I have rebooted several times.

Once again, thank you so much for your help. I really appreciate it.

---

### Post by Untitled_No4 on 2010-09-03
xorg.conf.failsafe shouldn't get in the way and should be useful for when you need a failsafe login, so I'd keep it as it is. 

From your personal info I gather you are actually on Lucid?

X -configure creates the file under the home folder of the user that runs the command, so if you logged "in as your own user that's why the file is there. It's perfectly normal.

The next step is copying the xorg.conf.new in your home folder to xorg.conf in /etc/X11
```
cp ~/xorg.conf.new /etc/X11/xorg.conf
```
and then restarting and hoping that X starts. If it doesn't you'll have to delete the xorg.conf file under /etc/X11 but leave the new file in your home folder.

If X does start and you can log in to your user, you're still probably going to have a low resolution since (form your xorg.conf.new file):
```
Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

```

So now add the add one line to make it look like:
```
Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
        Option	     "PreferredMode" "2560x1600"
EndSection

```
and restart again, and if you can log in, run
```
xrandr
```
and see if you have your mode listed there.

---

### Post by 007casper on 2010-09-03
I stil get GLib warning I ignored it.  Reboot the computer once more, and I got the proper login window.

Followed your directions.  I inserted Option "PreferredMode" "2560x1600" under xorg.conf file in /etc/X11

I didnt add that line to /home/xorg.conf.new

xrandr
> 
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 641mm x 401mm
1280x800 59.9*
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis) 

xrandr --output HDMI1 --mode 2560x1600
xrandr: cannot find mode 2560x1600 

:(

---

### Post by Untitled_No4 on 2010-09-03
Let's try the next step...

1. Can you please post the Xorg.0.log as before so we can see if there are any error messages?

2. I'm sorry, I just realised I put the code outside the CODE tags in my last post. Anyway, please edit your xorg.conf file. Delete the current contents and paste that in:
```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Module"
	Load  "extmod"
	Load  "glx"
	Load  "record"
	Load  "dri2"
	Load  "dri"
	Load  "dbe"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
	Option 	     "PreferredMode" "2560x1600"
EndSection

Section "Device"
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	Option	    "Monitor0" "0-HDMI"
	BoardName   "4 Series Chipset Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

I basically deleted all the stuff that you don't really need and added "Option	    "Monitor0" "0-HDMI"" under the Device section and made sure the Monitor section is as it should be. Restart and post your xrandr output again?

(You don't need to change ~/xorg.conf.new since it doesn't affect anything on the system)

---

### Post by Yellow Pasque on 2010-09-03
You have to create the mode before adding it:
```
xrandr --newmode "2560x1600" 268.00 2560 2608 2640 2720 1600 1603 1609 1646 +hsync -vsync 
xrandr --addmode HDMI1 2560x1600
```

---

### Post by 007casper on 2010-09-03
no worries.  I was able to read your code.
here is the Xorg.0.log, after inserting - Option "PreferredMode" "2560x1600"

```


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux symphony 2.6.32-24-server #42-Ubuntu SMP Fri Aug 20 15:38:55 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-server root=UUID=18ff0d20-28a6-405e-b186-cbbbb2c301ff ro quiet splash
Build Date: 21 July 2010  01:03:39PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep  3 08:58:35 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Keyboard0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
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
(**) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Mouse0
(WW) Disabling Keyboard0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:2e12:8086:1004 Intel Corporation 4 Series Chipset Integrated Graphics Controller rev 3, Mem @ 0xd0000000/4194304, 0xc0000000/268435456, I/O @ 0x0000f220/8
(--) PCI: (0:0:2:1) 8086:2e13:8086:1004 Intel Corporation 4 Series Chipset Integrated Graphics Controller rev 3, Mem @ 0xd0400000/1048576
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
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
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.9.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) Primary Device is: PCI 00@00:02:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) Q45/Q43
(--) intel(0): Chipset: "Q45/Q43"
(II) intel(0): Output VGA1 using monitor section Monitor0
(**) intel(0): Option "PreferredMode" "2560x1600"
(II) intel(0): Output HDMI1 has no monitor section
(II) intel(0): Output DP1 has no monitor section
(II) intel(0): Output HDMI2 has no monitor section
(II) intel(0): Output DP2 has no monitor section
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output HDMI1
(II) intel(0): Manufacturer: APP  Model: 9221  Serial#: 33555277
(II) intel(0): Year: 2007  Week: 42
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 64  vert.: 40
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing not preferred mode in violation of standard!
(II) intel(0): redX: 0.640 redY: 0.343   greenX: 0.292 greenY: 0.611
(II) intel(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 71.0 MHz   Image Size:  641 x 401 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 268.0 MHz   Image Size:  641 x 401 mm
(II) intel(0): h_active: 2560  h_sync: 2608  h_sync_end 2640 h_blank_end 2720 h_border: 0
(II) intel(0): v_active: 1600  v_sync: 1603  v_sync_end 1609 v_blanking: 1646 v_border: 0
(II) intel(0): Serial No: CY7420QVXMP
(II) intel(0): Monitor name: Cinema HD
(II) intel(0): Number of EDID sections to follow: 1
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff00061021924d030002
(II) intel(0): 	2a1101038040287828fe85a3574a9c25
(II) intel(0): 	13505400000001010101010101010101
(II) intel(0): 	010101010101bc1b00a0502017303020
(II) intel(0): 	360081912100001ab06800a0a0402e60
(II) intel(0): 	3020360081912100001a000000ff0043
(II) intel(0): 	59373432305156584d500a00000000fc
(II) intel(0): 	0043696e656d612048440a00000001cd
(II) intel(0): Printing probed modes for output HDMI1
(II) intel(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
(II) intel(0): EDID for output DP1
(II) intel(0): EDID for output HDMI2
(II) intel(0): EDID for output DP2
(II) intel(0): Output VGA1 disconnected
(II) intel(0): Output HDMI1 connected
(II) intel(0): Output DP1 disconnected
(II) intel(0): Output HDMI2 disconnected
(II) intel(0): Output DP2 disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output HDMI1 using initial mode 1280x800
(II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(==) Depth 24 pixmap format is 32 bpp
(II) intel(0): [DRI2] Setup complete
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): VideoRam: 262144 KB
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
(==) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder disabled
(II) intel(0): Set up textured video
(II) intel(0): direct rendering: DRI2 Enabled
(WW) intel(0): Option "PreferredMode" is not used
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
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) intel(0): Setting screen physical size to 338 x 211
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event2)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event2"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us,il"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle,lv3:ralt_switch,grp_led:scroll"
(II) XKB: reuse xkmfile /var/lib/xkb/server-D8FA2687F4CC47E114B5901F69BFCF7056C05E17.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us,il"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle,lv3:ralt_switch,grp_led:scroll"
(II) config/udev: Adding input device Sleep Button (/dev/input/event0)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event0"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us,il"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle,lv3:ralt_switch,grp_led:scroll"
(II) config/udev: Adding input device Dell Dell USB Keyboard (/dev/input/event4)
(**) Dell Dell USB Keyboard: Applying InputClass "evdev keyboard catchall"
(**) Dell Dell USB Keyboard: always reports core events
(**) Dell Dell USB Keyboard: Device: "/dev/input/event4"
(II) Dell Dell USB Keyboard: Found keys
(II) Dell Dell USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Dell Dell USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us,il"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle,lv3:ralt_switch,grp_led:scroll"
(II) config/udev: Adding input device Wacom Intuos 6x8 (/dev/input/event5)
(**) Wacom Intuos 6x8: Applying InputClass "evdev tablet catchall"
(**) Wacom Intuos 6x8: Applying InputClass "Wacom class"
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.10.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Option "Device" "/dev/input/event5"
(II) Wacom Intuos 6x8: type not specified, assuming 'stylus'.
(II) Wacom Intuos 6x8: other types will be automatically added.
(**) Wacom Intuos 6x8: always reports core events
(II) Wacom Intuos 6x8: hotplugging dependent devices.
(**) Option "Device" "/dev/input/event5"
(**) Wacom Intuos 6x8 eraser: always reports core events
(II) XINPUT: Adding extended input device "Wacom Intuos 6x8 eraser" (type: ERASER)
(--) Wacom Intuos 6x8 eraser: using pressure threshold of 61 for button 1
(--) Wacom Intuos 6x8 eraser: Wacom USB Intuos1 tablet speed=38400 maxX=20320 maxY=16240 maxZ=1023 resX=2540 resY=2540  tilt=enabled
(--) Wacom Intuos 6x8 eraser: top X=0 top Y=0 bottom X=20320 bottom Y=16240 resol X=2540 resol Y=2540
(**) Option "Device" "/dev/input/event5"
(**) Wacom Intuos 6x8 cursor: always reports core events
(II) XINPUT: Adding extended input device "Wacom Intuos 6x8 cursor" (type: CURSOR)
(--) Wacom Intuos 6x8 cursor: top X=0 top Y=0 bottom X=20320 bottom Y=16240 resol X=2540 resol Y=2540
(II) Wacom Intuos 6x8: hotplugging completed.
(II) XINPUT: Adding extended input device "Wacom Intuos 6x8" (type: STYLUS)
(--) Wacom Intuos 6x8: top X=0 top Y=0 bottom X=20320 bottom Y=16240 resol X=2540 resol Y=2540
(II) config/udev: Adding input device Wacom Intuos 6x8 (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event6)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event3)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
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
(II) intel(0): EDID vendor "APP", prod id 37409
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "2560x1600"x0.0  268.00  2560 2608 2640 2720  1600 1603 1609 1646 +hsync -vsync (98.5 kHz)
(II) intel(0): EDID vendor "APP", prod id 37409
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "2560x1600"x0.0  268.00  2560 2608 2640 2720  1600 1603 1609 1646 +hsync -vsync (98.5 kHz)
(II) intel(0): EDID vendor "APP", prod id 37409
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "2560x1600"x0.0  268.00  2560 2608 2640 2720  1600 1603 1609 1646 +hsync -vsync (98.5 kHz)
(II) intel(0): EDID vendor "APP", prod id 37409
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "2560x1600"x0.0  268.00  2560 2608 2640 2720  1600 1603 1609 1646 +hsync -vsync (98.5 kHz)

```

created mode as suggested by Temüjin
```

xrandr --newmode "2560x1600" 268.00 2560 2608 2640 2720 1600 1603 1609 1646 +hsync -vsync 
xrandr --addmode HDMI1 2560x1600

```

revised xorg.conf file
```

Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Module"
        Load  "extmod"
        Load  "glx"
        Load  "record"
        Load  "dri2"
        Load  "dri"
        Load  "dbe"
EndSection

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
        Option       "PreferredMode" "2560x1600"
EndSection

Section "Device"
        Identifier  "Card0"
        Driver      "intel"
        VendorName  "Intel Corporation"
        Option      "Monitor0" "0-HDMI"
        BoardName   "4 Series Chipset Integrated Graphics Controller"
        BusID       "PCI:0:2:0"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        SubSection "Display"
                Viewport   0 0
                Depth     1
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     4
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     8
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     15
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     16
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

```

> xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 641mm x 401mm
   1280x800       59.9* 
   2560x1600      59.9  
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)

I got really excited.  I went to display preferences, and looked at HDMI1 connected, pull down menu 2560x1600 is there.  Selected 2560x1600 refresh auto - screen went black for about a minute, then came back as 1280x1600

---

### Post by Untitled_No4 on 2010-09-03
Did you try to run xrandr after rebooting and setting the new mode to see what modes are available? I suspect that the xrandr newmod function needs to run after every reboot to the system, so if you reboot run it again and then run xrandr to see what modes are available.

---

### Post by 007casper on 2010-09-03
I tried xrandr before reboot.  I figured I should reboot for it to work.  I just wanted to see what it would print, and if it would work without a reboot.  Also, I was a bit hesitant to reboot right a way.  I know it sounds a bit crazy, but that GLib warning is a bit driving me crazy.

I have to 'turn on, and then off' the computer sometimes fifteen times hoping it will start.  

Anyways, I did a full shutdown.  I waited for a minute or two.  I turned on the computer, as expected I am stuck with GLib warning.  The login screen doesnt show up, it just gives me the warning after it seems like it would boot. 

I tried holding the delete button. This time no luck.  I have tried shift button.  No luck.

If I can boot the computer without that warning, I am going to run xrandr.

Unfortunately, right now there isnt any solution for GLib warning.  I think it started after I installed netbeans, and vector application

---

### Post by Untitled_No4 on 2010-09-03
I don't know if the reboot problem relates to the glib warning, I assume not. Do you have a live CD you can use to boot and then undo the last change to the xorg.conf file?

---

### Post by 007casper on 2010-09-03
I dont have a cd driver attached to this computer.  I could attach one, and create a cd if it is necessary.  The only thing that is attached to this computer is monitor, keyboard, wacom tablet, earphones, and ethernet cable.

However, I do have ubuntu 10.4 on usb flash drive.  Yesterday, I tried with usb flash, and I couldnt get it work.  I couldnt even get to bios menu to change the boot priority to flash.  It is crazy.

Right now, I am on the terminal on the command line.  I really dont think it is the xorg.conf causing the problem.  Because, I saw this kind of an error once before we were trying to set xorg.conf.

I am going to uninstall the netbeans from the command line.  The funny thing is I cant remember the vector applications name.

If you want me to run anything specific right now on the command line, please let me know.

---

### Post by 007casper on 2010-09-03
sudo apt-get remove netbeans

netbeans removed, it listed all these dependencies that I could remove since netbeans is uninstalled.  I wasnt really sure if these dependencies were required by other applications.  I am stuck at this GLib-Warning again.

I still cant start the system.  This time I did ctrl+alt+f1 and got into recovery mode.  It states - What would you like to do?
Run Ubuntu in low graphics mode for just one session
Reconfigure graphics
Troubleshoot the error
Exit to console login
Restart X

I tried Run Ubuntu in low graphics mode for just one session before without a luck.  I kept choosing exit to console login.  Do you think reconfigure graphics, or restart X would help.  Otherwise, I am going to choose exit to console and delete xorg.conf from /etc/X11 to see if I can get a login but I doubt xorg.conf is the problem, because it seems as everyone has a different opinion about Glib warning bug.

edit:  once in a while the computer goes for system check during the boot, and then warning problem occurred more frequently. I used to hit cancel for system check and that way I was able to get me to the login screen on the next boot.  This time, no luck.  Regarding this GLib-Warning the other threads indicates to ignore this warning and it is harmless.  The problem is that I cant login to the computer.

---

### Post by 007casper on 2010-09-03
this time I picked Reconfigure graphics on the terminal.  Then, picked default generic configuration.  Then, reboot the computer.  I also removed netbeans and its dependencies, and inkscape.

I am back to square one.  I really need to solve the graphic issue.  Low resolution is really slowing me down.  

Should I post .xsession-errors

---

### Post by Yellow Pasque on 2010-09-03
I copied the modeline from your Xorg log, which had 0Hz(?), so maybe it was not correct. If you need to generate a different one...
```
cvt -v 2560 1600 60.0Hz
```

---

### Post by 007casper on 2010-09-03
I am not really sure how to go about what you wrote.

Do you want me to ```

xrandr --newmode "2560x1600" 268.00 2560 2608 2640 2720 1600 1603 1609 1646 +hsync -vsync 
xrandr --addmode HDMI1 2560x1600
```

then
```
cvt -v 2560 1600 60.0Hz
```

then recreate xorg.conf file. At the moment the previous xorg.conf file is at /etc/X11 as xorg.conf-back-100903114240
Do you want me to delete it?
```

Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Module"
        Load  "extmod"
        Load  "glx"
        Load  "record"
        Load  "dri2"
        Load  "dri"
        Load  "dbe"
EndSection

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
        Option       "PreferredMode" "2560x1600"
EndSection

Section "Device"
        Identifier  "Card0"
        Driver      "intel"
        VendorName  "Intel Corporation"
        Option      "Monitor0" "0-HDMI"
        BoardName   "4 Series Chipset Integrated Graphics Controller"
        BusID       "PCI:0:2:0"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        SubSection "Display"
                Viewport   0 0
                Depth     1
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     4
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     8
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     15
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     16
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection
```

then reboot
then xrandr
depending on the output enter something like xrandr --output HDMI1 --mode 2560x1600

I have looked at xorg.0.log file. I saw (II) intel(0): Modeline "2560x1600"x0.0  268.00  2560 2608 2640 2720  1600 1603 1609 1646 +hsync -vsync (98.5 kHz).  

98.5 kHz - not 60? Am I looking at the wrong way?

Thank you so much for your help.

---

### Post by Yellow Pasque on 2010-09-03
Post the output of the cvt command (assuming 60Hz is the correct refresh rate for the monitor).

---

### Post by 007casper on 2010-09-03
sure.

cvt -v 2560 1600 60.0Hz
# 2560x1600 59.99 Hz (CVT 4.10MA) hsync: 99.46 kHz; pclk: 348.50 MHz
Modeline "2560x1600_60.00"  348.50  2560 2760 3032 3504  1600 1603 1609 1658 -hsync +vsync

---

### Post by Yellow Pasque on 2010-09-03
```
xrandr --newmode "2560x1600" 348.50 2560 2760 3032 3504 1600 1603 1609 1658 -hsync +vsync
xrandr --addmode HDMI1 2560x1600
xrandr --output HDMI1 --mode 2560x1600
```
If that works correctly, then we'll set it up permanently in xorg.conf

---

### Post by 007casper on 2010-09-03
xrandr --newmode "2560x1600" 348.50 2560 2760 3032 3504 1600 1603 1609 1658 -hsync +vsync
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  29                                                                          
  Current serial number in output stream:  29

I think it just gave errors.  Do you still want me to continue with?
xrandr --addmode HDMI1 2560x1600
xrandr --output HDMI1 --mode 2560x1600

---

### Post by Yellow Pasque on 2010-09-03
Hmm. It works fine for me (on Debian sid and in a Lucid VM).

---

### Post by 007casper on 2010-09-03
did you download a specific drive?

this is all default.  I havent done anything to kubuntu 10.4

The only application that I have installed gimp, and virtual machine by sun virtualbox.  I can remove those if necessary.  Even though, I dont think this is the problem.

I removed netbeans, inkscape, so I am only left with gimp if I still get GLip warnings, I will remove gimp too.  Because I didnt used to get that error before.  I got it only once before creating the xorg.conf file.  Even though it is stated it is harmless bug, it makes it really hard to boot in.

How is your set up?  Is there anything that I can post that we can compare?

Thank you.

---

### Post by Yellow Pasque on 2010-09-03
Sorry, but I'm not sure what else to suggest except trying an updated X Server (and maybe using the previous commands on it). [https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=lucid](https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=lucid)

---

### Post by 007casper on 2010-09-03
I am sorry if this sounds really stupid, but how do I go about that.

I looked at synaptic.  And the link you provided

looking at all these packages, the only thing I can think of xorg-server, and xserver-xorg-video-intel which seems to be for ubuntu

* For less fresh, more stable updates, see [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
 * For single driver updates, see [https://launchpad.net/~xorg-edgers/+archive/drivers-only](https://launchpad.net/~xorg-edgers/+archive/drivers-only) 
To revert to official packages, you can install the ppa-purge package and run sudo ppa-purge xorg-edgers

then looking around I found this
[https://wiki.ubuntu.com/XorgOnTheEdge](https://wiki.ubuntu.com/XorgOnTheEdge)

?

---

### Post by paul079 on 2010-09-04
2 things:
  1.  Ubuntu and it's derivates (Kubuntu, Xubuntu, etc.) have not used xorg.conf for a few releases now, though it might still work.  I don't remember if that's all of xorg or just Ubunutu.
  2.  This should help: [https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")

---

### Post by 007casper on 2010-09-06
I am still trying to make this work. When I create xorg.conf file it hicks up.  I get GLib Warning, and usually I cant login.  I wonder if xorg.conf file needs to be set up slightly differently.

The whole thing seems not steady.

The command> 
xrandr --newmode "2560x1600" 348.50 2560 2760 3032 3504 1600 1603 1609 1658 -hsync +vsync

worked before, and then gave me an error, and now it is working again.  I would update x server but not really sure how to go about it.

I also checked out the links paul079 provided.
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
[http://www.x.org/wiki/FAQVideoModes#head-82230a582646cbf28ac41dec2139732ee868e0d2](http://www.x.org/wiki/FAQVideoModes#head-82230a582646cbf28ac41dec2139732ee868e0d2)


xrandr```

Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 641mm x 401mm
   1280x800       59.9* 
   2560x1600      59.9  
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
```
Is there a reason why I have * for 1280x800 59.9* and not for 2560x1600 59.9?

```

xrandr --newmode "2560x1600" 348.50 2560 2760 3032 3504 1600 1603 1609 1658 -hsync +vsync
xrandr --addmode HDMI1 2560x1600

```

the gui display shows it.  I do xrandr.  It is there.  If I do xrandr --output HDMI1 --mode 2560x1600.  The screen goes black.  I dont see anything.  I have to shutdown and restart the computer.  I figure maybe it is refresh rate, and other little details causing this issue.

There is a missing link somewhere, but cant figured it out.  I created a new xorg.conf file, hoping this would work.  Slightly different than older ones.
```

Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Module"
        Load  "extmod"
        Load  "glx"
        Load  "record"
        Load  "dri2"
        Load  "dri"
        Load  "dbe"
EndSection

Section "Monitor"
        Identifier   "Monitor0"
        DisplaySize  641 401
        VendorName   "APP"
        ModelName    "Cinema HD"
        Option       "DPMS"
        Modeline     "2560x1600_60.00"  348.50  2560 2760 3032 3504  1600 1603 1609 1658 -hsync +vsync
        Option       "PreferredMode" "2560x1600"
EndSection

Section "Device"
        Identifier  "Card0"
        Driver      "intel"
        VendorName  "Intel Corporation"
        Option      "Monitor0" "0-HDMI"
        BoardName   "4 Series Chipset Integrated Graphics Controller"
        BusID       "PCI:0:2:0"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        SubSection "Display"
                Viewport   0 0
                Depth     1
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     4
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     8
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     15
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     16
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

```

---

### Post by Yellow Pasque on 2010-09-06
The chipset is capable:
> The GMCH&#8217;s SDVO ports are each capable of driving a 400 MP pixel rate. Each port is capable of driving a digital display up to 2560x1600 @ 60Hz.

I'm not sure if there is any driver limitation, but I doubt it. Make sure you have a dual-link DVI cable: [http://en.wikipedia.org/wiki/Digital_Visual_Interface](http://en.wikipedia.org/wiki/Digital_Visual_Interface) If you do, then it might be time to file a bug report.

---

### Post by 007casper on 2010-09-06
I will check the dvi cable.  I am not in front of the computer right now.

Do you think the * mark next to 59.9 has to do with it?  What is the significance of *?  I was thinking of trying another video graphic card, instead of using on board card.  But if it is a bug, it wont really matter I guess.

HDMI1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 641mm x 401mm
   1280x800       59.9* 
   2560x1600      59.9

---

### Post by Yellow Pasque on 2010-09-06
The * indicates the current mode/resolution.

---

### Post by 007casper on 2010-09-06
The monitor has DVI-D ([Dual link]("http://en.wikipedia.org/wiki/File:DVI_Connector_Types.svg")).


so, I guess it is time to file a bug report.  I wonder if ubuntu, or xcfe would work?

Do you think getting an nvidia graphic card would solve the problem?

thank you.

---

### Post by Yellow Pasque on 2010-09-06
Yes, the monitor is dual-link, but look at the cable connector...

> Do you think getting an nvidia graphic card would solve the problem?

No, especially if you don't have the right cable ;)

---

### Post by 007casper on 2010-09-07
The cable is DVI-D (Dual link). 

You know my friend had a similar problem with a similar board with smaller apple monitor.  His was not only low resolution, it flickered on top of that.

Someone suggested him to buy an acer monitor (acer monitor doesnt have internal video card, apple monitors have nvidia card) and hooking it up to a hdmi cable and that solved his problem.

The cinema display has a really nice resolution, and high pixel rate.  The acer monitor isnt even close to it in specs.  So, I wonder if I attached an nvidia card, maybe the monitor and the video card would work.  

The apple monitor doesnt have hdmi slot, and dvi-d dual link is considered to be partially compatible with the hdmi set up.  I also wondered maybe using DVI-D Female to HDMI Male Adaptor.  

It is really frustrating

---

