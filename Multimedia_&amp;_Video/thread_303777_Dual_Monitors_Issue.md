---
title: "Dual Monitors Issue"
date: 2006-11-20
forum: Multimedia &amp; Video
---

### Post by maliciouspixies on 2006-11-20
Right, after spending many hours, I got my HP dv2000 laptop to display on my Samsung SM 913 TM I was showered with bugs.

Using i810 driver, Edgy Kubuntu.

Right:

1) The first thing is that the start up pictures have a black background instead of being transparent. Confusing.

2) The display is shown in widescreen format at the top of the Samsung and a black screen with a tiny line of grey toolbar in the top left hand corner of the notebook screen. Even more confusing.

3) Both the displays work exactly how i want them to when i start up Ubuntu in recovery mode. 4:3 format on the samsung, 16:9 format in the notebook screen.

Please help.

Plus, how do i turn it back quickly for when i just use the laptop?

I include my xorg.conf

[COLOR="Red"]
Section "Device"
#       Identifier      "Intel Integrated Graphics Device"
        Identifier      "Intel-LCD"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option "MonitorLayout" "CRT, CRT+LFP"
EndSection
 
Section "Device"
        Identifier      "Intel-VGA"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Screen          1
        Option "MonitorLayout" "CRT, CRT+LFP"
EndSection
 
Section "Monitor"
        Identifier      "LCD"
        Option          "DPMS"
EndSection
 
Section "Monitor"
        Identifier      "CRT"
        Option          "DPMS"
        HorizSync       30-81
        VertRefresh     56-75
EndSection
 
Section "Screen"
        Identifier      "LCD-Screen"
        Device          "Intel-LCD"
        Monitor         "LCD"
        DefaultDepth    24
        SubSection "Display"
                Depth           16
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection
 
Section "Screen"
        Identifier      "CRT-Screen"
        Device          "Intel-VGA"
        Monitor         "CRT"
        DefaultDepth    24
        SubSection "Display"
                Depth           16
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024"
        EndSubSection
EndSection
 
 
Section "ServerLayout"
        Identifier      "Multihead"
        Screen          0 "LCD-Screen"
        Screen          1 "CRT-Screen" LeftOf "LCD-Screen"
        Option "Xinerama" "on"
        Option "Clone" "off"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
  Mode 0666
EndSection

Section "Extensions"
	Option "Composite" "false"
EndSection[/COLOR]

---

