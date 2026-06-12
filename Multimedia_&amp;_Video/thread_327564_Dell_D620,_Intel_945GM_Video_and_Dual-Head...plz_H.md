---
title: "Dell D620, Intel 945GM Video and Dual-Head...plz HELP!"
date: 2006-12-29
forum: Multimedia &amp; Video
---

### Post by geek777 on 2006-12-29
Hi All,

I just got a D620 as a corporate desktop replacement (I order desktop and they ship this thing instead).  Anyway, I immediately smoked the corp. Os image and put 6.06 LTS on it (Edgy kernel panics due to Duo Core with base kernel on install CD).

I installed latest Intel drivers and 915resolution to get native 1440x900...all good.

Problem comes though when i try to do dual-head monitors thru my D/Port / Port replicator (I guess this is what it's called).  the port replicator has VGA and DVI out and from Dells website, I know the WindBlowz XP driver will support dual-out with the latop LCD closed.  

I need the same capability with Ubuntu.   So far, I have had almost no luck running dual out from the docking base.  I use Fn-F8 to toggle external output and I am able to get video on 1 of my two external LCD Flat panels...and the laptop LCD...in this condition, the External FP LCD clearly has a frequency issues as it simply shakes.  Also, this External FP LCd image is a clone of the laptop LCD.

Any ideas or hints greatly appreciated.

Thnx.

P.S.  Attached is my xorg.conf:

<I lied...it won't attach...>

~~~snip~~~
Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "Emulate3Buttons"       "on"
        Option          "SHMConfig"             "on"
        Option          "LeftEdge"      "85"
        Option          "RightEdge"     "1010"
        Option          "TopEdge"       "85"
        Option          "BottomEdge"    "730"
        Option          "FingerLow"     "25"
        Option          "FingerHigh"    "30"
        Option          "MaxTapTime"    "180"
        Option          "MaxTapMove"    "220"
        Option          "VertScrollDelta"       "100"
        Option          "MinSpeed"      "0.10"
        Option          "MaxSpeed"      "0.60"
        Option          "AccelFactor"   "0.2"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "i945GM"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option "MonitorLayout" "LFP,LFP"
EndSection

Section "Device"
        Identifier      "i945GM2"
        Driver          "i810"
        BusID           "PCI:0:2:1"     
        Option "MonitorLayout" "LFP,LFP"
EndSection

Section "Monitor"
        Identifier      "monitor1"      
        Option          "DPMS"
        #HorizSync      28-72
        #VertRefresh    43-60
EndSection

Section "Monitor"
        Identifier      "monitor2"
        Option          "DPMS"
        #HorizSync       28-72
        #VertRefresh     43-60

EndSection
  
Section "Screen"
        Identifier      "Default Screen"
        Device          "i945GM"
        Monitor         "monitor1"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1440x900" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1440x900" "1280x1024" "1024x768" "800x600" "640

x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1440x900" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1440x900" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1440x900" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1440x900" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Second Screen"
        Device          "i945GM2"
        Monitor         "monitor2"
        DefaultDepth    24
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        #Screen         "Default Screen"
        Screen  0 "Default Screen" 0 0
        Screen  1 "Second Screen" LeftOf "Default Screen"
        Option          "Xinerama"  "On"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"

---

### Post by imonarock on 2007-05-07
Anyone getting this working?

---

### Post by misconfiguration on 2007-05-08
I have the same chipset on an ACER Aspire 5610z I'm unable to successfully get cedega to work, glxinfo and glxgears fails, how did you guys install drivers for this?

I'm currently using driver i810, is there an actual INTEL driver I can get from repositories? OpenGL 3d Rendering fails for me, odd issue here. =/

---

