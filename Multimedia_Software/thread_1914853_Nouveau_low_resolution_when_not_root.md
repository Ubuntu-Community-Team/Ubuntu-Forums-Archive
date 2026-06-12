---
title: "Nouveau low resolution when not root"
date: 2012-01-25
forum: Multimedia Software
---

### Post by wwwookie on 2012-01-25
Hi, I'm having trouble getting the Nouveau driver to display full resolution on my monitor

Monitor - Mitsubishi Diamond Plus 200 CRT
      HorizSync    30.0 - 107.0
      VertRefresh 48.0  - 170.0
      Max. resolution 2048x1538

Card      nVidia geForce 6200 128MB

In the past I've used nVidia drivers for systems that need graphics power, but because the nVidia driver has compatibitly issues with realtime kernels (and compositing uses resources), I've stuck with nv for audio systems. The reason I've used nv all this time is that I've alvays had trouble getting Nouveau to display full resolution on my monitor, but now nv is no longer in the 11.10 repo I have to get to grips with Nouveau. I'm building a lowlatency audio system from a minimal command line version of Ubuntu 11.10, and am using Xfce with Nouveau.

When using nVidia or nv I put Horizsync and Vertrefresh values in the Monitor section of xorg.conf, but this doesn't work for Nouveau. Instead, I've added a Modeline to the Monitor section of xorg.conf for each mode I want.

xorg.conf:
```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    Modeline "2048x1536_60.00"  267.25  2048 2208 2424 2800  1536 1539 1543 1592 -hsync +vsync
    Modeline "1536x1152_60.00"  147.75  1536 1640 1800 2064  1152 1155 1159 1195 -hsync +vsync
EndSection

Section "Device"
    Identifier  "Card0"
    Driver      "nouveau"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
EndSection
``` Now here's the odd bit: if I'm logged in as root at a virtual terminal and I type startx, X comes up fine and the new modes are available. If I do the same when logged in as a user, X comes up in low resolution. The manually defined modes are present in the Xfce resolution selector, but try 2048x1536 and the window says that it has changed to that resolution but the screen clicks twice and stays the same (the resolution selector works when running X as root). What seems to be happening is that X resizes to the high resolution, something fails when running as a user so it falls back to 1024x768.

I thought maybe it was a group permission thing, tried adding myself to the "video" group - to no avail. ( I don't know if this was a good idea so removed myself afterwards)

Does anyone know what could be happening?

Here's a copy of /var/log/Xorg.0.log when running as root:
```
[[  1074.082] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[  1074.082] X Protocol Version 11, Revision 0
[  1074.082] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[  1074.082] Current Operating System: Linux wookie-desktop 3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 15:59:53 UTC 2012 i686
[  1074.083] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-15-generic root=UUID=e5e3992d-7c53-4961-8eca-1ccbf5c77153 ro
[  1074.083] Build Date: 19 October 2011  05:09:41AM
[  1074.083] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[  1074.083] Current version of pixman: 0.22.2
[  1074.083]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[  1074.084] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  1074.085] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jan 25 09:22:11 2012
[  1074.085] (==) Using config file: "/etc/X11/xorg.conf"
[  1074.085] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  1074.086] (==) ServerLayout "X.org Configured"
[  1074.086] (**) |-->Screen "Screen0" (0)
[  1074.086] (**) |   |-->Monitor "Monitor0"
[  1074.087] (**) |   |-->Device "Card0"
[  1074.087] (==) Automatically adding devices
[  1074.087] (==) Automatically enabling devices
[  1074.087] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  1074.087]     Entry deleted from font path.
[  1074.087] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  1074.087]     Entry deleted from font path.
[  1074.087] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  1074.087]     Entry deleted from font path.
[  1074.087] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  1074.087]     Entry deleted from font path.
[  1074.087] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  1074.087]     Entry deleted from font path.
[  1074.087] (WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
[  1074.087]     Entry deleted from font path.
[  1074.087]     (Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
[  1074.087] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[  1074.087] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  1074.087] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[  1074.087] (II) Loader magic: 0x823ada0
[  1074.087] (II) Module ABI versions:
[  1074.087]     X.Org ANSI C Emulation: 0.4
[  1074.087]     X.Org Video Driver: 10.0
[  1074.087]     X.Org XInput driver : 12.3
[  1074.087]     X.Org Server Extension : 5.0
[  1074.088] (--) PCI:*(0:1:0:0) 10de:0221:0000:0000 rev 161, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, 0xf5000000/16777216, BIOS @ 0x????????/131072
[  1074.089] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[  1074.089] (II) LoadModule: "extmod"
[  1074.089] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  1074.089] (II) Module extmod: vendor="X.Org Foundation"
[  1074.089]     compiled for 1.10.4, module version = 1.0.0
[  1074.089]     Module class: X.Org Server Extension
[  1074.089]     ABI class: X.Org Server Extension, version 5.0
[  1074.089] (II) Loading extension MIT-SCREEN-SAVER
[  1074.089] (II) Loading extension XFree86-VidModeExtension
[  1074.089] (II) Loading extension XFree86-DGA
[  1074.089] (II) Loading extension DPMS
[  1074.089] (II) Loading extension XVideo
[  1074.090] (II) Loading extension XVideo-MotionCompensation
[  1074.090] (II) Loading extension X-Resource
[  1074.090] (II) LoadModule: "dbe"
[  1074.090] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  1074.090] (II) Module dbe: vendor="X.Org Foundation"
[  1074.090]     compiled for 1.10.4, module version = 1.0.0
[  1074.090]     Module class: X.Org Server Extension
[  1074.090]     ABI class: X.Org Server Extension, version 5.0
[  1074.090] (II) Loading extension DOUBLE-BUFFER
[  1074.090] (II) LoadModule: "glx"
[  1074.090] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  1074.090] (II) Module glx: vendor="X.Org Foundation"
[  1074.090]     compiled for 1.10.4, module version = 1.0.0
[  1074.090]     ABI class: X.Org Server Extension, version 5.0
[  1074.091] (==) AIGLX enabled
[  1074.091] (II) Loading extension GLX
[  1074.091] (II) LoadModule: "record"
[  1074.091] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  1074.091] (II) Module record: vendor="X.Org Foundation"
[  1074.091]     compiled for 1.10.4, module version = 1.13.0
[  1074.091]     Module class: X.Org Server Extension
[  1074.091]     ABI class: X.Org Server Extension, version 5.0
[  1074.091] (II) Loading extension RECORD
[  1074.091] (II) LoadModule: "dri"
[  1074.091] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  1074.092] (II) Module dri: vendor="X.Org Foundation"
[  1074.092]     compiled for 1.10.4, module version = 1.0.0
[  1074.092]     ABI class: X.Org Server Extension, version 5.0
[  1074.092] (II) Loading extension XFree86-DRI
[  1074.092] (II) LoadModule: "dri2"
[  1074.092] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  1074.092] (II) Module dri2: vendor="X.Org Foundation"
[  1074.092]     compiled for 1.10.4, module version = 1.2.0
[  1074.092]     ABI class: X.Org Server Extension, version 5.0
[  1074.092] (II) Loading extension DRI2
[  1074.092] (II) LoadModule: "nouveau"
[  1074.092] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[  1074.093] (II) Module nouveau: vendor="X.Org Foundation"
[  1074.093]     compiled for 1.10.1, module version = 0.0.16
[  1074.093]     Module class: X.Org Video Driver
[  1074.093]     ABI class: X.Org Video Driver, version 10.0
[  1074.093] (II) NOUVEAU driver Date:   Thu Mar 24 02:13:12 2011 +1000
[  1074.093] (II) NOUVEAU driver for NVIDIA chipset families :
[  1074.093]     RIVA TNT        (NV04)
[  1074.093]     RIVA TNT2       (NV05)
[  1074.093]     GeForce 256     (NV10)
[  1074.093]     GeForce 2       (NV11, NV15)
[  1074.093]     GeForce 4MX     (NV17, NV18)
[  1074.093]     GeForce 3       (NV20)
[  1074.093]     GeForce 4Ti     (NV25, NV28)
[  1074.093]     GeForce FX      (NV3x)
[  1074.093]     GeForce 6       (NV4x)
[  1074.093]     GeForce 7       (G7x)
[  1074.093]     GeForce 8       (G8x)
[  1074.094]     GeForce GTX 200 (NVA0)
[  1074.094]     GeForce GTX 400 (NVC0)
[  1074.094] (--) using VT number 8

[  1074.096] drmOpenDevice: node name is /dev/dri/card0
[  1074.096] drmOpenDevice: open result is 7, (OK)
[  1074.096] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[  1074.096] drmOpenDevice: node name is /dev/dri/card0
[  1074.096] drmOpenDevice: open result is 7, (OK)
[  1074.096] drmOpenByBusid: drmOpenMinor returns 7
[  1074.096] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[  1074.096] (II) [drm] nouveau interface version: 0.0.16
[  1074.096] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[  1074.097] (II) Loading sub module "dri"
[  1074.097] (II) LoadModule: "dri"
[  1074.097] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  1074.097] (II) Module dri: vendor="X.Org Foundation"
[  1074.097]     compiled for 1.10.4, module version = 1.0.0
[  1074.097]     ABI class: X.Org Server Extension, version 5.0
[  1074.097] (II) NOUVEAU(0): Loaded DRI module
[  1074.097] drmOpenDevice: node name is /dev/dri/card0
[  1074.097] drmOpenDevice: open result is 8, (OK)
[  1074.097] drmOpenDevice: node name is /dev/dri/card0
[  1074.097] drmOpenDevice: open result is 8, (OK)
[  1074.098] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[  1074.098] drmOpenDevice: node name is /dev/dri/card0
[  1074.098] drmOpenDevice: open result is 8, (OK)
[  1074.098] drmOpenByBusid: drmOpenMinor returns 8
[  1074.098] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[  1074.098] (II) [drm] DRM interface version 1.4
[  1074.098] (II) [drm] DRM open master succeeded.
[  1074.098] (--) NOUVEAU(0): Chipset: "NVIDIA NV4a"
[  1074.098] (II) NOUVEAU(0): Creating default Display subsection in Screen section
    "Screen0" for depth/fbbpp 24/32
[  1074.098] (==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
[  1074.098] (==) NOUVEAU(0): RGB weight 888
[  1074.098] (==) NOUVEAU(0): Default visual is TrueColor
[  1074.098] (==) NOUVEAU(0): Using HW cursor
[  1074.098] (==) NOUVEAU(0): GLX sync to VBlank disabled.
[  1074.098] (==) NOUVEAU(0): Page flipping enabled
[  1074.544] (II) NOUVEAU(0): Output VGA-1 using monitor section Monitor0
[  1074.608] (II) NOUVEAU(0): Output DVI-I-1 has no monitor section
[  1074.664] (II) NOUVEAU(0): Output TV-1 has no monitor section
[  1074.692] (II) NOUVEAU(0): EDID for output VGA-1
[  1074.692] (II) NOUVEAU(0): Printing probed modes for output VGA-1
[  1074.692] (II) NOUVEAU(0): Modeline "2048x1536_60.00"x60.0  267.25  2048 2208 2424 2800  1536 1539 1543 1592 -hsync +vsync (95.4 kHz)
[  1074.692] (II) NOUVEAU(0): Modeline "1536x1152_60.00"x59.9  147.75  1536 1640 1800 2064  1152 1155 1159 1195 -hsync +vsync (71.6 kHz)
[  1074.692] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  1074.692] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  1074.692] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  1074.692] (II) NOUVEAU(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz)
[  1074.692] (II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz)
[  1074.756] (II) NOUVEAU(0): EDID for output DVI-I-1
[  1074.812] (II) NOUVEAU(0): EDID for output TV-1
[  1074.812] (II) NOUVEAU(0): Output VGA-1 connected
[  1074.812] (II) NOUVEAU(0): Output DVI-I-1 disconnected
[  1074.812] (II) NOUVEAU(0): Output TV-1 disconnected
[  1074.812] (II) NOUVEAU(0): Using fuzzy aspect match for initial modes
[  1074.812] (II) NOUVEAU(0): Output VGA-1 using initial mode 2048x1536_60.00
[  1074.812] (II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[  1074.812] (--) NOUVEAU(0): Virtual size is 2048x1536 (pitch 0)
[  1074.812] (**) NOUVEAU(0):  Mode "2048x1536_60.00": 267.2 MHz (scaled from 0.0 MHz), 95.4 kHz, 60.0 Hz
[  1074.812] (II) NOUVEAU(0): Modeline "2048x1536_60.00"x60.0  267.25  2048 2208 2424 2800  1536 1539 1543 1592 -hsync +vsync (95.4 kHz)
[  1074.812] (**) NOUVEAU(0):  Mode "1536x1152_60.00": 147.8 MHz (scaled from 0.0 MHz), 71.6 kHz, 59.9 Hz
[  1074.812] (II) NOUVEAU(0): Modeline "1536x1152_60.00"x59.9  147.75  1536 1640 1800 2064  1152 1155 1159 1195 -hsync +vsync (71.6 kHz)
[  1074.812] (**) NOUVEAU(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
[  1074.812] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  1074.812] (**) NOUVEAU(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
[  1074.812] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  1074.812] (**) NOUVEAU(0):  Driver mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.2 Hz
[  1074.812] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  1074.812] (**) NOUVEAU(0):  Driver mode "848x480": 33.8 MHz (scaled from 0.0 MHz), 31.0 kHz, 60.0 Hz
[  1074.812] (II) NOUVEAU(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz)
[  1074.812] (**) NOUVEAU(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 59.9 Hz
[  1074.812] (II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz)
[  1074.812] (==) NOUVEAU(0): DPI set to (96, 96)
[  1074.812] (II) Loading sub module "fb"
[  1074.812] (II) LoadModule: "fb"
[  1074.812] (II) Loading /usr/lib/xorg/modules/libfb.so
[  1074.813] (II) Module fb: vendor="X.Org Foundation"
[  1074.813]     compiled for 1.10.4, module version = 1.0.0
[  1074.813]     ABI class: X.Org ANSI C Emulation, version 0.4
[  1074.813] (II) Loading sub module "exa"
[  1074.813] (II) LoadModule: "exa"
[  1074.813] (II) Loading /usr/lib/xorg/modules/libexa.so
[  1074.813] (II) Module exa: vendor="X.Org Foundation"
[  1074.813]     compiled for 1.10.4, module version = 2.5.0
[  1074.813]     ABI class: X.Org Video Driver, version 10.0
[  1074.813] (II) Loading sub module "shadowfb"
[  1074.813] (II) LoadModule: "shadowfb"
[  1074.814] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[  1074.814] (II) Module shadowfb: vendor="X.Org Foundation"
[  1074.814]     compiled for 1.10.4, module version = 1.0.0
[  1074.814]     ABI class: X.Org ANSI C Emulation, version 0.4
[  1074.814] (--) Depth 24 pixmap format is 32 bpp
[  1074.816] (II) NOUVEAU(0): Opened GPU channel 1
[  1074.816] (II) NOUVEAU(0): [DRI2] Setup complete
[  1074.816] (II) NOUVEAU(0): [DRI2]   DRI driver: nouveau
[  1074.816] (II) NOUVEAU(0): GART: 64MiB available
[  1074.826] (II) NOUVEAU(0): GART: Allocated 16MiB as a scratch buffer
[  1074.826] (II) EXA(0): Driver allocated offscreen pixmaps
[  1074.826] (II) EXA(0): Driver registered support for the following operations:
[  1074.826] (II)         Solid
[  1074.826] (II)         Copy
[  1074.826] (II)         Composite (RENDER acceleration)
[  1074.826] (II)         UploadToScreen
[  1074.826] (II)         DownloadFromScreen
[  1074.826] (==) NOUVEAU(0): Backing store disabled
[  1074.826] (==) NOUVEAU(0): Silken mouse enabled
[  1074.826] (II) NOUVEAU(0): [XvMC] Associated with NV40 texture adapter.
[  1074.826] (II) NOUVEAU(0): [XvMC] Extension initialized.
[  1074.826] (==) NOUVEAU(0): DPMS enabled
[  1074.827] (II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[  1074.827] (--) RandR disabled
[  1074.827] (II) Initializing built-in extension Generic Event Extension
[  1074.827] (II) Initializing built-in extension SHAPE
[  1074.827] (II) Initializing built-in extension MIT-SHM
[  1074.827] (II) Initializing built-in extension XInputExtension
[  1074.827] (II) Initializing built-in extension XTEST
[  1074.827] (II) Initializing built-in extension BIG-REQUESTS
[  1074.827] (II) Initializing built-in extension SYNC
[  1074.827] (II) Initializing built-in extension XKEYBOARD
[  1074.827] (II) Initializing built-in extension XC-MISC
[  1074.827] (II) Initializing built-in extension SECURITY
[  1074.827] (II) Initializing built-in extension XINERAMA
[  1074.827] (II) Initializing built-in extension XFIXES
[  1074.827] (II) Initializing built-in extension RENDER
[  1074.827] (II) Initializing built-in extension RANDR
[  1074.827] (II) Initializing built-in extension COMPOSITE
[  1074.827] (II) Initializing built-in extension DAMAGE
[  1074.827] (II) Initializing built-in extension GESTURE
[  1074.841] (II) AIGLX: Trying DRI driver /usr/lib/i386-linux-gnu/dri/nouveau_dri.so
[  1074.863] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[  1074.863] (II) AIGLX: enabled GLX_INTEL_swap_event
[  1074.863] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[  1074.863] (II) AIGLX: enabled GLX_SGI_make_current_read
[  1074.863] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[  1074.864] (II) AIGLX: Loaded and initialized nouveau
[  1074.864] (II) GLX: Initialized DRI2 GL provider for screen 0
[  1074.873] (II) NOUVEAU(0): NVEnterVT is called.
[  1074.894] (II) NOUVEAU(0): Setting screen physical size to 541 x 406
[  1074.894] resize called 2048 1536
[  1074.907] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  1074.922] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[  1074.922] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  1074.922] (II) LoadModule: "evdev"
[  1074.923] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1074.924] (II) Module evdev: vendor="X.Org Foundation"
[  1074.924]     compiled for 1.10.2, module version = 2.6.0
[  1074.924]     Module class: X.Org XInput Driver
[  1074.924]     ABI class: X.Org XInput driver, version 12.3
[  1074.924] (II) Using input driver 'evdev' for 'Power Button'
[  1074.924] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1074.924] (**) Power Button: always reports core events
[  1074.924] (**) Power Button: Device: "/dev/input/event1"
[  1074.924] (--) Power Button: Found keys
[  1074.924] (II) Power Button: Configuring as keyboard
[  1074.924] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[  1074.924] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  1074.924] (**) Option "xkb_rules" "evdev"
[  1074.924] (**) Option "xkb_model" "pc105"
[  1074.924] (**) Option "xkb_layout" "gb"
[  1074.928] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[  1074.932] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[  1074.932] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  1074.932] (II) Using input driver 'evdev' for 'Power Button'
[  1074.932] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1074.932] (**) Power Button: always reports core events
[  1074.932] (**) Power Button: Device: "/dev/input/event0"
[  1074.932] (--) Power Button: Found keys
[  1074.932] (II) Power Button: Configuring as keyboard
[  1074.932] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[  1074.932] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  1074.932] (**) Option "xkb_rules" "evdev"
[  1074.932] (**) Option "xkb_model" "pc105"
[  1074.932] (**) Option "xkb_layout" "gb"
[  1074.946] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[  1074.946] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  1074.946] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[  1074.946] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1074.947] (**) AT Translated Set 2 keyboard: always reports core events
[  1074.947] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[  1074.947] (--) AT Translated Set 2 keyboard: Found keys
[  1074.947] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[  1074.947] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[  1074.947] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[  1074.947] (**) Option "xkb_rules" "evdev"
[  1074.947] (**) Option "xkb_model" "pc105"
[  1074.947] (**) Option "xkb_layout" "gb"
[  1074.948] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event3)
[  1074.948] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
[  1074.948] (II) Using input driver 'evdev' for 'ImPS/2 Generic Wheel Mouse'
[  1074.948] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1074.948] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[  1074.948] (**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event3"
[  1074.948] (--) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
[  1074.948] (--) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
[  1074.948] (--) ImPS/2 Generic Wheel Mouse: Found relative axes
[  1074.948] (--) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
[  1074.948] (II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
[  1074.948] (II) ImPS/2 Generic Wheel Mouse: Adding scrollwheel support
[  1074.948] (**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
[  1074.948] (**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1074.948] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input3/event3"
[  1074.948] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
[  1074.948] (II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
[  1074.948] (**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
[  1074.948] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration profile 0
[  1074.949] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration factor: 2.000
[  1074.949] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration threshold: 4
[  1074.949] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse0)
[  1074.949] (II) No input driver/identifier specified (ignoring)
[  1078.920] (II) AIGLX: Suspending AIGLX clients for VT switch
[  1078.920] (II) NOUVEAU(0): NVLeaveVT is called.
[  1085.334] (II) ImPS/2 Generic Wheel Mouse: Close
[  1085.334] (II) UnloadModule: "evdev"
[  1085.334] (II) Unloading evdev
[  1085.336] (II) AT Translated Set 2 keyboard: Close
[  1085.336] (II) UnloadModule: "evdev"
[  1085.336] (II) Unloading evdev
[  1085.336] (II) Power Button: Close
[  1085.336] (II) UnloadModule: "evdev"
[  1085.336] (II) Unloading evdev
[  1085.336] (II) Power Button: Close
[  1085.336] (II) UnloadModule: "evdev"
[  1085.336] (II) Unloading evdev
[  1085.344] (II) NOUVEAU(0): Closed GPU channel 1
[  1085.351]  ddxSigGiveUp: Closing log


```And here's when running as a user:
```
[   550.960] [   550.960] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[   550.961] X Protocol Version 11, Revision 0
[   550.961] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[   550.961] Current Operating System: Linux wookie-desktop 3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 15:59:53 UTC 2012 i686
[   550.962] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-15-generic root=UUID=e5e3992d-7c53-4961-8eca-1ccbf5c77153 ro
[   550.962] Build Date: 19 October 2011  05:09:41AM
[   550.962] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[   550.963] Current version of pixman: 0.22.2
[   550.963]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   550.964] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   550.966] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jan 25 09:13:28 2012
[   550.966] (==) Using config file: "/etc/X11/xorg.conf"
[   550.967] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   550.968] (==) ServerLayout "X.org Configured"
[   550.968] (**) |-->Screen "Screen0" (0)
[   550.968] (**) |   |-->Monitor "Monitor0"
[   550.968] (**) |   |-->Device "Card0"
[   550.968] (==) Automatically adding devices
[   550.968] (==) Automatically enabling devices
[   550.968] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   550.968]     Entry deleted from font path.
[   550.968] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   550.968]     Entry deleted from font path.
[   550.968] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   550.968]     Entry deleted from font path.
[   550.969] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   550.969]     Entry deleted from font path.
[   550.969] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   550.969]     Entry deleted from font path.
[   550.969] (WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
[   550.969]     Entry deleted from font path.
[   550.969]     (Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
[   550.969] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   550.969] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   550.969] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   550.969] (II) Loader magic: 0x823ada0
[   550.969] (II) Module ABI versions:
[   550.969]     X.Org ANSI C Emulation: 0.4
[   550.969]     X.Org Video Driver: 10.0
[   550.969]     X.Org XInput driver : 12.3
[   550.969]     X.Org Server Extension : 5.0
[   550.970] (--) PCI:*(0:1:0:0) 10de:0221:0000:0000 rev 161, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, 0xf5000000/16777216, BIOS @ 0x????????/131072
[   550.970] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[   550.970] (II) LoadModule: "extmod"
[   550.970] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   550.971] (II) Module extmod: vendor="X.Org Foundation"
[   550.971]     compiled for 1.10.4, module version = 1.0.0
[   550.971]     Module class: X.Org Server Extension
[   550.971]     ABI class: X.Org Server Extension, version 5.0
[   550.971] (II) Loading extension MIT-SCREEN-SAVER
[   550.971] (II) Loading extension XFree86-VidModeExtension
[   550.971] (II) Loading extension XFree86-DGA
[   550.971] (II) Loading extension DPMS
[   550.971] (II) Loading extension XVideo
[   550.971] (II) Loading extension XVideo-MotionCompensation
[   550.971] (II) Loading extension X-Resource
[   550.971] (II) LoadModule: "dbe"
[   550.971] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   550.971] (II) Module dbe: vendor="X.Org Foundation"
[   550.971]     compiled for 1.10.4, module version = 1.0.0
X.Org X Server 1.10.4
Release Date: 2011-08-19
[   550.961] X Protocol Version 11, Revision 0
[   550.961] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[   550.961] Current Operating System: Linux wookie-desktop 3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 15:59:53 UTC 2012 i686
[   550.962] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-15-generic root=UUID=e5e3992d-7c53-4961-8eca-1ccbf5c77153 ro
[   550.962] Build Date: 19 October 2011  05:09:41AM
[   550.962] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[   550.963] Current version of pixman: 0.22.2
[   550.963]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   550.964] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   550.966] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jan 25 09:13:28 2012
[   550.966] (==) Using config file: "/etc/X11/xorg.conf"
[   550.967] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   550.968] (==) ServerLayout "X.org Configured"
[   550.968] (**) |-->Screen "Screen0" (0)
[   550.968] (**) |   |-->Monitor "Monitor0"
[   550.968] (**) |   |-->Device "Card0"
[   550.968] (==) Automatically adding devices
[   550.968] (==) Automatically enabling devices
[   550.968] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   550.968]     Entry deleted from font path.
[   550.968] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   550.968]     Entry deleted from font path.
[   550.968] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   550.968]     Entry deleted from font path.
[   550.969] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   550.969]     Entry deleted from font path.
[   550.969] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   550.969]     Entry deleted from font path.
[   550.969] (WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
[   550.969]     Entry deleted from font path.
[   550.969]     (Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
[   550.969] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   550.969] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   550.969] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   550.969] (II) Loader magic: 0x823ada0
[   550.969] (II) Module ABI versions:
[   550.969]     X.Org ANSI C Emulation: 0.4
[   550.969]     X.Org Video Driver: 10.0
[   550.969]     X.Org XInput driver : 12.3
[   550.969]     X.Org Server Extension : 5.0
[   550.970] (--) PCI:*(0:1:0:0) 10de:0221:0000:0000 rev 161, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, 0xf5000000/16777216, BIOS @ 0x????????/131072
[   550.970] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[   550.970] (II) LoadModule: "extmod"
[   550.970] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   550.971] (II) Module extmod: vendor="X.Org Foundation"
[   550.971]     compiled for 1.10.4, module version = 1.0.0
[   550.971]     Module class: X.Org Server Extension
[   550.971]     ABI class: X.Org Server Extension, version 5.0
[   550.971] (II) Loading extension MIT-SCREEN-SAVER
[   550.971] (II) Loading extension XFree86-VidModeExtension
[   550.971] (II) Loading extension XFree86-DGA
[   550.971] (II) Loading extension DPMS
[   550.971] (II) Loading extension XVideo
[   550.971] (II) Loading extension XVideo-MotionCompensation
[   550.971] (II) Loading extension X-Resource
[   550.971] (II) LoadModule: "dbe"
[   550.971] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   550.971] (II) Module dbe: vendor="X.Org Foundation"
[   550.971]     compiled for 1.10.4, module version = 1.0.0
```Can somebody point me in the right direction please?

---

### Post by wwwookie on 2012-01-25
Well, I've got a fix, of sorts: manually enabling the RandR extension by adding this to xorg.conf: 

```
Section "Extensions"
    Option "RandR" "Enable"
Endsection
```makes X come up in the maximum resolution even when started as a normal user.

However, the resolution selector in Xfce still doesn't work for resolutions greater that the defaults set by the driver. The command **xrandr** does work though, so that could be used instead. I still don't know what's going on though, any ideas?

---

