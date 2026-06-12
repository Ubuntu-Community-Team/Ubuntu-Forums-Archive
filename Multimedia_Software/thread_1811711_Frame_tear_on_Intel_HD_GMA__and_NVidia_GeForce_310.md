---
title: "Frame tear on Intel HD GMA  and NVidia GeForce 310M (No Compiz)"
date: 2011-07-25
forum: Multimedia Software
---

### Post by Washus on 2011-07-25
Hi

I bought an asus U33JC and except for one major issue (frame tear) it works fine  out of the box using 11.04 64bit, with some minor issues easily solved  (suspend, upside down cam on skype, flash and java). The U33JC has optimus, but also a bios option to disable the Intel GMA. So I could use the on chip Intel GMA or disable it and use the discrete GF310M.

The major issue I have now is poor video playback.  Frame tear occurs in  every single configuration I tried: Either using the internal Intel  GMA, or disabling the Intel via bios option and using the NVidia  proprietary drivers or even using bumblebee. This  frame tear occurs also on the desktop, but the real problem is that  it's very noticeable on video, specially when connecting my HD TV via HDMI. I tested 720p h264 mkv videos and even low res xvid avis in totem and mplayer/Smplayer all equally poor. Using mplayer I tried several vo options,  such as xv (intel? xv) and x11, and playback is poor on all of them. Oh,  and I don't use compiz (don't care for it). Refresh rate is 60Hz, and should be the right one. It works fine with vlc on the soon to be transformed into free space windows7, but that's not an option for me. I used Ubuntu before on a laptop, but I usually use Gentoo, so I'm not familiar with the ubuntu distro.

The purpose of this laptop was to be my "tv media center" when at home and my work laptop for travelling (13 inch :) ! ). But it failed miserably on the first count. I'm still using my old celeron based Gentoo laptop with RGB out to my tv for that, still with much better results (it can decode only up to 720p, which is fine). But it is dying! I really don't understand why playback is so poor. Could messing with xconf be the answer? 

**Please help!**
Washus


EDIT: Here's my xorg log. NO VSYNC? Is this right? Please help.
```
[    20.743] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    20.743] X Protocol Version 11, Revision 0
[    20.743] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    20.743] Current Operating System: Linux galileo 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64
[    20.743] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-10-generic root=UUID=d88d6f85-26ec-4ab1-97a9-25d1eeae086a ro splash quiet splash vt.handoff=7
[    20.743] Build Date: 21 May 2011  11:48:41AM
[    20.743] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[    20.743] Current version of pixman: 0.20.2
[    20.743]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    20.743] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    20.743] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jul 26 21:07:03 2011
[    20.743] (==) Using config file: "/etc/X11/xorg.conf"
[    20.743] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    20.743] (==) No Layout section.  Using the first Screen section.
[    20.743] (==) No screen section available. Using defaults.
[    20.743] (**) |-->Screen "Default Screen Section" (0)
[    20.743] (**) |   |-->Monitor "<default monitor>"
[    20.744] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
[    20.744] (**) |   |-->Device "Default Device"
[    20.744] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    20.744] (==) Automatically adding devices
[    20.744] (==) Automatically enabling devices
[    20.744] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    20.744]     Entry deleted from font path.
[    20.744] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    20.744]     Entry deleted from font path.
[    20.744] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    20.744]     Entry deleted from font path.
[    20.744] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    20.744]     Entry deleted from font path.
[    20.744] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    20.744]     Entry deleted from font path.
[    20.744] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    20.744] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    20.744] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    20.744] (II) Loader magic: 0x7e0280
[    20.744] (II) Module ABI versions:
[    20.744]     X.Org ANSI C Emulation: 0.4
[    20.744]     X.Org Video Driver: 10.0
[    20.744]     X.Org XInput driver : 12.3
[    20.744]     X.Org Server Extension : 5.0
[    20.745] (--) PCI:*(0:0:2:0) 8086:0046:1043:1362 rev 24, Mem @ 0xd3400000/4194304, 0xb0000000/268435456, I/O @ 0x0000e080/8
[    20.745] (--) PCI: (0:1:0:0) 10de:0a70:1043:1362 rev 162, Mem @ 0xd2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000d000/128, BIOS @ 0x????????/524288
[    20.745] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    20.745] (II) LoadModule: "extmod"
[    20.745] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    20.745] (II) Module extmod: vendor="X.Org Foundation"
[    20.745]     compiled for 1.10.1, module version = 1.0.0
[    20.745]     Module class: X.Org Server Extension
[    20.745]     ABI class: X.Org Server Extension, version 5.0
[    20.745] (II) Loading extension MIT-SCREEN-SAVER
[    20.745] (II) Loading extension XFree86-VidModeExtension
[    20.745] (II) Loading extension XFree86-DGA
[    20.745] (II) Loading extension DPMS
[    20.745] (II) Loading extension XVideo
[    20.745] (II) Loading extension XVideo-MotionCompensation
[    20.745] (II) Loading extension X-Resource
[    20.745] (II) LoadModule: "dbe"
[    20.745] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    20.745] (II) Module dbe: vendor="X.Org Foundation"
[    20.745]     compiled for 1.10.1, module version = 1.0.0
[    20.745]     Module class: X.Org Server Extension
[    20.745]     ABI class: X.Org Server Extension, version 5.0
[    20.745] (II) Loading extension DOUBLE-BUFFER
[    20.745] (II) LoadModule: "glx"
[    20.745] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    21.750] (II) Module glx: vendor="NVIDIA Corporation"
[    21.750]     compiled for 4.0.2, module version = 1.0.0
[    21.751]     Module class: X.Org Server Extension
[    21.751] (II) NVIDIA GLX Module  275.19  Tue Jul 12 18:31:51 PDT 2011
[    21.751] (II) Loading extension GLX
[    21.751] (II) LoadModule: "record"
[    21.751] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    21.751] (II) Module record: vendor="X.Org Foundation"
[    21.751]     compiled for 1.10.1, module version = 1.13.0
[    21.751]     Module class: X.Org Server Extension
[    21.751]     ABI class: X.Org Server Extension, version 5.0
[    21.751] (II) Loading extension RECORD
[    21.751] (II) LoadModule: "dri"
[    21.751] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    21.751] (II) Module dri: vendor="X.Org Foundation"
[    21.751]     compiled for 1.10.1, module version = 1.0.0
[    21.751]     ABI class: X.Org Server Extension, version 5.0
[    21.751] (II) Loading extension XFree86-DRI
[    21.751] (II) LoadModule: "dri2"
[    21.751] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    21.751] (II) Module dri2: vendor="X.Org Foundation"
[    21.751]     compiled for 1.10.1, module version = 1.2.0
[    21.751]     ABI class: X.Org Server Extension, version 5.0
[    21.751] (II) Loading extension DRI2
[    21.751] (==) Matched intel as autoconfigured driver 0
[    21.751] (==) Matched vesa as autoconfigured driver 1
[    21.751] (==) Matched fbdev as autoconfigured driver 2
[    21.751] (==) Assigned the driver to the xf86ConfigLayout
[    21.751] (II) LoadModule: "intel"
[    21.768] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    21.788] (II) Module intel: vendor="X.Org Foundation"
[    21.788]     compiled for 1.10.1, module version = 2.14.0
[    21.788]     Module class: X.Org Video Driver
[    21.788]     ABI class: X.Org Video Driver, version 10.0
[    21.788] (II) LoadModule: "vesa"
[    21.788] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    21.800] (II) Module vesa: vendor="X.Org Foundation"
[    21.800]     compiled for 1.10.0, module version = 2.3.0
[    21.800]     Module class: X.Org Video Driver
[    21.800]     ABI class: X.Org Video Driver, version 10.0
[    21.800] (II) LoadModule: "fbdev"
[    21.800] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    21.805] (II) Module fbdev: vendor="X.Org Foundation"
[    21.805]     compiled for 1.10.0, module version = 0.4.2
[    21.805]     ABI class: X.Org Video Driver, version 10.0
[    21.805] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
    Sandybridge, Sandybridge
[    21.805] (II) VESA: driver for VESA chipsets: vesa
[    21.805] (II) FBDEV: driver for framebuffer: fbdev
[    21.805] (++) using VT number 7

[    21.807] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    21.807] (WW) Falling back to old probe method for vesa
[    21.807] (WW) Falling back to old probe method for fbdev
[    21.807] (II) Loading sub module "fbdevhw"
[    21.807] (II) LoadModule: "fbdevhw"
[    21.809] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    21.822] (II) Module fbdevhw: vendor="X.Org Foundation"
[    21.822]     compiled for 1.10.1, module version = 0.0.2
[    21.822]     ABI class: X.Org Video Driver, version 10.0
[    21.823] drmOpenDevice: node name is /dev/dri/card0
[    21.823] drmOpenDevice: open result is 8, (OK)
[    21.823] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    21.823] drmOpenDevice: node name is /dev/dri/card0
[    21.823] drmOpenDevice: open result is 8, (OK)
[    21.823] drmOpenByBusid: drmOpenMinor returns 8
[    21.823] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    21.823] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    21.823] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    21.823] (==) intel(0): RGB weight 888
[    21.823] (==) intel(0): Default visual is TrueColor
[    21.823] (II) intel(0): Integrated Graphics Chipset: Intel(R) Arrandale
[    21.823] (--) intel(0): Chipset: "Arrandale"
[    21.823] (**) intel(0): Relaxed fencing enabled
[    21.823] (**) intel(0): Tiling enabled
[    21.823] (**) intel(0): SwapBuffers wait enabled
[    21.823] (==) intel(0): video overlay key set to 0x101fe
[    21.823] (II) intel(0): Output LVDS1 has no monitor section
[    21.823] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video1
[    21.823] (II) intel(0): Output VGA1 has no monitor section
[    21.828] (II) intel(0): Output HDMI1 has no monitor section
[    21.829] (II) intel(0): Output DP1 has no monitor section
[    21.829] (II) intel(0): EDID for output LVDS1
[    21.829] (II) intel(0): Manufacturer: AUO  Model: 102c  Serial#: 0
[    21.829] (II) intel(0): Year: 2008  Week: 1
[    21.829] (II) intel(0): EDID Version: 1.3
[    21.829] (II) intel(0): Digital Display Input
[    21.829] (II) intel(0): Max Image Size [cm]: horiz.: 29  vert.: 16
[    21.829] (II) intel(0): Gamma: 2.20
[    21.829] (II) intel(0): No DPMS capabilities specified
[    21.829] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    21.829] (II) intel(0): First detailed timing is preferred mode
[    21.829] (II) intel(0): redX: 0.607 redY: 0.351   greenX: 0.330 greenY: 0.619
[    21.829] (II) intel(0): blueX: 0.149 blueY: 0.104   whiteX: 0.302 whiteY: 0.321
[    21.829] (II) intel(0): Manufacturer's mask: 0
[    21.829] (II) intel(0): Supported detailed timing:
[    21.829] (II) intel(0): clock: 72.0 MHz   Image Size:  293 x 164 mm
[    21.829] (II) intel(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1494 h_border: 0
[    21.829] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 803 v_border: 0
[    21.829] (II) intel(0): Unknown vendor-specific block f
[    21.829] (II) intel(0):  AUO
[    21.829] (II) intel(0):  B133XW01 V0
[    21.829] (II) intel(0): EDID (in hex):
[    21.829] (II) intel(0):     00ffffffffffff0006af2c1000000000
[    21.829] (II) intel(0):     01120103801d10780aba659b59549e26
[    21.829] (II) intel(0):     1a4d5200000001010101010101010101
[    21.829] (II) intel(0):     010101010101201c5680500023303020
[    21.829] (II) intel(0):     360025a4100000180000000f00000000
[    21.829] (II) intel(0):     00000000000000000020000000fe0041
[    21.829] (II) intel(0):     554f0a202020202020202020000000fe
[    21.829] (II) intel(0):     004231333358573031205630200a00bc
[    21.829] (II) intel(0): EDID vendor "AUO", prod id 4140
[    21.829] (II) intel(0): Printing DDC gathered Modelines:
[    21.829] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    21.829] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    21.829] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    21.829] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    21.829] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    21.829] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    21.829] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    21.829] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    21.829] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    21.829] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    21.829] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    21.829] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    21.829] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    21.829] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    21.829] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    21.829] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    21.829] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    21.829] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    21.829] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    21.829] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    21.829] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    21.829] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    21.829] (II) intel(0): Printing probed modes for output LVDS1
[    21.829] (II) intel(0): Modeline "1366x768"x60.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    21.829] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    21.829] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[    21.829] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    21.829] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    21.829] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    21.829] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    21.829] (II) intel(0): EDID for output VGA1
[    21.834] (II) intel(0): EDID for output HDMI1
[    21.835] (II) intel(0): EDID for output DP1
[    21.835] (II) intel(0): Output LVDS1 connected
[    21.835] (II) intel(0): Output VGA1 disconnected
[    21.835] (II) intel(0): Output HDMI1 disconnected
[    21.835] (II) intel(0): Output DP1 disconnected
[    21.835] (II) intel(0): Using exact sizes for initial modes
[    21.835] (II) intel(0): Output LVDS1 using initial mode 1366x768
[    21.835] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    21.835] (II) intel(0): Kernel page flipping support detected, enabling
[    21.835] (**) intel(0): Display dimensions: (290, 160) mm
[    21.835] (**) intel(0): DPI set to (119, 121)
[    21.835] (II) Loading sub module "fb"
[    21.835] (II) LoadModule: "fb"
[    21.835] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.835] (II) Module fb: vendor="X.Org Foundation"
[    21.835]     compiled for 1.10.1, module version = 1.0.0
[    21.835]     ABI class: X.Org ANSI C Emulation, version 0.4
[    21.835] (II) UnloadModule: "vesa"
[    21.835] (II) Unloading vesa
[    21.835] (II) UnloadModule: "fbdev"
[    21.835] (II) Unloading fbdev
[    21.835] (II) UnloadModule: "fbdevhw"
[    21.835] (II) Unloading fbdevhw
[    21.835] (==) Depth 24 pixmap format is 32 bpp
[    21.835] (==) intel(0): VideoRam: 262144 KB
[    21.835] (II) intel(0): [DRI2] Setup complete
[    21.835] (II) intel(0): [DRI2]   DRI driver: i965
[    21.835] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[    21.841] (II) UXA(0): Driver registered support for the following operations:
[    21.841] (II)         solid
[    21.841] (II)         copy
[    21.841] (II)         composite (RENDER acceleration)
[    21.841] (II)         put_image
[    21.841] (II)         get_image
[    21.841] (==) intel(0): Backing store disabled
[    21.841] (==) intel(0): Silken mouse enabled
[    21.841] (II) intel(0): Initializing HW Cursor
[    21.910] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    21.910] (==) intel(0): DPMS enabled
[    21.910] (==) intel(0): Intel XvMC decoder enabled
[    21.910] (II) intel(0): Set up textured video
[    21.910] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    21.910] (II) intel(0): direct rendering: DRI2 Enabled
[    21.910] (WW) intel(0): Option "NoLogo" is not used
[    21.910] (==) intel(0): hotplug detection: "enabled"
[    21.911] (--) RandR disabled
[    21.911] (II) Initializing built-in extension Generic Event Extension
[    21.911] (II) Initializing built-in extension SHAPE
[    21.911] (II) Initializing built-in extension MIT-SHM
[    21.911] (II) Initializing built-in extension XInputExtension
[    21.911] (II) Initializing built-in extension XTEST
[    21.911] (II) Initializing built-in extension BIG-REQUESTS
[    21.911] (II) Initializing built-in extension SYNC
[    21.911] (II) Initializing built-in extension XKEYBOARD
[    21.911] (II) Initializing built-in extension XC-MISC
[    21.911] (II) Initializing built-in extension SECURITY
[    21.911] (II) Initializing built-in extension XINERAMA
[    21.911] (II) Initializing built-in extension XFIXES
[    21.911] (II) Initializing built-in extension RENDER
[    21.911] (II) Initializing built-in extension RANDR
[    21.911] (II) Initializing built-in extension COMPOSITE
[    21.911] (II) Initializing built-in extension DAMAGE
[    21.911] (II) Initializing built-in extension GESTURE
[    21.912] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    21.916] (II) intel(0): Setting screen physical size to 361 x 203
[    21.923] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    21.930] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    21.930] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.930] (II) LoadModule: "evdev"
[    21.931] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.931] (II) Module evdev: vendor="X.Org Foundation"
[    21.931]     compiled for 1.10.0.902, module version = 2.6.0
[    21.931]     Module class: X.Org XInput Driver
[    21.931]     ABI class: X.Org XInput driver, version 12.3
[    21.931] (II) Using input driver 'evdev' for 'Power Button'
[    21.931] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.931] (**) Power Button: always reports core events
[    21.931] (**) Power Button: Device: "/dev/input/event2"
[    21.970] (--) Power Button: Found keys
[    21.970] (II) Power Button: Configuring as keyboard
[    21.970] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    21.970] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    21.970] (**) Option "xkb_rules" "evdev"
[    21.970] (**) Option "xkb_model" "pc105"
[    21.970] (**) Option "xkb_layout" "es"
[    21.970] (**) Option "xkb_variant" "deadtilde"
[    21.972] (II) XKB: reuse xkmfile /var/lib/xkb/server-0726AB2F3A88C901B4B42789561A24D88B7EC131.xkm
[    21.973] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    21.973] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    21.973] (II) Using input driver 'evdev' for 'Video Bus'
[    21.973] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.973] (**) Video Bus: always reports core events
[    21.973] (**) Video Bus: Device: "/dev/input/event6"
[    22.010] (--) Video Bus: Found keys
[    22.010] (II) Video Bus: Configuring as keyboard
[    22.010] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:02/input/input6/event6"
[    22.010] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    22.010] (**) Option "xkb_rules" "evdev"
[    22.010] (**) Option "xkb_model" "pc105"
[    22.010] (**) Option "xkb_layout" "es"
[    22.010] (**) Option "xkb_variant" "deadtilde"
[    22.013] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    22.013] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    22.013] (II) Using input driver 'evdev' for 'Video Bus'
[    22.013] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.013] (**) Video Bus: always reports core events
[    22.013] (**) Video Bus: Device: "/dev/input/event5"
[    22.060] (--) Video Bus: Found keys
[    22.060] (II) Video Bus: Configuring as keyboard
[    22.060] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input5/event5"
[    22.060] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    22.060] (**) Option "xkb_rules" "evdev"
[    22.060] (**) Option "xkb_model" "pc105"
[    22.060] (**) Option "xkb_layout" "es"
[    22.060] (**) Option "xkb_variant" "deadtilde"
[    22.063] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    22.063] (II) No input driver/identifier specified (ignoring)
[    22.063] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    22.063] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    22.063] (II) Using input driver 'evdev' for 'Sleep Button'
[    22.063] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.063] (**) Sleep Button: always reports core events
[    22.063] (**) Sleep Button: Device: "/dev/input/event1"
[    22.120] (--) Sleep Button: Found keys
[    22.120] (II) Sleep Button: Configuring as keyboard
[    22.120] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[    22.120] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    22.120] (**) Option "xkb_rules" "evdev"
[    22.120] (**) Option "xkb_model" "pc105"
[    22.120] (**) Option "xkb_layout" "es"
[    22.120] (**) Option "xkb_variant" "deadtilde"
[    22.122] (II) config/udev: Adding input device USB2.0 UVC 2M WebCam (/dev/input/event4)
[    22.122] (**) USB2.0 UVC 2M WebCam: Applying InputClass "evdev keyboard catchall"
[    22.122] (II) Using input driver 'evdev' for 'USB2.0 UVC 2M WebCam'
[    22.122] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.122] (**) USB2.0 UVC 2M WebCam: always reports core events
[    22.122] (**) USB2.0 UVC 2M WebCam: Device: "/dev/input/event4"
[    22.170] (--) USB2.0 UVC 2M WebCam: Found keys
[    22.170] (II) USB2.0 UVC 2M WebCam: Configuring as keyboard
[    22.170] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input4/event4"
[    22.170] (II) XINPUT: Adding extended input device "USB2.0 UVC 2M WebCam" (type: KEYBOARD)
[    22.170] (**) Option "xkb_rules" "evdev"
[    22.170] (**) Option "xkb_model" "pc105"
[    22.170] (**) Option "xkb_layout" "es"
[    22.170] (**) Option "xkb_variant" "deadtilde"
[    22.171] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event10)
[    22.171] (II) No input driver/identifier specified (ignoring)
[    22.171] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event9)
[    22.171] (II) No input driver/identifier specified (ignoring)
[    22.175] (II) config/udev: Adding input device Asus Laptop extra buttons (/dev/input/event8)
[    22.175] (**) Asus Laptop extra buttons: Applying InputClass "evdev keyboard catchall"
[    22.175] (II) Using input driver 'evdev' for 'Asus Laptop extra buttons'
[    22.175] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.175] (**) Asus Laptop extra buttons: always reports core events
[    22.175] (**) Asus Laptop extra buttons: Device: "/dev/input/event8"
[    22.210] (--) Asus Laptop extra buttons: Found keys
[    22.210] (II) Asus Laptop extra buttons: Configuring as keyboard
[    22.210] (**) Option "config_info" "udev:/sys/devices/platform/asus_laptop/input/input8/event8"
[    22.210] (II) XINPUT: Adding extended input device "Asus Laptop extra buttons" (type: KEYBOARD)
[    22.210] (**) Option "xkb_rules" "evdev"
[    22.210] (**) Option "xkb_model" "pc105"
[    22.210] (**) Option "xkb_layout" "es"
[    22.210] (**) Option "xkb_variant" "deadtilde"
[    22.210] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    22.210] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    22.210] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    22.210] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.210] (**) AT Translated Set 2 keyboard: always reports core events
[    22.210] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    22.250] (--) AT Translated Set 2 keyboard: Found keys
[    22.250] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    22.250] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    22.250] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    22.250] (**) Option "xkb_rules" "evdev"
[    22.250] (**) Option "xkb_model" "pc105"
[    22.250] (**) Option "xkb_layout" "es"
[    22.250] (**) Option "xkb_variant" "deadtilde"
[    22.250] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[    22.250] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    22.250] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    22.250] (II) LoadModule: "synaptics"
[    22.251] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    22.251] (II) Module synaptics: vendor="X.Org Foundation"
[    22.251]     compiled for 1.10.1, module version = 1.3.99
[    22.251]     Module class: X.Org XInput Driver
[    22.251]     ABI class: X.Org XInput driver, version 12.3
[    22.251] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    22.251] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    22.251] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    22.251] (**) Option "Device" "/dev/input/event7"
[    22.350] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5818
[    22.350] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 5084
[    22.350] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    22.350] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    22.350] (--) SynPS/2 Synaptics TouchPad: buttons: left right
[    22.350] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    22.350] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    22.350] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input7/event7"
[    22.350] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    22.350] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    22.350] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    22.350] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.035
[    22.350] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    22.350] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    22.350] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    22.350] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    22.351] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[    22.351] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    22.351] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    22.351] (II) No input driver/identifier specified (ignoring)
[    22.937] (II) intel(0): EDID vendor "AUO", prod id 4140
[    22.937] (II) intel(0): Printing DDC gathered Modelines:
[    22.937] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    22.944] (II) intel(0): EDID vendor "AUO", prod id 4140
[    22.944] (II) intel(0): Printing DDC gathered Modelines:
[    22.944] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    22.992] (II) intel(0): EDID vendor "AUO", prod id 4140
[    22.992] (II) intel(0): Printing DDC gathered Modelines:
[    22.992] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    22.999] (II) intel(0): EDID vendor "AUO", prod id 4140
[    22.999] (II) intel(0): Printing DDC gathered Modelines:
[    22.999] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    25.672] (II) intel(0): EDID vendor "AUO", prod id 4140
[    25.672] (II) intel(0): Printing DDC gathered Modelines:
[    25.672] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    36.177] (II) intel(0): EDID vendor "AUO", prod id 4140
[    36.177] (II) intel(0): Printing DDC gathered Modelines:
[    36.177] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    36.184] (II) intel(0): EDID vendor "AUO", prod id 4140
[    36.184] (II) intel(0): Printing DDC gathered Modelines:
[    36.184] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    36.190] (II) intel(0): EDID vendor "AUO", prod id 4140
[    36.190] (II) intel(0): Printing DDC gathered Modelines:
[    36.190] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    36.825] (II) intel(0): EDID vendor "AUO", prod id 4140
[    36.825] (II) intel(0): Printing DDC gathered Modelines:
[    36.825] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    41.507] (II) intel(0): EDID vendor "AUO", prod id 4140
[    41.507] (II) intel(0): Printing DDC gathered Modelines:
[    41.507] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[  2905.295] (II) intel(0): EDID vendor "AUO", prod id 4140
[  2905.295] (II) intel(0): Printing DDC gathered Modelines:
[  2905.295] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
```
Configuration

- i3 370m processor
- HM55 Express Chipset 
- NVIDIA GF 310M - 1GB DDR3 VRAM + Intel GMA HD (Support NVIDIA Optimus Technology)
- 4GB 1066 MHz SDRAM

---

### Post by Washus on 2011-07-29
bump

---

### Post by drawkcab on 2011-07-29
I have the same problem.  10.4-11.4 have all had tearing issues that I cannot seem to fix.  It might mean leaving Ubuntu behind on my htpc.

---

### Post by BicyclerBoy on 2011-07-29
intel:
your xorg.cong shows intel i915 driver loading.
vsync is on by default.
Is your user a member of the video group ?

Install driconf to setup dri vsync..
xdriinfo
glxinfo

The xorg-edgers ppa is probably necessary to get any graphics performance.

nvidia:
The gt310m is pretty low power much like ION. Shame you did not get 330M.
You need to use VDPAU for video decode. (mplayer, XBMC & MythTV)
VDPAU vsync is always on internally.
OpenGL & Xv vsync can be controlled in the nvidia settings GUI.

xorg-edgers likely has a usable nvidia driver as well.

---

