---
title: "Succussful Quad monitors (or Triple Monitors) using ATI"
date: 2010-03-17
forum: Multimedia Software
---

### Post by adapeater on 2010-03-17
I can use all four outputs of two ATI cards (two outputs from each of the two cards). I found several threads about failed attempts to get this working. Here's a success story:

I have one desktop spanning four monitors and a second desktop on a fifth monitor using three outputs and a TripleHead2Go. If I had another monitor I'm sure I could span the second desktop across the fifth and sixth monitors.

If someone could help me start at 3072x768 I'd really appreciate it ;-) Currently I have to switch to 3072x768 using xrandr, which means I can't enable Xinerama to create one desktop spanning all five monitors.

I almost got this working with the open source driver, but it appears to have a bug (the outputs were switched off even though the card was active--I verified this by remote controlling the computer and could see what should have been displayed on those monitors). So I changed to the proprietary driver from ATI.

The trick is to create a basic xorg.conf that allows amdcccle to detect both cards, but not so complicated it doesn't know what to do with it, then use amdcccle to enable "Multiple-display desktop."

You will have two desktops, each covering two screens. If you want one large desktop covering all four screens, you can enable Xinerama, with all the side effects that causes.

```
Section "ServerLayout"
    Identifier     "Basic fglrx"
    Screen      0  "Screen1" 0 0
    Screen      1  "Screen0" RightOf "Screen1"
EndSection

Section "Device"
    Identifier  "Device0"
    Driver      "fglrx"
    BusID       "PCI:1:5:0"
EndSection

Section "Device"
    Identifier  "Device1"
    Driver      "fglrx"
    BusID       "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Device0"
    DefaultDepth  24
    SubSection "Display"
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Device1"
    DefaultDepth  24
    SubSection "Display"
        Depth     24
    EndSubSection
EndSection


```Change the BusID's as appropriate for your system. On my system:
```
$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3300 Graphics
02:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4350]
```

---

### Post by adapeater on 2010-03-17
Here is my current Xorg.conf. This creates a 'T' layout. A single 1024x768 LCD panel is below the middle monitor of three 1024x768 CRTs connected to the TripleHead2Go, and a single 1280x1024 CRT is off to the Right.

However, 4080x768 is not an option according to xrandr :(

If I change "PreferredMode" to "3072x768" it starts at 1024x768 :(

```
$ xrandr --output DFP5 --mode 3072x768
$ xrandr --output DFP5 --mode 3840x1024
$ xrandr --output DFP5 --mode 4080x768
xrandr: cannot find mode 4080x768

``````
Section "ServerLayout"
    Identifier    "amdcccle + edits"
    Screen      0 "Screen[4350]" 0 0
    Screen        "Screen[3300]" RightOf "Screen[4350]"
EndSection

Section "Monitor"
    Identifier    "0-DFP5"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "2048x768"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
    ModeLine      "3072x768_60.0" 195.0 3072 3144 3384 4032 768 771 780 806 -hsync -vsync
    ModeLine      "3840x1024_60" 254.3 3840 3856 3872 3976 1024 1025 1032 1066 +hsync +vsync
    ModeLine      "4080x768_60" 200.4 4080 4104 4136 4200 768 771 779 795 +hsync +vsync
EndSection

Section "Monitor"
    Identifier    "0-CRT2"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1024x768"
    Option        "TargetRefresh" "75"
    Option        "Position" "1020 768"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier    "1-CRT1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1280x1024"
    Option        "TargetRefresh" "75"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier    "Device[3300]"
    Driver        "fglrx"
    Option        "Monitor-CRT1" "1-CRT1"
    BusID         "PCI:1:5:0"
EndSection

Section "Device"
    Identifier    "Device[4350]"
    Driver        "fglrx"
    Option        "Monitor-DFP5" "0-DFP5"
    Option        "Monitor-CRT2" "0-CRT2"
    BusID         "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier    "Screen[3300]"
    Device        "Device[3300]"
    DefaultDepth  24
    SubSection    "Display"
        Virtual   5040 2208
        Depth     24
        Modes     "3072x768_60" "3840x1024_60" "4080x768_60"
    EndSubSection
EndSection

Section "Screen"
    Identifier    "Screen[4350]"
    Device        "Device[4350]"
    DefaultDepth  24
    SubSection    "Display"
        Virtual   5040 2208
        Depth     24
        Modes     "3072x768_60" "3840x1024_60" "4080x768_60"
    EndSubSection
EndSection


```

---

### Post by adapeater on 2010-03-17
Using the open source driver, the computer can start in any of the triple head modelines, even 4080x768

Since I can't span a single desktop to the fifth monitor, for now, I went back to the open source driver, and am using "only" four monitors. This is the xorg.conf for a single desktop spanning four monitors arranged in a T:

```
Section "ServerLayout"
    Identifier     "Layout"
        Screen      0  "Screen[4350]" 0 0
EndSection

Section "Screen"
    Identifier "Screen[4350]"
    Device     "Device[4350]"
    DefaultDepth  16
        SubSection "Display"
               Depth           16
               Virtual         5040 2208
               Modes          "3072x768_60" "3840x1024_60" "4080x768_60"
        EndSubSection
EndSection

Section "Device"
    Identifier  "Device[4350]"
    Driver      "radeon"
    VendorName  "ATI Technologies Inc"
    BoardName   "RV710 [Radeon HD 4350]"
    BusID       "PCI:1:0:0"
        Option      "monitor-VGA-0" "Monitor[4350-VGA]"
        Option      "monitor-HDMI-0" "Monitor[4350-HDMI]"
        Option      "monitor-DVI-0" "Monitor[4350-DVI]"
        Option      "MergedFB" "true"
        Option      "MergedXinerama" "true"
        Option      "MergedDPI" "94"
        Option      "MergedNonRectangular" "true"
EndSection

Section "Monitor"
    Identifier   "Monitor[4350-DVI]"
    VendorName   "MonitorVendor"
    ModelName    "MonitorModel"
#        Option       "Preferred Mode" "3072x768_60"
        Option       "Preferred Mode" "4080x768_60"
        Modeline     "3072x768_60"  195.00  3072 3144 3384 4032  768 771 780 806 -hsync -vsync
        ModeLine     "3840x1024_60" 254.3 3840 3856 3872 3976 1024 1025 1032 1066 +hsync +vsync
        ModeLine     "4080x768_60" 200.4 4080 4104 4136 4200 768 771 779 795 +hsync +vsync
EndSection

Section "Monitor"
    Identifier   "Monitor[4350-VGA]"
    VendorName   "MonitorVendor"
    ModelName    "MonitorModel"
    Option       "Position" "1024 768"
EndSection

```The Depth can be changed, or left out completely. For now I'm satisfied with 16 bits per pixel. I believe higher pixel depths require more processing, consume more energy and slow down the computer.

---

