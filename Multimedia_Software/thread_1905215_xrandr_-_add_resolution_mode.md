---
title: "xrandr - add resolution mode"
date: 2012-01-06
forum: Multimedia Software
---

### Post by Ivorne on 2012-01-06
Hello, I have my computer connected to TV with VGA cable. The TV resolution is writen to be HD Ready (not really sure about what it means). Anyway, for VGA input the TV has options XGA (1024x768) and WXGA (1280x768). On this computer i have Lubuntu 11.10. In automaticaly detected resolutions is no option of 1280x768, so I am setting it with these commands at startup:

# gtf 1280 768 59.9
xrandr --newmode "1280x768_59.90"  80.00  1280 1344 1480 1680  768 769 772 795  -HSync +Vsync
xrandr --addmode VGA-0 1280x768_59.90
xrandr -s 1280x768_59.90

It works OK and the resolution is really 1280x768. The trouble is that it seem this is not the good resolution. When i draw a square, it looks like rectangle (it is wider than it should be). So i looked at other computer which is connected to the same TV with HDMI. It is Windows 7 on it at the resolution is automaticaly detected as 1280x720. So I decided to try this resolution on the first computer as well. So i run these commands:

# gtf 1280 720 59.9
xrandr --newmode "1280x720_59.90"  74.36  1280 1336 1472 1664  720 721 724 746  -HSync +Vsync
xrandr --addmode VGA-0 1280x720_59.90
xrandr -s 1280x720_59.90

Unfortunately they dont work. When I execute the last command, the screen become black (I think xserver falls). When i restart lightdm, its working again, but not in 1280x720.

Could you please give me some advice, how to solve this? Thank you

---

### Post by efflandt on 2012-01-07
VGA in Linux often seems to be clueless about optimum video modes.  DVI communicates better what modes it is capable of and usually uses the best mode.  Perhaps this can shed some light on your video mode, from legacy ATI X1300 displaying native 1280x720 on an old Apex HDTV Ready 27" LCD.

```
From /var/log/Xorg.0.log

(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 60  vid: 16481
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 60  vid: 16453
(II) RADEON(0): #3: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 74.5 MHz   Image Size:  597 x 336 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1472 h_blank_end 1664 h_border: 0
(II) RADEON(0): v_active: 720  v_sync: 723  v_sync_end 728 v_blanking: 748 v_border: 0
(II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 64 kHz, PixClock max 110 MHz
(II) RADEON(0): Monitor name: NEXGEN NL27
(II) RADEON(0): Serial No: 
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):         00ffffffffffff0038b8920001000000
(II) RADEON(0):         300c0103813c22782a7e5ca554449924
(II) RADEON(0):         12484bafce0081806140454081c00101
(II) RADEON(0):         0101010101011a1d008051d01c204080
(II) RADEON(0):         350055502100001c000000fd00384b1e
(II) RADEON(0):         400b000a202020202020000000fc004e
(II) RADEON(0):         455847454e204e4c3237200a000000ff
(II) RADEON(0):         00200a20202020202020202020200027
(II) RADEON(0): Panel infos found from DDC detailed: 1280x720
(II) RADEON(0): EDID vendor "NEX", prod id 146
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)


efflandt@efflandt-lucid64:~$ gtf 1280 720 60

  # 1280x720 @ 60.00 Hz (GTF) hsync: 44.76 kHz; pclk: 74.48 MHz
  Modeline "1280x720_60.00"  74.48  1280 1336 1472 1664  720 721 724 746  -HSync +Vsync

efflandt@efflandt-lucid64:~$ gtf 1280 720 59.9

  # 1280x720 @ 59.90 Hz (GTF) hsync: 44.69 kHz; pclk: 74.36 MHz
  Modeline "1280x720_59.90"  74.36  1280 1336 1472 1664  720 721 724 746  -HSync +Vsync

efflandt@efflandt-lucid64:~$ cvt 1280 720
# 1280x720 59.86 Hz (CVT 0.92M9) hsync: 44.77 kHz; pclk: 74.50 MHz
Modeline "1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
```Note that **cvt**, without specifying Hz, seems to come up with numbers that match the optimum that the 59.9 DVI connection automatically uses, even if cvt rounds the description (in quotes) to 60.00.

---

