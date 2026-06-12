---
title: "hdmi on inspiron1525 -no image output"
date: 2012-01-10
forum: Multimedia Software
---

### Post by lessless on 2012-01-10
Hello! I connect laptop to tv with hdmi-hdmi cable and enabled HDMI1 in the Display Perferences, but screen on the TV is still black. Here is xrandr info: 

> 
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 8192 x 8192
LVDS1 connected 1440x900+0+0 (0x45) normal (normal left inverted right x axis y axis) 331mm x 207mm
    Identifier: 0x41
    Timestamp:  47810509
    Subpixel:   horizontal rgb
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0
    Clones:    
    CRTC:       1
    CRTCs:      1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    EDID:
        00ffffffffffff00320c00df00000000
        00110103802115780ae9d59959538e28
        26505400000001010101010101010101
        010101010101de21a07050841f302020
        56004bcf10000018de21a07050841f30
        202056004bcf10000000000000fe004b
        52353135003135345750310a000000fe
        0023333d486584aaff02010a202000a3
    BACKLIGHT: 1 (0x00000001)    range:  (0,7)
    Backlight: 1 (0x00000001)    range:  (0,7)
    scaling mode:    Full aspect
        supported: None         Full         Center       Full aspect 
  1440x900 (0x45)   86.7MHz -HSync -VSync *current +preferred
        h: width  1440 start 1472 end 1504 total 1552 skew    0 clock   55.9KHz
        v: height  900 start  905 end  911 total  931           clock   60.0Hz
  1440x900 (0x46)  106.5MHz -HSync +VSync
        h: width  1440 start 1520 end 1672 total 1904 skew    0 clock   55.9KHz
        v: height  900 start  903 end  909 total  934           clock   59.9Hz
  1360x768 (0x47)   84.8MHz -HSync +VSync
        h: width  1360 start 1432 end 1568 total 1776 skew    0 clock   47.7KHz
        v: height  768 start  771 end  781 total  798           clock   59.8Hz
  1360x768 (0x48)   72.0MHz +HSync -VSync
        h: width  1360 start 1408 end 1440 total 1520 skew    0 clock   47.4KHz
        v: height  768 start  771 end  781 total  790           clock   60.0Hz
  1152x864 (0x49)   81.6MHz -HSync +VSync
        h: width  1152 start 1216 end 1336 total 1520 skew    0 clock   53.7KHz
        v: height  864 start  865 end  868 total  895           clock   60.0Hz
  1024x768 (0x4a)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x4b)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  800x600 (0x4c)   36.0MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock   35.2KHz
        v: height  600 start  601 end  603 total  625           clock   56.2Hz
  640x480 (0x4d)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
VGA1 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x42
    Timestamp:  47810509
    Subpixel:   unknown
    Clones:     HDMI1
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
HDMI1 connected 1280x720+0+0 (0xc7) normal (normal left inverted right x axis y axis) 820mm x 460mm
    Identifier: 0x43
    Timestamp:  47810509
    Subpixel:   horizontal rgb
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0
    Clones:     VGA1
    CRTC:       0
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    EDID:
        00ffffffffffff004d10081000000000
        ff11010380522e782a1bbea25534b326
        144a5200000001010101010101010101
        010101010101011d00bc52d01e20b828
        554034cc3100001e011d007251d01e20
        6e28550034cc3100001e000000fc0053
        484152502048444d490a2020000000fd
        00313d0f2e08000a2020202020200196
        020325724d9384140512031102160715
        060123090707830100006a030c002000
        800f801501011d80d0721c1620102c25
        8034cc3100009e011d8018711c162058
        2c250034cc3100009e00000000000000
        00000000000000000000000000000000
        00000000000000000000000000000000
        00000000000000000000000000000037
    Broadcast RGB:    Full
        supported: Full         Limited 16:2
    audio:    auto
        supported: off          auto         on          
  1280x720 (0xc7)   74.2MHz +HSync +VSync *current +preferred
        h: width  1280 start 1720 end 1760 total 1980 skew    0 clock   37.5KHz
        v: height  720 start  725 end  730 total  750           clock   50.0Hz
  1280x720 (0xc8)   74.2MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock   45.0KHz
        v: height  720 start  725 end  730 total  750           clock   60.0Hz
TV1 unknown connection (normal left inverted right x axis y axis)
    Identifier: 0x44
    Timestamp:  47810509
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    bottom margin: 37 (0x00000025)    range:  (0,100)
    right margin: 46 (0x0000002e)    range:  (0,100)
    top margin: 36 (0x00000024)    range:  (0,100)
    left margin: 54 (0x00000036)    range:  (0,100)
    mode:    NTSC-M
        supported: NTSC-M       NTSC-443     NTSC-J       PAL-M       
                   PAL-N        PAL          480p@59.94Hz 480p@60Hz   
                   576p         720p@60Hz    720p@59.94Hz 720p@50Hz   
                   1080i@50Hz   1080i@60Hz   1080i@59.94H
  848x480 (0xc9)   14.5MHz +preferred
        h: width   848 start  849 end  912 total  944 skew    0 clock   15.4KHz
        v: height  480 start  481 end  512 total  513           clock   30.0Hz
  640x480 (0xca)   11.3MHz +preferred
        h: width   640 start  641 end  704 total  736 skew    0 clock   15.4KHz
        v: height  480 start  481 end  512 total  513           clock   30.0Hz
  1024x768 (0xcb)   26.9MHz
        h: width  1024 start 1025 end 1088 total 1120 skew    0 clock   24.0KHz
        v: height  768 start  769 end  800 total  801           clock   30.0Hz
  800x600 (0xcc)   17.0MHz
        h: width   800 start  801 end  864 total  896 skew    0 clock   19.0KHz
        v: height  600 start  601 end  632 total  633           clock   30.0Hz
lessless@lessless-Inspiron-1525:~/&#1047;&#1072;&#1075;&#1088;&#1091;&#1079;&#1082;&#1080;$ xrandr --verbose
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 8192 x 8192
LVDS1 connected 1440x900+0+0 (0x45) normal (normal left inverted right x axis y axis) 331mm x 207mm
    Identifier: 0x41
    Timestamp:  47810509
    Subpixel:   horizontal rgb
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0
    Clones:    
    CRTC:       1
    CRTCs:      1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    EDID:
        00ffffffffffff00320c00df00000000
        00110103802115780ae9d59959538e28
        26505400000001010101010101010101
        010101010101de21a07050841f302020
        56004bcf10000018de21a07050841f30
        202056004bcf10000000000000fe004b
        52353135003135345750310a000000fe
        0023333d486584aaff02010a202000a3
    BACKLIGHT: 1 (0x00000001)    range:  (0,7)
    Backlight: 1 (0x00000001)    range:  (0,7)
    scaling mode:    Full aspect
        supported: None         Full         Center       Full aspect 
  1440x900 (0x45)   86.7MHz -HSync -VSync *current +preferred
        h: width  1440 start 1472 end 1504 total 1552 skew    0 clock   55.9KHz
        v: height  900 start  905 end  911 total  931           clock   60.0Hz
  1440x900 (0x46)  106.5MHz -HSync +VSync
        h: width  1440 start 1520 end 1672 total 1904 skew    0 clock   55.9KHz
        v: height  900 start  903 end  909 total  934           clock   59.9Hz
  1360x768 (0x47)   84.8MHz -HSync +VSync
        h: width  1360 start 1432 end 1568 total 1776 skew    0 clock   47.7KHz
        v: height  768 start  771 end  781 total  798           clock   59.8Hz
  1360x768 (0x48)   72.0MHz +HSync -VSync
        h: width  1360 start 1408 end 1440 total 1520 skew    0 clock   47.4KHz
        v: height  768 start  771 end  781 total  790           clock   60.0Hz
  1152x864 (0x49)   81.6MHz -HSync +VSync
        h: width  1152 start 1216 end 1336 total 1520 skew    0 clock   53.7KHz
        v: height  864 start  865 end  868 total  895           clock   60.0Hz
  1024x768 (0x4a)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x4b)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  800x600 (0x4c)   36.0MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock   35.2KHz
        v: height  600 start  601 end  603 total  625           clock   56.2Hz
  640x480 (0x4d)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
VGA1 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x42
    Timestamp:  47810509
    Subpixel:   unknown
    Clones:     HDMI1
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
HDMI1 connected 1280x720+0+0 (0xc7) normal (normal left inverted right x axis y axis) 820mm x 460mm
    Identifier: 0x43
    Timestamp:  47810509
    Subpixel:   horizontal rgb
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0
    Clones:     VGA1
    CRTC:       0
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    EDID:
        00ffffffffffff004d10081000000000
        ff11010380522e782a1bbea25534b326
        144a5200000001010101010101010101
        010101010101011d00bc52d01e20b828
        554034cc3100001e011d007251d01e20
        6e28550034cc3100001e000000fc0053
        484152502048444d490a2020000000fd
        00313d0f2e08000a2020202020200196
        020325724d9384140512031102160715
        060123090707830100006a030c002000
        800f801501011d80d0721c1620102c25
        8034cc3100009e011d8018711c162058
        2c250034cc3100009e00000000000000
        00000000000000000000000000000000
        00000000000000000000000000000000
        00000000000000000000000000000037
    Broadcast RGB:    Full
        supported: Full         Limited 16:2
    audio:    auto
        supported: off          auto         on          
  1280x720 (0xc7)   74.2MHz +HSync +VSync *current +preferred
        h: width  1280 start 1720 end 1760 total 1980 skew    0 clock   37.5KHz
        v: height  720 start  725 end  730 total  750           clock   50.0Hz
  1280x720 (0xc8)   74.2MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock   45.0KHz
        v: height  720 start  725 end  730 total  750           clock   60.0Hz
TV1 unknown connection (normal left inverted right x axis y axis)
    Identifier: 0x44
    Timestamp:  47810509
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    bottom margin: 37 (0x00000025)    range:  (0,100)
    right margin: 46 (0x0000002e)    range:  (0,100)
    top margin: 36 (0x00000024)    range:  (0,100)
    left margin: 54 (0x00000036)    range:  (0,100)
    mode:    NTSC-M
        supported: NTSC-M       NTSC-443     NTSC-J       PAL-M       
                   PAL-N        PAL          480p@59.94Hz 480p@60Hz   
                   576p         720p@60Hz    720p@59.94Hz 720p@50Hz   
                   1080i@50Hz   1080i@60Hz   1080i@59.94H
  848x480 (0xc9)   14.5MHz +preferred
        h: width   848 start  849 end  912 total  944 skew    0 clock   15.4KHz
        v: height  480 start  481 end  512 total  513           clock   30.0Hz
  640x480 (0xca)   11.3MHz +preferred
        h: width   640 start  641 end  704 total  736 skew    0 clock   15.4KHz
        v: height  480 start  481 end  512 total  513           clock   30.0Hz
  1024x768 (0xcb)   26.9MHz
        h: width  1024 start 1025 end 1088 total 1120 skew    0 clock   24.0KHz
        v: height  768 start  769 end  800 total  801           clock   30.0Hz
  800x600 (0xcc)   17.0MHz
        h: width   800 start  801 end  864 total  896 skew    0 clock   19.0KHz
        v: height  600 start  601 end  632 total  633           clock   30.0Hz



---

