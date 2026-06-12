---
title: "Intel graphics i815"
date: 2006-06-23
forum: Multimedia &amp; Video
---

### Post by nilou on 2006-06-23
I would like to make my monitor work in 1280 1024 @ 60 hz (1024 768 @ 85 hz) but the display contains vertical white lines spaced equally across my monitor.

Hope someone can give a clue...

files now contains following:
xorg.conf:
Section "Device"
        Identifier      "Intel Corporation 82815 CGC [Chipset Graphics Controller]"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-67
        VertRefresh     50-160



  # 1024x768 @ 75.00 Hz (GTF) hsync: 60.15 kHz; pclk: 81.80 MHz
  Modeline "1024x768_75.00"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync

 # 1024x768 @ 85.00 Hz (GTF) hsync: 68.60 kHz; pclk: 94.39 MHz
  Modeline "1024x768_85.00"  94.39  1024 1088 1200 1376  768 769 772 807  -HSync +Vsync

 # 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
  Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060 -HSync +Vsync


EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82815 CGC [Chipset Graphics Controller]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024_60.00" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024_60.00" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024_60.00" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024_60.00" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024_60.00" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024_60.00" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

 .xsession-errors:
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "mich"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/DinoData-10:/tmp/.ICE-unix/7244

(gnome-panel:7311): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(gnome-panel:7311): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -15 and height 24
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

 /var/log/Xorg.0.log:
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
        compiled for 4.3.99.902, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
        i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, E7221 (i915),
        915GM, 945G, 945GM
(II) Primary Device is: PCI 00:02:0
(--) Chipset i815 found
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x40000000 - 0x40000fff (0x1000) MX[B]
        [5] -1  0       0x40300000 - 0x4037ffff (0x80000) MX[B](B)
        [6] -1  0       0x44000000 - 0x47ffffff (0x4000000) MX[B](B)
        [7] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [8] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
        [9] -1  0       0x00001000 - 0x0000103f (0x40) IX[B]
        [10] -1 0       0x00002400 - 0x0000243f (0x40) IX[B]
        [11] -1 0       0x00002000 - 0x000020ff (0x100) IX[B]
        [12] -1 0       0x00002440 - 0x0000245f (0x20) IX[B]
        [13] -1 0       0x00002460 - 0x0000246f (0x10) IX[B]
(II) resource ranges after probing:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x40000000 - 0x40000fff (0x1000) MX[B]
        [5] -1  0       0x40300000 - 0x4037ffff (0x80000) MX[B](B)
        [6] -1  0       0x44000000 - 0x47ffffff (0x4000000) MX[B](B)
        [7] 0   0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [8] 0   0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [9] 0   0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [10] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [11] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [12] -1 0       0x00001000 - 0x0000103f (0x40) IX[B]
        [13] -1 0       0x00002400 - 0x0000243f (0x40) IX[B]
        [14] -1 0       0x00002000 - 0x000020ff (0x100) IX[B]
        [15] -1 0       0x00002440 - 0x0000245f (0x20) IX[B]
        [16] -1 0       0x00002460 - 0x0000246f (0x10) IX[B]
        [17] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [18] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 0.1.0
        ABI class: X.Org Video Driver, version 0.8
(**) I810(0): Depth 24, (--) framebuffer bpp 24
(==) I810(0): RGB weight 888
(==) I810(0): Default visual is TrueColor
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.2.0
        ABI class: X.Org Video Driver, version 0.8
(**) I810(0): DRI is disabled because it runs only at 16-bit depth.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules/libvbe.so
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) I810(0): initializing int10
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 1024 kB
(II) I810(0): VESA VBE OEM: Intel(R) 815 Chipset Video BIOS
(II) I810(0): VESA VBE OEM Software Rev: 4.1
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(R) 815 Chipset
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) I810(0): VESA VBE DDC supported
(II) I810(0): VESA VBE DDC Level none
(II) I810(0): VESA VBE DDC transfer in appr. 0 sec.
(II) I810(0): VESA VBE DDC read failed
(--) I810(0): Chipset: "i815"
(--) I810(0): Linear framebuffer at 0x44000000
(--) I810(0): IO registers at addr 0x40300000
(II) I810(0): Kernel reported 82176 total, 1 used
(II) I810(0): I810CheckAvailableMemory: 328700k available
(==) I810(0): Will alloc AGP framebuffer: 8192 kByte
(==) I810(0): Using gamma correction (1.0, 1.0, 1.0)
(II) I810(0): Generic Monitor: Using hsync range of 30.00-67.00 kHz
(II) I810(0): Generic Monitor: Using vrefresh range of 50.00-160.00 Hz
(II) I810(0): Clock range:   9.50 to 136.00 MHz
(II) I810(0): Not using mode "1024x768_85.00" (hsync out of range)
(II) I810(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1024x768" (unknown reason)
(II) I810(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1024x768" (hsync out of range)
(II) I810(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1280x1024" (hsync out of range)
(II) I810(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1152x864" (hsync out of range)
(II) I810(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) I810(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) I810(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) I810(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) I810(0): Not using default mode "1440x900" (width too large for virtual size)
(--) I810(0): Virtual size is 1280x1024 (pitch 2048)
(**) I810(0): *Mode "1280x1024_60.00": 108.9 MHz, 63.6 kHz, 60.0 Hz
(II) I810(0): Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060 -hsync +vsync
(**) I810(0): *Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) I810(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(**) I810(0): *Default mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) I810(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) I810(0): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) I810(0): Modeline "800x600"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
(**) I810(0): *Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) I810(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 -hsync -vsync
(**) I810(0):  Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(II) I810(0): Modeline "1280x960"  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync
(**) I810(0):  Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(II) I810(0): Modeline "1280x800"   83.46  1280 1344 1480 1680  800 801 804 828
(**) I810(0):  Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) I810(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(**) I810(0):  Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(II) I810(0): Modeline "1280x768"   80.14  1280 1344 1480 1680  768 769 772 795
(**) I810(0):  Default mode "1152x768": 65.0 MHz, 44.2 kHz, 54.8 Hz
(II) I810(0): Modeline "1152x768"   65.00  1152 1178 1314 1472  768 771 777 806 +hsync +vsync
(**) I810(0):  Mode "1024x768_75.00": 81.8 MHz, 60.1 kHz, 75.0 Hz
(II) I810(0): Modeline "1024x768_75.00"   81.80  1024 1080 1192 1360  768 769 772 802 -hsync +vsync
(**) I810(0):  Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) I810(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) I810(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) I810(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) I810(0):  Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) I810(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) I810(0):  Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) I810(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) I810(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) I810(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) I810(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) I810(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) I810(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) I810(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) I810(0):  Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) I810(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) I810(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) I810(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(**) I810(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) I810(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) I810(0):  Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) I810(0): Modeline "720x400"   35.50  720 756 828 936  400 401 404 446 -hsync +vsync
(**) I810(0):  Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) I810(0): Modeline "640x400"   31.50  640 672 736 832  400 401 404 445 -hsync +vsync
(**) I810(0):  Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) I810(0): Modeline "640x350"   31.50  640 672 736 832  350 382 385 445 +hsync -vsync
(==) I810(0): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 0.1.0
        ABI class: X.Org Video Driver, version 0.8
(II) I810(0): XvMC is Disabled: use XvMCSurfaces config option to enable.
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] 0   0       0x40300000 - 0x4037ffff (0x80000) MS[B]
        [1] 0   0       0x44000000 - 0x47ffffff (0x4000000) MS[B]
        [2] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [3] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [4] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [5] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [6] -1  0       0x40000000 - 0x40000fff (0x1000) MX[B]
        [7] -1  0       0x40300000 - 0x4037ffff (0x80000) MX[B](B)
        [8] -1  0       0x44000000 - 0x47ffffff (0x4000000) MX[B](B)
        [9] 0   0       0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
        [10] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
        [11] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
        [12] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [13] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [14] -1 0       0x00001000 - 0x0000103f (0x40) IX[B]
        [15] -1 0       0x00002400 - 0x0000243f (0x40) IX[B]
        [16] -1 0       0x00002000 - 0x000020ff (0x100) IX[B]
        [17] -1 0       0x00002440 - 0x0000245f (0x20) IX[B]
        [18] -1 0       0x00002460 - 0x0000246f (0x10) IX[B]
        [19] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
        [20] 0  0       0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) I810(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) I810(0): Setting dot clock to 108.9 MHz [ 0x39 0xb 0x20 ] [ 59 13 2 ]
(II) I810(0): chose watermark 0x22418000: (tab.freq 121.0)
(II) I810(0): xf86BindGARTMemory: bind key 0 at 0x00000000 (pgoffset 0)
(II) I810(0): xf86BindGARTMemory: bind key 1 at 0x00800000 (pgoffset 2048)
(II) I810(0): xf86BindGARTMemory: bind key 2 at 0x00c00000 (pgoffset 3072)
(II) I810(0): Allocated of 4096 bytes for HW cursor
(II) I810(0): xf86BindGARTMemory: bind key 3 at 0x00c01000 (pgoffset 3073)
(II) I810(0): Allocated of 16384 bytes for ARGB HW cursor
(II) I810(0): Adding 256 scanlines for pixmap caching
(II) I810(0): Allocated Scratch Memory
(II) I810(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        8x8 mono pattern filled rectangles
        Indirect CPU to Screen color expansion
        Solid Horizontal and Vertical Lines
        Offscreen Pixmaps
        Setting up tile and stipple cache:
                32 128x128 slots
                12 256x256 slots
(==) I810(0): Backing store disabled
(==) I810(0): Silken mouse enabled
(**) Option "dpms"
(**) I810(0): DPMS enabled
(WW) I810(0): Direct rendering disabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
error opening security policy file /etc/X11/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "dk"
(**) Generic Keyboard: XkbLayout: "dk"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
AUDIT: Fri Jun 23 23:44:44 2006: 7232 X: client 1 rejected from local host
AUDIT: Fri Jun 23 23:44:44 2006: 7232 X: client 2 rejected from local host
AUDIT: Fri Jun 23 23:44:44 2006: 7232 X: client 3 rejected from local host
(II) I810(0): Setting dot clock to 78.9 MHz [ 0x15 0x5 0x20 ] [ 23 7 2 ]
(II) I810(0): chose watermark 0x22215000: (tab.freq 78.8)
(II) I810(0): Setting dot clock to 56.3 MHz [ 0x3b 0xb 0x30 ] [ 61 13 3 ]
(II) I810(0): chose watermark 0x22111000: (tab.freq 56.3)
(II) I810(0): Setting dot clock to 36.0 MHz [ 0x10 0x1 0x40 ] [ 18 3 4 ]
(II) I810(0): chose watermark 0x2210c000: (tab.freq 36.0)
(II) I810(0): Setting dot clock to 56.3 MHz [ 0x3b 0xb 0x30 ] [ 61 13 3 ]
(II) I810(0): chose watermark 0x22111000: (tab.freq 56.3)
(II) I810(0): Setting dot clock to 78.9 MHz [ 0x15 0x5 0x20 ] [ 23 7 2 ]
(II) I810(0): chose watermark 0x22215000: (tab.freq 78.8)

---

### Post by jonny on 2006-06-24
Never seen this exact problem, but I imagine you've tried using the 915 resolution package from Universe?  That solves a lot of resolution issues with Intel video cards.  Once you've installed it, try doing sudo dpkg-reconfigure xserver-xorg

---

### Post by H.E. Pennypacker on 2006-06-25
I have the Intel i915 card, and I also have an issue with vertical lines spaced equally apart.  These vertical lines only show up when booting, and disappear before log-in.

I already have the i810 family driver package installed via Synaptic, and I just found the 915resolution package (that's its name in Synaptic, "915resolution" - search for it).  I hope this solves that problem.

Moreover, I already changed Xorg from VESA to i810.

---

### Post by tibiker1966 on 2008-04-29
For what it's worth - I "fixed" the problem by changing the default color depth in my xorg.conf package from "24" to "16".

(I'm running an i815-based system and had the same visual issues).

Good luck.

-K

---

### Post by tibiker1966 on 2008-04-29
> **tibiker1966 said:**
> For what it's worth - I "fixed" the problem by changing the default color depth in my xorg.conf package from "24" to "16".

(I'm running an i815-based system and had the same visual issues).

Good luck.

-K


Ahh - more detail:   The "official" way to modify the default color depth is by using the "sudo dpkg-reconfigure xserver-xorg" command, and specifying a color depth of 16.   Do this rather than editing the xorg.conf directly, so the change you make will be preserved across an update to the xserver-xorg package.

Or so I've read - I'll try it when I get home tomorrow and update this post if it needs correcting.

The pleasant side effect of this change: apparently 3D acceleration is supported at depth 16, not 24 (again, need to confirm).

---

