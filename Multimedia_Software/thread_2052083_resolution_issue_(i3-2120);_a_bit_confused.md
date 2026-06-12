---
title: "resolution issue (i3-2120); a bit confused"
date: 2012-09-02
forum: Multimedia Software
---

### Post by Wim Sturkenboom on 2012-09-02
I had a Ubuntu 10.04 / WinXP dual boot system with GT520 video card connected to a Acer X243W via VGA. In both OSes I ran 1920x1200@60Hz (and the monitor confirmed that); under Ubuntu, I used a driver from the nVidia website (never got the ones from the repositories working).

Bought a new PC with I3-2120 dual booting Win7 and Ubuntu 12.04. Same monitor connected to the onboad VGA (I3-2120). In Win7, 1920x1200@60Hz (and 75kHz). In Ubuntu however, 1024x768.

And the only options are (were) 1024x768 and 800x600 in the monitor section in system settings.
Created an xorg.conf, added a modeline for 1920x1200@60Hz using [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl) and added the mode and the monitor tells me 'no signal'. OK, so either no signal (driver problem?) or maybe out-of-range, not sure what it's trying to tell me.

Only after generating a modeline for 1920x1200@50Hz, I now have a screen that looks like 1920x1200. This is based on the shape of the dash icon and firefox icon who now look more or less round instead of oval.
However the monitor tells me that it's 1600x1200 (62kHz, 49Hz).

1)
So what is going on here?
2)
And why does get-edid tell me that the monitor/videocard combo does not support DDC1 nor DDC2 transfers while Win7 has no issue adjusting to another monitor without user interference? Is there another 'protocol'?


xorg logfile
```

[    33.544] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    33.544] X Protocol Version 11, Revision 0
[    33.544] Build Operating System: Linux 2.6.42-26-generic x86_64 Ubuntu
[    33.544] Current Operating System: Linux i3-2120 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64
[    33.544] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-29-generic root=UUID=2e61cbc5-d982-4ada-8af7-cbdea09bb295 ro text quiet splash vt.handoff=7
[    33.544] Build Date: 04 August 2012  01:51:23AM
[    33.544] xorg-server 2:1.11.4-0ubuntu10.7 (For technical support please see http://www.ubuntu.com/support) 
[    33.544] Current version of pixman: 0.24.4
[    33.544] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    33.544] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    33.544] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Sep  2 19:06:59 2012
[    33.544] (==) Using config file: "/etc/X11/xorg.conf"
[    33.544] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    33.555] (==) ServerLayout "Layout0"
[    33.555] (**) |-->Screen "Screen0" (0)
[    33.555] (**) |   |-->Monitor "Monitor0"
[    33.555] (**) |   |-->Device "Device0"
[    33.555] (==) Automatically adding devices
[    33.555] (==) Automatically enabling devices
[    33.555] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    33.555] 	Entry deleted from font path.
[    33.555] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    33.555] 	Entry deleted from font path.
[    33.555] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    33.555] 	Entry deleted from font path.
[    33.555] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    33.555] 	Entry deleted from font path.
[    33.555] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    33.555] 	Entry deleted from font path.
[    33.555] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    33.555] 	Entry deleted from font path.
[    33.555] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    33.555] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    33.555] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    33.555] (II) Loader magic: 0x7f66420cdb00
[    33.555] (II) Module ABI versions:
[    33.555] 	X.Org ANSI C Emulation: 0.4
[    33.555] 	X.Org Video Driver: 11.0
[    33.555] 	X.Org XInput driver : 16.0
[    33.555] 	X.Org Server Extension : 6.0
[    33.555] (--) PCI:*(0:0:2:0) 8086:0102:1849:0102 rev 9, Mem @ 0xf7800000/4194304, 0xe0000000/268435456, I/O @ 0x0000f000/64
[    33.555] (II) Open ACPI successful (/var/run/acpid.socket)
[    33.555] (II) LoadModule: "extmod"
[    33.570] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    33.570] (II) Module extmod: vendor="X.Org Foundation"
[    33.570] 	compiled for 1.11.3, module version = 1.0.0
[    33.570] 	Module class: X.Org Server Extension
[    33.570] 	ABI class: X.Org Server Extension, version 6.0
[    33.570] (II) Loading extension MIT-SCREEN-SAVER
[    33.570] (II) Loading extension XFree86-VidModeExtension
[    33.570] (II) Loading extension XFree86-DGA
[    33.570] (II) Loading extension DPMS
[    33.570] (II) Loading extension XVideo
[    33.570] (II) Loading extension XVideo-MotionCompensation
[    33.570] (II) Loading extension X-Resource
[    33.570] (II) LoadModule: "dbe"
[    33.571] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    33.571] (II) Module dbe: vendor="X.Org Foundation"
[    33.571] 	compiled for 1.11.3, module version = 1.0.0
[    33.571] 	Module class: X.Org Server Extension
[    33.571] 	ABI class: X.Org Server Extension, version 6.0
[    33.571] (II) Loading extension DOUBLE-BUFFER
[    33.571] (II) LoadModule: "glx"
[    33.571] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    33.571] (II) Module glx: vendor="X.Org Foundation"
[    33.571] 	compiled for 1.11.3, module version = 1.0.0
[    33.571] 	ABI class: X.Org Server Extension, version 6.0
[    33.571] (==) AIGLX enabled
[    33.571] (II) Loading extension GLX
[    33.571] (II) LoadModule: "record"
[    33.571] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    33.571] (II) Module record: vendor="X.Org Foundation"
[    33.571] 	compiled for 1.11.3, module version = 1.13.0
[    33.571] 	Module class: X.Org Server Extension
[    33.571] 	ABI class: X.Org Server Extension, version 6.0
[    33.571] (II) Loading extension RECORD
[    33.571] (II) LoadModule: "dri"
[    33.571] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    33.571] (II) Module dri: vendor="X.Org Foundation"
[    33.571] 	compiled for 1.11.3, module version = 1.0.0
[    33.571] 	ABI class: X.Org Server Extension, version 6.0
[    33.571] (II) Loading extension XFree86-DRI
[    33.571] (II) LoadModule: "dri2"
[    33.571] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    33.571] (II) Module dri2: vendor="X.Org Foundation"
[    33.571] 	compiled for 1.11.3, module version = 1.2.0
[    33.571] 	ABI class: X.Org Server Extension, version 6.0
[    33.571] (II) Loading extension DRI2
[    33.571] (==) Matched intel as autoconfigured driver 0
[    33.571] (==) Matched vesa as autoconfigured driver 1
[    33.571] (==) Matched fbdev as autoconfigured driver 2
[    33.571] (==) Assigned the driver to the xf86ConfigLayout
[    33.571] (II) LoadModule: "intel"
[    33.572] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    33.572] (II) Module intel: vendor="X.Org Foundation"
[    33.572] 	compiled for 1.11.3, module version = 2.17.0
[    33.572] 	Module class: X.Org Video Driver
[    33.572] 	ABI class: X.Org Video Driver, version 11.0
[    33.572] (II) LoadModule: "vesa"
[    33.572] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    33.572] (II) Module vesa: vendor="X.Org Foundation"
[    33.572] 	compiled for 1.11.3, module version = 2.3.0
[    33.572] 	Module class: X.Org Video Driver
[    33.572] 	ABI class: X.Org Video Driver, version 11.0
[    33.572] (II) LoadModule: "fbdev"
[    33.572] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    33.572] (II) Module fbdev: vendor="X.Org Foundation"
[    33.572] 	compiled for 1.11.3, module version = 0.4.2
[    33.572] 	ABI class: X.Org Video Driver, version 11.0
[    33.572] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    33.572] (II) VESA: driver for VESA chipsets: vesa
[    33.572] (II) FBDEV: driver for framebuffer: fbdev
[    33.572] (++) using VT number 7

[    33.573] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    33.573] (WW) Falling back to old probe method for vesa
[    33.573] (WW) Falling back to old probe method for fbdev
[    33.573] (II) Loading sub module "fbdevhw"
[    33.573] (II) LoadModule: "fbdevhw"
[    33.574] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    33.574] (II) Module fbdevhw: vendor="X.Org Foundation"
[    33.574] 	compiled for 1.11.3, module version = 0.0.2
[    33.574] 	ABI class: X.Org Video Driver, version 11.0
[    33.574] drmOpenDevice: node name is /dev/dri/card0
[    33.574] drmOpenDevice: open result is 9, (OK)
[    33.574] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    33.574] drmOpenDevice: node name is /dev/dri/card0
[    33.574] drmOpenDevice: open result is 9, (OK)
[    33.574] drmOpenByBusid: drmOpenMinor returns 9
[    33.574] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    33.574] (**) intel(0): Depth 24, (--) framebuffer bpp 32
[    33.574] (==) intel(0): RGB weight 888
[    33.574] (==) intel(0): Default visual is TrueColor
[    33.574] (II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge Desktop (GT1)
[    33.574] (--) intel(0): Chipset: "Sandybridge Desktop (GT1)"
[    33.574] (**) intel(0): Relaxed fencing enabled
[    33.574] (**) intel(0): Wait on SwapBuffers? enabled
[    33.574] (**) intel(0): Triple buffering? enabled
[    33.574] (**) intel(0): Framebuffer tiled
[    33.574] (**) intel(0): Pixmaps tiled
[    33.574] (**) intel(0): 3D buffers tiled
[    33.574] (**) intel(0): SwapBuffers wait enabled
[    33.574] (==) intel(0): video overlay key set to 0x101fe
[    33.576] (II) intel(0): Output VGA1 using monitor section Monitor0
[    33.579] (II) intel(0): EDID for output VGA1
[    33.579] (II) intel(0): Printing probed modes for output VGA1
[    33.579] (II) intel(0): Modeline "1920x1200@50"x50.0  164.50  1920 1952 2576 2608  1200 1225 1235 1261 (63.1 kHz)
[    33.579] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    33.579] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    33.579] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    33.579] (II) intel(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz)
[    33.579] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz)
[    33.579] (II) intel(0): Output VGA1 connected
[    33.579] (II) intel(0): Using user preference for initial modes
[    33.579] (II) intel(0): Output VGA1 using initial mode 1920x1200@50
[    33.579] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    33.579] (II) intel(0): Kernel page flipping support detected, enabling
[    33.579] (==) intel(0): DPI set to (96, 96)
[    33.579] (II) Loading sub module "fb"
[    33.579] (II) LoadModule: "fb"
[    33.579] (II) Loading /usr/lib/xorg/modules/libfb.so
[    33.579] (II) Module fb: vendor="X.Org Foundation"
[    33.579] 	compiled for 1.11.3, module version = 1.0.0
[    33.579] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    33.579] (II) Loading sub module "dri2"
[    33.579] (II) LoadModule: "dri2"
[    33.579] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    33.579] (II) Module dri2: vendor="X.Org Foundation"
[    33.579] 	compiled for 1.11.3, module version = 1.2.0
[    33.579] 	ABI class: X.Org Server Extension, version 6.0
[    33.579] (II) UnloadModule: "vesa"
[    33.579] (II) Unloading vesa
[    33.579] (II) UnloadModule: "fbdev"
[    33.579] (II) Unloading fbdev
[    33.579] (II) UnloadModule: "fbdevhw"
[    33.579] (II) Unloading fbdevhw
[    33.579] (==) Depth 24 pixmap format is 32 bpp
[    33.579] (II) intel(0): [DRI2] Setup complete
[    33.579] (II) intel(0): [DRI2]   DRI driver: i965
[    33.579] (II) intel(0): Allocated new frame buffer 1920x1200 stride 7680, tiled
[    33.580] (II) UXA(0): Driver registered support for the following operations:
[    33.580] (II)         solid
[    33.580] (II)         copy
[    33.580] (II)         composite (RENDER acceleration)
[    33.580] (II)         put_image
[    33.580] (II)         get_image
[    33.580] (==) intel(0): Backing store disabled
[    33.580] (==) intel(0): Silken mouse enabled
[    33.580] (II) intel(0): Initializing HW Cursor
[    33.895] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    33.895] (**) intel(0): DPMS enabled
[    33.895] (==) intel(0): Intel XvMC decoder enabled
[    33.895] (II) intel(0): Set up textured video
[    33.895] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    33.895] (II) intel(0): direct rendering: DRI2 Enabled
[    33.895] (==) intel(0): hotplug detection: "enabled"
[    33.895] (--) RandR disabled
[    33.895] (II) Initializing built-in extension Generic Event Extension
[    33.895] (II) Initializing built-in extension SHAPE
[    33.895] (II) Initializing built-in extension MIT-SHM
[    33.895] (II) Initializing built-in extension XInputExtension
[    33.895] (II) Initializing built-in extension XTEST
[    33.895] (II) Initializing built-in extension BIG-REQUESTS
[    33.895] (II) Initializing built-in extension SYNC
[    33.895] (II) Initializing built-in extension XKEYBOARD
[    33.895] (II) Initializing built-in extension XC-MISC
[    33.895] (II) Initializing built-in extension SECURITY
[    33.895] (II) Initializing built-in extension XINERAMA
[    33.895] (II) Initializing built-in extension XFIXES
[    33.895] (II) Initializing built-in extension RENDER
[    33.895] (II) Initializing built-in extension RANDR
[    33.895] (II) Initializing built-in extension COMPOSITE
[    33.895] (II) Initializing built-in extension DAMAGE
[    33.900] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    33.900] (II) AIGLX: enabled GLX_INTEL_swap_event
[    33.900] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    33.900] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    33.900] (II) AIGLX: Loaded and initialized i965
[    33.900] (II) GLX: Initialized DRI2 GL provider for screen 0
[    33.900] (II) intel(0): Setting screen physical size to 508 x 317
[    33.904] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    33.906] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    33.906] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    33.906] (II) LoadModule: "evdev"
[    33.906] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    33.906] (II) Module evdev: vendor="X.Org Foundation"
[    33.906] 	compiled for 1.11.3, module version = 2.7.0
[    33.906] 	Module class: X.Org XInput Driver
[    33.906] 	ABI class: X.Org XInput driver, version 16.0
[    33.906] (II) Using input driver 'evdev' for 'Power Button'
[    33.906] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    33.906] (**) Power Button: always reports core events
[    33.906] (**) evdev: Power Button: Device: "/dev/input/event1"
[    33.906] (--) evdev: Power Button: Vendor 0 Product 0x1
[    33.906] (--) evdev: Power Button: Found keys
[    33.906] (II) evdev: Power Button: Configuring as keyboard
[    33.906] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    33.906] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    33.906] (**) Option "xkb_rules" "evdev"
[    33.906] (**) Option "xkb_model" "pc105"
[    33.906] (**) Option "xkb_layout" "za"
[    33.907] (II) XKB: reuse xkmfile /var/lib/xkb/server-BCF7C4B78F6775858E983A1661EA7F5FD69F5903.xkm
[    33.908] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    33.908] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    33.908] (II) Using input driver 'evdev' for 'Video Bus'
[    33.908] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    33.908] (**) Video Bus: always reports core events
[    33.908] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    33.908] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    33.908] (--) evdev: Video Bus: Found keys
[    33.908] (II) evdev: Video Bus: Configuring as keyboard
[    33.908] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5/event5"
[    33.908] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    33.908] (**) Option "xkb_rules" "evdev"
[    33.908] (**) Option "xkb_model" "pc105"
[    33.908] (**) Option "xkb_layout" "za"
[    33.908] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    33.908] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    33.908] (II) Using input driver 'evdev' for 'Power Button'
[    33.908] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    33.908] (**) Power Button: always reports core events
[    33.908] (**) evdev: Power Button: Device: "/dev/input/event0"
[    33.908] (--) evdev: Power Button: Vendor 0 Product 0x1
[    33.908] (--) evdev: Power Button: Found keys
[    33.908] (II) evdev: Power Button: Configuring as keyboard
[    33.908] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    33.908] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    33.908] (**) Option "xkb_rules" "evdev"
[    33.908] (**) Option "xkb_model" "pc105"
[    33.908] (**) Option "xkb_layout" "za"
[    33.909] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event6)
[    33.909] (II) No input driver specified, ignoring this device.
[    33.909] (II) This device may have been added with another device file.
[    33.909] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event7)
[    33.909] (II) No input driver specified, ignoring this device.
[    33.909] (II) This device may have been added with another device file.
[    33.909] (II) config/udev: Adding input device HDA Intel PCH Line-Out (/dev/input/event8)
[    33.909] (II) No input driver specified, ignoring this device.
[    33.909] (II) This device may have been added with another device file.
[    33.909] (II) config/udev: Adding input device Genius Optical Mouse (/dev/input/event2)
[    33.909] (**) Genius Optical Mouse: Applying InputClass "evdev pointer catchall"
[    33.909] (II) Using input driver 'evdev' for 'Genius Optical Mouse'
[    33.909] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    33.909] (**) Genius Optical Mouse: always reports core events
[    33.909] (**) evdev: Genius Optical Mouse: Device: "/dev/input/event2"
[    33.909] (--) evdev: Genius Optical Mouse: Vendor 0x458 Product 0x3a
[    33.909] (--) evdev: Genius Optical Mouse: Found 3 mouse buttons
[    33.909] (--) evdev: Genius Optical Mouse: Found scroll wheel(s)
[    33.909] (--) evdev: Genius Optical Mouse: Found relative axes
[    33.909] (--) evdev: Genius Optical Mouse: Found x and y relative axes
[    33.909] (II) evdev: Genius Optical Mouse: Configuring as mouse
[    33.909] (II) evdev: Genius Optical Mouse: Adding scrollwheel support
[    33.909] (**) evdev: Genius Optical Mouse: YAxisMapping: buttons 4 and 5
[    33.909] (**) evdev: Genius Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    33.909] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input2/event2"
[    33.909] (II) XINPUT: Adding extended input device "Genius Optical Mouse" (type: MOUSE, id 9)
[    33.909] (II) evdev: Genius Optical Mouse: initialized for relative axes.
[    33.909] (**) Genius Optical Mouse: (accel) keeping acceleration scheme 1
[    33.909] (**) Genius Optical Mouse: (accel) acceleration profile 0
[    33.909] (**) Genius Optical Mouse: (accel) acceleration factor: 2.000
[    33.909] (**) Genius Optical Mouse: (accel) acceleration threshold: 4
[    33.909] (II) config/udev: Adding input device Genius Optical Mouse (/dev/input/mouse0)
[    33.909] (II) No input driver specified, ignoring this device.
[    33.909] (II) This device may have been added with another device file.
[    33.910] (II) config/udev: Adding input device   USB Keyboard (/dev/input/event3)
[    33.910] (**)   USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    33.910] (II) Using input driver 'evdev' for '  USB Keyboard'
[    33.910] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    33.910] (**)   USB Keyboard: always reports core events
[    33.910] (**) evdev:   USB Keyboard: Device: "/dev/input/event3"
[    33.910] (--) evdev:   USB Keyboard: Vendor 0x4d9 Product 0x1503
[    33.910] (--) evdev:   USB Keyboard: Found keys
[    33.910] (II) evdev:   USB Keyboard: Configuring as keyboard
[    33.910] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input3/event3"
[    33.910] (II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD, id 10)
[    33.910] (**) Option "xkb_rules" "evdev"
[    33.910] (**) Option "xkb_model" "pc105"
[    33.910] (**) Option "xkb_layout" "za"
[    33.910] (II) config/udev: Adding input device   USB Keyboard (/dev/input/event4)
[    33.910] (**)   USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    33.910] (II) Using input driver 'evdev' for '  USB Keyboard'
[    33.910] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    33.910] (**)   USB Keyboard: always reports core events
[    33.910] (**) evdev:   USB Keyboard: Device: "/dev/input/event4"
[    33.910] (--) evdev:   USB Keyboard: Vendor 0x4d9 Product 0x1503
[    33.910] (--) evdev:   USB Keyboard: Found keys
[    33.910] (II) evdev:   USB Keyboard: Configuring as keyboard
[    33.910] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.1/input/input4/event4"
[    33.910] (II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD, id 11)
[    33.910] (**) Option "xkb_rules" "evdev"
[    33.910] (**) Option "xkb_model" "pc105"
[    33.910] (**) Option "xkb_layout" "za"
[    55.444] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[    56.461] (II) XKB: reuse xkmfile /var/lib/xkb/server-46A88BF1E1D409377117604E95C2D723F90517D8.xkm
[    98.406] (II) intel(0): Allocated new frame buffer 1920x1200 stride 7680, tiled
[   149.320] (II) AIGLX: Suspending AIGLX clients for VT switch
[   197.428] (II) config/udev: removing device Genius Optical Mouse
[   197.429] (II) evdev: Genius Optical Mouse: Close
[   197.429] (II) UnloadModule: "evdev"
[   197.429] (II) Unloading evdev
[   198.951] (II) config/udev: Adding input device Genius Optical Mouse (/dev/input/event2)
[   198.951] (**) Genius Optical Mouse: Applying InputClass "evdev pointer catchall"
[   198.951] (II) Using input driver 'evdev' for 'Genius Optical Mouse'
[   198.951] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   198.951] (**) Genius Optical Mouse: always reports core events
[   198.951] (**) evdev: Genius Optical Mouse: Device: "/dev/input/event2"
[   198.951] (--) evdev: Genius Optical Mouse: Vendor 0x458 Product 0x3a
[   198.951] (--) evdev: Genius Optical Mouse: Found 3 mouse buttons
[   198.951] (--) evdev: Genius Optical Mouse: Found scroll wheel(s)
[   198.951] (--) evdev: Genius Optical Mouse: Found relative axes
[   198.951] (--) evdev: Genius Optical Mouse: Found x and y relative axes
[   198.952] (II) evdev: Genius Optical Mouse: Configuring as mouse
[   198.952] (II) evdev: Genius Optical Mouse: Adding scrollwheel support
[   198.952] (**) evdev: Genius Optical Mouse: YAxisMapping: buttons 4 and 5
[   198.952] (**) evdev: Genius Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   198.952] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input9/event2"
[   198.952] (II) XINPUT: Adding extended input device "Genius Optical Mouse" (type: MOUSE, id 9)
[   198.952] (II) evdev: Genius Optical Mouse: initialized for relative axes.
[   198.952] (**) Genius Optical Mouse: (accel) keeping acceleration scheme 1
[   198.952] (**) Genius Optical Mouse: (accel) acceleration profile 0
[   198.952] (**) Genius Optical Mouse: (accel) acceleration factor: 2.000
[   198.952] (**) Genius Optical Mouse: (accel) acceleration threshold: 4
[   198.952] (II) config/udev: Adding input device Genius Optical Mouse (/dev/input/mouse0)
[   198.952] (II) No input driver specified, ignoring this device.
[   198.952] (II) This device may have been added with another device file.
[   425.517] (II) Open ACPI successful (/var/run/acpid.socket)
[   425.517] (II) AIGLX: Resuming AIGLX clients after VT switch
[  1351.659] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[  1358.605] (II) intel(0): Allocated new frame buffer 1920x1200 stride 7680, tiled

```

xorg.conf
```


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
EndSection

Section "Files"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Acer"
    ModelName      "X243W"
    HorizSync       28.0 - 76.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
#    Modeline "1920x1200@55" 186.84 1920 1952 2656 2688 1200 1225 1236 1261
    Modeline "1920x1200@50" 164.50 1920 1952 2576 2608 1200 1225 1235 1261
#    Modeline "1920x1200@60" 210.68 1920 1952 2752 2784 1200 1224 1236 1261
#    Modeline "1920x1200@59" 205.79 1920 1952 2728 2760 1200 1224 1236 1261
EndSection

Section "Device"

#    Driver         "nvidia"
    Identifier     "Device0"
#    Driver         "nvidia"
    VendorName     "Intel"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Modes      "1920x1200@50"
#        Modes      "1680x1050"
        Depth       24
    EndSubSection
EndSection

```

get-edid output
```

get-edid: get-edid version 2.0.0

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
	Function supported
	Call successful

	VBE version 300
	VBE string at 0x11100 "Intel(R) Sandybridge/Ivybridge Graphics Chipset Accelerated VGA BIOS"

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

```

---

### Post by oldfred on 2012-09-02
It looks like you are using the Intel driver.

Is your system one of these?
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

NVIDIA Confirms It's Working On Optimus Linux Support - Aug 31, 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY)

---

### Post by Wim Sturkenboom on 2012-09-03
> 
Is your system one of these?

Not that I'm aware of; it's a H61 based motherboard ([Asrock H61M-VS](http://www.asrock.com/mb/overview.asp?model=h61m-vs)). The GT520 is not installed (yet); might happen at a later stage. So no nVidia involved to my knowledge.

---

### Post by oldfred on 2012-09-03
I know with nVidia you need the nomodeset parameter until you get the nVidia drivers installed. But with the Intel drivers on the i3, I am not sure what if anything is required.

---

### Post by Wim Sturkenboom on 2012-09-09
A stupid VGA cable ](*,)

Replaced the cable and it now behaves. Still wondering why Win7 did not have the problem but I actually do not care.

---

