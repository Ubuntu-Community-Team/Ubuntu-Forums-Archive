---
title: "blank display after display restart w/ Ubuntu 10.04"
date: 2011-08-07
forum: Multimedia Software
---

### Post by metso on 2011-08-07
hi,

My ubuntu 10.04 system works perfectly, except when I turn off the display. When turning it on again it is black. I can still connect and control the PC via ssh but I have to do a "sudo /etc/init.d/gdm stop" and "sudo /etc/init.d/gdm start" in order to be able to log in again.

I tried modifying my /etc/X11/xorg.conf file but it did not make any difference. I guess it might be related to an EDID problem someone else has had ([http://markbrewster.wordpress.com/2010/02/04/ubuntu-9-10-not-starting-up-at-full-resolution-with-tv-turned-off/](http://markbrewster.wordpress.com/2010/02/04/ubuntu-9-10-not-starting-up-at-full-resolution-with-tv-turned-off/)) but even though I have an option "Option "UseEDID" "False"" in the config file, string "PSB(0): Option "UseEDID" is not used" is displayed in /var/log/Xorg.0.log.

Here is my xorg.conf file:
> 
Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
        ModelName    "Ancor Communications Inc"
        Modeline "1440x900" 59.9 1440 1488 1520 1600  900 903 909 926
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
            Viewport   0 0
            Depth     16
    EndSubSection
    SubSection "Display"
            Viewport   0 0
            Depth     24
    EndSubSection
EndSection

Section "Module"
    Load  "glx"
    Load  "record"
    Load  "extmod"
    Load  "xtrap"
    Load  "dbe"
    Load  "dri"
EndSection

Section "DRI"
    Mode    0666
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

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Device"
    Option      "IgnoreACPI"             "true"
    Option      "NoPanel"                "true"
    Identifier  "Card0"
        Option "UseEDID" "False"
    VendorName  "Intel Corporation"
    BoardName   "System Controller Hub (SCH Poulsbo) Graphics Controller"
    BusID       "PCI:0:2:0"
    Option "ForceEnablePipeA" "true"
    Driver    "psb"
    ### Available Driver options are:-
    ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
    ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
    ### [arg]: arg optional
    #Option     "ShadowFB"               # [<bool>]
    #Option     "NoAccel"                # [<bool>]
    #Option     "SWcursor"               # [<bool>]
    #Option     "ExaMem"                 # <i>
    #Option     "ExaScratch"             # <i>
    #Option     "LidTimer"               # [<bool>]
    #Option     "NoFitting"              # [<bool>]
    #Option     "DownScale"              # [<bool>]
EndSection

..and this is my [B]Xorg.0.log
[/B]> 
                                                                     
                                                                     
                                                                     
                                             

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux mikko-fitpc2 2.6.32-33-generic #71-Ubuntu SMP Wed Jul 20 17:30:40 UTC 2011 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-33-generic root=UUID=2097e0a1-14e7-46f9-8e4f-7ec7c7bda69b ro quiet splash
Build Date: 08 March 2011  08:22:50AM
xorg-server 2:1.7.6-2ubuntu7.6 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Aug  7 18:14:12 2011
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Keyboard0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(**) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Mouse0
(WW) Disabling Keyboard0
(II) Loader magic: 0x81f1e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI:*(0:0:2:0) 8086:8108:8086:8119 Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller rev 7, Mem @ 0xb0080000/524288, 0xc0000000/268435456, 0xb0000000/262144, I/O @ 0x00001810/8
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri2" will be loaded by default.
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
(II) LoadModule: "xtrap"
(WW) Warning, couldn't open module xtrap
(II) UnloadModule: "xtrap"
(EE) Failed to load module "xtrap" (module does not exist, 0)
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
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
(II) LoadModule: "psb"
(II) Loading /usr/lib/xorg/modules/drivers/psb_drv.so
(II) Module psb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.32.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) PSB: driver for Intel GMA500 chipsets: Intel GMA500
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for psb
(--) Chipset Intel GMA500 found
(II) PSB(0): psb_drv - 2.2.0.32L.0027
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Video Driver, version 6.0
(==) PSB(0): Depth 24, (--) framebuffer bpp 32
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(--) PSB(0): Linear framebuffer at 0x0
(==) PSB(0): RGB weight 888
(==) PSB(0): Default visual is TrueColor
(**) PSB(0): Option "IgnoreACPI" "true"
(**) PSB(0): Option "NoPanel" "true"
(==) PSB(0): Use hardware cursor.
(**) PSB(0): Not using ACPI for LVDS detection.
(II) Loading sub module "dri"
(II) LoadModule: "dri"
(II) Reloading /usr/lib/xorg/modules/extensions/libdri.so
(II) Loading sub module "Xpsb"
(II) LoadModule: "Xpsb"
(II) Loading /usr/lib/xorg/modules/drivers/Xpsb.so
(II) Module Xpsb: vendor="Tungsten Graphics Inc."
    compiled for 1.6.0, module version = 0.1.0
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.1.0
    ABI class: X.Org Video Driver, version 6.0
(--) PSB(0): Mapped PCI MMIO at physical address 0xb0080000
    with size 512 kiB
(EE) PSB(0): the stolenBase is:0x3f800000
(--) PSB(0): Detected 7932 kiB of "stolen" memory set aside as video RAM.
(EE) PSB(0): screnIndex is:0;fbPhys is:0x3f800000; fbsize is:0x007bf000
(--) PSB(0): Mapped graphics aperture at physical address 0x3f800000
    with size 7 MiB
(II) PSB(0): Poulsbo MemClock 533, CoreClock 200
(II) PSB(0): Poulsbo Latencies 324 744 210 450
(II) PSB(0): sku_value is 0x00800000, sku_bSDVOEnable is 1, sku_bMaxResEnableInt is 0
(II) PSB(0): No LVDS found (via ACPI)
(II) PSB(0): If you do have an LVDS panel, try adding Option "IgnoreACPI"
xf86TokenToOptinfo: table is NULL
(II) PSB(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) PSB(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) PSB(0): I2C bus "SDVOB DDC Bus" initialized.
(II) PSB(0): Output TMDS-1 using monitor section Monitor0
(II) PSB(0): SDVO device VID/DID: 02:3C.06, clock range 25.0MHz - 200.0MHz, input 1: Y, input 2: N, output 1: Y, output 2: N
(++) PSB(0): i830_psbSaveHWState
(II) PSB(0): Current clock rate multiplier: 1
(==) PSB(0): Shadow framebuffer disabled
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules/libexa.so
(II) Module exa: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.5.0
    ABI class: X.Org Video Driver, version 6.0
(==) PSB(0): Acceleration enabled
(==) PSB(0): [EXA] Allocate 32768 kiB for EXA pixmap cache.
(==) PSB(0): [EXA] Allocate 4 kiB for scratch memory.
(II) PSB(0): Output "TMDS-1" is assigned to this screen.
(WW) PSB(0): Output "LVDS0" was not found and cannot be assigned to this screen.
(II) PSB(0): Searching for matching Poulsbo mode(s):
(II) PSB(0): I2C device "SDVOB DDC Bus:ddc2" registered at address 0xA0.
(II) PSB(0): I2C device "SDVOB DDC Bus:DDC control interface" registered at address 0x6E.
(II) PSB(0): EDID for output TMDS-1
(II) PSB(0): Manufacturer: ACI  Model: 26a3  Serial#: 117308
(II) PSB(0): Year: 2010  Week: 11
(II) PSB(0): EDID Version: 1.3
(II) PSB(0): Digital Display Input
(II) PSB(0): Max Image Size [cm]: horiz.: 55  vert.: 34
(II) PSB(0): Gamma: 2.20
(II) PSB(0): DPMS capabilities: Off
(II) PSB(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) PSB(0): First detailed timing is preferred mode
(II) PSB(0): redX: 0.640 redY: 0.352   greenX: 0.287 greenY: 0.628
(II) PSB(0): blueX: 0.144 blueY: 0.075   whiteX: 0.312 whiteY: 0.328
(II) PSB(0): Supported established timings:
(II) PSB(0): 720x400@70Hz
(II) PSB(0): 640x480@60Hz
(II) PSB(0): 640x480@67Hz
(II) PSB(0): 640x480@72Hz
(II) PSB(0): 640x480@75Hz
(II) PSB(0): 800x600@56Hz
(II) PSB(0): 800x600@60Hz
(II) PSB(0): 800x600@72Hz
(II) PSB(0): 800x600@75Hz
(II) PSB(0): 832x624@75Hz
(II) PSB(0): 1024x768@60Hz
(II) PSB(0): 1024x768@70Hz
(II) PSB(0): 1024x768@75Hz
(II) PSB(0): 1280x1024@75Hz
(II) PSB(0): Manufacturer's mask: 0
(II) PSB(0): Supported standard timings:
(II) PSB(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) PSB(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) PSB(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) PSB(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) PSB(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) PSB(0): Supported detailed timing:
(II) PSB(0): clock: 154.0 MHz   Image Size:  550 x 340 mm
(II) PSB(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) PSB(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) PSB(0): Serial No: A3LMTF117308
(II) PSB(0): Ranges: V min: 50 V max: 75 Hz, H min: 30 H max: 85 kHz, PixClock max 170 MHz
(II) PSB(0): Monitor name: ASUS VK266H
(II) PSB(0): Number of EDID sections to follow: 1
(II) PSB(0): EDID (in hex):
(II) PSB(0):     00ffffffffffff000469a3263cca0100
(II) PSB(0):     0b140103803722782acbd0a35a49a024
(II) PSB(0):     135054bfef00714f0101814081809500
(II) PSB(0):     b30001010101283c80a070b023403020
(II) PSB(0):     360026542100001a000000ff0041334c
(II) PSB(0):     4d54463131373330380a000000fd0032
(II) PSB(0):     4b1e5511000a202020202020000000fc
(II) PSB(0):     004153555320564b323636480a200159
(II) PSB(0):     020322714f1f14041302110615011005
(II) PSB(0):     03120716230907078301000065030c00
(II) PSB(0):     10008c0ad08a20e02d10103e9600c48e
(II) PSB(0):     21000018011d007251d01e206e285500
(II) PSB(0):     c48e2100001e011d00bc52d01e20b828
(II) PSB(0):     5540c48e2100001e8c0ad09020403120
(II) PSB(0):     0c405500c48e210000188c0aa0205120
(II) PSB(0):     1810187e2300c48e210000980000004a
(II) PSB(0): EDID vendor "ACI", prod id 9891
(II) PSB(0): Using EDID range info for horizontal sync
(II) PSB(0): Using EDID range info for vertical refresh
(II) PSB(0): Printing DDC gathered Modelines:
(II) PSB(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) PSB(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) PSB(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) PSB(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) PSB(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) PSB(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) PSB(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) PSB(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) PSB(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) PSB(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) PSB(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) PSB(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) PSB(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) PSB(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) PSB(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) PSB(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) PSB(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) PSB(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) PSB(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) PSB(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) PSB(0): EDID vendor "ACI", prod id 9891
(II) PSB(0): Printing probed modes for output TMDS-1
(II) PSB(0): Modeline "1920x1200"x60.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) PSB(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) PSB(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) PSB(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) PSB(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) PSB(0): Modeline "1440x900"x40.4   59.90  1440 1488 1520 1600  900 903 909 926 (37.4 kHz)
(II) PSB(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) PSB(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) PSB(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
(II) PSB(0): Modeline "1280x720"x50.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
(II) PSB(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) PSB(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) PSB(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) PSB(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) PSB(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) PSB(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) PSB(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) PSB(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) PSB(0): Modeline "720x576"x50.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
(II) PSB(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) PSB(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) PSB(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) PSB(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) PSB(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) PSB(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) PSB(0): Output TMDS-1 connected
(II) PSB(0): Using exact sizes for initial modes
(II) PSB(0): Output TMDS-1 using initial mode 1920x1200
(II) PSB(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(**) PSB(0): Display dimensions: (550, 340) mm
(**) PSB(0): DPI set to (88, 143)
(--) Depth 24 pixmap format is 32 bpp
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID PCI:0:2:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) PSB(0): [drm] Using the DRM lock SAREA also for drawables.
(II) PSB(0): [drm] framebuffer handle = 0x3f800000
(II) PSB(0): [drm] added 1 reserved context for kernel
(II) PSB(0): X context handle = 0x1
(II) PSB(0): [drm] installed DRM signal handler
(II) PSB(0): [drm] Allocated device DRM context 2.
(II) [drm] Irq handler installed for IRQ 16.
(II) PSB(0): Using default MigrationHeuristic: greedy
(**) PSB(0): Option "MigrationHeuristic" "greedy"
(II) EXA(0): Driver allocated offscreen pixmaps
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(II)         UploadToScreen
(==) PSB(0): Backing store disabled
(==) PSB(0): Silken mouse enabled
(==) PSB(0): DPMS enabled
(WW) PSB(0): Option "UseEDID" is not used
(WW) PSB(0): Option "ForceEnablePipeA" is not used
(II) PSB(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) PSB(0): [DRI] installation complete
Xpsb - 5.0.1.0046
(II) PSB(0): [Xpsb] Disable hog plug daemon in PSB driver.
(II) PSB(0): [Xpsb] Started kernel request thread.
(II) PSB(0): Xpsb extension for 3D engine acceleration enabled.
(II) PSB(0): Set up textured video
(II) PSB(0): Xv video acceleration enabled.
(II) PSB(0): Initializing HW Cursor.
(EE) PSB(0): has_fbdev is true
(++) PSB(0): i830_psbSaveHWState
(II) PSB(0): Current clock rate multiplier: 1
(II) PSB(0): xxi830_Output configuration:
(II) PSB(0):   Pipe A is on
(II) PSB(0):   Display plane A is now enabled and connected to pipe A.
(II) PSB(0):   Pipe B is not available to this screen.
(II) PSB(0):   Output TMDS-1 is connected to pipe A
(--) RandR disabled
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
drmOpenDevice: open result is 13, (OK)
drmOpenByBusid: Searching for BusID PCI:0:2:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 13, (OK)
drmOpenByBusid: drmOpenMinor returns 13
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: Loaded and initialized /usr/lib/dri/psb_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) PSB(0): Setting screen physical size to 507 x 317
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "fi"
(II) XKB: reuse xkmfile /var/lib/xkb/server-F30D752BAEAAD4B8C79BE2C421539A0D3700902C.xkm
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event6)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Itron Powerful Receiver (/dev/input/event3)
(**) Itron Powerful Receiver: Applying InputClass "evdev pointer catchall"
(**) Itron Powerful Receiver: always reports core events
(**) Itron Powerful Receiver: Device: "/dev/input/event3"
(II) Itron Powerful Receiver: Found 9 mouse buttons
(II) Itron Powerful Receiver: Found scroll wheel(s)
(II) Itron Powerful Receiver: Found relative axes
(II) Itron Powerful Receiver: Found x and y relative axes
(II) Itron Powerful Receiver: Configuring as mouse
(**) Itron Powerful Receiver: YAxisMapping: buttons 4 and 5
(**) Itron Powerful Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Itron Powerful Receiver" (type: MOUSE)
(II) Itron Powerful Receiver: initialized for relative axes.
(II) config/udev: Adding input device Itron Powerful Receiver (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Itron Powerful Receiver (/dev/input/event4)
(**) Itron Powerful Receiver: Applying InputClass "evdev keyboard catchall"
(**) Itron Powerful Receiver: always reports core events
(**) Itron Powerful Receiver: Device: "/dev/input/event4"
(II) Itron Powerful Receiver: Found keys
(II) Itron Powerful Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Itron Powerful Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "fi"
(II) config/udev: Adding input device ASUS USB2.0 Webcam (/dev/input/event5)
(**) ASUS USB2.0 Webcam: Applying InputClass "evdev keyboard catchall"
(**) ASUS USB2.0 Webcam: always reports core events
(**) ASUS USB2.0 Webcam: Device: "/dev/input/event5"
(II) ASUS USB2.0 Webcam: Found keys
(II) ASUS USB2.0 Webcam: Configuring as keyboard
(II) XINPUT: Adding extended input device "ASUS USB2.0 Webcam" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "fi"
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "fi"
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event1)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event1"
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
(II) PSB(0): EDID vendor "ACI", prod id 9891
(II) PSB(0): Using hsync ranges from config file
(II) PSB(0): Using vrefresh ranges from config file
(II) PSB(0): Printing DDC gathered Modelines:
(II) PSB(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) PSB(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) PSB(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) PSB(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) PSB(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) PSB(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) PSB(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) PSB(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) PSB(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) PSB(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) PSB(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) PSB(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) PSB(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) PSB(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) PSB(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) PSB(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) PSB(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) PSB(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) PSB(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) PSB(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) PSB(0): EDID vendor "ACI", prod id 9891
(II) PSB(0): EDID vendor "ACI", prod id 9891
(II) PSB(0): Using hsync ranges from config file
(II) PSB(0): Using vrefresh ranges from config file
(II) PSB(0): Printing DDC gathered Modelines:
(II) PSB(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) PSB(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) PSB(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) PSB(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) PSB(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) PSB(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) PSB(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) PSB(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) PSB(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) PSB(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) PSB(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) PSB(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) PSB(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) PSB(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) PSB(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) PSB(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) PSB(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) PSB(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) PSB(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) PSB(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) PSB(0): EDID vendor "ACI", prod id 9891
(II) PSB(0): EDID vendor "ACI", prod id 9891
(II) PSB(0): Using hsync ranges from config file
(II) PSB(0): Using vrefresh ranges from config file
(II) PSB(0): Printing DDC gathered Modelines:
(II) PSB(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) PSB(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) PSB(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) PSB(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) PSB(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) PSB(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) PSB(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) PSB(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) PSB(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) PSB(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) PSB(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) PSB(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) PSB(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) PSB(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) PSB(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) PSB(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) PSB(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) PSB(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) PSB(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) PSB(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) PSB(0): EDID vendor "ACI", prod id 9891
(II) PSB(0): EDID vendor "ACI", prod id 9891
(II) PSB(0): Using hsync ranges from config file
(II) PSB(0): Using vrefresh ranges from config file
(II) PSB(0): Printing DDC gathered Modelines:
(II) PSB(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) PSB(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) PSB(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) PSB(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) PSB(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) PSB(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) PSB(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) PSB(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) PSB(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) PSB(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) PSB(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) PSB(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) PSB(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) PSB(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) PSB(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) PSB(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) PSB(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) PSB(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) PSB(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) PSB(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) PSB(0): EDID vendor "ACI", prod id 9891
(II) PSB(0): EDID vendor "ACI", prod id 9891
(II) PSB(0): Using hsync ranges from config file
(II) PSB(0): Using vrefresh ranges from config file
(II) PSB(0): Printing DDC gathered Modelines:
(II) PSB(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) PSB(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) PSB(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) PSB(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) PSB(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) PSB(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) PSB(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) PSB(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) PSB(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) PSB(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) PSB(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) PSB(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) PSB(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) PSB(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) PSB(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) PSB(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) PSB(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) PSB(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) PSB(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) PSB(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) PSB(0): EDID vendor "ACI", prod id 9891

Please help.
mikko

---

### Post by metso on 2011-08-08
hi,

I just noticed one way to restore my original screen without having to log in again due to gdm stop command:
-turn off display
-turn on display (after this the screen is all black)
-ssh into the machine and kill gnome-screensaver
-restart the screensaver with a command "DISPLAY=:0 gnome-screensaver-command"

..so starting of the gnome-screensaver wakes up the display for some reason. ..??

mikko

---

### Post by metso on 2011-08-09
Okay! I got a hint to try hitting CTRL-ALT-F1 following CTRL-ALT-F7 after turning on the display. That threw some garbage on screen but then I tried pressing CTRL-ALT-F8 and there it was, my original display!

I wanted to use a non-default resolution but after the CTRL-ALT-F8 the default kept always coming. But I got rid of that problem by changing the default resolution as instructed at [http://chrisjakeway.wordpress.com/2010/05/19/ubuntu-10-04-default-login-screen-gdm-resolution/](http://chrisjakeway.wordpress.com/2010/05/19/ubuntu-10-04-default-login-screen-gdm-resolution/)

I hope this helps someone with similar problems.

mikko

---

