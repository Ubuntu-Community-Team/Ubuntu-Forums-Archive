---
title: "Ubuntu Desktop 9.10: Screen resolution problem can not logon with admin account"
date: 2010-04-10
forum: Multimedia Software
---

### Post by CarlosHP2000 on 2010-04-10
Hi community,

 After Ubuntu Desktop start on my pc, when I try to login with the admin account I created, the screen try to fit the ubuntu splash screen ,some attempts to change the resolution may be seen, but immediately return back to the login accounts screen.

 When I try to login with a other  account (no admin privileges and created by command line) I enter to desktop with no problem and with the expected resolution.

I will really appreciate any help or recommendation to troubleshoot the issue, I was checking the log file under /var/logs/Xorg.0.log (attached the log file at the end of this post) and I can see this error :

[FONT=Courier New](EE) open /dev/fb0: No such file or directory[/FONT]
[B]
I use "sudo lspci |more"  to check the graphic card installed:[/B]

[FONT=Courier New]00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
 (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
 (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
 (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/
C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 A
C97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller
(rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3
 UniChrome] (rev 01)
[/FONT]

**This is the Log file /var/logs/Xorg.0.log**

[FONT=Courier New]
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux carlos-desktop 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=a4c7d8e1-da94-4a7a-b290-58f4332feb33 ro quiet splash
Build Date: 04 March 2010  09:56:47AM
xorg-server 2:1.6.4-2ubuntu4.2 (buildd@) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Apr 10 20:48:18 2010
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:1:0:0) 1106:7205:1849:7205 VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] rev 1, Mem @ 0xd8000000/67108864, 0xde000000/16777216, BIOS @ 0x????????/65536
(==) Using default built-in configuration (30 lines)
(==) --- Start of built-in configuration ---
    Section "Device"
        Identifier    "Builtin Default openchrome Device 0"
        Driver    "openchrome"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default openchrome Screen 0"
        Device    "Builtin Default openchrome Device 0"
    EndSection
    Section "Device"
        Identifier    "Builtin Default vesa Device 0"
        Driver    "vesa"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default vesa Screen 0"
        Device    "Builtin Default vesa Device 0"
    EndSection
    Section "Device"
        Identifier    "Builtin Default fbdev Device 0"
        Driver    "fbdev"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default fbdev Screen 0"
        Device    "Builtin Default fbdev Device 0"
    EndSection
    Section "ServerLayout"
        Identifier    "Builtin Default Layout"
        Screen    "Builtin Default openchrome Screen 0"
        Screen    "Builtin Default vesa Screen 0"
        Screen    "Builtin Default fbdev Screen 0"
    EndSection
(==) --- End of built-in configuration ---
(==) ServerLayout "Builtin Default Layout"
(**) |-->Screen "Builtin Default openchrome Screen 0" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default openchrome Device 0"
(==) No monitor specified for screen "Builtin Default openchrome Screen 0".
    Using a default monitor configuration.
(**) |-->Screen "Builtin Default vesa Screen 0" (1)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default vesa Device 0"
(==) No monitor specified for screen "Builtin Default vesa Screen 0".
    Using a default monitor configuration.
(**) |-->Screen "Builtin Default fbdev Screen 0" (2)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default fbdev Device 0"
(==) No monitor specified for screen "Builtin Default fbdev Screen 0".
    Using a default monitor configuration.
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
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "openchrome"
(II) Loading /usr/lib/xorg/modules/drivers//openchrome_drv.so
(II) Module openchrome: vendor="http://openchrome.org/"
    compiled for 1.6.1.901, module version = 0.2.903
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.6.3, module version = 2.2.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 0.4.0
    ABI class: X.Org Video Driver, version 5.0
(II) OPENCHROME: Driver for VIA Chrome chipsets: CLE266, KM400/KN400,
    K8M800/K8N800, PM800/PM880/CN400, P4M800Pro/VN800/CN700,
    K8M890/K8N890, P4M900/VN896/CN896, CX700/VX700, P4M890, VX800, VX855
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 01@00:00:0
(!!) VIA Technologies does not support this driver in any way.
(!!) For support, please refer to [http://www.openchrome.org/](http://www.openchrome.org/).
(!!) (development build, compiled on Mon Jul 27 22:18:45 2009)
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 0.0.2
    ABI class: X.Org Video Driver, version 5.0
(EE) open /dev/fb0: No such file or directory
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) CHROME(0): VIAPreInit
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 0.1.0
    ABI class: X.Org Video Driver, version 5.0
(II) CHROME(0): VIAGetRec
(II) CHROME(0): Creating default Display subsection in Screen section
    "Builtin Default openchrome Screen 0" for depth/fbbpp 24/32
(==) CHROME(0): Depth 24, (--) framebuffer bpp 32
(==) CHROME(0): RGB weight 888
(==) CHROME(0): Default visual is TrueColor
(--) CHROME(0): Chipset: KM400/KN400
(--) CHROME(0): Chipset revision: 132
(--) CHROME(0): Probed amount of VideoRAM = 65536 kB
(II) CHROME(0): Setting up default chipset options.
(II) CHROME(0): VIASetupDefaultOptions
(II) CHROME(0): Reading config file...
(II) CHROME(0): Starting to parse config file options...
(==) CHROME(0): Shadow framebuffer is disabled.
(==) CHROME(0): Hardware acceleration is enabled.
(==) CHROME(0): Using XAA acceleration architecture.
(==) CHROME(0): Using hardware two-color cursors and software full-color cursors.
(==) CHROME(0): GPU virtual command queue will be enabled.
(==) CHROME(0): DRI IRQ will be disabled if DRI is enabled.
(==) CHROME(0): AGP DMA will be enabled if DRI is enabled.
(==) CHROME(0): AGP DMA will be used for 2D acceleration.
(==) CHROME(0): PCI DMA will be used for XV image transfer if DRI is enabled.
(==) CHROME(0): Will not enable VBE modes.
(==) CHROME(0): VBE VGA register save & restore will not be used
    if VBE modes are enabled.
(==) CHROME(0): Xv Bandwidth check is enabled.
(==) CHROME(0): Will not impose a limit on video RAM reserved for DRI.
(==) CHROME(0): Will try to allocate 32768 kB of AGP memory.
(==) CHROME(0): Digital output bus width is 12 bits.
(==) CHROME(0): DVI Center is disabled.
(==) CHROME(0): Panel size is not selected from config file.
(==) CHROME(0): Panel will not be forced.
(==) CHROME(0): TV dotCrawl is disabled.
(==) CHROME(0): TV deflicker is set to 0.
(==) CHROME(0): No default TV type is set.
(==) CHROME(0): No default TV output signal type is set.
(II) CHROME(0): VIAMapMMIO
(--) CHROME(0): mapping MMIO @ 0xde000000 with size 0x9000
(--) CHROME(0): mapping BitBlt MMIO @ 0xde200000 with size 0x200000
(II) CHROME(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) CHROME(0): Will not print VGA registers.
(==) CHROME(0): Will not scan I2C buses.
(II) CHROME(0): ...Finished parsing config file options.
(--) CHROME(0): Detected ASRock Inc. K7VM2/3/4.
(II) CHROME(0): Detected MemClk 5
(II) CHROME(0): ViaGetMemoryBandwidth
(II) CHROME(0): Detected TV standard: NTSC.
(==) CHROME(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) CHROME(0): ViaI2CInit
(II) CHROME(0): ViaI2CBus1Init
(II) CHROME(0): I2C bus "I2C bus 1" initialized.
(II) CHROME(0): ViaI2cBus2Init
(II) CHROME(0): I2C bus "I2C bus 2" initialized.
(II) CHROME(0): ViaI2CBus3Init
(II) CHROME(0): I2C bus "I2C bus 3" initialized.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) CHROME(0): I2C device "I2C bus 1:E-EDID segment register" registered at address 0x60.
(II) CHROME(0): I2C device "I2C bus 1:ddc2" registered at address 0xA0.
(II) CHROME(0): Manufacturer: GSM  Model: 4386  Serial#: 18479
(II) CHROME(0): Year: 2005  Week: 7
(II) CHROME(0): EDID Version: 1.3
(II) CHROME(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) CHROME(0): Signal levels configurable
(II) CHROME(0): Sync:  Separate
(II) CHROME(0): Max Image Size [cm]: horiz.: 33  vert.: 25
(II) CHROME(0): Gamma: 2.83
(II) CHROME(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) CHROME(0): First detailed timing is preferred mode
(II) CHROME(0): redX: 0.625 redY: 0.336   greenX: 0.290 greenY: 0.599
(II) CHROME(0): blueX: 0.149 blueY: 0.073   whiteX: 0.283 whiteY: 0.298
(II) CHROME(0): Supported established timings:
(II) CHROME(0): 720x400@70Hz
(II) CHROME(0): 720x400@88Hz
(II) CHROME(0): 640x480@60Hz
(II) CHROME(0): 640x480@67Hz
(II) CHROME(0): 640x480@72Hz
(II) CHROME(0): 640x480@75Hz
(II) CHROME(0): 800x600@56Hz
(II) CHROME(0): 800x600@60Hz
(II) CHROME(0): 800x600@72Hz
(II) CHROME(0): 800x600@75Hz
(II) CHROME(0): 832x624@75Hz
(II) CHROME(0): 1024x768@87Hz (interlaced)
(II) CHROME(0): 1024x768@60Hz
(II) CHROME(0): 1024x768@70Hz
(II) CHROME(0): 1024x768@75Hz
(II) CHROME(0): 1152x870@75Hz
(II) CHROME(0): Manufacturer's mask: 0
(II) CHROME(0): Supported standard timings:
(II) CHROME(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) CHROME(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) CHROME(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) CHROME(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) CHROME(0): #4: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) CHROME(0): #5: hsize: 1280  vsize 960  refresh: 70  vid: 19073
(II) CHROME(0): Supported detailed timing:
(II) CHROME(0): clock: 94.5 MHz   Image Size:  310 x 230 mm
(II) CHROME(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) CHROME(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) CHROME(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 71 kHz, PixClock max 110 MHz
(II) CHROME(0): Monitor name: 710E
(II) CHROME(0): Monitor name: 
(II) CHROME(0): EDID (in hex):
(II) CHROME(0):     00ffffffffffff001e6d86432f480000
(II) CHROME(0):     070f0103182119b7ea0579a0564a9926
(II) CHROME(0):     12484cfffe803159714f455961598180
(II) CHROME(0):     814a01010101ea240060410028303060
(II) CHROME(0):     130036e61000001e000000fd0032a01e
(II) CHROME(0):     470b000a202020202020000000fc0037
(II) CHROME(0):     3130450a2020202020202020000000fc
(II) CHROME(0):     000a20202020202020202020202000b6
(II) CHROME(0): EDID vendor "GSM", prod id 17286
(II) CHROME(0): Using EDID range info for horizontal sync
(II) CHROME(0): Using EDID range info for vertical refresh
(II) CHROME(0): Printing DDC gathered Modelines:
(II) CHROME(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) CHROME(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) CHROME(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) CHROME(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) CHROME(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) CHROME(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) CHROME(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) CHROME(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) CHROME(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) CHROME(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) CHROME(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) CHROME(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) CHROME(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace +hsync +vsync (35.5 kHz)
(II) CHROME(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) CHROME(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) CHROME(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) CHROME(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) CHROME(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) CHROME(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) CHROME(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) CHROME(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) CHROME(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) CHROME(0): Modeline "1280x960"x70.0  120.84  1280 1368 1504 1728  960 961 964 999 -hsync +vsync (69.9 kHz)
(II) CHROME(0): ViaOutputsDetect
(II) CHROME(0): VIATVDetect
(II) CHROME(0): ViaOutputsSelect
(II) CHROME(0): ViaOutputsSelect: X Configuration: 0x00
(II) CHROME(0): ViaOutputsSelect: BIOS Initialised register: 0x00
(II) CHROME(0): ViaOutputsSelect: CRT.
(II) CHROME(0): ViaModesAttach
(II) CHROME(0): <default monitor>: Using hsync range of 30.00-71.00 kHz
(II) CHROME(0): <default monitor>: Using vrefresh range of 50.00-160.00 Hz
(II) CHROME(0): <default monitor>: Using maximum pixel clock of 110.00 MHz
(II) CHROME(0): Estimated virtual size for aspect ratio 1.3200 is 1280x960
(II) CHROME(0): Clock range:  20.00 to 230.00 MHz
(II) CHROME(0): ViaValidMode: Validating 640x350 (31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 31500 : c558 : 050b
(II) CHROME(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x400 (31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 31500 : c558 : 050b
(II) CHROME(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 720x400 (35500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 35500 : 5877 : c677
(II) CHROME(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x480 (25175)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 25175 : 0000 : 0407
(II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x480 (31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 31500 : c558 : 050b
(II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x480 (31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 31500 : c558 : 050b
(II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x480 (36000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 36000 : 5879 : c679
(II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 800x600 (36000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 36000 : 5879 : c679
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 800x600 (40000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 40000 : 515f : 8643
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 800x600 (50000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 50000 : c354 : 0207
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 800x600 (49500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 49500 : c353 : 8653
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 800x600 (56300)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 56300 : 4f76 : 4737
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (44900)
(II) CHROME(0): Not using default mode "1024x768" (interlace mode not supported)
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (65000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 65000 : 0d3b : 866d
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (75000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 75000 : 156e : 0415
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (78750)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 78750 : 0000 : 020b
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (94500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 94500 : 4542 : 0521
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (108000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 108000 : 0b53 : 8479
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x960 (108000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 108000 : 0b53 : 8479
(II) CHROME(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x960 (148500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 148500 : 0853 : 4453
(II) CHROME(0): Not using default mode "1280x960" (hsync out of range)
(II) CHROME(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) CHROME(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) CHROME(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) CHROME(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) CHROME(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 832x624 (57284)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 57284 : 4e70 : 0208
(II) CHROME(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (81620)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 81620 : 0000 : 4539
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (96770)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 96770 : 0000 : 041b
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (104990)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 104990 : 0000 : 0316
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (119650)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 119650 : 0000 : 4775
(II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (121500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 121500 : 0000 : 0211
(II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (143470)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 143470 : 0000 : 0214
(II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1360x768" (width too large for virtual size)
(II) CHROME(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1360x768" (width too large for virtual size)
(II) CHROME(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1440x900" (width too large for virtual size)
(II) CHROME(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) CHROME(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) CHROME(0): Not using default mode "960x540" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) CHROME(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (94500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 94500 : 4542 : 0521
(II) CHROME(0): ViaValidMode: Validating 800x600 (40000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 40000 : 515f : 8643
(II) CHROME(0): ViaValidMode: Validating 800x600 (36000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 36000 : 5879 : c679
(II) CHROME(0): ViaValidMode: Validating 640x480 (31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 31500 : c558 : 050b
(II) CHROME(0): ViaValidMode: Validating 640x480 (31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 31500 : c558 : 050b
(II) CHROME(0): ViaValidMode: Validating 640x480 (30240)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 30240 : 0000 : 873b
(II) CHROME(0): ViaValidMode: Validating 640x480 (25175)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 25175 : 0000 : 0407
(II) CHROME(0): ViaValidMode: Validating 720x400 (35500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 35500 : 5877 : c677
(II) CHROME(0): ViaValidMode: Validating 720x400 (28320)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 28320 : 0000 : c65f
(II) CHROME(0): ViaValidMode: Validating 1024x768 (78750)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 78750 : 0000 : 020b
(II) CHROME(0): ViaValidMode: Validating 1024x768 (75000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 75000 : 156e : 0415
(II) CHROME(0): ViaValidMode: Validating 1024x768 (65000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 65000 : 0d3b : 866d
(II) CHROME(0): ViaValidMode: Validating 1024x768 (44900)
(II) CHROME(0): Not using driver mode "1024x768" (interlace mode not supported)
(II) CHROME(0): ViaValidMode: Validating 832x624 (57284)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 57284 : 4e70 : 0208
(II) CHROME(0): ViaValidMode: Validating 800x600 (49500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 49500 : c353 : 8653
(II) CHROME(0): ViaValidMode: Validating 800x600 (50000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 50000 : c354 : 0207
(II) CHROME(0): ViaValidMode: Validating 1152x864 (108000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 108000 : 0b53 : 8479
(II) CHROME(0): ViaValidMode: Validating 640x480 (36000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 36000 : 5879 : c679
(II) CHROME(0): ViaValidMode: Validating 1152x864 (108000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 108000 : 0b53 : 8479
(II) CHROME(0): ViaValidMode: Validating 800x600 (56250)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 56250 : 0000 : 4737
(II) CHROME(0): ViaValidMode: Validating 1024x768 (94500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 94500 : 4542 : 0521
(II) CHROME(0): Not using driver mode "1280x1024" (height too large for virtual size)
(II) CHROME(0): ViaValidMode: Validating 1280x960 (120839)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 120839 : 0000 : 073b
(II) CHROME(0): Not using driver mode "1280x960" (mode clock too high)
(II) CHROME(0): ViaValidMode: Validating 1280x960 (108000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 108000 : 0b53 : 8479
(II) CHROME(0): ViaValidMode: Validating 1152x864 (108000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 108000 : 0b53 : 8479
(II) CHROME(0): ViaValidMode: Validating 1152x864 (108000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 108000 : 0b53 : 8479
(II) CHROME(0): ViaValidMode: Validating 1152x864 (108000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 108000 : 0b53 : 8479
(II) CHROME(0): ViaValidMode: Validating 1152x864 (104990)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 104990 : 0000 : 0316
(II) CHROME(0): ViaValidMode: Validating 1152x864 (96770)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 96770 : 0000 : 041b
(II) CHROME(0): ViaValidMode: Validating 1152x864 (81620)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 81620 : 0000 : 4539
(II) CHROME(0): ViaValidMode: Validating 1024x768 (94500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 94500 : 4542 : 0521
(II) CHROME(0): ViaValidMode: Validating 1024x768 (94500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 94500 : 4542 : 0521
(II) CHROME(0): ViaValidMode: Validating 1024x768 (78750)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 78750 : 0000 : 020b
(II) CHROME(0): ViaValidMode: Validating 1024x768 (75000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 75000 : 156e : 0415
(II) CHROME(0): ViaValidMode: Validating 1024x768 (65000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 65000 : 0d3b : 866d
(II) CHROME(0): ViaValidMode: Validating 1024x768 (94500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 94500 : 4542 : 0521
(II) CHROME(0): ViaValidMode: Validating 1024x768 (78750)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 78750 : 0000 : 020b
(II) CHROME(0): ViaValidMode: Validating 1024x768 (75000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 75000 : 156e : 0415
(II) CHROME(0): ViaValidMode: Validating 1024x768 (65000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 65000 : 0d3b : 866d
(II) CHROME(0): ViaValidMode: Validating 832x624 (57284)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 57284 : 4e70 : 0208
(II) CHROME(0): ViaValidMode: Validating 832x624 (57284)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 57284 : 4e70 : 0208
(II) CHROME(0): ViaValidMode: Validating 800x600 (56250)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 56250 : 0000 : 4737
(II) CHROME(0): ViaValidMode: Validating 800x600 (49500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 49500 : c353 : 8653
(II) CHROME(0): ViaValidMode: Validating 800x600 (50000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 50000 : c354 : 0207
(II) CHROME(0): ViaValidMode: Validating 800x600 (40000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 40000 : 515f : 8643
(II) CHROME(0): ViaValidMode: Validating 800x600 (36000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 36000 : 5879 : c679
(II) CHROME(0): ViaValidMode: Validating 800x600 (56300)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 56300 : 4f76 : 4737
(II) CHROME(0): ViaValidMode: Validating 800x600 (49500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 49500 : c353 : 8653
(II) CHROME(0): ViaValidMode: Validating 800x600 (50000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 50000 : c354 : 0207
(II) CHROME(0): ViaValidMode: Validating 800x600 (40000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 40000 : 515f : 8643
(II) CHROME(0): ViaValidMode: Validating 800x600 (36000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 36000 : 5879 : c679
(II) CHROME(0): ViaValidMode: Validating 640x480 (36000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 36000 : 5879 : c679
(II) CHROME(0): ViaValidMode: Validating 640x480 (31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 31500 : c558 : 050b
(II) CHROME(0): ViaValidMode: Validating 640x480 (31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 31500 : c558 : 050b
(II) CHROME(0): ViaValidMode: Validating 640x480 (30240)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 30240 : 0000 : 873b
(II) CHROME(0): ViaValidMode: Validating 640x480 (25175)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 25175 : 0000 : 0407
(II) CHROME(0): ViaValidMode: Validating 640x480 (36000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 36000 : 5879 : c679
(II) CHROME(0): ViaValidMode: Validating 640x480 (31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 31500 : c558 : 050b
(II) CHROME(0): ViaValidMode: Validating 640x480 (31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 31500 : c558 : 050b
(II) CHROME(0): ViaValidMode: Validating 640x480 (25175)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 25175 : 0000 : 0407
(II) CHROME(0): ViaValidMode: Validating 720x400 (35500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 35500 : 5877 : c677
(II) CHROME(0): ViaValidMode: Validating 720x400 (28320)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 28320 : 0000 : c65f
(II) CHROME(0): ViaValidMode: Validating 720x400 (35500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 35500 : 5877 : c677
(II) CHROME(0): ViaValidMode: Validating 640x400 (31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 31500 : c558 : 050b
(II) CHROME(0): ViaValidMode: Validating 640x350 (31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaComputeDotClock 31500 : c558 : 050b
(--) CHROME(0): Virtual size is 1280x960 (pitch 1280)
(**) CHROME(0): *Default mode "1280x960": 108.0 MHz (scaled from 287712.0 MHz), 60.0 kHz, 60.0 Hz
(II) CHROME(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(**) CHROME(0): *Driver mode "1152x864": 108.0 MHz (scaled from 287712.0 MHz), 67.5 kHz, 75.0 Hz
(II) CHROME(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) CHROME(0): *Driver mode "1152x864": 108.0 MHz (scaled from 287712.0 MHz), 67.5 kHz, 75.0 Hz
(II) CHROME(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) CHROME(0): *Default mode "1152x864": 108.0 MHz (scaled from 287712.0 MHz), 67.5 kHz, 75.0 Hz
(II) CHROME(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) CHROME(0): *Default mode "1152x864": 105.0 MHz (scaled from 279693.4 MHz), 67.6 kHz, 75.0 Hz
(II) CHROME(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(**) CHROME(0): *Default mode "1152x864": 96.8 MHz (scaled from 257795.3 MHz), 63.0 kHz, 70.0 Hz
(II) CHROME(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(**) CHROME(0): *Default mode "1152x864": 81.6 MHz (scaled from 217435.7 MHz), 53.7 kHz, 60.0 Hz
(II) CHROME(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(**) CHROME(0): *Driver mode "1024x768": 94.5 MHz (scaled from 251748.0 MHz), 68.7 kHz, 85.0 Hz
(II) CHROME(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(**) CHROME(0): *Driver mode "1024x768": 94.5 MHz (scaled from 251748.0 MHz), 68.7 kHz, 85.0 Hz
(II) CHROME(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(**) CHROME(0): *Driver mode "1024x768": 78.8 MHz (scaled from 209790.0 MHz), 60.0 kHz, 75.0 Hz
(II) CHROME(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) CHROME(0): *Driver mode "1024x768": 75.0 MHz (scaled from 199800.0 MHz), 56.5 kHz, 70.1 Hz
(II) CHROME(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) CHROME(0): *Driver mode "1024x768": 65.0 MHz (scaled from 173160.0 MHz), 48.4 kHz, 60.0 Hz
(II) CHROME(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) CHROME(0): *Default mode "1024x768": 94.5 MHz (scaled from 251748.0 MHz), 68.7 kHz, 85.0 Hz
(II) CHROME(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(**) CHROME(0): *Default mode "1024x768": 78.8 MHz (scaled from 209790.0 MHz), 60.0 kHz, 75.0 Hz
(II) CHROME(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) CHROME(0): *Default mode "1024x768": 75.0 MHz (scaled from 199800.0 MHz), 56.5 kHz, 70.1 Hz
(II) CHROME(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) CHROME(0): *Default mode "1024x768": 65.0 MHz (scaled from 173160.0 MHz), 48.4 kHz, 60.0 Hz
(II) CHROME(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) CHROME(0): *Driver mode "832x624": 57.3 MHz (scaled from 152604.6 MHz), 49.7 kHz, 74.6 Hz
(II) CHROME(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) CHROME(0): *Default mode "832x624": 57.3 MHz (scaled from 152604.6 MHz), 49.7 kHz, 74.6 Hz
(II) CHROME(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) CHROME(0): *Driver mode "800x600": 56.2 MHz (scaled from 149850.0 MHz), 53.7 kHz, 85.1 Hz
(II) CHROME(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(**) CHROME(0): *Driver mode "800x600": 49.5 MHz (scaled from 131868.0 MHz), 46.9 kHz, 75.0 Hz
(II) CHROME(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) CHROME(0): *Driver mode "800x600": 50.0 MHz (scaled from 133200.0 MHz), 48.1 kHz, 72.2 Hz
(II) CHROME(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) CHROME(0): *Driver mode "800x600": 40.0 MHz (scaled from 106560.0 MHz), 37.9 kHz, 60.3 Hz
(II) CHROME(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) CHROME(0): *Driver mode "800x600": 36.0 MHz (scaled from 95904.0 MHz), 35.2 kHz, 56.2 Hz
(II) CHROME(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) CHROME(0): *Default mode "800x600": 56.3 MHz (scaled from 149983.2 MHz), 53.7 kHz, 85.1 Hz
(II) CHROME(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(**) CHROME(0): *Default mode "800x600": 49.5 MHz (scaled from 131868.0 MHz), 46.9 kHz, 75.0 Hz
(II) CHROME(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) CHROME(0): *Default mode "800x600": 50.0 MHz (scaled from 133200.0 MHz), 48.1 kHz, 72.2 Hz
(II) CHROME(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) CHROME(0): *Default mode "800x600": 40.0 MHz (scaled from 106560.0 MHz), 37.9 kHz, 60.3 Hz
(II) CHROME(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) CHROME(0): *Default mode "800x600": 36.0 MHz (scaled from 95904.0 MHz), 35.2 kHz, 56.2 Hz
(II) CHROME(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) CHROME(0): *Driver mode "640x480": 36.0 MHz (scaled from 95904.0 MHz), 43.3 kHz, 85.0 Hz
(II) CHROME(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(**) CHROME(0): *Driver mode "640x480": 31.5 MHz (scaled from 83916.0 MHz), 37.5 kHz, 75.0 Hz
(II) CHROME(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) CHROME(0): *Driver mode "640x480": 31.5 MHz (scaled from 83916.0 MHz), 37.9 kHz, 72.8 Hz
(II) CHROME(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) CHROME(0): *Driver mode "640x480": 30.2 MHz (scaled from 80559.4 MHz), 35.0 kHz, 66.7 Hz
(II) CHROME(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(**) CHROME(0): *Driver mode "640x480": 25.2 MHz (scaled from 67066.2 MHz), 31.5 kHz, 59.9 Hz
(II) CHROME(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) CHROME(0): *Default mode "640x480": 36.0 MHz (scaled from 95904.0 MHz), 43.3 kHz, 85.0 Hz
(II) CHROME(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(**) CHROME(0): *Default mode "640x480": 31.5 MHz (scaled from 83916.0 MHz), 37.5 kHz, 75.0 Hz
(II) CHROME(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) CHROME(0): *Default mode "640x480": 31.5 MHz (scaled from 83916.0 MHz), 37.9 kHz, 72.8 Hz
(II) CHROME(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) CHROME(0): *Default mode "640x480": 25.2 MHz (scaled from 67066.2 MHz), 31.5 kHz, 59.9 Hz
(II) CHROME(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) CHROME(0): *Driver mode "720x400": 35.5 MHz (scaled from 94572.0 MHz), 39.4 kHz, 87.8 Hz
(II) CHROME(0): Modeline "720x400"x87.8   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(**) CHROME(0): *Driver mode "720x400": 28.3 MHz (scaled from 75444.5 MHz), 31.5 kHz, 70.1 Hz
(II) CHROME(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(**) CHROME(0): *Default mode "720x400": 35.5 MHz (scaled from 94572.0 MHz), 37.9 kHz, 85.0 Hz
(II) CHROME(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(**) CHROME(0): *Default mode "640x400": 31.5 MHz (scaled from 83916.0 MHz), 37.9 kHz, 85.1 Hz
(II) CHROME(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(**) CHROME(0): *Default mode "640x350": 31.5 MHz (scaled from 83916.0 MHz), 37.9 kHz, 85.1 Hz
(II) CHROME(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(**) CHROME(0): Display dimensions: (330, 250) mm
(**) CHROME(0): DPI set to (98, 97)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.2.1
    ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) CHROME(0): VIAUnmapMem
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux//libfbdevhw.so
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) CHROME(0): VIAScreenInit
(II) CHROME(0): VIAMapFB
(--) CHROME(0): mapping framebuffer @ 0xd8000000 with size 0x4000000
(--) CHROME(0): Frame buffer start: 0xb3800000, free start: 0x4b0000 end: 0x4000000
(II) CHROME(0): VIAMapMMIO
(--) CHROME(0): mapping MMIO @ 0xde000000 with size 0x9000
(--) CHROME(0): mapping BitBlt MMIO @ 0xde200000 with size 0x200000
(II) CHROME(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) CHROME(0): VIASave
(II) CHROME(0): Primary
(II) CHROME(0): Crtc...
(II) CHROME(0): TVSave...
(II) CHROME(0): VIAWriteMode
(II) CHROME(0): ViaModePrimary
(II) CHROME(0): Name: 1280x960
(II) CHROME(0): Clock: 108000
(II) CHROME(0): VRefresh: 60.000000
(II) CHROME(0): HSync: 60.000000
(II) CHROME(0): HDisplay: 1280
(II) CHROME(0): HSyncStart: 1376
(II) CHROME(0): HSyncEnd: 1488
(II) CHROME(0): HTotal: 1800
(II) CHROME(0): HSkew: 0
(II) CHROME(0): VDisplay: 960
(II) CHROME(0): VSyncStart: 961
(II) CHROME(0): VSyncEnd: 964
(II) CHROME(0): VTotal: 1000
(II) CHROME(0): VScan: 0
(II) CHROME(0): Flags: 5
(II) CHROME(0): CrtcHDisplay: 0x500
(II) CHROME(0): CrtcHBlankStart: 0x500
(II) CHROME(0): CrtcHSyncStart: 0x560
(II) CHROME(0): CrtcHSyncEnd: 0x5d0
(II) CHROME(0): CrtcHBlankEnd: 0x708
(II) CHROME(0): CrtcHTotal: 0x708
(II) CHROME(0): CrtcHSkew: 0x0
(II) CHROME(0): CrtcVDisplay: 0x3c0
(II) CHROME(0): CrtcVBlankStart: 0x3c0
(II) CHROME(0): CrtcVSyncStart: 0x3c1
(II) CHROME(0): CrtcVSyncEnd: 0x3c4
(II) CHROME(0): CrtcVBlankEnd: 0x3e8
(II) CHROME(0): CrtcVTotal: 0x3e8
(II) CHROME(0): ViaFirstCRTCSetMode
(II) CHROME(0): Setting up 1280x960
(II) CHROME(0): ViaComputeDotClock 108000 : 0b53 : 8479
(II) CHROME(0): ViaTVPower: Off.
(II) CHROME(0): ViaSetPrimaryFIFO
(II) CHROME(0): ViaSetPrimaryExpireNumber
(II) CHROME(0): ViaSetDotclock to 0x008479
(II) CHROME(0): ViaSetUseExternalClock
(II) CHROME(0): VIAAdjustFrame
(II) CHROME(0): VIAAdjustFrame
(II) CHROME(0): - Blanked
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] loaded kernel module for "via" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) CHROME(0): [drm] Using the DRM lock SAREA also for drawables.
(II) CHROME(0): [drm] framebuffer handle = 0xd8000000
(II) CHROME(0): [drm] added 1 reserved context for kernel
(II) CHROME(0): X context handle = 0x1
(II) CHROME(0): [drm] installed DRM signal handler
(II) CHROME(0): [dri] visual configs initialized.
(II) CHROME(0): [drm] register handle = 0xde000000
(II) CHROME(0): [drm] framebuffer handle = 0xd8000000
(II) CHROME(0): [drm] mmio Registers = 0xde000000
(II) CHROME(0): [dri] mmio mapped.
(II) CHROME(0): - Visuals set up
(II) CHROME(0): VIAInternalScreenInit
(II) CHROME(0): - B & W
(II) CHROME(0): CursorStart: 0x3fc0000
(II) CHROME(0): Using 2880 lines for offscreen memory.
(II) CHROME(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    8x8 mono pattern filled rectangles
    8x8 color pattern filled rectangles
    Solid Lines
    Dashed Lines
    Image Writes
    Setting up tile and stipple cache:
        32 128x128 slots
        23 256x256 slots
        6 512x512 slots
        32 8x8 color pattern slots
(==) CHROME(0): Backing store disabled
(II) CHROME(0): - Backing store set up
(II) CHROME(0): - SW cursor set up
(II) CHROME(0): VIAHWCursorInit
(II) CHROME(0): - Def Color map set up
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): - Palette loaded
(II) CHROME(0): DPMS enabled
(II) CHROME(0): - DPMS set up
(II) CHROME(0): - Color maps etc. set up
(II) CHROME(0): [drm] Detected AGP vendor 0x1106, device 0x3205
(II) CHROME(0): [drm] Didn't find any AGP v3 compatible device. Trying AGP 4X mode.
(II) CHROME(0): [drm] Trying to enable AGP fast writes.
(II) CHROME(0): [drm] drmAgpEnabled succeeded
(II) CHROME(0): [drm] agpAddr = 0xe0000000
(II) CHROME(0): [drm] agpBase = (nil)
(II) CHROME(0): [drm] agpAddr = 0xe0000000
(II) CHROME(0): [drm] agpSize = 0x01e00000
(II) CHROME(0): [drm] agp physical addr = 0x00000000
(II) CHROME(0): [dri] Using AGP.
(II) CHROME(0): [drm] Using 47175648 bytes for DRM memory heap.
(II) CHROME(0): [dri] Frame buffer initialized.
(II) CHROME(0): [DRI] installation complete
(II) CHROME(0): [dri] Kernel data initialized.
(II) CHROME(0): [drm] Initialized AGP ring-buffer, size 0x200000 at AGP offset 0x1e00000.
(II) CHROME(0): direct rendering enabled
(II) CHROME(0): [Xv] Using PCI DMA for Xv image transfer.
Fulfilled via DRI at 19665920
(II) CHROME(0): Benchmarking video copy.  Less time is better.
(--) CHROME(0): Timed   libc YUV420 copy... 12710968. Throughput: 77.8 MiB/s.
(--) CHROME(0): Timed kernel YUV420 copy... 8066838. Throughput: 122.5 MiB/s.
(--) CHROME(0): Timed    SSE YUV420 copy... 23568220. Throughput: 41.9 MiB/s.
(--) CHROME(0): Timed    MMX YUV420 copy... 20658678. Throughput: 47.8 MiB/s.
(--) CHROME(0): Timed 3DNow! YUV420 copy... 7995838. Throughput: 123.6 MiB/s.
(--) CHROME(0): Timed   MMX2 YUV420 copy... 7974410. Throughput: 123.9 MiB/s.
Freed 19665920 (pool 2)
(--) CHROME(0): Using MMX2 YUV42X copy for video.
(WW) CHROME(0): [XvMC] XvMC is not supported on this chipset.
(II) CHROME(0): - Done
(==) RandR enabled
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
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: Loaded and initialized /usr/lib/dri/unichrome_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.2.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "es"
(II) config/hal: Adding input device ImExPS/2 Generic Explorer Mouse
(**) ImExPS/2 Generic Explorer Mouse: always reports core events
(**) ImExPS/2 Generic Explorer Mouse: Device: "/dev/input/event5"
(II) ImExPS/2 Generic Explorer Mouse: Found 9 mouse buttons
(II) ImExPS/2 Generic Explorer Mouse: Found x and y relative axes
(II) ImExPS/2 Generic Explorer Mouse: Found scroll wheel(s)
(II) ImExPS/2 Generic Explorer Mouse: Configuring as mouse
(**) ImExPS/2 Generic Explorer Mouse: YAxisMapping: buttons 4 and 5
(**) ImExPS/2 Generic Explorer Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImExPS/2 Generic Explorer Mouse" (type: MOUSE)
(**) ImExPS/2 Generic Explorer Mouse: (accel) keeping acceleration scheme 1
(**) ImExPS/2 Generic Explorer Mouse: (accel) filter chain progression: 2.00
(**) ImExPS/2 Generic Explorer Mouse: (accel) filter stage 0: 20.00 ms
(**) ImExPS/2 Generic Explorer Mouse: (accel) set acceleration profile 0
(II) ImExPS/2 Generic Explorer Mouse: initialized for relative axes.
(II) config/hal: Adding input device Sleep Button
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event2"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "es"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "es"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "es"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) CHROME(0): ViaDisplayDisableCRT[/FONT]

---

### Post by CarlosHP2000 on 2010-04-16
Hi  community,

 I solved the problem, after removing the file **"monitor.xml" **under:
 [FONT=Courier New]/home/carlos/.config/monitor.xml [/FONT]I can now login with no problem.

 It seems that after I changed the screen resolution (testing some options) using System>Preferences>Display  this file got created and after this happened I couldn't login anymore being sent back to the main accounts login screen.

I realized that other account which did not have this file was working with no problem, so it has nothing to do with other components, it was just a config file associated with the account.

Hope this could help any of you having the same issue, I apologize for not giving a better technical explanation, GNOME settings and Video issues are not my strength area.

Regards,

Carlos.

---

