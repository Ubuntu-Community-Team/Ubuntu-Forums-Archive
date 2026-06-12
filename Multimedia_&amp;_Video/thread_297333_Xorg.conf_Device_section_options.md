---
title: "Xorg.conf Device section options"
date: 2006-11-11
forum: Multimedia &amp; Video
---

### Post by CowzRule on 2006-11-11
I'm trying to optimize my video card for games and Beryl (neither installed yet). I've added some extra options in the 
Device section of my xorg.conf file and I'm wondering if anything listed might cause any problems or conflicts.
```
[COLOR="Black"]Section "Device"
Identifier  "ATI Technologies, Inc. R420 JI [Radeon X800PRO]"
Driver      "fglrx"
Option        "VideoOverlay" "on"
Option        "OpenGLOverlay" "off"[/COLOR][COLOR=Blue]
Option        "FSAAEnable" "on"
Option        "FSAAScale" "6"
Option        "FSAADisableGamma" "off"[/COLOR][COLOR=Red]
Option         "DRI" "true"
Option         "ColorTiling" "on"
Option         "EnablePageFlip" "true"
Option         "AccelMethod" "EXA"
Option         "XAANoOffscreenPixmaps"
Option         "RenderAccel" "true"
Option         "AGPFastWrite" "on"[/COLOR][COLOR=Black]
BusID       "PCI:1:0:0"
EndSection[/COLOR]
```The lines in black were the only lines there after I installed the fglrx 8.30.3 drivers using method 2 from this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) (worked fine,no errors).
I added the blue lines using the "aticonfig --[OPTION]" in the terminal and I added the red lines from my research of the 
forums.
Also, the guide said to add the following section (which I did):
```
Section "Extensions"
Option	    "Composite" "Disable"
EndSection
```I know the **Disable** part has to be there, but I've seen in the forums were it's been **false** or **0**. Will any one of those work? Which one of the 3 would be considerd "correct" ?
Thanks

---

