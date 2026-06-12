---
title: "computer drops to low graphics mode after powersave"
date: 2010-05-31
forum: Multimedia Software
---

### Post by violinuxer on 2010-05-31
I have recently been experiencing some issues with the powersave on my computer. I had my computer set to put the display to sleep after 10 minutes and put the computer to sleep after 30 minutes. The screen saver also activates at 5 minutes. When I woke up my computer (hit the power button) the computer would sometimes tell me that it was going into low graphics mode. I had to reboot to get my x server back. I disabled the power save to fix the problem, but I would really like to have it back. My latest Xorg.log gives an error, but I'm not sure if the power save caused the problem (more below). I am running a computer with an Intel Integrated chipset.

My questions:

What caused the x server to crash?

Should I post a bug report on Launchpad? If so, how? (im a bit of a noob as far as bug reporting:???:)

How can I fix the problem?

Thanks so much!

violinuxer

Xorg.log:

```
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux eamon-desktop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686
Kernel command line: root=UUID=a8b870dc-b72b-4c9d-9f30-a5b45f25e3a8 ro splash quiet 
Build Date: 23 April 2010  05:11:50PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.7.log", Time: Mon May 17 16:42:18 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Optoma PanoView PV755A"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI:*(0:0:2:0) 8086:2582:103c:3005 Intel Corporation 82915G/GV/910GL Integrated Graphics Controller rev 4, Mem @ 0xcfe00000/524288, 0xe0000000/268435456, 0xcff00000/262144, I/O @ 0x00001800/8
(--) PCI: (0:0:2:1) 8086:2782:103c:3005 Intel Corporation 82915G Integrated Graphics Controller rev 4, Mem @ 0xcfe80000/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.9.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) Primary Device is: PCI 00@00:02:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 915G
(--) intel(0): Chipset: "915G"
(II) intel(0): Output VGA1 using monitor section Optoma PanoView PV755A
(II) intel(0): EDID for output VGA1
(II) intel(0): Not using mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "640x350" (vrefresh out of range)
(II) intel(0): Not using default mode "320x175" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x400" (vrefresh out of range)
(II) intel(0): Not using default mode "320x200" (doublescan mode not supported)
(II) intel(0): Not using default mode "720x400" (vrefresh out of range)
(II) intel(0): Not using default mode "360x200" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (interlace mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x960" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
(II) intel(0): Not using default mode "1792x1344" (hsync out of range)
(II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
(II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
(II) intel(0): Not using default mode "1856x1392" (hsync out of range)
(II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (hsync out of range)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "416x312" (doublescan mode not supported)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (hsync out of range)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "2048x1536"x60.0  266.95  2048 2200 2424 2800  1536 1537 1540 1589 -hsync +vsync (95.3 kHz)
(II) intel(0): Modeline "1920x1440"x60.0  234.00  1920 2048 2256 2600  1440 1441 1444 1500 -hsync +vsync (90.0 kHz)
(II) intel(0): Modeline "1856x1392"x60.0  218.30  1856 1952 2176 2528  1392 1393 1396 1439 -hsync +vsync (86.4 kHz)
(II) intel(0): Modeline "1792x1344"x60.0  204.80  1792 1920 2120 2448  1344 1345 1348 1394 -hsync +vsync (83.7 kHz)
(II) intel(0): Modeline "1600x1200"x75.0  202.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (93.8 kHz)
(II) intel(0): Modeline "1600x1200"x70.0  189.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (87.5 kHz)
(II) intel(0): Modeline "1600x1200"x65.0  175.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (81.2 kHz)
(II) intel(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) intel(0): Modeline "1680x1050"x74.9  187.00  1680 1800 1976 2272  1050 1053 1059 1099 -hsync +vsync (82.3 kHz)
(II) intel(0): Modeline "1680x1050"x69.9  174.00  1680 1800 1976 2272  1050 1053 1059 1096 -hsync +vsync (76.6 kHz)
(II) intel(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz)
(II) intel(0): Modeline "1400x1050"x74.8  155.80  1400 1464 1784 1912  1050 1052 1064 1090 +hsync +vsync (81.5 kHz)
(II) intel(0): Modeline "1400x1050"x70.0  145.06  1400 1496 1648 1896  1050 1051 1054 1093 -hsync +vsync (76.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
(II) intel(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(II) intel(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Output VGA1 connected
(II) intel(0): Using user preference for initial modes
(II) intel(0): Output VGA1 using initial mode 1024x768
(II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(==) Depth 24 pixmap format is 32 bpp
(II) intel(0): [DRI2] Setup complete
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): No memory allocations

Fatal server error:
Failed to submit batchbuffer: Input/output error


Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.7.log" for additional information.

 ddxSigGiveUp: Closing log
```My Xorg.conf (manually edited because of some refresh rate issues):

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "intel"
EndSection

Section "Monitor"
    Identifier    "Optoma PanoView PV755A"
    HorizSync    31-101
        VertRefresh    60-75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Optoma PanoView PV755A"
    Device        "Configured Video Device"
    SubSection "Display"
        Depth        24
        Modes        "1024x768" "800x600" "640x480" 
    EndSubSection
EndSection
```My hardware (from lspci):

```
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation 82915G Integrated Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
40:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
```

---

### Post by violinuxer on 2010-06-02
Just had my computer crash on logout. could this mean a problem with gdm? i am attaching my messages log; it has some interesting messages about Invalid EDIDs.:confused:

Does anyone know where x server puts its error logs? I have 7 xorg.log's but they are all old.

Another thing- should I /how do I move this to general support?

Thanks again!

violinuxer

---

### Post by TylerW on 2010-06-24
I am like extremely new to Linux and the terminal stuff in any operating system (just learned how to command line shut down :P  Bad I know.)

I was told that you could put ubuntu on any system so I put the newest (Ubuntu Version 10.04 LTS) on my Dell Dimension 4700 series with an Intel 915G processor.

Worked fine until a while ago where I noticed that my display would go into sleep mode and then would not set the actual system into sleep mode.  I moved the mouse to wake the display up and Low Graphics Mode came up.  I looked at the log (because even though I have no clue what I am doing, I figured I could find something that went wrong) and the end showed the same thing here.  So, I am stuck with the same problem you are having.

Like I said, I am a total newbie at all this, so don't mind me.  I guess this is more common than anything.  From what I see on launchpad, this happens with Fedora to a lot of people.

(sorry I couldn't help, but I wanted to follow this)

---

### Post by violinuxer on 2010-06-28
Welcome to the forums! ):P I am new to the forums but have been using linux for about a year and have had quite a few problems with graphics too.

Ont thing- have you tried running any 3d games? I found that there was one game that always crashed like the powersave when it was in full screen, so I think it might be a problem with OpenGL (basically open source Direct3D).

Also, are you running desktop effects? You can check by going to System > Preferences > Appearance > Visual Effects Tab. If Normal or extra are checked, then desktop effects are running. If the effects are running, try running this command in terminal:

```
sudo metacity --replace
```Note: This turns _off_ desktop effects, but for me it fixed the problem with the 3d games. I think the computer gets hung up when exiting from the screensaver, so, assuming that you are running an OpenGL screensaver (3D), this might help as a workaround.

If you want to turn desktop effects back on run this command:

```
sudo compiz --replace
```You may or may not need the sudo in front, it just tells the computer to run as root (administrator). I can't remember if you need it or not :tongue:

It might also help to know a little bit more about your system. To get more info, run this
command:

```
lspci >> lspci.txt
```This will create a text file (lspci.txt) in your home folder that contains info on the system board and stuff connected to it.

Also, run this command to tell about your 3D acceleration capablilties. It will again create a text file.

```
glxinfo >> glxinfo.txt
```You can then attach those text files to your next post to help with troubleshooting.

So, to sum it up, you might try running some _fullscreen_ 3d games (cannon smash will probably run on your computer. its a ping-pong game)  and see if it crashes. For me, it actually goes to a black screen with some text on it but I am pretty sure that the X server is crashing.

If you need help installing games, feel free to ask.

Hope this helps and best of luck to you!

violinuxer

---

### Post by t3h_g3n3r4l on 2010-06-28
Actually, I am having a similar problem, it's just fairly random in occurance.  Some days, I will turn off the monitor when I leave the lab for the night and come back and all is well, but other times I'll leave the monitor on and get the X server crash after about half an hour.

When I go to restart the X server, however, is when things get bad.  The system will hang up on "checking battery state."  I'm on a desktop (Jetway Atom 330, 1GB ram) with power saving features turned off.  I checked the .xsession-errors file and get the following:

```

(polkit-gnome-authentication-agent-1:1155): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1155): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** (nm-applet:1166): DEBUG: old state indicates that this was not a disconnect 0

(gnome-power-manager:1151): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x9c610f8'

** (gnome-power-manager:1151): WARNING **: Either HAL or DBUS are not working!

** (gnome-power-manager:1151): WARNING **: proxy failed

** (gnome-power-manager:1151): WARNING **: failed to get Computer root object

** (gnome-power-manager:1151): WARNING **: proxy NULL!!
[Info  12:08:45.587] Docky version: 2.0.2 Release
[Info  12:08:05.589] Kernel version: 2.6.32.22
[Info  12:08:05.613] CLR version: 2.0.50727.1433
Initializing nautilus-gdu extension
Unable to find a synaptics device.
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
Starting gtk-window-decorator
Unable to open desktop file evolution-mail.desktop for panel launcher
/usr/bin/compiz (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
I/O warning : failed to load external entity "/home/alston/.compiz/session/1012e95637d97e333e127774492386681000000010490028"
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
evolution-alarm-notify-Message: Setting timeout for 24684 1277769600 1277744916
evolution-alarm-notify-Message:  Mon Jun 28 19:00:00 2010

evolution-alarm-notify-Message:  Mon Jun 28 12:08:36 2010

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

** (update-notifier:1420): DEBUG: Skipping reboot required
```

I don't have this problem with my laptop, nor did I have this problem under 9.04 or 9.10, just 10.04.

---

### Post by TylerW on 2010-06-28
> **violinuxer said:**
> Welcome to the forums! ):P I am new to the forums but have been using linux for about a year and have had quite a few problems with graphics too.

Ont thing- have you tried running any 3d games? I found that there was one game that always crashed like the powersave when it was in full screen, so I think it might be a problem with OpenGL (basically open source Direct3D).

Also, are you running desktop effects? You can check by going to System > Preferences > Appearance > Visual Effects Tab. If Normal or extra are checked, then desktop effects are running. If the effects are running, try running this command in terminal:

```
sudo metacity --replace
```Note: This turns _off_ desktop effects, but for me it fixed the problem with the 3d games. I think the computer gets hung up when exiting from the screensaver, so, assuming that you are running an OpenGL screensaver (3D), this might help as a workaround.

If you want to turn desktop effects back on run this command:

```
sudo compiz --replace
```You may or may not need the sudo in front, it just tells the computer to run as root (administrator). I can't remember if you need it or not :tongue:

It might also help to know a little bit more about your system. To get more info, run this
command:

```
lspci >> lspci.txt
```This will create a text file (lspci.txt) in your home folder that contains info on the system board and stuff connected to it.

Also, run this command to tell about your 3D acceleration capablilties. It will again create a text file.

```
glxinfo >> glxinfo.txt
```You can then attach those text files to your next post to help with troubleshooting.

So, to sum it up, you might try running some _fullscreen_ 3d games (cannon smash will probably run on your computer. its a ping-pong game)  and see if it crashes. For me, it actually goes to a black screen with some text on it but I am pretty sure that the X server is crashing.

If you need help installing games, feel free to ask.

Hope this helps and best of luck to you!

violinuxer

Heh.  Sorry I am not really helping the issue, but I did find something relevant to this similar crash that I got on my system.

I set the power save setting for my monitor so it does not go into standby mode after 30 minutes.  Although, I did keep my system set to go into sleep mode after an hour or so.

I no longer see the "low graphics warning" and I did try putting graphic effects on again.  Still no crash and I haven't shut the computer down in four days.

So, maybe this is the solution to *my problem*, sorry.  But maybe this could help you in some strange and odd way...

Here is the summary of my 3D capabilities.  This is on a Dell Inspiron 4700 Series with an Intel 915G card.  (note: games ran fine when it was running Windows XP.)

***Just tested Cannon Smash.  Ran great.  Smooth graphics.***

---

### Post by t3h_g3n3r4l on 2010-06-29
I'm thinking there is a bug with the gnome-power-manager on powering down the monitor.  What video chipset are you using?

My computer in question is running an Intel 945 video chipset.

---

### Post by violinuxer on 2010-06-29
I think Im running the intel 915 g

---

### Post by violinuxer on 2010-06-29
btw, you might try running this and then do a reboot:

```
sudo dpkg-reconfigure xserver-xorg 
```

Fixed the problems with 3d for me.

Hope this helps!

violinuxer

---

### Post by t3h_g3n3r4l on 2010-06-29
I guess I should have mentioned, I am running desktop effects, but set at normal and not playing any 3D games.  I primarily use this box for web browsing and MATLAB based data acquisition, so the problem is more of an annoyance than anything.

I looked through some of the bugs in launchpad (searched for intel 945), and most of the bugs listed seem to be related to compiz crashing and locking up the system.  None of them reported the "low graphics mode" issue we seem to be facing.

Also, does anybody else's .xsession-errors log have anything similar to what I posted earlier  (HAL or DBUS not working, proxy failed, etc)?  It might be a clue as to where the problem is arising.

---

### Post by violinuxer on 2010-06-29
Just a thought- If you checked your x errors **after** rebooting, you may not have gotten the data on the x crash. I got a fatal error when I checked mine. Here is what I did:

1. Reproduce crash

2. When the low graphics mode choices come up, choose to exit to console login.

3. Login and immediately type the following command:

```
nano ./xsession-errors
```It might also be worth backing it up:

```
sudo cp ./xsession-errors ./<enter new file name here>
```Hope this helps!

violinuxer

---

### Post by t3h_g3n3r4l on 2010-06-30
So, I re-enabled the power saving mode for the monitor under the power preferences and got the crash again.  Here's the tail-end of the xsession-errors file from after the crash:


```
evolution-alarm-notify-Message: Setting timeout for 24016 1277856000 1277831984
evolution-alarm-notify-Message:  Tue Jun 29 19:00:00 2010

evolution-alarm-notify-Message:  Tue Jun 29 12:19:44 2010

** (update-notifier:1397): DEBUG: Skipping reboot required

(gnome-terminal:1422): Gtk-CRITICAL **: gtk_accel_map_unlock_path: assertion `entry != NULL && entry->lock_count > 0' failed

(gnome-appearance-properties:1855): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1855): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-display-properties:1858): Gtk-WARNING **: Ignoring the separator setting

(gnome-display-properties:1858): Gtk-WARNING **: No object called: 

(gnome-terminal:1881): Gtk-CRITICAL **: gtk_accel_map_unlock_path: assertion `entry != NULL && entry->lock_count > 0' failed

(gnome-appearance-properties:1950): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:1950): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(firefox-bin:1368): Gtk-CRITICAL **: _gtk_text_layout_get_block_cursor: assertion `layout != NULL' failed

(firefox-bin:1368): Gtk-CRITICAL **: gtk_text_layout_get_cursor_locations: assertion `layout != NULL' failed

(firefox-bin:1368): Gdk-CRITICAL **: gdk_window_invalidate_rect_full: assertion `GDK_IS_WINDOW (window)' failed

(firefox-bin:1368): Gdk-CRITICAL **: gdk_window_invalidate_rect_full: assertion `GDK_IS_WINDOW (window)' failed

(firefox-bin:1368): Gtk-CRITICAL **: _gtk_text_layout_get_block_cursor: assertion `layout != NULL' failed

(firefox-bin:1368): Gtk-CRITICAL **: gtk_text_layout_get_cursor_locations: assertion `layout != NULL' failed

(firefox-bin:1368): Gdk-CRITICAL **: gdk_window_invalidate_rect_full: assertion `GDK_IS_WINDOW (window)' failed

(firefox-bin:1368): Gdk-CRITICAL **: gdk_window_invalidate_rect_full: assertion `GDK_IS_WINDOW (window)' failed
** (nm-applet:1189): DEBUG: old state indicates that this was not a disconnect 2
** (nm-applet:1189): DEBUG: foo_client_state_changed_cb
** (nm-applet:1189): DEBUG: going for offline with icon: notification-network-ethernet-disconnected
** (nm-applet:1189): DEBUG: going for offline with icon: notification-network-ethernet-disconnected
** (nm-applet:1189): DEBUG: old state indicates that this was not a disconnect 1
** (nm-applet:1189): DEBUG: old state indicates that this was not a disconnect 1
** (nm-applet:1189): DEBUG: old state indicates that this was not a disconnect 2
(gnome-power-manager:1183): devkit-power-gobject-DEBUG: DBUS timed out, but recovering
** (nm-applet:1189): DEBUG: foo_client_state_changed_cb
** (update-notifier:1397): DEBUG: --security-updates-unattended: 0

gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

** (gnome-settings-daemon:1168): WARNING **: Connection failed, reconnecting...
evolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1277856000
gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-power-manager: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
nautilus: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
Docky: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
evolution-alarm-notify-Message: alarm.c:249: Requested removal of nonexistent alarm!
gtk-window-decorator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
XOpenDisplay() failed
gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
applet.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
update-manager: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
firefox-bin: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
gnome-panel: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
Window manager error: Unable to open X display :0.0
**
ERROR:orbit-object.c:149:do_unref: assertion failed: (robj->refs < ORBIT_REFCOUNT_MAX && robj->refs > 0)
```

---

