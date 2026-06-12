---
title: "Problems with composite out on N6200"
date: 2007-09-19
forum: Multimedia &amp; Video
---

### Post by kalias on 2007-09-19
Hi!  I am having trouble getting the composite output to work on my N6200 card.  I have it to the point where the splash screen comes up on the tv, I can see text, but when the computer switches over to graphics, the tv goes black.  I am currently running my crt and tv at the same time.  Here is my xorg.conf.

# Xorg configuration created by system-config-display

Section "ServerLayout"
Identifier "single head configuration"
Screen 0 "Screen0" 0 0
InputDevice "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
ModulePath "/usr/lib/xorg/modules/extensions/nvidia"
ModulePath "/usr/lib/xorg/modules/extensions"
ModulePath "/usr/lib/xorg/modules"
EndSection

Section "InputDevice"
Identifier "Keyboard0"
Driver "kbd"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "Monitor"

### Comment all HorizSync and VertSync values to use DDC:
Identifier "Monitor1"
VendorName "Monitor Vendor"
#ModelName "Monitor 800x600"
# wjk changed
ModelName "Samsung SyncMaster"
### Comment all HorizSync and VertSync values to use DDC:
HorizSync 31.5 - 35.1
VertRefresh 50.0 - 61.0
Option "dpms"
EndSection

Section "Device"
Identifier "Videocard0"
Driver "nvidia"
## added by wjk
VendorName "NVIDIA Corporation"
BoardName "GeForce 6200"
Option "TVStandard" "NTSC-M"
Option "TVOutFormat" "COMPOSITE"
Option "TVOverScan" "0.5"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Videocard0"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
EndSubSection
EndSection

Can anyone see any problems with this?

thx :)

kalias

---

