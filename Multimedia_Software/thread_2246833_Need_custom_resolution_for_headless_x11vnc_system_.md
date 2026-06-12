---
title: "Need custom resolution for headless x11vnc system using xorg dummy display driver"
date: 2014-10-03
forum: Multimedia Software
---

### Post by ben115 on 2014-10-03
***NOTE***
I just solved this problem as I was typing up the post, but I get an error message every time I startup due to the way I "solved" it.  So it's not a permanent solution, and for that reason I didn't prefix this with [SOLVED].

Setup: 
    1) CPU running x11vnc server: headless, Ubuntu 12.04 LTS 32bit OS, i5 processor, integrated graphics, 8gb RAM, 250gb ssd  
    2) Tablet running vnc viewer:   Android tablet with 1280x800 screen resolution using bVNC Free (generic vnc viewer).

Goal: 
    I want to connect to my headless system (via my Android tablet) with a custom resolution of 1280x800 using the Xorg dummy display driver.

What I've Done:
Installed the Xorg dummy display driver:
```
sudo apt-get install xserver-xorg-video-dummy
```
Modified /etc/X11/xorg.conf:
```
Section "Device"    Identifier  "Configured Video Device"
    Driver      "dummy"
EndSection


Section "Monitor"
    Identifier  "Configured Monitor"
    HorizSync 22-83
    VertRefresh 50-76
EndSection


Section "Screen"
    Identifier  "Default Screen"
    Monitor     "Configured Monitor"
    Device      "Configured Video Device"
    DefaultDepth 24
    SubSection "Display"
    Depth 24
    Modes "1024x800"
    EndSubSection
EndSection
```
This results in me connecting to my headless system at a resolution of 1360x768.  If I go to change the display under system settings, I have options for 1360x768(16:9), 1024x768(4:3), 896x672(4:3), 832x624(4:3), and 800x600(4:3).  I looked at my Xorg log file and saw that the virtual size is set to 1360x768, so I guess "1024x800" was not recognized and the driver defaulted to the virtual size?

Here are the results in the logfile, /var/log/Xorg.0.log:
```
[     3.666] X.Org X Server 1.11.3
Release Date: 2011-12-16
[     3.667] X Protocol Version 11, Revision 0
[     3.667] Build Operating System: Linux 2.6.42-37-generic i686 Ubuntu
[     3.667] Current Operating System: Linux nuc-minipc 3.2.0-68-generic-pae #102-Ubuntu SMP Tue Aug 12 22:23:54 UTC 2014 i686
[     3.667] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-68-generic-pae root=UUID=8e01152d-35e3-453a-ba5e-958b140db610 ro quiet splash vt.handoff=7
[     3.667] Build Date: 16 October 2013  04:45:22PM
[     3.667] xorg-server 2:1.11.4-0ubuntu10.14 (For technical support please see http://www.ubuntu.com/support) 
[     3.667] Current version of pixman: 0.30.2
[     3.667]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     3.667] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     3.667] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Oct  3 11:15:31 2014
[     3.667] (==) Using config file: "/etc/X11/xorg.conf"
[     3.667] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     3.667] (==) No Layout section.  Using the first Screen section.
[     3.667] (**) |-->Screen "Default Screen" (0)
[     3.667] (**) |   |-->Monitor "Configured Monitor"
[     3.667] (**) |   |-->Device "Configured Video Device"
[     3.667] (==) Automatically adding devices
[     3.667] (==) Automatically enabling devices
[     3.667] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     3.667]     Entry deleted from font path.
[     3.667] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     3.667]     Entry deleted from font path.
[     3.667] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     3.667]     Entry deleted from font path.
[     3.667] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     3.667]     Entry deleted from font path.
[     3.667] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     3.667]     Entry deleted from font path.
[     3.667] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[     3.667]     Entry deleted from font path.
[     3.667] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     3.667] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     3.667] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     3.667] (II) Loader magic: 0xb77fc5a0
[     3.667] (II) Module ABI versions:
[     3.667]     X.Org ANSI C Emulation: 0.4
[     3.667]     X.Org Video Driver: 11.0
[     3.667]     X.Org XInput driver : 16.0
[     3.667]     X.Org Server Extension : 6.0
[     3.668] (--) PCI:*(0:0:2:0) 8086:0166:8086:204f rev 9, Mem @ 0xf7800000/4194304, 0xe0000000/268435456, I/O @ 0x0000f000/64
[     3.668] (II) Open ACPI successful (/var/run/acpid.socket)
[     3.668] (II) LoadModule: "extmod"
[     3.669] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[     3.669] (II) Module extmod: vendor="X.Org Foundation"
[     3.669]     compiled for 1.11.3, module version = 1.0.0
[     3.669]     Module class: X.Org Server Extension
[     3.669]     ABI class: X.Org Server Extension, version 6.0
[     3.669] (II) Loading extension MIT-SCREEN-SAVER
[     3.669] (II) Loading extension XFree86-VidModeExtension
[     3.669] (II) Loading extension XFree86-DGA
[     3.669] (II) Loading extension DPMS
[     3.669] (II) Loading extension XVideo
[     3.669] (II) Loading extension XVideo-MotionCompensation
[     3.669] (II) Loading extension X-Resource
[     3.669] (II) LoadModule: "dbe"
[     3.669] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[     3.669] (II) Module dbe: vendor="X.Org Foundation"
[     3.669]     compiled for 1.11.3, module version = 1.0.0
[     3.669]     Module class: X.Org Server Extension
[     3.669]     ABI class: X.Org Server Extension, version 6.0
[     3.669] (II) Loading extension DOUBLE-BUFFER
[     3.669] (II) LoadModule: "glx"
[     3.669] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     3.670] (II) Module glx: vendor="X.Org Foundation"
[     3.670]     compiled for 1.11.3, module version = 1.0.0
[     3.670]     ABI class: X.Org Server Extension, version 6.0
[     3.670] (==) AIGLX enabled
[     3.670] (II) Loading extension GLX
[     3.670] (II) LoadModule: "record"
[     3.670] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[     3.670] (II) Module record: vendor="X.Org Foundation"
[     3.670]     compiled for 1.11.3, module version = 1.13.0
[     3.670]     Module class: X.Org Server Extension
[     3.670]     ABI class: X.Org Server Extension, version 6.0
[     3.670] (II) Loading extension RECORD
[     3.670] (II) LoadModule: "dri"
[     3.670] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[     3.670] (II) Module dri: vendor="X.Org Foundation"
[     3.670]     compiled for 1.11.3, module version = 1.0.0
[     3.670]     ABI class: X.Org Server Extension, version 6.0
[     3.670] (II) Loading extension XFree86-DRI
[     3.670] (II) LoadModule: "dri2"
[     3.670] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     3.670] (II) Module dri2: vendor="X.Org Foundation"
[     3.670]     compiled for 1.11.3, module version = 1.2.0
[     3.670]     ABI class: X.Org Server Extension, version 6.0
[     3.670] (II) Loading extension DRI2
[     3.670] (II) LoadModule: "dummy"
[     3.670] (II) Loading /usr/lib/xorg/modules/drivers/dummy_drv.so
[     3.671] (II) Module dummy: vendor="X.Org Foundation"
[     3.671]     compiled for 1.11.3, module version = 0.3.4
[     3.671]     Module class: X.Org Video Driver
[     3.671]     ABI class: X.Org Video Driver, version 11.0
[     3.671] (II) DUMMY: Driver for Dummy chipsets: dummy
[     3.671] (WW) Falling back to old probe method for dummy
[     3.671] (II) Loading /usr/lib/xorg/modules/drivers/dummy_drv.so
[     3.671] (II) DUMMY(0): Chipset is a DUMMY
[     3.671] (**) DUMMY(0): Depth 24, (--) framebuffer bpp 32
[     3.671] (==) DUMMY(0): RGB weight 888
[     3.671] (==) DUMMY(0): Default visual is TrueColor
[     3.671] (==) DUMMY(0): Using gamma correction (1.0, 1.0, 1.0)
[     3.671] (--) DUMMY(0): VideoRAM: 4096 kByte
[     3.671] (--) DUMMY(0): Max Clock: 230000 kHz
[     3.671] (II) DUMMY(0): Configured Monitor: Using hsync range of 22.00-83.00 kHz
[     3.671] (II) DUMMY(0): Configured Monitor: Using vrefresh range of 50.00-76.00 Hz
[     3.671] (II) DUMMY(0): Clock range:  11.00 to 300.00 MHz
[     3.671] (II) DUMMY(0): Not using default mode "640x350" (vrefresh out of range)
[     3.671] (II) DUMMY(0): Not using default mode "320x175" (vrefresh out of range)
[     3.671] (II) DUMMY(0): Not using default mode "640x400" (vrefresh out of range)
[     3.671] (II) DUMMY(0): Not using default mode "320x200" (vrefresh out of range)
[     3.671] (II) DUMMY(0): Not using default mode "720x400" (vrefresh out of range)
[     3.671] (II) DUMMY(0): Not using default mode "360x200" (vrefresh out of range)
[     3.671] (II) DUMMY(0): Not using default mode "640x480" (vrefresh out of range)
[     3.671] (II) DUMMY(0): Not using default mode "320x240" (vrefresh out of range)
[     3.671] (II) DUMMY(0): Not using default mode "800x600" (vrefresh out of range)
[     3.671] (II) DUMMY(0): Not using default mode "400x300" (vrefresh out of range)
[     3.671] (II) DUMMY(0): Not using default mode "1024x768i" (vrefresh out of range)
[     3.671] (II) DUMMY(0): Not using default mode "512x384i" (vrefresh out of range)
[     3.671] (II) DUMMY(0): Not using default mode "1024x768" (vrefresh out of range)
[     3.671] (II) DUMMY(0): Not using default mode "512x384" (vrefresh out of range)
[     3.671] (II) DUMMY(0): Not using default mode "1280x960" (insufficient memory for mode)
[     3.671] (II) DUMMY(0): Not using default mode "1280x960" (insufficient memory for mode)
[     3.671] (II) DUMMY(0): Not using default mode "640x480" (hsync out of range)
[     3.671] (II) DUMMY(0): Not using default mode "1280x1024" (insufficient memory for mode)
[     3.671] (II) DUMMY(0): Not using default mode "1280x1024" (insufficient memory for mode)
[     3.671] (II) DUMMY(0): Not using default mode "1280x1024" (insufficient memory for mode)
[     3.671] (II) DUMMY(0): Not using default mode "640x512" (hsync out of range)
[     3.671] (II) DUMMY(0): Not using default mode "1600x1200" (insufficient memory for mode)
[     3.671] (II) DUMMY(0): Not using default mode "1600x1200" (insufficient memory for mode)
[     3.671] (II) DUMMY(0): Not using default mode "1600x1200" (insufficient memory for mode)
[     3.671] (II) DUMMY(0): Not using default mode "800x600" (hsync out of range)
[     3.671] (II) DUMMY(0): Not using default mode "1600x1200" (insufficient memory for mode)
[     3.671] (II) DUMMY(0): Not using default mode "800x600" (hsync out of range)
[     3.671] (II) DUMMY(0): Not using default mode "1600x1200" (insufficient memory for mode)
[     3.671] (II) DUMMY(0): Not using default mode "800x600" (hsync out of range)
[     3.671] (II) DUMMY(0): Not using default mode "1792x1344" (insufficient memory for mode)
[     3.671] (II) DUMMY(0): Not using default mode "1792x1344" (insufficient memory for mode)
[     3.671] (II) DUMMY(0): Not using default mode "896x672" (hsync out of range)
[     3.671] (II) DUMMY(0): Not using default mode "1856x1392" (insufficient memory for mode)
[     3.671] (II) DUMMY(0): Not using default mode "928x696" (hsync out of range)
[     3.671] (II) DUMMY(0): Not using default mode "1856x1392" (insufficient memory for mode)
[     3.671] (II) DUMMY(0): Not using default mode "928x696" (hsync out of range)
[     3.671] (II) DUMMY(0): Not using default mode "1920x1440" (insufficient memory for mode)
[     3.671] (II) DUMMY(0): Not using default mode "960x720" (hsync out of range)
[     3.671] (II) DUMMY(0): Not using default mode "1920x1440" (insufficient memory for mode)
[     3.671] (II) DUMMY(0): Not using default mode "960x720" (hsync out of range)
[     3.671] (II) DUMMY(0): Not using default mode "1152x864" (vrefresh out of range)
[     3.671] (II) DUMMY(0): Not using default mode "576x432" (vrefresh out of range)
[     3.671] (II) DUMMY(0): Not using default mode "1152x864" (vrefresh out of range)
[     3.671] (II) DUMMY(0): Not using default mode "576x432" (vrefresh out of range)
[     3.671] (II) DUMMY(0): Not using default mode "1152x864" (hsync out of range)
[     3.671] (II) DUMMY(0): Not using default mode "576x432" (hsync out of range)
[     3.671] (II) DUMMY(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[     3.671] (II) DUMMY(0): Not using default mode "1400x1050" (insufficient memory for mode)
[     3.671] (II) DUMMY(0): Not using default mode "1400x1050" (insufficient memory for mode)
[     3.671] (II) DUMMY(0): Not using default mode "1400x1050" (insufficient memory for mode)
[     3.671] (II) DUMMY(0): Not using default mode "1400x1050" (insufficient memory for mode)
[     3.671] (II) DUMMY(0): Not using default mode "700x525" (hsync out of range)
[     3.671] (II) DUMMY(0): Not using default mode "1440x900" (insufficient memory for mode)
[     3.671] (II) DUMMY(0): Not using default mode "1600x1024" (insufficient memory for mode)
[     3.671] (II) DUMMY(0): Not using default mode "1680x1050" (insufficient memory for mode)
[     3.671] (II) DUMMY(0): Not using default mode "1680x1050" (insufficient memory for mode)
[     3.671] (II) DUMMY(0): Not using default mode "1680x1050" (insufficient memory for mode)
[     3.671] (II) DUMMY(0): Not using default mode "1680x1050" (insufficient memory for mode)
[     3.671] (II) DUMMY(0): Not using default mode "1680x1050" (insufficient memory for mode)
[     3.671] (II) DUMMY(0): Not using default mode "840x525" (hsync out of range)
[     3.671] (II) DUMMY(0): Not using default mode "1920x1080" (insufficient memory for mode)
[     3.671] (II) DUMMY(0): Not using default mode "1920x1200" (insufficient memory for mode)
[     3.671] (II) DUMMY(0): Not using default mode "1920x1440" (insufficient memory for mode)
[     3.671] (II) DUMMY(0): Not using default mode "960x720" (hsync out of range)
[     3.671] (II) DUMMY(0): Not using default mode "2048x1536" (insufficient memory for mode)
[     3.671] (II) DUMMY(0): Not using default mode "1024x768" (hsync out of range)
[     3.671] (II) DUMMY(0): Not using default mode "2048x1536" (insufficient memory for mode)
[     3.671] (II) DUMMY(0): Not using default mode "1024x768" (hsync out of range)
[     3.671] (II) DUMMY(0): Not using default mode "2048x1536" (insufficient memory for mode)
[     3.671] (II) DUMMY(0): Not using default mode "1024x768" (hsync out of range)
[     3.671] (II) DUMMY(0): Not using mode "1024x800" (no mode of this name)
[     3.671] (II) DUMMY(0): Not using default mode "1152x864" (height too large for virtual size)
[     3.671] (II) DUMMY(0): Not using default mode "1152x864" (height too large for virtual size)
[     3.671] (II) DUMMY(0): Not using default mode "1152x864" (height too large for virtual size)
[     3.671] (II) DUMMY(0): Not using default mode "1152x864" (height too large for virtual size)
[     3.671] (--) DUMMY(0): Virtual size is 1360x768 (pitch 1360)
[     3.671] (**) DUMMY(0):  Default mode "1360x768": 84.8 MHz, 47.7 kHz, 59.8 Hz
[     3.671] (II) DUMMY(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[     3.671] (**) DUMMY(0):  Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
[     3.671] (II) DUMMY(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[     3.671] (**) DUMMY(0):  Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
[     3.671] (II) DUMMY(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[     3.671] (**) DUMMY(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
[     3.671] (II) DUMMY(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[     3.671] (**) DUMMY(0):  Default mode "896x672": 102.4 MHz, 83.7 kHz, 60.0 Hz (D)
[     3.671] (II) DUMMY(0): Modeline "896x672"x60.0  102.40  896 960 1060 1224  672 672 674 697 doublescan -hsync +vsync (83.7 kHz)
[     3.671] (**) DUMMY(0):  Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
[     3.671] (II) DUMMY(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[     3.671] (**) DUMMY(0):  Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
[     3.671] (II) DUMMY(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[     3.671] (**) DUMMY(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
[     3.671] (II) DUMMY(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[     3.671] (**) DUMMY(0):  Default mode "800x600": 87.8 MHz, 81.2 kHz, 65.0 Hz (D)
[     3.672] (II) DUMMY(0): Modeline "800x600"x65.0   87.75  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (81.2 kHz)
[     3.672] (**) DUMMY(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
[     3.672] (II) DUMMY(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[     3.672] (**) DUMMY(0):  Default mode "800x600": 81.0 MHz, 75.0 kHz, 60.0 Hz (D)
[     3.672] (II) DUMMY(0): Modeline "800x600"x60.0   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (75.0 kHz)
[     3.672] (**) DUMMY(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
[     3.672] (II) DUMMY(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[     3.672] (**) DUMMY(0):  Default mode "840x525": 93.5 MHz, 82.3 kHz, 75.0 Hz (D)
[     3.672] (II) DUMMY(0): Modeline "840x525"x75.0   93.50  840 900 988 1136  525 526 529 549 doublescan -hsync +vsync (82.3 kHz)
[     3.672] (**) DUMMY(0):  Default mode "840x525": 87.0 MHz, 76.6 kHz, 69.9 Hz (D)
[     3.672] (II) DUMMY(0): Modeline "840x525"x69.9   87.00  840 900 988 1136  525 526 529 548 doublescan -hsync +vsync (76.6 kHz)
[     3.672] (**) DUMMY(0):  Default mode "840x525": 73.1 MHz, 65.3 kHz, 60.0 Hz (D)
[     3.672] (II) DUMMY(0): Modeline "840x525"x60.0   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync (65.3 kHz)
[     3.672] (**) DUMMY(0):  Default mode "700x525": 77.9 MHz, 81.5 kHz, 74.8 Hz (D)
[     3.672] (II) DUMMY(0): Modeline "700x525"x74.8   77.90  700 732 892 956  525 526 532 545 doublescan +hsync +vsync (81.5 kHz)
[     3.672] (**) DUMMY(0):  Default mode "700x525": 72.5 MHz, 76.5 kHz, 70.1 Hz (D)
[     3.672] (II) DUMMY(0): Modeline "700x525"x70.1   72.53  700 748 824 948  525 525 527 546 doublescan -hsync +vsync (76.5 kHz)
[     3.672] (**) DUMMY(0):  Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
[     3.672] (II) DUMMY(0): Modeline "700x525"x60.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz)
[     3.672] (**) DUMMY(0):  Default mode "640x512": 67.5 MHz, 80.0 kHz, 75.0 Hz (D)
[     3.672] (II) DUMMY(0): Modeline "640x512"x75.0   67.50  640 648 720 844  512 512 514 533 doublescan +hsync +vsync (80.0 kHz)
[     3.672] (**) DUMMY(0):  Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
[     3.672] (II) DUMMY(0): Modeline "640x512"x60.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz)
[     3.672] (**) DUMMY(0):  Default mode "720x450": 53.2 MHz, 55.9 kHz, 59.9 Hz (D)
[     3.672] (II) DUMMY(0): Modeline "720x450"x59.9   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz)
[     3.672] (**) DUMMY(0):  Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
[     3.672] (II) DUMMY(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[     3.672] (**) DUMMY(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
[     3.672] (II) DUMMY(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[     3.672] (**) DUMMY(0):  Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
[     3.672] (II) DUMMY(0): Modeline "640x480"x60.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz)
[     3.672] (**) DUMMY(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
[     3.672] (II) DUMMY(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[     3.672] (**) DUMMY(0):  Default mode "680x384": 36.0 MHz, 47.4 kHz, 60.0 Hz (D)
[     3.672] (II) DUMMY(0): Modeline "680x384"x60.0   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz)
[     3.672] (**) DUMMY(0):  Default mode "680x384": 42.4 MHz, 47.7 kHz, 59.8 Hz (D)
[     3.672] (II) DUMMY(0): Modeline "680x384"x59.8   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz)
[     3.672] (**) DUMMY(0):  Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
[     3.672] (II) DUMMY(0): Modeline "576x432"x75.0   54.00  576 608 672 800  432 432 434 450 doublescan +hsync +vsync (67.5 kHz)
[     3.672] (**) DUMMY(0):  Default mode "576x432": 52.5 MHz, 67.6 kHz, 75.0 Hz (D)
[     3.672] (II) DUMMY(0): Modeline "576x432"x75.0   52.49  576 612 676 776  432 432 434 451 doublescan -hsync +vsync (67.6 kHz)
[     3.672] (**) DUMMY(0):  Default mode "576x432": 48.4 MHz, 63.0 kHz, 70.0 Hz (D)
[     3.672] (II) DUMMY(0): Modeline "576x432"x70.0   48.38  576 612 672 768  432 432 434 450 doublescan -hsync +vsync (63.0 kHz)
[     3.672] (**) DUMMY(0):  Default mode "576x432": 40.8 MHz, 53.7 kHz, 60.1 Hz (D)
[     3.672] (II) DUMMY(0): Modeline "576x432"x60.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz)
[     3.672] (**) DUMMY(0):  Default mode "512x384": 39.4 MHz, 60.0 kHz, 75.0 Hz (D)
[     3.672] (II) DUMMY(0): Modeline "512x384"x75.0   39.38  512 520 568 656  384 384 386 400 doublescan +hsync +vsync (60.0 kHz)
[     3.672] (**) DUMMY(0):  Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
[     3.672] (II) DUMMY(0): Modeline "512x384"x70.1   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync (56.5 kHz)
[     3.672] (**) DUMMY(0):  Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
[     3.672] (II) DUMMY(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz)
[     3.672] (**) DUMMY(0):  Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
[     3.672] (II) DUMMY(0): Modeline "416x312"x74.7   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync (49.7 kHz)
[     3.672] (**) DUMMY(0):  Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
[     3.672] (II) DUMMY(0): Modeline "400x300"x75.1   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync (46.9 kHz)
[     3.672] (**) DUMMY(0):  Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
[     3.672] (II) DUMMY(0): Modeline "400x300"x72.2   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync (48.1 kHz)
[     3.672] (**) DUMMY(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
[     3.672] (II) DUMMY(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
[     3.672] (**) DUMMY(0):  Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
[     3.672] (II) DUMMY(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
[     3.672] (**) DUMMY(0):  Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
[     3.672] (II) DUMMY(0): Modeline "320x240"x75.0   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync (37.5 kHz)
[     3.672] (**) DUMMY(0):  Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
[     3.672] (II) DUMMY(0): Modeline "320x240"x72.8   15.75  320 332 352 416  240 244 246 260 doublescan -hsync -vsync (37.9 kHz)
[     3.672] (**) DUMMY(0):  Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
[     3.672] (II) DUMMY(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
[     3.672] (==) DUMMY(0): DPI set to (96, 96)
[     3.672] (II) Loading sub module "fb"
[     3.672] (II) LoadModule: "fb"
[     3.672] (II) Loading /usr/lib/xorg/modules/libfb.so
[     3.672] (II) Module fb: vendor="X.Org Foundation"
[     3.672]     compiled for 1.11.3, module version = 1.0.0
[     3.672]     ABI class: X.Org ANSI C Emulation, version 0.4
[     3.672] (II) Loading sub module "ramdac"
[     3.672] (II) LoadModule: "ramdac"
[     3.672] (II) Module "ramdac" already built-in
[     3.672] (--) Depth 24 pixmap format is 32 bpp
[     3.672] (II) DUMMY(0): Using 3 scanlines of offscreen memory 
[     3.672] (==) DUMMY(0): Backing store disabled
[     3.672] (==) DUMMY(0): Silken mouse enabled
[     3.673] (==) RandR enabled
[     3.673] (II) Initializing built-in extension Generic Event Extension
[     3.673] (II) Initializing built-in extension SHAPE
[     3.673] (II) Initializing built-in extension MIT-SHM
[     3.673] (II) Initializing built-in extension XInputExtension
[     3.673] (II) Initializing built-in extension XTEST
[     3.673] (II) Initializing built-in extension BIG-REQUESTS
[     3.673] (II) Initializing built-in extension SYNC
[     3.673] (II) Initializing built-in extension XKEYBOARD
[     3.673] (II) Initializing built-in extension XC-MISC
[     3.673] (II) Initializing built-in extension SECURITY
[     3.673] (II) Initializing built-in extension XINERAMA
[     3.673] (II) Initializing built-in extension XFIXES
[     3.673] (II) Initializing built-in extension RENDER
[     3.673] (II) Initializing built-in extension RANDR
[     3.673] (II) Initializing built-in extension COMPOSITE
[     3.673] (II) Initializing built-in extension DAMAGE
[     3.678] (II) AIGLX: Screen 0 is not DRI2 capable
[     3.678] (II) AIGLX: Screen 0 is not DRI capable
[     3.724] (II) AIGLX: Loaded and initialized swrast
[     3.724] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[     3.732] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     3.734] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     3.734] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     3.734] (II) LoadModule: "evdev"
[     3.734] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     3.734] (II) Module evdev: vendor="X.Org Foundation"
[     3.734]     compiled for 1.11.3, module version = 2.7.0
[     3.734]     Module class: X.Org XInput Driver
[     3.734]     ABI class: X.Org XInput driver, version 16.0
[     3.734] (II) Using input driver 'evdev' for 'Power Button'
[     3.734] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     3.734] (**) Power Button: always reports core events
[     3.734] (**) evdev: Power Button: Device: "/dev/input/event1"
[     3.734] (--) evdev: Power Button: Vendor 0 Product 0x1
[     3.734] (--) evdev: Power Button: Found keys
[     3.734] (II) evdev: Power Button: Configuring as keyboard
[     3.734] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     3.734] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     3.734] (**) Option "xkb_rules" "evdev"
[     3.734] (**) Option "xkb_model" "pc105"
[     3.734] (**) Option "xkb_layout" "us"
[     3.735] (II) config/udev: Adding input device Video Bus (/dev/input/event3)
[     3.735] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[     3.735] (II) Using input driver 'evdev' for 'Video Bus'
[     3.735] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     3.735] (**) Video Bus: always reports core events
[     3.735] (**) evdev: Video Bus: Device: "/dev/input/event3"
[     3.735] (--) evdev: Video Bus: Vendor 0 Product 0x6
[     3.735] (--) evdev: Video Bus: Found keys
[     3.735] (II) evdev: Video Bus: Configuring as keyboard
[     3.735] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input3/event3"
[     3.735] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[     3.735] (**) Option "xkb_rules" "evdev"
[     3.735] (**) Option "xkb_model" "pc105"
[     3.735] (**) Option "xkb_layout" "us"
[     3.735] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     3.735] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     3.735] (II) Using input driver 'evdev' for 'Power Button'
[     3.735] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     3.735] (**) Power Button: always reports core events
[     3.735] (**) evdev: Power Button: Device: "/dev/input/event0"
[     3.735] (--) evdev: Power Button: Vendor 0 Product 0x1
[     3.735] (--) evdev: Power Button: Found keys
[     3.735] (II) evdev: Power Button: Configuring as keyboard
[     3.735] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[     3.735] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[     3.735] (**) Option "xkb_rules" "evdev"
[     3.735] (**) Option "xkb_model" "pc105"
[     3.735] (**) Option "xkb_layout" "us"
[     3.736] (II) config/udev: Adding input device PC Speaker (/dev/input/event2)
[     3.736] (II) No input driver specified, ignoring this device.
[     3.736] (II) This device may have been added with another device file.
[     3.958] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=8 (/dev/input/event4)
[     3.958] (II) No input driver specified, ignoring this device.
[     3.958] (II) This device may have been added with another device file.
[     3.962] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=7 (/dev/input/event5)
[     3.962] (II) No input driver specified, ignoring this device.
[     3.962] (II) This device may have been added with another device file.
[     3.965] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event6)
[     3.965] (II) No input driver specified, ignoring this device.
[     3.965] (II) This device may have been added with another device file.
[     5.098] (II) config/udev: Adding input device HD Pro Webcam C920 (/dev/input/event7)
[     5.098] (**) HD Pro Webcam C920: Applying InputClass "evdev keyboard catchall"
[     5.098] (II) Using input driver 'evdev' for 'HD Pro Webcam C920'
[     5.098] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     5.098] (**) HD Pro Webcam C920: always reports core events
[     5.098] (**) evdev: HD Pro Webcam C920: Device: "/dev/input/event7"
[     5.098] (--) evdev: HD Pro Webcam C920: Vendor 0x46d Product 0x82d
[     5.098] (--) evdev: HD Pro Webcam C920: Found keys
[     5.098] (II) evdev: HD Pro Webcam C920: Configuring as keyboard
[     5.098] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5.2/2-1.5.2:1.0/input/input7/event7"
[     5.098] (II) XINPUT: Adding extended input device "HD Pro Webcam C920" (type: KEYBOARD, id 9)
[     5.098] (**) Option "xkb_rules" "evdev"
[     5.098] (**) Option "xkb_model" "pc105"
[     5.098] (**) Option "xkb_layout" "us"
[     5.566] (II) config/udev: Adding input device SINO WEALTH USB Composite Device (/dev/input/mouse0)
[     5.566] (II) No input driver specified, ignoring this device.
[     5.566] (II) This device may have been added with another device file.
[     5.566] (II) config/udev: Adding input device SINO WEALTH USB Composite Device (/dev/input/event9)
[     5.566] (**) SINO WEALTH USB Composite Device: Applying InputClass "evdev pointer catchall"
[     5.566] (**) SINO WEALTH USB Composite Device: Applying InputClass "evdev keyboard catchall"
[     5.566] (II) Using input driver 'evdev' for 'SINO WEALTH USB Composite Device'
[     5.567] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     5.567] (**) SINO WEALTH USB Composite Device: always reports core events
[     5.567] (**) evdev: SINO WEALTH USB Composite Device: Device: "/dev/input/event9"
[     5.567] (--) evdev: SINO WEALTH USB Composite Device: Vendor 0x603 Product 0x2
[     5.567] (--) evdev: SINO WEALTH USB Composite Device: Found 9 mouse buttons
[     5.567] (--) evdev: SINO WEALTH USB Composite Device: Found scroll wheel(s)
[     5.567] (--) evdev: SINO WEALTH USB Composite Device: Found relative axes
[     5.567] (--) evdev: SINO WEALTH USB Composite Device: Found x and y relative axes
[     5.567] (--) evdev: SINO WEALTH USB Composite Device: Found absolute axes
[     5.567] (II) evdev: SINO WEALTH USB Composite Device: Forcing absolute x/y axes to exist.
[     5.567] (--) evdev: SINO WEALTH USB Composite Device: Found keys
[     5.567] (II) evdev: SINO WEALTH USB Composite Device: Configuring as mouse
[     5.567] (II) evdev: SINO WEALTH USB Composite Device: Configuring as keyboard
[     5.567] (II) evdev: SINO WEALTH USB Composite Device: Adding scrollwheel support
[     5.567] (**) evdev: SINO WEALTH USB Composite Device: YAxisMapping: buttons 4 and 5
[     5.567] (**) evdev: SINO WEALTH USB Composite Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     5.567] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6.3/2-1.6.3:1.1/input/input9/event9"
[     5.567] (II) XINPUT: Adding extended input device "SINO WEALTH USB Composite Device" (type: KEYBOARD, id 10)
[     5.567] (**) Option "xkb_rules" "evdev"
[     5.567] (**) Option "xkb_model" "pc105"
[     5.567] (**) Option "xkb_layout" "us"
[     5.567] (II) evdev: SINO WEALTH USB Composite Device: initialized for relative axes.
[     5.567] (WW) evdev: SINO WEALTH USB Composite Device: ignoring absolute axes.
[     5.567] (**) SINO WEALTH USB Composite Device: (accel) keeping acceleration scheme 1
[     5.567] (**) SINO WEALTH USB Composite Device: (accel) acceleration profile 0
[     5.567] (**) SINO WEALTH USB Composite Device: (accel) acceleration factor: 2.000
[     5.567] (**) SINO WEALTH USB Composite Device: (accel) acceleration threshold: 4
[     5.735] (II) config/udev: Adding input device SINO WEALTH USB Composite Device (/dev/input/event8)
[     5.735] (**) SINO WEALTH USB Composite Device: Applying InputClass "evdev keyboard catchall"
[     5.735] (II) Using input driver 'evdev' for 'SINO WEALTH USB Composite Device'
[     5.735] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     5.736] (**) SINO WEALTH USB Composite Device: always reports core events
[     5.736] (**) evdev: SINO WEALTH USB Composite Device: Device: "/dev/input/event8"
[     5.736] (--) evdev: SINO WEALTH USB Composite Device: Vendor 0x603 Product 0x2
[     5.736] (--) evdev: SINO WEALTH USB Composite Device: Found keys
[     5.736] (II) evdev: SINO WEALTH USB Composite Device: Configuring as keyboard
[     5.736] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6.3/2-1.6.3:1.0/input/input8/event8"
[     5.736] (II) XINPUT: Adding extended input device "SINO WEALTH USB Composite Device" (type: KEYBOARD, id 11)
[     5.736] (**) Option "xkb_rules" "evdev"
[     5.736] (**) Option "xkb_model" "pc105"
[     5.736] (**) Option "xkb_layout" "us"
[    36.923] (II) XKB: reuse xkmfile /var/lib/xkb/server-06D88AAF5356C6CF875D73CED515513D3FEA00ED.xkm
[   428.014] (II) XKB: reuse xkmfile /var/lib/xkb/server-06D88AAF5356C6CF875D73CED515513D3FEA00ED.xkm
```
When I change:
```
Modes "1024x800"
``` to ```
Modes "1024x768"
```
The system starts up in 1024x768, and I have the following resolutions to choose from: 1024x768(4:3), 896x672(4:3), 832x624(4:3), and 800x600(4:3).  

Also, I'm not sure if it's relevant, but I get the following error message:
```
Could not apply the stored configuration for monitorsnone of the selected modes were compatible with the possible modes:
Trying modes for CRTC 310
CRTC 310: trying mode 1024x768@75Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 1024x768@70Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 1024x768@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 896x672@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 832x624@75Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 800x600@75Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 800x600@72Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 800x600@65Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 800x600@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 800x600@56Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 840x525@75Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 840x525@70Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 840x525@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 700x525@75Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 700x525@70Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 700x525@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 640x512@75Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 640x512@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 720x450@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 640x480@75Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 640x480@73Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 640x480@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 680x384@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 576x432@75Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 576x432@70Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 576x432@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 512x384@75Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 512x384@70Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 512x384@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 416x312@75Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 400x300@75Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 400x300@72Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 400x300@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 400x300@56Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 320x240@75Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 320x240@73Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 320x240@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 1024x768@75Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 1024x768@70Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 1024x768@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 896x672@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 832x624@75Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 800x600@75Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 800x600@72Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 800x600@65Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 800x600@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 800x600@56Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 840x525@75Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 840x525@70Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 840x525@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 700x525@75Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 700x525@70Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 700x525@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 640x512@75Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 640x512@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 720x450@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 640x480@75Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 640x480@73Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 640x480@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 680x384@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 576x432@75Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 576x432@70Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 576x432@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 512x384@75Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 512x384@70Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 512x384@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 416x312@75Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 400x300@75Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 400x300@72Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 400x300@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 400x300@56Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 320x240@75Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 320x240@73Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 320x240@60Hz with output at 1360x768@60Hz (pass 1)
```
If I try: ```
Modes "1280x800"
```
The system starts up in 1360x768(16:9) again, and I have the same choices for resolution as I did when Modes was set to "1024x800".  I didn't include this log file, but I have it if necessary.  I did, however, see  in the log file that there is no default modeline for 1280x800.

If I try: ```
Modes "1920x1080"
```
I get the 1360x768 resolution again.  BUT, I saw in the log file that there is not enough VideoRam to support 1920x1080.  The default VideoRam is 4096Kbytes and I read that you need 4bytes of VideoRam per pixel.  1920x1080x4=8294Kbytes. So I changed VideoRam to 10000Kbytes.

I went back to /etc/X11/xorg.conf and left Modes "1920x1080" unchanged, but changed the Device section to:
```
Section "Device"    Identifier  "Configured Video Device"
    Driver      "dummy"
    VideoRam 10000
EndSection
```
It still started up at 1360x768 resolution, but I had more choices than before.  I had all the previous ones with the addition of: 1152x864(4:3), 1280x960(4:3), 1280x1024(5:4), 1400x1050(4:3), 1440x900(16:10), 1600x1200(4:3), 1680x1050(16:10), and 1792x1344(4:3).  

I have the log file for this as well.

I'll note that I also tried increasing VideoRam to 256000, but got the same results as VideoRam 10000.

So, it looks to me like I need to add a custom modeline for a resolution of 1280x800.  This is where I am currently stuck.

This is what I tried (/etc/X11/xorg.conf):
```
Section "Device"    Identifier  "Configured Video Device"
    Driver      "dummy"
    VideoRam 256000
EndSection


Section "Monitor"
    Identifier  "Configured Monitor"
    HorizSync 5.0 - 1000.0
    VertRefresh 5.0 - 200.0
    Modeline "1280x800" 24.15 1280 1312 1400 1432 800 819 822 841
EndSection


Section "Screen"
    Identifier  "Default Screen"
    Monitor     "Configured Monitor"
    Device      "Configured Video Device"
    DefaultDepth 24
    SubSection "Display"
    Depth 24
    Modes "1920x1080" "1280x800"
    EndSubSection
EndSection
```
...and it works!!! OKAY, so I guess I'm not stuck! 

So, in writing up this post, I kind of solved my own problem.  With the above change, I booted up in 1280x800 resolution.  But it's not a perfect solution because I get an error message every time I startup my system...

I got a startup error message similar to the one I got when I tried to start with a resolution of 1024x768.  Here it is:
```
Could not apply the stored configuration for monitorsnone of the selected modes were compatible with the possible modes:
Trying modes for CRTC 310
CRTC 310: trying mode 1024x768@75Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 1024x768@70Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 1024x768@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 896x672@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 832x624@75Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 800x600@75Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 800x600@72Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 800x600@65Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 800x600@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 800x600@56Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 840x525@75Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 840x525@70Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 840x525@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 700x525@75Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 700x525@70Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 700x525@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 640x512@75Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 640x512@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 720x450@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 640x480@75Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 640x480@73Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 640x480@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 680x384@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 576x432@75Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 576x432@70Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 576x432@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 512x384@75Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 512x384@70Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 512x384@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 416x312@75Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 400x300@75Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 400x300@72Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 400x300@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 400x300@56Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 320x240@75Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 320x240@73Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 320x240@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 310: trying mode 1024x768@75Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 1024x768@70Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 1024x768@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 896x672@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 832x624@75Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 800x600@75Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 800x600@72Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 800x600@65Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 800x600@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 800x600@56Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 840x525@75Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 840x525@70Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 840x525@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 700x525@75Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 700x525@70Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 700x525@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 640x512@75Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 640x512@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 720x450@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 640x480@75Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 640x480@73Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 640x480@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 680x384@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 576x432@75Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 576x432@70Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 576x432@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 512x384@75Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 512x384@70Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 512x384@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 416x312@75Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 400x300@75Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 400x300@72Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 400x300@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 400x300@56Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 320x240@75Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 320x240@73Hz with output at 1360x768@60Hz (pass 1)
CRTC 310: trying mode 320x240@60Hz with output at 1360x768@60Hz (pass 1)
```
Also, this is part of the log file from the working 1280x800 configuration:
```
[     3.689] (--) DUMMY(0): Virtual size is 1280x800 (pitch 1280)[     3.689] (**) DUMMY(0): *Mode "1280x800": 24.1 MHz, 16.9 kHz, 20.1 Hz
[     3.689] (II) DUMMY(0): Modeline "1280x800"x20.1   24.15  1280 1312 1400 1432  800 819 822 841 (16.9 kHz)
```
Questions:
[LIST]
[*]How do I get rid of this error message?
[*]Does this mean that I am running at a framerate of 20.1Hz?
[*]Is there a better way to do this?
[/LIST]

p.s. First time posting.  Sorry in advance for everything I did wrong. ;)

---

### Post by ben115 on 2014-10-08
Okay, the error message ended up going away so I'm going to change this to solved.

---

