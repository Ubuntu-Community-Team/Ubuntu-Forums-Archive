---
title: "nvidia 3 monitor setup?"
date: 2006-08-29
forum: Multimedia &amp; Video
---

### Post by elglas on 2006-08-29
Hi there, yet another support question.

after following the previous how to i have been unable to get a second nvidia pci card to work.  here is the X11 config file and the relevant PCI data

```

0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1) (prog-if 00 [VGA])
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 185
        Memory at e1000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Expansion ROM at e2000000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:00:0b.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2) (prog-if 00 [VGA])
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 201
        Memory at e0000000 (32-bit, non-prefetchable) [disabled] [size=16M]
        Memory at d8000000 (32-bit, prefetchable) [disabled] [size=128M]
        Expansion ROM at 30020000 [disabled] [size=64K]
        Capabilities: <available only to root>

```

```

#Mike's most evil xorg.conf file
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg
###################################
# ubuntu default files and device #
###################################
Section "Files"
  FontPath "/usr/share/X11/fonts/misc"
  FontPath "/usr/share/X11/fonts/cyrillic"
  FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
  FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
  FontPath "/usr/share/X11/fonts/Type1"
  FontPath "/usr/share/X11/fonts/100dpi"
  FontPath "/usr/share/X11/fonts/75dpi"
  # path to defoma fonts
  FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "InputDevice"
  Identifier "Keyboard1"
  Driver "kbd"
  option "CoreKeyboard"
  option "XkbRules" "xorg"
  option "XkbModel" "pc104"
  option "XkbLayout" "us"
EndSection

Section "InputDevice"
  Identifier "Mouse1"
  Driver "mouse"
  option "CorePointer"
  option "Device" "/dev/input/mice"
  option "Protocol" "ExplorerPS/2"
  option "ZAxisMapping" "4 5"
  option "Emulate3Buttons" "true"
  option "Buttons" "5"
EndSection

################
# server flags #
################

Section "ServerFlags"
Option "DefaultServerLayout" "DUALSCREEN"
Option "AllowDeactivateGrabs" "true"
Option "AllowClosedownGrabs" "true"
Option "AllowMouseOpenFail" "true"
EndSection

##################
# Module section #
##################
Section "Module"
Load "dbe" # Double buffer extension
SubSection "extmod"
Option "omit xfree86-dga" # don't initialise the DGA extension
EndSubSection
Load "type1"
Load "freetype"
Load "glx"
Load "record"
Load "evdev"
Load "xtrap"
# Load "extmod"
# Load "v41"
# Load "speedo"
# Load "bitmap"
# Load "ddc"
# Load "dri"
# Load "int10"
# Load "vbe"
EndSection

#Section "Extensions"
# Option "Composite" "Enable"
#EndSection 

####################
# Acer LCD Monitor # 
####################

Section "Monitor"
  identifier "Monitor1"
  vendorname "Plug 'n' Play"
  modelname "Plug 'n' Play"
  option "DPMS" 
 # gamma 1.0
EndSection

Section "Monitor"
  Identifier "Monitor2"
  VendorName "generic"
  #HorizSync 30-107
  #VertRefresh 50-160
  Option "DPMS"
EndSection

#######################
# second card monitor #
#######################

Section "Monitor"
  Identifier "Monitor3"
  VendorName "generic"
  HorizSync 30-107
  VertRefresh 50-160
  #Option "DPMS"
EndSection


Section "Device"
Identifier "Videocard2"
#VideoRam 128000
Driver "nv"
#Option "HWCursor" "On"
BusID "PCI:0:11:0"
Screen 1
EndSection

Section "Device"
Identifier "twinview"
VideoRam 256000
VendorName "nVidia Corporation"
BoardName "Video device"
Driver "nvidia"
BusID "PCI:1:0:0"
Screen 0
Option "TwinView"
Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
Option "TwinViewOrientation" "LeftOf"
Option "SecondMonitorHorizSync""UseEdidFreqs"
Option "SecondMonitorVertRefresh" "UseEdidFreqs"
Option "HWCursor" "On"
Option "UseEdidFreqs" "true"
Option "NvAGP" "1"
# Option "NoLogo" "true"
# Option "RenderAccel" "true"
# Option "CursorShadow" "true"
# Option "XvmcUsesTextures" "true"
EndSection

Section "Screen"
Identifier "twinviewscreen"
Device "twinview"
Monitor "Monitor1"

DefaultDepth 24

Subsection "Display"
    Depth 8
    Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubsection
Subsection "Display"
    Depth 16
    Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubsection
Subsection "Display"
    Depth 24
    Modes "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
EndSubsection
Subsection "Display"
    Depth 32
    Modes "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
EndSubsection

EndSection

Section "Screen"
Identifier "Screen1"
Device "Videocard2"
Monitor "Monitor3"

DefaultDepth 24

Subsection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubsection
Subsection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubsection
Subsection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubsection
Subsection "Display"
Depth 32
Modes "1024x768" "800x600" "640x480"
EndSubsection
EndSection

#
# 2 MONITORS, ONE CARD
#
#Section "ServerLayout"
#Identifier "TWINVIEW"
#Screen "twinviewscreen"
#InputDevice "Mouse1" "CorePointer"
#InputDevice "Keyboard1" "CoreKeyboard"
#Endsection

Section "ServerLayout"
Identifier "DUALSCREEN"
Screen 0 "twinviewscreen" 0 0
Screen 1 "Screen1" LeftOf "twinviewscreen"
InputDevice "Mouse1" "CorePointer"
InputDevice "Keyboard1" "CoreKeyboard"
EndSection


Section "DRI"
  Mode 0666
EndSection

```

---

