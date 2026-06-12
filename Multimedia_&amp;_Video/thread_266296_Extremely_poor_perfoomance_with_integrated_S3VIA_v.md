---
title: "Extremely poor perfoomance with integrated S3\VIA video"
date: 2006-09-27
forum: Multimedia &amp; Video
---

### Post by GSMD on 2006-09-27
Hello.
I face the same problem on all workstations upgraded to Ubuntu: extremely low perfomance in 2D (native Gnome and Java apps). All PSs are somewhat like 1.7GHz 512Mb previously running WinXP smoothly.
The video cards are detected as following:
```
Section "Device"
    Identifier    "VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
    Driver        "via"
    BusID        "PCI:1:0:0"
EndSection
``````
Section "Device"
    Identifier    "S3 Inc. VT8375 [ProSavage8 KM266/KL266]"
    Driver        "savage"
    BusID        "PCI:1:0:0"
EndSection
``````
Section "Device"
    Identifier    "VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
    Driver        "via"
    BusID        "PCI:1:0:0"
EndSection
```Just default installations, no any tweaks applied yet.

What may be wrong? How can I improve perfomance?

Thanks.

---

### Post by GSMD on 2006-09-30
No ideas? Should perform tweaks or smth?

---

