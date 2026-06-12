---
title: "Shining vertical lines on the screen"
date: 2008-08-04
forum: Multimedia Software
---

### Post by Tamao on 2008-08-04
Hi everybody !

I just bought a new computer. My screen is an LCD HP L1710, and the display is handled by the motherboard, which is an INTEL SIS LAN_SATA_DDR2_SVIDEO_DB98PCI.
It was sold with a Dapper Drake on it (!). There was no problem with the display, except the fact that the resolution was rather bad.

I installed a Hardy Heron on it, and now I have some shining vertical lines on the screen. Increasing the refresh rate turns these lines into wider stripes (I cannot decrease it, since only 60Hz and 75Hz are available, and 60Hz is the standard for my screen). When lowering the resolution to 800x600 (standard for this screen is 1280*1024), they disappear.

This screen seems to be unknown from Ubuntu. I tried to use the windows driver (.INF file) that were given by HP but it didn't work.
I already edited the xorg.conf file to add two lines (HorizSync 24-83 & VertRefresh 50-77) and some SubSections "Display".

I eventually turned the Depth to 16 (and kept a 1280x1024 resolution), and the only remaining trouble is some shining dots where the vertical lines were before.

I guess there is some RefreshRate issue to be solved in order to get rid of these annoying dots, but I cannot fix it.

Thanks in advance for your help
Tam

---

