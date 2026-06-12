---
title: "AtI Radeon HD 3650 AGP display problems"
date: 2010-08-28
forum: Multimedia Software
---

### Post by Wickk on 2010-08-28
My refresh rate is constantly stuck at 60hz which is really bothersome, when I know my card and my monitor are capable of going to 75hz. I'm not entirely sure if there's something I'm just not seeing on how to fix this. Running 10.04

My Xorg: ```
 Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    HorizSync    30.0 - 67.0
    VertRefresh  50.0 - 75.0
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "Default Device"
    Driver      "fglrx"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Monitor    "Monitor1"
    DefaultDepth     24
EndSection

```When I try and run ```
aticonfig --initial
``` I get this result: ```
Found fglrx primary device section
 Unable to find any supported Screen sections
```

---

