---
title: "Screen Res problems Ubuntu based Mepis 6"
date: 2006-08-08
forum: Multimedia &amp; Video
---

### Post by Kiwi-Hawk on 2006-08-08
Hi

I have installed Mepis 6 RC2 and done all the updates etc and installed the Nvidia drivers
and have duel screen working on my Intel 64bit system with 1gig ram and a Galaxy CeForce 7 series 7600 vidion card I have at this time got a KDE 3.5.3 desktop and get this wee msg if I go to configure desktop > Display:

Your X Server does not support resizing and rotating the display. Please update to version 4.3 or greater. You need the X Resize and Roate extemtion (RANDR) version 1.1 or greater to use this feature.

Before you shoot me for being in the wrong place I did post this in the Mepis group also and it was sujested that as this is based on Ubuntu I ask here.

I will include my xorg.conf incase that has errors in it,.. I should mention too I guess that screen0 is a VX922 ViewSonic LCD and screen1 is a 7F AOC CRT.

========================================================

Section "Device"
  Identifier  "NVIDIA0"
  Driver "nvidia"
  BoardName "Galaxy 7600"
  Option "RenderAccel" "true"
  Option "AllowGLXWithComposite" "true"
  Option "UseDisplayDevice" "DFP"
  Option "IgnoreEdid" "False" # needs to be true for some nvidia cards
  BusID  "PCI:06:00:0"
  Screen 0
EndSection

Section "Device"
  Identifier  "NVIDIA1"
  Driver "nvidia"
  BoardName "Galaxy 7600"
  Option "RenderAccel" "true"
  Option "AllowGLXWithComposite" "true"
  Option "UseDisplayDevice" "CRT"
  Option "IgnoreEdid" "False" # needs to be true for some nvidia cards
  BusID  "PCI:06:00:0"
  Screen 1
EndSection

Section "Monitor"
  Identifier "Monitor0"
  VendorName "ViewSonic"
  ModelName "VX922"
  Option "DPMS" "true"
  HorizSync    30-82
  VertRefresh  50-85
  Modeline "640x480"     25.175 640  664  760  800   480  491  493  525 #60Hz
  Modeline "800x600"     40.12  800  848  968 1056   600  601  605  628 #60Hz
  Modeline "1024x768"    75    1024 1048 1184 1328   768  771  777  806 -hsync -vsync
  Modeline "1024x768"    85    1024 1056 1152 1360   768  784  787  823
  ModeLine "1152x864"    65    1152 1168 1384 1480   864  865  875  985 Interlace
  Modeline "1152x864"    92    1152 1208 1368 1474   864  865  875  895
  Modeline "1152x864"   110    1152 1240 1324 1552   864  864  876  908
  Modeline "1152x864"   135    1152 1464 1592 1776   864  864  876  908
  Modeline "1152x864"   137.65 1152 1184 1312 1536   864  866  885  902 -HSync -VSync
  Modeline "1280x768"    80.14 1280 1344 1480 1680   768  769  772  795
  ModeLine "1280x800"    80.58 1280 1344 1480 1680   800  801  804  827 -HSync -VSync
  Modeline "1280x1024"   80    1280 1296 1512 1568  1024 1025 1037 1165 Interlace
  Modeline "1280x1024"  110    1280 1328 1512 1712  1024 1025 1028 1054
  Modeline "1280x1024"  126.5  1280 1312 1472 1696  1024 1032 1040 1068 -HSync -VSync
  Modeline "1280x1024"  135    1280 1312 1456 1712  1024 1027 1030 1064
  Modeline "1280x1024"  135    1280 1312 1416 1664  1024 1027 1030 1064
  Modeline "1280x1024"  157.5  1280 1344 1504 1728  1024 1025 1028 1072 +HSync +VSync
  Modeline "1280x1024"  181.75 1280 1312 1440 1696  1024 1031 1046 1072 -HSync -VSync
  Modeline "1440x900"   106.47 1440 1520 1672 1904   900  901  904  932 +HSync +VSync
  Modeline "1400x1050"  129    1400 1464 1656 1960  1050 1051 1054 1100 +HSync +VSync
  Modeline "1600x1200"  162    1600 1664 1856 2160  1200 1201 1204 1250 +HSync +VSync
  Modeline "1600x1200"  189    1600 1664 1856 2160  1200 1201 1204 1250 -HSync -VSync
  Modeline "1600x1200"  202.5  1600 1664 1856 2160  1200 1201 1204 1250 +HSync +VSync
  Modeline "1600x1200"  220    1600 1616 1808 2080  1200 1204 1207 1244 +HSync +VSync
  Modeline "1680x1050"  147.14 1680 1784 1968 2256  1050 1051 1054 1087
  ModeLine "1800x1440"  230    1800 1896 2088 2392  1440 1441 1444 1490 +HSync +VSync
  ModeLine "1800x1440"  250    1800 1896 2088 2392  1440 1441 1444 1490 +HSync +VSync
  Modeline "1920x1200"  230    1920 1936 2096 2528  1200 1201 1204 1250 +HSync +VSync
EndSection

Section "Monitor"
  Identifier  "Monitor1"
  VendorName "AOC"
  ModelName "7F"
  Option "DPMS" "true"
  HorizSync    30-72
  VertRefresh  50-130
  Modeline "640x480"     25.175 640  664  760  800   480  491  493  525 #60Hz
  Modeline "800x600"     40.12  800  848  968 1056   600  601  605  628 #60Hz
  Modeline "1024x768"    75    1024 1048 1184 1328   768  771  777  806 -hsync -vsync
  Modeline "1024x768"    85    1024 1056 1152 1360   768  784  787  823
  ModeLine "1152x864"    65    1152 1168 1384 1480   864  865  875  985 Interlace
  Modeline "1152x864"    92    1152 1208 1368 1474   864  865  875  895
  Modeline "1152x864"   110    1152 1240 1324 1552   864  864  876  908
  Modeline "1152x864"   135    1152 1464 1592 1776   864  864  876  908
  Modeline "1152x864"   137.65 1152 1184 1312 1536   864  866  885  902 -HSync -VSync
  Modeline "1280x768"    80.14 1280 1344 1480 1680   768  769  772  795
  ModeLine "1280x800"    80.58 1280 1344 1480 1680   800  801  804  827 -HSync -VSync
  Modeline "1280x1024"   80    1280 1296 1512 1568  1024 1025 1037 1165 Interlace
  Modeline "1280x1024"  110    1280 1328 1512 1712  1024 1025 1028 1054
  Modeline "1280x1024"  126.5  1280 1312 1472 1696  1024 1032 1040 1068 -HSync -VSync
  Modeline "1280x1024"  135    1280 1312 1456 1712  1024 1027 1030 1064
  Modeline "1280x1024"  135    1280 1312 1416 1664  1024 1027 1030 1064
  Modeline "1280x1024"  157.5  1280 1344 1504 1728  1024 1025 1028 1072 +HSync +VSync
  Modeline "1280x1024"  181.75 1280 1312 1440 1696  1024 1031 1046 1072 -HSync -VSync
  Modeline "1440x900"   106.47 1440 1520 1672 1904   900  901  904  932 +HSync +VSync
  Modeline "1400x1050"  129    1400 1464 1656 1960  1050 1051 1054 1100 +HSync +VSync
  Modeline "1600x1200"  162    1600 1664 1856 2160  1200 1201 1204 1250 +HSync +VSync
  Modeline "1600x1200"  189    1600 1664 1856 2160  1200 1201 1204 1250 -HSync -VSync
  Modeline "1600x1200"  202.5  1600 1664 1856 2160  1200 1201 1204 1250 +HSync +VSync
  Modeline "1600x1200"  220    1600 1616 1808 2080  1200 1204 1207 1244 +HSync +VSync
  Modeline "1680x1050"  147.14 1680 1784 1968 2256  1050 1051 1054 1087
  ModeLine "1800x1440"  230    1800 1896 2088 2392  1440 1441 1444 1490 +HSync +VSync
  ModeLine "1800x1440"  250    1800 1896 2088 2392  1440 1441 1444 1490 +HSync +VSync
  Modeline "1920x1200"  230    1920 1936 2096 2528  1200 1201 1204 1250 +HSync +VSync
EndSection

Section "Screen"
  Identifier "Screen0"
  Device "NVIDIA0"
  Monitor "Monitor0"
  DefaultColorDepth 24
 SubSection "Display"
  Depth  24
  Modes  "1280x1024, 1152x864, 1024x768"
 EndSubSection
EndSection

Section "Screen"
  Identifier "Screen1"
  Device "NVIDIA1"
  Monitor "Monitor1"
  DefaultColorDepth 24
 SubSection "Display"
  Depth  24
  Modes  "1280x1024, 1152x864, 1024x768"
 EndSubSection
EndSection

Section "ServerFlags"  
  Option  "Xinerama" "true"
  Option  "AllowMouseOpenFail" "true"
EndSection

Section "ServerLayout"
  Identifier "Default Layout"
  Screen 0 "Screen0" 0 0
  Screen 1 "Screen1" RightOf "Screen0"
  Option  "Xinerama" "on"
  #Option  "Twinview" "on"
  #Option  "TwinViewOrientation" "RightOf"
  InputDevice "Keyboard0" "CoreKeyboard"
  InputDevice "PS/2 Mouse" "CorePointer"
 #InputDevice "USB Mouse" "CorePointer"
 #InputDevice "Touchpad" "CorePointer"
 #InputDevice "Stylus" "CorePointer"
 #InputDevice "Eraser" "CorePointer"
 #InputDevice "Cursor" "CorePointer"
 #InputDevice "Serial Mouse" "CorePointer"
EndSection

Section "Module"
#  Load "GLcore"
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
  Load "synaptics"
  Load "xtrap"
EndSection

Section "InputDevice"
  Identifier "Keyboard0"
  Driver "keyboard"
  Option "CoreKeyboard"
  Option "XkbModel" "pc105"
  Option "XkbLayout" "us"
  Option "XKbOptions" ""
EndSection

Section "InputDevice"
  Identifier "Serial Mouse"
  Driver "mouse"
  Option  "Protocol" "Microsoft"
  Option  "Device" "/dev/ttyS0"
  Option  "Emulate3Buttons" "false"
  Option  "Emulate3Timeout" "70"
EndSection

Section "InputDevice"
 Identifier "Touchpad"
 Driver "synaptics"
 Option "Device" "/dev/psaux"
 Option "Protocol" "auto-dev"
 Option "LeftEdge" "1700"
 Option "RightEdge" "5300"
 Option "TopEdge" "1700"
 Option "BottomEdge" "4200"
 Option "FingerLow" "25"
 Option "FingerHigh" "30"
 Option "MaxTapTime" "180"
 Option "MaxTapMove" "220"
 Option "VertScrollDelta" "100"
 Option "MinSpeed" "0.06"
 Option "MaxSpeed" "0.12"
 Option "AccelFactor" "0.0010"
 Option "SHMConfig" "on"
 Option "Repeater" "/dev/input/mice"
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

Section "InputDevice"
  Identifier "Stylus"
  Driver "wacom"
  Option "Mode" "Absolute"
  Option "Type" "stylus"
  Option "Device" "/dev/input/wacom"
Endsection

# Settings for wacom eraser
Section "InputDevice"
  Identifier "Eraser"
  Driver "wacom"
  Option "Mode" "Absolute"
  Option "Type" "eraser"
  Option "Device" "/dev/input/wacom"
Endsection
# Settings for wacom cursor (mouse)
Section "InputDevice"
  Identifier "Cursor"
  Driver "wacom"
  Option "Mode" "Absolute"
  Option "Type" "cursor"
  Option "Device" "/dev/input/wacom"
Endsection

Section "DRI"
  Mode 0666
EndSection

Section "Extensions"
        Option  "Composite" "Enable"
EndSection

==========================================================

I went to hell on a broom stick getting this far so I be ever greatful to be able to finish off the config so it's fully functional

Cheers
Kiwi-Hawk

---

