---
title: "video playback only sometimes possible without issues"
date: 2012-11-28
forum: Multimedia Software
---

### Post by kallew on 2012-11-28
I am at my wit's end trying to play video files in lubuntu or other ubuntu based distributions and really need help solving or at least understanding what is going on.

Whenever I try to play a videofile with mplayer (gmplayer, mplayer2, mplayer) or vlc, either from a live-cd, an installed system with all updates, a system with an up-to-date mplayer, either x86 or amd64 architecture, playback of most video files is messed up.

Using mplayer, the video stream either goes out of sync going fullscreen (catching up with higher speed when returning to window mode) or hangs/crashes the player. Sometimes I got a message running 'dmesg' that gmplayer crashed <- don't know how to reproduce those.

With vlc the video stream is fine, but audio is terribly distorted (the same files that go out of sync with mplayer). Other files on the other hand hang or crash vlc.

The files may have almost any container/codec/size (tried mp4, avi, mkv, flv, ogv, wmv) and used to work fine on my previous pc. I am testing with both default settings and using opengl as output. Opengl usually does not crash the player, but leaves audio/video out of sync.

Funny thing is: 1080p encoded Quake videos I tested play pretty much without trouble using mplayer and in vlc, except for some rare artifacts or scenes with rapid changes. This is the behaviour I would expect from this system playing HD stuff and that is totally fine.

There are times playback does work, but I have no idea why or what I can do to reproduce that.
Yesterday, for example, I 
[LIST=1]
[*]test files with mplayer -> issues
[*]installed vlc
[*]test files with vlc -> issues
[*]test again with mplayer -> issues
[*]test again with vlc -> working
[*]test again with mplayer -> working
[*]browsing and reading man pages for about an hour
[*]test again with mplayer or vlc -> issues
[/LIST]

No trouble playing flash videos, even fullscreen. Windows XP Prof. 32bit shows none of those issues using vlc.

Could that be audio related? vlc complained once or twice about not being able to activate audio, resource busy or so. A second try usually does work. I have no other software using video/audio at that time, except chromium and maybe flash on some website. Are there special xorg.conf settings or software packages for an Intel GMA3100?

Running lubuntu 12.04, 12.10 (x86 and amd64), xubuntu 12.04, linux mint 9.04 either from livecd or installed, with kernel 2.6.xx, 3.2.xx, 3.5.xx, 3.6.xx, all with the same result.

EDIT: Checked with Archbang and had the same problems. CPU is usually idle when playing videos. As soon as the window exceeds what seems to be 1600x1200, the video starts to cause the mentioned problems.

System
[LIST]
[*]Fujitsu CELCIUS W360
[*]Core2Duo E6650 2.3GHz
[*]2GB DDR2 dual channel ram
[*]Intel Q35 chipset
[*]onboard GMA 3100 (using i915 kernel module)
[*]DVI 1920x1200 resolution on 24" screen
[/LIST]

Xorg.log
```
[    16.951] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    16.951] X Protocol Version 11, Revision 0
[    16.951] Build Operating System: Linux 2.6.42-26-generic i686 Ubuntu
[    16.951] Current Operating System: Linux springfield 3.2.0-33-generic #52-Ubuntu SMP Thu Oct 18 16:19:45 UTC 2012 i686
[    16.951] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-33-generic root=UUID=752c31b1-cc3c-4315-ae3f-4476b2289119 ro quiet splash 
[    16.951] Build Date: 29 August 2012  12:10:05AM
[    16.951] xorg-server 2:1.11.4-0ubuntu10.8 (For technical support please see http://www.ubuntu.com/support) 
[    16.951] Current version of pixman: 0.24.4
[    16.951]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    16.951] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    16.951] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Nov 28 01:57:41 2012
[    17.140] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    17.140] (==) No Layout section.  Using the first Screen section.
[    17.140] (==) No screen section available. Using defaults.
[    17.140] (**) |-->Screen "Default Screen Section" (0)
[    17.140] (**) |   |-->Monitor "<default monitor>"
[    17.140] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    17.140] (==) Automatically adding devices
[    17.140] (==) Automatically enabling devices
[    17.140] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    17.140]     Entry deleted from font path.
[    17.140] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    17.140]     Entry deleted from font path.
[    17.140] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    17.140]     Entry deleted from font path.
[    17.140] (WW) The directory "/usr/share/fonts/X11/Type1" does not exist.
[    17.140]     Entry deleted from font path.
[    17.140] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    17.140]     Entry deleted from font path.
[    17.140] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    17.140]     Entry deleted from font path.
[    17.140] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    17.140]     Entry deleted from font path.
[    17.140] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    built-ins
[    17.140] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    17.140] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    17.140] (II) Loader magic: 0xfa15a0
[    17.140] (II) Module ABI versions:
[    17.140]     X.Org ANSI C Emulation: 0.4
[    17.140]     X.Org Video Driver: 11.0
[    17.140]     X.Org XInput driver : 16.0
[    17.140]     X.Org Server Extension : 6.0
[    17.141] (--) PCI:*(0:0:2:0) 8086:29b2:1734:10fc rev 2, Mem @ 0xd0080000/524288, 0xe0000000/268435456, 0xd0100000/1048576, I/O @ 0x00001c70/8
[    17.141] (--) PCI: (0:0:2:1) 8086:29b3:1734:10fc rev 2, Mem @ 0x80000000/524288
[    17.141] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    17.141] (II) LoadModule: "extmod"
[    17.177] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    17.177] (II) Module extmod: vendor="X.Org Foundation"
[    17.177]     compiled for 1.11.3, module version = 1.0.0
[    17.177]     Module class: X.Org Server Extension
[    17.177]     ABI class: X.Org Server Extension, version 6.0
[    17.177] (II) Loading extension MIT-SCREEN-SAVER
[    17.177] (II) Loading extension XFree86-VidModeExtension
[    17.177] (II) Loading extension XFree86-DGA
[    17.177] (II) Loading extension DPMS
[    17.177] (II) Loading extension XVideo
[    17.177] (II) Loading extension XVideo-MotionCompensation
[    17.177] (II) Loading extension X-Resource
[    17.177] (II) LoadModule: "dbe"
[    17.177] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    17.178] (II) Module dbe: vendor="X.Org Foundation"
[    17.178]     compiled for 1.11.3, module version = 1.0.0
[    17.178]     Module class: X.Org Server Extension
[    17.178]     ABI class: X.Org Server Extension, version 6.0
[    17.178] (II) Loading extension DOUBLE-BUFFER
[    17.178] (II) LoadModule: "glx"
[    17.178] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    17.178] (II) Module glx: vendor="X.Org Foundation"
[    17.178]     compiled for 1.11.3, module version = 1.0.0
[    17.178]     ABI class: X.Org Server Extension, version 6.0
[    17.178] (==) AIGLX enabled
[    17.178] (II) Loading extension GLX
[    17.178] (II) LoadModule: "record"
[    17.178] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    17.178] (II) Module record: vendor="X.Org Foundation"
[    17.178]     compiled for 1.11.3, module version = 1.13.0
[    17.178]     Module class: X.Org Server Extension
[    17.178]     ABI class: X.Org Server Extension, version 6.0
[    17.178] (II) Loading extension RECORD
[    17.178] (II) LoadModule: "dri"
[    17.179] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    17.179] (II) Module dri: vendor="X.Org Foundation"
[    17.179]     compiled for 1.11.3, module version = 1.0.0
[    17.179]     ABI class: X.Org Server Extension, version 6.0
[    17.179] (II) Loading extension XFree86-DRI
[    17.179] (II) LoadModule: "dri2"
[    17.179] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    17.179] (II) Module dri2: vendor="X.Org Foundation"
[    17.179]     compiled for 1.11.3, module version = 1.2.0
[    17.179]     ABI class: X.Org Server Extension, version 6.0
[    17.179] (II) Loading extension DRI2
[    17.179] (==) Matched intel as autoconfigured driver 0
[    17.179] (==) Matched vesa as autoconfigured driver 1
[    17.179] (==) Matched fbdev as autoconfigured driver 2
[    17.179] (==) Assigned the driver to the xf86ConfigLayout
[    17.179] (II) LoadModule: "intel"
[    17.180] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    17.180] (II) Module intel: vendor="X.Org Foundation"
[    17.180]     compiled for 1.11.3, module version = 2.17.0
[    17.180]     Module class: X.Org Video Driver
[    17.180]     ABI class: X.Org Video Driver, version 11.0
[    17.180] (II) LoadModule: "vesa"
[    17.180] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    17.180] (II) Module vesa: vendor="X.Org Foundation"
[    17.180]     compiled for 1.11.3, module version = 2.3.0
[    17.180]     Module class: X.Org Video Driver
[    17.180]     ABI class: X.Org Video Driver, version 11.0
[    17.180] (II) LoadModule: "fbdev"
[    17.180] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    17.180] (II) Module fbdev: vendor="X.Org Foundation"
[    17.180]     compiled for 1.11.3, module version = 0.4.2
[    17.180]     ABI class: X.Org Video Driver, version 11.0
[    17.180] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    17.181] (II) VESA: driver for VESA chipsets: vesa
[    17.181] (II) FBDEV: driver for framebuffer: fbdev
[    17.181] (++) using VT number 7

[    17.182] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    17.182] (WW) Falling back to old probe method for vesa
[    17.182] (WW) Falling back to old probe method for fbdev
[    17.182] (II) Loading sub module "fbdevhw"
[    17.182] (II) LoadModule: "fbdevhw"
[    17.183] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    17.183] (II) Module fbdevhw: vendor="X.Org Foundation"
[    17.183]     compiled for 1.11.3, module version = 0.0.2
[    17.183]     ABI class: X.Org Video Driver, version 11.0
[    17.183] drmOpenDevice: node name is /dev/dri/card0
[    17.183] drmOpenDevice: open result is 8, (OK)
[    17.183] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    17.183] drmOpenDevice: node name is /dev/dri/card0
[    17.183] drmOpenDevice: open result is 8, (OK)
[    17.183] drmOpenByBusid: drmOpenMinor returns 8
[    17.183] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    17.183] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    17.183] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    17.183] (==) intel(0): RGB weight 888
[    17.183] (==) intel(0): Default visual is TrueColor
[    17.183] (II) intel(0): Integrated Graphics Chipset: Intel(R) Q35
[    17.183] (--) intel(0): Chipset: "Q35"
[    17.183] (**) intel(0): Relaxed fencing enabled
[    17.183] (**) intel(0): Wait on SwapBuffers? enabled
[    17.183] (**) intel(0): Triple buffering? enabled
[    17.183] (**) intel(0): Framebuffer tiled
[    17.183] (**) intel(0): Pixmaps tiled
[    17.183] (**) intel(0): 3D buffers tiled
[    17.183] (**) intel(0): SwapBuffers wait enabled
[    17.183] (==) intel(0): video overlay key set to 0x101fe
[    17.204] (II) intel(0): Output VGA1 has no monitor section
[    17.329] (II) intel(0): Output DVI1 has no monitor section
[    17.344] (II) intel(0): EDID for output VGA1
[    17.469] (II) intel(0): EDID for output DVI1
[    17.469] (II) intel(0): Manufacturer: ENC  Model: 1887  Serial#: 16843009
[    17.469] (II) intel(0): Year: 2007  Week: 37
[    17.469] (II) intel(0): EDID Version: 1.3
[    17.469] (II) intel(0): Digital Display Input
[    17.469] (II) intel(0): Max Image Size [cm]: horiz.: 52  vert.: 33
[    17.469] (II) intel(0): Gamma: 2.20
[    17.469] (II) intel(0): DPMS capabilities: StandBy Suspend Off
[    17.469] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    17.469] (II) intel(0): First detailed timing is preferred mode
[    17.469] (II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.608
[    17.469] (II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    17.469] (II) intel(0): Supported established timings:
[    17.469] (II) intel(0): 720x400@70Hz
[    17.469] (II) intel(0): 640x480@60Hz
[    17.469] (II) intel(0): 800x600@60Hz
[    17.469] (II) intel(0): 1024x768@60Hz
[    17.469] (II) intel(0): Manufacturer's mask: 0
[    17.469] (II) intel(0): Supported standard timings:
[    17.469] (II) intel(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    17.469] (II) intel(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    17.469] (II) intel(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    17.469] (II) intel(0): #3: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    17.469] (II) intel(0): Supported detailed timing:
[    17.469] (II) intel(0): clock: 154.0 MHz   Image Size:  519 x 324 mm
[    17.469] (II) intel(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
[    17.469] (II) intel(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
[    17.469] (II) intel(0): Serial No: 34018097
[    17.469] (II) intel(0): Ranges: V min: 59 V max: 61 Hz, H min: 31 H max: 76 kHz, PixClock max 175 MHz
[    17.470] (II) intel(0): Monitor name: S2431W
[    17.470] (II) intel(0): EDID (in hex):
[    17.470] (II) intel(0):     00ffffffffffff0015c3871801010101
[    17.470] (II) intel(0):     2511010380342178eaef95a3544c9b26
[    17.470] (II) intel(0):     0f5054a10800a94081808140b3000101
[    17.470] (II) intel(0):     010101010101283c80a070b023403020
[    17.470] (II) intel(0):     360007442100001a000000ff00333430
[    17.470] (II) intel(0):     31383039370a20202020000000fd003b
[    17.470] (II) intel(0):     3d1f4c11000a202020202020000000fc
[    17.470] (II) intel(0):     005332343331570a202020202020009f
[    17.470] (II) intel(0): Printing probed modes for output DVI1
[    17.470] (II) intel(0): Modeline "1920x1200"x60.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
[    17.470] (II) intel(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    17.470] (II) intel(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    17.470] (II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    17.470] (II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    17.470] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    17.470] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    17.470] (II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    17.470] (II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    17.470] (II) intel(0): Output VGA1 disconnected
[    17.470] (II) intel(0): Output DVI1 connected
[    17.470] (II) intel(0): Using exact sizes for initial modes
[    17.470] (II) intel(0): Output DVI1 using initial mode 1920x1200
[    17.470] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    17.470] (II) intel(0): Kernel page flipping support detected, enabling
[    17.470] (==) intel(0): DPI set to (96, 96)
[    17.470] (II) Loading sub module "fb"
[    17.470] (II) LoadModule: "fb"
[    17.470] (II) Loading /usr/lib/xorg/modules/libfb.so
[    17.470] (II) Module fb: vendor="X.Org Foundation"
[    17.470]     compiled for 1.11.3, module version = 1.0.0
[    17.470]     ABI class: X.Org ANSI C Emulation, version 0.4
[    17.470] (II) Loading sub module "dri2"
[    17.470] (II) LoadModule: "dri2"
[    17.471] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    17.471] (II) Module dri2: vendor="X.Org Foundation"
[    17.471]     compiled for 1.11.3, module version = 1.2.0
[    17.471]     ABI class: X.Org Server Extension, version 6.0
[    17.471] (II) UnloadModule: "vesa"
[    17.471] (II) Unloading vesa
[    17.471] (II) UnloadModule: "fbdev"
[    17.471] (II) Unloading fbdev
[    17.471] (II) UnloadModule: "fbdevhw"
[    17.471] (II) Unloading fbdevhw
[    17.471] (==) Depth 24 pixmap format is 32 bpp
[    17.471] (II) intel(0): [DRI2] Setup complete
[    17.471] (II) intel(0): [DRI2]   DRI driver: i915
[    17.471] (II) intel(0): Allocated new frame buffer 1920x1200 stride 8192, tiled
[    17.471] (II) UXA(0): Driver registered support for the following operations:
[    17.471] (II)         solid
[    17.471] (II)         copy
[    17.471] (II)         composite (RENDER acceleration)
[    17.471] (II)         put_image
[    17.471] (II)         get_image
[    17.471] (==) intel(0): Backing store disabled
[    17.471] (==) intel(0): Silken mouse enabled
[    17.471] (II) intel(0): Initializing HW Cursor
[    17.496] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    17.496] (==) intel(0): DPMS enabled
[    17.496] (==) intel(0): Intel XvMC decoder disabled
[    17.496] (II) intel(0): Set up textured video
[    17.496] (II) intel(0): Set up overlay video
[    17.496] (II) intel(0): direct rendering: DRI2 Enabled
[    17.496] (==) intel(0): hotplug detection: "enabled"
[    17.496] (--) RandR disabled
[    17.496] (II) Initializing built-in extension Generic Event Extension
[    17.496] (II) Initializing built-in extension SHAPE
[    17.496] (II) Initializing built-in extension MIT-SHM
[    17.496] (II) Initializing built-in extension XInputExtension
[    17.496] (II) Initializing built-in extension XTEST
[    17.496] (II) Initializing built-in extension BIG-REQUESTS
[    17.496] (II) Initializing built-in extension SYNC
[    17.496] (II) Initializing built-in extension XKEYBOARD
[    17.496] (II) Initializing built-in extension XC-MISC
[    17.496] (II) Initializing built-in extension SECURITY
[    17.496] (II) Initializing built-in extension XINERAMA
[    17.496] (II) Initializing built-in extension XFIXES
[    17.496] (II) Initializing built-in extension RENDER
[    17.496] (II) Initializing built-in extension RANDR
[    17.496] (II) Initializing built-in extension COMPOSITE
[    17.496] (II) Initializing built-in extension DAMAGE
[    17.508] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    17.508] (II) AIGLX: enabled GLX_INTEL_swap_event
[    17.508] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    17.508] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    17.508] (II) AIGLX: Loaded and initialized i915
[    17.508] (II) GLX: Initialized DRI2 GL provider for screen 0
[    17.509] (II) intel(0): Setting screen physical size to 507 x 317
[    17.516] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    17.519] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    17.519] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    17.519] (II) LoadModule: "evdev"
[    17.520] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.520] (II) Module evdev: vendor="X.Org Foundation"
[    17.520]     compiled for 1.11.3, module version = 2.7.0
[    17.520]     Module class: X.Org XInput Driver
[    17.520]     ABI class: X.Org XInput driver, version 16.0
[    17.520] (II) Using input driver 'evdev' for 'Power Button'
[    17.520] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.520] (**) Power Button: always reports core events
[    17.520] (**) evdev: Power Button: Device: "/dev/input/event1"
[    17.520] (--) evdev: Power Button: Vendor 0 Product 0x1
[    17.520] (--) evdev: Power Button: Found keys
[    17.520] (II) evdev: Power Button: Configuring as keyboard
[    17.520] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    17.520] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    17.520] (**) Option "xkb_rules" "evdev"
[    17.520] (**) Option "xkb_model" "pc105"
[    17.520] (**) Option "xkb_layout" "de"
[    17.522] (II) XKB: reuse xkmfile /var/lib/xkb/server-808BBA3D4C227BDB44C370226C34E44C5D69A4A9.xkm
[    17.523] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    17.523] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    17.523] (II) Using input driver 'evdev' for 'Power Button'
[    17.523] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.523] (**) Power Button: always reports core events
[    17.523] (**) evdev: Power Button: Device: "/dev/input/event0"
[    17.523] (--) evdev: Power Button: Vendor 0 Product 0x1
[    17.523] (--) evdev: Power Button: Found keys
[    17.523] (II) evdev: Power Button: Configuring as keyboard
[    17.523] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    17.523] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    17.523] (**) Option "xkb_rules" "evdev"
[    17.523] (**) Option "xkb_model" "pc105"
[    17.523] (**) Option "xkb_layout" "de"
[    17.524] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event4)
[    17.524] (II) No input driver specified, ignoring this device.
[    17.524] (II) This device may have been added with another device file.
[    17.524] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event5)
[    17.524] (II) No input driver specified, ignoring this device.
[    17.524] (II) This device may have been added with another device file.
[    17.525] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event6)
[    17.525] (II) No input driver specified, ignoring this device.
[    17.525] (II) This device may have been added with another device file.
[    17.525] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event7)
[    17.525] (II) No input driver specified, ignoring this device.
[    17.525] (II) This device may have been added with another device file.
[    17.525] (II) config/udev: Adding input device HDA Intel Line-Out (/dev/input/event8)
[    17.525] (II) No input driver specified, ignoring this device.
[    17.525] (II) This device may have been added with another device file.
[    17.525] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event3)
[    17.526] (**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
[    17.526] (II) Using input driver 'evdev' for 'Logitech USB-PS/2 Optical Mouse'
[    17.526] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.526] (**) Logitech USB-PS/2 Optical Mouse: always reports core events
[    17.526] (**) evdev: Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event3"
[    17.526] (--) evdev: Logitech USB-PS/2 Optical Mouse: Vendor 0x46d Product 0xc03e
[    17.526] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found 3 mouse buttons
[    17.526] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
[    17.526] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found relative axes
[    17.526] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
[    17.526] (II) evdev: Logitech USB-PS/2 Optical Mouse: Configuring as mouse
[    17.526] (II) evdev: Logitech USB-PS/2 Optical Mouse: Adding scrollwheel support
[    17.526] (**) evdev: Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
[    17.526] (**) evdev: Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    17.526] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2.1/2-2.1:1.0/input/input3/event3"
[    17.526] (II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE, id 8)
[    17.526] (II) evdev: Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
[    17.526] (**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
[    17.526] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration profile 0
[    17.526] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration factor: 2.000
[    17.526] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration threshold: 4
[    17.526] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse0)
[    17.526] (II) No input driver specified, ignoring this device.
[    17.526] (II) This device may have been added with another device file.
[    17.527] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    17.527] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    17.527] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    17.527] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.527] (**) AT Translated Set 2 keyboard: always reports core events
[    17.527] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    17.527] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    17.527] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    17.527] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    17.527] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    17.527] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    17.527] (**) Option "xkb_rules" "evdev"
[    17.527] (**) Option "xkb_model" "pc105"
[    17.527] (**) Option "xkb_layout" "de"
[    18.434] (II) intel(0): EDID vendor "ENC", prod id 6279
[    18.435] (II) intel(0): Using EDID range info for horizontal sync
[    18.435] (II) intel(0): Using EDID range info for vertical refresh
[    18.435] (II) intel(0): Printing DDC gathered Modelines:
[    18.435] (II) intel(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
[    18.435] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.435] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.435] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    18.435] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.435] (II) intel(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    18.435] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    18.435] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    18.435] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    18.585] (II) intel(0): EDID vendor "ENC", prod id 6279
[    18.585] (II) intel(0): Using hsync ranges from config file
[    18.585] (II) intel(0): Using vrefresh ranges from config file
[    18.585] (II) intel(0): Printing DDC gathered Modelines:
[    18.585] (II) intel(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
[    18.585] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.585] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.586] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    18.586] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.586] (II) intel(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    18.586] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    18.586] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    18.586] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
```dmesg
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-33-generic (buildd@lamiak) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #52-Ubuntu SMP Thu Oct 18 16:19:45 UTC 2012 (Ubuntu 3.2.0-33.52-generic 3.2.31)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009c800 (usable)
[    0.000000]  BIOS-e820: 000000000009c800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000cc000 - 00000000000d0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007d5d0000 (usable)
[    0.000000]  BIOS-e820: 000000007d5d0000 - 000000007d5d8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007d5d8000 - 000000007d5db000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007d5db000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: FUJITSU SIEMENS CELSIUS W360                  /D2587-A1, BIOS 6.00 R1.18.2587.A1               02/05/2009
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7d5d0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07D600000 mask FFFE00000 uncachable
[    0.000000]   2 base 07D800000 mask FFF800000 uncachable
[    0.000000]   3 base 07E000000 mask FFE000000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2006MB, range: 2MB, type UC
[    0.000000] reg 2, base: 2008MB, range: 8MB, type UC
[    0.000000] reg 3, base: 2016MB, range: 32MB, type UC
[    0.000000] total RAM covered: 2006M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 64M     num_reg: 4      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2006MB, range: 2MB, type UC
[    0.000000] reg 2, base: 2008MB, range: 8MB, type UC
[    0.000000] reg 3, base: 2016MB, range: 32MB, type UC
[    0.000000] found SMP MP-table at [c00f7420] f7420
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c0098000] 98000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 37272000 - 37ff0000
[    0.000000] Allocated new RAMDISK: 364f4000 - 37271be4
[    0.000000] Move RAMDISK from 0000000037272000 - 0000000037fefbe3 to 364f4000 - 37271be3
[    0.000000] ACPI: RSDP 000f7320 00014 (v00 PTLTD )
[    0.000000] ACPI: RSDT 7d5d2d30 00058 (v01 PTLTD    RSDT   00060000  LTP 00000000)
[    0.000000] ACPI: FACP 7d5d7af3 00074 (v01 FSC             00060000      000F4240)
[    0.000000] ACPI: DSDT 7d5d2d88 04D6B (v01 FSC    D2587/A1 00060000 MSFT 03000001)
[    0.000000] ACPI: FACS 7d5dafc0 00040
[    0.000000] ACPI: TCPA 7d5d7b67 00032 (v01 Phoeni  x       00060000  TL  00000000)
[    0.000000] ACPI: _MAR 7d5d7b99 00030 (v01 Intel  OEMDMAR  00060000 LOHR 00000001)
[    0.000000] ACPI: SSDT 7d5d7bc9 0007A (v01 FSC    CST_CPU0 00060000  CSF 00000001)
[    0.000000] ACPI: SSDT 7d5d7c43 0007A (v01 FSC    CST_CPU1 00060000  CSF 00000001)
[    0.000000] ACPI: SSDT 7d5d7cbd 000B6 (v01 FSC    PST_CPU0 00060000  CSF 00000001)
[    0.000000] ACPI: SSDT 7d5d7d73 000B6 (v01 FSC    PST_CPU1 00060000  CSF 00000001)
[    0.000000] ACPI: SPCR 7d5d7e29 00050 (v01 PTLTD  $UCRTBL$ 00060000 PTL  00000001)
[    0.000000] ACPI: MCFG 7d5d7e79 0003C (v01 PTLTD    MCFG   00060000  LTP 00000000)
[    0.000000] ACPI: HPET 7d5d7eb5 00038 (v01 PTLTD  HPETTBL  00060000  LTP 00000001)
[    0.000000] ACPI: APIC 7d5d7eed 00068 (v01 PTLTD  ? APIC   00060000  LTP 00000000)
[    0.000000] ACPI: BOOT 7d5d7f55 00028 (v01 PTLTD  $SBFTBL$ 00060000  LTP 00000001)
[    0.000000] ACPI: ASF! 7d5d7f7d 00083 (v16   CETP     CETP 00060000 PTL  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1117MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007d5d0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009c
[    0.000000]     0: 0x00000100 -> 0x0007d5d0
[    0.000000] On node 0 totalpages: 513372
[    0.000000] free_area_init_node: node 0, pgdat c1825580, node_mem_map f5544200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3948 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2236 pages used for memmap
[    0.000000]   HighMem zone: 283926 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 000000000009d000
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000cc000
[    0.000000] PM: Registered nosave memory: 00000000000cc000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:78000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f77d7000 s31616 r0 d21632 u53248
[    0.000000] pcpu-alloc: s31616 r0 d21632 u53248 alloc=13*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 509360
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-33-generic root=UUID=752c31b1-cc3c-4315-ae3f-4476b2289119 ro quiet splash 
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 8215552 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007d5d0)
[    0.000000] Memory: 2004608k/2053952k available (5621k kernel code, 48880k reserved, 2769k data, 712k init, 1144648k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc1832000 - 0xc18e4000   ( 712 kB)
[    0.000000]       .data : 0xc157d644 - 0xc1831c80   (2769 kB)
[    0.000000]       .text : 0xc1000000 - 0xc157d644   (5621 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f4808000 soft=f480a000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2327.310 MHz processor.
[    0.004001] Calibrating delay loop (skipped), value calculated using timer frequency.. 4654.62 BogoMIPS (lpj=9309240)
[    0.004006] pid_max: default: 32768 minimum: 301
[    0.008021] Security Framework initialized
[    0.008036] AppArmor: AppArmor initialized
[    0.008038] Yama: becoming mindful.
[    0.008089] Mount-cache hash table entries: 512
[    0.008208] Initializing cgroup subsys cpuacct
[    0.008214] Initializing cgroup subsys memory
[    0.008221] Initializing cgroup subsys devices
[    0.008223] Initializing cgroup subsys freezer
[    0.008225] Initializing cgroup subsys blkio
[    0.008232] Initializing cgroup subsys perf_event
[    0.008257] CPU: Physical Processor ID: 0
[    0.008258] CPU: Processor Core ID: 0
[    0.008263] mce: CPU supports 6 MCE banks
[    0.008270] CPU0: Thermal monitoring enabled (TM2)
[    0.008273] using mwait in idle threads.
[    0.010193] ACPI: Core revision 20110623
[    0.016029] ftrace: allocating 25915 entries in 51 pages
[    0.020042] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.020399] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.062594] CPU0: Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz stepping 0b
[    0.064003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.064003] PEBS disabled due to CPU errata.
[    0.064003] ... version:                2
[    0.064003] ... bit width:              40
[    0.064003] ... generic registers:      2
[    0.064003] ... value mask:             000000ffffffffff
[    0.064003] ... max period:             000000007fffffff
[    0.064003] ... fixed-purpose events:   3
[    0.064003] ... event mask:             0000000700000003
[    0.064003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.064003] CPU 1 irqstacks, hard=f48cc000 soft=f48ce000
[    0.064003] Booting Node   0, Processors  #1 Ok.
[    0.064003] smpboot cpu 1: start_ip = 98000
[    0.008000] Initializing CPU#1
[    0.152035] NMI watchdog enabled, takes one hw-pmu counter.
[    0.152072] Brought up 2 CPUs
[    0.152075] Total of 2 processors activated (9309.61 BogoMIPS).
[    0.154710] devtmpfs: initialized
[    0.154710] EVM: security.selinux
[    0.154710] EVM: security.SMACK64
[    0.154710] EVM: security.capability
[    0.154710] PM: Registering ACPI NVS region at 7d5d8000 (12288 bytes)
[    0.156166] print_constraints: dummy: 
[    0.156194] RTC time:  1:57:25, date: 11/28/12
[    0.156232] NET: Registered protocol family 16
[    0.156261] Trying to unpack rootfs image as initramfs...
[    0.156367] EISA bus registered
[    0.156395] ACPI: bus type pci registered
[    0.156459] PCI: MMCONFIG for domain 0000 [bus 00-03] at [mem 0xf8000000-0xf83fffff] (base 0xf8000000)
[    0.156462] PCI: MMCONFIG at [mem 0xf8000000-0xf83fffff] reserved in E820
[    0.156464] PCI: Using MMCONFIG for extended config space
[    0.156466] PCI: Using configuration type 1 for base access
[    0.157638] bio: create slab <bio-0> at 0
[    0.157716] ACPI: Added _OSI(Module Device)
[    0.157718] ACPI: Added _OSI(Processor Device)
[    0.157721] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.157723] ACPI: Added _OSI(Processor Aggregator Device)
[    0.158693] ACPI: EC: Look up EC in DSDT
[    0.161900] ACPI: Interpreter enabled
[    0.161911] ACPI: (supports S0 S1 S3 S4 S5)
[    0.161933] ACPI: Using IOAPIC for interrupt routing
[    0.165938] ACPI: No dock devices found.
[    0.165940] HEST: Table not found.
[    0.165946] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.166455] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.167443] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.167446] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.167449] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.167452] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.167455] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.167457] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.167460] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.167463] pci_root PNP0A08:00: host bridge window [mem 0x7e000000-0xf7ffffff]
[    0.167465] pci_root PNP0A08:00: host bridge window [mem 0xfc000000-0xfebfffff]
[    0.167468] pci_root PNP0A08:00: host bridge window [mem 0xfed00000-0xfedfffff]
[    0.167471] pci_root PNP0A08:00: host bridge window [mem 0xfef00000-0xffafffff]
[    0.167473] pci_root PNP0A08:00: host bridge window [mem 0xffc00000-0xffefffff]
[    0.167488] pci 0000:00:00.0: [8086:29b0] type 0 class 0x000600
[    0.167531] pci 0000:00:02.0: [8086:29b2] type 0 class 0x000300
[    0.167541] pci 0000:00:02.0: reg 10: [mem 0xd0080000-0xd00fffff]
[    0.167547] pci 0000:00:02.0: reg 14: [io  0x1c70-0x1c77]
[    0.167553] pci 0000:00:02.0: reg 18: [mem 0xe0000000-0xefffffff pref]
[    0.167559] pci 0000:00:02.0: reg 1c: [mem 0xd0100000-0xd01fffff]
[    0.167595] pci 0000:00:02.1: [8086:29b3] type 0 class 0x000380
[    0.167604] pci 0000:00:02.1: reg 10: [mem 0x00000000-0x0007ffff]
[    0.167653] pci 0000:00:03.0: [8086:29b4] type 0 class 0x000780
[    0.167667] pci 0000:00:03.0: reg 10: [mem 0xd0004000-0xd000400f 64bit]
[    0.167711] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.167714] pci 0000:00:03.0: PME# disabled
[    0.167729] pci 0000:00:03.2: [8086:29b6] type 0 class 0x000101
[    0.167740] pci 0000:00:03.2: reg 10: [io  0x1c88-0x1c8f]
[    0.167747] pci 0000:00:03.2: reg 14: [io  0x1c7c-0x1c7f]
[    0.167753] pci 0000:00:03.2: reg 18: [io  0x1c80-0x1c87]
[    0.167760] pci 0000:00:03.2: reg 1c: [io  0x1c78-0x1c7b]
[    0.167766] pci 0000:00:03.2: reg 20: [io  0x1c40-0x1c4f]
[    0.167811] pci 0000:00:03.3: [8086:29b7] type 0 class 0x000700
[    0.167823] pci 0000:00:03.3: reg 10: [io  0x1c90-0x1c97]
[    0.167829] pci 0000:00:03.3: reg 14: [mem 0xd0006000-0xd0006fff]
[    0.167911] pci 0000:00:19.0: [8086:10bd] type 0 class 0x000200
[    0.167929] pci 0000:00:19.0: reg 10: [mem 0xd0020000-0xd003ffff]
[    0.167938] pci 0000:00:19.0: reg 14: [mem 0xd0007000-0xd0007fff]
[    0.167946] pci 0000:00:19.0: reg 18: [io  0x1820-0x183f]
[    0.168022] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.168026] pci 0000:00:19.0: PME# disabled
[    0.168045] pci 0000:00:1a.0: [8086:2937] type 0 class 0x000c03
[    0.168087] pci 0000:00:1a.0: reg 20: [io  0x1840-0x185f]
[    0.168137] pci 0000:00:1a.1: [8086:2938] type 0 class 0x000c03
[    0.168179] pci 0000:00:1a.1: reg 20: [io  0x1860-0x187f]
[    0.168229] pci 0000:00:1a.2: [8086:2939] type 0 class 0x000c03
[    0.168270] pci 0000:00:1a.2: reg 20: [io  0x1880-0x189f]
[    0.168329] pci 0000:00:1a.7: [8086:293c] type 0 class 0x000c03
[    0.168350] pci 0000:00:1a.7: reg 10: [mem 0xd0008000-0xd00083ff]
[    0.168439] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.168443] pci 0000:00:1a.7: PME# disabled
[    0.168466] pci 0000:00:1b.0: [8086:293e] type 0 class 0x000403
[    0.168481] pci 0000:00:1b.0: reg 10: [mem 0xd0000000-0xd0003fff 64bit]
[    0.168546] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.168550] pci 0000:00:1b.0: PME# disabled
[    0.168570] pci 0000:00:1c.0: [8086:2940] type 1 class 0x000604
[    0.168637] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.168641] pci 0000:00:1c.0: PME# disabled
[    0.168666] pci 0000:00:1c.4: [8086:2948] type 1 class 0x000604
[    0.168735] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.168739] pci 0000:00:1c.4: PME# disabled
[    0.168764] pci 0000:00:1d.0: [8086:2934] type 0 class 0x000c03
[    0.168815] pci 0000:00:1d.0: reg 20: [io  0x18a0-0x18bf]
[    0.168875] pci 0000:00:1d.1: [8086:2935] type 0 class 0x000c03
[    0.168917] pci 0000:00:1d.1: reg 20: [io  0x18c0-0x18df]
[    0.168968] pci 0000:00:1d.2: [8086:2936] type 0 class 0x000c03
[    0.169009] pci 0000:00:1d.2: reg 20: [io  0x18e0-0x18ff]
[    0.169068] pci 0000:00:1d.7: [8086:293a] type 0 class 0x000c03
[    0.169089] pci 0000:00:1d.7: reg 10: [mem 0xd0009000-0xd00093ff]
[    0.169177] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.169181] pci 0000:00:1d.7: PME# disabled
[    0.169200] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    0.169262] pci 0000:00:1f.0: [8086:2914] type 0 class 0x000601
[    0.169339] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.169344] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH6 GPIO
[    0.169348] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0500 (mask 00ff)
[    0.169398] pci 0000:00:1f.2: [8086:2922] type 0 class 0x000106
[    0.169416] pci 0000:00:1f.2: reg 10: [io  0x1ca8-0x1caf]
[    0.169424] pci 0000:00:1f.2: reg 14: [io  0x1c9c-0x1c9f]
[    0.169432] pci 0000:00:1f.2: reg 18: [io  0x1ca0-0x1ca7]
[    0.169440] pci 0000:00:1f.2: reg 1c: [io  0x1c98-0x1c9b]
[    0.169448] pci 0000:00:1f.2: reg 20: [io  0x1c00-0x1c1f]
[    0.169456] pci 0000:00:1f.2: reg 24: [mem 0xd000a000-0xd000a7ff]
[    0.169500] pci 0000:00:1f.2: PME# supported from D3hot
[    0.169504] pci 0000:00:1f.2: PME# disabled
[    0.169520] pci 0000:00:1f.3: [8086:2930] type 0 class 0x000c05
[    0.169535] pci 0000:00:1f.3: reg 10: [mem 0xd000b000-0xd000b0ff 64bit]
[    0.169555] pci 0000:00:1f.3: reg 20: [io  0x1c20-0x1c3f]
[    0.169620] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.169666] pci 0000:00:1c.4: PCI bridge to [bus 02-02]
[    0.169732] pci 0000:00:1e.0: PCI bridge to [bus 03-03] (subtractive decode)
[    0.169742] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.169745] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.169747] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.169750] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.169752] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.169755] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.169758] pci 0000:00:1e.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.169760] pci 0000:00:1e.0:   bridge window [mem 0x7e000000-0xf7ffffff] (subtractive decode)
[    0.169763] pci 0000:00:1e.0:   bridge window [mem 0xfc000000-0xfebfffff] (subtractive decode)
[    0.169766] pci 0000:00:1e.0:   bridge window [mem 0xfed00000-0xfedfffff] (subtractive decode)
[    0.169768] pci 0000:00:1e.0:   bridge window [mem 0xfef00000-0xffafffff] (subtractive decode)
[    0.169771] pci 0000:00:1e.0:   bridge window [mem 0xffc00000-0xffefffff] (subtractive decode)
[    0.169785] pci_bus 0000:00: on NUMA node 0
[    0.169789] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.169997] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEXB._PRT]
[    0.170048] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEXC._PRT]
[    0.170132] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIH._PRT]
[    0.170285]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.170289]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.170291] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.176904] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 7 9 10 *11 12 14 15)
[    0.176963] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 7 9 10 11 12 14 15) *5
[    0.177021] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 7 9 *10 11 12 14 15)
[    0.177077] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 7 9 10 *11 12 14 15)
[    0.177133] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 7 *9 10 11 12 14 15)
[    0.177189] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 7 9 10 *11 12 14 15)
[    0.177244] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 7 9 10 *11 12 14 15)
[    0.177301] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 7 9 10 *11 12 14 15)
[    0.177404] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.177418] vgaarb: loaded
[    0.177420] vgaarb: bridge control possible 0000:00:02.0
[    0.177537] i2c-core: driver [aat2870] using legacy suspend method
[    0.177539] i2c-core: driver [aat2870] using legacy resume method
[    0.177622] SCSI subsystem initialized
[    0.180241] libata version 3.00 loaded.
[    0.180241] usbcore: registered new interface driver usbfs
[    0.180241] usbcore: registered new interface driver hub
[    0.180241] usbcore: registered new device driver usb
[    0.180241] PCI: Using ACPI for IRQ routing
[    0.180241] PCI: pci_cache_line_size set to 64 bytes
[    0.180297] Expanded resource reserved due to conflict with PCI Bus 0000:00
[    0.180300] reserve RAM buffer: 000000000009c800 - 000000000009ffff 
[    0.180302] reserve RAM buffer: 000000007d5d0000 - 000000007fffffff 
[    0.180403] NetLabel: Initializing
[    0.180405] NetLabel:  domain hash size = 128
[    0.180406] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.180417] NetLabel:  unlabeled traffic allowed by default
[    0.180462] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.180467] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.180472] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.184237] Switching to clocksource hpet
[    0.192100] AppArmor: AppArmor Filesystem Enabled
[    0.192134] pnp: PnP ACPI init
[    0.192154] ACPI: bus type pnp registered
[    0.192684] pnp 00:00: [bus 00-ff]
[    0.192688] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.192690] pnp 00:00: [io  0x0d00-0xffff window]
[    0.192692] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.192694] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.192697] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.192699] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.192701] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.192704] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.192706] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.192708] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.192710] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.192713] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.192715] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.192717] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.192719] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.192722] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.192724] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.192727] pnp 00:00: [mem 0x7e000000-0xf7ffffff window]
[    0.192729] pnp 00:00: [mem 0xfc000000-0xfebfffff window]
[    0.192731] pnp 00:00: [mem 0xfed00000-0xfedfffff window]
[    0.192734] pnp 00:00: [mem 0xfef00000-0xffafffff window]
[    0.192736] pnp 00:00: [mem 0xffc00000-0xffefffff window]
[    0.192797] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.193014] pnp 00:01: [mem 0xffb00000-0xffbfffff]
[    0.193057] pnp 00:01: Plug and Play ACPI device, IDs INT0800 (active)
[    0.193167] pnp 00:02: [io  0x0010-0x001f]
[    0.193169] pnp 00:02: [io  0x0022-0x002d]
[    0.193171] pnp 00:02: [io  0x0030-0x003f]
[    0.193173] pnp 00:02: [io  0x0050-0x0053]
[    0.193175] pnp 00:02: [io  0x0062-0x0063]
[    0.193177] pnp 00:02: [io  0x0065-0x006f]
[    0.193179] pnp 00:02: [io  0x0074-0x007f]
[    0.193181] pnp 00:02: [io  0x0090-0x009f]
[    0.193183] pnp 00:02: [io  0x00a2-0x00b1]
[    0.193185] pnp 00:02: [io  0x00b2-0x00b3]
[    0.193187] pnp 00:02: [io  0x00b4-0x00bf]
[    0.193189] pnp 00:02: [io  0x00ec-0x00ef]
[    0.193191] pnp 00:02: [io  0x0072-0x0073]
[    0.193193] pnp 00:02: [io  0x004e-0x004f]
[    0.193195] pnp 00:02: [io  0x04d0-0x04d1]
[    0.193197] pnp 00:02: [io  0x1000-0x107f]
[    0.193199] pnp 00:02: [io  0x1100-0x110f]
[    0.193200] pnp 00:02: [io  0x1180-0x11bf]
[    0.193205] pnp 00:02: [io  0x0500-0x057f]
[    0.193207] pnp 00:02: [io  0x0800-0x080f]
[    0.193209] pnp 00:02: [io  0x0810-0x081f]
[    0.193211] pnp 00:02: [io  0xfe00]
[    0.193213] pnp 00:02: [io  0xff00]
[    0.193215] pnp 00:02: [mem 0xfec00000-0xfecfffff]
[    0.193217] pnp 00:02: [mem 0xfee00000-0xfeefffff]
[    0.193219] pnp 00:02: [mem 0xf8000000-0xfbffffff]
[    0.193221] pnp 00:02: [mem 0xfed19000-0xfed19fff]
[    0.193223] pnp 00:02: [mem 0xfed14000-0xfed17fff]
[    0.193225] pnp 00:02: [mem 0xfed18000-0xfed18fff]
[    0.193322] system 00:02: [io  0x04d0-0x04d1] has been reserved
[    0.193325] system 00:02: [io  0x1000-0x107f] has been reserved
[    0.193328] system 00:02: [io  0x1100-0x110f] has been reserved
[    0.193331] system 00:02: [io  0x1180-0x11bf] has been reserved
[    0.193333] system 00:02: [io  0x0500-0x057f] has been reserved
[    0.193336] system 00:02: [io  0x0800-0x080f] has been reserved
[    0.193339] system 00:02: [io  0x0810-0x081f] has been reserved
[    0.193342] system 00:02: [io  0xfe00] has been reserved
[    0.193344] system 00:02: [io  0xff00] has been reserved
[    0.193347] system 00:02: [mem 0xfec00000-0xfecfffff] could not be reserved
[    0.193351] system 00:02: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.193353] system 00:02: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.193356] system 00:02: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.193359] system 00:02: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.193362] system 00:02: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.193365] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.193377] pnp 00:03: [io  0x0000-0x000f]
[    0.193379] pnp 00:03: [io  0x0080-0x008f]
[    0.193381] pnp 00:03: [io  0x00c0-0x00df]
[    0.193383] pnp 00:03: [dma 4]
[    0.193424] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.193438] pnp 00:04: [io  0x0070-0x0071]
[    0.193450] pnp 00:04: [irq 8]
[    0.193491] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.193505] pnp 00:05: [io  0x00f0-0x00fe]
[    0.193510] pnp 00:05: [irq 13]
[    0.193553] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.193563] pnp 00:06: [io  0x0061]
[    0.193605] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.193665] pnp 00:07: [mem 0xfed00000-0xfed003ff]
[    0.193711] pnp 00:07: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.193741] pnp 00:08: [io  0x0060]
[    0.193743] pnp 00:08: [io  0x0064]
[    0.193749] pnp 00:08: [irq 1]
[    0.193800] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.193860] pnp 00:09: [irq 12]
[    0.193929] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.194090] pnp 00:0a: [io  0x0378-0x037b]
[    0.194095] pnp 00:0a: [irq 7]
[    0.194198] pnp 00:0a: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.194355] pnp 00:0b: [io  0x03f8-0x03ff]
[    0.194361] pnp 00:0b: [irq 4]
[    0.194425] pnp 00:0b: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.194461] pnp: PnP ACPI: found 12 devices
[    0.194463] ACPI: ACPI bus type pnp unregistered
[    0.194468] PnPBIOS: Disabled by ACPI PNP
[    0.230882] PCI: max bus depth: 1 pci_try_num: 2
[    0.230920] pci 0000:00:02.1: BAR 0: assigned [mem 0x80000000-0x8007ffff]
[    0.230924] pci 0000:00:02.1: BAR 0: set to [mem 0x80000000-0x8007ffff] (PCI address [0x80000000-0x8007ffff])
[    0.230929] pci 0000:00:1c.4: BAR 14: assigned [mem 0x80100000-0x802fffff]
[    0.230933] pci 0000:00:1c.4: BAR 15: assigned [mem 0x80300000-0x804fffff 64bit pref]
[    0.230937] pci 0000:00:1c.4: BAR 13: assigned [io  0x2000-0x2fff]
[    0.230941] pci 0000:00:1c.0: BAR 14: assigned [mem 0x80500000-0x806fffff]
[    0.230945] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80700000-0x808fffff 64bit pref]
[    0.230948] pci 0000:00:1c.0: BAR 13: assigned [io  0x3000-0x3fff]
[    0.230951] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.230954] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.230959] pci 0000:00:1c.0:   bridge window [mem 0x80500000-0x806fffff]
[    0.230963] pci 0000:00:1c.0:   bridge window [mem 0x80700000-0x808fffff 64bit pref]
[    0.230969] pci 0000:00:1c.4: PCI bridge to [bus 02-02]
[    0.230972] pci 0000:00:1c.4:   bridge window [io  0x2000-0x2fff]
[    0.230977] pci 0000:00:1c.4:   bridge window [mem 0x80100000-0x802fffff]
[    0.230981] pci 0000:00:1c.4:   bridge window [mem 0x80300000-0x804fffff 64bit pref]
[    0.230987] pci 0000:00:1e.0: PCI bridge to [bus 03-03]
[    0.231002] pci 0000:00:1c.0: enabling device (0000 -> 0003)
[    0.231020] pci 0000:00:1c.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.231026] pci 0000:00:1c.0: setting latency timer to 64
[    0.231032] pci 0000:00:1c.4: enabling device (0000 -> 0003)
[    0.231042] pci 0000:00:1c.4: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    0.231046] pci 0000:00:1c.4: setting latency timer to 64
[    0.231053] pci 0000:00:1e.0: setting latency timer to 64
[    0.231057] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.231059] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.231062] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.231064] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.231067] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.231069] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.231071] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.231074] pci_bus 0000:00: resource 11 [mem 0x7e000000-0xf7ffffff]
[    0.231076] pci_bus 0000:00: resource 12 [mem 0xfc000000-0xfebfffff]
[    0.231079] pci_bus 0000:00: resource 13 [mem 0xfed00000-0xfedfffff]
[    0.231081] pci_bus 0000:00: resource 14 [mem 0xfef00000-0xffafffff]
[    0.231083] pci_bus 0000:00: resource 15 [mem 0xffc00000-0xffefffff]
[    0.231086] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
[    0.231088] pci_bus 0000:01: resource 1 [mem 0x80500000-0x806fffff]
[    0.231091] pci_bus 0000:01: resource 2 [mem 0x80700000-0x808fffff 64bit pref]
[    0.231094] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.231096] pci_bus 0000:02: resource 1 [mem 0x80100000-0x802fffff]
[    0.231099] pci_bus 0000:02: resource 2 [mem 0x80300000-0x804fffff 64bit pref]
[    0.231101] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.231104] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.231106] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.231109] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.231111] pci_bus 0000:03: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.231113] pci_bus 0000:03: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.231116] pci_bus 0000:03: resource 10 [mem 0x000dc000-0x000dffff]
[    0.231118] pci_bus 0000:03: resource 11 [mem 0x7e000000-0xf7ffffff]
[    0.231121] pci_bus 0000:03: resource 12 [mem 0xfc000000-0xfebfffff]
[    0.231123] pci_bus 0000:03: resource 13 [mem 0xfed00000-0xfedfffff]
[    0.231126] pci_bus 0000:03: resource 14 [mem 0xfef00000-0xffafffff]
[    0.231128] pci_bus 0000:03: resource 15 [mem 0xffc00000-0xffefffff]
[    0.231172] NET: Registered protocol family 2
[    0.231240] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.231475] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.231897] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.232120] TCP: Hash tables configured (established 131072 bind 65536)
[    0.232123] TCP reno registered
[    0.232126] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.232135] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.232215] NET: Registered protocol family 1
[    0.232230] pci 0000:00:02.0: Boot video device
[    0.232256] pci 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.232272] pci 0000:00:1a.0: PCI INT A disabled
[    0.232279] pci 0000:00:1a.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    0.232295] pci 0000:00:1a.1: PCI INT B disabled
[    0.232304] pci 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.232320] pci 0000:00:1a.2: PCI INT C disabled
[    0.232328] pci 0000:00:1a.7: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    0.232351] pci 0000:00:1a.7: PCI INT B disabled
[    0.232365] pci 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.232381] pci 0000:00:1d.0: PCI INT A disabled
[    0.232388] pci 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    0.232403] pci 0000:00:1d.1: PCI INT B disabled
[    0.232412] pci 0000:00:1d.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    0.232427] pci 0000:00:1d.2: PCI INT C disabled
[    0.232435] pci 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.232448] pci 0000:00:1d.7: PCI INT A disabled
[    0.232460] PCI: CLS 32 bytes, default 64
[    0.232466] Simple Boot Flag at 0x43 set to 0x1
[    0.232822] audit: initializing netlink socket (disabled)
[    0.232832] type=2000 audit(1354067843.228:1): initialized
[    0.253950] highmem bounce pool size: 64 pages
[    0.253955] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.256019] VFS: Disk quotas dquot_6.5.2
[    0.256081] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.256636] fuse init (API version 7.17)
[    0.256736] msgmni has been set to 1679
[    0.257038] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.257064] io scheduler noop registered
[    0.257066] io scheduler deadline registered
[    0.257073] io scheduler cfq registered (default)
[    0.257199] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.257240] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.257301] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.257336] pcieport 0000:00:1c.4: irq 41 for MSI/MSI-X
[    0.257420] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.257444] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.257549] intel_idle: MWAIT substates: 0x220
[    0.257550] intel_idle: does not run on family 6 model 15
[    0.257628] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.257634] ACPI: Power Button [PWRB]
[    0.257688] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.257691] ACPI: Power Button [PWRF]
[    0.257756] Marking TSC unstable due to TSC halts in idle
[    0.257760] ACPI: acpi_idle registered with cpuidle
[    0.259035] ERST: Table is not found!
[    0.259037] GHES: HEST is not enabled!
[    0.259105] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.268053] isapnp: Scanning for PnP cards...
[    0.279494] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.450584] Freeing initrd memory: 13816k freed
[    0.620969] isapnp: No Plug & Play device found
[    0.696588] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.712084] serial 0000:00:03.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.732191] 0000:00:03.3: ttyS4 at I/O 0x1c90 (irq = 17) is a 16550A
[    0.748310] Linux agpgart interface v0.103
[    0.748411] agpgart-intel 0000:00:00.0: Intel Q35 Chipset
[    0.748481] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    0.749466] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.749585] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    0.751130] brd: module loaded
[    0.751928] loop: module loaded
[    0.752059] ahci 0000:00:1f.2: version 3.0
[    0.752072] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.752112] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    0.752173] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    0.752177] ahci 0000:00:1f.2: flags: 64bit ncq sntf led clo pmp pio slum part ccc sxs 
[    0.752181] ahci 0000:00:1f.2: setting latency timer to 64
[    0.752926] scsi0 : ahci
[    0.753017] scsi1 : ahci
[    0.753093] scsi2 : ahci
[    0.753168] scsi3 : ahci
[    0.753242] scsi4 : ahci
[    0.753317] scsi5 : ahci
[    0.753490] ata1: SATA max UDMA/133 abar m2048@0xd000a000 port 0xd000a100 irq 42
[    0.753493] ata2: SATA max UDMA/133 abar m2048@0xd000a000 port 0xd000a180 irq 42
[    0.753496] ata3: SATA max UDMA/133 abar m2048@0xd000a000 port 0xd000a200 irq 42
[    0.753499] ata4: SATA max UDMA/133 abar m2048@0xd000a000 port 0xd000a280 irq 42
[    0.753501] ata5: SATA max UDMA/133 abar m2048@0xd000a000 port 0xd000a300 irq 42
[    0.753504] ata6: SATA max UDMA/133 abar m2048@0xd000a000 port 0xd000a380 irq 42
[    0.753619] pata_acpi 0000:00:03.2: enabling device (0004 -> 0005)
[    0.753623] pata_acpi 0000:00:03.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.753642] pata_acpi 0000:00:03.2: setting latency timer to 64
[    0.753653] pata_acpi 0000:00:03.2: PCI INT C disabled
[    0.753682] ata_generic 0000:00:03.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.753697] ata_generic 0000:00:03.2: setting latency timer to 64
[    0.753988] scsi6 : ata_generic
[    0.754059] scsi7 : ata_generic
[    0.754107] ata7: PATA max UDMA/100 cmd 0x1c88 ctl 0x1c7c bmdma 0x1c40 irq 18
[    0.754110] ata8: PATA max UDMA/100 cmd 0x1c80 ctl 0x1c78 bmdma 0x1c48 irq 18
[    0.754446] Fixed MDIO Bus: probed
[    0.754468] tun: Universal TUN/TAP device driver, 1.6
[    0.754470] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.754528] PPP generic driver version 2.4.2
[    0.754649] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.754665] ehci_hcd 0000:00:1a.7: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    0.754678] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.754681] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.754724] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.754747] ehci_hcd 0000:00:1a.7: debug port 1
[    0.758629] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.758635] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xd0008000
[    0.772029] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.772184] hub 1-0:1.0: USB hub found
[    0.772188] hub 1-0:1.0: 6 ports detected
[    0.772276] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.772287] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.772290] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.772334] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.772354] ehci_hcd 0000:00:1d.7: debug port 1
[    0.776242] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.776260] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xd0009000
[    0.792029] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.792178] hub 2-0:1.0: USB hub found
[    0.792182] hub 2-0:1.0: 6 ports detected
[    0.792267] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.792285] uhci_hcd: USB Universal Host Controller Interface driver
[    0.792302] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.792308] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.792311] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.792358] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.792379] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00001840
[    0.792505] hub 3-0:1.0: USB hub found
[    0.792509] hub 3-0:1.0: 2 ports detected
[    0.792574] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    0.792581] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.792584] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.792625] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.792646] uhci_hcd 0000:00:1a.1: irq 18, io base 0x00001860
[    0.792767] hub 4-0:1.0: USB hub found
[    0.792771] hub 4-0:1.0: 2 ports detected
[    0.792835] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.792841] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.792844] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.792888] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.792918] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00001880
[    0.793041] hub 5-0:1.0: USB hub found
[    0.793045] hub 5-0:1.0: 2 ports detected
[    0.793109] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.793115] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.793118] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.793159] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.793180] uhci_hcd 0000:00:1d.0: irq 20, io base 0x000018a0
[    0.793303] hub 6-0:1.0: USB hub found
[    0.793307] hub 6-0:1.0: 2 ports detected
[    0.793371] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    0.793377] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.793380] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.793424] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.793453] uhci_hcd 0000:00:1d.1: irq 22, io base 0x000018c0
[    0.793579] hub 7-0:1.0: USB hub found
[    0.793583] hub 7-0:1.0: 2 ports detected
[    0.793648] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    0.793655] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.793658] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.793703] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.793734] uhci_hcd 0000:00:1d.2: irq 21, io base 0x000018e0
[    0.793857] hub 8-0:1.0: USB hub found
[    0.793861] hub 8-0:1.0: 2 ports detected
[    0.793980] usbcore: registered new interface driver libusual
[    0.794027] i8042: PNP: PS/2 Controller [PNP0303:KEYB] at 0x60,0x64 irq 1
[    0.794029] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.794546] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.794655] mousedev: PS/2 mouse device common for all mice
[    0.794809] rtc_cmos 00:04: RTC can wake from S4
[    0.794907] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.794929] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.794997] device-mapper: uevent: version 1.0.3
[    0.795070] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.795104] EISA: Probing bus 0 at eisa.0
[    0.795106] EISA: Cannot allocate resource for mainboard
[    0.795108] Cannot allocate resource for EISA slot 1
[    0.795110] Cannot allocate resource for EISA slot 2
[    0.795112] Cannot allocate resource for EISA slot 3
[    0.795114] Cannot allocate resource for EISA slot 4
[    0.795116] Cannot allocate resource for EISA slot 5
[    0.795118] Cannot allocate resource for EISA slot 6
[    0.795119] Cannot allocate resource for EISA slot 7
[    0.795121] Cannot allocate resource for EISA slot 8
[    0.795123] EISA: Detected 0 cards.
[    0.795131] cpufreq-nforce2: No nForce2 chipset.
[    0.795180] cpuidle: using governor ladder
[    0.795256] cpuidle: using governor menu
[    0.795258] EFI Variables Facility v0.08 2004-May-17
[    0.795513] TCP cubic registered
[    0.795636] NET: Registered protocol family 10
[    0.796226] NET: Registered protocol family 17
[    0.796230] Registering the dns_resolver key type
[    0.796251] Using IPI No-Shortcut mode
[    0.796369] PM: Hibernation image not present or could not be loaded.
[    0.796383] registered taskstats version 1
[    0.802701]   Magic number: 4:680:964
[    0.802782] rtc_cmos 00:04: setting system clock to 2012-11-28 01:57:25 UTC (1354067845)
[    0.802820] P-state transition latency capped at 20 uS
[    0.802899] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.802901] EDD information not available.
[    0.815065] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.072039] ata5: SATA link down (SStatus 0 SControl 300)
[    1.072061] ata6: SATA link down (SStatus 0 SControl 300)
[    1.072075] ata4: SATA link down (SStatus 0 SControl 300)
[    1.072091] ata3: SATA link down (SStatus 0 SControl 300)
[    1.104024] usb 2-2: new high-speed USB device number 2 using ehci_hcd
[    1.236608] hub 2-2:1.0: USB hub found
[    1.236691] hub 2-2:1.0: 3 ports detected
[    1.244027] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.244042] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.246928] ata1.00: ATA-8: WDC WD10EARS-00Y5B1, 80.00A80, max UDMA/133
[    1.246932] ata1.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    1.247435] ata2.00: ATAPI: Optiarc DVD-ROM DDU1671S, 1.81, max UDMA/33
[    1.247439] ata2.00: applying bridge limits
[    1.248795] ata2.00: configured for UDMA/33
[    1.248975] ata1.00: configured for UDMA/133
[    1.249100] scsi 0:0:0:0: Direct-Access     ATA      WDC WD10EARS-00Y 80.0 PQ: 0 ANSI: 5
[    1.249218] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.249244] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.249265] sd 0:0:0:0: [sda] Write Protect is off
[    1.249268] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.249288] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.254989] scsi 1:0:0:0: CD-ROM            Optiarc  DVD-ROM DDU1671S 1.81 PQ: 0 ANSI: 5
[    1.257526] sr0: scsi3-mmc drive: 4x/48x cd/rw xa/form2 cdda tray
[    1.257529] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.257662] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.257738] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.347162]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 sda8 >
[    1.347749] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.422340] Freeing unused kernel memory: 712k freed
[    1.422557] Write protecting the kernel text: 5624k
[    1.422604] Write protecting the kernel read-only data: 2324k
[    1.437943] udevd[99]: starting version 175
[    1.484518] e1000e: Intel(R) PRO/1000 Network Driver - 1.5.1-k
[    1.484521] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    1.484567] e1000e 0000:00:19.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.484577] e1000e 0000:00:19.0: setting latency timer to 64
[    1.484665] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[    1.524201] usb 2-2.1: new low-speed USB device number 3 using ehci_hcd
[    1.643369] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2.1/2-2.1:1.0/input/input3
[    1.643473] generic-usb 0003:046D:C03E.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-2.1/input0
[    1.643488] usbcore: registered new interface driver usbhid
[    1.643489] usbhid: USB HID core driver
[    1.724198] usb 2-2.3: new full-speed USB device number 4 using ehci_hcd
[    1.790308] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) 00:19:99:26:44:a6
[    1.790311] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    1.790333] e1000e 0000:00:19.0: eth0: MAC: 7, PHY: 6, PBA No: FFFFFF-0FF
[    2.446110] kjournald starting.  Commit interval 5 seconds
[    2.446144] EXT3-fs (sda5): mounted filesystem with ordered data mode
[    2.900210] generic-usb 0003:056D:0002.0002: hiddev0,hidraw1: USB HID v1.10 Device [EIZO EIZO USB HID Monitor] on usb-0000:00:1d.7-2.3/input0
[   14.817399] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.835863] udevd[316]: starting version 175
[   14.882000] lp: driver loaded but no devices found
[   14.887651] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   14.887950] mei 0000:00:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.887955] mei 0000:00:03.0: setting latency timer to 64
[   14.887990] mei 0000:00:03.0: irq 44 for MSI/MSI-X
[   14.890678] [drm] Initialized drm 1.1.0 20060810
[   14.893863] Adding 1048572k swap on /dev/sda2.  Priority:-1 extents:1 across:1048572k 
[   14.960903] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.960909] i915 0000:00:02.0: setting latency timer to 64
[   15.007166] i915 0000:00:02.0: irq 45 for MSI/MSI-X
[   15.007173] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   15.007175] [drm] Driver supports precise vblank timestamp query.
[   15.007213] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   15.065570] parport_pc 00:0a: reported by Plug and Play ACPI
[   15.065594] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   15.101017] type=1400 audit(1354064259.797:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=483 comm="apparmor_parser"
[   15.101447] type=1400 audit(1354064259.797:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=483 comm="apparmor_parser"
[   15.101688] type=1400 audit(1354064259.797:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=483 comm="apparmor_parser"
[   15.104478] EXT3-fs (sda5): using internal journal
[   15.105127] type=1400 audit(1354064259.801:5): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=542 comm="apparmor_parser"
[   15.152190] lp0: using parport0 (interrupt-driven).
[   15.298171] ppdev: user-space parallel port driver
[   15.404414] [drm] initialized overlay support
[   15.484418] init: failsafe main process (673) killed by TERM signal
[   15.541218] type=1400 audit(1354064260.237:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=724 comm="apparmor_parser"
[   15.543120] type=1400 audit(1354064260.237:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=723 comm="apparmor_parser"
[   15.544023] type=1400 audit(1354064260.241:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=724 comm="apparmor_parser"
[   15.544307] type=1400 audit(1354064260.241:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=724 comm="apparmor_parser"
[   15.556486] type=1400 audit(1354064260.253:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=726 comm="apparmor_parser"
[   15.573187] fbcon: inteldrmfb (fb0) is primary device
[   15.574707] type=1400 audit(1354064260.269:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=726 comm="apparmor_parser"
[   15.742753] Console: switching to colour frame buffer device 240x75
[   15.752153] fb0: inteldrmfb frame buffer device
[   15.752155] drm: registered panic notifier
[   15.754630] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   15.754671] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   15.754725] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   15.754751] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   15.777089] Bluetooth: Core ver 2.16
[   15.779151] NET: Registered protocol family 31
[   15.779155] Bluetooth: HCI device and connection manager initialized
[   15.779157] Bluetooth: HCI socket layer initialized
[   15.779159] Bluetooth: L2CAP socket layer initialized
[   15.791209] Bluetooth: SCO socket layer initialized
[   15.806549] hda_codec: ALC262: BIOS auto-probing.
[   15.808570] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.808573] Bluetooth: BNEP filters: protocol multicast
[   15.814491] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
[   15.814689] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   15.814873] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   15.815056] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   15.815151] input: HDA Intel Line-Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   15.889766] Bluetooth: RFCOMM TTY layer initialized
[   15.889771] Bluetooth: RFCOMM socket layer initialized
[   15.889773] Bluetooth: RFCOMM ver 1.11
[   16.244218] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   16.300074] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   16.300315] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.303248] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.616885] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   17.616890] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   17.617054] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   28.472014] eth0: no IPv6 routers present
```glxinfo
```
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_create_context_es2_profile, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Q35 x86/MMX/SSE2
OpenGL version string: 1.4 Mesa 8.0.4
OpenGL extensions:
    GL_ARB_multisample, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_copy_texture, 
    GL_EXT_polygon_offset, GL_EXT_subtexture, GL_EXT_texture_object, 
    GL_EXT_vertex_array, GL_EXT_compiled_vertex_array, GL_EXT_texture, 
    GL_EXT_texture3D, GL_IBM_rasterpos_clip, GL_ARB_point_parameters, 
    GL_EXT_draw_range_elements, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_separate_specular_color, 
    GL_EXT_texture_edge_clamp, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_ARB_multitexture, GL_IBM_multimode_draw_arrays, 
    GL_IBM_texture_mirrored_repeat, GL_3DFX_texture_compression_FXT1, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, GL_ARB_transpose_matrix, 
    GL_EXT_blend_func_separate, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_secondary_color, GL_EXT_texture_env_add, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_INGR_blend_func_separate, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, 
    GL_SUN_multi_draw_arrays, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_EXT_framebuffer_object, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, GL_MESA_window_pos, 
    GL_NV_packed_depth_stencil, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_ARB_depth_texture, GL_ARB_shadow, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_window_pos, 
    GL_EXT_stencil_two_side, GL_EXT_texture_cube_map, GL_NV_vertex_program1_1, 
    GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_shader_objects, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ATI_draw_buffers, 
    GL_ATI_texture_env_combine3, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_ARB_half_float_pixel, 
    GL_ARB_point_sprite, GL_ARB_shading_language_100, GL_ARB_sync, 
    GL_ARB_texture_non_power_of_two, GL_ARB_vertex_buffer_object, 
    GL_ATI_blend_equation_separate, GL_EXT_blend_equation_separate, 
    GL_OES_read_format, GL_ARB_pixel_buffer_object, GL_ARB_texture_rectangle, 
    GL_EXT_pixel_buffer_object, GL_EXT_texture_rectangle, 
    GL_ARB_framebuffer_object, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_packed_depth_stencil, 
    GL_APPLE_object_purgeable, GL_ARB_vertex_array_object, 
    GL_ATI_separate_stencil, GL_EXT_gpu_program_parameters, GL_OES_EGL_image, 
    GL_ARB_copy_buffer, GL_ARB_map_buffer_range, 
    GL_EXT_separate_shader_objects, GL_ARB_ES2_compatibility, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_explicit_attrib_location, 
    GL_ARB_provoking_vertex, GL_ARB_sampler_objects, GL_EXT_provoking_vertex, 
    GL_ARB_robustness

32 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x091 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x092 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x093 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x094 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x095 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x096 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x097 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x098 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x099 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x09a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x09c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x09d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x09f 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a1 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a2 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a4 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a5 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a6 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a7 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a8 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a9 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0aa 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0ab 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0ac 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0ad 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x060 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None

48 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x061  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x062  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x063  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x064  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x065  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x066  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x067 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x068 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x069 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x06a 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06d 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x070 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x071 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x072 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x073  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x074  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x075 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x076 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x077 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x078 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x079  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07a  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07b  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07c  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07d  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07e  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07f 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x080 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x081 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x082 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x083 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x084 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x085 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x086 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x087 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x088 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x089 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08b  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x08c  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x08d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x08e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x08f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x090 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
```

---

