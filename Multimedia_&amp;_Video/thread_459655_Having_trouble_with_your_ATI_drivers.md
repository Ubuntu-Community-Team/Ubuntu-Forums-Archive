---
title: "Having trouble with your ATI drivers?"
date: 2007-05-30
forum: Multimedia &amp; Video
---

### Post by spacedogg on 2007-05-30
After I installed the fglrx drivers, I couldn't get the resolution that I needed to show up. What made the difference for me was adding the HorizSync & VertRefresh for my monitor in the xorg.conf file. Try adding those lines to your xorg.conf if you've just installed the fglrx driver and can't get the resolution you need. If there are already entries in your xorg.conf, make sure they're correct. You should be able to find the values for your monitor in the user manual for your monitor.

Example:

Section "Monitor"
Identifier "Monitor0"
VendorName "Unknown"
ModelName "DELL M1110"
HorizSync 30.0 - 107.0
VertRefresh 50.0 - 160.0
Option "DPMS"
EndSection

My specs:

MSI K8 Neo4 Platinum
AMD Athlon 64 4000+
2 GB OCZ Gold 2-2-2-5 timings
ATI X850XT PE
Maxtor 300GB HDD
SB Audigy Sound Card (I really want X-Fi Drivers)
Sony DRU-810A DVD Drive
Dell 2005FPW Monitor

---

