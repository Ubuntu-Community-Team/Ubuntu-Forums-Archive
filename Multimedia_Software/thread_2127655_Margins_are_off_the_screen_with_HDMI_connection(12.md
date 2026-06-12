---
title: "Margins are off the screen with HDMI connection(12.04)"
date: 2013-03-20
forum: Multimedia Software
---

### Post by StylusJunky on 2013-03-20
When I connect to my TV with HDMI, the top and left margins are off the screen.  I am unable to see the top menu bar or the launcher.  Everything works fine except for the margins.  Is there any way to correct this? 

Here is the output from xrandr --verbose
HDMI1 connected 1920x1080+0+0 (0x4d) normal (normal left inverted right x axis y axis) 700mm x 390mm
    Identifier: 0x43
    Timestamp:  15589176
    Subpixel:   unknown
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0
    Clones:    
    CRTC:       0
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    EDID:
        00ffffffffffff00593a220001010101
        0911010380522e780ad970a357499c25
        11494b20000001010101010101010101
        0101010101c1011d007251d01e206e1f
        5500bc862100001e000000fd0032551f
        460b000a202020202020000000ff0053
        4c4142424830393231373330000000fc
        00565833374c20484454563130410151
        02031d714a8401031305121514060723
        0907038301000065030c002000011d00
        bc52d01e20b8285540bc862100001e01
        1d80d0721c1620102c2580bc86210000
        9e8c0ad08a20e02d10103e9600bc8621
        000018011d8018711c1620582c2500bc
        862100009e8c0ad090204031200c4055
        00bc8621000018000000000000000037
    Broadcast RGB:    Full
        supported: Full         Limited 16:2
    audio:    auto
        supported: force-dvi    off          auto         on          
  1280x720 (0x4c)   74.2MHz +HSync +VSync +preferred
        h: width  1280 start 1390 end 1421 total 1650 skew    0 clock   45.0KHz
        v: height  720 start  725 end  730 total  750           clock   60.0Hz
  1920x1080 (0x4d)   74.2MHz +HSync +VSync Interlace *current
        h: width  1920 start 2448 end 2492 total 2640 skew    0 clock   28.1KHz
        v: height 1080 start 1084 end 1094 total 1125           clock   25.0Hz
  1920x1080 (0x4e)   74.2MHz +HSync +VSync Interlace
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock   33.8KHz
        v: height 1080 start 1084 end 1094 total 1125           clock   30.0Hz
  1400x1050 (0x4f)  101.0MHz +HSync -VSync
        h: width  1400 start 1448 end 1480 total 1560 skew    0 clock   64.7KHz
        v: height 1050 start 1053 end 1057 total 1080           clock   59.9Hz
  1280x1024 (0x50)  108.0MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock   64.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   60.0Hz
  1440x900 (0x51)   88.8MHz +HSync -VSync
        h: width  1440 start 1488 end 1520 total 1600 skew    0 clock   55.5KHz
        v: height  900 start  903 end  909 total  926           clock   59.9Hz
  1280x960 (0x52)  108.0MHz +HSync +VSync
        h: width  1280 start 1376 end 1488 total 1800 skew    0 clock   60.0KHz
        v: height  960 start  961 end  964 total 1000           clock   60.0Hz
  1366x768 (0x53)   85.9MHz -HSync +VSync
        h: width  1366 start 1439 end 1583 total 1800 skew    0 clock   47.7KHz
        v: height  768 start  769 end  772 total  795           clock   60.0Hz
  1360x768 (0x54)   85.5MHz +HSync +VSync
        h: width  1360 start 1424 end 1536 total 1792 skew    0 clock   47.7KHz
        v: height  768 start  771 end  777 total  795           clock   60.0Hz
  1280x800 (0x55)  106.5MHz -HSync +VSync
        h: width  1280 start 1360 end 1488 total 1696 skew    0 clock   62.8KHz
        v: height  800 start  803 end  809 total  838           clock   74.9Hz
  1280x800 (0x56)   71.0MHz +HSync -VSync
        h: width  1280 start 1328 end 1360 total 1440 skew    0 clock   49.3KHz
        v: height  800 start  803 end  809 total  823           clock   59.9Hz
  1152x864 (0x57)  108.0MHz +HSync +VSync
        h: width  1152 start 1216 end 1344 total 1600 skew    0 clock   67.5KHz
        v: height  864 start  865 end  868 total  900           clock   75.0Hz
  1280x768 (0x58)  102.2MHz +HSync -VSync
        h: width  1280 start 1360 end 1488 total 1696 skew    0 clock   60.3KHz
        v: height  768 start  771 end  778 total  805           clock   74.9Hz
  1280x768 (0x59)   68.2MHz +HSync -VSync
        h: width  1280 start 1328 end 1360 total 1440 skew    0 clock   47.4KHz
        v: height  768 start  771 end  778 total  790           clock   60.0Hz
  1280x720 (0x5a)   74.2MHz +HSync +VSync
        h: width  1280 start 1720 end 1760 total 1980 skew    0 clock   37.5KHz
        v: height  720 start  725 end  730 total  750           clock   50.0Hz
  1280x720 (0x5b)   74.2MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock   45.0KHz
        v: height  720 start  725 end  730 total  750           clock   60.0Hz
  1440x576 (0x5c)   27.0MHz -HSync -VSync Interlace
        h: width  1440 start 1464 end 1590 total 1728 skew    0 clock   15.6KHz
        v: height  576 start  580 end  586 total  625           clock   25.0Hz
  1024x768 (0x5d)   94.5MHz +HSync +VSync
        h: width  1024 start 1072 end 1168 total 1376 skew    0 clock   68.7KHz
        v: height  768 start  769 end  772 total  808           clock   85.0Hz
  1024x768 (0x5e)   78.8MHz +HSync +VSync
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock   60.0KHz
        v: height  768 start  769 end  772 total  800           clock   75.0Hz
  1024x768 (0x5f)   75.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1328 skew    0 clock   56.5KHz
        v: height  768 start  771 end  777 total  806           clock   70.1Hz
  1024x768 (0x48)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  1440x480 (0x60)   27.0MHz -HSync -VSync Interlace
        h: width  1440 start 1478 end 1602 total 1716 skew    0 clock   15.7KHz
        v: height  480 start  488 end  494 total  525           clock   30.0Hz
  1024x576 (0x61)   47.0MHz -HSync +VSync
        h: width  1024 start 1064 end 1168 total 1312 skew    0 clock   35.8KHz
        v: height  576 start  577 end  580 total  597           clock   60.0Hz
  800x600 (0x62)   56.2MHz +HSync +VSync
        h: width   800 start  832 end  896 total 1048 skew    0 clock   53.7KHz
        v: height  600 start  601 end  604 total  631           clock   85.1Hz
  800x600 (0x63)   50.0MHz +HSync +VSync
        h: width   800 start  856 end  976 total 1040 skew    0 clock   48.1KHz
        v: height  600 start  637 end  643 total  666           clock   72.2Hz
  800x600 (0x64)   49.5MHz +HSync +VSync
        h: width   800 start  816 end  896 total 1056 skew    0 clock   46.9KHz
        v: height  600 start  601 end  604 total  625           clock   75.0Hz
  800x600 (0x49)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  800x600 (0x4a)   36.0MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock   35.2KHz
        v: height  600 start  601 end  603 total  625           clock   56.2Hz
  720x576 (0x65)   27.0MHz -HSync -VSync
        h: width   720 start  732 end  796 total  864 skew    0 clock   31.2KHz
        v: height  576 start  581 end  586 total  625           clock   50.0Hz
  848x480 (0x66)   33.8MHz +HSync +VSync
        h: width   848 start  864 end  976 total 1088 skew    0 clock   31.0KHz
        v: height  480 start  486 end  494 total  517           clock   60.0Hz
  720x480 (0x67)   27.0MHz -HSync -VSync
        h: width   720 start  736 end  798 total  858 skew    0 clock   31.5KHz
        v: height  480 start  489 end  495 total  525           clock   59.9Hz
  640x480 (0x68)   36.0MHz -HSync -VSync
        h: width   640 start  696 end  752 total  832 skew    0 clock   43.3KHz
        v: height  480 start  481 end  484 total  509           clock   85.0Hz
  640x480 (0x69)   31.5MHz -HSync -VSync
        h: width   640 start  656 end  720 total  840 skew    0 clock   37.5KHz
        v: height  480 start  481 end  484 total  500           clock   75.0Hz
  640x480 (0x6a)   31.5MHz -HSync -VSync
        h: width   640 start  664 end  704 total  832 skew    0 clock   37.9KHz
        v: height  480 start  489 end  492 total  520           clock   72.8Hz
  640x480 (0x6b)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   60.0Hz
  640x480 (0x4b)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
  720x400 (0x6c)   35.5MHz -HSync +VSync
        h: width   720 start  756 end  828 total  936 skew    0 clock   37.9KHz
        v: height  400 start  401 end  404 total  446           clock   85.0Hz
  640x400 (0x6d)   31.5MHz -HSync +VSync
        h: width   640 start  672 end  736 total  832 skew    0 clock   37.9KHz
        v: height  400 start  401 end  404 total  445           clock   85.1Hz
  640x350 (0x6e)   31.5MHz +HSync -VSync
        h: width   640 start  672 end  736 total  832 skew    0 clock   37.9KHz
        v: height  350 start  382 end  385 total  445           clock   85.1Hz

---

