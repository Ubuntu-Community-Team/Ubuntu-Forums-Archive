---
title: "Resolution problem with AMD HD 3450 and Dell U3011"
date: 2012-10-28
forum: Multimedia Software
---

### Post by johanmazel on 2012-10-28
Hi
I am trying to use a a Dell U3011 (30 inches IPS screen) on a Dell Optiplex 960 with an AMD HD 3450 running Ubuntu 12.04.

The HD3450 is able to display the screen`s native resolution (2560x1600) according to [http://www.amd.com/us/products/desktop/graphics/ati-radeon-hd-3000/hd-3400/Pages/ati-radeon-hd-3400-specifications.aspx ]("http://www.amd.com/us/products/desktop/graphics/ati-radeon-hd-3000/hd-3400/Pages/ati-radeon-hd-3400-specifications.aspx")provided that a dual-link DVI cable is used, which is the case. 
Unfortunately, the biggest available resolution is 1600x1200.

The contents of /var/log/Xorg.0.log seems to show that the screen`s announced resolutions are correctly detected through EDID (included 2560x1600):
[    48.674] (II) fglrx(0): EDID vendor "DEL", prod id 16483
[    48.674] (II) fglrx(0): Using hsync ranges from config file
[    48.674] (II) fglrx(0): Using vrefresh ranges from config file
[    48.674] (II) fglrx(0): Printing DDC gathered Modelines:
[    48.674] (II) fglrx(0): Modeline "2560x1600"x0.0  268.50  2560 2608 2640 2720  1600 1603 1609 1646 +hsync -vsync (98.7 kHz)
[    48.674] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    48.674] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    48.674] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    48.674] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    48.674] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    48.674] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    48.674] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    48.674] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    48.674] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    48.674] (II) fglrx(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
[    48.674] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    48.674] (II) fglrx(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    48.674] (II) fglrx(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
[    48.674] (II) fglrx(0): Modeline "1920x1440"x0.0  234.00  1920 2048 2256 2600  1440 1441 1444 1500 -hsync +vsync (90.0 kHz)
[    48.967] (WW) fglrx(0): Cannot get updated TV attributes.

I tried both open source and proprietary drivers.

Thanks for your time.
Regards.
Johan

---

