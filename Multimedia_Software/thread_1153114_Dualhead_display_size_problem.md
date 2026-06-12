---
title: "Dualhead display size problem"
date: 2009-05-08
forum: Multimedia Software
---

### Post by aroby on 2009-05-08
Adding to the litany of dual head problems, here's another one, running Ubuntu 8.10.   

I want to have two X displays off one card.  One display (DVI) is an LCD monitor @ 1280x1024.  The other display (COMPONENT VIDEO) is at 1920x1080.

Using the attached xorg.conf, this is all working.  Except that the LCD monitor, working at 1280x1024, has a much larger display surface (so I only see the top left hand corner of it).  I don't know how to find out what is the size of that surface.

Any thoughts on how to fix this appreciated,

Anthony

[INDENT][FONT=Courier New]Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "LCD Screen" 0 0
    Screen      1  "HD Screen"  1280 0
    Option         "DualHead"   "true"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier     "LCD Monitor"
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Component Video"
    Gamma          1.5
EndSection

Section "Device"
    Identifier  "0 Radeon HD3450"
    Driver      "fglrx"
    BusID       "PCI:1@:0:0"
    Option      "COMPONENT_VIDEO" "Component Video"
    Option      "DFP2" "LCD Monitor"
EndSection

Section "Device"
    Identifier  "1 Radeon HD3450"
    Driver      "fglrx"
    BusID       "PCI:1@:0:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "LCD Screen"
    Device     "0 Radeon HD3450"
    Monitor    "LCD Monitor"
    DefaultDepth 24
    SubSection "Display"
        Depth    24
        Modes    "1280x1024"
    EndSubSection
EndSection

Section "Screen"
    Identifier "HD Screen"
    Device     "1 Radeon HD3450"
    Monitor    "Component Video"
    DefaultDepth 24
    SubSection "Display"
        Depth    24
        Modes    "1920x1080"
    EndSubSection
EndSection
[/FONT][/INDENT]

---

