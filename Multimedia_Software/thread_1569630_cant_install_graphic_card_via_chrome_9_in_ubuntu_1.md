---
title: "cant install graphic card via chrome 9 in ubuntu 10.04"
date: 2010-09-07
forum: Multimedia Software
---

### Post by linsan on 2010-09-07
this is my lspci, please help me how to download a driver for graphic card, the more important problem, how to install it.
.......................................................
ehsan@ehsan-laptop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)
06:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
07:04.0 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
07:04.1 SD Host controller: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller
07:04.3 FLASH memory: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller
....................
thanks a lot

---

### Post by Yellow Pasque on 2010-09-07
The best available driver (openchrome) is enabled by default. If you want more assistance, provide more details on your issue and your system (/var/log/Xorg.0.log is often helpful).

---

### Post by linsan on 2010-09-07
the problem is that, my visual effects doesn't work, and i have problem with watching moves.
but now, i installed VIA Chrome 9 HC driver , now my screen can't be filled completely, i mean that my desktop size is smaller than my monitor size, there is a black line at the right side of screen. and again my visual effects doesn't work.
please help
thanks
and my xorg.conf is this
....................
Section "ServerLayout"
       Identifier    "Default Layout"
       Screen        "Default Screen"
       InputDevice    "Mouse"
       InputDevice    "Keyboard"
EndSection

Section "Files"
#     RgbPath      "/usr/local/share/X11/rgb"
       ModulePath   "/usr/lib/xorg/modules"
#     FontPath     "/usr/share/fonts/X11/misc/"
#     FontPath     "/usr/share/fonts/X11/TTF/"
#     FontPath     "/usr/share/fonts/X11/OTF"
#     FontPath     "/usr/share/fonts/X11/Type1/"
#     FontPath     "/usr/share/fonts/X11/100dpi/"
#     FontPath     "/usr/share/fonts/X11/75dpi/"
EndSection

Section "InputDevice"
       Identifier    "Keyboard"
       Driver        "kbd"
       Option        "XkbRules"    "xorg"
       Option        "XkbModel"    "pc105"
       Option        "XkbLayout"    "cn"
EndSection

Section "InputDevice"
       Identifier    "Mouse"
       Driver        "mouse"
       Option        "CorePointer"
EndSection

Section "Monitor"
       Identifier    "CRT"
       Option    "Enable"    "true"            
EndSection

Section "Monitor"
       Identifier    "LCD"
       Option     "Enable"    "false"         
EndSection    

Section "Monitor"
       Identifier    "DVI"
       Option     "Enable"    "false"
EndSection    

Section "Monitor"
       Identifier    "TV"
       Option  "Ignore"    "true"
EndSection    

Section "Monitor"
       Identifier    "HDMI"
       Option  "Ignore"    "true"
EndSection    

Section "Monitor"
       Identifier    "CRT-2"
       Option      "Ignore"    "true"
EndSection

Section "Monitor"
       Identifier    "LCD-2"
       Option      "Ignore"    "true"
EndSection

Section "Monitor"
       Identifier    "DVI-2"
       Option      "Ignore"    "true"
EndSection

Section "Monitor"
       Identifier    "TV-2"
       Option      "Ignore"    "true"
EndSection

Section "Device"
    #BusID "PCI:01:00:0"
    Driver     "via"
    VendorName      "VIA Tech"
    BoardName       "via"
    Identifier    "Configured Video Device"
    Option        "MigrationHeuristic" "greedy"
EndSection

Section "Screen"
       DefaultDepth 24
       SubSection "Display"
#             Virtual 2000 2000 
              Depth  24
       EndSubSection
       Identifier    "Default Screen"
       Device        "Configured Video Device"
EndSection

Section "Module"
      Load  "glx"
      Load  "dri"
      Load  "extmod"
EndSection

Section "DRI"
       Group 0
       Mode 0666
EndSection

Section "Extensions"
    Option    "Composite"            "Enable"
EndSection

---

