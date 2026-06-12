---
title: "No sound after install:"
date: 2006-01-05
forum: Multimedia &amp; Video
---

### Post by Mcjensen on 2006-01-05
After install, my sound doesnt work here...though it still works on my 1st hard drive with windows 2000...Ive have allegro sound card, any suggestions, McJensen


[COLOR="Red"]# /etc/X11/xorg.conf (xorg X Window System server configuration file)[/COLOR]
Section "Files"
FontPath "/usr/share/X11/fonts/misc"
FontPath "/usr/share/X11/fonts/cyrillic"
FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
FontPath "/usr/share/X11/fonts/Type1"
FontPath "/usr/share/X11/fonts/CID"
FontPath "/usr/share/X11/fonts/100dpi"
FontPath "/usr/share/X11/fonts/75dpi"
# paths to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
Load "GLcore"
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

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "dk"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "Emulate3Buttons" "true"
Option "ZAxisMapping" "4 5"
EndSection

Section "Device"
Identifier "Trident Microsystems CyberBlade/i7"
Driver "trident"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "HP D8905"
Option "DPMS"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Trident Microsystems CyberBlade/i7"
Monitor "HP D8905"
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

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
EndSection

Section "DRI"
Mode 0666
EndSection

---

### Post by stratotak on 2006-01-05
your xorg.config dosent have anything to do with sound..just graphics,keyboard,monitor,mouse....    im no linux expert but id start of and see if any sound modules for my card are loaded  ..do  lsmod ..check in sound preference to see if its set to alsa..and also can  run  alsaconf  from console..if alsa supports your card it should work..if not maybe try using oss instead.

---

