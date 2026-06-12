---
title: "Does any external widescreen work with ATI Radeon XPRESS 200M"
date: 2007-11-15
forum: Multimedia &amp; Video
---

### Post by medievalvent on 2007-11-15
Hi,

It looks like most ATI card users are having a lot of problems. I would first like to thank the writers of all the posts who helped me get to this stage in my struggle. I installed the proprietary ATI drivers and the Catalyst Control Center in Ubuntu 7.10. I now run two monitors with resolutions of 1280x800 and 1600x1200 with a ATI Radeon Xpress 200m card. 

However, I tried three different widescreen monitors so far, a SOYO (1680x1050), a Samsung (1680x1050) and now, NEC (1440x900). Somehow, the computer always detects them as 1600x1200 normal monitors and proceeds to show that resolution. I have spent a good five or six days fiddling with it, and every time I try to do something different, I get the X low resolution mode. I have un-installed and re-installed ati proprietary drivers several times now.  

I have plugged in the refresh and frequency values, which are invariably rejected by X. I have tried "DDC" "false" and plugged in the modeline. What is below is the only set up that has worked so far and is there for those who would like to use it. It sets up two displays that run separately. Even that is fine, if the resolution were correct.

Does anyone have any idea about how I should go about this? I know 200M is a card of minimal capabilities, but I would assume that since it does have video out, it should support these fixed resolution monitors regardless of speed. 

Any help would be much appreciated. 

Here's my xconf file.


Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice "stylus"	"SendCoreEvents"
#	InputDevice "cursor"	"SendCoreEvents"
#	InputDevice "eraser"	"SendCoreEvents"
Identifier "Default Layout"
Screen 0 "aticonfig-Screen[0]" 0 0
Screen "aticonfig-Screen[1]" LeftOf "aticonfig-Screen[0]"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option	 "CoreKeyboard"
Option	 "XkbRules" "xorg"
Option	 "XkbModel" "pc105"
Option	 "XkbLayout" "tr"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option	 "CorePointer"
Option	 "Device" "/dev/input/mice"
Option	 "Protocol" "ImPS/2"
Option	 "ZAxisMapping" "4 5"
Option	 "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option	 "SendCoreEvents" "true"
Option	 "Device" "/dev/psaux"
Option	 "Protocol" "auto-dev"
Option	 "HorizEdgeScroll" "0"
EndSection

Section "InputDevice"
Identifier "stylus"
Driver "wacom"
Option	 "Device" "/dev/input/wacom"
Option	 "Type" "stylus"
Option	 "ForceDevice" "ISDV4"	 # Tablet PC ONLY
EndSection

Section "InputDevice"
Identifier "eraser"
Driver "wacom"
Option	 "Device" "/dev/input/wacom"
Option	 "Type" "eraser"
Option	 "ForceDevice" "ISDV4"	 # Tablet PC ONLY
EndSection

Section "InputDevice"
Identifier "cursor"
Driver "wacom"
Option	 "Device" "/dev/input/wacom"
Option	 "Type" "cursor"
Option	 "ForceDevice" "ISDV4"	 # Tablet PC ONLY
EndSection

Section "Monitor"
Identifier "aticonfig-Monitor[0]"
Option	 "VendorName" "ATI Proprietary Driver"
Option	 "ModelName" "Generic Autodetecting Monitor"
Option	 "DPMS" "true"
EndSection

Section "Monitor"
Identifier "aticonfig-Monitor[1]"
Option	 "VendorName" "ATI Proprietary Driver"
Option	 "ModelName" "Generic Autodetecting Monitor"
Option	 "DPMS" "true"
EndSection

Section "Device"
Identifier "aticonfig-Device[0]"
Driver "fglrx"
BusID "PCI:1:5:0"
EndSection

Section "Device"
Identifier "aticonfig-Device[1]"
Driver "fglrx"
BusID "PCI:1:5:0"
Screen 1
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

---

