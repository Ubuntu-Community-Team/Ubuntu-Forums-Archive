---
title: "New install killed dual monitors, nvidia setup not working"
date: 2010-09-14
forum: Multimedia Software
---

### Post by xfred on 2010-09-14
I've just installed 10.04 on an old system.  Hardware is:

- NVIDIA GeForce 6600 GT video card
- Gigabyte EP35C-DS3R motherboard with 3 gig ram, few TB of hard-drive
- dual monitors, both viewsonic vx2235wm, primary on analog, secondary on digital (but whatever, happy to reverse the order)

On the old setup (8.04) the monitors were set up as twinview, 1680x1050 each, no problems.
On the new setup (10.04) my old xorg.conf (see below) doesn't work and nvidia xserver settings refuses to detect my second (digital) monitor at any resolution greater than 640x480.

I've tried messing with xorg.conf to no avail and google doesn't appear to be my friend.  Anyone have any suggestions?

Here's the old xorg.conf file that worked in 8.04 but refuses to even boot under 10.04:
```
Section "Files"
    FontPath    "/usr/share/fonts/X11/misc"
    FontPath    "/usr/share/fonts/X11/cyrillic"
    FontPath    "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/Type1"
    FontPath    "/usr/share/fonts/X11/100dpi"
    FontPath    "/usr/share/fonts/X11/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load    "i2c"
    Load    "bitmap"
    Load    "ddc"
#    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "vbe"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "stylus"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "eraser"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "cursor"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 Ultra]"
    Driver         "nvidia"
    VendorName     "Videocard vendor"
    BoardName     "NVIDIA GeForce 6600 GT"
    BusID         "PCI:1:0:0"
    Option         "NvAGP" "2"
    Option         "NoLogo" "1"
#    turn this on later
    Option         "RenderAccel" "1"
    Option         "CursorShadow" "1"
    Option         "Coolbits" "1"
    Option         "ConnectedMonitor" "crt, dfp"
    Option         "NoPowerConnectorCheck"
    Option         "TwinView" "1"
    Option         "Metamodes" "1680x1050,1680x1050; 1440x900,1140x900; 1280x800,1280x800; 1024x640,1024x640; 1680x1050,NULL; 1440x900,NULL; 1280x800,NULL; 1024x640,NULL"
    Option         "SecondMonitorHorizSync" "31-82"
    Option         "SecondMonitorVertRefresh" "56-76"
#    this option can be used to make windows span by default
    # Option    "NoTwinViewXineramaInfo"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
    HorizSync    28-204
    VertRefresh    43-60
        Modeline     "1680x1050@60" 154.20 1680 1712 2296 2328 1050 1071 1081 1103 -hsync +vsync
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 Ultra]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Viewport     0 0
        Depth        1
        Modes        "4095x4095" "1680x1050" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Viewport     0 0
        Depth        4
        Modes        "4095x4095" "1680x1050" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Viewport     0 0
        Depth        8
        Modes        "4095x4095" "1680x1050" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Viewport     0 0
        Depth        15
        Modes        "4095x4095" "1680x1050" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Viewport     0 0
        Depth        16
        Modes        "4095x4095" "1680x1050" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Viewport     0 0
        Depth        24
        Modes        "4095x4095" "1680x1050" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Twinview configuration"
    Screen        0 "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
        Option        "Xinerama" "Off"
    InputDevice     "stylus"    "SendCoreEvents"
    InputDevice     "cursor"    "SendCoreEvents"
    InputDevice     "eraser"    "SendCoreEvents"
EndSection

Section "DRI"
    Mode    0666
EndSection
```

---

### Post by xfred on 2010-12-06
Solved it!  Well sort of solved, anyhow, after a longish break from trying.  After much searching and swearing I have a workable solution and I've come to following conclusions:

- you can't combine digital and VGA outputs and get a decent twinview setup with these cards - digital can't do more than 640x480 in such a setup.
- hence you need to use the digital->vga dongle thingy and run both monitors off VGA cables.
- EDID support is thoroughly messed up for this combo of monitor/video card, so you'll need to disable it and do things manually.
- messing with xorg.conf is a thoroughly unpleasant experience.

Anyhow that said here's my xorg.conf file that works with the above hardware.  Hope it helps, and feel free to enlighten me if you can work out you can't have one monitor on VGA and one on digital like you could in older versions of ubuntu.

```
# Final version: Nvidia GeForce 6600 card, two ViewSonic VX2235wm monitors.
#
# Notes: 
# - digital doesn't work in a dual-monitor setup.  No idea why: it used to in ubuntu 8.whatever, but in ubuntu 10.04 it doesn't
# - instead use a digital-vga dongle thing and plug the second monitor into the vga
# - EDID is also mangled for this setup, so need to use manual override.  Again this wasn't the case in 8.whatever
# - initial source nabbed from mangled autogen version, then modified to work

Section "ServerLayout"
    Identifier     "DualScreenLayout"
    Screen	   0 "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # Sourced manually from EDID
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync	   30-82
    VertRefresh	   50-75
    Modeline 	   "1680x1050" 146.25 1680 1784 1960 2240 1050 1053 1059 1089 +hsync -vsync
    Option         "DPMS"
EndSection

Section "Device"
    #Information sources (some even currentish):
    #
    #http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/appendix-b.html
    #ftp://download.nvidia.com/XFree86/Linux-x86_64/1.0-8762/README/appendix-d.html
    #ftp://download.nvidia.com/XFree86/Linux-x86_64/1.0-8762/README/appendix-g.html
    #ftp://download.nvidia.com/XFree86/Linux-x86_64/1.0-8762/README/appendix-r.html
    #http://www.x.org/archive/X11R6.8.2/doc/DESIGN2.html
    #http://http.download.nvidia.com/XFree86_40/1.0-2880/README.txt
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6600"
    BusID 	   "PCI:1:0:0"
    Option         "UseEDID" "False"      #ignore bad edid reading
    Option         "UseEdidFreqs" "False" #ignore bad edid reading
    # Option         "IgnoreEDID" "True"    #ignore bad edid reading (deprecated)
    # Option         "AllowDDCCI" "False"   #don't use DDC/CI: may need to use this
    Option 	   "ConnectedMonitor" "CRT-0, CRT-1"
    # Option 	   "ConnectedMonitor" "CRT, CRT"     #alternative version
    # Option          "ModeValidation" "" may need to use this to disable EDID more
    Option 	   "NvAGP" "2"
    Option 	   "NoLogo" "1"
    Option 	   "RenderAccel" "1"
    Option 	   "CursorShadow" "1"
    Option 	   "Coolbits" "1"
    Option 	   "NoPowerConnectorCheck" "True"
    # Option 	   "TwinView"
    # Option 	   "TwinView" "1"
    # Option 	   "Metamodes" "1680x1050,1680x1050"
    # Option 	   "Metamodes" "1680x1050,1680x1050; 1680x1050,NULL"
    # Option         "TwinViewOrientation" "RightOf"
    Option 	   "HorizSync"   "CRT-0: 30-82; CRT-1: 30-82"
    Option 	   "VertRefresh" "CRT-0: 30-82; CRT-1: 30-82"
    # Option         "NoTwinViewXineramaInfo"    #this option can be used to make windows span by default
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0, CRT-1"
    # Option         "metamodes" "CRT: 1680x1050 +0+0, CRT: 640x480 +1680+0"
    Option         "metamodes" "CRT: 1680x1050 +0+0, CRT: 1680x1050 +1680+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

