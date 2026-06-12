---
title: "Add unlisted screen resolution"
date: 2011-06-13
forum: Multimedia Software
---

### Post by MiG29 on 2011-06-13
I'm trying to get my Xubuntu 11.04 installation to recognize 1680x1050 resolution for my monitor.  It's a dual-boot system, and the resolution works just great in Windows 7.  

Can anyone fill me in on how to add this resolution to Xubuntu 11.04 ?  Right now the highest listed is 1280x1024.

Thanks in advance.

---

### Post by handy on 2011-06-14
If when you say listed, you are referring to the /etc/X11/xorg.conf ?

Then you should be able to add your resolution so that it is the first one in the line like so:

```
        Modes      "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
```

If you are referring to something else (X)ubuntu specific, I can't help you as I'm not familiar with it these days.

---

### Post by Toz on 2011-06-14
It's possible that you may not have an xorg.conf file. If that's the case, can you post back the contents of your **/var/log/Xorg.0.log** file?

Also, open a terminal window, type in the following command, and post back the results:```
lspci | grep VGA
```

---

### Post by happyisland on 2011-06-14
I'm having the same issue, trying to get my Ubuntu 11.04 system to recognize a new monitor I just switched to. This new monitor's native resolution is 1920 x 1200, but the highest resolution I can get is an extremely ugly 1024 x 768.

When I do lspci | grep VGA I get:

00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)


And for good measure, here's my /var/log/Xorg.0.log
```
[    20.768] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    20.768] X Protocol Version 11, Revision 0
[    20.768] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    20.768] Current Operating System: Linux manager-desktop 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64
[    20.768] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=87a737e1-ea1f-4230-bb9a-af13a24e9c59 ro quiet splash vt.handoff=7
[    20.768] Build Date: 21 May 2011  11:48:41AM
[    20.768] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    20.768] Current version of pixman: 0.20.2
[    20.768] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    20.768] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    20.768] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jun 14 16:58:36 2011
[    20.822] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    20.865] (==) No Layout section.  Using the first Screen section.
[    20.865] (==) No screen section available. Using defaults.
[    20.865] (**) |-->Screen "Default Screen Section" (0)
[    20.865] (**) |   |-->Monitor "<default monitor>"
[    20.866] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    20.866] (==) Automatically adding devices
[    20.866] (==) Automatically enabling devices
[    20.895] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    20.895] 	Entry deleted from font path.
[    20.930] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    20.930] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    20.930] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    20.930] (II) Loader magic: 0x7e0280
[    20.930] (II) Module ABI versions:
[    20.930] 	X.Org ANSI C Emulation: 0.4
[    20.930] 	X.Org Video Driver: 10.0
[    20.930] 	X.Org XInput driver : 12.3
[    20.930] 	X.Org Server Extension : 5.0
[    20.931] (--) PCI:*(0:0:2:0) 8086:29c2:8086:29c2 rev 16, Mem @ 0xfeb00000/524288, 0xd0000000/268435456, 0xfe900000/1048576, I/O @ 0x0000e140/8
[    20.931] (II) Open ACPI successful (/var/run/acpid.socket)
[    20.931] (II) LoadModule: "extmod"
[    21.001] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    21.009] (II) Module extmod: vendor="X.Org Foundation"
[    21.009] 	compiled for 1.10.1, module version = 1.0.0
[    21.009] 	Module class: X.Org Server Extension
[    21.009] 	ABI class: X.Org Server Extension, version 5.0
[    21.009] (II) Loading extension MIT-SCREEN-SAVER
[    21.009] (II) Loading extension XFree86-VidModeExtension
[    21.009] (II) Loading extension XFree86-DGA
[    21.009] (II) Loading extension DPMS
[    21.009] (II) Loading extension XVideo
[    21.009] (II) Loading extension XVideo-MotionCompensation
[    21.009] (II) Loading extension X-Resource
[    21.009] (II) LoadModule: "dbe"
[    21.009] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    21.019] (II) Module dbe: vendor="X.Org Foundation"
[    21.019] 	compiled for 1.10.1, module version = 1.0.0
[    21.019] 	Module class: X.Org Server Extension
[    21.019] 	ABI class: X.Org Server Extension, version 5.0
[    21.019] (II) Loading extension DOUBLE-BUFFER
[    21.019] (II) LoadModule: "glx"
[    21.020] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    21.113] (II) Module glx: vendor="X.Org Foundation"
[    21.113] 	compiled for 1.10.1, module version = 1.0.0
[    21.113] 	ABI class: X.Org Server Extension, version 5.0
[    21.113] (==) AIGLX enabled
[    21.113] (II) Loading extension GLX
[    21.114] (II) LoadModule: "record"
[    21.114] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    21.123] (II) Module record: vendor="X.Org Foundation"
[    21.123] 	compiled for 1.10.1, module version = 1.13.0
[    21.123] 	Module class: X.Org Server Extension
[    21.123] 	ABI class: X.Org Server Extension, version 5.0
[    21.123] (II) Loading extension RECORD
[    21.123] (II) LoadModule: "dri"
[    21.123] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    21.124] (II) Module dri: vendor="X.Org Foundation"
[    21.124] 	compiled for 1.10.1, module version = 1.0.0
[    21.124] 	ABI class: X.Org Server Extension, version 5.0
[    21.124] (II) Loading extension XFree86-DRI
[    21.124] (II) LoadModule: "dri2"
[    21.124] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    21.127] (II) Module dri2: vendor="X.Org Foundation"
[    21.127] 	compiled for 1.10.1, module version = 1.2.0
[    21.127] 	ABI class: X.Org Server Extension, version 5.0
[    21.127] (II) Loading extension DRI2
[    21.127] (==) Matched intel as autoconfigured driver 0
[    21.127] (==) Matched vesa as autoconfigured driver 1
[    21.127] (==) Matched fbdev as autoconfigured driver 2
[    21.127] (==) Assigned the driver to the xf86ConfigLayout
[    21.127] (II) LoadModule: "intel"
[    21.128] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    21.138] (II) Module intel: vendor="X.Org Foundation"
[    21.138] 	compiled for 1.10.1, module version = 2.14.0
[    21.138] 	Module class: X.Org Video Driver
[    21.138] 	ABI class: X.Org Video Driver, version 10.0
[    21.138] (II) LoadModule: "vesa"
[    21.139] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    21.141] (II) Module vesa: vendor="X.Org Foundation"
[    21.141] 	compiled for 1.10.0, module version = 2.3.0
[    21.141] 	Module class: X.Org Video Driver
[    21.141] 	ABI class: X.Org Video Driver, version 10.0
[    21.141] (II) LoadModule: "fbdev"
[    21.141] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    21.151] (II) Module fbdev: vendor="X.Org Foundation"
[    21.151] 	compiled for 1.10.0, module version = 0.4.2
[    21.151] 	ABI class: X.Org Video Driver, version 10.0
[    21.151] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[    21.152] (II) VESA: driver for VESA chipsets: vesa
[    21.152] (II) FBDEV: driver for framebuffer: fbdev
[    21.152] (++) using VT number 7

[    21.154] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    21.154] (WW) Falling back to old probe method for vesa
[    21.154] (WW) Falling back to old probe method for fbdev
[    21.154] (II) Loading sub module "fbdevhw"
[    21.154] (II) LoadModule: "fbdevhw"
[    21.163] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    21.164] (II) Module fbdevhw: vendor="X.Org Foundation"
[    21.164] 	compiled for 1.10.1, module version = 0.0.2
[    21.164] 	ABI class: X.Org Video Driver, version 10.0
[    21.164] drmOpenDevice: node name is /dev/dri/card0
[    21.164] drmOpenDevice: open result is 9, (OK)
[    21.164] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    21.164] drmOpenDevice: node name is /dev/dri/card0
[    21.164] drmOpenDevice: open result is 9, (OK)
[    21.164] drmOpenByBusid: drmOpenMinor returns 9
[    21.164] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    21.164] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    21.164] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    21.164] (==) intel(0): RGB weight 888
[    21.164] (==) intel(0): Default visual is TrueColor
[    21.164] (II) intel(0): Integrated Graphics Chipset: Intel(R) G33
[    21.164] (--) intel(0): Chipset: "G33"
[    21.164] (**) intel(0): Relaxed fencing enabled
[    21.164] (**) intel(0): Tiling enabled
[    21.164] (**) intel(0): SwapBuffers wait enabled
[    21.164] (==) intel(0): video overlay key set to 0x101fe
[    21.202] (II) intel(0): Output VGA1 has no monitor section
[    21.222] (II) intel(0): EDID for output VGA1
[    21.222] (II) intel(0): Printing probed modes for output VGA1
[    21.222] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    21.222] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    21.222] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    21.222] (II) intel(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz)
[    21.222] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz)
[    21.222] (II) intel(0): Output VGA1 connected
[    21.222] (II) intel(0): Using fuzzy aspect match for initial modes
[    21.222] (II) intel(0): Output VGA1 using initial mode 1024x768
[    21.222] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    21.222] (II) intel(0): Kernel page flipping support detected, enabling
[    21.222] (==) intel(0): DPI set to (96, 96)
[    21.222] (II) Loading sub module "fb"
[    21.222] (II) LoadModule: "fb"
[    21.222] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.266] (II) Module fb: vendor="X.Org Foundation"
[    21.266] 	compiled for 1.10.1, module version = 1.0.0
[    21.266] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    21.266] (II) UnloadModule: "vesa"
[    21.266] (II) Unloading vesa
[    21.266] (II) UnloadModule: "fbdev"
[    21.266] (II) Unloading fbdev
[    21.266] (II) UnloadModule: "fbdevhw"
[    21.266] (II) Unloading fbdevhw
[    21.266] (==) Depth 24 pixmap format is 32 bpp
[    21.266] (==) intel(0): VideoRam: 262144 KB
[    21.266] (II) intel(0): [DRI2] Setup complete
[    21.266] (II) intel(0): [DRI2]   DRI driver: i915
[    21.266] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[    21.290] (II) UXA(0): Driver registered support for the following operations:
[    21.290] (II)         solid
[    21.290] (II)         copy
[    21.290] (II)         composite (RENDER acceleration)
[    21.290] (II)         put_image
[    21.290] (II)         get_image
[    21.290] (==) intel(0): Backing store disabled
[    21.290] (==) intel(0): Silken mouse enabled
[    21.301] (II) intel(0): Initializing HW Cursor
[    21.320] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    21.320] (==) intel(0): DPMS enabled
[    21.320] (==) intel(0): Intel XvMC decoder disabled
[    21.320] (II) intel(0): Set up textured video
[    21.320] (II) intel(0): Set up overlay video
[    21.320] (II) intel(0): direct rendering: DRI2 Enabled
[    21.320] (==) intel(0): hotplug detection: "enabled"
[    21.320] (--) RandR disabled
[    21.320] (II) Initializing built-in extension Generic Event Extension
[    21.320] (II) Initializing built-in extension SHAPE
[    21.320] (II) Initializing built-in extension MIT-SHM
[    21.320] (II) Initializing built-in extension XInputExtension
[    21.320] (II) Initializing built-in extension XTEST
[    21.320] (II) Initializing built-in extension BIG-REQUESTS
[    21.320] (II) Initializing built-in extension SYNC
[    21.320] (II) Initializing built-in extension XKEYBOARD
[    21.320] (II) Initializing built-in extension XC-MISC
[    21.320] (II) Initializing built-in extension SECURITY
[    21.320] (II) Initializing built-in extension XINERAMA
[    21.320] (II) Initializing built-in extension XFIXES
[    21.320] (II) Initializing built-in extension RENDER
[    21.320] (II) Initializing built-in extension RANDR
[    21.320] (II) Initializing built-in extension COMPOSITE
[    21.320] (II) Initializing built-in extension DAMAGE
[    21.320] (II) Initializing built-in extension GESTURE
[    21.338] (II) AIGLX: Trying DRI driver /usr/lib/dri/i915_dri.so
[    21.736] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    21.736] (II) AIGLX: enabled GLX_INTEL_swap_event
[    21.736] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    21.736] (II) AIGLX: enabled GLX_SGI_make_current_read
[    21.736] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    21.736] (II) AIGLX: Loaded and initialized i915
[    21.736] (II) GLX: Initialized DRI2 GL provider for screen 0
[    21.737] (II) intel(0): Setting screen physical size to 270 x 203
[    21.995] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    22.027] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    22.027] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.027] (II) LoadModule: "evdev"
[    22.045] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.279] (II) Module evdev: vendor="X.Org Foundation"
[    22.279] 	compiled for 1.10.0.902, module version = 2.6.0
[    22.279] 	Module class: X.Org XInput Driver
[    22.279] 	ABI class: X.Org XInput driver, version 12.3
[    22.279] (II) Using input driver 'evdev' for 'Power Button'
[    22.279] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.279] (**) Power Button: always reports core events
[    22.279] (**) Power Button: Device: "/dev/input/event2"
[    22.340] (--) Power Button: Found keys
[    22.340] (II) Power Button: Configuring as keyboard
[    22.340] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    22.340] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    22.340] (**) Option "xkb_rules" "evdev"
[    22.340] (**) Option "xkb_model" "pc105"
[    22.340] (**) Option "xkb_layout" "us"
[    22.340] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    22.340] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    22.340] (II) Using input driver 'evdev' for 'Video Bus'
[    22.340] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.340] (**) Video Bus: always reports core events
[    22.340] (**) Video Bus: Device: "/dev/input/event5"
[    22.380] (--) Video Bus: Found keys
[    22.380] (II) Video Bus: Configuring as keyboard
[    22.380] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5/event5"
[    22.380] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    22.380] (**) Option "xkb_rules" "evdev"
[    22.380] (**) Option "xkb_model" "pc105"
[    22.380] (**) Option "xkb_layout" "us"
[    22.381] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    22.381] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.382] (II) Using input driver 'evdev' for 'Power Button'
[    22.382] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.382] (**) Power Button: always reports core events
[    22.382] (**) Power Button: Device: "/dev/input/event1"
[    22.420] (--) Power Button: Found keys
[    22.420] (II) Power Button: Configuring as keyboard
[    22.420] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    22.420] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    22.420] (**) Option "xkb_rules" "evdev"
[    22.420] (**) Option "xkb_model" "pc105"
[    22.420] (**) Option "xkb_layout" "us"
[    22.420] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[    22.420] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    22.420] (II) Using input driver 'evdev' for 'Sleep Button'
[    22.420] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.420] (**) Sleep Button: always reports core events
[    22.420] (**) Sleep Button: Device: "/dev/input/event0"
[    22.460] (--) Sleep Button: Found keys
[    22.460] (II) Sleep Button: Configuring as keyboard
[    22.460] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0/event0"
[    22.460] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    22.460] (**) Option "xkb_rules" "evdev"
[    22.460] (**) Option "xkb_model" "pc105"
[    22.460] (**) Option "xkb_layout" "us"
[    22.462] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event6)
[    22.462] (II) No input driver/identifier specified (ignoring)
[    22.463] (II) config/udev: Adding input device Dell Dell USB Optical Mouse (/dev/input/event3)
[    22.463] (**) Dell Dell USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    22.463] (II) Using input driver 'evdev' for 'Dell Dell USB Optical Mouse'
[    22.463] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.463] (**) Dell Dell USB Optical Mouse: always reports core events
[    22.463] (**) Dell Dell USB Optical Mouse: Device: "/dev/input/event3"
[    22.500] (--) Dell Dell USB Optical Mouse: Found 3 mouse buttons
[    22.500] (--) Dell Dell USB Optical Mouse: Found scroll wheel(s)
[    22.500] (--) Dell Dell USB Optical Mouse: Found relative axes
[    22.500] (--) Dell Dell USB Optical Mouse: Found x and y relative axes
[    22.500] (II) Dell Dell USB Optical Mouse: Configuring as mouse
[    22.500] (II) Dell Dell USB Optical Mouse: Adding scrollwheel support
[    22.500] (**) Dell Dell USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    22.500] (**) Dell Dell USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    22.500] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input3/event3"
[    22.500] (II) XINPUT: Adding extended input device "Dell Dell USB Optical Mouse" (type: MOUSE)
[    22.500] (II) Dell Dell USB Optical Mouse: initialized for relative axes.
[    22.500] (**) Dell Dell USB Optical Mouse: (accel) keeping acceleration scheme 1
[    22.500] (**) Dell Dell USB Optical Mouse: (accel) acceleration profile 0
[    22.500] (**) Dell Dell USB Optical Mouse: (accel) acceleration factor: 2.000
[    22.500] (**) Dell Dell USB Optical Mouse: (accel) acceleration threshold: 4
[    22.500] (II) config/udev: Adding input device Dell Dell USB Optical Mouse (/dev/input/mouse0)
[    22.500] (II) No input driver/identifier specified (ignoring)
[    22.501] (II) config/udev: Adding input device Dell Dell USB Keyboard (/dev/input/event4)
[    22.501] (**) Dell Dell USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    22.501] (II) Using input driver 'evdev' for 'Dell Dell USB Keyboard'
[    22.501] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.501] (**) Dell Dell USB Keyboard: always reports core events
[    22.501] (**) Dell Dell USB Keyboard: Device: "/dev/input/event4"
[    22.550] (--) Dell Dell USB Keyboard: Found keys
[    22.550] (II) Dell Dell USB Keyboard: Configuring as keyboard
[    22.550] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input4/event4"
[    22.550] (II) XINPUT: Adding extended input device "Dell Dell USB Keyboard" (type: KEYBOARD)
[    22.550] (**) Option "xkb_rules" "evdev"
[    22.550] (**) Option "xkb_model" "pc105"
[    22.550] (**) Option "xkb_layout" "us"
```

---

### Post by Toz on 2011-06-14
@happyisland - X is not automatically probing resultions greater than 1024x768.
> [    21.222] (II) intel(0): Printing probed modes for output VGA1
[    21.222] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    21.222] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    21.222] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    21.222] (II) intel(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz)
[    21.222] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz)

What make/model of monitor do you have?

You can also try to re-initialize X using the old method to see if it can create a working xorg.conf file for you. Follow the directions from this post: [http://ubuntuforums.org/showpost.php?p=4289996&postcount=1]("http://ubuntuforums.org/showpost.php?p=4289996&postcount=1")

---

### Post by BicyclerBoy on 2011-06-15
Your Xorg.0.log does not seem to indicate EDID probing failure but seems to be missing display info.
Do you have a
/etc/X11/xorg.conf
file from previous setup ?

It must be a good idea to dump the VGA for DVI cable.
If you can get the monitor/TV? recognised correctly the problem may go away.

---

### Post by happyisland on 2011-06-15
> **Toz said:**
> @happyisland - X is not automatically probing resultions greater than 1024x768.


What make/model of monitor do you have?

You can also try to re-initialize X using the old method to see if it can create a working xorg.conf file for you. Follow the directions from this post: [http://ubuntuforums.org/showpost.php?p=4289996&postcount=1]("http://ubuntuforums.org/showpost.php?p=4289996&postcount=1")

The monitor is an old Dell 2407. Unfortunately I'm stuck with using the VGA cable, since the workstation it's connected to is VGA only. 

I also checked your link, but there's a big warning at the top that says it's not expected to work on anything after Gutsy (and I'm running Natty).

Pretty weird that it's such an issue in Ubuntu to connect a new VGA monitor...

---

### Post by happyisland on 2011-06-15
> **BicyclerBoy said:**
> Your Xorg.0.log does not seem to indicate EDID probing failure but seems to be missing display info.
Do you have a
/etc/X11/xorg.conf
file from previous setup ?

It must be a good idea to dump the VGA for DVI cable.
If you can get the monitor/TV? recognised correctly the problem may go away.

I can get the monitor to work correctly for the session if I do these three steps:
cvt 1920 1200 60
xrandr --newmode (PASTE MODELINE OUTPUT FROM PREVIOUS HERE)
xrandr --addmode VGA1 "1920x1200_60.00"

The problem is that if I restart the settings revert to 1024x768. 

How do I make these changes permanent?

---

### Post by Toz on 2011-06-15
Here is one solution using xrandr: [http://www.myokyawhtun.com/ubuntu-linux/how-to-change-custom-resolution-in-ubuntu-10.html]("http://www.myokyawhtun.com/ubuntu-linux/how-to-change-custom-resolution-in-ubuntu-10.html")

Here is a solution involving an X configuration file. Since xorg.conf os being deprecated, I would suggest adding that code to /usr/share/X11/xorg.conf.d/ in a file called 20-monitor.conf (you'll probably need to create the file): [http://ubuntuforums.org/showpost.php?p=9800808&postcount=2]("http://ubuntuforums.org/showpost.php?p=9800808&postcount=2")

---

### Post by happyisland on 2011-06-17
@Toz, thanks for the help. I tried the easier-looking solution in your second link first, but that didn't appear to do anything so I removed the file. The good news is that following the instructions on your first link I was able to get the monitor to work. As instructed, I created a ~/.xprofile file with the proper commands in it.

It's inelegant - looks funky as hell on startup - but it works and I can get back to doing my job instead of monkeying around with the PC. 

I really, really appreciate your help in getting my issue solved.

---

### Post by Toz on 2011-06-17
Great, glad to hear it worked out. If you don't mind, can you flag this thread as solved using the Thread Tools link above?
Thanks.

---

### Post by happyisland on 2011-06-21
I would be happy to, but since I'm just a humble thread hijacker I don't think I'm allowed to. Thanks again for the help!

---

