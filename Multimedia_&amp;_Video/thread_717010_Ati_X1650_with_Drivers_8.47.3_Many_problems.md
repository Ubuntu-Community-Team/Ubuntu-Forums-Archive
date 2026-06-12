---
title: "Ati X1650 with Drivers 8.47.3: Many problems"
date: 2008-03-06
forum: Multimedia &amp; Video
---

### Post by MadeR on 2008-03-06
Basicly overlayed and opengl windows have problems:
I can see digital tv or a movie with kaffeine or use my Creative Optia ONLY with kopete 3.5.x, but I cannot use any opengl program, use the webcam with skype or kopete 4.x or games like planeshift or fgl_glxgears or frets on fire.

The window, contains a copy of the background, the program runs, without hanging or crashing, simply no output.

fglrxinfo
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1650 Series
OpenGL version string: 2.1.7412 Release
```

xorg.conf
```
Section "ServerLayout"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
        Option      "XkbVariant" "alt-intl"
        Option      "XkbOptions" "lv3:ralt_switch,compose:rwin"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ImPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "stylus"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "eraser"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "cursor"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier   "Acer AL732"
        Option      "DPMS"      "on"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "false"
EndSection

Section "Device"
        Identifier  "Generic Video Card"
        Driver      "vesa"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
#       Option      "VideoOverlay" "off"
#       Option      "OpenGLOverlay" "on"
#       Option      "DynamicClocks" "false"
#       Option      "TexturedVideo" "on"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "Generic Video Card"
        Monitor    "Acer AL732"
        DefaultDepth     24
        SubSection "Display"
                Modes    "1280x1024"
#"1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection
```

xvinfo
```
X-Video Extension version 2.2
screen #0
  Adaptor #0: "ATI Radeon AVIVO Video"
    number of ports: 4
    port base: 131
    operations supported: PutImage
    supported visuals:
      depth 24, visualID 0x23
      depth 24, visualID 0x24
      depth 24, visualID 0x25
      depth 24, visualID 0x26
      depth 24, visualID 0x27
      depth 24, visualID 0x28
      depth 24, visualID 0x29
      depth 24, visualID 0x2a
      depth 24, visualID 0x2b
      depth 24, visualID 0x2c
      depth 24, visualID 0x2d
      depth 24, visualID 0x2e
      depth 24, visualID 0x2f
      depth 24, visualID 0x30
      depth 24, visualID 0x31
      depth 24, visualID 0x32
      depth 24, visualID 0x33
      depth 24, visualID 0x34
      depth 24, visualID 0x35
      depth 24, visualID 0x36
      depth 24, visualID 0x37
      depth 24, visualID 0x38
      depth 24, visualID 0x39
      depth 24, visualID 0x3a
      depth 24, visualID 0x3b
      depth 24, visualID 0x3c
      depth 24, visualID 0x3d
      depth 24, visualID 0x3e
      depth 24, visualID 0x3f
      depth 24, visualID 0x40
      depth 24, visualID 0x41
      depth 24, visualID 0x42
      depth 24, visualID 0x43
      depth 24, visualID 0x44
      depth 24, visualID 0x45
      depth 24, visualID 0x46
      depth 24, visualID 0x47
      depth 24, visualID 0x48
      depth 24, visualID 0x49
      depth 24, visualID 0x4a
      depth 24, visualID 0x4b
      depth 24, visualID 0x4c
      depth 24, visualID 0x4d
      depth 24, visualID 0x4e
      depth 24, visualID 0x4f
      depth 24, visualID 0x50
      depth 24, visualID 0x51
      depth 24, visualID 0x52
      depth 24, visualID 0x53
      depth 24, visualID 0x54
      depth 24, visualID 0x55
      depth 24, visualID 0x56
      depth 24, visualID 0x57
      depth 24, visualID 0x58
      depth 24, visualID 0x59
      depth 24, visualID 0x5a
      depth 24, visualID 0x5b
      depth 24, visualID 0x5c
      depth 24, visualID 0x5d
      depth 24, visualID 0x5e
      depth 24, visualID 0x5f
      depth 24, visualID 0x60
      depth 24, visualID 0x61
      depth 24, visualID 0x62
      depth 24, visualID 0x63
      depth 24, visualID 0x64
      depth 24, visualID 0x65
      depth 24, visualID 0x66
      depth 24, visualID 0x67
      depth 24, visualID 0x68
      depth 24, visualID 0x69
      depth 24, visualID 0x6a
      depth 24, visualID 0x6b
      depth 24, visualID 0x6c
      depth 24, visualID 0x6d
      depth 24, visualID 0x6e
      depth 24, visualID 0x6f
      depth 24, visualID 0x70
      depth 24, visualID 0x71
      depth 24, visualID 0x72
    number of attributes: 10
      "XV_SET_DEFAULTS" (range 0 to 1)
              client settable attribute
      "XV_DOUBLE_BUFFER" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
      "XV_BRIGHTNESS" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_CONTRAST" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_SATURATION" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_COLOR" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_HUE" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_RED_INTENSITY" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_GREEN_INTENSITY" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_BLUE_INTENSITY" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
    maximum XvImage size: 4096 x 4096
    Number of image formats: 2
      id: 0x32315659 (YV12)
        guid: 59563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x30323449 (I420)
        guid: 49343230-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
```

Do you need other files?

---

### Post by kellemes on 2008-03-06
Please also post /var/log/Xorg.0.log

Not sure if I can help, probably not since I have the same card and still using "fglrx-version-veryveryold" because all the others don't work.. ;-)
By the way, is this an AGP version?

---

### Post by MadeR on 2008-03-06
Yes AGP version.

ati control center
[IMG]http://www.massimilianodellarovere.eu/bildoj/ceterajxoj/aticc.png[/IMG]

/var/log/Xorg.0.log
```
X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux silmarillion 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686
Build Date: 18 January 2008
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Mar  6 20:57:59 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig-Screen[0]" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]"
(**) |   |-->Device "aticonfig-Device[0]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
        Entry deleted from font path.
(==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81e9800
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.3
        X.Org Video Driver: 1.2
        X.Org XInput driver : 0.7
        X.Org Server Extension : 0.3
        X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2570 card 17f2,2570 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2571 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24d2 card 17f2,24d2 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 17f2,24d2 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24d7 card 17f2,24d2 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,24de card 17f2,24d2 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24dd card 17f2,24dd rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24db card 17f2,24d2 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,24d1 card 17f2,24d1 rev 02 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,24d3 card 17f2,24d2 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24d5 card 17f2,2405 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 1002,71c6 card 174b,0850 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,71e6 card 174b,0851 rev 00 class 03,80,00 hdr 00
(II) PCI: 02:00:0: chip 11ab,4320 card 17f2,1c03 rev 13 class 02,00,00 hdr 00
(II) PCI: 02:07:0: chip 104c,9066 card 1186,3b04 rev 00 class 02,80,00 hdr 00
(II) PCI: 02:0a:0: chip 1131,7133 card 11bd,002f rev d1 class 04,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[b]
(II) Bus 0 prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[b]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
        [0] -1  0       0x00009000 - 0x000090ff (0x100) IX[b]
        [1] -1  0       0x00009400 - 0x000094ff (0x100) IX[b]
        [2] -1  0       0x00009800 - 0x000098ff (0x100) IX[b]
        [3] -1  0       0x00009c00 - 0x00009cff (0x100) IX[b]
(II) Bus 1 non-prefetchable memory range:
        [0] -1  0       0xd0000000 - 0xefffffff (0x20000000) MX[b]
(II) Bus 1 prefetchable memory range:
        [0] -1  0       0x88000000 - 0x880fffff (0x100000) MX[b]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
        [0] -1  0       0x0000a000 - 0x0000a0ff (0x100) IX[b]
        [1] -1  0       0x0000a400 - 0x0000a4ff (0x100) IX[b]
        [2] -1  0       0x0000a800 - 0x0000a8ff (0x100) IX[b]
        [3] -1  0       0x0000ac00 - 0x0000acff (0x100) IX[b]
(II) Bus 2 non-prefetchable memory range:
        [0] -1  0       0xf0000000 - 0xf1ffffff (0x2000000) MX[b]
(II) Bus 2 prefetchable memory range:
        [0] -1  0       0x88100000 - 0x881fffff (0x100000) MX[b]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc RV530LE [Radeon X1600] rev 0, Mem @ 0xd0000000/28, 0xe1000000/16, I/O @ 0x9000/8
(--) PCI: (1:0:1) ATI Technologies Inc unknown chipset (0x71e6) rev 0, Mem @ 0xe1010000/16
(II) Addressable bus resource ranges are
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[b]
        [1] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) OS-reported resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[b]
(II) PCI Memory resource overlap reduced 0xc0000000 from 0xcfffffff to 0xbfffffff
(II) Active PCI resource ranges:
        [0] -1  0       0xf1026000 - 0xf10267ff (0x800) MX[b]
        [1] -1  0       0xf1000000 - 0xf101ffff (0x20000) MX[b]
        [2] -1  0       0xf1024000 - 0xf1025fff (0x2000) MX[b]
        [3] -1  0       0xf1020000 - 0xf1023fff (0x4000) MX[b]
        [4] -1  0       0xf2002000 - 0xf20020ff (0x100) MX[b]
        [5] -1  0       0xf2001000 - 0xf20011ff (0x200) MX[b]
        [6] -1  0       0x88200000 - 0x882003ff (0x400) MX[b]
        [7] -1  0       0xf2000000 - 0xf20003ff (0x400) MX[b]
        [8] -1  0       0xc0000000 - 0xbfffffff (0x0) MX[b]O
        [9] -1  0       0xe1000000 - 0xe100ffff (0x10000) MX[b](B)
        [10] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
        [11] -1 0       0x0000a000 - 0x0000a0ff (0x100) IX[b]
        [12] -1 0       0x0000dc00 - 0x0000dc3f (0x40) IX[b]
        [13] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[b]
        [14] -1 0       0x00000500 - 0x0000051f (0x20) IX[b]
        [15] -1 0       0x0000d000 - 0x0000d00f (0x10) IX[b]
        [16] -1 0       0x0000cc00 - 0x0000cc03 (0x4) IX[b]
        [17] -1 0       0x0000c800 - 0x0000c807 (0x8) IX[b]
        [18] -1 0       0x0000c400 - 0x0000c403 (0x4) IX[b]
        [19] -1 0       0x0000c000 - 0x0000c007 (0x8) IX[b]
        [20] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[b]
        [21] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[b]
        [22] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[b]
        [23] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[b]
        [24] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[b]
        [25] -1 0       0x0000b800 - 0x0000b81f (0x20) IX[b]
        [26] -1 0       0x0000b400 - 0x0000b41f (0x20) IX[b]
        [27] -1 0       0x0000b000 - 0x0000b01f (0x20) IX[b]
        [28] -1 0       0x0000bc00 - 0x0000bc1f (0x20) IX[b]
        [29] -1 0       0x00009000 - 0x000090ff (0x100) IX[b](B)
(II) Inactive PCI resource ranges:
        [0] -1  0       0xe1010000 - 0xe101ffff (0x10000) MX[b](B)
(II) Active PCI resource ranges after removing overlaps:
        [0] -1  0       0xf1026000 - 0xf10267ff (0x800) MX[b]
        [1] -1  0       0xf1000000 - 0xf101ffff (0x20000) MX[b]
        [2] -1  0       0xf1024000 - 0xf1025fff (0x2000) MX[b]
        [3] -1  0       0xf1020000 - 0xf1023fff (0x4000) MX[b]
        [4] -1  0       0xf2002000 - 0xf20020ff (0x100) MX[b]
        [5] -1  0       0xf2001000 - 0xf20011ff (0x200) MX[b]
        [6] -1  0       0x88200000 - 0x882003ff (0x400) MX[b]
        [7] -1  0       0xf2000000 - 0xf20003ff (0x400) MX[b]
        [8] -1  0       0xc0000000 - 0xbfffffff (0x0) MX[b]O
        [9] -1  0       0xe1000000 - 0xe100ffff (0x10000) MX[b](B)
        [10] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
        [11] -1 0       0x0000a000 - 0x0000a0ff (0x100) IX[b]
        [12] -1 0       0x0000dc00 - 0x0000dc3f (0x40) IX[b]
        [13] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[b]
        [14] -1 0       0x00000500 - 0x0000051f (0x20) IX[b]
        [15] -1 0       0x0000d000 - 0x0000d00f (0x10) IX[b]
        [16] -1 0       0x0000cc00 - 0x0000cc03 (0x4) IX[b]
        [17] -1 0       0x0000c800 - 0x0000c807 (0x8) IX[b]
        [18] -1 0       0x0000c400 - 0x0000c403 (0x4) IX[b]
        [19] -1 0       0x0000c000 - 0x0000c007 (0x8) IX[b]
        [20] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[b]
        [21] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[b]
        [22] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[b]
        [23] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[b]
        [24] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[b]
        [25] -1 0       0x0000b800 - 0x0000b81f (0x20) IX[b]
        [26] -1 0       0x0000b400 - 0x0000b41f (0x20) IX[b]
        [27] -1 0       0x0000b000 - 0x0000b01f (0x20) IX[b]
        [28] -1 0       0x0000bc00 - 0x0000bc1f (0x20) IX[b]
        [29] -1 0       0x00009000 - 0x000090ff (0x100) IX[b](B)
(II) Inactive PCI resource ranges after removing overlaps:
        [0] -1  0       0xe1010000 - 0xe101ffff (0x10000) MX[b](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[b]
(II) All system resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [4] -1  0       0xf1026000 - 0xf10267ff (0x800) MX[b]
        [5] -1  0       0xf1000000 - 0xf101ffff (0x20000) MX[b]
        [6] -1  0       0xf1024000 - 0xf1025fff (0x2000) MX[b]
        [7] -1  0       0xf1020000 - 0xf1023fff (0x4000) MX[b]
        [8] -1  0       0xf2002000 - 0xf20020ff (0x100) MX[b]
        [9] -1  0       0xf2001000 - 0xf20011ff (0x200) MX[b]
        [10] -1 0       0x88200000 - 0x882003ff (0x400) MX[b]
        [11] -1 0       0xf2000000 - 0xf20003ff (0x400) MX[b]
        [12] -1 0       0xc0000000 - 0xbfffffff (0x0) MX[b]O
        [13] -1 0       0xe1000000 - 0xe100ffff (0x10000) MX[b](B)
        [14] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
        [15] -1 0       0xe1010000 - 0xe101ffff (0x10000) MX[b](B)
        [16] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [17] -1 0       0x00000000 - 0x000000ff (0x100) IX[b]
        [18] -1 0       0x0000a000 - 0x0000a0ff (0x100) IX[b]
        [19] -1 0       0x0000dc00 - 0x0000dc3f (0x40) IX[b]
        [20] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[b]
        [21] -1 0       0x00000500 - 0x0000051f (0x20) IX[b]
        [22] -1 0       0x0000d000 - 0x0000d00f (0x10) IX[b]
        [23] -1 0       0x0000cc00 - 0x0000cc03 (0x4) IX[b]
        [24] -1 0       0x0000c800 - 0x0000c807 (0x8) IX[b]
        [25] -1 0       0x0000c400 - 0x0000c403 (0x4) IX[b]
        [26] -1 0       0x0000c000 - 0x0000c007 (0x8) IX[b]
        [27] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[b]
        [28] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[b]
        [29] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[b]
        [30] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[b]
        [31] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[b]
        [32] -1 0       0x0000b800 - 0x0000b81f (0x20) IX[b]
        [33] -1 0       0x0000b400 - 0x0000b41f (0x20) IX[b]
        [34] -1 0       0x0000b000 - 0x0000b01f (0x20) IX[b]
        [35] -1 0       0x0000bc00 - 0x0000bc1f (0x20) IX[b]
        [36] -1 0       0x00009000 - 0x000090ff (0x100) IX[b](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 1.3.0, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.13.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
        compiled for 7.1.0, module version = 8.47.3
        Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.2.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.2.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.7
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.47.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.471         
(II) ATI Proprietary Linux Driver Build Date: Feb 25 2008 21:22:09
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x71C6) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [4] -1  0       0xf1026000 - 0xf10267ff (0x800) MX[b]
        [5] -1  0       0xf1000000 - 0xf101ffff (0x20000) MX[b]
        [6] -1  0       0xf1024000 - 0xf1025fff (0x2000) MX[b]
        [7] -1  0       0xf1020000 - 0xf1023fff (0x4000) MX[b]
        [8] -1  0       0xf2002000 - 0xf20020ff (0x100) MX[b]
        [9] -1  0       0xf2001000 - 0xf20011ff (0x200) MX[b]
        [10] -1 0       0x88200000 - 0x882003ff (0x400) MX[b]
        [11] -1 0       0xf2000000 - 0xf20003ff (0x400) MX[b]
        [12] -1 0       0xc0000000 - 0xbfffffff (0x0) MX[b]O
        [13] -1 0       0xe1000000 - 0xe100ffff (0x10000) MX[b](B)
        [14] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
        [15] -1 0       0xe1010000 - 0xe101ffff (0x10000) MX[b](B)
        [16] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [17] -1 0       0x00000000 - 0x000000ff (0x100) IX[b]
        [18] -1 0       0x0000a000 - 0x0000a0ff (0x100) IX[b]
        [19] -1 0       0x0000dc00 - 0x0000dc3f (0x40) IX[b]
        [20] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[b]
        [21] -1 0       0x00000500 - 0x0000051f (0x20) IX[b]
        [22] -1 0       0x0000d000 - 0x0000d00f (0x10) IX[b]
        [23] -1 0       0x0000cc00 - 0x0000cc03 (0x4) IX[b]
        [24] -1 0       0x0000c800 - 0x0000c807 (0x8) IX[b]
        [25] -1 0       0x0000c400 - 0x0000c403 (0x4) IX[b]
        [26] -1 0       0x0000c000 - 0x0000c007 (0x8) IX[b]
        [27] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[b]
        [28] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[b]
        [29] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[b]
        [30] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[b]
        [31] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[b]
        [32] -1 0       0x0000b800 - 0x0000b81f (0x20) IX[b]
        [33] -1 0       0x0000b400 - 0x0000b41f (0x20) IX[b]
        [34] -1 0       0x0000b000 - 0x0000b01f (0x20) IX[b]
        [35] -1 0       0x0000bc00 - 0x0000bc1f (0x20) IX[b]
        [36] -1 0       0x00009000 - 0x000090ff (0x100) IX[b](B)
(II) fglrx(0): pEnt->device->identifier=0x82095f8
(II) resource ranges after probing:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [4] -1  0       0xf1026000 - 0xf10267ff (0x800) MX[b]
        [5] -1  0       0xf1000000 - 0xf101ffff (0x20000) MX[b]
        [6] -1  0       0xf1024000 - 0xf1025fff (0x2000) MX[b]
        [7] -1  0       0xf1020000 - 0xf1023fff (0x4000) MX[b]
        [8] -1  0       0xf2002000 - 0xf20020ff (0x100) MX[b]
        [9] -1  0       0xf2001000 - 0xf20011ff (0x200) MX[b]
        [10] -1 0       0x88200000 - 0x882003ff (0x400) MX[b]
        [11] -1 0       0xf2000000 - 0xf20003ff (0x400) MX[b]
        [12] -1 0       0xc0000000 - 0xbfffffff (0x0) MX[b]O
        [13] -1 0       0xe1000000 - 0xe100ffff (0x10000) MX[b](B)
        [14] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
        [15] -1 0       0xe1010000 - 0xe101ffff (0x10000) MX[b](B)
        [16] 0  0       0x000a0000 - 0x000affff (0x10000) MS[b]
        [17] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[b]
        [18] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[b]
        [19] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [20] -1 0       0x00000000 - 0x000000ff (0x100) IX[b]
        [21] -1 0       0x0000a000 - 0x0000a0ff (0x100) IX[b]
        [22] -1 0       0x0000dc00 - 0x0000dc3f (0x40) IX[b]
        [23] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[b]
        [24] -1 0       0x00000500 - 0x0000051f (0x20) IX[b]
        [25] -1 0       0x0000d000 - 0x0000d00f (0x10) IX[b]
        [26] -1 0       0x0000cc00 - 0x0000cc03 (0x4) IX[b]
        [27] -1 0       0x0000c800 - 0x0000c807 (0x8) IX[b]
        [28] -1 0       0x0000c400 - 0x0000c403 (0x4) IX[b]
        [29] -1 0       0x0000c000 - 0x0000c007 (0x8) IX[b]
        [30] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[b]
        [31] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[b]
        [32] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[b]
        [33] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[b]
        [34] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[b]
        [35] -1 0       0x0000b800 - 0x0000b81f (0x20) IX[b]
        [36] -1 0       0x0000b400 - 0x0000b41f (0x20) IX[b]
        [37] -1 0       0x0000b000 - 0x0000b01f (0x20) IX[b]
        [38] -1 0       0x0000bc00 - 0x0000bc1f (0x20) IX[b]
        [39] -1 0       0x00009000 - 0x000090ff (0x100) IX[b](B)
        [40] 0  0       0x000003b0 - 0x000003bb (0xc) IS[b]
        [41] 0  0       0x000003c0 - 0x000003df (0x20) IS[b]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 0.1.0
        ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS" "false"
(II) fglrx(0): Loading PCS database from /etc/ati/amdpcsdb
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "Radeon X1650 Series" (Chipset = 0x71c6)
(--) fglrx(0): (PciSubVendor = 0x174b, PciSubDevice = 0x0850)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xe1000000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.1.0
        ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.12
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: RV530
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
        compiled for 7.1.0, module version = 8.47.3
        ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): Using adapter: 1:0.0.
(--) fglrx(0): VideoRAM: 262144 kByte, Type: DDR2
(II) fglrx(0): AGP card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0):  Display1: No EDID information from DDC.
(II) fglrx(0):  Display1: Failed to get EDID information.
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay not supported on this hardware
(==) fglrx(0): Qbs is not supported in this release. Disabled.
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled
(==) fglrx(0): TMDS coherent mode is enabled
(II) fglrx(0): Total of 24 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x1024 (pitch 0)
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync
(**) fglrx(0): *Mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 772 817 interlace
(**) fglrx(0): *Mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "800x600"   29.60  800 816 896 992  600 601 604 635 interlace +hsync
(**) fglrx(0): *Mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x960"  108.00  1280 1376 1488 1800  960 961 964 1000
(**) fglrx(0):  Default mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"   79.50  1280 1344 1472 1664  768 771 778 798 +hsync
(**) fglrx(0):  Default mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync
(**) fglrx(0):  Default mode "1280x720": 60.5 MHz (scaled from 0.0 MHz), 37.0 kHz, 50.0 Hz
(II) fglrx(0): Modeline "1280x720"   60.46  1280 1328 1456 1632  720 721 724 741 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0):  Default mode "1152x864": 64.7 MHz (scaled from 0.0 MHz), 43.0 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   64.67  1152 1208 1328 1504  864 865 868 915 interlace +hsync
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   58.28  1152 1200 1320 1488  864 865 868 911 interlace +hsync
(**) fglrx(0):  Default mode "720x576": 26.6 MHz (scaled from 0.0 MHz), 29.6 kHz, 50.0 Hz
(II) fglrx(0): Modeline "720x576"   26.56  720 736 808 896  576 577 580 593 +hsync
(**) fglrx(0):  Default mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0):  Default mode "640x432": 21.1 MHz (scaled from 0.0 MHz), 26.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432"   21.07  640 648 712 784  432 433 436 448 +hsync
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(==) fglrx(0): DPI set to (100, 100)
(--) fglrx(0): Virtual size is 1280x1024 (pitch 1280)
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync
(**) fglrx(0): *Mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 772 817 interlace
(**) fglrx(0): *Mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "800x600"   29.60  800 816 896 992  600 601 604 635 interlace +hsync
(**) fglrx(0): *Mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x960"  108.00  1280 1376 1488 1800  960 961 964 1000
(**) fglrx(0):  Default mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"   79.50  1280 1344 1472 1664  768 771 778 798 +hsync
(**) fglrx(0):  Default mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync
(**) fglrx(0):  Default mode "1280x720": 60.5 MHz (scaled from 0.0 MHz), 37.0 kHz, 50.0 Hz
(II) fglrx(0): Modeline "1280x720"   60.46  1280 1328 1456 1632  720 721 724 741 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0):  Default mode "1152x864": 64.7 MHz (scaled from 0.0 MHz), 43.0 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   64.67  1152 1208 1328 1504  864 865 868 915 interlace +hsync
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   58.28  1152 1200 1320 1488  864 865 868 911 interlace +hsync
(**) fglrx(0):  Default mode "720x576": 26.6 MHz (scaled from 0.0 MHz), 29.6 kHz, 50.0 Hz
(II) fglrx(0): Modeline "720x576"   26.56  720 736 808 896  576 577 580 593 +hsync
(**) fglrx(0):  Default mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0):  Default mode "640x432": 21.1 MHz (scaled from 0.0 MHz), 26.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432"   21.07  640 648 712 784  432 433 436 448 +hsync
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.2.0
        ABI class: X.Org Video Driver, version 1.2
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 256 MB
(II) fglrx(0): [pci] find AGP GART
(II) fglrx(0): [agp] Mode=0x1f004a1b bridge: 0x8086/0x2570
(II) fglrx(0): [agp] AGP v1/2 disable mask 0x00000000
(II) fglrx(0): [agp] AGP v3 disable mask   0x00000000
(II) fglrx(0): [agp] enabling AGP with mode=0x1f004b1a
(II) fglrx(0): [agp] Remapping MC AGP space (new MCAGPBase = 0xe0000000, MCAGPSize = 0x10000000)
(II) fglrx(0): [agp] AGP protocol is enabled for graphics board. (cmd=0x1f004312)
(II) fglrx(0): [agp] graphics chipset has AGP v3.0 (native mode)
(II) fglrx(0): [pcie] 262144 kB allocated
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] 0   0       0xe1000000 - 0xe100ffff (0x10000) MX[b]
        [1] 0   0       0xd0000000 - 0xdfffffff (0x10000000) MX[b]
        [2] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
        [3] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [4] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [5] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [6] -1  0       0xf1026000 - 0xf10267ff (0x800) MX[b]
        [7] -1  0       0xf1000000 - 0xf101ffff (0x20000) MX[b]
        [8] -1  0       0xf1024000 - 0xf1025fff (0x2000) MX[b]
        [9] -1  0       0xf1020000 - 0xf1023fff (0x4000) MX[b]
        [10] -1 0       0xf2002000 - 0xf20020ff (0x100) MX[b]
        [11] -1 0       0xf2001000 - 0xf20011ff (0x200) MX[b]
        [12] -1 0       0x88200000 - 0x882003ff (0x400) MX[b]
        [13] -1 0       0xf2000000 - 0xf20003ff (0x400) MX[b]
        [14] -1 0       0xc0000000 - 0xbfffffff (0x0) MX[b]O
        [15] -1 0       0xe1000000 - 0xe100ffff (0x10000) MX[b](B)
        [16] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
        [17] -1 0       0xe1010000 - 0xe101ffff (0x10000) MX[b](B)
        [18] 0  0       0x000a0000 - 0x000affff (0x10000) MS[b](OprU)
        [19] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[b](OprU)
        [20] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[b](OprU)
        [21] 0  0       0x00009000 - 0x000090ff (0x100) IX[b]
        [22] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [23] -1 0       0x00000000 - 0x000000ff (0x100) IX[b]
        [24] -1 0       0x0000a000 - 0x0000a0ff (0x100) IX[b]
        [25] -1 0       0x0000dc00 - 0x0000dc3f (0x40) IX[b]
        [26] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[b]
        [27] -1 0       0x00000500 - 0x0000051f (0x20) IX[b]
        [28] -1 0       0x0000d000 - 0x0000d00f (0x10) IX[b]
        [29] -1 0       0x0000cc00 - 0x0000cc03 (0x4) IX[b]
        [30] -1 0       0x0000c800 - 0x0000c807 (0x8) IX[b]
        [31] -1 0       0x0000c400 - 0x0000c403 (0x4) IX[b]
        [32] -1 0       0x0000c000 - 0x0000c007 (0x8) IX[b]
        [33] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[b]
        [34] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[b]
        [35] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[b]
        [36] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[b]
        [37] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[b]
        [38] -1 0       0x0000b800 - 0x0000b81f (0x20) IX[b]
        [39] -1 0       0x0000b400 - 0x0000b41f (0x20) IX[b]
        [40] -1 0       0x0000b000 - 0x0000b01f (0x20) IX[b]
        [41] -1 0       0x0000bc00 - 0x0000bc1f (0x20) IX[b]
        [42] -1 0       0x00009000 - 0x000090ff (0x100) IX[b](B)
        [43] 0  0       0x000003b0 - 0x000003bb (0xc) IS[b](OprU)
        [44] 0  0       0x000003c0 - 0x000003df (0x20) IS[b](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb7fa2000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.47.3
(II) fglrx(0):     Date: Feb 25 2008
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.22-14-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): Interrupt handler installed at IRQ 16.
(II) fglrx(0): Exposed events to the /proc interface
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xc1100000 FBMappedSize: 0x01004000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,3280)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 2256
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(**) fglrx(0): Textured Video is enabled.
(II) LoadModule: "glesx"
(II) Loading /usr/lib/xorg/modules//glesx.so
(II) Module glesx: vendor="X.Org Foundation"
        compiled for 7.1.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension GLESX
(II) fglrx(0): GLESX enableFlags = 16
(II) fglrx(0): GLESX is enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        8x8 mono pattern filled rectangles
        Solid Lines
        Dashed Lines
        Offscreen Pixmaps
        Setting up tile and stipple cache:
                32 128x128 slots
                14 256x256 slots
                5 512x512 slots
(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
[atiddx] ASYNCIO init succeed!
Receive enable interrupt ret message
...irqEnableMask: 10000000
...dwIRQEnableId: 00000008
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(WW) AIGLX: 3D driver claims to not support visual 0x33
(WW) AIGLX: 3D driver claims to not support visual 0x34
(WW) AIGLX: 3D driver claims to not support visual 0x35
(WW) AIGLX: 3D driver claims to not support visual 0x36
(WW) AIGLX: 3D driver claims to not support visual 0x37
(WW) AIGLX: 3D driver claims to not support visual 0x38
(WW) AIGLX: 3D driver claims to not support visual 0x39
(WW) AIGLX: 3D driver claims to not support visual 0x3a
(WW) AIGLX: 3D driver claims to not support visual 0x3b
(WW) AIGLX: 3D driver claims to not support visual 0x3c
(WW) AIGLX: 3D driver claims to not support visual 0x3d
(WW) AIGLX: 3D driver claims to not support visual 0x3e
(WW) AIGLX: 3D driver claims to not support visual 0x3f
(WW) AIGLX: 3D driver claims to not support visual 0x40
(WW) AIGLX: 3D driver claims to not support visual 0x41
(WW) AIGLX: 3D driver claims to not support visual 0x42
(WW) AIGLX: 3D driver claims to not support visual 0x43
(WW) AIGLX: 3D driver claims to not support visual 0x44
(WW) AIGLX: 3D driver claims to not support visual 0x45
(WW) AIGLX: 3D driver claims to not support visual 0x46
(WW) AIGLX: 3D driver claims to not support visual 0x47
(WW) AIGLX: 3D driver claims to not support visual 0x48
(WW) AIGLX: 3D driver claims to not support visual 0x49
(WW) AIGLX: 3D driver claims to not support visual 0x4a
(WW) AIGLX: 3D driver claims to not support visual 0x4b
(WW) AIGLX: 3D driver claims to not support visual 0x4c
(WW) AIGLX: 3D driver claims to not support visual 0x4d
(WW) AIGLX: 3D driver claims to not support visual 0x4e
(WW) AIGLX: 3D driver claims to not support visual 0x4f
(WW) AIGLX: 3D driver claims to not support visual 0x50
(WW) AIGLX: 3D driver claims to not support visual 0x51
(WW) AIGLX: 3D driver claims to not support visual 0x52
(WW) AIGLX: 3D driver claims to not support visual 0x53
(WW) AIGLX: 3D driver claims to not support visual 0x54
(WW) AIGLX: 3D driver claims to not support visual 0x55
(WW) AIGLX: 3D driver claims to not support visual 0x56
(WW) AIGLX: 3D driver claims to not support visual 0x57
(WW) AIGLX: 3D driver claims to not support visual 0x58
(WW) AIGLX: 3D driver claims to not support visual 0x59
(WW) AIGLX: 3D driver claims to not support visual 0x5a
(WW) AIGLX: 3D driver claims to not support visual 0x5b
(WW) AIGLX: 3D driver claims to not support visual 0x5c
(WW) AIGLX: 3D driver claims to not support visual 0x5d
(WW) AIGLX: 3D driver claims to not support visual 0x5e
(WW) AIGLX: 3D driver claims to not support visual 0x5f
(WW) AIGLX: 3D driver claims to not support visual 0x60
(WW) AIGLX: 3D driver claims to not support visual 0x61
(WW) AIGLX: 3D driver claims to not support visual 0x62
(WW) AIGLX: 3D driver claims to not support visual 0x63
(WW) AIGLX: 3D driver claims to not support visual 0x64
(WW) AIGLX: 3D driver claims to not support visual 0x65
(WW) AIGLX: 3D driver claims to not support visual 0x66
(WW) AIGLX: 3D driver claims to not support visual 0x67
(WW) AIGLX: 3D driver claims to not support visual 0x68
(WW) AIGLX: 3D driver claims to not support visual 0x69
(WW) AIGLX: 3D driver claims to not support visual 0x6a
(WW) AIGLX: 3D driver claims to not support visual 0x6b
(WW) AIGLX: 3D driver claims to not support visual 0x6c
(WW) AIGLX: 3D driver claims to not support visual 0x6d
(WW) AIGLX: 3D driver claims to not support visual 0x6e
(WW) AIGLX: 3D driver claims to not support visual 0x6f
(WW) AIGLX: 3D driver claims to not support visual 0x70
(WW) AIGLX: 3D driver claims to not support visual 0x71
(WW) AIGLX: 3D driver claims to not support visual 0x72
(II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbVariant" "alt-intl"
(**) Generic Keyboard: XkbVariant: "alt-intl"
(**) Option "XkbOptions" "lv3:ralt_switch,compose:rwin"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch,compose:rwin"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
```

---

### Post by MadeR on 2008-03-07
What can I do ? :(

---

### Post by MadeR on 2008-03-09
I tried using the fglrx AGP module, without success it seems. The idea came to me from the following dmesg output:

[   62.044928] Linux agpgart interface v0.102 (c) Dave Jones
[   62.187687] agpgart: Detected an Intel 865 Chipset.
[   62.198889] agpgart: AGP aperture is 256M @ 0xc0000000
[   63.024938] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   63.058145] [fglrx] Maximum main memory to use for locked dma buffers: 1899 MBytes.
[   63.058243] [fglrx] ASYNCIO init succeed!
[   63.058938] [fglrx] PAT is enabled successfully!
[   63.060773] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[  119.604359] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[  119.604407] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[  119.604447] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[COLOR=red][B][  119.604213] [fglrx] Internal AGP support requested, but kernel AGP support active.
[  119.604220] [fglrx] Have to use kernel AGP support to avoid conflicts.[/B][/COLOR]
[  119.604228] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)
[  119.604510] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[  119.806225] [fglrx] Reserve Block - 0 offset =  0X7ffb000 length = 0X5000
[  119.806232] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
[  119.806237] [fglrx] Reserve Block - 2 offset =  0X1ffff000 length = 0X1000
[  119.806241] [fglrx] Reserve Block - 3 offset =  0Xff80000 length = 0X80000
[  120.201630] [fglrx] interrupt source 10000000 successfully enabled
[  120.201636] [fglrx] enable ID = 0x00000008
[  120.201649] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000


So I tried blacklisting agpgart and intel_agp and adding *Option "UseInternalAGPGART" "yes"* to the Device section in xorg.conf. You can see the output below. Anyway xorg reverted to using the vesa driver.

[   45.254235] Linux agpgart interface v0.102 (c) Dave Jones
mader@silmarillion:~$ dmesg | grep fgl
[   45.454906] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   45.487617] [fglrx] Maximum main memory to use for locked dma buffers: 1899 MBytes.
[   45.487717] [fglrx] ASYNCIO init succeed!
[   45.488416] [fglrx] PAT is enabled successfully!
[   45.488739] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[COLOR=red]**[  103.462700] [fglrx] Internal AGP is not supported in 2.6 kernel.[/color]**

Of course I removed the agpgart and intel_agp modules from /etc/modprobe.d/blacklist and useinternalagp from xorg.conf.

---

### Post by ahreece on 2008-03-12
I've been having the same problems with with a Compaq nc6230 for the past month, both with Gutsy & the Hardy Alpha builds (which are getting better!)  It has a built-in ATI x300 with 64 Megs of RAM and it has been driving me crazy. I've tried both the open source ati/radeon drivers and the Binary ones from ATI/AMD and I have had some success with both, and some failures with both.

Here is how it breaks down:
[LIST]
[*]Open Source Single Screen  - mostly good, but some hanging
[*]Open Source Dual Head - not so hot at this point
[*]Binary Single Screen - mostly good
[*]Binary Big Dual Head (ATI's version) - not yet.
[/LIST]

I've was actually doing quite well with the Binary Driver and Compiz until I started to play around with it. From what I can tell:

BLACKLIST intel_agp

AND

LEAVE IN agpgart

Both the open source and ati drivers apparently use the agpgart. I think intel_agp is for the various Integrated chip sets. In other words, for some reason, a second unwanted video driver (intel_agp)  is being loaded up and causing problems, BUT agpgart is needed.

Now I've temporarily switched back to Gutsy until I can figure out which driver is more stable, but for a while there, I had absolutely no problems so long as I was on a single screen , even with advanced Compiz features.

---

### Post by MadeR on 2008-03-12
Did you have the same problem with opengl windows?

---

### Post by ahreece on 2008-03-12
I haven't tried yet. I was having unusual problems with my video camera. It turns out my video camera (my PS/2 Eye Toy) had simply died, drat it! It was cheap, too! Under $20 bucks CDN on sale.

I just haven't had the opportunity to try many OpenGL or video applications yet. I intend to:  I'm just looking for stability at this point.

---

### Post by MadeR on 2008-03-12
I am having problems even with fgl_glxgears!
Try [planeshift](http://www.planeshift.it/) for a nice opengl application ;)

---

### Post by MadeR on 2008-03-13
Anybody else having the same problem with crappy ati cards and opengl?

---

### Post by ahreece on 2008-03-13
I'm having better luck, but only because I just did a fresh rebuild of Ubuntu 7.10 off of the Alternate Install CD. The stock install off of the CD with no patches (I had disconnected my network to start with) was extremely unreliable. I tried to log in about three times, but each time, X.org seems to hang less than a minute after logging in. The mouse and the mouse icon still worked, but the rest of the screen program seemed to have hung and the keyboard didn't respond. OpenSSH & Telnet aren't installed or active, some I'm unsure of how hard the lockup went.

Updating Gutsy to the latest patches seemed to clear up a lot of problems. Basic Compiz effects are enabled and seem to be working. I haven't tried PlaneShift yet (the client just got updated and I've yet to get a valid binary download from the active mirrors), but the few OpenGL screen savers I've tried are giving me some problems. Previewing the screensavers either doesn't work or it only works for a few seconds, and glxgears runs, but if you move it around the screen it leaves copies of itself that aren't cleared until the program is completely refreshed.

I might try playing with the Compiz effects next, but I don't dare try to enable dual head/xinerama/big window/etc at this point since that seems to aggravate the problems.

I manually added intel_agp is to /etc/modprobe.d/blacklist
```
# causes problems with ATI / AMD driver
blacklist intel_agp

```

xorg.conf
```

# xorg.conf (xorg X Window System server configuration file)
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc M22 [Mobility Radeon X300]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc M22 [Mobility Radeon X300]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection
```

glxinfo
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2

```

xvinfo
```

X-Video Extension version 2.2
screen #0
  Adaptor #0: "ATI Radeon Video Overlay"
    number of ports: 1
    port base: 73
    operations supported: PutImage 
    supported visuals:
      depth 24, visualID 0x23
      depth 24, visualID 0x24
      depth 24, visualID 0x25
      depth 24, visualID 0x26
      depth 24, visualID 0x27
      depth 24, visualID 0x28
      depth 24, visualID 0x29
      depth 24, visualID 0x2a
      depth 24, visualID 0x2b
      depth 24, visualID 0x2c
      depth 24, visualID 0x2d
      depth 24, visualID 0x2e
      depth 24, visualID 0x2f
      depth 24, visualID 0x30
      depth 24, visualID 0x31
      depth 24, visualID 0x32
    number of attributes: 22
      "XV_DEVICE_ID" (range 0 to -1)
              client gettable attribute (current value is 109)
      "XV_LOCATION_ID" (range 0 to -1)
              client gettable attribute (current value is 110)
      "XV_INSTANCE_ID" (range 0 to -1)
              client gettable attribute (current value is 111)
      "XV_DUMP_STATUS" (range 0 to 1)
              client settable attribute
      "XV_SET_DEFAULTS" (range 0 to 1)
              client settable attribute
      "XV_AUTOPAINT_COLORKEY" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
      "XV_COLORKEY" (range 0 to -1)
              client settable attribute
              client gettable attribute (current value is 30)
      "XV_DOUBLE_BUFFER" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
      "XV_OVERLAY_ALPHA" (range 0 to 255)
              client settable attribute
              client gettable attribute (current value is 255)
      "XV_GRAPHICS_ALPHA" (range 0 to 255)
              client settable attribute
              client gettable attribute (current value is 255)
      "XV_ALPHA_MODE" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_BRIGHTNESS" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_CONTRAST" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_SATURATION" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_COLOR" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_HUE" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_RED_INTENSITY" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_GREEN_INTENSITY" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_BLUE_INTENSITY" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_CRTC" (range -1 to 1)
              client settable attribute
              client gettable attribute (current value is -1)
      "XV_GAMMA" (range 100 to 10000)
              client settable attribute
              client gettable attribute (current value is 1000)
      "XV_COLORSPACE" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 0)
    maximum XvImage size: 2048 x 2048
    Number of image formats: 8
      id: 0x41424752 (RGBA)
        guid: 52474241-0000-0010-8000-00aa00389b71
        bits per pixel: 32
        number of planes: 1
        type: RGB (packed)
        depth: 32
        red, green, blue masks: 0xff0000, 0xff00, 0xff
      id: 0x0
        guid: 52474200-0000-0010-8000-00aa00389b71
        bits per pixel: 24
        number of planes: 1
        type: RGB (packed)
        depth: 24
        red, green, blue masks: 0xff0000, 0xff00, 0xff
      id: 0x54424752 (RGBT)
        guid: 52474254-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: RGB (packed)
        depth: 16
        red, green, blue masks: 0x7c00, 0x3e0, 0x1f
      id: 0x32424752 (RGB2)
        guid: 52474200-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: RGB (packed)
        depth: 16
        red, green, blue masks: 0xf800, 0x7e0, 0x1f
      id: 0x32595559 (YUY2)
        guid: 59555932-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x59565955 (UYVY)
        guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x32315659 (YV12)
        guid: 59563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x30323449 (I420)
        guid: 49343230-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
```

---

### Post by MadeR on 2008-03-13
I do not have direct rendering!!!

glxinfo
```

name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2

```

---

### Post by MadeR on 2008-03-13
> **MadeR said:**
> I do not have direct rendering!!!

glxinfo
```

name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2

```


it seems that if I blacklist intel_agp, the ati driver is not used!

---

### Post by ahreece on 2008-03-13
That's OK. I'm not having as much luck as I thought. My laptop is dual boot because it has to be, so the last the time I logged into Gutsy, the first thing it did was hang on me.

I did read somewhere that some older ATI cards are problematic (I don't understand how a 2005 chipset could be considered one of the older ones, but such is obsolescence on the Internet), so I restarted into recovery mode and added 

```
Option    "AGPMode" "4"
```

to the device section of my xorg.conf:

```
Section "Device"
        Identifier      "ATI Technologies Inc M22 [Mobility Radeon X300]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "AGPMode" "4"
EndSection
```

But you have to remember, I'm currently using the open source driver right at the moment. The last time I had success with the binary drivers, I used Envy to install it (from [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")), BUT, my major problems started after I tried to enable the dual head mode enabled via the AMD/ATI control panel. That screwed everything up for me, and after that nothing was reliable. EVER.

Even using Envy to remove the Binary driver and return to the opensource driver didn't seem to work right. Hence, my recent quick rebuild. I didn't really lose anything, just time.

---

### Post by ahreece on 2008-03-14
It is taken a while, but I am now running a very stable setup of Ubuntu Hardy Heron (7.10) with the ATI Binary Driver 8.471.0 on an HP nc6230 with an ATI x300 chipset with 64M of video ram.

I did a clean install off of the 7.10 Alternate CD (I've never liked performance for the Desktop Installer CD, but I'm impatient).

I blacklisted the intel_agp driver and ran "depmod -a" to remove any chance of it being installed.

I used the opensource driver for a while, but it proved to be quite unstable. Choosing mouse options or running programs could cause the screen to hang. As I stated previously, it left my mouse functional, but nothing else appeared to work.

My final act was to obtain Envy from [http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html") and use it to install the latest ATI driver. I let it install the driver and configure xorg.conf.

The system is stable and fast and seems to work very well. I haven't had any crashes yet (fingers crossed), and fglxinfo reports:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X300
OpenGL version string: 2.1.7412 Release
```

What works:
[LIST]
[*]Compiz
[*]OpenGL Screensavers - I tried about 5 different ones
[*]PlaneShift 0.3.0.2 - I don't have an account, so all I got was the login screen
[/LIST]

What doesn't work:
[LIST]
[*]Dual head - Any form, and I am not going to try at this point!
[*]Compiz plus any other OpenGL
[/LIST]

I seem to have a choice: I can either have eye candy with Compiz OR I can run OpenGL apps & video applications (Flash, video players, etc.), but I either don't have enough CPU and/or video RAM to do both at the same time. I can give you my configuration files, but I'm not sure what would work for you at this point. I'm not even touching xorg.conf if I can help it.

My other problem is going to be what do I do when I want to install Hardy. Envy is great at installing, but removing it caused me some many problems that it just made more sense to wipe and re-install (What is this with binary software trying to emulate W*ndows reliability?!). Maybe I missed something on the FAQ.

As a side note, I also have my winmodem AND my IRDA port working properly. It isn't straightforward yet, but it is getting close.

---

### Post by MadeR on 2008-03-17
I am using kubuntu gutsy and I installed the 8.3 (8.47.3) drivers by hand.

Does anybody know what kind of modifications this envy thingy adds to the standard ATI setup?

---

