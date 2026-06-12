---
title: "Component Video as Standalone Display - Radeon 2400 HD PCI"
date: 2009-02-17
forum: Multimedia Software
---

### Post by jaysmit9 on 2009-02-17
All - I have the Component Video as my standalone display only partially working (720x480).  I can't seem to select different modes using aticonfig or in the xorg.conf file.  I've posted many of my findings below.  Please help.  It seems (based on my comprehensive online search) that many others want this solution resolved.  If anyone can help!

How I got it working (sortof):

If I enter the command:
aticonfig --enable-monitor cv
The component video is enabled. However, it doesn't have the same resolution. It scrolls around on the 1280x720 screen. 

Also - It added --> Option "EnableMonitor" "cv"
to the xorg.conf device section. Unfortunately, it still boots to the VGA device.

--------------Preconditions to above-------------

------------aticonfig output---------
aticonfig --query-monitor
Connected monitors: crt2, cv
Enabled monitors: crt2
sudo aticonfig --enable-monitor=crt2,cv --effective=now
ati_dm:FGLRX EnableDisplays failed when try to enable display: 50
------------Xorg.0.log---------

(II) fglrx(0): ***Display: ConnectedDisplayTypes=0x00000050, disabled=0x00000000
(II) fglrx(0): Connected Display1: CRT on secondary DAC [crt2]
(II) fglrx(0): Display1: No EDID information from DDC.
(II) fglrx(0): Display1: Failed to get EDID information.
(II) fglrx(0): Connected Display2: Component Video [cv]
(II) fglrx(0): Display2: No EDID information from DDC.
(II) fglrx(0): Display2: Failed to get EDID information.
(WW) fglrx(0): DALEnableDriverInstance on secondary failed: 9
(II) fglrx(0): For single mode, Component Video is disabled


------------xorg.conf----------
Section "ServerLayout"

# Uncomment if you have a wacom tablet
# InputDevice "stylus" "SendCoreEvents"
# InputDevice "cursor" "SendCoreEvents"
# InputDevice "eraser" "SendCoreEvents"
Identifier "Default Layout"
Screen 0 "aticonfig-Screen[0]-0" 0 0
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
Option "Xinerama" "off"
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
Identifier "stylus"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Identifier "eraser"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Identifier "cursor"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Monitor"
Identifier "aticonfig-Monitor[0]-0"
Option "VendorName" "ATI Proprietary Driver"
Option "ModelName" "Generic Autodetecting Monitor"
Option "DPMS" "true"
EndSection

Section "Device"
Identifier "aticonfig-Device[0]-0"
Driver "fglrx"
BusID "PCI:2:0:0"
EndSection

Section "Screen"
Identifier "aticonfig-Screen[0]-0"
Device "aticonfig-Device[0]-0"
Monitor "aticonfig-Monitor[0]-0"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
Modes "1280x720" "1024x768"
EndSubSection
EndSection

---

### Post by jaysmit9 on 2009-02-17
Anyone have experience with this?  ----  Or does someone have a recommendation of a PCI video card that does component out?  I can go either way.  :)

---

### Post by Favux on 2009-02-17
Hi jaysmit9,

I can't be much help on the video part.  But I did notice some "problems" with your xorg.conf.  You didn't say what model computer you have, but I'm guessing it is not a tablet pc nor do you have an external Wacom graphics tablet.  Also what version of Ubuntu are you running?  Hardy (8.04)?

In which case those sections of your xorg.conf should be commented out.  Also "ServerLayout" should be at the end.  I also put your video card at the head of the video section like so:
```
Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
Option "Xinerama" "off"
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

# Uncomment if you have a wacom tablet.
#Section "InputDevice"
#Identifier "stylus"
#Driver "wacom"
#Option "Device" "/dev/input/wacom"
#Option "Type" "stylus"
#Option "ForceDevice" "ISDV4" # Tablet PC ONLY
#EndSection

# Uncomment if you have a wacom tablet with an eraser on the stylus.
#Section "InputDevice"
#Identifier "eraser"
#Driver "wacom"
#Option "Device" "/dev/input/wacom"
#Option "Type" "eraser"
#Option "ForceDevice" "ISDV4" # Tablet PC ONLY
#EndSection

# Uncomment if you have an external wacom tablet that has a mouse.
#Section "InputDevice"
#Identifier "cursor"
#Driver "wacom"
#Option "Device" "/dev/input/wacom"
#Option "Type" "cursor"
#Option "ForceDevice" "ISDV4" # Tablet PC ONLY
#EndSection

Section "Device"
Identifier "aticonfig-Device[0]-0"
Driver "fglrx"
BusID "PCI:2:0:0"
EndSection

Section "Monitor"
Identifier "aticonfig-Monitor[0]-0"
Option "VendorName" "ATI Proprietary Driver"
Option "ModelName" "Generic Autodetecting Monitor"
Option "DPMS" "true"
EndSection

Section "Screen"
Identifier "aticonfig-Screen[0]-0"
Device "aticonfig-Device[0]-0"
Monitor "aticonfig-Monitor[0]-0"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
Modes "1280x720" "1024x768"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen 0 "aticonfig-Screen[0]-0" 0 0
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
# Uncomment if you have a wacom tablet
# InputDevice "stylus" "SendCoreEvents"
# InputDevice "cursor" "SendCoreEvents"
# InputDevice "eraser" "SendCoreEvents"
EndSection
```
I don't know how the aticonfi utility works, but isn't there suppose to be "duplicate" xorg.conf entries of the video sections of "Monitor" and "Screen" and probably "Device" for a second monitor?  Only labeled somehow with a (1)?  Could this be why you get the error message:
```
(WW) fglrx(0): DALEnableDriverInstance on secondary failed: 9
(II) fglrx(0): For single mode, Component Video is disabled
```
And the second (labeled 1) "Screen" section having the resolution for your second monitor?

---

### Post by Favux on 2009-02-18
Two references that may be useful:

[http://navetz.com/v/132/Simple-dual-monitor-setup-with-XrandR-in-Ubuntu-Linux]("http://navetz.com/v/132/Simple-dual-monitor-setup-with-XrandR-in-Ubuntu-Linux")

[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2")

---

### Post by jaysmit9 on 2009-02-18
Thanks!  ---  I'll try these tonight and report back.

FYI - I upgraded to 8.10 last night to be at the latest rev.  Haven't installed the ATI driver yet.  Will do so tonight as well.

---

### Post by jaysmit9 on 2009-02-22
Just to update the thread (for future readers).  I've tried every permutation of driver (radeon, radeonhd, fglrx).  For my card 2400 HD, the only one that is fast enough to do video is the fglrx (radeonhd doesn't recognize the card).  The best resolution I can get out of the card in component mode is 720x480.  This is a bummer... but this system was a test to see if I could do what I wanted to with ubuntu/mythtv.  I would say it passed with flying colors.  I'm going to buy another PC this week that has the speed and capabilities I need.  This time -- Nvidia.

---

