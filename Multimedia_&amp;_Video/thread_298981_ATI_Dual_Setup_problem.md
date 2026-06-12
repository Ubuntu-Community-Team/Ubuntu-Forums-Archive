---
title: "ATI Dual Setup problem"
date: 2006-11-13
forum: Multimedia &amp; Video
---

### Post by ids777 on 2006-11-13
(Cross posted apologies!)

Arrrgh!!

Just installed Ubuntu for the first time & I've trying for day's to get my ATI Radeon 9800 to dual screen. 

The closest i've got is at the logon screen **it's is** a dual screen - but as soon as i've logged on it switches to a clone again....
I've read sooo many differing opinions I no lost.... Please help...

Copy of xorg.conf
Section "Device"
Identifier "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
# Driver "ati"
# BusID "PCI:1:0:0"
Driver "fglrx"
BusID "PCI:1:0:0"
Option "UseInternalAGPGART" "no"
Option "no_accel" "no"
Option "no_dri" "no"
Option "mtrr" "off"
Option "DesktopSetup" "0x00000200"
Option "MonitorLayout" "AUTO, AUTO"
Option "IgnoreEDID" "off"
Option "NoTV" "yes"
Option "TVStandard" "PAL-B"
Option "TVHSizeAdj" "0"
Option "BlockSignalsOnLock" "on"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
Screen 0
EndSection

Section "Monitor"
Identifier "ULTRASCANP99"
Option "DPMS"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
Monitor "ULTRASCANP99"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "false"
EndSection

---

### Post by molo on 2006-11-15
Take a look at this thread, and try the process outlined there:
[http://www.ubuntuforums.org/showthread.php?t=221174](http://www.ubuntuforums.org/showthread.php?t=221174)

Basically:
you need to duplicate your Device and Monitor, and Screen sections, and give them different identifiers (one for the built-in device and LCD, one for the external device and desktop monitor).

Then you need to edit the ServerLayout section to make the layout as you want it, for example:
```
...
Screen 0 "Laptop Screen"
Screen 1 "Default Screen" LeftOf "Laptop Screen"
...
```

Also, I don't believe the "MonitorLayout" section works well for "AUTO" as the options.  If you have a laptop you're probably going to want to set it to "LVDS,CRT" (if using an external CRT) or "LVDS,TMDS" (if using an external LCD).

The details are in the post linked above.

Good luck,
molo

---

### Post by Manuel82b on 2006-11-17
ok, maybe i can help you. im a noob to but i get the dual screen working (without 3d).

first go to a terminal and type "fglrxinfo".. it shows stuff like this: 

manuel@mbleser:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.5814 (8.25.18)

when it shows that the driver is "mesa Project blabla" reinstall the ati-driver with this "xorg-driver-fglrx". 

for dual screen u have to get the "fglrx-control" package. install this, go to the terminal and type "sudo fireglcontrol".... then the tab "desktop Setup" and switch to "Big Desktop Horizontal"... restart the x-server.. then go to the display properties (system->properties->resolution!?) and u will see an resolution like 3200x1600 (thats mine)... click on it and you have your dual screen..

hope that help.

ps: sorry for my english :-)

---

### Post by ids777 on 2006-11-17
I ended up fixing it by re-insatlling Ubuntu
installed fglrx
then used 'sudo fglrxconfig'

It worked,  i think where i went wrong the first time work not using 'sudo'!!!

---

### Post by Hasen_A on 2006-11-20
How do you control which monitor is to the left or right?

---

