---
title: "AMD.ATI Mobility - video and flash playback flickering"
date: 2008-06-28
forum: Multimedia Software
---

### Post by extigyro on 2008-06-28
Hello from Bulgaria, folks !

My card is AMD.ATI Mobility X1600. I've a serious problem, that can't be solved at all.
There is a lot of flickering, while i'm playing video files or flash (or whatever it is: flash, windows video media net streaming, quicktime... any kind of video playback) clips in firefox ([http://youtube.com/](http://youtube.com/) for example).
It makes no difference, if i'm using the opensource ATI driver - radeonhd or the propriety driver - fglrx (i've tested the whole version tree from 8.33 to 8.493).
I should specify that there's flickering when the objects move on the video, if they are motionless (static picture) - no flickering.
The monitor is LCD Widescreen, 17 ", 1680x1050. The computer is a HP nx9420 rh450ea laptop.

This is my original 'xorg.conf' file:
.................................................. ..............

Section "Files"
InputDevices "/dev/gpmdata"
InputDevices "/dev/input/mice"
FontPath "/usr/share/fonts/misc:unscaled"
FontPath "/usr/share/fonts/75dpi:unscaled"
FontPath "/usr/share/fonts/100dpi:unscaled"
FontPath "/usr/share/fonts/Type1"
FontPath "/usr/share/fonts/URW"
FontPath "/usr/share/fonts/Speedo"
FontPath "/usr/share/fonts/cyrillic"
FontPath "/usr/share/fonts/truetype"
FontPath "/opt/kde3/share/fonts"
FontPath "/usr/local/share/fonts"
EndSection

Section "ServerFlags"
Option "AllowMouseOpenFail" "on"
Option "ZapWarning" "on"
EndSection

Section "Module"
Load "dbe"
Load "type1"
Load "freetype"
Load "extmod"
Load "glx"
EndSection

Section "InputDevice"
Driver "kbd"
Identifier "Keyboard[0]"
Option "Protocol" "Standard"
Option "XkbLayout" "us"
Option "XkbModel" "microsoftpro"
Option "XkbRules" "xfree86"
EndSection


Section "InputDevice"
Driver "mouse"
Identifier "Mouse[1]"
Option "Buttons" "12"
Option "Device" "/dev/input/mice"
Option "Name" "Logitech USB Optical Mouse"
Option "Protocol" "explorerps/2"
Option "Vendor" "Sysp"
Option "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
Driver "synaptics"
Identifier "Mouse[3]"
Option "Buttons" "5"
Option "Device" "/dev/input/mice"
Option "Emulate3Buttons" "on"
Option "HorizScrollDelta" "0"
Option "InputFashion" "Mouse"
Option "Name" "Synaptics;Touchpad"
Option "Protocol" "explorerps/2"
Option "SHMConfig" "on"
Option "Vendor" "Sysp"
Option "ZAxisMapping" "4 5"
EndSection


Section "Monitor"
DisplaySize 367 230
HorizSync 30-82
Identifier "Monitor[0]"
ModelName "LGPHILIPSLCD LCD MONITOR"
Option "DPMS"
Option "PreferredMode" "1680x1050"
VendorName "LPL"
VertRefresh 43-60
UseModes "Modes[0]"
EndSection


Section "Modes"
Identifier "Modes[0]"
Modeline "1680x1050" 147.14 1680 1784 1968 2256 1050 1051 1054 1087
Modeline "1680x1050" 117.00 1680 1728 1760 1840 1050 1053 1059 1080 +HSync -Vsync
EndSection


Section "Screen"
DefaultDepth 24
SubSection "Display"
Depth 15
Modes "1680x1050"
EndSubSection
SubSection "Display"
Depth 16
Modes "1680x1050"
EndSubSection
SubSection "Display"
Depth 24
Modes "1680x1050"
EndSubSection
SubSection "Display"
Depth 8
Modes "1680x1050"
EndSubSection
Device "Device[0]"
Identifier "Screen[0]"
Monitor "Monitor[0]"
EndSection


Section "Device"
BoardName "Mobility Radeon X1600"
BusID "1:0:0"
Driver "radeonhd"
Identifier "Device[0]"
Option "monitor-PANEL" "Monitor[0]"
VendorName "ATI"
EndSection



Section "ServerLayout"
Identifier "Layout[all]"
InputDevice "Keyboard[0]" "CoreKeyboard"
InputDevice "Mouse[1]" "CorePointer"
InputDevice "Mouse[3]" "SendCoreEvents"
Option "Clone" "off"
Option "Xinerama" "off"
Screen "Screen[0]"
EndSection


Section "DRI"
Group "video"
Mode 0660
EndSection

Section "Extensions"
EndSection
.................................................. ..............



I've also tried some tweaking in the 'xorg.file' like:
Option "TexturedVideo" "off"
Option "VideoOverlay" "on/off"
Option "OpenGLOverlay" "off"
Option "XvmcUsesTextures" "True"
...
No difference !

My current distro is Ubuntu 8.04 LTS, but this is a common issue for me, which occurs also under openSuSE 11, Mandriva 2008.1, Fedora 8/9, Slackware...etc...

Any suggestions !?!
Or it's an ATI (opensource and propriety) driver drawback.

---

### Post by mislam on 2008-06-28
I have the same problem when I am using ATI proprietary driver. I do not have this issue when using opensource. I have ATI radeon X300SE. I do not remember having issue with ATI proprietary drivers before. This could be a new thing. Sorry no solution here, just a confirmation.

---

### Post by |{urse on 2008-06-28
k guys

run this

```
gstreamer-properties
```

click the 'video' tab select 'X Window System (no Xv) from the first dropdown menu. *poof* fixed!
 
If you are having problems with video games flickering and are tired of enabling and reenabling desktops effects try making simple bash scripts to do it for you.

Example

> #!/bin/bash
metacity --replace &
sleep 2
/usr/local/games/etqw.demo/etqw &&
sleep 2
compiz --replace &

---

### Post by extigyro on 2008-06-28
> **|{urse said:**
> k guys

run this

```
gstreamer-properties
```

click the 'video' tab select 'X Window System (no Xv) from the first dropdown menu. *poof* fixed!
 

Thanks |{urse, but i've already tried this. I've read your previous post about a connate problem in another thread. But yet thanks again. :)

---

### Post by extigyro on 2008-06-29
I've also tried 'vesa' and 'fbdev' driver. The problem persists again, but there's less flickering, particularly with 'vesa' driver. 

Under WinXP - i've never noticed ANY flickering, so i exclude the possibility of hardware failure.

---

### Post by extigyro on 2008-07-01
There's high possibility the reason for the flickering to be the X Server, isn't it... 

Or ... ?

---

### Post by extigyro on 2010-06-30
Almost 2 YEARS later my card is old enough to be replaced.
My card IS NOT supported anymore by the proprietary driver for more than a year now. ((((((((((((:

There is still flickering when watching Flash video clips in youtube.com, etc.
There is at least NO flickering when watching video files on my HDD using VLC, Totem, etc. (applications which use the Xv video extension) with the open-source ati driver (ver. 6.12 and above).

That is the situation if Karmic is in use and NO KMS.
With Lucid (X Server 1.7 and ati driver ver. 6.13) and KMS on by default, there is again flickering when both watching Flash video clips and video files with VLC, Totem, etc.

That's the reason to use Ubuntu Karmic for now and wait another 2-3 years until there is decent support under Linux of a video card model of autumn 2005.

AMD.ATI and Adobe rock, aren't they.

---

