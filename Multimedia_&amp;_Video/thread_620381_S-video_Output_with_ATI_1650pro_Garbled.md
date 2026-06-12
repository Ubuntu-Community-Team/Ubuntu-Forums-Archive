---
title: "S-video Output with ATI 1650pro Garbled"
date: 2007-11-22
forum: Multimedia &amp; Video
---

### Post by ropsta on 2007-11-22
Hello. 

I've been trying to get my video card to work with s-video output.  At first I got nothing but blue screens when I connected the s-video. Screens were found but were unusable... However, after hours of searching and reconfiguring the xorg.conf I finally found a setup that intialized the output with any errors. That's not to say there are no problems.

The video on the TV is in black and white and jumps violently.  Also, the monitor turns off,  so the way only to make adjustments is with a ctrl+alt+F1 deal (the only way to bring it back on).

This is my current configuration. I'm usually more inclined to exhaust all possibilities myself.  I'm completely stumped, though, and any help youz genii can afford me will be most appreciated

```
Section "ServerLayout"
Identifier "Default Layout"
Screen 0 "aticonfig-Screen[0]" 0 0
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
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
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
Load "v4l"
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
Option "XkbModel" "pc104"
Option "XkbLayout" "us"
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
Identifier "Generic Monitor"
HorizSync 28.0 - 49.0
VertRefresh 43.0 - 72.0
Option "DPMS"
EndSection

Section "Monitor"
Identifier "aticonfig-Monitor[0]"
Option "VendorName" "ATI Proprietary Driver"
Option "ModelName" "Generic Autodetecting Monitor"
Option "DPMS" "true"
EndSection

Section "Monitor"
Identifier "aticonfig-Monitor[1]"
Option "VendorName" "ATI Proprietary Driver"
Option "ModelName" "Generic Autodetecting Monitor"
Option "DPMS" "true"
EndSection

Section "Device"
Identifier "ATI Technologies, Inc. [Radeon 1650 pro]"
Driver "fglrx"
BusID "PCI:2:0:0"
EndSection

Section "Device"
Identifier "aticonfig-Device[0]"
Driver "fglrx"
Option "DesktopSetup" "single"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
BusID "PCI:2:0:0"
EndSection

Section "Device"
Identifier "aticonfig-Device[1]"
Driver "ati"
BusID "PCI:2:0:1"
Screen 1
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. [Radeon 1650 pro]"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "Screen"
Identifier "aticonfig-Screen[0]"
Device "aticonfig-Device[0]"
Monitor "aticonfig-Monitor[0]"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
EndSubSection
EndSection

Section "Screen"
Identifier "aticonfig-Screen[1]"
Device "aticonfig-Device[1]"
Monitor "aticonfig-Monitor[1]"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
EndSubSection
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection

```

If youz guyz need more just lemme know.

---

### Post by ropsta on 2007-11-23
Strange... whenever I hit the search button it returns no results unless I search by username....:(

---

### Post by ropsta on 2007-11-30
Sadness :(

Guess I should have researched a bit more on compatibility before I bought this card.

---

### Post by ropsta on 2008-04-08
So, I've got Beryl and Compiz and the likes to work. 

I just need to get this card working with S-video output to remove myself from windows totally. 

I just need someone to confirm that this card actually works with S-video output under Linux. Doesn't have to be Ubuntu. I just need to know it works.

Correction, I just need to know it works properly. I got S-video to show on the TV a few times, but the color was gone and screen was jumpy, like the olden days when we had antennas on them.

Any of youz out there...:confused:

PS xrandr only detects "default" display.

---

### Post by ropsta on 2008-07-22
I figured I'd give this another bump. I've learn enough to drive the average person mad and I'm still not having any luck with this...

:(

---

