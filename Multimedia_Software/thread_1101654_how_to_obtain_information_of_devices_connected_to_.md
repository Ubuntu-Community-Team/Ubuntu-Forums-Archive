---
title: "how to obtain information of devices connected to  HDMI/DVI-D"
date: 2009-03-20
forum: Multimedia Software
---

### Post by ghat on 2009-03-20
hi

basic question, whenever I run a X server I can look at the /var/log/Xorg.log.0 and get the information like... 

```


[    0.533840] (II) intel(0): Monitor name: DENON-AVAMP
[    0.533861] (II) intel(0): Ranges: V min: 55 V max: 76 Hz, H min: 15 H max: 75 kHz, PixClock max 170
[    0.533872] (II) intel(0): Number of EDID sections to follow: 1
[    0.533878] (II) intel(0): EDID (in hex):
[    0.533886] (II) intel(0):   00ffffffffffff0011ee0d0001010101
[    0.533895] (II) intel(0):   0011010380522e782a1bbea25534b326
[    0.533903] (II) intel(0):   144a52afce00d1c0a940904081800101
[    0.533911] (II) intel(0):   010101010101023a801871382d40582c
[    0.533919] (II) intel(0):   450034cc3100001e662150b051001b30
[    0.533927] (II) intel(0):   4070360000000000001e000000fc0044
[    0.533935] (II) intel(0):   454e4f4e2d4156414d500a20000000fd
[    0.533944] (II) intel(0):   00374c0f4b11000a20202020202001c7
[    0.533952] (II) intel(0):   020340714f9020050403020706010e23
[    0.533960] (II) intel(0):   0f240a0b3b0f7f073d1ec0150750597e
[    0.533968] (II) intel(0):   015f1e015706006154006714004d0200
[    0.533976] (II) intel(0):   835f0000e305030167030c002200b82d
[    0.533984] (II) intel(0):   011d8018711c1620582c250034cc3100
[    0.533992] (II) intel(0):   009e011d007251d01e206e28550034cc
[    0.534001] (II) intel(0):   3100001e8c0ad08a20e02d10103e9600
[    0.534009] (II) intel(0):   67cc210000180000000000000000004b
[    0.534023] (II) intel(0): EDID vendor "DON", prod id 13
[    0.534068] (II) intel(0): Not using mode "1920x1080" (bad mode clock/interlace/doublescan)
[    0.534078] (II) intel(0): Printing probed modes for output HDMI-1
[    0.534086] (II) intel(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 112
[    0.534098] (II) intel(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 125
[    0.534108] (II) intel(0): Modeline "1400x1050"x59.9  101.00  1400 1448 1480 1560  1050 1053 1057 108
[    0.534119] (II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 106
[    0.534129] (II) intel(0): Modeline "1360x768"x60.0   85.50  1360 1424 1536 1792  768 771 777 795 +hs
[    0.534140] (II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hs
[    0.534150] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hs
[    0.534160] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hs
[    0.534170] (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync
[    0.534181] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync
[    0.534190] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync
[    0.534200] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync
[    0.534210] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -
[    0.534220] (II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -
[    0.534230] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -
[    0.534240] (II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +
[    0.534251] (II) intel(0): EDID for output HDMI-2
[    0.534258] (II) intel(0): Output VGA disconnected
[    0.534264] (II) intel(0): Output HDMI-1 connected
[    0.534270] (II) intel(0): Output HDMI-2 disconnected
[    0.534277] (II) intel(0): Using exact sizes for initial modes
[    0.534284] (II) intel(0): Output HDMI-1 using initial mode 1920x1080
[    0.880894] (II) intel(0): detected 512 kB GTT.
[    0.880914] (II) intel(0): detected 32764 kB stolen memory.
[    0.880928] (==) intel(0): video overlay key set to 0x101fe
[    0.880942] (==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
[    0.880980] (==) intel(0): DPI set to (96, 96)

```The question I have is there any other way of getting the same information on the command line..

basically I have a HTPC and someone is watching a movie, and I am remotly logged in 
trying to find out what monitor etc is connected and what its doing on the video interface, or query some other parameter, and I want to do it from the command line.  (like lspci, lsusb, dmidecode etc ?)

Is there any other place I can find the same information in /proc/ or /sys?

Ghat
> 
you may wonder why I am trying to do this... the actual problem is that when the computer was booted up and X was started the AV receiver and the TV was on and hence X started faithfully, however when I am debugging and fixing something I want to restart my X, and I am not sure if the AV receiver and the TV is on or not and if it is connected 
correctly in the AV receiver menu.. 
I hence want to probe the displays before I restart X, other wise it may just poop out saying no displays connected... 


---

### Post by ghat on 2009-03-20
hi 

sorry for answering my own question... I guess this helps, and hopefully it will help others too...

If you have any better ideas let me know

```


htpc:~> xrandr -q --verbose -display :0
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 1920 x 1920
VGA disconnected (normal left inverted right x axis y axis)
        Identifier: 0x3b
        Timestamp:  62942464
        Subpixel:   unknown
        Clones:    
        CRTCs:      0 1
        Transform:  1.000000 0.000000 0.000000
                    0.000000 1.000000 0.000000
                    0.000000 0.000000 1.000000
                   filter: 
HDMI-1 disconnected 1920x1080+0+0 (0x3e) normal (normal left inverted right x axis y axis) 820mm x 460mm
        Identifier: 0x3c
        Timestamp:  62942464
        Subpixel:   unknown
        Clones:     HDMI-2
        CRTC:       0
        CRTCs:      0 1
        Panning:    0x0+0+0
        Tracking:   0x0+0+0
        Border:     0/0/0/0
        Transform:  1.000000 0.000000 0.000000
                    0.000000 1.000000 0.000000
                    0.000000 0.000000 1.000000
                   filter: 
  480p/60 (0xb0)   23.9MHz
        h: width   640 start  664 end  736 total  760 skew    0 clock   31.5KHz
        v: height  480 start  484 end  492 total  525           clock   60.0Hz
  720p/60 (0xb1)   74.2MHz
        h: width  1280 start 1320 end 1376 total 1650 skew    0 clock   45.0KHz
        v: height  720 start  722 end  728 total  750           clock   60.0Hz
  1080i/60 (0xb2)   74.2MHz Interlace
        h: width  1920 start 1960 end 2016 total 2200 skew    0 clock   33.8KHz
        v: height 1080 start 1082 end 1088 total 1125           clock   30.0Hz
  1080p/60 (0xb3)  148.5MHz
        h: width  1920 start 1960 end 2016 total 2200 skew    0 clock   67.5KHz
        v: height 1080 start 1082 end 1088 total 1125           clock   60.0Hz
HDMI-2 disconnected (normal left inverted right x axis y axis)
        Identifier: 0x3d
        Timestamp:  62942464
        Subpixel:   unknown
        Clones:     HDMI-1
        CRTCs:      0 1
        Transform:  1.000000 0.000000 0.000000
                    0.000000 1.000000 0.000000
                    0.000000 0.000000 1.000000
                   filter: 
  1920x1080 (0x3e)  148.5MHz
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock   67.5KHz
        v: height 1080 start 1084 end 1089 total 1125           clock   60.0Hz
  480i/60 (0xaf)   12.0MHz
        h: width   640 start  664 end  736 total  760 skew    0 clock   15.8KHz
        v: height  480 start  484 end  492 total  525           clock   30.0Hz
htpc:~> 


```


:P

---

