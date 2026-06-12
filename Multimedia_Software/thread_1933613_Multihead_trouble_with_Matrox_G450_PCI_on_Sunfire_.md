---
title: "Multihead trouble with Matrox G450 PCI on Sunfire V40z"
date: 2012-02-29
forum: Multimedia Software
---

### Post by Mad Tux on 2012-02-29
I'd like to use this SunFire server for image processing, playing with Blender (runs fine with the G450 BTW) and all the other things where a normal PIII/P4/Athlon computer is too slow for. It's a really cool octacore machine with 32GB RAM, a bit noisy, but that doesn't matter so far as I have headphones with music. I'm using Ubuntu 10.04, as I had trouble with Gentoo detecting the Ultra-SCSI drives.

  Because the onboard Trident Microsystems Blade 3D graphic card doesn't allow high resolutions, I got 4 [Matrox G450 PCI]("http://www.3dfx.ch/gallery/v/3dfx_collectors/collectors_goldleader/matrox/G450PCI/Matrox+Millenium+G450+PCI+32MB+SGDDR+Rev_A+4904+top.JPG.html") graphic cards and plugged them into the PCI-X slots and they work fine on 3,3V bus. (my USB cards don't seem to like the 3,3V PCI-X bus BTW)

  The system works fine upon a resolution of 2048x1534 with one graphic card and a Iiyama Vision Master 514. But as I try to attach a second monitor to the second G450 on the PCI-X bus, the X11 server complains about insufficient memory (see the xorg.o.log file attached). This reduces the resolution of the second monitor to 832x624. Furthermore the system freezes as soon as I move the mouse pointer to the second screen on the left. Other than that, the second screen works fine. I use the xorg.conf in /etc/X11 to configure the X11 server.

The main monitor is the G450 on PCI(0:4:0:0)
[PCI Slot 2]("http://www.sunshack.org/data/sh/2.1.8/infoserver.central/data/syshbk/Systems/SunFireV40z/images/SunFireV40z_rear_zoom.jpg"), the second G450 is PCI(0:5:0:0) in Slot 3. I've tried some options like xinerama and the vesa driver instead of the MGA driver but this didn't help. 

The weird thing is that the DMA memory ranges of both graphic cards are separated, 0xe0000000 for the first G450 in PCI(0:4:0:0) and 0xe2000000 for the second G450 in PCI(0:5:0:0) and yet the xorg.0.log complains about insufficient memory.

  So far I don't know any further. Does anyone have some idea how I could get the second monitor working at a better resolution (1600x1200 prefered). Is there a way to determine the DMA memory ranges in Linux, so that I can see if there is some memory overlapping with some other devices? BTW how is system level debugging done in Linux (I only know the EDB user level debugger for Linux), I used to tamper with SoftICE on Win95 and even managed to patch (Jump-over) the mouse pointer movement routine in the Tident graphics driver on my Thinkpad 365XD, so that the mouse wouldn't react on inputs on the trackpointer and stay in the middle. But I've no idea how to debug the X11 server on Linux.


Preferably use Kate for viewing this code, as it highlights xorg.conf config code quite nicely 

 ```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
Current Operating System: Linux SunV40z 2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:12:07 UTC 2012 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-38-generic root=UUID=d4225efa-557d-4625-bfc1-e3762546c4c8 ro quiet splash
Build Date: 20 October 2011  03:03:02PM
xorg-server 2:1.7.6-2ubuntu7.10 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jan 15 01:31:04 2003
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen1-0" (0)
(**) |   |-->Monitor "Vision Master 514_1-0"
(**) |   |-->Device "Card1-0"
(**) |-->Screen "Screen2-0" (1)
(**) |   |-->Monitor "Vision Master 514_2-0"
(**) |   |-->Device "Card2-0"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Keyboard0"
(**) Option "Xinerama" "on"
(==) Automatically adding devices
(==) Automatically enabling devices
(**) Xinerama: enabled
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
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Mouse0
(WW) Disabling Keyboard0
(II) Loader magic: 0x7cb840
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI: (0:1:5:0) 1023:9880:ffff:ffff Trident Microsystems Blade 3D PCI/AGP rev 58, Mem @ 0xdd000000/8388608, 0xdc120000/131072, 0xdc800000/8388608, BIOS @ 0x????????/65536
(--) PCI:*(0:4:0:0) 102b:0525:1014:0233 Matrox Graphics, Inc. MGA G400/G450 rev 133, Mem @ 0xe0000000/33554432, 0xdd900000/16384, 0xde000000/8388608, BIOS @ 0x????????/131072
(--) PCI: (0:5:0:0) 102b:0525:1014:0233 Matrox Graphics, Inc. MGA G400/G450 rev 133, Mem @ 0xe2000000/33554432, 0xdf000000/16384, 0xde800000/8388608, BIOS @ 0x????????/131072
(--) PCI: (0:42:0:0) 102b:0525:1014:0233 Matrox Graphics, Inc. MGA G400/G450 rev 133, Mem @ 0xf4000000/33554432, 0xe6800000/16384, 0xe6000000/8388608, BIOS @ 0x????????/131072
(--) PCI: (0:47:0:0) 102b:0525:102b:0d43 Matrox Graphics, Inc. MGA G400/G450 rev 133, Mem @ 0xf8000000/33554432, 0xe7800000/16384, 0xe7000000/8388608, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
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
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "mga"
(II) Loading /usr/lib/xorg/modules/drivers/mga_drv.so
(II) Module mga: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.4.11
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) MGA: driver for Matrox chipsets: mga2064w, mga1064sg, mga2164w,
    mga2164w AGP, mgag100, mgag100 PCI, mgag200, mgag200 PCI,
    mgag200 SE A PCI, mgag200 SE B PCI, mgag200 EV Maxim,
    mgag200 eW Nuvoton, mgag200eH, mgag400, mgag550
(II) Primary Device is: PCI 04@00:00:0
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.1.0
    ABI class: X.Org Video Driver, version 6.0
(--) MGA(0): Chipset: "mgag400" (G450)
(--) MGA(0): Linear framebuffer at 0xE0000000
(--) MGA(0): MMIO registers at 0xDD900000
(--) MGA(0): Pseudo-DMA transfer window at 0xDE000000
(**) MGA(0): Depth 24, (--) framebuffer bpp 32
(==) MGA(0): RGB weight 888
(==) MGA(0): Using AGP 1x mode
(==) MGA(0): Using HW cursor
(==) MGA(0): Using XAA acceleration
(--) MGA(0): Video BIOS info block at offset 0x079C0
(==) MGA(0): VideoRAM: 32768 kByte
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) MGA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) MGA(0): I2C bus "DDC P1" initialized.
(II) MGA(0): I2C device "DDC P1:ddc2" registered at address 0xA0.
(--) MGA(0): No DDC signal
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Video Driver, version 6.0
(II) MGA(0): initializing int10
(II) MGA(0): Primary V_BIOS segment is: 0xc000
(II) MGA(0): VESA BIOS detected
(II) MGA(0): VESA VBE Version 3.0
(II) MGA(0): VESA VBE Total Mem: 32768 kB
(II) MGA(0): VESA VBE OEM: Matrox Graphics Inc.
(II) MGA(0): VESA VBE OEM Software Rev: 1.6
(II) MGA(0): VESA VBE OEM Vendor: Matrox
(II) MGA(0): VESA VBE OEM Product: Matrox G450
(II) MGA(0): VESA VBE OEM Product Rev: 00
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) MGA(0): VESA VBE DDC supported
(II) MGA(0): VESA VBE DDC Level 2
(II) MGA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) MGA(0): VESA VBE DDC read successfully
(II) MGA(0): VBE monitor info
(II) MGA(0): Manufacturer: IVM  Model: 216a  Serial#: 10011329
(II) MGA(0): Year: 2003  Week: 8
(II) MGA(0): EDID Version: 1.3
(II) MGA(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) MGA(0): Sync:  Separate  Composite  SyncOnGreenSerration on. V.Sync Pulse req. if CompSync or SyncOnGreen
(II) MGA(0): Max Image Size [cm]: horiz.: 45  vert.: 33
(II) MGA(0): Gamma: 2.20
(II) MGA(0): DPMS capabilities: Suspend Off; RGB/Color Display
(II) MGA(0): Default color space is primary color space
(II) MGA(0): First detailed timing is preferred mode
(II) MGA(0): GTF timings supported
(II) MGA(0): redX: 0.627 redY: 0.328   greenX: 0.292 greenY: 0.604
(II) MGA(0): blueX: 0.148 blueY: 0.071   whiteX: 0.305 whiteY: 0.310
(II) MGA(0): Supported established timings:
(II) MGA(0): 720x400@70Hz
(II) MGA(0): 640x480@60Hz
(II) MGA(0): 640x480@67Hz
(II) MGA(0): 640x480@72Hz
(II) MGA(0): 640x480@75Hz
(II) MGA(0): 800x600@56Hz
(II) MGA(0): 800x600@60Hz
(II) MGA(0): 800x600@72Hz
(II) MGA(0): 800x600@75Hz
(II) MGA(0): 832x624@75Hz
(II) MGA(0): 1024x768@60Hz
(II) MGA(0): 1024x768@70Hz
(II) MGA(0): 1024x768@75Hz
(II) MGA(0): 1280x1024@75Hz
(II) MGA(0): 1152x864@75Hz
(II) MGA(0): Manufacturer's mask: 0
(II) MGA(0): Supported standard timings:
(II) MGA(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) MGA(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) MGA(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) MGA(0): #3: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) MGA(0): #4: hsize: 1600  vsize 1200  refresh: 85  vid: 22953
(II) MGA(0): #5: hsize: 1920  vsize 1440  refresh: 85  vid: 22993
(II) MGA(0): #6: hsize: 2048  vsize 1536  refresh: 85  vid: 23009
(II) MGA(0): Supported detailed timing:
(II) MGA(0): clock: 157.5 MHz   Image Size:  395 x 295 mm
(II) MGA(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) MGA(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) MGA(0): Monitor name: HM204D DT
(II) MGA(0): Ranges: V min: 50 V max: 200 Hz, H min: 30 H max: 140 kHz, PixClock max 390 MHz
(II) MGA(0):  2nd GTF parameters: f: 100 kHz c: 50 m: 2800 k 128 j 30
(II) MGA(0): Supported detailed timing:
(II) MGA(0): clock: 388.0 MHz   Image Size:  395 x 295 mm
(II) MGA(0): h_active: 2048  h_sync: 2216  h_sync_end 2440 h_blank_end 2832 h_border: 0
(II) MGA(0): v_active: 1536  v_sync: 1537  v_sync_end 1540 v_blanking: 1612 v_border: 0
(II) MGA(0): EDID (in hex):
(II) MGA(0):     00ffffffffffff0026cd6a21c1c29800
(II) MGA(0):     080d01030f2d21786f8f11a0544a9a26
(II) MGA(0):     124e4fbfef803159455961598199a959
(II) MGA(0):     d159e1590101863d00c05100304040a0
(II) MGA(0):     13008b271100001e000000fc00484d32
(II) MGA(0):     3034442044540a202020000000fd0032
(II) MGA(0):     c81e8c2702003264f00a803c90970010
(II) MGA(0):     83004c60a8e013008b271100001e0094
(II) MGA(0): end of monitor info
(II) MGA(0): EDID vendor "IVM", prod id 8554
(II) MGA(0): Using hsync ranges from config file
(II) MGA(0): Using vrefresh ranges from config file
(II) MGA(0): Printing DDC gathered Modelines:
(II) MGA(0): Modeline "1280x1024"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) MGA(0): Modeline "2048x1536"x0.0  388.00  2048 2216 2440 2832  1536 1537 1540 1612 +hsync +vsync (137.0 kHz)
(II) MGA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) MGA(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) MGA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) MGA(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) MGA(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) MGA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) MGA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) MGA(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) MGA(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) MGA(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) MGA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) MGA(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) MGA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) MGA(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) MGA(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) MGA(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) MGA(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) MGA(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) MGA(0): Modeline "1600x1200"x0.0  229.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (106.2 kHz)
(II) MGA(0): Modeline "1920x1440"x85.0  341.35  1920 2072 2288 2656  1440 1441 1444 1512 -hsync +vsync (128.5 kHz)
(II) MGA(0): Modeline "2048x1536"x85.0  388.04  2048 2216 2440 2832  1536 1537 1540 1612 -hsync +vsync (137.0 kHz)
(==) MGA(0): Using gamma correction (1.0, 1.0, 1.0)
(==) MGA(0): Min pixel clock is 17 MHz
(--) MGA(0): Max pixel clock is 1200 MHz
(II) MGA(0): Vision Master 514_1-0: Using hsync range of 30.00-142.00 kHz
(II) MGA(0): Vision Master 514_1-0: Using vrefresh range of 50.00-200.00 Hz
(II) MGA(0): Vision Master 514_1-0: Using maximum pixel clock of 390.00 MHz
(II) MGA(0): Clock range:  17.75 to 1200.00 MHz
(II) MGA(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) MGA(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) MGA(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) MGA(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) MGA(0): Not using mode "1600x1400" (no mode of this name)
(--) MGA(0): Has SDRAM
(--) MGA(0): Virtual size is 1920x1440 (pitch 1920)
(**) MGA(0): *Driver mode "1920x1440": 341.3 MHz, 128.5 kHz, 85.0 Hz
(II) MGA(0): Modeline "1920x1440"x85.0  341.35  1920 2072 2288 2656  1440 1441 1444 1512 -hsync +vsync (128.5 kHz)
(**) MGA(0): *Driver mode "1280x1024": 157.5 MHz, 91.1 kHz, 85.0 Hz
(II) MGA(0): Modeline "1280x1024"x85.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(**) MGA(0): *Driver mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) MGA(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(**) MGA(0): Display dimensions: (406, 304) mm
(WW) MGA(0): Probed monitor is 450x330 mm, using Displaysize 406x304 mm
(**) MGA(0): DPI set to (120, 120)
(II) MGA(0): YDstOrg is set to 0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.2.1
    ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Reloading /usr/lib/xorg/modules/libvgahw.so
(--) MGA(1): Chipset: "mgag400" (G450)
(--) MGA(1): Linear framebuffer at 0xE2000000
(--) MGA(1): MMIO registers at 0xDF000000
(--) MGA(1): Pseudo-DMA transfer window at 0xDE800000
(**) MGA(1): Depth 24, (--) framebuffer bpp 32
(==) MGA(1): RGB weight 888
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) MGA(1): Initializing int10
(==) MGA(1): Using AGP 1x mode
(==) MGA(1): Using HW cursor
(==) MGA(1): Using XAA acceleration
(--) MGA(1): Video BIOS info block at offset 0x079C0
(==) MGA(1): VideoRAM: 2048 kByte
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) MGA(1): vgaHWGetIOBase: hwp->IOBase is 0x03b0, hwp->PIOOffset is 0x0000
(II) MGA(1): DDC1 disabled - chip not in VGA mode
(II) MGA(1): I2C bus "DDC P1" initialized.
(II) MGA(1): I2C device "DDC P1:ddc2" registered at address 0xA0.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules/libvbe.so
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) MGA(1): initializing int10
(II) MGA(1): VESA BIOS detected
(II) MGA(1): VESA VBE Version 3.0
(II) MGA(1): VESA VBE Total Mem: 32768 kB
(II) MGA(1): VESA VBE OEM: Matrox Graphics Inc.
(II) MGA(1): VESA VBE OEM Software Rev: 1.6
(II) MGA(1): VESA VBE OEM Vendor: Matrox
(II) MGA(1): VESA VBE OEM Product: Matrox G450
(II) MGA(1): VESA VBE OEM Product Rev: 00
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) MGA(1): VESA VBE DDC supported
(II) MGA(1): VESA VBE DDC Level none
(II) MGA(1): VESA VBE DDC transfer in appr. 0 sec.
(II) MGA(1): VESA VBE DDC read failed
(==) MGA(1): Using gamma correction (1.0, 1.0, 1.0)
(==) MGA(1): Min pixel clock is 17 MHz
(--) MGA(1): Max pixel clock is 1200 MHz
(II) MGA(1): Vision Master 514_2-0: Using hsync range of 30.00-142.00 kHz
(II) MGA(1): Vision Master 514_2-0: Using vrefresh range of 50.00-200.00 Hz
(II) MGA(1): Clock range:  17.75 to 1200.00 MHz
(II) MGA(1): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) MGA(1): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) MGA(1): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MGA(1): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MGA(1): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MGA(1): Not using default mode "1024x768" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1024x768" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1024x768" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1024x768" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1024x768" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1152x864" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1280x960" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1280x960" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1280x1024" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1280x1024" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1280x1024" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1600x1200" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1600x1200" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1600x1200" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1600x1200" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1600x1200" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1792x1344" (insufficient memory for mode)
(II) MGA(1): Not using default mode "896x672" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1792x1344" (insufficient memory for mode)
(II) MGA(1): Not using default mode "896x672" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1856x1392" (insufficient memory for mode)
(II) MGA(1): Not using default mode "928x696" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1856x1392" (insufficient memory for mode)
(II) MGA(1): Not using default mode "928x696" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MGA(1): Not using default mode "960x720" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MGA(1): Not using default mode "960x720" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1152x864" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1152x864" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1152x864" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1152x864" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1152x864" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1152x864" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1360x768" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1360x768" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1400x1050" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1400x1050" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1400x1050" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1400x1050" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1440x900" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1600x1024" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1680x1050" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1680x1050" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1680x1050" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1680x1050" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1680x1050" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1920x1080" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1920x1200" (insufficient memory for mode)
(II) MGA(1): Not using default mode "960x600" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MGA(1): Not using default mode "960x720" (insufficient memory for mode)
(II) MGA(1): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1024x768" (insufficient memory for mode)
(II) MGA(1): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1024x768" (insufficient memory for mode)
(II) MGA(1): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1024x768" (insufficient memory for mode)
(II) MGA(1): Not using mode "1920x1440" (no mode of this name)
(II) MGA(1): Not using mode "1600x1400" (no mode of this name)
(II) MGA(1): Not using mode "1280x1024" (no mode of this name)
(II) MGA(1): Not using mode "1024x768" (no mode of this name)
(II) MGA(1): Not using default mode "840x525" (width too large for virtual size)
(II) MGA(1): Not using default mode "840x525" (width too large for virtual size)
(II) MGA(1): Not using default mode "840x525" (width too large for virtual size)
(II) MGA(1): Not using default mode "840x525" (width too large for virtual size)
(II) MGA(1): Not using default mode "840x525" (width too large for virtual size)
(--) MGA(1): Has SDRAM
(--) MGA(1): Virtual size is 832x624 (pitch 832)
(**) MGA(1):  Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) MGA(1): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) MGA(1):  Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) MGA(1): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(**) MGA(1):  Default mode "800x600": 114.8 MHz, 106.2 kHz, 85.0 Hz (D)
(II) MGA(1): Modeline "800x600"x85.0  114.75  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (106.2 kHz)
(**) MGA(1):  Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) MGA(1): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) MGA(1):  Default mode "800x600": 101.2 MHz, 93.8 kHz, 75.0 Hz (D)
(II) MGA(1): Modeline "800x600"x75.0  101.25  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (93.8 kHz)
(**) MGA(1):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) MGA(1): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) MGA(1):  Default mode "800x600": 94.5 MHz, 87.5 kHz, 70.0 Hz (D)
(II) MGA(1): Modeline "800x600"x70.0   94.50  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (87.5 kHz)
(**) MGA(1):  Default mode "800x600": 87.8 MHz, 81.2 kHz, 65.0 Hz (D)
(II) MGA(1): Modeline "800x600"x65.0   87.75  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (81.2 kHz)
(**) MGA(1):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) MGA(1): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) MGA(1):  Default mode "800x600": 81.0 MHz, 75.0 kHz, 60.0 Hz (D)
(II) MGA(1): Modeline "800x600"x60.0   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (75.0 kHz)
(**) MGA(1):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) MGA(1): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) MGA(1):  Default mode "700x525": 89.6 MHz, 93.8 kHz, 85.1 Hz (D)
(II) MGA(1): Modeline "700x525"x85.1   89.63  700 752 828 956  525 525 527 551 doublescan -hsync +vsync (93.8 kHz)
(**) MGA(1):  Default mode "700x525": 77.9 MHz, 81.5 kHz, 74.8 Hz (D)
(II) MGA(1): Modeline "700x525"x74.8   77.90  700 732 892 956  525 526 532 545 doublescan +hsync +vsync (81.5 kHz)
(**) MGA(1):  Default mode "700x525": 72.5 MHz, 76.5 kHz, 70.1 Hz (D)
(II) MGA(1): Modeline "700x525"x70.1   72.53  700 748 824 948  525 525 527 546 doublescan -hsync +vsync (76.5 kHz)
(**) MGA(1):  Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(II) MGA(1): Modeline "700x525"x60.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz)
(**) MGA(1):  Default mode "640x512": 78.8 MHz, 91.1 kHz, 85.0 Hz (D)
(II) MGA(1): Modeline "640x512"x85.0   78.75  640 672 752 864  512 512 514 536 doublescan +hsync +vsync (91.1 kHz)
(**) MGA(1):  Default mode "640x512": 67.5 MHz, 80.0 kHz, 75.0 Hz (D)
(II) MGA(1): Modeline "640x512"x75.0   67.50  640 648 720 844  512 512 514 533 doublescan +hsync +vsync (80.0 kHz)
(**) MGA(1):  Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(II) MGA(1): Modeline "640x512"x60.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz)
(**) MGA(1):  Default mode "720x450": 53.2 MHz, 55.9 kHz, 59.9 Hz (D)
(II) MGA(1): Modeline "720x450"x59.9   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz)
(**) MGA(1):  Default mode "640x480": 74.2 MHz, 85.9 kHz, 85.1 Hz (D)
(II) MGA(1): Modeline "640x480"x85.1   74.25  640 672 752 864  480 480 482 505 doublescan +hsync +vsync (85.9 kHz)
(**) MGA(1):  Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) MGA(1): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(**) MGA(1):  Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) MGA(1): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) MGA(1):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) MGA(1): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) MGA(1):  Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) MGA(1): Modeline "640x480"x60.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz)
(**) MGA(1):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) MGA(1): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) MGA(1):  Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) MGA(1): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(**) MGA(1):  Default mode "680x384": 36.0 MHz, 47.4 kHz, 60.0 Hz (D)
(II) MGA(1): Modeline "680x384"x60.0   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz)
(**) MGA(1):  Default mode "680x384": 42.4 MHz, 47.7 kHz, 59.8 Hz (D)
(II) MGA(1): Modeline "680x384"x59.8   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz)
(**) MGA(1):  Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) MGA(1): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(**) MGA(1):  Default mode "576x432": 71.7 MHz, 91.5 kHz, 100.1 Hz (D)
(II) MGA(1): Modeline "576x432"x100.1   71.73  576 616 680 784  432 432 434 457 doublescan -hsync +vsync (91.5 kHz)
(**) MGA(1):  Default mode "576x432": 60.8 MHz, 77.5 kHz, 85.2 Hz (D)
(II) MGA(1): Modeline "576x432"x85.2   60.75  576 608 672 784  432 432 434 455 doublescan +hsync -vsync (77.5 kHz)
(**) MGA(1):  Default mode "576x432": 59.8 MHz, 77.1 kHz, 85.1 Hz (D)
(II) MGA(1): Modeline "576x432"x85.1   59.83  576 612 676 776  432 432 434 453 doublescan -hsync +vsync (77.1 kHz)
(**) MGA(1):  Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(II) MGA(1): Modeline "576x432"x75.0   54.00  576 608 672 800  432 432 434 450 doublescan +hsync +vsync (67.5 kHz)
(**) MGA(1):  Default mode "576x432": 52.5 MHz, 67.6 kHz, 75.0 Hz (D)
(II) MGA(1): Modeline "576x432"x75.0   52.49  576 612 676 776  432 432 434 451 doublescan -hsync +vsync (67.6 kHz)
(**) MGA(1):  Default mode "576x432": 48.4 MHz, 63.0 kHz, 70.0 Hz (D)
(II) MGA(1): Modeline "576x432"x70.0   48.38  576 612 672 768  432 432 434 450 doublescan -hsync +vsync (63.0 kHz)
(**) MGA(1):  Default mode "576x432": 40.8 MHz, 53.7 kHz, 60.1 Hz (D)
(II) MGA(1): Modeline "576x432"x60.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz)
(**) MGA(1):  Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) MGA(1): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(**) MGA(1):  Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(II) MGA(1): Modeline "512x384"x85.0   47.25  512 536 584 688  384 384 386 404 doublescan +hsync +vsync (68.7 kHz)
(**) MGA(1):  Default mode "512x384": 39.4 MHz, 60.0 kHz, 75.0 Hz (D)
(II) MGA(1): Modeline "512x384"x75.0   39.38  512 520 568 656  384 384 386 400 doublescan +hsync +vsync (60.0 kHz)
(**) MGA(1):  Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) MGA(1): Modeline "512x384"x70.1   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync (56.5 kHz)
(**) MGA(1):  Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) MGA(1): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz)
(**) MGA(1):  Default mode "512x384": 22.4 MHz, 35.5 kHz, 86.6 Hz (D)
(II) MGA(1): Modeline "512x384"x86.6   22.45  512 516 604 632  384 384 388 409 interlace doublescan +hsync +vsync (35.5 kHz)
(**) MGA(1):  Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) MGA(1): Modeline "416x312"x74.7   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync (49.7 kHz)
(**) MGA(1):  Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(II) MGA(1): Modeline "400x300"x85.3   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync (53.7 kHz)
(**) MGA(1):  Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) MGA(1): Modeline "400x300"x75.1   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync (46.9 kHz)
(**) MGA(1):  Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) MGA(1): Modeline "400x300"x72.2   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync (48.1 kHz)
(**) MGA(1):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) MGA(1): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) MGA(1):  Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) MGA(1): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) MGA(1):  Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(II) MGA(1): Modeline "320x240"x85.2   18.00  320 348 376 416  240 240 242 254 doublescan -hsync -vsync (43.3 kHz)
(**) MGA(1):  Default mode "360x200": 17.8 MHz, 37.9 kHz, 85.0 Hz (D)
(II) MGA(1): Modeline "360x200"x85.0   17.75  360 378 414 468  200 200 202 223 doublescan -hsync +vsync (37.9 kHz)
(**) MGA(1): Display dimensions: (406, 304) mm
(**) MGA(1): DPI set to (52, 52)
(II) MGA(1): YDstOrg is set to 0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Reloading /usr/lib/xorg/modules/libfb.so
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Reloading /usr/lib/xorg/modules/libxaa.so
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(--) Depth 24 pixmap format is 32 bpp
(II) MGA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(--) MGA(0): 16 DWORD fifo
(==) MGA(0): Default visual is TrueColor
(II) MGA(0): [drm] bpp: 32 depth: 24
(II) MGA(0): [drm] Sarea 2200+664: 2864
(WW) MGA(0): Direct rendering is not supported when VGA arb is necessary for the device
(EE) MGA(0): [drm] DRIScreenInit failed.  Disabling DRI.
(II) MGA(0): Using 744 lines for offscreen memory.
(II) MGA(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    Solid filled trapezoids
    8x8 mono pattern filled rectangles
    8x8 mono pattern filled trapezoids
    Indirect CPU to Screen color expansion
    Screen to Screen color expansion
    Solid Lines
    Dashed Lines
    Scanline Image Writes
    Setting up tile and stipple cache:
        32 128x128 slots
        10 256x256 slots
(==) MGA(0): Backing store disabled
(==) MGA(0): Silken mouse enabled
(**) MGA(0): DPMS enabled
(II) MGA(0): Using overlay video
(WW) MGA(0): Direct rendering disabled
(==) RandR enabled
(II) MGA(1): vgaHWGetIOBase: hwp->IOBase is 0x03b0, hwp->PIOOffset is 0x0000
(--) MGA(1): 16 DWORD fifo
(==) MGA(1): Default visual is TrueColor
(EE) MGA(1): Static buffer allocation failed, not initializing the DRI
(EE) MGA(1): Need at least 6084 kB video memory at this resolution, bit depth
(II) MGA(1): Using 5 lines for offscreen memory.
(II) MGA(1): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    Solid filled trapezoids
    8x8 mono pattern filled rectangles
    8x8 mono pattern filled trapezoids
    Indirect CPU to Screen color expansion
    Screen to Screen color expansion
    Solid Lines
    Dashed Lines
    Scanline Image Writes
    Setting up tile and stipple cache:
        Not enough video memory for pixmap cache
(==) MGA(1): Backing store disabled
(==) MGA(1): Silken mouse enabled
(==) MGA(1): DPMS enabled
(II) MGA(1): Using overlay video
(WW) MGA(1): Direct rendering disabled
(==) RandR enabled
(II) Found 5 VGA devices: arbiter wrapping enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) AIGLX: Screen 1 is not DRI2 capable
(II) AIGLX: Screen 1 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 1
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "de"
(**) Option "xkb_variant" "qwerty"
(II) XKB: reuse xkmfile /var/lib/xkb/server-5C1067FD84883051D58CEB235F5CD1EA8046564F.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "de"
(**) Option "xkb_variant" "qwerty"
(II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/event4)
(**) Logitech USB Optical Mouse: Applying InputClass "evdev pointer catchall"
(**) Logitech USB Optical Mouse: always reports core events
(**) Logitech USB Optical Mouse: Device: "/dev/input/event4"
(II) Logitech USB Optical Mouse: Found 3 mouse buttons
(II) Logitech USB Optical Mouse: Found scroll wheel(s)
(II) Logitech USB Optical Mouse: Found relative axes
(II) Logitech USB Optical Mouse: Found x and y relative axes
(II) Logitech USB Optical Mouse: Configuring as mouse
(**) Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE)
(II) Logitech USB Optical Mouse: initialized for relative axes.
(II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "de"
(**) Option "xkb_variant" "qwerty"
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)

``````
Section "ServerLayout"
    Identifier     "X.org Configured"
    #Screen         0  "Screen0" 0 0
    Screen        1  "Screen1-0" 0 0
    Screen        2  "Screen2-0" RightOf "Screen1-0"
    #Screen        3  "Screen3-0" RightOf "Screen2-0"
    #Screen        4  "Screen4-0" RightOf "Screen3-0"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

# Section "Files"
#     ModulePath   "/usr/lib/xorg/modules"
#     FontPath     "/usr/share/fonts/X11/misc"
#     FontPath     "/usr/share/fonts/X11/cyrillic"
#     FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
#     FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
#     FontPath     "/usr/share/fonts/X11/Type1"
#     FontPath     "/usr/share/fonts/X11/100dpi"
#     FontPath     "/usr/share/fonts/X11/75dpi"
#     FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
#     FontPath     "built-ins"
#     EndSection

Section "Module"
    #Load  "dri"
    Load  "dbe"
    Load  "glx"
    #Load  "extmod"
    #Load  "record"
    #Load  "dri2"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection



#Section "Device"
#    Identifier  "Card0"
#    Driver      "trident"
#    VendorName  "Trident Microsystems"
#    BoardName   "Blade 3D PCI/AGP"
#    BusID       "PCI:1:5:0"
#EndSection
#Section "Monitor"
#    Identifier   "Vision Master 514_0"
##    VendorName   "Ijima"
##    ModelName    "514"
#EndSection
#Section "Screen"
#    Identifier "Screen0"
#    Device     "Card0"
#    Monitor    "Vision Master 514_0"
#    SubSection "Display"
#        Depth     24
#        Modes "1600x1400" "1280x1024" "1024x768" 
#    EndSubSection
#EndSection


Section "Device"
    Identifier  "Card1-0"
    Driver      "mga"
    VendorName  "Matrox Graphics, Inc."
    BoardName   "MGA G400/G450"
    BusID       "PCI:4:0:0"
#    Screen 0
EndSection
Section "Monitor"
    Identifier   "Vision Master 514_1-0"
#    VendorName   "Ijima"
#    ModelName    "514"
#    Option       "DPMS"
        HorizSync    30-128
        VertRefresh  50-85
        DisplaySize  406 304
EndSection
Section "Screen"
    Identifier "Screen1-0"
    Device     "Card1-0"
    Monitor    "Vision Master 514_1-0"
    DefaultDepth    24
    SubSection "Display"
        Depth     24
        Modes  "1600x1400" "1280x1024" "1024x768" 
    EndSubSection
EndSection

# Section "Device"
#     Identifier  "Card1-1"
#     Driver      "vesa"
#     VendorName  "Matrox Graphics, Inc."
#     BoardName   "MGA G400/G450"
#     BusID       "PCI:4:0:0"
#     Screen 1
# EndSection
# Section "Monitor"
#     Identifier   "Vision Master 514_1-1"
#     VendorName   "Ijima"
#     ModelName    "514"
#     Option       "DPMS"
#         HorizSync    30-128
#         VertRefresh  50-85
#         DisplaySize  406 304
# EndSection
# Section "Screen"
#     Identifier "Screen1-1"
#     Device     "Card1-1"
#     Monitor    "Vision Master 514_1-1"
#     DefaultDepth    16
#     SubSection "Display"
#         Depth     16
#         Modes "1280x1024" "1024x768" "1600x1400"
#     EndSubSection
# EndSection


Section "Device"
    Identifier  "Card2-0"
    Driver      "mga"
    VendorName  "Matrox Graphics, Inc."
    BoardName   "MGA G400/G450"
    BusID       "PCI:5:0:0"
#    Screen 0
EndSection
Section "Monitor"
    Identifier   "Vision Master 514_2-0"
#    VendorName   "Ijima"
#    ModelName    "514"
#    Option       "DPMS"
    HorizSync    30-128
    VertRefresh  50-85
    DisplaySize  406 304
EndSection
Section "Screen"
    Identifier "Screen2-0"
    Device     "Card2-0"
    Monitor    "Vision Master 514_2-0"
    DefaultDepth    24
    SubSection "Display"
        Depth     24
        Modes "1600x1400" "1280x1024" "1024x768" 
    EndSubSection
EndSection


# Section "Device"
#     Identifier  "Card3-0"
#     Driver      "vesa"
# #    VendorName  "Matrox Graphics, Inc."
# #    BoardName   "MGA G400/G450"
#     BusID       "PCI:42:0:0"
# #    Screen 0
# EndSection
# Section "Monitor"
#     Identifier   "Vision Master 514_3-0"
# #    VendorName   "Ijima"
# #    ModelName    "514"
# #    Option       "DPMS"
#     HorizSync    30-128
#     VertRefresh  50-85
#     DisplaySize  406 304
# EndSection
# Section "Screen"
#     Identifier "Screen3-0"
#     Device     "Card3-0"
#     Monitor    "Vision Master 514_3-0"
#     DefaultDepth    24
#     SubSection "Display"
#         Depth     24
#         Modes "1280x1024" "1024x768" "1600x1400"
#     EndSubSection
# EndSection



# Section "Device"
#     Identifier  "Card4-0"
#     Driver      "vesa"
# #    VendorName  "Matrox Graphics, Inc."
# #    BoardName   "MGA G400/G450"
#     BusID       "PCI:47:0:0"
# #    Screen 0
# EndSection
# Section "Monitor"
#     Identifier   "Vision Master 514_4-0"
# #    VendorName   "Ijima"
# #    ModelName    "514"
# #    Option       "DPMS"
#     HorizSync    30-128
#     VertRefresh  50-85
#     DisplaySize  406 304
# EndSection
# Section "Screen"
#     Identifier "Screen4-0"
#     Device     "Card4-0"
#     Monitor    "Vision Master 514_4-0"
#     SubSection "Display"
#         Depth     24
#         Modes "1280x1024" "1024x768" "1600x1400"
#     EndSubSection
# EndSection










### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "AccelMethod"            # [<str>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "PciRetry"               # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "SetMClk"                # <freq>
        #Option     "MUXThreshold"           # <i>
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # [<str>]
        #Option     "VideoKey"               # <i>
        #Option     "NoMMIO"                 # [<bool>]
        #Option     "NoPciBurst"             # [<bool>]
        #Option     "MMIOonly"               # [<bool>]
        #Option     "CyberShadow"            # [<bool>]
        #Option     "CyberStretch"           # [<bool>]
        #Option     "XvHsync"                # <i>
        #Option     "XvVsync"                # <i>
        #Option     "XvBskew"                # <i>
        #Option     "XvRskew"                # <i>
        #Option     "FpDelay"                # <i>
        #Option     "Display1400"            # [<bool>]
        #Option     "Display"                # [<str>]
        #Option     "GammaBrightness"        # [<str>]
        #Option     "TVChipset"              # [<str>]
        #Option     "TVSignal"               # <i>


```Thank you

---

### Post by Mad Tux on 2012-03-03
I've tested several modifications like the vesa driver in the xorg.conf, nothing worked so far. I'm considering installing the unofficial drivers supplied by Matrox. The latest is v 4.4.0 for Xfree86 4.4 and X.org 7.0.


Does someone know if these Matrox mga_hal driver work for Ubuntu 10.04?
[ftp://ftp.matrox.com/pub/mga/archive/linux/2006/64bit/](ftp://ftp.matrox.com/pub/mga/archive/linux/2006/64bit/)
The latest X.org version supported by this driver is 7.0, Ubuntu 10.04 uses X.org 7.5, according to wikipedia. The last Ubuntu with X.org 7.0 was 6.04, which is quite old.
How much difference is between 7.0 and 7.5, is there a change that these will wok for my dual head setup? Is there a possibility to downgrade Xorg 7.5 to 7.0 so that the old Matrox drivers will work?

---

