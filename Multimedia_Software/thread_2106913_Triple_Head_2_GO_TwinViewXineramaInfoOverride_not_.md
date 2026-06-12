---
title: "Triple Head 2 GO TwinViewXineramaInfoOverride not working"
date: 2013-01-20
forum: Multimedia Software
---

### Post by dillzz on 2013-01-20
Greetings! I have the triple head 2 go with three identical 24" monitors hooked up. I have been running this setup for a couple years now without a hiccup. I upgraded and loaded up the nvidia driver and updated my xorg.conf. I used to have 3 x 1920x1200 X screens. I now see 1 1920x1200 and 1 3840x1200. I have not changed my configuration, any thoughts?

Section "ServerLayout"
Identifier "Default Layout"
Screen 0 "Screen0" 0 0
EndSection

Section "Module"
Load "glx"
EndSection

Section "Monitor"
Identifier "Monitor0"
ModeLine "1920x1200" 154.00 1920 1968 2000 2080 1200 1203 1209 1235 +HSync +HSync
ModeLine "3840x1200" 308.00 3840 3904 3968 4160 1200 1203 1213 1235 +HSync +VSync
HorizSync 30-83
VertRefresh 56-76
EndSection

Section "Device"
Identifier "Videocard0"
Driver "nvidia"
VendorName "Leadtek"
BoardName "9600GT"
# Option "Coolbits" "4"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Videocard0"
Monitor "Monitor0"
DefaultDepth 24
Option "UseEDID" "False"
Option "ExactModeTimingsDVI" "True"
Option "NoLogo" "True"
Option "TwinView" "True"
Option "TwinViewOrientation" "RightOf"
Option "TwinviewXineramaInfo" "True"
Option "TwinViewXineramaInfoOverride" "1920x1200+0+0, 1920x1200+1920+0, 1920x1200+3840+0"
Option "DynamicTwinView" "False"
Option "MetaModes" "1920x1200,3840x1200"
Option "SecondMonitorHorizSync" "30-83"
Option "SecondMonitorVertRefresh" "56-76"
SubSection "Display"
Viewport 0 0
Depth 24
Modes "3840x1200"
EndSubSection
EndSection



Relevant Xorg.0.log
X.Org X Server 1.13.1
Release Date: 2012-12-13
[ 8.657] X Protocol Version 11, Revision 0
[ 8.657] Build Operating System: 2.6.32-279.9.1.el6.x86_64 
[ 8.657] Build Date: 09 January 2013 03:42:52AM
[ 8.657] Build ID: xorg-x11-server 1.13.1-4.fc18 
[ 8.657] Current version of pixman: 0.26.2
[ 8.657] Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
to make sure that you have the latest version.
[ 8.658] Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[ 8.658] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Jan 20 06:44:08 2013
[ 8.658] (==) Using config file: "/etc/X11/xorg.conf"
[ 8.658] (==) Using config directory: "/etc/X11/xorg.conf.d"
[ 8.658] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[ 8.658] (==) ServerLayout "Default Layout"
[ 8.658] (**) |-->Screen "Screen0" (0)
[ 8.658] (**) | |-->Monitor "Monitor0"
[ 8.658] (**) | |-->Device "Videocard0"
[ 8.658] (==) Automatically adding devices
[ 8.658] (==) Automatically enabling devices
[ 8.658] (==) Automatically adding GPU devices
[ 8.658] (==) FontPath set to:
catalogue:/etc/X11/fontpath.d,
built-ins
[ 8.658] (**) ModulePath set to "/usr/lib64/nvidia/xorg,/usr/lib64/xorg/modules"
[ 8.658] (II) The server relies on udev to provide the list of input devices.
If no devices become available, reconfigure udev or disable AutoAddDevices.
[ 8.658] (II) Loader magic: 0x801ce0
[ 8.658] (II) Module ABI versions:
[ 8.658] X.Org ANSI C Emulation: 0.4
[ 8.658] X.Org Video Driver: 13.1
[ 8.658] X.Org XInput driver : 18.0
[ 8.658] X.Org Server Extension : 7.0
[ 8.660] (--) PCI:*(0:1:0:0) 10de:06cd:10de:079f rev 163, Mem @ 0xf4000000/33554432, 0xe0000000/134217728, 0xe8000000/67108864, I/O @ 0x0000a000/128, BIOS @ 0x????????/524288
[ 8.660] Initializing built-in extension Generic Event Extension
[ 8.660] Initializing built-in extension SHAPE
[ 8.660] Initializing built-in extension MIT-SHM
[ 8.660] Initializing built-in extension XInputExtension
[ 8.660] Initializing built-in extension XTEST
[ 8.660] Initializing built-in extension BIG-REQUESTS
[ 8.660] Initializing built-in extension SYNC
[ 8.660] Initializing built-in extension XKEYBOARD
[ 8.660] Initializing built-in extension XC-MISC
[ 8.660] Initializing built-in extension XINERAMA
[ 8.660] Initializing built-in extension XFIXES
[ 8.660] Initializing built-in extension RENDER
[ 8.660] Initializing built-in extension RANDR
[ 8.660] Initializing built-in extension COMPOSITE
[ 8.660] Initializing built-in extension DAMAGE
[ 8.660] Initializing built-in extension MIT-SCREEN-SAVER
[ 8.660] Initializing built-in extension DOUBLE-BUFFER
[ 8.660] Initializing built-in extension RECORD
[ 8.660] Initializing built-in extension DPMS
[ 8.660] Initializing built-in extension X-Resource
[ 8.660] Initializing built-in extension XVideo
[ 8.660] Initializing built-in extension XVideo-MotionCompensation
[ 8.660] Initializing built-in extension SELinux
[ 8.660] Initializing built-in extension XFree86-VidModeExtension
[ 8.660] Initializing built-in extension XFree86-DGA
[ 8.660] Initializing built-in extension XFree86-DRI
[ 8.660] Initializing built-in extension DRI2
[ 8.660] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[ 8.660] (II) LoadModule: "glx"
[ 8.660] (II) Loading /usr/lib64/nvidia/xorg/libglx.so
[ 8.677] (II) Module glx: vendor="NVIDIA Corporation"
[ 8.677] compiled for 4.0.2, module version = 1.0.0
[ 8.677] Module class: X.Org Server Extension
[ 8.677] (II) NVIDIA GLX Module 304.64 Tue Oct 30 11:18:32 PDT 2012
[ 8.677] Loading extension GLX
[ 8.677] (II) LoadModule: "nvidia"
[ 8.677] (II) Loading /usr/lib64/xorg/modules/drivers/nvidia_drv.so
[ 8.678] (II) Module nvidia: vendor="NVIDIA Corporation"
[ 8.678] compiled for 4.0.2, module version = 1.0.0
[ 8.678] Module class: X.Org Video Driver
[ 8.678] (II) NVIDIA dlloader X Driver 304.64 Tue Oct 30 10:59:51 PDT 2012
[ 8.678] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[ 8.678] (++) using VT number 1

[ 8.680] (II) Loading sub module "fb"
[ 8.680] (II) LoadModule: "fb"
[ 8.681] (II) Loading /usr/lib64/xorg/modules/libfb.so
[ 8.681] (II) Module fb: vendor="X.Org Foundation"
[ 8.681] compiled for 1.13.1, module version = 1.0.0
[ 8.681] ABI class: X.Org ANSI C Emulation, version 0.4
[ 8.681] (II) Loading sub module "wfb"
[ 8.681] (II) LoadModule: "wfb"
[ 8.681] (II) Loading /usr/lib64/xorg/modules/libwfb.so
[ 8.681] (II) Module wfb: vendor="X.Org Foundation"
[ 8.681] compiled for 1.13.1, module version = 1.0.0
[ 8.681] ABI class: X.Org ANSI C Emulation, version 0.4
[ 8.681] (II) Loading sub module "ramdac"
[ 8.681] (II) LoadModule: "ramdac"
[ 8.681] (II) Module "ramdac" already built-in
[ 8.681] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[ 8.681] (==) NVIDIA(0): RGB weight 888
[ 8.681] (==) NVIDIA(0): Default visual is TrueColor
[ 8.681] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[ 8.681] (**) NVIDIA(0): Option "NoLogo" "True"
[ 8.681] (**) NVIDIA(0): Option "TwinViewOrientation" "RightOf"
[ 8.681] (**) NVIDIA(0): Option "twinviewxineramainfo" "True"
[ 8.681] (**) NVIDIA(0): Option "TwinViewXineramaInfoOverride" "1920x1200+0+0, 1920x1200+1920+0, 1920x1200+3840+0"
[ 8.681] (**) NVIDIA(0): Option "ExactModeTimingsDVI" "True"
[ 8.681] (**) NVIDIA(0): Option "DynamicTwinView" "False"
[ 8.681] (**) NVIDIA(0): Option "UseEDID" "False"
[ 8.681] (**) NVIDIA(0): Option "MetaModes" "1920x1200,3840x1200"
[ 8.681] (**) NVIDIA(0): Enabling 2D acceleration
[ 8.681] (**) NVIDIA(0): Ignoring EDIDs
[ 9.364] (II) NVIDIA(GPU-0): Not probing EDID on DFP-0.
[ 9.379] (II) NVIDIA(GPU-0): Not probing EDID on DFP-2.
[ 9.380] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 470 (GF100) at PCI:1:0:0 (GPU-0)
[ 9.380] (--) NVIDIA(0): Memory: 1310720 kBytes
[ 9.380] (--) NVIDIA(0): VideoBIOS: 70.00.21.00.03
[ 9.380] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[ 9.380] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[ 9.382] (--) NVIDIA(0): Valid display device(s) on GeForce GTX 470 at PCI:1:0:0
[ 9.382] (--) NVIDIA(0): CRT-0
[ 9.382] (--) NVIDIA(0): CRT-1
[ 9.382] (--) NVIDIA(0): DFP-0 (connected)
[ 9.382] (--) NVIDIA(0): DFP-1
[ 9.382] (--) NVIDIA(0): DFP-2 (connected)
[ 9.382] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[ 9.382] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[ 9.382] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[ 9.382] (--) NVIDIA(0): DFP-0: Internal Dual Link TMDS
[ 9.382] (--) NVIDIA(0): DFP-1: 165.0 MHz maximum pixel clock
[ 9.382] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[ 9.382] (--) NVIDIA(0): DFP-2: 330.0 MHz maximum pixel clock
[ 9.382] (--) NVIDIA(0): DFP-2: Internal Dual Link TMDS
[ 9.382] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[ 9.382] (**) NVIDIA(0): device DFP-0 (Using EDID frequencies has been enabled on
[ 9.382] (**) NVIDIA(0): all display devices.)
[ 9.392] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[ 9.392] (**) NVIDIA(0): device DFP-2 (Using EDID frequencies has been enabled on
[ 9.392] (**) NVIDIA(0): all display devices.)
[ 9.402] (II) NVIDIA(0): Validated MetaModes:
[ 9.402] (II) NVIDIA(0): "1920x1200,3840x1200"
[ 9.402] (II) NVIDIA(0): Virtual screen size determined to be 5760 x 1200
[ 9.436] (WW) NVIDIA(0): Unable to get display device DFP-0's EDID; cannot compute DPI
[ 9.436] (WW) NVIDIA(0): from DFP-0's EDID.
[ 9.436] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[ 9.436] (--) Depth 24 pixmap format is 32 bpp
[ 9.436] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[ 9.436] (II) NVIDIA: access.
[ 9.440] (II) NVIDIA(0): ACPI: failed to connect to the ACPI event daemon; the daemon
[ 9.440] (II) NVIDIA(0): may not be running or the "AcpidSocketPath" X
[ 9.440] (II) NVIDIA(0): configuration option may not be set correctly. When the
[ 9.440] (II) NVIDIA(0): ACPI event daemon is available, the NVIDIA X driver will
[ 9.440] (II) NVIDIA(0): try to use it to receive ACPI event notifications. For
[ 9.440] (II) NVIDIA(0): details, please see the "ConnectToAcpid" and
[ 9.440] (II) NVIDIA(0): "AcpidSocketPath" X configuration options in Appendix B: X
[ 9.440] (II) NVIDIA(0): Config Options in the README.
[ 9.442] (II) NVIDIA(0): Setting mode "1920x1200,3840x1200"
[ 9.515] Loading extension NV-GLX
[ 9.625] (==) NVIDIA(0): Disabling shared memory pixmaps
[ 9.625] (==) NVIDIA(0): Backing store disabled
[ 9.625] (==) NVIDIA(0): Silken mouse enabled
[ 9.625] (==) NVIDIA(0): DPMS enabled
[ 9.626] Loading extension NV-CONTROL
[ 9.626] Loading extension XINERAMA
[ 9.626] (WW) NVIDIA(0): Option "TwinView" is not used
[ 9.626] (WW) NVIDIA(0): Option "SecondMonitorHorizSync" is not used
[ 9.626] (WW) NVIDIA(0): Option "SecondMonitorVertRefresh" is not used
[ 9.626] (II) Loading sub module "dri2"
[ 9.626] (II) LoadModule: "dri2"
[ 9.626] (II) Module "dri2" already built-in
[ 9.626] (II) NVIDIA(0): [DRI2] Setup complete
[ 9.626] (II) NVIDIA(0): [DRI2] VDPAU driver: nvidia
[ 9.626] (--) RandR disabled
[ 9.631] (II) SELinux: Disabled by boolean
[ 9.632] (II) Initializing extension GLX
[ 9.690] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[ 9.690] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 9.691] (**) Power Button: Applying InputClass "anaconda-keyboard"
[ 9.691] (II) LoadModule: "evdev"
[ 9.691] (II) Loading /usr/lib64/xorg/modules/input/evdev_drv.so
[ 9.691] (II) Module evdev: vendor="X.Org Foundation"
[ 9.691] compiled for 1.13.0, module version = 2.7.3
[ 9.691] Module class: X.Org XInput Driver
[ 9.691] ABI class: X.Org XInput driver, version 18.0
[ 9.691] (II) Using input driver 'evdev' for 'Power Button'
[ 9.691] (**) Power Button: always reports core events
[ 9.691] (**) evdev: Power Button: Device: "/dev/input/event1"
[ 9.691] (--) evdev: Power Button: Vendor 0 Product 0x1
[ 9.691] (--) evdev: Power Button: Found keys
[ 9.691] (II) evdev: Power Button: Configuring as keyboard
[ 9.691] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[ 9.691] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[ 9.691] (**) Option "xkb_rules" "evdev"
[ 9.691] (**) Option "xkb_model" "evdev"
[ 9.691] (**) Option "xkb_layout" "us"
[ 9.713] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[ 9.713] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 9.713] (**) Power Button: Applying InputClass "anaconda-keyboard"
[ 9.713] (II) Using input driver 'evdev' for 'Power Button'
[ 9.713] (**) Power Button: always reports core events
[ 9.713] (**) evdev: Power Button: Device: "/dev/input/event0"
[ 9.713] (--) evdev: Power Button: Vendor 0 Product 0x1
[ 9.713] (--) evdev: Power Button: Found keys
[ 9.713] (II) evdev: Power Button: Configuring as keyboard
[ 9.713] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[ 9.713] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[ 9.713] (**) Option "xkb_rules" "evdev"
[ 9.713] (**) Option "xkb_model" "evdev"
[ 9.713] (**) Option "xkb_layout" "us"
[ 9.714] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event4)
[ 9.714] (II) No input driver specified, ignoring this device.
[ 9.714] (II) This device may have been added with another device file.
[ 9.714] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event5)
[ 9.714] (II) No input driver specified, ignoring this device.
[ 9.714] (II) This device may have been added with another device file.
[ 9.714] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event6)
[ 9.714] (II) No input driver specified, ignoring this device.
[ 9.714] (II) This device may have been added with another device file.
[ 9.714] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event7)
[ 9.714] (II) No input driver specified, ignoring this device.
[ 9.714] (II) This device may have been added with another device file.
[ 9.715] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:4002 (/dev/input/event2)
[ 9.715] (**) Logitech Unifying Device. Wireless PID:4002: Applying InputClass "evdev keyboard catchall"
[ 9.715] (**) Logitech Unifying Device. Wireless PID:4002: Applying InputClass "anaconda-keyboard"
[ 9.715] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:4002'
[ 9.715] (**) Logitech Unifying Device. Wireless PID:4002: always reports core events
[ 9.715] (**) evdev: Logitech Unifying Device. Wireless PID:4002: Device: "/dev/input/event2"
[ 9.715] (--) evdev: Logitech Unifying Device. Wireless PID:4002: Vendor 0x46d Product 0xc52b
[ 9.715] (--) evdev: Logitech Unifying Device. Wireless PID:4002: Found 1 mouse buttons
[ 9.715] (--) evdev: Logitech Unifying Device. Wireless PID:4002: Found scroll wheel(s)
[ 9.715] (--) evdev: Logitech Unifying Device. Wireless PID:4002: Found relative axes
[ 9.715] (II) evdev: Logitech Unifying Device. Wireless PID:4002: Forcing relative x/y axes to exist.
[ 9.715] (--) evdev: Logitech Unifying Device. Wireless PID:4002: Found absolute axes
[ 9.715] (II) evdev: Logitech Unifying Device. Wireless PID:4002: Forcing absolute x/y axes to exist.
[ 9.715] (--) evdev: Logitech Unifying Device. Wireless PID:4002: Found keys
[ 9.715] (II) evdev: Logitech Unifying Device. Wireless PID:4002: Configuring as mouse
[ 9.715] (II) evdev: Logitech Unifying Device. Wireless PID:4002: Configuring as keyboard
[ 9.715] (II) evdev: Logitech Unifying Device. Wireless PID:4002: Adding scrollwheel support
[ 9.715] (**) evdev: Logitech Unifying Device. Wireless PID:4002: YAxisMapping: buttons 4 and 5
[ 9.715] (**) evdev: Logitech Unifying Device. Wireless PID:4002: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 9.715] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.2/0003:046D:C52B.0003/input/input2/event2"
[ 9.715] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:4002" (type: KEYBOARD, id 8)
[ 9.715] (**) Option "xkb_rules" "evdev"
[ 9.715] (**) Option "xkb_model" "evdev"
[ 9.715] (**) Option "xkb_layout" "us"
[ 9.715] (II) evdev: Logitech Unifying Device. Wireless PID:4002: initialized for relative axes.
[ 9.715] (WW) evdev: Logitech Unifying Device. Wireless PID:4002: ignoring absolute axes.
[ 9.715] (**) Logitech Unifying Device. Wireless PID:4002: (accel) keeping acceleration scheme 1
[ 9.715] (**) Logitech Unifying Device. Wireless PID:4002: (accel) acceleration profile 0
[ 9.715] (**) Logitech Unifying Device. Wireless PID:4002: (accel) acceleration factor: 2.000
[ 9.715] (**) Logitech Unifying Device. Wireless PID:4002: (accel) acceleration threshold: 4
[ 9.716] (II) config/udev: Adding input device FV TouchCam N1 (/dev/input/event9)
[ 9.716] (**) FV TouchCam N1: Applying InputClass "evdev keyboard catchall"
[ 9.716] (**) FV TouchCam N1: Applying InputClass "anaconda-keyboard"
[ 9.716] (II) Using input driver 'evdev' for 'FV TouchCam N1'
[ 9.716] (**) FV TouchCam N1: always reports core events
[ 9.716] (**) evdev: FV TouchCam N1: Device: "/dev/input/event9"
[ 9.716] (--) evdev: FV TouchCam N1: Vendor 0x408 Product 0x1030
[ 9.716] (--) evdev: FV TouchCam N1: Found keys
[ 9.716] (II) evdev: FV TouchCam N1: Configuring as keyboard
[ 9.716] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-5/1-5.2/1-5.2.2/1-5.2.2:1.0/input/input9/event9"
[ 9.716] (II) XINPUT: Adding extended input device "FV TouchCam N1" (type: KEYBOARD, id 9)
[ 9.716] (**) Option "xkb_rules" "evdev"
[ 9.716] (**) Option "xkb_model" "evdev"
[ 9.716] (**) Option "xkb_layout" "us"
[ 9.716] (II) config/udev: Adding input device faceVsion FV Audio (/dev/input/event8)
[ 9.716] (II) No input driver specified, ignoring this device.
[ 9.716] (II) This device may have been added with another device file.
[ 9.716] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:1028 (/dev/input/event3)
[ 9.716] (**) Logitech Unifying Device. Wireless PID:1028: Applying InputClass "evdev pointer catchall"
[ 9.717] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:1028'
[ 9.717] (**) Logitech Unifying Device. Wireless PID:1028: always reports core events
[ 9.717] (**) evdev: Logitech Unifying Device. Wireless PID:1028: Device: "/dev/input/event3"
[ 9.717] (--) evdev: Logitech Unifying Device. Wireless PID:1028: Vendor 0x46d Product 0xc52b
[ 9.717] (--) evdev: Logitech Unifying Device. Wireless PID:1028: Found 20 mouse buttons
[ 9.717] (--) evdev: Logitech Unifying Device. Wireless PID:1028: Found scroll wheel(s)
[ 9.717] (--) evdev: Logitech Unifying Device. Wireless PID:1028: Found relative axes
[ 9.717] (--) evdev: Logitech Unifying Device. Wireless PID:1028: Found x and y relative axes
[ 9.717] (II) evdev: Logitech Unifying Device. Wireless PID:1028: Configuring as mouse
[ 9.717] (II) evdev: Logitech Unifying Device. Wireless PID:1028: Adding scrollwheel support
[ 9.717] (**) evdev: Logitech Unifying Device. Wireless PID:1028: YAxisMapping: buttons 4 and 5
[ 9.717] (**) evdev: Logitech Unifying Device. Wireless PID:1028: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 9.717] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.2/0003:046D:C52B.0009/input/input3/event3"
[ 9.717] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:1028" (type: MOUSE, id 10)
[ 9.717] (II) evdev: Logitech Unifying Device. Wireless PID:1028: initialized for relative axes.
[ 9.717] (**) Logitech Unifying Device. Wireless PID:1028: (accel) keeping acceleration scheme 1
[ 9.717] (**) Logitech Unifying Device. Wireless PID:1028: (accel) acceleration profile 0
[ 9.717] (**) Logitech Unifying Device. Wireless PID:1028: (accel) acceleration factor: 2.000
[ 9.717] (**) Logitech Unifying Device. Wireless PID:1028: (accel) acceleration threshold: 4
[ 9.717] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:1028 (/dev/input/mouse0)
[ 9.717] (II) No input driver specified, ignoring this device.
[ 9.717] (II) This device may have been added with another device file.
[ 33.752] (II) NVIDIA(GPU-0): Not probing EDID on DFP-0.
[ 33.752] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[ 33.752] (**) NVIDIA(0): device DFP-0 (Using EDID frequencies has been enabled on
[ 33.752] (**) NVIDIA(0): all display devices.)
[ 33.775] (II) NVIDIA(GPU-0): Not probing EDID on DFP-2.
[ 33.775] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[ 33.775] (**) NVIDIA(0): device DFP-2 (Using EDID frequencies has been enabled on
[ 33.775] (**) NVIDIA(0): all display devices.)
[ 223.022] (II) config/udev: removing device FV TouchCam N1
[ 223.028] (II) evdev: FV TouchCam N1: Close
[ 223.028] (II) UnloadModule: "evdev"
[ 231.715] (II) config/udev: Adding input device faceVsion FV Audio (/dev/input/event9)
[ 231.715] (II) No input driver specified, ignoring this device.
[ 231.715] (II) This device may have been added with another device file.
[ 231.716] (II) config/udev: Adding input device FV TouchCam N1 (/dev/input/event8)
[ 231.716] (**) FV TouchCam N1: Applying InputClass "evdev keyboard catchall"
[ 231.716] (**) FV TouchCam N1: Applying InputClass "anaconda-keyboard"
[ 231.716] (II) Using input driver 'evdev' for 'FV TouchCam N1'
[ 231.716] (**) FV TouchCam N1: always reports core events
[ 231.716] (**) evdev: FV TouchCam N1: Device: "/dev/input/event8"
[ 231.716] (--) evdev: FV TouchCam N1: Vendor 0x408 Product 0x1030
[ 231.716] (--) evdev: FV TouchCam N1: Found keys
[ 231.716] (II) evdev: FV TouchCam N1: Configuring as keyboard
[ 231.716] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-5/1-5.2/1-5.2.2/1-5.2.2:1.0/input/input10/event8"
[ 231.716] (II) XINPUT: Adding extended input device "FV TouchCam N1" (type: KEYBOARD, id 9)
[ 231.716] (**) Option "xkb_rules" "evdev"
[ 231.716] (**) Option "xkb_model" "evdev"
[ 231.716] (**) Option "xkb_layout" "us"

---

