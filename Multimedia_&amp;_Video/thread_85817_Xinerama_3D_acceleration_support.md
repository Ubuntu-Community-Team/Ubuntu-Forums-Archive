---
title: "Xinerama 3D acceleration support"
date: 2005-11-03
forum: Multimedia &amp; Video
---

### Post by sleepkreep on 2005-11-03
I have read that it is not possible to use 3D acceleration on a dual monitor system.  I was wondering if someone knew a way around this.  I'm using Hoary.

Here is my current xorg.conf file:


Section "Files"
 FontPath "unix/:7100"   # local font server
 # if the local font server has problems, we can fall back on these (we always have problems)
 FontPath "/usr/lib/X11/fonts/misc"
 FontPath "/usr/lib/X11/fonts/cyrillic"
 FontPath "/usr/lib/X11/fonts/100dpi/:unscaled"
 FontPath "/usr/lib/X11/fonts/75dpi/:unscaled"
 FontPath "/usr/lib/X11/fonts/Type1"
 FontPath "/usr/lib/X11/fonts/CID"
 FontPath "/usr/lib/X11/fonts/100dpi"
 FontPath "/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
 FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
 FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
 Load "bitmap"
 Load "dbe"
 Load "ddc"
 Load "dri"
 Load "extmod"
 Load "freetype"
 Load "glx"
 Load "int10"
 Load "record"
 Load "type1"
 Load "vbe"
EndSection

Section "InputDevice"
 Identifier "Generic Keyboard"
 Driver  "keyboard"
 Option  "CoreKeyboard"
 Option  "XkbRules" "xorg"
 Option  "XkbModel" "pc104"
 Option  "XkbLayout" "us"
EndSection

Section "InputDevice"
 Identifier "Configured Mouse"
 Driver  "mouse"
 Option  "CorePointer"
 Option  "Device"  "/dev/input/mice"
 Option  "Protocol"  "ImPS/2"
 Option  "Emulate3Buttons" "true"
 Option  "ZAxisMapping"  "4 5"
EndSection

Section "Device"
 Identifier "Intel Corporation 82865G Integrated Graphics Device"
 Driver  "i810"
 BusID  "PCI:0:2:0"
EndSection

Section  "Device 
 Identifier      "ati radeon"
 Driver          "radeon"
 BusID           "PCI:1:0:0"
 Option "BusType"         "PCI"
 Option  "RenderAccel" "true"
# Option "OpenGLOverlay" "1"
 Option "EnablePageFlip" "true"
EndSection

Section "Monitor"
 Identifier "Generic Monitor"
 Option  "DPMS"
 HorizSync 30-65
 VertRefresh 50-75
EndSection

Section "Monitor"
 Identifier      "New Monitor"
 Option          "DPMS"
 HorizSync       30-65
 VertRefresh     50-75
EndSection

Section "Screen"
 Identifier "Default Screen"
 Device  "Intel Corporation 82865G Integrated Graphics Device"
 Monitor  "Generic Monitor"
 DefaultDepth 24
 SubSection "Display"
  Depth  1
  Modes  "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  4
  Modes  "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  8
  Modes  "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  15
  Modes  "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  16
  Modes  "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  24
  Modes  "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
EndSection

Section "Screen"
 Identifier "New Screen"
 Device "ati radeon" 
 Monitor "New Monitor"
 DefaultDepth 24
 SubSection "Display"
                Depth          24 
                Modes          "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection

 SubSection "Display"
  Depth  16
  Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
EndSection

Section "ServerLayout"
 Identifier "Default Layout"
 Screen 0 "New Screen" RightOf "Default Screen"
 Screen 1        "Default Screen" 0 0
 Option          "Xinerama" "on"

 InputDevice "Generic Keyboard"
 InputDevice "Configured Mouse"
EndSection

Section "DRI"
 Mode 0666
EndSection

---

