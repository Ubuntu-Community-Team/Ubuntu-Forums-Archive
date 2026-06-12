---
title: "Screen panning 1360x768 Tatung 37&quot; LCD TV and S3G CX700(M2)"
date: 2007-08-06
forum: Multimedia &amp; Video
---

### Post by arnevidar on 2007-08-06
Hi
I am using Ubuntu 7.04 on VIA EPIA-EX Mini-ITX motherboard with S3G CX700(M2) graphic chipset. It is connected using DVI to a Tatung 37" LCD TV. My problem is that the signal is not filling the whole screen. I got a 5" black area on the right side of the screen, while its about 2" outside on the other side. In addition I got vertical scrolling within the window manager. Ie, I move the mouse to the right end of the screen and it will scroll the screen.

I have compiled the official source driver (cle266cn400cn-cx700cn800xorg40072-kernel-src_20061226c(20070604103608).zip) according to the official guide ([http://www.viaarena.com/Driver/via%20linux%20unichrome%20kernel%20driver%20source%20code%20installation%20guide%20v0%5B1%5D.83.gz](http://www.viaarena.com/Driver/via%20linux%20unichrome%20kernel%20driver%20source%20code%20installation%20guide%20v0%5B1%5D.83.gz)).

The modeline is created according to the TV-manual, specifying pixel clock of 85.5Mhz and a resolution of 1360x768. I am not sure about the monitors HorSync and VertSync but they should be within the specified resolution so this is not an issue (afaik). With the specified modeline the HorSync is 47.7 and vertSync is 60.

I am wondering about what this error means:

How to set default panel size?
(II) VIA(0): Unknow panel size max resolution = 1360 ! set default panel size.

My xorg.config looks like this:
```

Section "Device"
        Identifier      "Generic Video Card"
        BusID           "PCI:1:0:0"
        BoardName   "via"
        VendorName  "VIA Tech"
        Driver "via"
        Option "NoDCCValue"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
#       Option          "DPMS"
        HorizSync       30 - 70
        VertRefresh     50 - 160
        Modeline "1360x768" 85.50 1360 1440 1552 1792 768 771 777 795
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes  "1360x768"
                Depth           24
        EndSubSection
EndSection

```

dmsg |grep agpgart
```

info@info-desktop:~$ sudo dmesg|grep agpgart
[   34.684478] Linux agpgart interface v0.102 (c) Dave Jones
[   34.699544] agpgart: Detected VIA CX700 chipset
[   34.707299] agpgart: AGP aperture is 128M @ 0xd0000000
[   56.834807] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   56.835241] agpgart: Xorg tried to set rate=x12. Setting to AGP3 x8 mode.
[   56.835496] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   56.835780] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode

```

Xorg.0.log
```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux info-desktop 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(II) LoadModule: "via"
(II) Loading /usr/lib/xorg/modules/drivers//via_drv.so
(II) Module via: vendor="X.Org Foundation"
        compiled for 4.3.99.902, module version = 4.1.72
        Module class: X.Org Video Driver
(II) via: driver for VIA chipsets: CLE266, KM400/KN400, K8M800/K8N800,
        PM800/PM880/CN400, P4M800PRO, CX700, K8M890, P4M890, CN750, P4M900
(II) Primary Device is: PCI 01:00:0
(--) Chipset CX700 found
(II) Setting vga for screen 0.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 0.1.0
        ABI class: X.Org Video Driver, version 1.1
(**) VIA(0): Depth 24, (--) framebuffer bpp 32
(==) VIA(0): RGB weight 888
(==) VIA(0): Default visual is TrueColor
(II) VIA(0): MergedFB mode forced off.
(==) VIA(0): Not using video BIOS to set modes
(II) VIA(0): VESA BIOS detected
(II) VIA(0): VESA VBE Version 3.0
(II) VIA(0): VESA VBE Total Mem: 65536 kB
(II) VIA(0): VESA VBE OEM: VIA CX700
(II) VIA(0): VESA VBE OEM Software Rev: 1.0
(II) VIA(0): VESA VBE OEM Vendor:
(II) VIA(0): VESA VBE OEM Product:
(II) VIA(0): VESA VBE OEM Product Rev:
(--) VIA(0): Chipset: "CX700"
(--) VIA(0): Chipset Rev.: 0
(--) VIA(0): mapping MMIO @ 0xdd000000 with size 0x9000
(--) VIA(0): mapping BitBlt MMIO @ 0xdd200000 with size 0x200000
(--) VIA(0): mapping Integrated TV MMIO @ 0xdd00c000 with size 0x100
(II) VIA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) VIA(0): Using gamma correction (1.0, 1.0, 1.0)
(--) VIA(0): videoram =  65536k
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Reloading /usr/lib/xorg/modules//libi2c.so
(II) VIA(0): I2C bus "I2C bus 1" initialized.
(II) VIA(0): I2C bus "I2C bus 2" initialized.
(II) VIA(0): VESA VBE DDC supported
(II) VIA(0): VESA VBE DDC Level 2
(II) VIA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VIA(0): VESA VBE DDC read failed
(II) VIA(0): I2C device "I2C bus 1:ddc2" registered at address 0xA0.
(II) VIA(0): I2C device "I2C bus 1:ddc2" removed.
(--) VIA(0): No DDC signal
(II) VIA(0): Generic Monitor: Using hsync range of 30.00-113.00 kHz
(II) VIA(0): Generic Monitor: Using vrefresh range of 50.00-160.00 Hz
(II) VIA(0): Clock range:  20.00 to 270.00 MHz
(II) VIA(0): Not using default mode "640x350" (vertical timing out of range)
(II) VIA(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "640x400" (vertical timing out of range)
(II) VIA(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "720x400" (vertical timing out of range)
(II) VIA(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1024x768" (vertical timing out of range)
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "832x624" (horizontal timing out of range)
(II) VIA(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1152x768" (vertical timing out of range)
(II) VIA(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) VIA(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) VIA(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) VIA(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) VIA(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) VIA(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) VIA(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) VIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) VIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) VIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) VIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) VIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) VIA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) VIA(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) VIA(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) VIA(0): Not using default mode "1440x900" (width too large for virtual size)
(II) VIA(0): Not using default mode "1280x960" (height too large for virtual size)
(II) VIA(0): Not using default mode "1280x960" (height too large for virtual size)
(II) VIA(0): Not using default mode "1280x800" (height too large for virtual size)
(II) VIA(0): Not using default mode "1152x864" (height too large for virtual size)
(II) VIA(0): Not using default mode "1152x864" (height too large for virtual size)
(--) VIA(0): Virtual size is 1360x768 (pitch 1360)
(**) VIA(0): *Mode "1360x768": 85.5 MHz, 47.7 kHz, 60.0 Hz
(II) VIA(0): Modeline "1360x768"   85.50  1360 1440 1552 1792  768 771 777 795
(**) VIA(0):  Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(II) VIA(0): Modeline "1280x768"   80.14  1280 1344 1480 1680  768 769 772 795
(**) VIA(0):  Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) VIA(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
(**) VIA(0):  Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) VIA(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) VIA(0):  Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) VIA(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) VIA(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) VIA(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) VIA(0):  Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) VIA(0): Modeline "800x600"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
(**) VIA(0):  Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) VIA(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) VIA(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) VIA(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) VIA(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) VIA(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) VIA(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) VIA(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) VIA(0):  Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) VIA(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 -hsync -vsync
(**) VIA(0):  Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) VIA(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) VIA(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) VIA(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 -hsync -vsync
(**) VIA(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) VIA(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
(==) VIA(0): DPI set to (75, 75)
(II) VIA(0): I2C device "I2C bus 2:EDID1" registered at address 0xA0.
(II) VIA(0): I2C device "I2C bus 2:EDID1" removed.
(II) VIA(0): I2C device "I2C bus 2:EDID1" registered at address 0xA0.
(II) VIA(0): I2C device "I2C bus 2:EDID1" removed.
(II) VIA(0): I2C device "I2C bus 2:ddc2" registered at address 0xA0.
(II) VIA(0): I2C device "I2C bus 2:ddc2" removed.
(II) VIA(0): Manufacturer: TAT  Model: 23e9  Serial#: 24
(II) VIA(0): Year: 2007  Week: 28
(II) VIA(0): EDID Version: 1.3
(II) VIA(0): Digital Display Input
(II) VIA(0): DFP 1.x compatible TMDS
(II) VIA(0): Max H-Image Size [cm]: horiz.: 82  vert.: 46
(II) VIA(0): Gamma: 2.20
(II) VIA(0): DPMS capabilities: Off; RGB/Color Display
(II) VIA(0): First detailed timing is preferred mode
(II) VIA(0): redX: 0.650 redY: 0.331   greenX: 0.270 greenY: 0.590
(II) VIA(0): blueX: 0.142 blueY: 0.068   whiteX: 0.285 whiteY: 0.293
(II) VIA(0): Supported VESA Video Modes:
(II) VIA(0): 720x400@70Hz
(II) VIA(0): 640x480@60Hz
(II) VIA(0): 640x480@67Hz
(II) VIA(0): 800x600@56Hz
(II) VIA(0): 800x600@60Hz
(II) VIA(0): 1024x768@60Hz
(II) VIA(0): 1024x768@70Hz
(II) VIA(0): 1024x768@75Hz
(II) VIA(0): Manufacturer's mask: 0
(II) VIA(0): Supported additional Video Mode:
(II) VIA(0): clock: 85.5 MHz   Image Size:  697 x 392 mm
(II) VIA(0): h_active: 1360  h_sync: 1424  h_sync_end 1536 h_blank_end 1792 h_border: 0
(II) VIA(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 795 v_border: 0
(II) VIA(0): Ranges: V min: 56  V max: 76 Hz, H min: 31  H max: 61 kHz, PixClock max 100 MHz
(II) VIA(0): Serial No: EVK7283A0024
(II) VIA(0): Monitor name: V37MCGI
(II) VIA(0): EDID (in hex):
(II) VIA(0):    00ffffffffffff005034e92318000000
(II) VIA(0):    1c11010381522e782ab060a654459724
(II) VIA(0):    11494bb30e0001010101010101010101
(II) VIA(0):    010101010101662150b051001b304070
(II) VIA(0):    3600b9882100001e000000fd00384c1f
(II) VIA(0):    3d0a000a202020202020000000ff0045
(II) VIA(0):    564b3732383341303032340a000000fc
(II) VIA(0):    005633374d4347490a20202020200080
(II) VIA(0): Using hsync ranges from config file
(II) VIA(0): Using vrefresh ranges from config file
(II) VIA(0): Printing DDC gathered Modelines:
(II) VIA(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) VIA(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) VIA(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) VIA(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) VIA(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) VIA(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) VIA(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) VIA(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) VIA(0): Modeline "1360x768"   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync
(II) VIA(0): Unknow panel size max resolution = 1360 ! set default panel size.
(II) VIA(0): I2C device "I2C bus 2:EDID1" registered at address 0xA0.
(II) VIA(0): I2C device "I2C bus 2:EDID1" removed.
(**) VIA(0): Option: Cap0 auto detect= 0
(**) VIA(0): Option: Cap1 auto detect= 0
(**) VIA(0): Option: Cap0_FieldSwap Disabled
(**) VIA(0): Option: Cap0_HFilter Enabled
(**) VIA(0): Option: Cap1_HFilter Enabled
(**) VIA(0): Option: Capture Over Scan ON
(**) VIA(0): Option: HQV Filter Manual Select Disabled
(**) VIA(0): Option: Set MPEG decode frame buffer number Disable
(**) VIA(0): Option: Capture 1 use H/W auto flip
(**) VIA(0): Option: Capture 0 use V1 engine : Default path
(**) VIA(0): Option: HQV Manual Switch Disabled
(**) VIA(0): Option: No mpeg add one line on bottom = 0
(**) VIA(0): Option: DeBlocking Disable!!
(**) VIA(0): DeBlocking Minimum Width Default : 320
(**) VIA(0): DeBlocking Minimum Height Default: 240
(**) VIA(0): Option: Use 2D BitBlt method to write event-tag into VQ and make sure MPEG decode END Disable
(II) VIALoadVideoOption
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(--) VIA(0): mapping framebuffer @ 0xa0000000 with size 0x4000000
(==) VIA(0): Write-combining range (0xa0000000,0x4000000)
(--) VIA(0): Frame buffer start: 0xb3788000, free start: 0x3fc000 end: 0x4000000
(--) VIA(0): mapping MMIO @ 0xdd000000 with size 0x9000
(--) VIA(0): mapping BitBlt MMIO @ 0xdd200000 with size 0x200000
(--) VIA(0): mapping Integrated TV MMIO @ 0xdd00c000 with size 0x100
(II) VIA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(EE) VIA(0):  Couldn't open "/dev/video2"
(II) VIA(0): VIAScreenInit : V4L Disabled : fd2 = -1
(II) VIA(0): I2C device "I2C bus 2:TV" registered at address 0x40.
(II) VIA(0): I2C device "I2C bus 2:TV" removed.
(II) VIA(0): CRT Max Resolution 1024x768, set virtual desktop!!
(II) VIA(0): DFP Max Resolution 1024x768, set virtual desktop!!
(II) VIA(0): I2C device "I2C bus 2:TV" registered at address 0x40.
(II) VIA(0): I2C device "I2C bus 2:TV" removed.
(II) VIA(0): I2C device "I2C bus 2:TV" registered at address 0x40.
(II) VIA(0): I2C device "I2C bus 2:TV" removed.
(II) VIA(0): 3D Engine has been initilized.
(EE) VIA(0):  Couldn't open "/dev/video2"
(II) VIA(0): [drm] DRM interface version 1.3
(II) VIA(0): [drm] created "via" driver at busid "PCI:1:0:0"
(II) VIA(0): [drm] added 8192 byte SAREA at 0xdcc4d000
(II) VIA(0): [drm] mapped SAREA 0xdcc4d000 to 0xb3786000
(II) VIA(0): [drm] framebuffer handle = 0xa0000000
(II) VIA(0): [drm] added 1 reserved context for kernel
(II) VIA(0): [drm] drmAgpEnabled succeeded
(II) VIA(0): [drm] agpAddr = 0xd0000000
(II) VIA(0): [drm] agpBase = 0x00000000
(II) VIA(0): [drm] agpAddr = 0xd0000000
(II) VIA(0): [drm] agpSize = 0x02000000
(II) VIA(0): [drm] agp physical addr = 0x00000000
(II) VIA(0): [dri] use agp.
(II) VIA(0): [dri] frame buffer initialized.
(II) VIA(0): [dri] visual configs initialized.
(II) VIA(0): [drm] register handle = 0xdd000000
(II) VIA(0): [drm] mmio Registers = 0xdd000000
(II) VIA(0): [dri] mmio maped.
(II) VIA(0): VIAInternalScreenInit
(II) VIA(0): Frame Buffer From (0,0) To (1360,1153)
(II) VIA(0): Using 1153 lines for offscreen memory.
(II) VIA(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        8x8 mono pattern filled rectangles
        8x8 color pattern filled rectangles
        CPU to Screen color expansion
        Solid Lines
        Dashed Lines
        Image Writes
        Offscreen Pixmaps
        Setting up tile and stipple cache:
                30 128x128 slots
                32 8x8 color pattern slots
(II) VIA(0): [drm] FBFreeStart= 0x005fb540 FBFreeEnd= 0x03cbe000 FBSize= 0x036c2ac0
(==) VIA(0): Backing store disabled
(==) VIA(0): Silken mouse enabled
(II) VIA(0): X context handle = 0x1
(II) VIA(0): [drm] installed DRM signal handler
(II) VIA(0): [DRI] installation complete
(II) VIA(0): [dri] kernel data initilized.
(II) VIA(0): direct rendering enabled
(WW) VIA(0): Option "NoDCCValue" is not used

```

---

### Post by arnevidar on 2007-08-06
Reading the Installation.txt part 2.5 it sais the following
2.5 LCD support
2.5.3 Supported Panel Size & Mode
a. Panel Size - 640x480
b. Panel Size - 800x600
c. Panel Size - 1024x768
mode:
640x480, 800x600 -
support "Expand" and "Center" mode

1024x768 -
support

1280x768, 1280x800, 1280x960, 1280x1024, 1360x768,
1366x768, 1400x1050, 1600x1200, 1920x1080, 1920x1440 -
support virtual desktop mode

d. Panel Size - 1280x1024
e. Panel Size - 1600x1200

Virtual desktop mode running 1360x768 while the real resolution is 1024x768 doesn't help me a bit!
PLEASE say it is a way to work around this.

---

