---
title: "ubuntu 8.10 xorg.conf editor"
date: 2009-01-20
forum: Multimedia Software
---

### Post by moongodjon on 2009-01-20
displayconfig-gtk is no longer available in 8.10? 

what is the xorg.conf for a hp widescreen monitor with radeon driver

---

### Post by ajgreeny on 2009-01-20
You may need a manual edit to get your desired resolution with a pattern like this, which is my xorg.conf, needed as 8.10 got it wrong, the first time ubuntu has been incorrect.
```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
            [B]HorizSync    30-80
            VertRefresh    50-75[/B]
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        **Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"**
    EndSubSection
EndSection

```I have omitted all the introductory info at the top of the text.
Change the figures shown **here** for those needed for your monitor.

---

