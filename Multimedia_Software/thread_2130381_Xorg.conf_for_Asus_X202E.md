---
title: "Xorg.conf for Asus X202E"
date: 2013-03-29
forum: Multimedia Software
---

### Post by titansmc on 2013-03-29
Hi guys, I just got my new laptop and after installing the wired network driver as following:

sudo apt-get install linux-backports-modules-cw-3.6-quantal-generic

I rebooted the box from command line:

josep@josep-X202E:~$ sudo reboot 

And not sure if it is due to the driver but the problem is that I am not able to get into graphical environment, there is no xorg.conf .

So, I am wondering if someone could post the default xorg.cong. I know, it was my bad, because I did not backed up the file before doing things :)

Thanks, I would appreciate any kind of help!!

Btw, I tryed dpkg-reconfigure xserver-xorg but it did not help.

---

### Post by MacOsX74 on 2013-03-29
Have you tried.
$ sudo Xorg -configure

---

### Post by Yellow Pasque on 2013-03-29
There is no xorg.conf by default these days. Post your /var/log/Xorg.0.log

---

### Post by titansmc on 2013-04-02
Here is the output from the Xorg.0.log But now I am confused, because after installing ethernet driver, It created another kernel version in which ethernet card is working but not sound card neither touch screen .... So I am able to start up Ubuntu with the latest update of the kernel with ethernet card support, but with no sound on it, and with the first entry entry for kernel works everything except ethernet card, just like it came out of the box.

[QUOTE][QUOTE][QUOTE] root@josep-X202E:/home/josep# cat /var/log/Xorg.0.log[    14.244] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[    14.244] X Protocol Version 11, Revision 0
[    14.244] Build Operating System: Linux 3.2.0-32-generic x86_64 Ubuntu
[    14.244] Current Operating System: Linux josep-X202E 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64
[    14.244] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-17-generic root=UUID=bd43a546-3bea-460b-8b59-c50bd070e0bd ro quiet splash vt.handoff=7
[    14.244] Build Date: 27 November 2012  07:44:35AM
[    14.244] xorg-server 2:1.13.0-0ubuntu6.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    14.244] Current version of pixman: 0.26.0
[    14.244] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    14.244] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.244] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Apr  2 16:02:00 2013
[    14.244] (==) Using config file: "/etc/X11/xorg.conf"
[    14.244] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.320] (==) ServerLayout "X.org Configured"
[    14.320] (**) |-->Screen "Screen0" (0)
[    14.320] (**) |   |-->Monitor "Monitor0"
[    14.321] (**) |   |-->Device "Card0"
[    14.321] (**) |-->Screen "Screen1" (1)
[    14.321] (**) |   |-->Monitor "Monitor1"
[    14.321] (**) |   |-->Device "Card1"
[    14.321] (**) |-->Screen "Screen2" (2)
[    14.321] (**) |   |-->Monitor "Monitor2"
[    14.321] (**) |   |-->Device "Card2"
[    14.321] (**) |-->Screen "Screen3" (3)
[    14.321] (**) |   |-->Monitor "Monitor3"
[    14.321] (**) |   |-->Device "Card3"
[    14.321] (**) |-->Input Device "Mouse0"
[    14.321] (**) |-->Input Device "Keyboard0"
[    14.321] (==) Automatically adding devices
[    14.321] (==) Automatically enabling devices
[    14.321] (==) Automatically adding GPU devices
[    14.393] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.393] 	Entry deleted from font path.
[    14.393] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    14.393] 	Entry deleted from font path.
[    14.393] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    14.393] 	Entry deleted from font path.
[    14.404] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    14.404] 	Entry deleted from font path.
[    14.404] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    14.404] 	Entry deleted from font path.
[    14.404] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    14.404] 	Entry deleted from font path.
[    14.404] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.404] 	Entry deleted from font path.
[    14.404] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    14.404] 	Entry deleted from font path.
[    14.404] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    14.404] 	Entry deleted from font path.
[    14.404] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    14.404] 	Entry deleted from font path.
[    14.404] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    14.404] 	Entry deleted from font path.
[    14.404] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    14.404] 	Entry deleted from font path.
[    14.404] (**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    14.404] (**) ModulePath set to "/usr/lib/xorg/modules"
[    14.404] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    14.404] (WW) Disabling Mouse0
[    14.404] (WW) Disabling Keyboard0
[    14.404] (II) Loader magic: 0x7f14019ecc40
[    14.404] (II) Module ABI versions:
[    14.404] 	X.Org ANSI C Emulation: 0.4
[    14.404] 	X.Org Video Driver: 13.0
[    14.404] 	X.Org XInput driver : 18.0
[    14.404] 	X.Org Server Extension : 7.0
[    14.404] (II) config/udev: Adding drm device (/dev/dri/card0)
[    14.581] (--) PCI:*(0:0:2:0) 8086:0166:1043:108d rev 9, Mem @ 0xf7800000/4194304, 0xe0000000/268435456, I/O @ 0x0000f000/64
[    14.581] (II) Open ACPI successful (/var/run/acpid.socket)
[    14.581] Initializing built-in extension Generic Event Extension
[    14.581] Initializing built-in extension SHAPE
[    14.581] Initializing built-in extension MIT-SHM
[    14.581] Initializing built-in extension XInputExtension
[    14.581] Initializing built-in extension XTEST
[    14.581] Initializing built-in extension BIG-REQUESTS
[    14.581] Initializing built-in extension SYNC
[    14.581] Initializing built-in extension XKEYBOARD
[    14.581] Initializing built-in extension XC-MISC
[    14.581] Initializing built-in extension SECURITY
[    14.581] Initializing built-in extension XINERAMA
[    14.581] Initializing built-in extension XFIXES
[    14.581] Initializing built-in extension RENDER
[    14.581] Initializing built-in extension RANDR
[    14.581] Initializing built-in extension COMPOSITE
[    14.581] Initializing built-in extension DAMAGE
[    14.581] Initializing built-in extension MIT-SCREEN-SAVER
[    14.581] Initializing built-in extension DOUBLE-BUFFER
[    14.581] Initializing built-in extension RECORD
[    14.581] Initializing built-in extension DPMS
[    14.581] Initializing built-in extension X-Resource
[    14.581] Initializing built-in extension XVideo
[    14.581] Initializing built-in extension XVideo-MotionCompensation
[    14.581] Initializing built-in extension XFree86-VidModeExtension
[    14.581] Initializing built-in extension XFree86-DGA
[    14.581] Initializing built-in extension XFree86-DRI
[    14.581] Initializing built-in extension DRI2
[    14.581] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    14.581] (II) LoadModule: "glx"
[    14.581] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    14.582] (II) Module glx: vendor="X.Org Foundation"
[    14.582] 	compiled for 1.13.0, module version = 1.0.0
[    14.582] 	ABI class: X.Org Server Extension, version 7.0
[    14.582] (==) AIGLX enabled
[    14.582] Loading extension GLX
[    14.582] (II) LoadModule: "modesetting"
[    14.709] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    14.709] (II) Module modesetting: vendor="X.Org Foundation"
[    14.709] 	compiled for 1.13.0, module version = 0.5.0
[    14.709] 	Module class: X.Org Video Driver
[    14.709] 	ABI class: X.Org Video Driver, version 13.0
[    14.709] (II) LoadModule: "intel"
[    14.710] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    14.710] (II) Module intel: vendor="X.Org Foundation"
[    14.710] 	compiled for 1.13.0, module version = 2.20.9
[    14.710] 	Module class: X.Org Video Driver
[    14.710] 	ABI class: X.Org Video Driver, version 13.0
[    14.710] (II) LoadModule: "fbdev"
[    14.710] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    14.710] (II) Module fbdev: vendor="X.Org Foundation"
[    14.710] 	compiled for 1.12.99.902, module version = 0.4.3
[    14.710] 	Module class: X.Org Video Driver
[    14.710] 	ABI class: X.Org Video Driver, version 13.0
[    14.710] (II) LoadModule: "vesa"
[    14.710] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    14.710] (II) Module vesa: vendor="X.Org Foundation"
[    14.710] 	compiled for 1.12.99.902, module version = 2.3.2
[    14.710] 	Module class: X.Org Video Driver
[    14.710] 	ABI class: X.Org Video Driver, version 13.0
[    14.710] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    14.710] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
	Ivybridge Server (GT2), Haswell Desktop (GT1), Haswell Desktop (GT2),
	Haswell Desktop (GT2+), Haswell Mobile (GT1), Haswell Mobile (GT2),
	Haswell Mobile (GT2+), Haswell Server (GT1), Haswell Server (GT2),
	Haswell Server (GT2+), Haswell SDV Desktop (GT1),
	Haswell SDV Desktop (GT2), Haswell SDV Desktop (GT2+),
	Haswell SDV Mobile (GT1), Haswell SDV Mobile (GT2),
	Haswell SDV Mobile (GT2+), Haswell SDV Server (GT1),
	Haswell SDV Server (GT2), Haswell SDV Server (GT2+),
	Haswell ULT Desktop (GT1), Haswell ULT Desktop (GT2),
	Haswell ULT Desktop (GT2+), Haswell ULT Mobile (GT1),
	Haswell ULT Mobile (GT2), Haswell ULT Mobile (GT2+),
	Haswell ULT Server (GT1), Haswell ULT Server (GT2),
	Haswell ULT Server (GT2+), Haswell CRW Desktop (GT1),
	Haswell CRW Desktop (GT2), Haswell CRW Desktop (GT2+),
	Haswell CRW Mobile (GT1), Haswell CRW Mobile (GT2),
	Haswell CRW Mobile (GT2+), Haswell CRW Server (GT1),
	Haswell CRW Server (GT2), Haswell CRW Server (GT2+),
	ValleyView PO board
[    14.711] (II) FBDEV: driver for framebuffer: fbdev
[    14.711] (II) VESA: driver for VESA chipsets: vesa
[    14.711] (++) using VT number 7


[    14.711] (II) modesetting(0): using drv /dev/dri/card0
[    14.711] (WW) Falling back to old probe method for fbdev
[    14.711] (II) Loading sub module "fbdevhw"
[    14.711] (II) LoadModule: "fbdevhw"
[    14.711] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    14.711] (II) Module fbdevhw: vendor="X.Org Foundation"
[    14.711] 	compiled for 1.13.0, module version = 0.0.2
[    14.711] 	ABI class: X.Org Video Driver, version 13.0
[    14.711] (WW) Falling back to old probe method for vesa
[    14.711] (==) modesetting(0): Depth 24, (==) framebuffer bpp 32
[    14.711] (==) modesetting(0): RGB weight 888
[    14.711] (==) modesetting(0): Default visual is TrueColor
[    14.711] (II) modesetting(0): ShadowFB: preferred YES, enabled YES
[    14.711] (II) modesetting(0): Output LVDS-0 using monitor section Monitor0
[    14.711] (II) modesetting(0): Output VGA-0 has no monitor section
[    14.724] (II) modesetting(0): Output HDMI-0 has no monitor section
[    14.772] (II) modesetting(0): Output DisplayPort-0 has no monitor section
[    14.772] (II) modesetting(0): EDID for output LVDS-0
[    14.772] (II) modesetting(0): Manufacturer: AUO  Model: 305c  Serial#: 0
[    14.772] (II) modesetting(0): Year: 2009  Week: 0
[    14.772] (II) modesetting(0): EDID Version: 1.3
[    14.772] (II) modesetting(0): Digital Display Input
[    14.772] (II) modesetting(0): Max Image Size [cm]: horiz.: 26  vert.: 14
[    14.772] (II) modesetting(0): Gamma: 2.20
[    14.772] (II) modesetting(0): No DPMS capabilities specified
[    14.772] (II) modesetting(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    14.772] (II) modesetting(0): First detailed timing is preferred mode
[    14.772] (II) modesetting(0): redX: 0.584 redY: 0.333   greenX: 0.338 greenY: 0.571
[    14.772] (II) modesetting(0): blueX: 0.158 blueY: 0.133   whiteX: 0.313 whiteY: 0.329
[    14.772] (II) modesetting(0): Manufacturer's mask: 0
[    14.772] (II) modesetting(0): Supported detailed timing:
[    14.772] (II) modesetting(0): clock: 69.3 MHz   Image Size:  256 x 144 mm
[    14.772] (II) modesetting(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1456 h_border: 0
[    14.772] (II) modesetting(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 793 v_border: 0
[    14.772] (II) modesetting(0): Unknown vendor-specific block f
[    14.772] (II) modesetting(0):  AUO
[    14.772] (II) modesetting(0):  B116XW03 V0
[    14.772] (II) modesetting(0): EDID (in hex):
[    14.772] (II) modesetting(0): 	00ffffffffffff0006af5c3000000000
[    14.772] (II) modesetting(0): 	00130103801a0e780a99859555569228
[    14.772] (II) modesetting(0): 	22505400000001010101010101010101
[    14.772] (II) modesetting(0): 	010101010101121b565a500019303020
[    14.772] (II) modesetting(0): 	36000090100000180000000f00000000
[    14.772] (II) modesetting(0): 	00000000000000000020000000fe0041
[    14.772] (II) modesetting(0): 	554f0a202020202020202020000000fe
[    14.772] (II) modesetting(0): 	004231313658573033205630200a00ec
[    14.772] (II) modesetting(0): Printing probed modes for output LVDS-0
[    14.772] (II) modesetting(0): Modeline "1366x768"x60.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz eP)
[    14.772] (II) modesetting(0): EDID for output VGA-0
[    14.788] (II) modesetting(0): EDID for output HDMI-0
[    14.836] (II) modesetting(0): EDID for output DisplayPort-0
[    14.836] (II) modesetting(0): Output LVDS-0 connected
[    14.836] (II) modesetting(0): Output VGA-0 disconnected
[    14.836] (II) modesetting(0): Output HDMI-0 disconnected
[    14.836] (II) modesetting(0): Output DisplayPort-0 disconnected
[    14.836] (II) modesetting(0): Using exact sizes for initial modes
[    14.836] (II) modesetting(0): Output LVDS-0 using initial mode 1366x768
[    14.836] (II) modesetting(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    14.836] (==) modesetting(0): DPI set to (96, 96)
[    14.836] (II) Loading sub module "fb"
[    14.836] (II) LoadModule: "fb"
[    14.836] (II) Loading /usr/lib/xorg/modules/libfb.so
[    14.866] (II) Module fb: vendor="X.Org Foundation"
[    14.866] 	compiled for 1.13.0, module version = 1.0.0
[    14.866] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    14.866] (II) Loading sub module "shadow"
[    14.866] (II) LoadModule: "shadow"
[    14.866] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    14.873] (II) Module shadow: vendor="X.Org Foundation"
[    14.873] 	compiled for 1.13.0, module version = 1.1.0
[    14.873] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    14.873] (II) UnloadModule: "intel"
[    14.873] (II) Unloading intel
[    14.873] (II) UnloadModule: "fbdev"
[    14.873] (II) Unloading fbdev
[    14.873] (II) UnloadSubModule: "fbdevhw"
[    14.873] (II) Unloading fbdevhw
[    14.873] (II) UnloadModule: "vesa"
[    14.873] (II) Unloading vesa
[    14.873] (==) Depth 24 pixmap format is 32 bpp
[    14.897] (==) modesetting(0): Backing store disabled
[    14.897] (==) modesetting(0): Silken mouse enabled
[    14.897] (II) modesetting(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    14.897] (==) modesetting(0): DPMS enabled
[    14.908] (--) RandR disabled
[    14.914] (II) AIGLX: Screen 0 is not DRI2 capable
[    14.914] (II) AIGLX: Screen 0 is not DRI capable
[    15.644] (II) AIGLX: Loaded and initialized swrast
[    15.644] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    15.645] (II) modesetting(0): Damage tracking initialized
[    15.645] (II) modesetting(0): Setting screen physical size to 361 x 203
[    15.750] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    15.755] (II) config/udev: Adding input device Video Bus (/dev/input/event8)
[    15.756] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    15.756] (II) LoadModule: "evdev"
[    15.756] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.800] (II) Module evdev: vendor="X.Org Foundation"
[    15.800] 	compiled for 1.13.0, module version = 2.7.3
[    15.800] 	Module class: X.Org XInput Driver
[    15.800] 	ABI class: X.Org XInput driver, version 18.0
[    15.800] (II) Using input driver 'evdev' for 'Video Bus'
[    15.800] (**) Video Bus: always reports core events
[    15.800] (**) evdev: Video Bus: Device: "/dev/input/event8"
[    15.800] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    15.800] (--) evdev: Video Bus: Found keys
[    15.800] (II) evdev: Video Bus: Configuring as keyboard
[    15.800] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input8/event8"
[    15.800] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 6)
[    15.800] (**) Option "xkb_rules" "evdev"
[    15.800] (**) Option "xkb_model" "pc105"
[    15.800] (**) Option "xkb_layout" "us"
[    15.801] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    15.801] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    15.801] (II) Using input driver 'evdev' for 'Power Button'
[    15.801] (**) Power Button: always reports core events
[    15.801] (**) evdev: Power Button: Device: "/dev/input/event1"
[    15.801] (--) evdev: Power Button: Vendor 0 Product 0x1
[    15.801] (--) evdev: Power Button: Found keys
[    15.801] (II) evdev: Power Button: Configuring as keyboard
[    15.801] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    15.801] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    15.801] (**) Option "xkb_rules" "evdev"
[    15.801] (**) Option "xkb_model" "pc105"
[    15.801] (**) Option "xkb_layout" "us"
[    15.802] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    15.802] (II) No input driver specified, ignoring this device.
[    15.802] (II) This device may have been added with another device file.
[    15.802] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    15.802] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    15.802] (II) Using input driver 'evdev' for 'Sleep Button'
[    15.802] (**) Sleep Button: always reports core events
[    15.802] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    15.802] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    15.802] (--) evdev: Sleep Button: Found keys
[    15.802] (II) evdev: Sleep Button: Configuring as keyboard
[    15.802] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    15.802] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    15.802] (**) Option "xkb_rules" "evdev"
[    15.802] (**) Option "xkb_model" "pc105"
[    15.802] (**) Option "xkb_layout" "us"
[    15.802] (II) config/udev: Adding drm device (/dev/dri/card0)
[    15.803] (II) config/udev: Adding input device USB2.0 UVC HD Webcam (/dev/input/event6)
[    15.803] (**) USB2.0 UVC HD Webcam: Applying InputClass "evdev keyboard catchall"
[    15.803] (II) Using input driver 'evdev' for 'USB2.0 UVC HD Webcam'
[    15.803] (**) USB2.0 UVC HD Webcam: always reports core events
[    15.803] (**) evdev: USB2.0 UVC HD Webcam: Device: "/dev/input/event6"
[    15.803] (--) evdev: USB2.0 UVC HD Webcam: Vendor 0x13d3 Product 0x5188
[    15.803] (--) evdev: USB2.0 UVC HD Webcam: Found keys
[    15.803] (II) evdev: USB2.0 UVC HD Webcam: Configuring as keyboard
[    15.803] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input6/event6"
[    15.803] (II) XINPUT: Adding extended input device "USB2.0 UVC HD Webcam" (type: KEYBOARD, id 9)
[    15.803] (**) Option "xkb_rules" "evdev"
[    15.803] (**) Option "xkb_model" "pc105"
[    15.803] (**) Option "xkb_layout" "us"
[    15.804] (II) config/udev: Adding input device Atmel Atmel maXTouch Digitizer (/dev/input/event4)
[    15.804] (**) Atmel Atmel maXTouch Digitizer: Applying InputClass "evdev touchscreen catchall"
[    15.804] (II) Using input driver 'evdev' for 'Atmel Atmel maXTouch Digitizer'
[    15.804] (**) Atmel Atmel maXTouch Digitizer: always reports core events
[    15.804] (**) evdev: Atmel Atmel maXTouch Digitizer: Device: "/dev/input/event4"
[    15.804] (--) evdev: Atmel Atmel maXTouch Digitizer: Vendor 0x3eb Product 0x8417
[    15.804] (--) evdev: Atmel Atmel maXTouch Digitizer: Found absolute axes
[    15.804] (--) evdev: Atmel Atmel maXTouch Digitizer: Found absolute multitouch axes
[    15.804] (--) evdev: Atmel Atmel maXTouch Digitizer: Found x and y absolute axes
[    15.804] (--) evdev: Atmel Atmel maXTouch Digitizer: Found absolute touchscreen
[    15.804] (II) evdev: Atmel Atmel maXTouch Digitizer: Configuring as touchscreen
[    15.804] (**) evdev: Atmel Atmel maXTouch Digitizer: YAxisMapping: buttons 4 and 5
[    15.804] (**) evdev: Atmel Atmel maXTouch Digitizer: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    15.804] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input4/event4"
[    15.804] (II) XINPUT: Adding extended input device "Atmel Atmel maXTouch Digitizer" (type: TOUCHSCREEN, id 10)
[    15.804] (II) evdev: Atmel Atmel maXTouch Digitizer: initialized for absolute axes.
[    15.804] (**) Atmel Atmel maXTouch Digitizer: (accel) keeping acceleration scheme 1
[    15.804] (**) Atmel Atmel maXTouch Digitizer: (accel) acceleration profile 0
[    15.804] (**) Atmel Atmel maXTouch Digitizer: (accel) acceleration factor: 2.000
[    15.804] (**) Atmel Atmel maXTouch Digitizer: (accel) acceleration threshold: 4
[    15.804] (II) config/udev: Adding input device Atmel Atmel maXTouch Digitizer (/dev/input/mouse0)
[    15.804] (II) No input driver specified, ignoring this device.
[    15.804] (II) This device may have been added with another device file.
[    15.805] (II) config/udev: Adding input device HDA Intel PCH Headphone Mic (/dev/input/event10)
[    15.805] (II) No input driver specified, ignoring this device.
[    15.805] (II) This device may have been added with another device file.
[    15.805] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event9)
[    15.805] (II) No input driver specified, ignoring this device.
[    15.805] (II) This device may have been added with another device file.
[    15.805] (II) config/udev: Adding input device Asus WMI hotkeys (/dev/input/event5)
[    15.805] (**) Asus WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    15.805] (II) Using input driver 'evdev' for 'Asus WMI hotkeys'
[    15.805] (**) Asus WMI hotkeys: always reports core events
[    15.805] (**) evdev: Asus WMI hotkeys: Device: "/dev/input/event5"
[    15.805] (--) evdev: Asus WMI hotkeys: Vendor 0 Product 0
[    15.805] (--) evdev: Asus WMI hotkeys: Found keys
[    15.805] (II) evdev: Asus WMI hotkeys: Configuring as keyboard
[    15.805] (**) Option "config_info" "udev:/sys/devices/platform/asus-nb-wmi/input/input5/event5"
[    15.805] (II) XINPUT: Adding extended input device "Asus WMI hotkeys" (type: KEYBOARD, id 11)
[    15.805] (**) Option "xkb_rules" "evdev"
[    15.805] (**) Option "xkb_model" "pc105"
[    15.805] (**) Option "xkb_layout" "us"
[    15.806] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    15.806] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    15.806] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    15.806] (**) AT Translated Set 2 keyboard: always reports core events
[    15.806] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    15.806] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    15.806] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    15.806] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    15.806] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    15.806] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[    15.806] (**) Option "xkb_rules" "evdev"
[    15.806] (**) Option "xkb_model" "pc105"
[    15.806] (**) Option "xkb_layout" "us"
[    15.806] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event7)
[    15.806] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    15.806] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    15.806] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[    15.806] (II) LoadModule: "synaptics"
[    15.807] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    15.817] (II) Module synaptics: vendor="X.Org Foundation"
[    15.817] 	compiled for 1.12.99.905, module version = 1.6.2
[    15.817] 	Module class: X.Org XInput Driver
[    15.817] 	ABI class: X.Org XInput driver, version 18.0
[    15.817] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    15.817] (**) ETPS/2 Elantech Touchpad: always reports core events
[    15.817] (**) Option "Device" "/dev/input/event7"
[    15.817] (II) synaptics: ETPS/2 Elantech Touchpad: found clickpad property
[    15.817] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 3260
[    15.818] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 1793
[    15.818] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    15.818] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    15.818] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left double triple
[    15.818] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[    15.818] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[    15.818] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    15.818] (**) ETPS/2 Elantech Touchpad: always reports core events
[    15.818] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input7/event7"
[    15.818] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 13)
[    15.818] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    15.818] (**) synaptics: ETPS/2 Elantech Touchpad: MaxSpeed is now 1.75
[    15.818] (**) synaptics: ETPS/2 Elantech Touchpad: AccelFactor is now 0.054
[    15.818] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    15.818] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    15.818] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    15.818] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    15.818] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    15.818] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse1)
[    15.819] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[    22.168] (II) modesetting(0): EDID vendor "AUO", prod id 12380
[    22.168] (II) modesetting(0): Printing DDC gathered Modelines:
[    22.168] (II) modesetting(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz eP)
[    26.150] (II) modesetting(0): EDID vendor "AUO", prod id 12380
[    26.150] (II) modesetting(0): Printing DDC gathered Modelines:
[    26.150] (II) modesetting(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz eP)
[    36.335] (II) modesetting(0): EDID vendor "AUO", prod id 12380
[    36.335] (II) modesetting(0): Printing DDC gathered Modelines:
[    36.335] (II) modesetting(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz eP)
[    36.719] (II) modesetting(0): EDID vendor "AUO", prod id 12380
[    36.719] (II) modesetting(0): Printing DDC gathered Modelines:
[    36.719] (II) modesetting(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz eP)
[    37.838] (II) modesetting(0): EDID vendor "AUO", prod id 12380
[    37.838] (II) modesetting(0): Printing DDC gathered Modelines:
[    37.838] (II) modesetting(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz eP)
[    43.077] (II) modesetting(0): EDID vendor "AUO", prod id 12380
[    43.077] (II) modesetting(0): Printing DDC gathered Modelines:
[    43.077] (II) modesetting(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz eP)
[    51.465] (II) XKB: reuse xkmfile /var/lib/xkb/server-8C3648A5FD728529D869F46730BE1BC287DB231C.xkm
[    57.546] (II) modesetting(0): EDID vendor "AUO", prod id 12380
[    57.546] (II) modesetting(0): Printing DDC gathered Modelines:
[    57.546] (II) modesetting(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz eP)
[   200.449] (II) modesetting(0): EDID vendor "AUO", prod id 12380
[   200.449] (II) modesetting(0): Printing DDC gathered Modelines:
[   200.449] (II) modesetting(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz eP)
[   201.467] (II) PM Event received: Capability Changed
[   207.404] (II) Open ACPI successful (/var/run/acpid.socket)
[   207.420] (II) modesetting(0): EDID vendor "AUO", prod id 12380
[   207.420] (II) modesetting(0): Printing DDC gathered Modelines:
[   207.420] (II) modesetting(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz eP)
[   207.506] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[   208.221] (II) modesetting(0): EDID vendor "AUO", prod id 12380
[   208.221] (II) modesetting(0): Printing DDC gathered Modelines:
[   208.221] (II) modesetting(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz eP)
root@josep-X202E:/home/josep#

---

### Post by titansmc on 2013-04-02
After upgrading the system, to kernel 3.5.0-26 it seems the problem got corrected. ethernet working, sound on, touch screen on.... Could someone, please suggest what it was due to?

Also shutdown button works.... so weird, but it is simply what I needed.

Cheers.

---

