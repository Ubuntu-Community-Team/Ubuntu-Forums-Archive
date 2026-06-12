---
title: "Xorg log errors?"
date: 2012-08-09
forum: Multimedia Software
---

### Post by mips on 2012-08-09
/var/log/Xorg.0.log
```
[    18.207] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    18.207] X Protocol Version 11, Revision 0
[    18.207] Build Operating System: Linux 2.6.42-23-generic x86_64 Ubuntu
[    18.207] Current Operating System: Linux obelix 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64
[    18.207] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic root=UUID=d0841918-eebe-44f8-8e91-a5fef8c700cf ro quiet splash vt.handoff=7
[    18.207] Build Date: 20 April 2012  05:12:02AM
[    18.207] xorg-server 2:1.11.4-0ubuntu10.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    18.207] Current version of pixman: 0.24.4
[    18.207] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    18.207] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.207] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Aug  9 13:31:51 2012
[    18.207] (==) Using config file: "/etc/X11/xorg.conf"
[    18.207] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    18.208] (==) ServerLayout "X.org Configured"
[    18.208] (**) |-->Screen "Screen0" (0)
[    18.208] (**) |   |-->Monitor "Monitor0"
[    18.229] (**) |   |-->Device "Device0"
[    18.251] (**) |-->Input Device "Mouse0"
[    18.251] (**) |-->Input Device "Keyboard0"
[    18.251] (**) Option "Xinerama" "0"
[    18.251] (==) Automatically adding devices
[    18.251] (==) Automatically enabling devices
[    18.278] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.278] 	Entry deleted from font path.
[    18.279] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    18.279] 	Entry deleted from font path.
[    18.279] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    18.279] 	Entry deleted from font path.
[    18.286] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    18.286] 	Entry deleted from font path.
[    18.286] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    18.286] 	Entry deleted from font path.
[    18.286] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    18.286] 	Entry deleted from font path.
[    18.286] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.286] 	Entry deleted from font path.
[    18.286] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    18.286] 	Entry deleted from font path.
[    18.286] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    18.286] 	Entry deleted from font path.
[    18.286] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    18.286] 	Entry deleted from font path.
[    18.286] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    18.286] 	Entry deleted from font path.
[    18.286] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    18.286] 	Entry deleted from font path.
[    18.286] (**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    18.286] (**) ModulePath set to "/usr/lib/xorg/modules"
[    18.286] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    18.286] (WW) Disabling Mouse0
[    18.286] (WW) Disabling Keyboard0
[    18.286] (II) Loader magic: 0x7f600e17ab00
[    18.286] (II) Module ABI versions:
[    18.286] 	X.Org ANSI C Emulation: 0.4
[    18.286] 	X.Org Video Driver: 11.0
[    18.286] 	X.Org XInput driver : 16.0
[    18.286] 	X.Org Server Extension : 6.0
[    18.287] (--) PCI:*(0:1:0:0) 10de:0622:1682:2362 rev 161, Mem @ 0xd2000000/16777216, 0xa0000000/536870912, 0xd0000000/33554432, I/O @ 0x0000c000/128, BIOS @ 0x????????/524288
[    18.287] (II) Open ACPI successful (/var/run/acpid.socket)
[    18.287] (II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
[    18.287] (II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
[    18.287] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    18.287] (II) "record" will be loaded. This was enabled by default and also specified in the config file.
[    18.287] (II) "dri" will be loaded. This was enabled by default and also specified in the config file.
[    18.287] (II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
[    18.287] (II) LoadModule: "dbe"
[    18.307] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    18.307] (II) Module dbe: vendor="X.Org Foundation"
[    18.307] 	compiled for 1.11.3, module version = 1.0.0
[    18.307] 	Module class: X.Org Server Extension
[    18.307] 	ABI class: X.Org Server Extension, version 6.0
[    18.307] (II) Loading extension DOUBLE-BUFFER
[    18.307] (II) LoadModule: "record"
[    18.307] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    18.307] (II) Module record: vendor="X.Org Foundation"
[    18.307] 	compiled for 1.11.3, module version = 1.13.0
[    18.307] 	Module class: X.Org Server Extension
[    18.307] 	ABI class: X.Org Server Extension, version 6.0
[    18.307] (II) Loading extension RECORD
[    18.307] (II) LoadModule: "extmod"
[    18.307] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    18.307] (II) Module extmod: vendor="X.Org Foundation"
[    18.307] 	compiled for 1.11.3, module version = 1.0.0
[    18.307] 	Module class: X.Org Server Extension
[    18.307] 	ABI class: X.Org Server Extension, version 6.0
[    18.307] (II) Loading extension MIT-SCREEN-SAVER
[    18.307] (II) Loading extension XFree86-VidModeExtension
[    18.307] (II) Loading extension XFree86-DGA
[    18.307] (II) Loading extension DPMS
[    18.307] (II) Loading extension XVideo
[    18.307] (II) Loading extension XVideo-MotionCompensation
[    18.307] (II) Loading extension X-Resource
[    18.307] (II) LoadModule: "dri"
[    18.307] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    18.308] (II) Module dri: vendor="X.Org Foundation"
[    18.308] 	compiled for 1.11.3, module version = 1.0.0
[    18.308] 	ABI class: X.Org Server Extension, version 6.0
[    18.308] (II) Loading extension XFree86-DRI
[    18.308] (II) LoadModule: "dri2"
[    18.308] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    18.308] (II) Module dri2: vendor="X.Org Foundation"
[    18.308] 	compiled for 1.11.3, module version = 1.2.0
[    18.308] 	ABI class: X.Org Server Extension, version 6.0
[    18.308] (II) Loading extension DRI2
[    18.308] (II) LoadModule: "glx"
[    18.308] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    18.308] (EE) Failed to load /usr/lib/xorg/modules/extensions/libglx.so: /usr/lib/xorg/modules/extensions/libglx.so: cannot open shared object file: No such file or directory
[    18.308] (II) UnloadModule: "glx"
[    18.308] (II) Unloading glx
[    18.308] (EE) Failed to load module "glx" (loader failed, 7)
[    18.308] (II) LoadModule: "nvidia"
[    18.308] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    18.309] (II) Module nvidia: vendor="NVIDIA Corporation"
[    18.309] 	compiled for 4.0.2, module version = 1.0.0
[    18.309] 	Module class: X.Org Video Driver
[    18.309] (II) NVIDIA dlloader X Driver  295.40  Thu Apr  5 21:38:35 PDT 2012
[    18.309] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    18.309] (++) using VT number 7

[    18.309] (II) Loading sub module "fb"
[    18.309] (II) LoadModule: "fb"
[    18.309] (II) Loading /usr/lib/xorg/modules/libfb.so
[    18.309] (II) Module fb: vendor="X.Org Foundation"
[    18.309] 	compiled for 1.11.3, module version = 1.0.0
[    18.309] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    18.309] (II) Loading sub module "wfb"
[    18.309] (II) LoadModule: "wfb"
[    18.309] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    18.309] (II) Module wfb: vendor="X.Org Foundation"
[    18.309] 	compiled for 1.11.3, module version = 1.0.0
[    18.309] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    18.309] (II) Loading sub module "ramdac"
[    18.309] (II) LoadModule: "ramdac"
[    18.309] (II) Module "ramdac" already built-in
[    18.309] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    18.309] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    18.309] (II) Loading /usr/lib/xorg/modules/libfb.so
[    18.309] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    18.309] (==) NVIDIA(0): RGB weight 888
[    18.309] (==) NVIDIA(0): Default visual is TrueColor
[    18.309] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    18.309] (**) NVIDIA(0): Option "TwinView" "1"
[    18.309] (**) NVIDIA(0): Option "MetaModes" "DFP-0: nvidia-auto-select +1680+0, DFP-1: nvidia-auto-select +0+0"
[    18.309] (**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "DFP-0"
[    18.310] (**) NVIDIA(0): Enabling 2D acceleration
[    18.310] (EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
[    18.310] (EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
[    18.310] (EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
[    18.310] (EE) NVIDIA(0):     you continue to encounter problems, Please try
[    18.310] (EE) NVIDIA(0):     reinstalling the NVIDIA driver.
[    20.194] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[    20.194] (II) NVIDIA(GPU-0):     3D Vision stereo.
[    20.260] (II) NVIDIA(GPU-0): Display (LG Electronics W2252 (DFP-1)) does not support NVIDIA
[    20.260] (II) NVIDIA(GPU-0):     3D Vision stereo.
[    20.261] (II) NVIDIA(0): NVIDIA GPU GeForce 9600 GT (G94) at PCI:1:0:0 (GPU-0)
[    20.261] (--) NVIDIA(0): Memory: 524288 kBytes
[    20.261] (--) NVIDIA(0): VideoBIOS: 62.94.11.00.00
[    20.261] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    20.261] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    20.264] (--) NVIDIA(0): Connected display device(s) on GeForce 9600 GT at PCI:1:0:0
[    20.264] (--) NVIDIA(0):     Samsung SyncMaster (DFP-0)
[    20.264] (--) NVIDIA(0):     LG Electronics W2252 (DFP-1)
[    20.264] (--) NVIDIA(0): Samsung SyncMaster (DFP-0): 330.0 MHz maximum pixel clock
[    20.264] (--) NVIDIA(0): Samsung SyncMaster (DFP-0): Internal Dual Link TMDS
[    20.264] (--) NVIDIA(0): LG Electronics W2252 (DFP-1): 330.0 MHz maximum pixel clock
[    20.264] (--) NVIDIA(0): LG Electronics W2252 (DFP-1): Internal Dual Link TMDS
[    20.264] (**) NVIDIA(0): TwinView enabled
[    20.264] (II) NVIDIA(0): Display Devices found referenced in MetaMode: DFP-0, DFP-1
[    20.264] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    20.264] (**) NVIDIA(0):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[    20.264] (**) NVIDIA(0):     has been enabled on all display devices.)
[    20.264] (WW) NVIDIA(0): The EDID for Samsung SyncMaster (DFP-0) contradicts itself:
[    20.264] (WW) NVIDIA(0):     mode "1920x1080" is specified in the EDID; however, the
[    20.264] (WW) NVIDIA(0):     EDID's valid VertRefresh range (56.000-60.000 Hz) would
[    20.264] (WW) NVIDIA(0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    20.264] (WW) NVIDIA(0):     VertRefresh check for mode "1920x1080".
[    20.264] (WW) NVIDIA(0): The EDID for Samsung SyncMaster (DFP-0) contradicts itself:
[    20.264] (WW) NVIDIA(0):     mode "1280x720" is specified in the EDID; however, the
[    20.264] (WW) NVIDIA(0):     EDID's valid VertRefresh range (56.000-60.000 Hz) would
[    20.264] (WW) NVIDIA(0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    20.264] (WW) NVIDIA(0):     VertRefresh check for mode "1280x720".
[    20.264] (WW) NVIDIA(0): The EDID for Samsung SyncMaster (DFP-0) contradicts itself:
[    20.264] (WW) NVIDIA(0):     mode "720x576" is specified in the EDID; however, the
[    20.264] (WW) NVIDIA(0):     EDID's valid VertRefresh range (56.000-60.000 Hz) would
[    20.264] (WW) NVIDIA(0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    20.264] (WW) NVIDIA(0):     VertRefresh check for mode "720x576".
[    20.265] (WW) NVIDIA(0): The EDID for Samsung SyncMaster (DFP-0) contradicts itself:
[    20.265] (WW) NVIDIA(0):     mode "1920x1080" is specified in the EDID; however, the
[    20.265] (WW) NVIDIA(0):     EDID's valid VertRefresh range (56.000-60.000 Hz) would
[    20.265] (WW) NVIDIA(0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    20.265] (WW) NVIDIA(0):     VertRefresh check for mode "1920x1080".
[    20.265] (WW) NVIDIA(0): The EDID for Samsung SyncMaster (DFP-0) contradicts itself:
[    20.265] (WW) NVIDIA(0):     mode "1280x720" is specified in the EDID; however, the
[    20.265] (WW) NVIDIA(0):     EDID's valid VertRefresh range (56.000-60.000 Hz) would
[    20.265] (WW) NVIDIA(0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    20.265] (WW) NVIDIA(0):     VertRefresh check for mode "1280x720".
[    20.265] (WW) NVIDIA(0): The EDID for Samsung SyncMaster (DFP-0) contradicts itself:
[    20.265] (WW) NVIDIA(0):     mode "720x576" is specified in the EDID; however, the
[    20.265] (WW) NVIDIA(0):     EDID's valid VertRefresh range (56.000-60.000 Hz) would
[    20.266] (WW) NVIDIA(0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    20.266] (WW) NVIDIA(0):     VertRefresh check for mode "720x576".
[    20.309] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    20.309] (**) NVIDIA(0):     device LG Electronics W2252 (DFP-1) (Using EDID
[    20.309] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[    20.352] (II) NVIDIA(0): Assigned Display Devices: DFP-0, DFP-1
[    20.356] (II) NVIDIA(0): Validated modes:
[    20.356] (II) NVIDIA(0):    
[    20.356] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select+1680+0,DFP-1:nvidia-auto-select+0+0"
[    20.356] (II) NVIDIA(0): Virtual screen size determined to be 3600 x 1080
[    20.378] (--) NVIDIA(0): DPI set to (95, 94); computed from "UseEdidDpi" X config
[    20.378] (--) NVIDIA(0):     option
[    20.378] (--) Depth 24 pixmap format is 32 bpp
[    20.379] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    20.384] (II) NVIDIA(0): Setting mode
[    20.384] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select+1680+0,DFP-1:nvidia-auto-select+0+0"
[    20.421] (II) Loading extension NV-GLX
[    20.556] (==) NVIDIA(0): Disabling shared memory pixmaps
[    20.557] (==) NVIDIA(0): Backing store disabled
[    20.557] (==) NVIDIA(0): Silken mouse enabled
[    20.557] (==) NVIDIA(0): DPMS enabled
[    20.557] (II) Loading extension NV-CONTROL
[    20.557] (II) Loading extension XINERAMA
[    20.557] (II) Loading sub module "dri2"
[    20.557] (II) LoadModule: "dri2"
[    20.557] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    20.557] (II) Module dri2: vendor="X.Org Foundation"
[    20.557] 	compiled for 1.11.3, module version = 1.2.0
[    20.557] 	ABI class: X.Org Server Extension, version 6.0
[    20.557] (II) NVIDIA(0): [DRI2] Setup complete
[    20.557] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    20.558] (==) RandR enabled
[    20.558] (II) Initializing built-in extension Generic Event Extension
[    20.558] (II) Initializing built-in extension SHAPE
[    20.558] (II) Initializing built-in extension MIT-SHM
[    20.558] (II) Initializing built-in extension XInputExtension
[    20.558] (II) Initializing built-in extension XTEST
[    20.558] (II) Initializing built-in extension BIG-REQUESTS
[    20.558] (II) Initializing built-in extension SYNC
[    20.558] (II) Initializing built-in extension XKEYBOARD
[    20.558] (II) Initializing built-in extension XC-MISC
[    20.558] (II) Initializing built-in extension SECURITY
[    20.558] (II) Initializing built-in extension XINERAMA
[    20.558] (II) Initializing built-in extension XFIXES
[    20.558] (II) Initializing built-in extension RENDER
[    20.558] (II) Initializing built-in extension RANDR
[    20.558] (II) Initializing built-in extension COMPOSITE
[    20.558] (II) Initializing built-in extension DAMAGE
[    20.638] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    20.641] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    20.641] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.641] (II) LoadModule: "evdev"
[    20.641] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.663] (II) Module evdev: vendor="X.Org Foundation"
[    20.663] 	compiled for 1.11.3, module version = 2.7.0
[    20.663] 	Module class: X.Org XInput Driver
[    20.663] 	ABI class: X.Org XInput driver, version 16.0
[    20.663] (II) Using input driver 'evdev' for 'Power Button'
[    20.663] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.663] (**) Power Button: always reports core events
[    20.663] (**) evdev: Power Button: Device: "/dev/input/event1"
[    20.663] (--) evdev: Power Button: Vendor 0 Product 0x1
[    20.663] (--) evdev: Power Button: Found keys
[    20.663] (II) evdev: Power Button: Configuring as keyboard
[    20.663] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    20.664] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    20.664] (**) Option "xkb_rules" "evdev"
[    20.664] (**) Option "xkb_model" "pc105"
[    20.664] (**) Option "xkb_layout" "us"
[    20.664] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    20.664] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.664] (II) Using input driver 'evdev' for 'Power Button'
[    20.664] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.664] (**) Power Button: always reports core events
[    20.664] (**) evdev: Power Button: Device: "/dev/input/event0"
[    20.664] (--) evdev: Power Button: Vendor 0 Product 0x1
[    20.664] (--) evdev: Power Button: Found keys
[    20.664] (II) evdev: Power Button: Configuring as keyboard
[    20.664] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    20.664] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    20.664] (**) Option "xkb_rules" "evdev"
[    20.664] (**) Option "xkb_model" "pc105"
[    20.664] (**) Option "xkb_layout" "us"
[    20.665] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event5)
[    20.665] (II) No input driver specified, ignoring this device.
[    20.665] (II) This device may have been added with another device file.
[    20.665] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event6)
[    20.665] (II) No input driver specified, ignoring this device.
[    20.665] (II) This device may have been added with another device file.
[    20.665] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event7)
[    20.665] (II) No input driver specified, ignoring this device.
[    20.665] (II) This device may have been added with another device file.
[    20.665] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event8)
[    20.665] (II) No input driver specified, ignoring this device.
[    20.665] (II) This device may have been added with another device file.
[    20.666] (II) config/udev: Adding input device HDA Intel Line-Out (/dev/input/event9)
[    20.666] (II) No input driver specified, ignoring this device.
[    20.666] (II) This device may have been added with another device file.
[    20.666] (II) config/udev: Adding input device Logitech HID compliant keyboard (/dev/input/event2)
[    20.666] (**) Logitech HID compliant keyboard: Applying InputClass "evdev keyboard catchall"
[    20.666] (II) Using input driver 'evdev' for 'Logitech HID compliant keyboard'
[    20.666] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.666] (**) Logitech HID compliant keyboard: always reports core events
[    20.666] (**) evdev: Logitech HID compliant keyboard: Device: "/dev/input/event2"
[    20.666] (--) evdev: Logitech HID compliant keyboard: Vendor 0x46d Product 0xc30e
[    20.666] (--) evdev: Logitech HID compliant keyboard: Found keys
[    20.666] (II) evdev: Logitech HID compliant keyboard: Configuring as keyboard
[    20.666] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/input/input2/event2"
[    20.666] (II) XINPUT: Adding extended input device "Logitech HID compliant keyboard" (type: KEYBOARD, id 8)
[    20.666] (**) Option "xkb_rules" "evdev"
[    20.666] (**) Option "xkb_model" "pc105"
[    20.666] (**) Option "xkb_layout" "us"
[    20.667] (II) config/udev: Adding input device Logitech HID compliant keyboard (/dev/input/event3)
[    20.667] (**) Logitech HID compliant keyboard: Applying InputClass "evdev keyboard catchall"
[    20.667] (II) Using input driver 'evdev' for 'Logitech HID compliant keyboard'
[    20.667] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.667] (**) Logitech HID compliant keyboard: always reports core events
[    20.667] (**) evdev: Logitech HID compliant keyboard: Device: "/dev/input/event3"
[    20.667] (--) evdev: Logitech HID compliant keyboard: Vendor 0x46d Product 0xc30e
[    20.667] (--) evdev: Logitech HID compliant keyboard: Found 20 mouse buttons
[    20.667] (--) evdev: Logitech HID compliant keyboard: Found keys
[    20.667] (II) evdev: Logitech HID compliant keyboard: Configuring as mouse
[    20.667] (II) evdev: Logitech HID compliant keyboard: Configuring as keyboard
[    20.667] (**) evdev: Logitech HID compliant keyboard: YAxisMapping: buttons 4 and 5
[    20.667] (**) evdev: Logitech HID compliant keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    20.667] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.1/input/input3/event3"
[    20.667] (II) XINPUT: Adding extended input device "Logitech HID compliant keyboard" (type: KEYBOARD, id 9)
[    20.667] (**) Option "xkb_rules" "evdev"
[    20.667] (**) Option "xkb_model" "pc105"
[    20.667] (**) Option "xkb_layout" "us"
[    20.667] (II) config/udev: Adding input device HID 04b4:0033 (/dev/input/event4)
[    20.667] (**) HID 04b4:0033: Applying InputClass "evdev pointer catchall"
[    20.667] (II) Using input driver 'evdev' for 'HID 04b4:0033'
[    20.667] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.668] (**) HID 04b4:0033: always reports core events
[    20.668] (**) evdev: HID 04b4:0033: Device: "/dev/input/event4"
[    20.668] (--) evdev: HID 04b4:0033: Vendor 0x4b4 Product 0x33
[    20.668] (--) evdev: HID 04b4:0033: Found 9 mouse buttons
[    20.668] (--) evdev: HID 04b4:0033: Found scroll wheel(s)
[    20.668] (--) evdev: HID 04b4:0033: Found relative axes
[    20.668] (--) evdev: HID 04b4:0033: Found x and y relative axes
[    20.668] (II) evdev: HID 04b4:0033: Configuring as mouse
[    20.668] (II) evdev: HID 04b4:0033: Adding scrollwheel support
[    20.668] (**) evdev: HID 04b4:0033: YAxisMapping: buttons 4 and 5
[    20.668] (**) evdev: HID 04b4:0033: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    20.668] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/input/input4/event4"
[    20.668] (II) XINPUT: Adding extended input device "HID 04b4:0033" (type: MOUSE, id 10)
[    20.668] (II) evdev: HID 04b4:0033: initialized for relative axes.
[    20.668] (**) HID 04b4:0033: (accel) keeping acceleration scheme 1
[    20.668] (**) HID 04b4:0033: (accel) acceleration profile 0
[    20.668] (**) HID 04b4:0033: (accel) acceleration factor: 2.000
[    20.668] (**) HID 04b4:0033: (accel) acceleration threshold: 4
[    20.668] (II) config/udev: Adding input device HID 04b4:0033 (/dev/input/mouse0)
[    20.668] (II) No input driver specified, ignoring this device.
[    20.668] (II) This device may have been added with another device file.

```


/var/log/lightdm/x-0.log
```

X.Org X Server 1.11.3
Release Date: 2011-12-16
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.42-23-generic x86_64 Ubuntu
Current Operating System: Linux obelix 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic root=UUID=d0841918-eebe-44f8-8e91-a5fef8c700cf ro quiet splash vt.handoff=7
Build Date: 20 April 2012  05:12:02AM
xorg-server 2:1.11.4-0ubuntu10.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.24.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Aug  9 13:31:51 2012
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) Failed to load /usr/lib/xorg/modules/extensions/libglx.so: /usr/lib/xorg/modules/extensions/libglx.so: cannot open shared object file: No such file or directory
(EE) Failed to load module "glx" (loader failed, 7)
(EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
(EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
(EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
(EE) NVIDIA(0):     you continue to encounter problems, Please try
(EE) NVIDIA(0):     reinstalling the NVIDIA driver.

```


/etc/X11/xorg.conf
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 295.33  (buildd@allspice)  Fri Mar 30 13:37:33 UTC 2012

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
    Option         "Xinerama" "0"
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
    Load           "dbe"
    Load           "record"
    Load           "extmod"
    Load           "dri"
    Load           "dri2"
    Load           "glx"
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
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 60.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Monitor Vendor"
    ModelName      "Monitor Model"
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "Monitor Vendor"
    ModelName      "Monitor Model"
EndSection

Section "Monitor"
    Identifier     "Monitor3"
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
        #Option     "VideoKey"           	# <i>
        #Option     "WrappedFB"          	# [<bool>]
        #Option     "GLXVBlank"          	# [<bool>]
        #Option     "ZaphodHeads"        	# <str>
        #Option     "PageFlip"           	# [<bool>]
    Identifier     "Card0"
    Driver         "nouveau"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Card1"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"

        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "Rotate"             	# <str>
        #Option     "fbdev"              	# <str>
        #Option     "debug"              	# [<bool>]
    Identifier     "Card2"
    Driver         "fbdev"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"

        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "DefaultRefresh"     	# [<bool>]
        #Option     "ModeSetClearScreen" 	# [<bool>]
    Identifier     "Card3"
    Driver         "vesa"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9600 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +1680+0, DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Card1"
    Monitor        "Monitor1"
    SubSection     "Display"
        Viewport    0 0
        Depth       1
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
    Identifier     "Screen2"
    Device         "Card2"
    Monitor        "Monitor2"
    SubSection     "Display"
        Viewport    0 0
        Depth       1
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
    Identifier     "Screen3"
    Device         "Card3"
    Monitor        "Monitor3"
    SubSection     "Display"
        Viewport    0 0
        Depth       1
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


```


/home/<username>/
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 295.33  (buildd@allspice)  Fri Mar 30 13:37:33 UTC 2012

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
    Option         "Xinerama" "0"
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
    Load           "dbe"
    Load           "record"
    Load           "extmod"
    Load           "dri"
    Load           "dri2"
    Load           "glx"
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
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 60.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Monitor Vendor"
    ModelName      "Monitor Model"
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "Monitor Vendor"
    ModelName      "Monitor Model"
EndSection

Section "Monitor"
    Identifier     "Monitor3"
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
        #Option     "VideoKey"           	# <i>
        #Option     "WrappedFB"          	# [<bool>]
        #Option     "GLXVBlank"          	# [<bool>]
        #Option     "ZaphodHeads"        	# <str>
        #Option     "PageFlip"           	# [<bool>]
    Identifier     "Card0"
    Driver         "nouveau"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Card1"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"

        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "Rotate"             	# <str>
        #Option     "fbdev"              	# <str>
        #Option     "debug"              	# [<bool>]
    Identifier     "Card2"
    Driver         "fbdev"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"

        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "DefaultRefresh"     	# [<bool>]
        #Option     "ModeSetClearScreen" 	# [<bool>]
    Identifier     "Card3"
    Driver         "vesa"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9600 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +1680+0, DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Card1"
    Monitor        "Monitor1"
    SubSection     "Display"
        Viewport    0 0
        Depth       1
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
    Identifier     "Screen2"
    Device         "Card2"
    Monitor        "Monitor2"
    SubSection     "Display"
        Viewport    0 0
        Depth       1
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
    Identifier     "Screen3"
    Device         "Card3"
    Monitor        "Monitor3"
    SubSection     "Display"
        Viewport    0 0
        Depth       1
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


```


```
xxxx@obelix:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

```


```
xxxx@obelix:~$ uname -a
Linux obelix 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```


```
xxxx@obelix:~$ dpkg --list | grep -i --color nvidia
ii  nvidia-current                         295.40-0ubuntu1                         NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                        295.33-0ubuntu1                         Tool of configuring the NVIDIA graphics driver

```

So what needs fixing?

---

### Post by chkneater on 2012-08-15
8.308] (II) LoadModule: "glx"
[    18.308] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    18.308] (EE) Failed to load /usr/lib/xorg/modules/extensions/libglx.so: /usr/lib/xorg/modules/extensions/libglx.so: cannot open shared object file: No such file or directory
[    18.308] (II) UnloadModule: "glx"
[    18.308] (II) Unloading glx
[    18.308] (EE) Failed to load module "glx" (loader failed, 



Well, I copied this from your x.log and noticed this.  It looks like you don't have the 'libglx.so' extension form some reason.  Try:

sudo apt-get install libglx.so

---

