---
title: "Getting third monitor to work with laptop"
date: 2011-07-26
forum: Multimedia Software
---

### Post by MyNDIrish on 2011-07-26
I have a Lenovo Thinkpad T500 that currently functions - through the standard monitor hookup - with two monitors: the laptop monitor and a Samsung SyncMaster 920NW monitor.  I want to add a third monitor (an Acer AL1916W), so I bought a Kensington Universal Multi-Display Adapter.  This is a USB to VGA adapter.  I have tried multiple things and I think I am almost there.  I think this because I have gone through several iterations of "no screen", "green screen" and finally, the weirdest part - "Ubuntu screen".

When I rebooted my laptop this last time I get my laptop screen works just fine.  My Samsung screen is also working fine - it is connected via the docking station standard video port.  My Acer screen is on, has a signal from the laptop, but the only thing it displays is a graphical "Ubuntu" in the middle like the other monitors do when the system is being started.  

Details:
```
$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 08ff:2810 AuthenTec, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 17e9:0036 Newnham Research 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 001 Device 005: ID 0518:0001 EzKEY Corp. USB to PS2 Adaptor v1.09
Bus 001 Device 004: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 003: ID 04b3:4485 IBM Corp. Serial Converter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
``````
$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:03.0 Communication controller: Intel Corporation Mobile 4 Series Chipset MEI Controller (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 11)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)
``````
$ cat /etc/X11/xorg.conf
Section "ServerLayout"
    Identifier     "Server Layout"
    Screen      0  "Screen[0]" 0 0
    Screen      1  "Screen[1]" LeftOf "Screen[0]"
    Screen      2  "Screen[2]" RightOf "Screen[0]"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

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
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "extmod"
    Load  "dri"
    Load  "dbe"
    Load  "dri2"
    Load  "record"
    Load  "glx"
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

Section "Monitor"
    Identifier   "Monitor[0]"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor[1]"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor[2]"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
    Identifier  "Device[0]"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "Mobile 4 Series Chipset Integrated Graphics Controller"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
    Identifier  "Device[1]"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "Mobile 4 Series Chipset Integrated Graphics Controller"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
    Identifier  "Device[2]"
    Driver      "sisusb"
EndSection

Section "Screen"
    Identifier "Screen[0]"
    Device     "Device[0]"
    Monitor    "Monitor[0]"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen[1]"
    Device     "Device[1]"
    Monitor    "Monitor[1]"
        DefaultDepth 24
    SubSection "Display"
        Depth     24
                Modes "1440x900_75"
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen[2]"
    Device     "Device[2]"
    Monitor    "Monitor[2]"
        DefaultDepth 24
    SubSection "Display"
        Depth     24
                Modes "1440x900_75"
    EndSubSection
EndSection
``````
$ uname -a
Linux my-laptop 2.6.34-020634-generic #020634 SMP Mon May 17 19:27:49 UTC 2010 x86_64 GNU/Linux
```

---

