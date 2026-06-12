---
title: "Upgrade to Natty causes xorg trouble with Nvidia card"
date: 2011-05-12
forum: Multimedia Software
---

### Post by tepperly on 2011-05-12
In short, my system was working fine under Maverick with the nvidia-96 proprietary driver. I denied upgrading to Natty a few times because I noticed that nvida-96 wouldn't be installed, but it kept pestering me to upgrade. I gave in and did upgraded to Natty. I figured the nvidia drivers could be worked out after the upgrade because there was a nvidia-96 package for natty. This was wrong.

nvidia-96 is not installable, and there is no ETA for an upgrade from Nvidia that will install.

I've tried downgrading xorg and all its pieces back to maverick, but the downgrade xorg server seems to crash on start up with no useful output.

Okay, plan B -- try the nouveau driver.  I struggled with nouveau for a while, and I am pretty close to getting it working. I can't seem to get it to set up with a 60Hz refresh. All the choices in the gnome-display-properties are 50Hz (which seems appropriate for PAL rather than NTSC-M). I've tried setting tv_norm=NSTC-M, but it doesn't seem to change anything.
mythtv:~# cat /sys/module/ttm/holders/nouveau/parameters/tv_norm
NTSC-M
mythtv:~# cat /var/log/Xorg.0.log
[   820.643] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[   820.643] X Protocol Version 11, Revision 0
[   820.643] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[   820.643] Current Operating System: Linux mythtv 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[   820.643] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=dac27fc6-a822-4da6-bf60-bb1c8c1199f6 ro quiet splash vt.handoff=7
[   820.643] Build Date: 19 April 2011  03:33:17PM
[   820.643] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[   820.643] Current version of pixman: 0.20.2
[   820.643]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[   820.643] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   820.643] (==) Log file: "/var/log/Xorg.0.log", Time: Thu May 12 10:16:19 2011
[   820.643] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   820.643] (==) No Layout section.  Using the first Screen section.
[   820.643] (==) No screen section available. Using defaults.
[   820.643] (**) |-->Screen "Default Screen Section" (0)
[   820.643] (**) |   |-->Monitor "<default monitor>"
[   820.643] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
[   820.643] (**) |   |-->Device "Device[0]"
[   820.643] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   820.643] (==) Automatically adding devices
[   820.643] (==) Automatically enabling devices
[   820.644] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   820.644]     Entry deleted from font path.
[   820.644] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[   820.644] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   820.644] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   820.644] (II) Loader magic: 0x81ffde0
[   820.644] (II) Module ABI versions:
[   820.644]     X.Org ANSI C Emulation: 0.4
[   820.644]     X.Org Video Driver: 10.0
[   820.644]     X.Org XInput driver : 12.3
[   820.644]     X.Org Server Extension : 5.0
[   820.644] (--) PCI: (0:0:13:0) 10de:03d6:1458:d000 rev 162, Mem @ 0xfd000000/16777216, 0xc0000000/268435456, 0xfc000000/16777216, BIOS @ 0x????????/131072
[   820.644] (--) PCI:*(0:1:6:0) 10de:0110:0000:0000 rev 178, Mem @ 0xfa000000/16777216, 0xd0000000/134217728, BIOS @ 0x????????/65536
[   820.644] (--) PCI: (0:1:7:0) 4444:0803:0070:4000 rev 1, Mem @ 0xdc000000/67108864
[   820.645] (II) Open ACPI successful (/var/run/acpid.socket)
[   820.645] (II) LoadModule: "extmod"
[   820.645] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   820.645] (II) Module extmod: vendor="X.Org Foundation"
[   820.645]     compiled for 1.10.1, module version = 1.0.0
[   820.645]     Module class: X.Org Server Extension
[   820.645]     ABI class: X.Org Server Extension, version 5.0
[   820.645] (II) Loading extension MIT-SCREEN-SAVER
[   820.645] (II) Loading extension XFree86-VidModeExtension
[   820.645] (II) Loading extension XFree86-DGA
[   820.645] (II) Loading extension DPMS
[   820.645] (II) Loading extension XVideo
[   820.645] (II) Loading extension XVideo-MotionCompensation
[   820.645] (II) Loading extension X-Resource
[   820.645] (II) LoadModule: "dbe"
[   820.645] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   820.645] (II) Module dbe: vendor="X.Org Foundation"
[   820.645]     compiled for 1.10.1, module version = 1.0.0
[   820.645]     Module class: X.Org Server Extension
[   820.645]     ABI class: X.Org Server Extension, version 5.0
[   820.645] (II) Loading extension DOUBLE-BUFFER
[   820.645] (II) LoadModule: "glx"
[   820.646] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   820.646] (II) Module glx: vendor="X.Org Foundation"
[   820.646]     compiled for 1.10.1, module version = 1.0.0
[   820.646]     ABI class: X.Org Server Extension, version 5.0
[   820.646] (==) AIGLX enabled
[   820.646] (II) Loading extension GLX
[   820.646] (II) LoadModule: "record"
[   820.646] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   820.646] (II) Module record: vendor="X.Org Foundation"
[   820.646]     compiled for 1.10.1, module version = 1.13.0
[   820.646]     Module class: X.Org Server Extension
[   820.646]     ABI class: X.Org Server Extension, version 5.0
[   820.646] (II) Loading extension RECORD
[   820.646] (II) LoadModule: "dri"
[   820.646] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   820.646] (II) Module dri: vendor="X.Org Foundation"
[   820.646]     compiled for 1.10.1, module version = 1.0.0
[   820.646]     ABI class: X.Org Server Extension, version 5.0
[   820.646] (II) Loading extension XFree86-DRI
[   820.646] (II) LoadModule: "dri2"
[   820.646] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   820.647] (II) Module dri2: vendor="X.Org Foundation"
[   820.647]     compiled for 1.10.1, module version = 1.2.0
[   820.647]     ABI class: X.Org Server Extension, version 5.0
[   820.647] (II) Loading extension DRI2
[   820.647] (II) LoadModule: "nouveau"
[   820.647] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   820.647] (II) Module nouveau: vendor="X.Org Foundation"
[   820.647]     compiled for 1.10.0, module version = 0.0.16
[   820.647]     Module class: X.Org Video Driver
[   820.647]     ABI class: X.Org Video Driver, version 10.0
[   820.647] (II) NOUVEAU driver Date:   Fri Jan 7 13:33:36 2011 +1000
[   820.647] (II) NOUVEAU driver for NVIDIA chipset families :
[   820.647]     RIVA TNT    (NV04)
[   820.647]     RIVA TNT2   (NV05)
[   820.647]     GeForce 256 (NV10)
[   820.647]     GeForce 2   (NV11, NV15)
[   820.647]     GeForce 4MX (NV17, NV18)
[   820.647]     GeForce 3   (NV20)
[   820.647]     GeForce 4Ti (NV25, NV28)
[   820.647]     GeForce FX  (NV3x)
[   820.647]     GeForce 6   (NV4x)
[   820.647]     GeForce 7   (G7x)
[   820.647]     GeForce 8   (G8x)
[   820.647] (--) using VT number 8

[   820.648] drmOpenDevice: node name is /dev/dri/card0
[   820.648] drmOpenDevice: open result is 8, (OK)
[   820.648] drmOpenByBusid: Searching for BusID pci:0000:01:06.0
[   820.648] drmOpenDevice: node name is /dev/dri/card0
[   820.648] drmOpenDevice: open result is 8, (OK)
[   820.648] drmOpenByBusid: drmOpenMinor returns 8
[   820.648] drmOpenByBusid: drmGetBusid reports pci:0000:01:06.0
[   820.648] (II) [drm] nouveau interface version: 0.0.16
[   820.649] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   820.649] (II) Loading sub module "dri"
[   820.649] (II) LoadModule: "dri"
[   820.649] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   820.649] (II) Module dri: vendor="X.Org Foundation"
[   820.649]     compiled for 1.10.1, module version = 1.0.0
[   820.649]     ABI class: X.Org Server Extension, version 5.0
[   820.649] (II) NOUVEAU(0): Loaded DRI module
[   820.649] drmOpenDevice: node name is /dev/dri/card0
[   820.649] drmOpenDevice: open result is 9, (OK)
[   820.649] drmOpenDevice: node name is /dev/dri/card0
[   820.649] drmOpenDevice: open result is 9, (OK)
[   820.649] drmOpenByBusid: Searching for BusID pci:0000:01:06.0
[   820.649] drmOpenDevice: node name is /dev/dri/card0
[   820.649] drmOpenDevice: open result is 9, (OK)
[   820.649] drmOpenByBusid: drmOpenMinor returns 9
[   820.649] drmOpenByBusid: drmGetBusid reports pci:0000:01:06.0
[   820.649] (II) [drm] DRM interface version 1.4
[   820.649] (II) [drm] DRM open master succeeded.
[   820.649] (--) NOUVEAU(0): Chipset: "NVIDIA NV11"
[   820.649] (II) NOUVEAU(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   820.649] (==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
[   820.649] (==) NOUVEAU(0): RGB weight 888
[   820.649] (==) NOUVEAU(0): Default visual is TrueColor
[   820.649] (==) NOUVEAU(0): Using HW cursor
[   820.649] (==) NOUVEAU(0): GLX sync to VBlank disabled.
[   820.700] (II) NOUVEAU(0): Output VGA-1 has no monitor section
[   820.734] (II) NOUVEAU(0): Output TV-1 has no monitor section
[   820.784] (II) NOUVEAU(0): EDID for output VGA-1
[   820.818] (II) NOUVEAU(0): EDID for output TV-1
[   820.818] (II) NOUVEAU(0): Printing probed modes for output TV-1
[   820.819] (II) NOUVEAU(0): Modeline "800x600"x50.0   36.00  800 816 880 960  600 610 626 750 +hsync +vsync (37.5 kHz)
[   820.819] (II) NOUVEAU(0): Modeline "720x576"x50.0   29.50  720 816 880 944  576 586 602 625 +hsync +vsync (31.2 kHz)
[   820.819] (II) NOUVEAU(0): Modeline "640x480"x50.0   26.25  640 656 720 840  480 490 506 625 -hsync -vsync (31.2 kHz)
[   820.819] (II) NOUVEAU(0): Modeline "720x400"x50.0   28.12  720 736 800 1125  400 410 426 500 -hsync -vsync (25.0 kHz)
[   820.819] (II) NOUVEAU(0): Modeline "640x400"x50.0   25.00  640 656 720 1000  400 410 426 500 -hsync -vsync (25.0 kHz)
[   820.819] (II) NOUVEAU(0): Modeline "512x384"x50.0   21.00  512 528 592 840  384 394 410 500 -hsync -vsync (25.0 kHz)
[   820.819] (II) NOUVEAU(0): Output VGA-1 disconnected
[   820.819] (II) NOUVEAU(0): Output TV-1 connected
[   820.819] (II) NOUVEAU(0): Using fuzzy aspect match for initial modes
[   820.819] (II) NOUVEAU(0): Output TV-1 using initial mode 800x600
[   820.819] (II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   820.819] (--) NOUVEAU(0): Virtual size is 800x600 (pitch 0)
[   820.819] (**) NOUVEAU(0):  Driver mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 37.5 kHz, 50.0 Hz
[   820.819] (II) NOUVEAU(0): Modeline "800x600"x50.0   36.00  800 816 880 960  600 610 626 750 +hsync +vsync (37.5 kHz)
[   820.819] (**) NOUVEAU(0):  Driver mode "720x576": 29.5 MHz (scaled from 0.0 MHz), 31.2 kHz, 50.0 Hz
[   820.819] (II) NOUVEAU(0): Modeline "720x576"x50.0   29.50  720 816 880 944  576 586 602 625 +hsync +vsync (31.2 kHz)
[   820.819] (**) NOUVEAU(0):  Driver mode "640x480": 26.2 MHz (scaled from 0.0 MHz), 31.2 kHz, 50.0 Hz
[   820.819] (II) NOUVEAU(0): Modeline "640x480"x50.0   26.25  640 656 720 840  480 490 506 625 -hsync -vsync (31.2 kHz)
[   820.819] (**) NOUVEAU(0):  Driver mode "720x400": 28.1 MHz (scaled from 0.0 MHz), 25.0 kHz, 50.0 Hz
[   820.819] (II) NOUVEAU(0): Modeline "720x400"x50.0   28.12  720 736 800 1125  400 410 426 500 -hsync -vsync (25.0 kHz)
[   820.819] (**) NOUVEAU(0):  Driver mode "640x400": 25.0 MHz (scaled from 0.0 MHz), 25.0 kHz, 50.0 Hz
[   820.819] (II) NOUVEAU(0): Modeline "640x400"x50.0   25.00  640 656 720 1000  400 410 426 500 -hsync -vsync (25.0 kHz)
[   820.819] (**) NOUVEAU(0):  Driver mode "512x384": 21.0 MHz (scaled from 0.0 MHz), 25.0 kHz, 50.0 Hz
[   820.819] (II) NOUVEAU(0): Modeline "512x384"x50.0   21.00  512 528 592 840  384 394 410 500 -hsync -vsync (25.0 kHz)
[   820.819] (==) NOUVEAU(0): DPI set to (96, 96)
[   820.819] (II) Loading sub module "fb"
[   820.819] (II) LoadModule: "fb"
[   820.819] (II) Loading /usr/lib/xorg/modules/libfb.so
[   820.819] (II) Module fb: vendor="X.Org Foundation"
[   820.819]     compiled for 1.10.1, module version = 1.0.0
[   820.819]     ABI class: X.Org ANSI C Emulation, version 0.4
[   820.819] (II) Loading sub module "exa"
[   820.819] (II) LoadModule: "exa"
[   820.819] (II) Loading /usr/lib/xorg/modules/libexa.so
[   820.819] (II) Module exa: vendor="X.Org Foundation"
[   820.819]     compiled for 1.10.1, module version = 2.5.0
[   820.819]     ABI class: X.Org Video Driver, version 10.0
[   820.819] (II) Loading sub module "shadowfb"
[   820.819] (II) LoadModule: "shadowfb"
[   820.820] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[   820.820] (II) Module shadowfb: vendor="X.Org Foundation"
[   820.820]     compiled for 1.10.1, module version = 1.0.0
[   820.820]     ABI class: X.Org ANSI C Emulation, version 0.4
[   820.820] (--) Depth 24 pixmap format is 32 bpp
[   820.821] (II) NOUVEAU(0): Opened GPU channel 1
[   820.821] (II) NOUVEAU(0): [DRI2] Setup complete
[   820.821] (II) NOUVEAU(0): [DRI2]   DRI driver: nouveau_vieux
[   820.821] (II) NOUVEAU(0): GART: 64MiB available
[   820.823] (II) NOUVEAU(0): GART: Allocated 16MiB as a scratch buffer
[   820.823] (II) EXA(0): Driver allocated offscreen pixmaps
[   820.823] (II) EXA(0): Driver registered support for the following operations:
[   820.823] (II)         Solid
[   820.823] (II)         Copy
[   820.823] (II)         Composite (RENDER acceleration)
[   820.823] (II)         UploadToScreen
[   820.823] (II)         DownloadFromScreen
[   820.823] (==) NOUVEAU(0): Backing store disabled
[   820.823] (==) NOUVEAU(0): Silken mouse enabled
[   820.823] (==) NOUVEAU(0): DPMS enabled
[   820.823] (II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   820.823] (--) RandR disabled
[   820.823] (II) Initializing built-in extension Generic Event Extension
[   820.823] (II) Initializing built-in extension SHAPE
[   820.823] (II) Initializing built-in extension MIT-SHM
[   820.823] (II) Initializing built-in extension XInputExtension
[   820.823] (II) Initializing built-in extension XTEST
[   820.823] (II) Initializing built-in extension BIG-REQUESTS
[   820.823] (II) Initializing built-in extension SYNC
[   820.823] (II) Initializing built-in extension XKEYBOARD
[   820.823] (II) Initializing built-in extension XC-MISC
[   820.823] (II) Initializing built-in extension SECURITY
[   820.823] (II) Initializing built-in extension XINERAMA
[   820.823] (II) Initializing built-in extension XFIXES
[   820.823] (II) Initializing built-in extension RENDER
[   820.823] (II) Initializing built-in extension RANDR
[   820.823] (II) Initializing built-in extension COMPOSITE
[   820.823] (II) Initializing built-in extension DAMAGE
[   820.823] (II) Initializing built-in extension GESTURE
[   820.830] (II) AIGLX: Trying DRI driver /usr/lib/dri/nouveau_vieux_dri.so
[   820.833] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[   820.833] (II) AIGLX: enabled GLX_INTEL_swap_event
[   820.833] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[   820.833] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[   820.833] (II) AIGLX: Loaded and initialized nouveau_vieux
[   820.833] (II) GLX: Initialized DRI2 GL provider for screen 0
[   820.835] (II) NOUVEAU(0): NVEnterVT is called.
[   820.835] (II) NOUVEAU(0): Setting screen physical size to 211 x 158
[   820.835] resize called 800 600
[   820.851] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   820.858] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   820.858] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   820.858] (II) LoadModule: "evdev"
[   820.858] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   820.858] (II) Module evdev: vendor="X.Org Foundation"
[   820.858]     compiled for 1.10.0.902, module version = 2.6.0
[   820.858]     Module class: X.Org XInput Driver
[   820.858]     ABI class: X.Org XInput driver, version 12.3
[   820.858] (II) Using input driver 'evdev' for 'Power Button'
[   820.858] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   820.858] (**) Power Button: always reports core events
[   820.858] (**) Power Button: Device: "/dev/input/event1"
[   820.858] (--) Power Button: Found keys
[   820.858] (II) Power Button: Configuring as keyboard
[   820.858] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[   820.858] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   820.858] (**) Option "xkb_rules" "evdev"
[   820.858] (**) Option "xkb_model" "pc105"
[   820.858] (**) Option "xkb_layout" "us"
[   820.861] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   820.861] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   820.861] (II) Using input driver 'evdev' for 'Power Button'
[   820.861] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   820.861] (**) Power Button: always reports core events
[   820.861] (**) Power Button: Device: "/dev/input/event0"
[   820.861] (--) Power Button: Found keys
[   820.861] (II) Power Button: Configuring as keyboard
[   820.861] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[   820.861] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   820.861] (**) Option "xkb_rules" "evdev"
[   820.861] (**) Option "xkb_model" "pc105"
[   820.861] (**) Option "xkb_layout" "us"
[   820.862] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event2)
[   820.862] (**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
[   820.862] (II) Using input driver 'evdev' for 'Logitech USB-PS/2 Optical Mouse'
[   820.862] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   820.862] (**) Logitech USB-PS/2 Optical Mouse: always reports core events
[   820.862] (**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event2"
[   820.862] (--) Logitech USB-PS/2 Optical Mouse: Found 3 mouse buttons
[   820.862] (--) Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
[   820.862] (--) Logitech USB-PS/2 Optical Mouse: Found relative axes
[   820.862] (--) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
[   820.862] (II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
[   820.862] (II) Logitech USB-PS/2 Optical Mouse: Adding scrollwheel support
[   820.862] (**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
[   820.862] (**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   820.862] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-5/2-5:1.0/input/input2/event2"
[   820.862] (II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
[   820.862] (II) Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
[   820.862] (**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
[   820.862] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration profile 0
[   820.862] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration factor: 2.000
[   820.862] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration threshold: 4
[   820.862] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse0)
[   820.863] (II) No input driver/identifier specified (ignoring)
[   822.269] resize called 640 400
[   877.343] resize called 640 480
mythtv:~# cat /usr/share/X11/xorg.conf.d/65-nvidia.conf
#Section "Monitor"
#    Identifier "Monitor[1]" #TV
#    HorizSync 30-50
#    VertRefresh 60
#EndSection

Section "Device"
    Identifier    "Device[0]"
#    Option "ZaphodHeads" "TV-1"
#    Option "tv_norm" "NTSC-M"
# nvidia-96
#    Driver                "nvidia"
#    Option "TVOutFormat"        "Composite"
#    Option "TVStandard"        "NTSC-M"
#    Option "ConnectedMonitor"   "TV"
#    BusID                "PCI:1:06:0"
####        Option "XAANoOffscreenPixmaps" "true"
#        Option "AllowGLXWithComposite" "true"
# nouveau
    Driver "nouveau"
EndSection

#Section "Screen"
#    Identifier "Screen[0]"
#    Device        "Device[0]"
#    Monitor    "Monitor[1]"
#    DefaultDepth 24
#    SubSection "Display"
#           Depth 24
#           Modes "640x480"
##           Virtual 1024 768
#        EndSubSection
#EndSection

---

