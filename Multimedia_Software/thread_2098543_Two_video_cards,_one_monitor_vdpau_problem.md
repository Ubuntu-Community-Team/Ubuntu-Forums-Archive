---
title: "Two video cards, one monitor vdpau problem"
date: 2012-12-26
forum: Multimedia Software
---

### Post by diskmaster23 on 2012-12-26
I have two video cards, but only one monitor.

One is a NVIDIA GPU GeForce 6200, AGP, second is a NVIDIA GPU GeForce 8400GS, PCI. The AGP card is hooked up to my monitor.

I bought the second one for VDPAU decoding. I was having trouble with my system crashing without the VDPAU. 

I took out the AGP card to start with and put in the PCI card. Booted up fine. Configured my Xorg configuration. Ran vdpauinfo. Watched a movie. Not a single crash.

Decided I was going to put back in the AGP card. Booted up. Configured the xorg. Ran vdpauinfo, but got nothing. How do I know that my XBMC app is going to use the vdpau and not my CPU? 

How do I pull up the information of my PCI card in vdpauinfo?

Thanks!

Xorg.0.log
```
[   667.330] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[   667.330] X Protocol Version 11, Revision 0
[   667.330] Build Operating System: Linux 3.2.0-26-generic i686 Ubuntu
[   667.330] Current Operating System: Linux legia 3.5.0-19-generic #30-Ubuntu SMP Tue Nov 13 17:49:53 UTC 2012 i686
[   667.330] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-19-generic root=UUID=0d6b36f5-0ba9-440d-a04a-026f149e1d13 ro crashkernel=384M-2G:64M,2G-:128M quiet splash vmalloc=256MB vt.handoff=7
[   667.330] Build Date: 27 November 2012  07:44:37AM
[   667.330] xorg-server 2:1.13.0-0ubuntu6.1 (For technical support please see http://www.ubuntu.com/support) 
[   667.330] Current version of pixman: 0.26.0
[   667.330] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   667.330] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   667.330] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 26 22:12:00 2012
[   667.330] (==) Using config file: "/etc/X11/xorg.conf"
[   667.330] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   667.369] (==) ServerLayout "Layout0"
[   667.369] (**) |-->Screen "Screen0" (0)
[   667.369] (**) |   |-->Monitor "Monitor0"
[   667.369] (**) |   |-->Device "Device0"
[   667.369] (**) |-->Input Device "Keyboard0"
[   667.369] (**) |-->Input Device "Mouse0"
[   667.369] (==) Automatically adding devices
[   667.369] (==) Automatically enabling devices
[   667.369] (==) Automatically adding GPU devices
[   667.369] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   667.369] 	Entry deleted from font path.
[   667.369] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   667.369] 	Entry deleted from font path.
[   667.369] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   667.369] 	Entry deleted from font path.
[   667.369] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   667.369] 	Entry deleted from font path.
[   667.369] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   667.369] 	Entry deleted from font path.
[   667.369] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[   667.369] 	Entry deleted from font path.
[   667.369] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[   667.369] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   667.369] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[   667.369] (WW) Disabling Keyboard0
[   667.369] (WW) Disabling Mouse0
[   667.370] (II) Loader magic: 0xb778b640
[   667.370] (II) Module ABI versions:
[   667.370] 	X.Org ANSI C Emulation: 0.4
[   667.370] 	X.Org Video Driver: 13.0
[   667.370] 	X.Org XInput driver : 18.0
[   667.370] 	X.Org Server Extension : 7.0
[   667.371] (--) PCI:*(0:1:0:0) 10de:0221:3842:a401 rev 161, Mem @ 0xf7000000/16777216, 0xb0000000/268435456, 0xf8000000/16777216, BIOS @ 0x????????/131072
[   667.371] (--) PCI: (0:2:9:0) 4444:0016:0070:8003 rev 1, Mem @ 0xe0000000/67108864
[   667.371] (--) PCI: (0:3:0:0) 10de:10c3:0000:0000 rev 162, Mem @ 0xf2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00008000/128, BIOS @ 0x????????/524288
[   667.371] (II) Open ACPI successful (/var/run/acpid.socket)
[   667.371] Initializing built-in extension Generic Event Extension
[   667.372] Initializing built-in extension SHAPE
[   667.372] Initializing built-in extension MIT-SHM
[   667.372] Initializing built-in extension XInputExtension
[   667.372] Initializing built-in extension XTEST
[   667.372] Initializing built-in extension BIG-REQUESTS
[   667.372] Initializing built-in extension SYNC
[   667.372] Initializing built-in extension XKEYBOARD
[   667.372] Initializing built-in extension XC-MISC
[   667.372] Initializing built-in extension SECURITY
[   667.372] Initializing built-in extension XINERAMA
[   667.372] Initializing built-in extension XFIXES
[   667.372] Initializing built-in extension RENDER
[   667.372] Initializing built-in extension RANDR
[   667.372] Initializing built-in extension COMPOSITE
[   667.372] Initializing built-in extension DAMAGE
[   667.372] Initializing built-in extension MIT-SCREEN-SAVER
[   667.372] Initializing built-in extension DOUBLE-BUFFER
[   667.372] Initializing built-in extension RECORD
[   667.372] Initializing built-in extension DPMS
[   667.372] Initializing built-in extension X-Resource
[   667.372] Initializing built-in extension XVideo
[   667.372] Initializing built-in extension XVideo-MotionCompensation
[   667.372] Initializing built-in extension XFree86-VidModeExtension
[   667.372] Initializing built-in extension XFree86-DGA
[   667.372] Initializing built-in extension XFree86-DRI
[   667.372] Initializing built-in extension DRI2
[   667.372] (II) LoadModule: "glx"
[   667.372] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/libglx.so
[   667.414] (II) Module glx: vendor="NVIDIA Corporation"
[   667.414] 	compiled for 4.0.2, module version = 1.0.0
[   667.414] 	Module class: X.Org Server Extension
[   667.414] (II) NVIDIA GLX Module  304.64  Tue Oct 30 11:31:18 PDT 2012
[   667.414] Loading extension GLX
[   667.414] (II) LoadModule: "nvidia"
[   667.414] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/nvidia_drv.so
[   667.415] (II) Module nvidia: vendor="NVIDIA Corporation"
[   667.415] 	compiled for 4.0.2, module version = 1.0.0
[   667.415] 	Module class: X.Org Video Driver
[   667.415] (II) NVIDIA dlloader X Driver  304.64  Tue Oct 30 11:11:05 PDT 2012
[   667.415] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   667.415] (++) using VT number 7

[   667.416] (II) Loading sub module "fb"
[   667.416] (II) LoadModule: "fb"
[   667.416] (II) Loading /usr/lib/xorg/modules/libfb.so
[   667.416] (II) Module fb: vendor="X.Org Foundation"
[   667.416] 	compiled for 1.13.0, module version = 1.0.0
[   667.416] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   667.416] (II) Loading sub module "wfb"
[   667.416] (II) LoadModule: "wfb"
[   667.416] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   667.416] (II) Module wfb: vendor="X.Org Foundation"
[   667.416] 	compiled for 1.13.0, module version = 1.0.0
[   667.416] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   667.416] (II) Loading sub module "ramdac"
[   667.416] (II) LoadModule: "ramdac"
[   667.416] (II) Module "ramdac" already built-in
[   667.417] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[   667.417] (==) NVIDIA(0): RGB weight 888
[   667.417] (==) NVIDIA(0): Default visual is TrueColor
[   667.417] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   667.417] (**) NVIDIA(0): Option "RenderAccel" "true"
[   667.417] (**) NVIDIA(0): Enabling RENDER acceleration
[   667.417] (**) NVIDIA(0): Option "UseEvents" "false"
[   667.417] (**) NVIDIA(0): Enabling 2D acceleration
[   667.559] (II) NVIDIA(GPU-0): Display (WDT VR-3225 (CRT-0)) does not support NVIDIA 3D
[   667.790] (II) NVIDIA(GPU-0):     Vision stereo.
[   667.794] (II) NVIDIA(0): NVIDIA GPU GeForce 6200 (NV44) at PCI:1:0:0 (GPU-0)
[   667.794] (--) NVIDIA(0): Memory: 262144 kBytes
[   667.794] (--) NVIDIA(0): VideoBIOS: 05.44.a2.10.40
[   667.794] (II) NVIDIA(0): Detected AGP rate: 8X
[   667.794] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[   667.794] (--) NVIDIA(0): Valid display device(s) on GeForce 6200 at PCI:1:0:0
[   667.794] (--) NVIDIA(0):     WDT VR-3225 (CRT-0) (connected)
[   667.794] (--) NVIDIA(0):     CRT-1
[   667.794] (--) NVIDIA(0):     TV-0
[   667.794] (--) NVIDIA(0):     DFP-0
[   667.794] (--) NVIDIA(0): WDT VR-3225 (CRT-0): 400.0 MHz maximum pixel clock
[   667.794] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[   667.794] (--) NVIDIA(0): TV-0: 400.0 MHz maximum pixel clock
[   667.794] (--) NVIDIA(0): TV encoder: (null)
[   667.794] (--) NVIDIA(0): DFP-0: 155.0 MHz maximum pixel clock
[   667.794] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
[   667.794] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   667.794] (**) NVIDIA(0):     device WDT VR-3225 (CRT-0) (Using EDID frequencies has
[   667.794] (**) NVIDIA(0):     been enabled on all display devices.)
[   667.794] (==) NVIDIA(0): 
[   667.794] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[   667.794] (==) NVIDIA(0):     will be used as the requested mode.
[   667.794] (==) NVIDIA(0): 
[   667.794] (II) NVIDIA(0): Validated MetaModes:
[   667.794] (II) NVIDIA(0):     "CRT-0:nvidia-auto-select"
[   667.794] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[   667.797] (WW) NVIDIA(0): Unable to support custom viewPortOut 1920 x 1080 +0 +0
[   667.797] (--) NVIDIA(0): DPI set to (68, 68); computed from "UseEdidDpi" X config
[   667.797] (--) NVIDIA(0):     option
[   667.797] (--) Depth 24 pixmap format is 32 bpp
[   667.842] (II) NVIDIA(GPU-1): NVIDIA GPU GeForce 8400GS (GT218) at PCI:3:0:0 (GPU-1)
[   667.842] (--) NVIDIA(GPU-1): Memory: 262144 kBytes
[   667.842] (--) NVIDIA(GPU-1): VideoBIOS: 70.18.76.00.21
[   667.842] (II) NVIDIA(GPU-1): Detected PCI Express Link width: 16X
[   667.842] (--) NVIDIA(GPU-1): Interlaced video modes are supported on this GPU
[   667.842] (--) NVIDIA(GPU-1): Valid display device(s) on GeForce 8400GS at PCI:3:0:0
[   667.842] (--) NVIDIA(GPU-1):     CRT-0
[   667.842] (--) NVIDIA(GPU-1):     CRT-1
[   667.842] (--) NVIDIA(GPU-1):     DFP-0
[   667.842] (--) NVIDIA(GPU-1):     DFP-1
[   667.842] (--) NVIDIA(GPU-1): CRT-0: 400.0 MHz maximum pixel clock
[   667.842] (--) NVIDIA(GPU-1): CRT-1: 400.0 MHz maximum pixel clock
[   667.842] (--) NVIDIA(GPU-1): DFP-0: 330.0 MHz maximum pixel clock
[   667.842] (--) NVIDIA(GPU-1): DFP-0: Internal Single Link TMDS
[   667.842] (--) NVIDIA(GPU-1): DFP-1: 165.0 MHz maximum pixel clock
[   667.842] (--) NVIDIA(GPU-1): DFP-1: Internal Single Link TMDS
[   667.861] (II) NVIDIA(0): Setting mode "CRT-0:nvidia-auto-select"
[   667.949] Loading extension NV-GLX
[   667.991] (==) NVIDIA(0): Disabling shared memory pixmaps
[   667.991] (==) NVIDIA(0): Backing store disabled
[   667.991] (==) NVIDIA(0): Silken mouse enabled
[   667.991] (**) NVIDIA(0): DPMS enabled
[   667.991] Loading extension NV-CONTROL
[   667.992] Loading extension XINERAMA
[   667.992] (II) Loading sub module "dri2"
[   667.992] (II) LoadModule: "dri2"
[   667.992] (II) Module "dri2" already built-in
[   667.992] (II) NVIDIA(0): [DRI2] Setup complete
[   667.992] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[   667.992] (--) RandR disabled
[   668.003] (II) Initializing extension GLX
[   668.026] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   668.029] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   668.029] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   668.029] (II) LoadModule: "evdev"
[   668.030] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   668.030] (II) Module evdev: vendor="X.Org Foundation"
[   668.030] 	compiled for 1.13.0, module version = 2.7.3
[   668.030] 	Module class: X.Org XInput Driver
[   668.030] 	ABI class: X.Org XInput driver, version 18.0
[   668.030] (II) Using input driver 'evdev' for 'Power Button'
[   668.030] (**) Power Button: always reports core events
[   668.030] (**) evdev: Power Button: Device: "/dev/input/event1"
[   668.030] (--) evdev: Power Button: Vendor 0 Product 0x1
[   668.030] (--) evdev: Power Button: Found keys
[   668.030] (II) evdev: Power Button: Configuring as keyboard
[   668.030] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[   668.030] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   668.030] (**) Option "xkb_rules" "evdev"
[   668.030] (**) Option "xkb_model" "pc105"
[   668.030] (**) Option "xkb_layout" "us"
[   668.031] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   668.031] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   668.031] (II) Using input driver 'evdev' for 'Power Button'
[   668.031] (**) Power Button: always reports core events
[   668.031] (**) evdev: Power Button: Device: "/dev/input/event0"
[   668.031] (--) evdev: Power Button: Vendor 0 Product 0x1
[   668.031] (--) evdev: Power Button: Found keys
[   668.031] (II) evdev: Power Button: Configuring as keyboard
[   668.031] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[   668.031] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[   668.031] (**) Option "xkb_rules" "evdev"
[   668.031] (**) Option "xkb_model" "pc105"
[   668.031] (**) Option "xkb_layout" "us"
[   668.032] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/event3)
[   668.032] (**) Logitech USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[   668.032] (II) Using input driver 'evdev' for 'Logitech USB Optical Mouse'
[   668.032] (**) Logitech USB Optical Mouse: always reports core events
[   668.032] (**) evdev: Logitech USB Optical Mouse: Device: "/dev/input/event3"
[   668.032] (--) evdev: Logitech USB Optical Mouse: Vendor 0x46d Product 0xc00c
[   668.032] (--) evdev: Logitech USB Optical Mouse: Found 3 mouse buttons
[   668.032] (--) evdev: Logitech USB Optical Mouse: Found scroll wheel(s)
[   668.032] (--) evdev: Logitech USB Optical Mouse: Found relative axes
[   668.032] (--) evdev: Logitech USB Optical Mouse: Found x and y relative axes
[   668.032] (II) evdev: Logitech USB Optical Mouse: Configuring as mouse
[   668.033] (II) evdev: Logitech USB Optical Mouse: Adding scrollwheel support
[   668.033] (**) evdev: Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
[   668.033] (**) evdev: Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   668.033] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.1/usb3/3-1/3-1:1.0/input/input3/event3"
[   668.033] (II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE, id 8)
[   668.033] (II) evdev: Logitech USB Optical Mouse: initialized for relative axes.
[   668.033] (**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
[   668.033] (**) Logitech USB Optical Mouse: (accel) acceleration profile 0
[   668.033] (**) Logitech USB Optical Mouse: (accel) acceleration factor: 2.000
[   668.033] (**) Logitech USB Optical Mouse: (accel) acceleration threshold: 4
[   668.033] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse0)
[   668.033] (II) No input driver specified, ignoring this device.
[   668.033] (II) This device may have been added with another device file.
[   668.033] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event4)
[   668.034] (II) No input driver specified, ignoring this device.
[   668.034] (II) This device may have been added with another device file.
[   668.034] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event5)
[   668.034] (II) No input driver specified, ignoring this device.
[   668.034] (II) This device may have been added with another device file.
[   668.034] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event6)
[   668.034] (II) No input driver specified, ignoring this device.
[   668.034] (II) This device may have been added with another device file.
[   668.034] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event7)
[   668.034] (II) No input driver specified, ignoring this device.
[   668.034] (II) This device may have been added with another device file.
[   668.035] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[   668.035] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   668.035] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   668.035] (**) AT Translated Set 2 keyboard: always reports core events
[   668.035] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[   668.035] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[   668.035] (--) evdev: AT Translated Set 2 keyboard: Found keys
[   668.035] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[   668.035] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[   668.035] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[   668.035] (**) Option "xkb_rules" "evdev"
[   668.035] (**) Option "xkb_model" "pc105"
[   668.035] (**) Option "xkb_layout" "us"
[   668.038] (II) config/udev: Adding input device i2c IR (Hauppauge WinTV PVR-150 (/dev/input/event8)
[   668.038] (**) i2c IR (Hauppauge WinTV PVR-150: Ignoring device from InputClass "i2c IR (Hauppauge WinTV PVR-150"
[   669.928] (II) NVIDIA(GPU-0): Display (WDT VR-3225 (CRT-0)) does not support NVIDIA 3D
[   669.928] (II) NVIDIA(GPU-0):     Vision stereo.
[   669.928] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   669.928] (**) NVIDIA(0):     device WDT VR-3225 (CRT-0) (Using EDID frequencies has
[   669.928] (**) NVIDIA(0):     been enabled on all display devices.)
[   670.368] (II) NVIDIA(GPU-0): Display (WDT VR-3225 (CRT-0)) does not support NVIDIA 3D
[   670.368] (II) NVIDIA(GPU-0):     Vision stereo.
[   670.368] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   670.368] (**) NVIDIA(0):     device WDT VR-3225 (CRT-0) (Using EDID frequencies has
[   670.368] (**) NVIDIA(0):     been enabled on all display devices.)
```

xorg.conf
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@swio-display-x86-rh72-02.nvidia.com)  Tue Sep 11 12:34:48 PDT 2012


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputClass"
  Identifier "i2c IR (Hauppauge WinTV PVR-150"
  MatchProduct "i2c IR (Hauppauge WinTV PVR-150"
  MatchIsKeyboard "true"
  Option "Ignore" "true"
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
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
     Identifier     "Device0"
     BusID          "PCI:1:0:0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option         "UseEvents" "false"
    Option "DPMS" "yes"
    Option  "RenderAccel" "true"
EndSection

Section "Device"
     Identifier     "Device1"
     BusID          "PCI:3:0:0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option         "UseEvents" "false"
    Option "DPMS" "yes"
    Option  "RenderAccel" "true"
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
```

---

### Post by diskmaster23 on 2012-12-27
Bumping.

---

### Post by diskmaster23 on 2012-12-30
Bumping.

---

### Post by gordintoronto on 2012-12-30
"Decided I was going to put back in the AGP card..."

Why?

---

### Post by diskmaster23 on 2012-12-30
> **gordintoronto said:**
> "Decided I was going to put back in the AGP card..."

Why?

I had this idea that I could use the AGP card to do the normal graphics and I can have the PCI card do the decoding in the background.

---

### Post by diskmaster23 on 2013-01-02
Bump.

---

### Post by diskmaster23 on 2013-01-04
Bump

---

### Post by dannyboy79 on 2013-01-04
NO, it won't work that way sorry. Choose one graphics card or the other.

---

### Post by diskmaster23 on 2013-01-04
I thought that it could be done that way because of Folding@Home or Bitcoin mining using the GPU for such applications like . Thought maybe that video decoding could work the same way?

But if it cannot be done then that is fine.

---

