---
title: "svideo out ti4600?"
date: 2005-11-11
forum: Multimedia &amp; Video
---

### Post by October on 2005-11-11
Desperately in need of help!

Trying to get my wife's nvidia ti4600 ultra to "clone" twinview to our tv.

Here is the xfree conf from our older mepis install... taking the relevant bits out and transplanting them to ubuntu's xorg.conf does nothing...  Anyone else have svideo twinview clone working on an nvidia ti card?  If so, please share your xorg.conf?

Thanks in advance!

> 
Section "ServerLayout"
Identifier "XFree86 Configured"
Screen 0 "Screen0" 0 0
InputDevice "Keyboard0" "CoreKeyboard"
#InputDevice "PS/2 Mouse" "CorePointer"
InputDevice "USB Mouse" "CorePointer"
#InputDevice "Serial Mouse" "CorePointer"
EndSection

Section "ServerFlags"
Option "AllowMouseOpenFail" "true"
EndSection

Section "Files"
RgbPath "/usr/X11R6/lib/X11/rgb"
ModulePath "/usr/X11R6/lib/modules"
FontPath "/usr/X11R6/lib/X11/fonts/misc:unscaled"
FontPath "/usr/X11R6/lib/X11/fonts/misc"
FontPath "/usr/X11R6/lib/X11/fonts/75dpi:unscaled"
FontPath "/usr/X11R6/lib/X11/fonts/75dpi"
FontPath "/usr/X11R6/lib/X11/fonts/100dpi:unscaled"
FontPath "/usr/X11R6/lib/X11/fonts/100dpi"
FontPath "/usr/X11R6/lib/X11/fonts/Speedo"
FontPath "/usr/X11R6/lib/X11/fonts/PEX"
FontPath "/usr/X11R6/lib/X11/fonts/cyrillic"
# True type and type1 fonts
FontPath "/usr/share/fonts/truetype/ttf-xfree86-nonfree"
FontPath "/usr/share/fonts/truetype/java"
FontPath "/usr/share/fonts/truetype/freefont"
FontPath "/usr/share/fonts/truetype/openoffice"
FontPath "/usr/share/fonts/truetype/ttf-bitstream-vera"
FontPath "/usr/share/fonts/ttf/western"
FontPath "/usr/share/fonts/ttf/decoratives"
FontPath "/usr/share/fonts/type1/gsfonts"
FontPath "/usr/X11R6/lib/X11/fonts/Type1"
FontPath "/usr/X11R6/lib/X11/fonts/defoma/CID"
FontPath "/usr/X11R6/lib/X11/fonts/defoma/TrueType"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"

EndSection

Section "Module"
# Load "GLcore"
Load "bitmap"
Load "dbe"
# Load "ddc"
# Load "dri"
Load "extmod"
Load "v4l"
Load "freetype"
Load "glx"
# Load "int10"
# Load "record"
Load "speedo"
Load "type1"
# Load "vbe"
EndSection

Section "InputDevice"
Identifier "Keyboard0"
Driver "keyboard"
Option "CoreKeyboard"
Option "XkbRules" "xfree86"
Option "XkbModel" "pc105"
Option "XkbLayout" "defkeymap"
EndSection

Section "InputDevice"
Identifier "Serial Mouse"
Driver "mouse"
Option "Protocol" "Microsoft"
Option "Device" "/dev/ttyS0"
Option "Emulate3Buttons" "false"
Option "Emulate3Timeout" "70"
EndSection

Section "InputDevice"
Identifier "PS/2 Mouse"
Driver "mouse"
Option "Protocol" "auto"
Option "Device" "/dev/psaux"
Option "Emulate3Buttons" "false"
Option "Emulate3Timeout" "70"
Option "ZAxisMapping" "4 5"
Option "Buttons" "5"
EndSection

Section "InputDevice"
Identifier "USB Mouse"
Driver "mouse"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "Buttons" "5"
EndSection

Section "Monitor"
Identifier "Monitor0"
VendorName "Plug'n Play"
HorizSync 30-70
VertRefresh 50-160

# Sony Vaio C1(X,XS,VE,VN)?
# 1024x480 @ 85.6 Hz, 48 kHz hsync
ModeLine "1024x480" 65.00 1024 1032 1176 1344 480 488 494 563 -hsync -vsync

# TV fullscreen mode or DVD fullscreen output.
# 768x576 @ 79 Hz, 50 kHz hsync
ModeLine "768x576" 50.00 768 832 846 1000 576 590 595 630

# 768x576 @ 100 Hz, 61.6 kHz hsync
ModeLine "768x576" 63.07 768 800 960 1024 576 578 590 616
EndSection

Section "Device"
#Option "sw_cursor" # needed for some ati cards
#Option "hw_cursor"
#Option "NoAccel"
#Option "ShowCache"
#Option "ShadowFB"
#Option "UseFBDev"
#Option "Rotate"
#Option "NoUseBios" # needed for some Savage cards
# nvidia special options, use with care
Option "CursorShadow" "1"
Option "CursorShadowAlpha" "63"
Option "CursorShadowYOffset" "2"
Option "CursorShadowXOffset" "4"
# Option "FlatPanelProperties" "Scaling = native"
Option "NoLogo" "false"
Option "IgnoreEdid" "true" # needs to be true for some nvidia cards
Identifier "Card0"
VendorName "NVidia"
BoardName "NVIDIA GeForce ti4600 (generic)"
Driver "nvidia"
#BusID "PCI:1:0:0"
# Only the official NVIDIA driver supports twinview
# these setting are an example
Option "DPMS"
#Option "NvAGP" "3"
Option "TwinView"
Option "TwinViewOrientation" "Clone"
Option "ConnectedMonitor" "CRT-0,TV-0"
Option "MetaModes" "1024x768,1024x768"
Option "TVStandard""NTSC-M"
Option "SecondMonitorHorizSync" "30-50"
Option "SecondMonitorVertRefresh" "60"
Option "TVOutFormat" "SVIDEO"
EndSection


Section "Screen"
Identifier "Screen0"
Device "Card0"
Monitor "Monitor0"
DefaultColorDepth 16
SubSection "Display"
Depth 1
Modes "1024x768""800x600"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768""800x600"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768""800x600"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768""800x600"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024""1024x768""800x600"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024""1024x768""800x600"
EndSubSection
SubSection "Display"
Depth 32
Modes "1280x1024""1024x768""800x600"
EndSubSection
EndSection

#Section "DRI"
# Mode 0666
#EndSection


---

