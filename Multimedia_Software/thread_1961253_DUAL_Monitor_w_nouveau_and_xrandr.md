---
title: "DUAL Monitor w/ nouveau and xrandr"
date: 2012-04-18
forum: Multimedia Software
---

### Post by jardineworks on 2012-04-18
Hey everyone,

I'm desperate for help. I think I've tried everything but I am sure there is a guru out there with a trick up his sleeve that isn't up mine. Here is what I have.

DELL PRECISION T5500 Workstation
nVidia Quadro NVS 295 video card (dual display ports)

+ If I use the nVidia drivers, then using nvidia-settings I see both displays. 
+ When I set them both to active, one renders, one does not.
+ though the second screen does not render, the cursor can travel to it
+ I removed the nVidia drivers and enabled the nouveau drivers.
+ xrandr shows both displays connected (DP-1 and DP-2). 
+ Same thing -- second monitor blank, but cursor can travel to it.
+ Checked the gnome display settings -- both monitors listed and active
+ Tried no xorg.conf file -- no change. 
+ Tried barebones with contents

Section "Device"
Identifier "n"
Driver "nouveau"
EndSection

    .. no change.

Can anyone help me? This is the last issue I have to resolve!

---

### Post by BicyclerBoy on 2012-04-19
What ubuntu version are you using?
What desktop are you using? unity3d or gnome-fallback ?

nouveau in 11.10 & later should give you the 'windows like' dual screen experience out of the box.

The nVidia driver requires you to set twinview mode to get the 'windows like' experi..
As you seem to know..the gnome desktop display prefs tool does not work with nVidia.

Explain "does not render"..
do you mean: no menus, no background
Do mouse events do anything ?

---

### Post by jardineworks on 2012-04-20
> **BicyclerBoy said:**
> What ubuntu version are you using?
What desktop are you using? unity3d or gnome-fallback ?

nouveau in 11.10 & later should give you the 'windows like' dual screen experience out of the box.

The nVidia driver requires you to set twinview mode to get the 'windows like' experi..
As you seem to know..the gnome desktop display prefs tool does not work with nVidia.

Explain "does not render"..
do you mean: no menus, no background
Do mouse events do anything ?

Hi BicyclerBoy,

In answer to your questions --

1. I'm using 11.10 

2. Desktop is Unity3d

3. The monitor is on and I know there is a signal because it does not go into sleep mode. The screen itself though is black -- as if the monitor were shut off. No background, no menu bar, no cursor, nadda. I know the screen is mapped because when I move the mouse past the right edge of the right screen (the one that IS rendering) to the left screen it goes there. In fact, some of the windows I open will actually open on the other screen and I have to alt-f7 them to drag them onto the screen that is visible.

I know the monitor does function because I am able to hook it up to anther machine, using the same port, and it works without issue. I know that there is a signal because xrandr should the two display ports as connected.

---

### Post by BicyclerBoy on 2012-04-20
It seems odd that both nouveau & nVidia drivers have problems with 2nd screen..
My experience of live CD 11.10 & dual screens on nVidia 7300 & unity3d..the default driver is nouveau & the desktop is mirrored screens.

Can you rename delete /etc/X11/xorg.conf.
logout/login
install nvidia driver
reboot
post the /var/log/Xorg.0.log

The release notes for 295.33 states:
> 
Fixed a bug that caused DisplayPort devices to not be listed in Xorg.*.log. For example, if only DisplayPort devices are attached, the log file would contain

    (--) NVIDIA(0): Connected display device(s) on NVIDIA GPU at PCI:2:0:0
    (--) NVIDIA(0): none 

whether that causes any other real problem or just logging, is not obvious.

295.40 is the current bug fix..

---

### Post by jardineworks on 2012-04-20
So I did as suggested. I downloaded the latest drivers from NVidia -- 290.44 I think it is. I stopped the Xserver and installed them without issue. When I rebooted neither screen would come up. I am using DP to DVI connectors. When I switched the monitor that was working to a straight DP to DP the screen comes up. I can't use it without the adapter because the screen flicks on and off every 5 - 10 seconds. Really annoying. Here is the output from the log 

---
[    20.037] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    20.037] X Protocol Version 11, Revision 0
[    20.037] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    20.037] Current Operating System: Linux hal9000 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 20:45:39 UTC 2012 x86_64
[    20.037] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-17-generic root=UUID=dd7a7559-268e-42df-b545-8fb72d2522cb ro quiet splash vt.handoff=7
[    20.037] Build Date: 19 October 2011  05:21:26AM
[    20.037] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    20.037] Current version of pixman: 0.22.2
[    20.037]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    20.037] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    20.037] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Apr 20 19:58:40 2012
[    20.076] (==) Using config file: "/etc/X11/xorg.conf"
[    20.076] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    20.360] (==) ServerLayout "Layout0"
[    20.360] (**) |-->Screen "Screen0" (0)
[    20.360] (**) |   |-->Monitor "Monitor0"
[    20.360] (**) |   |-->Device "Device0"
[    20.360] (**) |-->Input Device "Keyboard0"
[    20.360] (**) |-->Input Device "Mouse0"
[    20.360] (==) Automatically adding devices
[    20.360] (==) Automatically enabling devices
[    20.446] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    20.446]     Entry deleted from font path.
[    20.446] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    20.446]     Entry deleted from font path.
[    20.446] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    20.446]     Entry deleted from font path.
[    20.446] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    20.446]     Entry deleted from font path.
[    20.446] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    20.446]     Entry deleted from font path.
[    20.474] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    20.474] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    20.474] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    20.474] (WW) Disabling Keyboard0
[    20.474] (WW) Disabling Mouse0
[    20.474] (II) Loader magic: 0x7e0220
[    20.474] (II) Module ABI versions:
[    20.474]     X.Org ANSI C Emulation: 0.4
[    20.474]     X.Org Video Driver: 10.0
[    20.474]     X.Org XInput driver : 12.3
[    20.474]     X.Org Server Extension : 5.0
[    20.475] (--) PCI:*(0:3:0:0) 10de:06fd:10de:062e rev 161, Mem @ 0xf6000000/16777216, 0xec000000/67108864, 0xf4000000/33554432, I/O @ 0x0000dc80/128, BIOS @ 0x????????/131072
[    20.475] (II) Open ACPI successful (/var/run/acpid.socket)
[    20.475] (II) LoadModule: "extmod"
[    20.494] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    20.501] (II) Module extmod: vendor="X.Org Foundation"
[    20.501]     compiled for 1.10.4, module version = 1.0.0
[    20.501]     Module class: X.Org Server Extension
[    20.501]     ABI class: X.Org Server Extension, version 5.0
[    20.501] (II) Loading extension MIT-SCREEN-SAVER
[    20.501] (II) Loading extension XFree86-VidModeExtension
[    20.501] (II) Loading extension XFree86-DGA
[    20.501] (II) Loading extension DPMS
[    20.501] (II) Loading extension XVideo
[    20.501] (II) Loading extension XVideo-MotionCompensation
[    20.501] (II) Loading extension X-Resource
[    20.501] (II) LoadModule: "dbe"
[    20.501] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    20.513] (II) Module dbe: vendor="X.Org Foundation"
[    20.513]     compiled for 1.10.4, module version = 1.0.0
[    20.513]     Module class: X.Org Server Extension
[    20.513]     ABI class: X.Org Server Extension, version 5.0
[    20.513] (II) Loading extension DOUBLE-BUFFER
[    20.513] (II) LoadModule: "glx"
[    20.513] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    21.114] (II) Module glx: vendor="NVIDIA Corporation"
[    21.332]     compiled for 4.0.2, module version = 1.0.0
[    21.332]     Module class: X.Org Server Extension
[    21.332] (II) NVIDIA GLX Module  295.40  Thu Apr  5 21:57:38 PDT 2012
[    21.332] (II) Loading extension GLX
[    21.332] (II) LoadModule: "record"
[    21.332] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    21.387] (II) Module record: vendor="X.Org Foundation"
[    21.387]     compiled for 1.10.4, module version = 1.13.0
[    21.387]     Module class: X.Org Server Extension
[    21.387]     ABI class: X.Org Server Extension, version 5.0
[    21.387] (II) Loading extension RECORD
[    21.387] (II) LoadModule: "dri"
[    21.388] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    21.394] (II) Module dri: vendor="X.Org Foundation"
[    21.394]     compiled for 1.10.4, module version = 1.0.0
[    21.394]     ABI class: X.Org Server Extension, version 5.0
[    21.394] (II) Loading extension XFree86-DRI
[    21.394] (II) LoadModule: "dri2"
[    21.394] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    21.395] (II) Module dri2: vendor="X.Org Foundation"
[    21.395]     compiled for 1.10.4, module version = 1.2.0
[    21.395]     ABI class: X.Org Server Extension, version 5.0
[    21.395] (II) Loading extension DRI2
[    21.395] (II) LoadModule: "nvidia"
[    21.395] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    21.455] (II) Module nvidia: vendor="NVIDIA Corporation"
[    21.455]     compiled for 4.0.2, module version = 1.0.0
[    21.455]     Module class: X.Org Video Driver
[    21.470] (II) NVIDIA dlloader X Driver  295.40  Thu Apr  5 21:38:35 PDT 2012
[    21.470] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    21.470] (++) using VT number 7

[    21.471] (II) Loading sub module "fb"
[    21.471] (II) LoadModule: "fb"
[    21.471] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.477] (II) Module fb: vendor="X.Org Foundation"
[    21.477]     compiled for 1.10.4, module version = 1.0.0
[    21.477]     ABI class: X.Org ANSI C Emulation, version 0.4
[    21.477] (II) Loading sub module "wfb"
[    21.477] (II) LoadModule: "wfb"
[    21.477] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    21.479] (II) Module wfb: vendor="X.Org Foundation"
[    21.480]     compiled for 1.10.4, module version = 1.0.0
[    21.480]     ABI class: X.Org ANSI C Emulation, version 0.4
[    21.480] (II) Loading sub module "ramdac"
[    21.480] (II) LoadModule: "ramdac"
[    21.480] (II) Module "ramdac" already built-in
[    21.485] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    21.485] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    21.485] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.550] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    21.550] (==) NVIDIA(0): RGB weight 888
[    21.550] (==) NVIDIA(0): Default visual is TrueColor
[    21.550] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    21.551] (**) NVIDIA(0): Enabling 2D acceleration
[    23.690] (II) NVIDIA(GPU-0): Display (DELL 2408WFP (DFP-1)) does not support NVIDIA 3D
[    23.690] (II) NVIDIA(GPU-0):     Vision stereo.
[    23.690] (WW) NVIDIA(GPU-0): Unable to read EDID for display device DFP-2
[    23.706] (II) NVIDIA(GPU-0): Display (DELL 2408WFP (DFP-2)) does not support NVIDIA 3D
[    23.706] (II) NVIDIA(GPU-0):     Vision stereo.
[    23.708] (II) NVIDIA(0): NVIDIA GPU Quadro NVS 295 (G98GL) at PCI:3:0:0 (GPU-0)
[    23.708] (--) NVIDIA(0): Memory: 262144 kBytes
[    23.708] (--) NVIDIA(0): VideoBIOS: 62.98.75.00.07
[    23.708] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    23.708] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    23.754] (--) NVIDIA(0): Connected display device(s) on Quadro NVS 295 at PCI:3:0:0
[    23.754] (--) NVIDIA(0):     DELL 2408WFP (DFP-1)
[    23.754] (--) NVIDIA(0):     DELL 2408WFP (DFP-2)
[    23.754] (--) NVIDIA(0): DELL 2408WFP (DFP-1): 165.0 MHz maximum pixel clock
[    23.754] (--) NVIDIA(0): DELL 2408WFP (DFP-1): Internal Single Link TMDS
[    23.754] (--) NVIDIA(0): DELL 2408WFP (DFP-2): 480.0 MHz maximum pixel clock
[    23.754] (--) NVIDIA(0): DELL 2408WFP (DFP-2): Internal DisplayPort
[    23.834] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    23.834] (**) NVIDIA(0):     device DELL 2408WFP (DFP-2) (Using EDID frequencies has
[    23.834] (**) NVIDIA(0):     been enabled on all display devices.)
[    23.918] (II) NVIDIA(0): Assigned Display Device: DFP-2
[    23.918] (==) NVIDIA(0): 
[    23.918] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    23.918] (==) NVIDIA(0):     will be used as the requested mode.
[    23.918] (==) NVIDIA(0): 
[    23.918] (II) NVIDIA(0): Validated modes:
[    23.918] (II) NVIDIA(0):     "nvidia-auto-select"
[    23.918] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1200
[    23.930] (--) NVIDIA(0): DPI set to (93, 95); computed from "UseEdidDpi" X config
[    23.930] (--) NVIDIA(0):     option
[    23.930] (--) Depth 24 pixmap format is 32 bpp
[    23.930] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    23.981] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    24.031] (II) Loading extension NV-GLX
[    24.086] (==) NVIDIA(0): Disabling shared memory pixmaps
[    24.086] (==) NVIDIA(0): Backing store disabled
[    24.086] (==) NVIDIA(0): Silken mouse enabled
[    24.086] (**) NVIDIA(0): DPMS enabled
[    24.086] (II) Loading extension NV-CONTROL
[    24.087] (II) Loading extension XINERAMA
[    24.087] (II) Loading sub module "dri2"
[    24.087] (II) LoadModule: "dri2"
[    24.087] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    24.087] (II) Module dri2: vendor="X.Org Foundation"
[    24.087]     compiled for 1.10.4, module version = 1.2.0
[    24.087]     ABI class: X.Org Server Extension, version 5.0
[    24.087] (II) NVIDIA(0): [DRI2] Setup complete
[    24.087] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    24.087] (==) RandR enabled
[    24.087] (II) Initializing built-in extension Generic Event Extension
[    24.087] (II) Initializing built-in extension SHAPE
[    24.087] (II) Initializing built-in extension MIT-SHM
[    24.087] (II) Initializing built-in extension XInputExtension
[    24.087] (II) Initializing built-in extension XTEST
[    24.087] (II) Initializing built-in extension BIG-REQUESTS
[    24.087] (II) Initializing built-in extension SYNC
[    24.087] (II) Initializing built-in extension XKEYBOARD
[    24.087] (II) Initializing built-in extension XC-MISC
[    24.087] (II) Initializing built-in extension SECURITY
[    24.087] (II) Initializing built-in extension XINERAMA
[    24.087] (II) Initializing built-in extension XFIXES
[    24.087] (II) Initializing built-in extension RENDER
[    24.087] (II) Initializing built-in extension RANDR
[    24.087] (II) Initializing built-in extension COMPOSITE
[    24.087] (II) Initializing built-in extension DAMAGE
[    24.087] (II) Initializing built-in extension GESTURE
[    24.088] (II) Initializing extension GLX
[    24.262] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    24.273] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    24.273] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    24.273] (II) LoadModule: "evdev"
[    24.274] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.291] (II) Module evdev: vendor="X.Org Foundation"
[    24.291]     compiled for 1.10.2, module version = 2.6.0
[    24.291]     Module class: X.Org XInput Driver
[    24.291]     ABI class: X.Org XInput driver, version 12.3
[    24.291] (II) Using input driver 'evdev' for 'Power Button'
[    24.291] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.291] (**) Power Button: always reports core events
[    24.291] (**) Power Button: Device: "/dev/input/event1"
[    24.291] (--) Power Button: Found keys
[    24.291] (II) Power Button: Configuring as keyboard
[    24.291] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    24.291] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    24.291] (**) Option "xkb_rules" "evdev"
[    24.291] (**) Option "xkb_model" "pc105"
[    24.291] (**) Option "xkb_layout" "us"
[    24.292] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    24.292] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    24.292] (II) Using input driver 'evdev' for 'Power Button'
[    24.292] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.292] (**) Power Button: always reports core events
[    24.292] (**) Power Button: Device: "/dev/input/event0"
[    24.292] (--) Power Button: Found keys
[    24.292] (II) Power Button: Configuring as keyboard
[    24.292] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    24.292] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    24.292] (**) Option "xkb_rules" "evdev"
[    24.292] (**) Option "xkb_model" "pc105"
[    24.292] (**) Option "xkb_layout" "us"
[    24.294] (II) config/udev: Adding input device LITEON Technology USB Multimedia Keyboard (/dev/input/event3)
[    24.294] (**) LITEON Technology USB Multimedia Keyboard: Applying InputClass "evdev keyboard catchall"
[    24.294] (II) Using input driver 'evdev' for 'LITEON Technology USB Multimedia Keyboard'
[    24.294] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.294] (**) LITEON Technology USB Multimedia Keyboard: always reports core events
[    24.294] (**) LITEON Technology USB Multimedia Keyboard: Device: "/dev/input/event3"
[    24.294] (--) LITEON Technology USB Multimedia Keyboard: Found keys
[    24.294] (II) LITEON Technology USB Multimedia Keyboard: Configuring as keyboard
[    24.294] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input3/event3"
[    24.294] (II) XINPUT: Adding extended input device "LITEON Technology USB Multimedia Keyboard" (type: KEYBOARD)
[    24.294] (**) Option "xkb_rules" "evdev"
[    24.294] (**) Option "xkb_model" "pc105"
[    24.294] (**) Option "xkb_layout" "us"
[    24.294] (II) config/udev: Adding input device LITEON Technology USB Multimedia Keyboard (/dev/input/event4)
[    24.294] (**) LITEON Technology USB Multimedia Keyboard: Applying InputClass "evdev keyboard catchall"
[    24.294] (II) Using input driver 'evdev' for 'LITEON Technology USB Multimedia Keyboard'
[    24.294] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.294] (**) LITEON Technology USB Multimedia Keyboard: always reports core events
[    24.294] (**) LITEON Technology USB Multimedia Keyboard: Device: "/dev/input/event4"
[    24.294] (--) LITEON Technology USB Multimedia Keyboard: Found keys
[    24.294] (II) LITEON Technology USB Multimedia Keyboard: Configuring as keyboard
[    24.294] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.1/input/input4/event4"
[    24.294] (II) XINPUT: Adding extended input device "LITEON Technology USB Multimedia Keyboard" (type: KEYBOARD)
[    24.294] (**) Option "xkb_rules" "evdev"
[    24.295] (**) Option "xkb_model" "pc105"
[    24.295] (**) Option "xkb_layout" "us"
[    24.296] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event5)
[    24.296] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    24.296] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    24.296] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.296] (**) Logitech USB Receiver: always reports core events
[    24.296] (**) Logitech USB Receiver: Device: "/dev/input/event5"
[    24.296] (--) Logitech USB Receiver: Found keys
[    24.296] (II) Logitech USB Receiver: Configuring as keyboard
[    24.296] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2.1/1-2.1:1.0/input/input5/event5"
[    24.296] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    24.296] (**) Option "xkb_rules" "evdev"
[    24.296] (**) Option "xkb_model" "pc105"
[    24.296] (**) Option "xkb_layout" "us"
[    24.296] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event6)
[    24.296] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    24.296] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    24.296] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    24.296] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.296] (**) Logitech USB Receiver: always reports core events
[    24.296] (**) Logitech USB Receiver: Device: "/dev/input/event6"
[    24.296] (--) Logitech USB Receiver: Found 20 mouse buttons
[    24.296] (--) Logitech USB Receiver: Found scroll wheel(s)
[    24.296] (--) Logitech USB Receiver: Found relative axes
[    24.296] (--) Logitech USB Receiver: Found x and y relative axes
[    24.296] (--) Logitech USB Receiver: Found absolute axes
[    24.296] (II) evdev-grail: failed to open grail, no gesture support
[    24.296] (--) Logitech USB Receiver: Found keys
[    24.296] (II) Logitech USB Receiver: Configuring as mouse
[    24.296] (II) Logitech USB Receiver: Configuring as keyboard
[    24.296] (II) Logitech USB Receiver: Adding scrollwheel support
[    24.296] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    24.296] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    24.296] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2.1/1-2.1:1.1/input/input6/event6"
[    24.296] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    24.296] (**) Option "xkb_rules" "evdev"
[    24.296] (**) Option "xkb_model" "pc105"
[    24.296] (**) Option "xkb_layout" "us"
[    24.297] (II) Logitech USB Receiver: initialized for relative axes.
[    24.297] (WW) Logitech USB Receiver: ignoring absolute axes.
[    24.297] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    24.297] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    24.297] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    24.297] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    24.297] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    24.297] (II) No input driver/identifier specified (ignoring)
[    24.298] (II) config/udev: Adding input device Logitech Logitech BT Mini-Receiver (/dev/input/event7)
[    24.298] (**) Logitech Logitech BT Mini-Receiver: Applying InputClass "evdev keyboard catchall"
[    24.298] (II) Using input driver 'evdev' for 'Logitech Logitech BT Mini-Receiver'
[    24.298] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.298] (**) Logitech Logitech BT Mini-Receiver: always reports core events
[    24.298] (**) Logitech Logitech BT Mini-Receiver: Device: "/dev/input/event7"
[    24.298] (--) Logitech Logitech BT Mini-Receiver: Found keys
[    24.298] (II) Logitech Logitech BT Mini-Receiver: Configuring as keyboard
[    24.298] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2.2/1-2.2.2/1-2.2.2:1.0/input/input7/event7"
[    24.298] (II) XINPUT: Adding extended input device "Logitech Logitech BT Mini-Receiver" (type: KEYBOARD)
[    24.298] (**) Option "xkb_rules" "evdev"
[    24.298] (**) Option "xkb_model" "pc105"
[    24.298] (**) Option "xkb_layout" "us"
[    24.298] (II) config/udev: Adding input device Logitech Logitech BT Mini-Receiver (/dev/input/event8)
[    24.298] (**) Logitech Logitech BT Mini-Receiver: Applying InputClass "evdev pointer catchall"
[    24.298] (**) Logitech Logitech BT Mini-Receiver: Applying InputClass "evdev keyboard catchall"
[    24.298] (II) Using input driver 'evdev' for 'Logitech Logitech BT Mini-Receiver'
[    24.298] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.298] (**) Logitech Logitech BT Mini-Receiver: always reports core events
[    24.298] (**) Logitech Logitech BT Mini-Receiver: Device: "/dev/input/event8"
[    24.298] (--) Logitech Logitech BT Mini-Receiver: Found 16 mouse buttons
[    24.298] (--) Logitech Logitech BT Mini-Receiver: Found scroll wheel(s)
[    24.298] (--) Logitech Logitech BT Mini-Receiver: Found relative axes
[    24.298] (--) Logitech Logitech BT Mini-Receiver: Found x and y relative axes
[    24.298] (--) Logitech Logitech BT Mini-Receiver: Found absolute axes
[    24.298] (II) evdev-grail: failed to open grail, no gesture support
[    24.298] (--) Logitech Logitech BT Mini-Receiver: Found keys
[    24.299] (II) Logitech Logitech BT Mini-Receiver: Configuring as mouse
[    24.299] (II) Logitech Logitech BT Mini-Receiver: Configuring as keyboard
[    24.299] (II) Logitech Logitech BT Mini-Receiver: Adding scrollwheel support
[    24.299] (**) Logitech Logitech BT Mini-Receiver: YAxisMapping: buttons 4 and 5
[    24.299] (**) Logitech Logitech BT Mini-Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    24.299] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2.2/1-2.2.3/1-2.2.3:1.0/input/input8/event8"
[    24.299] (II) XINPUT: Adding extended input device "Logitech Logitech BT Mini-Receiver" (type: KEYBOARD)
[    24.299] (**) Option "xkb_rules" "evdev"
[    24.299] (**) Option "xkb_model" "pc105"
[    24.299] (**) Option "xkb_layout" "us"
[    24.299] (II) Logitech Logitech BT Mini-Receiver: initialized for relative axes.
[    24.299] (WW) Logitech Logitech BT Mini-Receiver: ignoring absolute axes.
[    24.299] (**) Logitech Logitech BT Mini-Receiver: (accel) keeping acceleration scheme 1
[    24.299] (**) Logitech Logitech BT Mini-Receiver: (accel) acceleration profile 0
[    24.299] (**) Logitech Logitech BT Mini-Receiver: (accel) acceleration factor: 2.000
[    24.299] (**) Logitech Logitech BT Mini-Receiver: (accel) acceleration threshold: 4
[    24.299] (II) config/udev: Adding input device Logitech Logitech BT Mini-Receiver (/dev/input/mouse1)
[    24.299] (II) No input driver/identifier specified (ignoring)
[    24.306] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event2)
[    24.306] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    24.306] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    24.306] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.306] (**) Dell WMI hotkeys: always reports core events
[    24.306] (**) Dell WMI hotkeys: Device: "/dev/input/event2"
[    24.306] (--) Dell WMI hotkeys: Found keys
[    24.306] (II) Dell WMI hotkeys: Configuring as keyboard
[    24.307] (**) Option "config_info" "udev:/sys/devices/virtual/input/input2/event2"
[    24.307] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
[    24.307] (**) Option "xkb_rules" "evdev"
[    24.307] (**) Option "xkb_model" "pc105"
[    24.307] (**) Option "xkb_layout" "us"
[    44.562] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm

--
\
The nvidia-settings shows both monitors. I enabled them and hit apply but same result. Going to try a reboot now, but I am not hopeful.

---

### Post by BicyclerBoy on 2012-04-20
Just thinking out loud..
The maximum screen resolution for a single link DP is not the same as a single link DVI (really stupid design flaw).
But 1920x1200@60 reduced timing is still 154MHz < 164MHz..

But a single lane DP is max 4.32Gbps
And 1920x1200@60 requires 4.62Gbps.
**4.62 > 4.32** so problem..

There is a problem with DP -->DVI **passive** adapter at the point where dual link bandwidth is required. DP can **not** output dual link DVI with passive adaptor.

To be able to use a passive DP-->DVI-I adapter the DP output must also be a dual-mode device.

I know the latest iProduct DP LCDs require 2 link DP. The passive DVI adapter does not work.

There is an active DP-->DVI adapter that supports higher res screens..
Or you need to resolve the DP-->DP connection problem.

The DP has a lot of clever features, but this is not one of them..

---

