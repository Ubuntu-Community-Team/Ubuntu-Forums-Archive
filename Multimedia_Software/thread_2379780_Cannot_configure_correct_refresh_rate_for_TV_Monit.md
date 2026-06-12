---
title: "Cannot configure correct refresh rate for TV Monitor on Xorg"
date: 2017-12-09
forum: Multimedia Software
---

### Post by unholder on 2017-12-09
My problem is with a TCL 49s405 4K TV on Ubuntu 16.04.3. I automatically get 4K@60Hz in Windows, with 4:4:4 rendering, however xorg does not recognize all the modelines from its EDID file. I have tried almost all troubleshooting steps that I could find out there, even ones that were from other Linux platforms. Some of them are:

 - Manually  add the modeline built with cvt to xrandr which always
   returns: "xrandr: Configure crtc 1 failed."
 - Configured all monitor specs in xorg.conf.
 - Tried to make xorg ignore the EDID file, but since I am using the Intel graphics, the option doesn't do anything.
 - Manually extracted the EDID file from Windows and pointed the Display port to it, but this breaks lightDM and it won't even start.
   It will go on "Low graphics mode."
 - I have been monitoring the Xorg.0.log while doing all this and the only thing I found out is that xorg "corrupts" (actually makes
   changes in) the EDID file I copied in the X11 directory. The xorg
   logs shows the gibberish when trying to read it. I know the file I
   copy is fine because I read with edide-decode before restarting X,
   and it looks fine but it shows gibberish characters in the beginning
   of the file after.

The only time that I came close to getting 3840x2160@60Hz is with a reduced modeline. However, this would cause the monitor to switch to 4:2:0 mode and makes it hard to read text, which is what I want to do with this.

The modeline that the TV EDID file shows for 4k@60 doesn't match the numbers that CVT produces, but when I tried it with the modeline copied directly from the EDID file, xrandr returns the same error. I have also tried adding this to xorg.conf with a and setting it as preferred mode, and it doesn't work either.

The last two Wiki pages that I have followed are these:

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

[https://wiki.ubuntu.com/X/Troubleshooting/Resolution](https://wiki.ubuntu.com/X/Troubleshooting/Resolution)

I would really appreciate any help, I have been digging all over for a few weeks now!

Here are some info that might be useful:

The monitor is connected with a HDMI 2.0 cable to a mini Display Port to HDMI adapter (4k compatible) to my Lenovo ThinkPad T450s.

Outpu of xrandr --verbose:
```

        Screen 0: minimum 8 x 8, current 4096 x 3240, maximum 32767 x 32767
    eDP1 connected primary 1920x1080+0+2160 (0x4a) normal (normal left inverted right x axis y axis) 310mm x 170mm
        Identifier: 0x43
        Timestamp:  52223346
        Subpixel:   unknown
        Gamma:      1.0:1.0:1.0
        Brightness: 1.0
        Clones:    
        CRTC:       0
        CRTCs:      0 1 2
        Transform:  1.000000 0.000000 0.000000
                    0.000000 1.000000 0.000000
                    0.000000 0.000000 1.000000
                   filter: 
        EDID: 
            00ffffffffffff0030e46d0400000000
            00180104951f1178eadc95a35855a026
            0d505400000001010101010101010101
            0101010101012e3680a070381f403020
            350035ae1000001a0000000000000000
            00000000000000000000000000fe004c
            4720446973706c61790a2020000000fe
            004c503134305746332d5350443100c3
        BACKLIGHT: 852 
            range: (0, 852)
        Backlight: 852 
            range: (0, 852)
        scaling mode: Full aspect 
            supported: None, Full, Center, Full aspect
        Broadcast RGB: Automatic 
            supported: Automatic, Full, Limited 16:235
        audio: auto 
            supported: force-dvi, off, auto, on
      1920x1080 (0x4a) 138.700MHz +HSync -VSync *current +preferred
            h: width  1920 start 1968 end 2000 total 2080 skew    0 clock  66.68KHz
            v: height 1080 start 1083 end 1088 total 1111           clock  60.02Hz
      1920x1080 (0x4b) 138.500MHz +HSync -VSync
            h: width  1920 start 1968 end 2000 total 2080 skew    0 clock  66.59KHz
            v: height 1080 start 1083 end 1088 total 1111           clock  59.93Hz
      1680x1050 (0x4c) 119.000MHz +HSync -VSync
            h: width  1680 start 1728 end 1760 total 1840 skew    0 clock  64.67KHz
            v: height 1050 start 1053 end 1059 total 1080           clock  59.88Hz
      1600x1024 (0x4d) 103.125MHz +HSync +VSync
            h: width  1600 start 1600 end 1656 total 1664 skew    0 clock  61.97KHz
            v: height 1024 start 1024 end 1029 total 1030           clock  60.17Hz
      1400x1050 (0x4e) 122.000MHz +HSync +VSync
            h: width  1400 start 1488 end 1640 total 1880 skew    0 clock  64.89KHz
            v: height 1050 start 1052 end 1064 total 1082           clock  59.98Hz
      1600x900 (0x4f) 118.997MHz -HSync +VSync
            h: width  1600 start 1696 end 1864 total 2128 skew    0 clock  55.92KHz
            v: height  900 start  901 end  904 total  932           clock  60.00Hz
      1280x1024 (0x50) 108.000MHz +HSync +VSync
            h: width  1280 start 1328 end 1440 total 1688 skew    0 clock  63.98KHz
            v: height 1024 start 1025 end 1028 total 1066           clock  60.02Hz
      1440x900 (0x51) 106.500MHz -HSync +VSync
            h: width  1440 start 1520 end 1672 total 1904 skew    0 clock  55.93KHz
            v: height  900 start  903 end  909 total  934           clock  59.89Hz
      1280x960 (0x52) 108.000MHz +HSync +VSync
            h: width  1280 start 1376 end 1488 total 1800 skew    0 clock  60.00KHz
            v: height  960 start  961 end  964 total 1000           clock  60.00Hz
      1368x768 (0x53) 85.860MHz -HSync +VSync
            h: width  1368 start 1440 end 1584 total 1800 skew    0 clock  47.70KHz
            v: height  768 start  769 end  772 total  795           clock  60.00Hz
      1360x768 (0x54) 84.750MHz -HSync +VSync
            h: width  1360 start 1432 end 1568 total 1776 skew    0 clock  47.72KHz
            v: height  768 start  771 end  781 total  798           clock  59.80Hz
      1360x768 (0x55) 72.000MHz +HSync -VSync
            h: width  1360 start 1408 end 1440 total 1520 skew    0 clock  47.37KHz
            v: height  768 start  771 end  781 total  790           clock  59.96Hz
      1152x864 (0x56) 81.620MHz -HSync +VSync
            h: width  1152 start 1216 end 1336 total 1520 skew    0 clock  53.70KHz
            v: height  864 start  865 end  868 total  895           clock  60.00Hz
      1280x720 (0x57) 74.480MHz -HSync +VSync
            h: width  1280 start 1336 end 1472 total 1664 skew    0 clock  44.76KHz
            v: height  720 start  721 end  724 total  746           clock  60.00Hz
      1024x768 (0x58) 65.000MHz -HSync -VSync
            h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
            v: height  768 start  771 end  777 total  806           clock  60.00Hz
      1024x576 (0x59) 46.995MHz -HSync +VSync
            h: width  1024 start 1064 end 1168 total 1312 skew    0 clock  35.82KHz
            v: height  576 start  577 end  580 total  597           clock  60.00Hz
      960x540 (0x5a) 40.784MHz -HSync +VSync
            h: width   960 start  992 end 1088 total 1216 skew    0 clock  33.54KHz
            v: height  540 start  541 end  544 total  559           clock  60.00Hz
      800x600 (0x5b) 40.000MHz +HSync +VSync
            h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
            v: height  600 start  601 end  605 total  628           clock  60.32Hz
      800x600 (0x5c) 36.000MHz +HSync +VSync
            h: width   800 start  824 end  896 total 1024 skew    0 clock  35.16KHz
            v: height  600 start  601 end  603 total  625           clock  56.25Hz
      864x486 (0x5d) 32.901MHz -HSync +VSync
            h: width   864 start  888 end  976 total 1088 skew    0 clock  30.24KHz
            v: height  486 start  487 end  490 total  504           clock  60.00Hz
      640x480 (0x5e) 25.175MHz -HSync -VSync
            h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
            v: height  480 start  490 end  492 total  525           clock  59.94Hz
      720x405 (0x5f) 22.176MHz -HSync +VSync
            h: width   720 start  728 end  800 total  880 skew    0 clock  25.20KHz
            v: height  405 start  406 end  409 total  420           clock  60.00Hz
      640x360 (0x60) 17.187MHz -HSync +VSync
            h: width   640 start  640 end  704 total  768 skew    0 clock  22.38KHz
            v: height  360 start  361 end  364 total  373           clock  60.00Hz
    DP1 connected 4096x2160+0+0 (0x62) normal (normal left inverted right x axis y axis) 1100mm x 620mm
        Identifier: 0x44
        Timestamp:  52223346
        Subpixel:   unknown
        Gamma:      1.0:1.0:1.0
        Brightness: 1.0
        Clones:     HDMI1
        CRTC:       1
        CRTCs:      0 1 2
        Transform:  1.000000 0.000000 0.000000
                    0.000000 1.000000 0.000000
                    0.000000 0.000000 1.000000
                   filter: 
        EDID: 
            00ffffffffffff00506c000000000000
            001b0103806e3e780a8a9da455529f25
            0e474aadcf00714f8140818081009500
            b300d1c081c008e80030f2705a80b058
            8a0020c23100001e04740030f2705a80
            b0588a0020c23100001e000000fc0034
            39533430350a202020202020000000fd
            00184b0f873c000a202020202020012d
            0203477150615f5d6664621022200504
            3e3c0201062909070715075057070083
            010000e200cfe305c0006d030c003000
            b83c20106001030467d85dc401788003
            e3060501e20f09023a801871382d4058
            2c450020c23100001e011d007251d01e
            206e28550020c23100001e662150b051
            001b304070360000000000001e000052
        Broadcast RGB: Automatic 
            supported: Automatic, Full, Limited 16:235
        audio: auto 
            supported: force-dvi, off, auto, on
      1920x1080 (0x61) 148.500MHz +HSync +VSync +preferred
            h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  67.50KHz
            v: height 1080 start 1084 end 1089 total 1125           clock  60.00Hz
      4096x2160 (0x62) 297.000MHz +HSync +VSync *current
            h: width  4096 start 5116 end 5204 total 5500 skew    0 clock  54.00KHz
            v: height 2160 start 2168 end 2178 total 2250           clock  24.00Hz
      4096x2160 (0x63) 296.703MHz +HSync +VSync
            h: width  4096 start 5116 end 5204 total 5500 skew    0 clock  53.95KHz
            v: height 2160 start 2168 end 2178 total 2250           clock  23.98Hz
      3840x2160 (0x64) 297.000MHz +HSync +VSync
            h: width  3840 start 4016 end 4104 total 4400 skew    0 clock  67.50KHz
            v: height 2160 start 2168 end 2178 total 2250           clock  30.00Hz
      3840x2160 (0x65) 297.000MHz +HSync +VSync
            h: width  3840 start 5116 end 5204 total 5500 skew    0 clock  54.00KHz
            v: height 2160 start 2168 end 2178 total 2250           clock  24.00Hz
      3840x2160 (0x66) 296.703MHz +HSync +VSync
            h: width  3840 start 4016 end 4104 total 4400 skew    0 clock  67.43KHz
            v: height 2160 start 2168 end 2178 total 2250           clock  29.97Hz
      3840x2160 (0x67) 296.703MHz +HSync +VSync
            h: width  3840 start 5116 end 5204 total 5500 skew    0 clock  53.95KHz
            v: height 2160 start 2168 end 2178 total 2250           clock  23.98Hz
      1920x1080 (0x68) 148.352MHz +HSync +VSync
            h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  67.43KHz
            v: height 1080 start 1084 end 1089 total 1125           clock  59.94Hz
      1920x1080i (0x69) 74.250MHz +HSync +VSync Interlace
            h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  33.75KHz
            v: height 1080 start 1084 end 1094 total 1125           clock  60.00Hz
      1920x1080 (0x6a) 74.250MHz +HSync +VSync
            h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  33.75KHz
            v: height 1080 start 1084 end 1089 total 1125           clock  30.00Hz
      1920x1080 (0x6b) 74.250MHz +HSync +VSync
            h: width  1920 start 2558 end 2602 total 2750 skew    0 clock  27.00KHz
            v: height 1080 start 1084 end 1089 total 1125           clock  24.00Hz
      1920x1080i (0x6c) 74.176MHz +HSync +VSync Interlace
            h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  33.72KHz
            v: height 1080 start 1084 end 1094 total 1125           clock  59.94Hz
      1920x1080 (0x6d) 74.176MHz +HSync +VSync
            h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  33.72KHz
            v: height 1080 start 1084 end 1089 total 1125           clock  29.97Hz
      1920x1080 (0x6e) 74.176MHz +HSync +VSync
            h: width  1920 start 2558 end 2602 total 2750 skew    0 clock  26.97KHz
            v: height 1080 start 1084 end 1089 total 1125           clock  23.98Hz
      1680x1050 (0x4c) 119.000MHz +HSync -VSync
            h: width  1680 start 1728 end 1760 total 1840 skew    0 clock  64.67KHz
            v: height 1050 start 1053 end 1059 total 1080           clock  59.88Hz
      1280x1024 (0x6f) 135.000MHz +HSync +VSync
            h: width  1280 start 1296 end 1440 total 1688 skew    0 clock  79.98KHz
            v: height 1024 start 1025 end 1028 total 1066           clock  75.02Hz
      1280x1024 (0x50) 108.000MHz +HSync +VSync
            h: width  1280 start 1328 end 1440 total 1688 skew    0 clock  63.98KHz
            v: height 1024 start 1025 end 1028 total 1066           clock  60.02Hz
      1440x900 (0x70) 88.750MHz +HSync -VSync
            h: width  1440 start 1488 end 1520 total 1600 skew    0 clock  55.47KHz
            v: height  900 start  903 end  909 total  926           clock  59.90Hz
      1280x960 (0x52) 108.000MHz +HSync +VSync
            h: width  1280 start 1376 end 1488 total 1800 skew    0 clock  60.00KHz
            v: height  960 start  961 end  964 total 1000           clock  60.00Hz
      1360x768 (0x71) 85.500MHz +HSync +VSync
            h: width  1360 start 1424 end 1536 total 1792 skew    0 clock  47.71KHz
            v: height  768 start  771 end  777 total  795           clock  60.02Hz
      1280x800 (0x72) 71.000MHz +HSync -VSync
            h: width  1280 start 1328 end 1360 total 1440 skew    0 clock  49.31KHz
            v: height  800 start  803 end  809 total  823           clock  59.91Hz
      1152x864 (0x73) 108.000MHz +HSync +VSync
            h: width  1152 start 1216 end 1344 total 1600 skew    0 clock  67.50KHz
            v: height  864 start  865 end  868 total  900           clock  75.00Hz
      1280x720 (0x74) 74.250MHz +HSync +VSync
            h: width  1280 start 1390 end 1430 total 1650 skew    0 clock  45.00KHz
            v: height  720 start  725 end  730 total  750           clock  60.00Hz
      1280x720 (0x75) 74.250MHz +HSync +VSync
            h: width  1280 start 3040 end 3080 total 3300 skew    0 clock  22.50KHz
            v: height  720 start  725 end  730 total  750           clock  30.00Hz
      1280x720 (0x76) 74.176MHz +HSync +VSync
            h: width  1280 start 1390 end 1430 total 1650 skew    0 clock  44.96KHz
            v: height  720 start  725 end  730 total  750           clock  59.94Hz
      1280x720 (0x77) 74.176MHz +HSync +VSync
            h: width  1280 start 3040 end 3080 total 3300 skew    0 clock  22.48KHz
            v: height  720 start  725 end  730 total  750           clock  29.97Hz
      1280x720 (0x78) 59.400MHz +HSync +VSync
            h: width  1280 start 3040 end 3080 total 3300 skew    0 clock  18.00KHz
            v: height  720 start  725 end  730 total  750           clock  24.00Hz
      1280x720 (0x79) 59.341MHz +HSync +VSync
            h: width  1280 start 3040 end 3080 total 3300 skew    0 clock  17.98KHz
            v: height  720 start  725 end  730 total  750           clock  23.98Hz
      1024x768 (0x7a) 78.750MHz +HSync +VSync
            h: width  1024 start 1040 end 1136 total 1312 skew    0 clock  60.02KHz
            v: height  768 start  769 end  772 total  800           clock  75.03Hz
      1024x768 (0x7b) 75.000MHz -HSync -VSync
            h: width  1024 start 1048 end 1184 total 1328 skew    0 clock  56.48KHz
            v: height  768 start  771 end  777 total  806           clock  70.07Hz
      1024x768 (0x58) 65.000MHz -HSync -VSync
            h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
            v: height  768 start  771 end  777 total  806           clock  60.00Hz
      800x600 (0x7c) 50.000MHz +HSync +VSync
            h: width   800 start  856 end  976 total 1040 skew    0 clock  48.08KHz
            v: height  600 start  637 end  643 total  666           clock  72.19Hz
      800x600 (0x7d) 49.500MHz +HSync +VSync
            h: width   800 start  816 end  896 total 1056 skew    0 clock  46.88KHz
            v: height  600 start  601 end  604 total  625           clock  75.00Hz
      800x600 (0x5b) 40.000MHz +HSync +VSync
            h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
            v: height  600 start  601 end  605 total  628           clock  60.32Hz
      720x480 (0x7e) 27.027MHz -HSync -VSync
            h: width   720 start  736 end  798 total  858 skew    0 clock  31.50KHz
            v: height  480 start  489 end  495 total  525           clock  60.00Hz
      720x480 (0x7f) 27.000MHz -HSync -VSync
            h: width   720 start  736 end  798 total  858 skew    0 clock  31.47KHz
            v: height  480 start  489 end  495 total  525           clock  59.94Hz
      640x480 (0x80) 31.500MHz -HSync -VSync
            h: width   640 start  656 end  720 total  840 skew    0 clock  37.50KHz
            v: height  480 start  481 end  484 total  500           clock  75.00Hz
      640x480 (0x81) 31.500MHz -HSync -VSync
            h: width   640 start  664 end  704 total  832 skew    0 clock  37.86KHz
            v: height  480 start  489 end  492 total  520           clock  72.81Hz
      640x480 (0x82) 25.200MHz -HSync -VSync
            h: width   640 start  656 end  752 total  800 skew    0 clock  31.50KHz
            v: height  480 start  490 end  492 total  525           clock  60.00Hz
      640x480 (0x5e) 25.175MHz -HSync -VSync
            h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
            v: height  480 start  490 end  492 total  525           clock  59.94Hz
      720x400 (0x83) 28.320MHz -HSync +VSync
            h: width   720 start  738 end  846 total  900 skew    0 clock  31.47KHz
            v: height  400 start  412 end  414 total  449           clock  70.08Hz
      3840x2160_60.00 (0x163) 712.750MHz -HSync +VSync
            h: width  3840 start 4160 end 4576 total 5312 skew    0 clock 134.18KHz
            v: height 2160 start 2163 end 2168 total 2237           clock  59.98Hz
    DP2 disconnected (normal left inverted right x axis y axis)
        Identifier: 0x45
        Timestamp:  52223346
        Subpixel:   unknown
        Clones:     HDMI2
        CRTCs:      0 1 2
        Transform:  1.000000 0.000000 0.000000
                    0.000000 1.000000 0.000000
                    0.000000 0.000000 1.000000
                   filter: 
        Broadcast RGB: Automatic 
            supported: Automatic, Full, Limited 16:235
        audio: auto 
            supported: force-dvi, off, auto, on
    HDMI1 disconnected (normal left inverted right x axis y axis)
        Identifier: 0x46
        Timestamp:  52223346
        Subpixel:   unknown
        Clones:     DP1
        CRTCs:      0 1 2
        Transform:  1.000000 0.000000 0.000000
                    0.000000 1.000000 0.000000
                    0.000000 0.000000 1.000000
                   filter: 
        aspect ratio: Automatic 
            supported: Automatic, 4:3, 16:9
        Broadcast RGB: Automatic 
            supported: Automatic, Full, Limited 16:235
        audio: auto 
            supported: force-dvi, off, auto, on
    HDMI2 disconnected (normal left inverted right x axis y axis)
        Identifier: 0x47
        Timestamp:  52223346
        Subpixel:   unknown
        Clones:     DP2
        CRTCs:      0 1 2
        Transform:  1.000000 0.000000 0.000000
                    0.000000 1.000000 0.000000
                    0.000000 0.000000 1.000000
                   filter: 
        aspect ratio: Automatic 
            supported: Automatic, 4:3, 16:9
        Broadcast RGB: Automatic 
            supported: Automatic, Full, Limited 16:235
        audio: auto 
            supported: force-dvi, off, auto, on
    VIRTUAL1 disconnected (normal left inverted right x axis y axis)
        Identifier: 0x48
        Timestamp:  52223346
        Subpixel:   no subpixels
        Clones:    
        CRTCs:      3
        Transform:  1.000000 0.000000 0.000000
                    0.000000 1.000000 0.000000
                    0.000000 0.000000 1.000000
                   filter: 
```

This is the last xorg.conf file that I built and worked:
```

    Section "Device"
            Identifier      "Intel 945G"
            Driver         "intel"
    
            # Using the name of the output defined by the video driver plus the identifier of a
            #     monitor section, one associates a monitor section with an output by adding an
            #     option to the Device section in the following format:
            #     Option "Monitor-outputname" "monitor ID"
    
            Option          "monitor-eDP-1" "bar"
            Option          "monitor-DP-1" "foo"
        Option          "monitor-DP1" "foo"
            Option          "monitor-eDP1" "bar"
        #Option        "monitor-DP-1" "telv"
            #Option         "monitor-TMDS-1" "dvi"
        Option          "CustomEDID" "DP1:/etc/X11/dp1.edid"
    EndSection
    
    Section "Device"
            Identifier      "Joobed"
            Driver         "intel"
    
            # Using the name of the output defined by the video driver plus the identifier of a
            #     monitor section, one associates a monitor section with an output by adding an
            #     option to the Device section in the following format:
            #     Option "Monitor-outputname" "monitor ID"
    
            #Option          "monitor-eDP-1" "bar"
            Option          "monitor-DP-1" "foo"
        Option          "monitor-DP1" "foo"
            #Option         "monitor-eDP1" "bar"
        #Option        "monitor-DP-1" "telv"
            #Option         "monitor-TMDS-1" "dvi"
        Option         "CustomEDID" "DP1:/etc/X11/dp1.edid"
    EndSection
    
    Section "Monitor"
            Identifier      "bar"
    
            #Options LeftOf, RightOf, Above, Below specify monitors' relative position
    
            # This optional entry specifies  whether  the  monitor  should  be
            #     turned  on  at  startup.  By default, the server will attempt to
            #     enable all connected monitors.
            #Option "Enable"  "true"       
    
            #This optional entry specifies the initial rotation of the given monitor.
            #     Valid values for rotation are "normal", "left", "right", and "inverted".
            # Option "Rotate"  "left"
    EndSection
    
    Section "Monitor"
            Identifier      "foo"
    
            Option "Above"  "bar"
        VendorName      "TCL"
        HorizSync       15-135
        VertRefresh     24-75
        DisplaySize     1100 620
        Gamma           2.20
        
            # specifies a mode to be marked as the preferred initial mode of the monitor
            # Option "PreferredMode"  "800x600"
            # This optional entry specifies the position of the monitor within the X screen.
            #Option        "Position" "1024 0"
            #This optional entry specifies that the monitor should be ignored
            #     entirely, and not reported through RandR.  This is useful if the
            #     hardware reports  the  presence  of  outputs  that do not exist.
            #Option "Ignore"  "true"
    EndSection
    
    Section "Screen"
            Identifier      "Default Screen"
            Device        "Intel 945G"
            Monitor       "bar"
            DefaultDepth  24
            SubSection "Display"
                    Depth          24
                    Modes         "1920x1080"  "1280x1024"  "1024x768"   "640x480"
            EndSubSection
    EndSection
    
    Section "Screen"
            Identifier      "Secondary Screen"
            Device        "Intel 945G"
            Monitor       "foo"
            DefaultDepth  24
            SubSection "Display"
                    Depth          24
                    Modes         "1920x1080"  "1280x1024"  "1024x768"   "640x480"
            EndSubSection
    EndSection

```

---

### Post by Autodave on 2017-12-10
What video card are you running? Did you install any driver for it and if so, where did you get the driver from?

---

### Post by unholder on 2017-12-10
> **Autodave said:**
> What video card are you running? Did you install any driver for it and if so, where did you get the driver from?

Thanks for replying! As I said in the OP, I'm using Intel HD Graphics 550. Intel drivers are installed and I got additional proprietary drivers with the Intel Graphics Update Tool.

---

### Post by benhur10cp on 2017-12-10
[COLOR=#000000]Hi, i have the same issue. I'm running ubuntu 17 and nvidia GT 1030, on a samsung 40mu6100 4k.[/COLOR]

---

