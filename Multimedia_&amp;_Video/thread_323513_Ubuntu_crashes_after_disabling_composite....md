---
title: "Ubuntu crashes after disabling composite..."
date: 2006-12-22
forum: Multimedia &amp; Video
---

### Post by karbar on 2006-12-22
Hi!
Problems with ati drivers are common, but i couldn't find solution for my problem.
I skim this forum, google and Polish ubuntu's forum without result.

I have Ubuntu 6.10 and Ati Raedon 9100.
I tried to install drivers from repo... and official ati's automated installer (ati-driver-installer-8.28.8). In both cases reaction is the same: I have no 3d acceleration and stable Ubuntu or, after modify xorg.conf and disabling composite, I have 3d acceleration for a while, then Ubuntu immidiately crashes (no response for any action)

My xorg.conf is:

> Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen" 0 0
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
EndSection

Section "Files"

# path to defoma fonts
FontPath "/usr/share/X11/fonts/misc"
FontPath "/usr/share/X11/fonts/cyrillic"
FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
FontPath "/usr/share/X11/fonts/Type1"
FontPath "/usr/share/X11/fonts/100dpi"
FontPath "/usr/share/X11/fonts/75dpi"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection

Section "ServerFlags"
Option "AIGLX" "off"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "pl"
Option "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

# /dev/input/event
# for USB
Identifier "stylus"
Driver "wacom"
Option "Device" "/dev/wacom" # Change to
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"

# /dev/input/event
# for USB
Identifier "eraser"
Driver "wacom"
Option "Device" "/dev/wacom" # Change to
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"

# /dev/input/event
# for USB
Identifier "cursor"
Driver "wacom"
Option "Device" "/dev/wacom" # Change to
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Monitor"
Identifier "AOC Spectrum"
#HorizSync 30.0 - 95.0
#VertRefresh 50.0 - 160.0
Option "DPMS"
EndSection

Section "Device"
Identifier "ATI Technologies, Inc. Radeon R200 QM [Radeon 9100]"
Driver "fglrx"
#Option "VideoOverlay" "on"
#Option "OpenGLOverlay" "off"
BusID "PCI:1:0:0"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Radeon R200 QM [Radeon 9100]"
Monitor "AOC Spectrum"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
	Option "Composite" "Disable"
EndSection

Thank you for your help.
Sorry about my english

---

