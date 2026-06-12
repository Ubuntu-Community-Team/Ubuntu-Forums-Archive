---
title: "DFP monitor after installing nvidia drivers"
date: 2007-06-27
forum: Multimedia &amp; Video
---

### Post by redheat on 2007-06-27
Before I begin I want to say that I installed the Nvidia drivers using the both Tseliot Alberto Morino's Way and also Nvidia's way listed as a sticky on their Linuxforum: 

 [http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

 my system specs are as follows:
 I have a Gigabyte GA-965P-DS3 (ver 3.3), a Viewsonic 20.1" VX2025WM monitor, a XFX 8600 GT video card, oh and E6600 Pentium Core 2 Duo processor. The drivers' for my video card are the 100.14.11. the installation process went as smooth and by the book no error popped-up everything went ok. Not even the famous API mismatch disregarding which method used the result was the same, the moment I restart and login I get faced with a 640x480 resolution and a monitor named DFP-0!? I just have one monitor, the viewsonic VX2025wm connected to my video card, though my video card can support dual link, I only have one connected through a DVI connection to my video card and that's it. Nothing else.

 This is the xorg file I got: 

```
Section "Files"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/usr/share/fonts/X11/cyrillic"
FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
FontPath "/usr/share/fonts/X11/Type1"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
# path to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/input/wacom"
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/input/wacom"
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/input/wacom"
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/input/wacom"
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/input/wacom"
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/input/wacom"
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/input/wacom"
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Device"
Identifier "Generic Video Card"
Driver "nvidia"
BusID "PCI:1:0:0"
EndSection

EndSection

Section "Device"
Identifier "Generic Video Card"
Driver "nvidia"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-51
VertRefresh 43-60
EndSection

Section "Screen"
Section "Screen"
Identifier "Default Screen"
Device "Generic Video Card"
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

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
EndSection

```

 Just one more thing, the option of enabling the nvidia drivers through the restricted drivers manager never worked for me either before installing the nvidia drivers or after. I'm always faced with a message saying: "your hardware needs no restricted drivers" ...

 also here's a post with the same name I made on nvidia's linuxforum with the same name:

[http://www.nvnews.net/vbulletin/showthread.php?t=93707](http://www.nvnews.net/vbulletin/showthread.php?t=93707)

I would truely appreciate some help

regards
redheat

---

### Post by redheat on 2007-06-29
can someone please tell me what's the problem with the above x config file.. I mean anything...does the nvidia device see my monitor, and if so why does it denote it as DFP monitor with a max resolution of 640x480? when I uninstall the nvidia driver, the system sees my monitor with maximum resolution of 1680x1050 which is the native resolution for my monitor.

 please any help? cause I've had it..

regards
redheat

---

