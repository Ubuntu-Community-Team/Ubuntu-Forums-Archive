---
title: "Dual head with NVidia (nouveau) and Dell FP2001"
date: 2010-06-15
forum: Multimedia Software
---

### Post by Dan Gravell on 2010-06-15
I'm trying to use the nouveau drivers to setup dual head with the following hardware/software:

Dell Latitude E6400 (a laptop)
NVidia Quadro NVS 160M
Dell FP2001 monitor connected via DVI in docking station
Xubuntu Lucid

The proprietary drivers with nvidia-settings *do* allow dual head, but cause other problems with the software I use (Eclipse IDE - corrupted graphics). So I want to use nouveau.

At boot time, the laptop screen is detected although it is put into a lower-than-desired resolution:
[HTML](--) NOUVEAU(0): Chipset: "NVIDIA NV98"
(II) NOUVEAU(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
(==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
(==) NOUVEAU(0): RGB weight 888
(==) NOUVEAU(0): Default visual is TrueColor
(==) NOUVEAU(0): Using HW cursor
(II) NOUVEAU(0): Output LVDS-1 has no monitor section
(II) NOUVEAU(0): Output VGA-1 has no monitor section
(II) NOUVEAU(0): Output DP-1 has no monitor section
(II) NOUVEAU(0): Output DP-2 has no monitor section
(II) NOUVEAU(0): EDID for output LVDS-1
(II) NOUVEAU(0): Manufacturer: LPL  Model: 140  Serial#: 0
(II) NOUVEAU(0): Year: 2008  Week: 0
(II) NOUVEAU(0): EDID Version: 1.3
(II) NOUVEAU(0): Digital Display Input
(II) NOUVEAU(0): Max Image Size [cm]: horiz.: 30  vert.: 19
(II) NOUVEAU(0): Gamma: 2.20
(II) NOUVEAU(0): No DPMS capabilities specified
(II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NOUVEAU(0): First detailed timing is preferred mode
(II) NOUVEAU(0): redX: 0.577 redY: 0.349   greenX: 0.329 greenY: 0.550
(II) NOUVEAU(0): blueX: 0.162 blueY: 0.133   whiteX: 0.313 whiteY: 0.329
(II) NOUVEAU(0): Manufacturer's mask: 0
(II) NOUVEAU(0): Supported detailed timing:
(II) NOUVEAU(0): clock: 101.6 MHz   Image Size:  304 x 190 mm
(II) NOUVEAU(0): h_active: 1440  h_sync: 1488  h_sync_end 1520 h_blank_end 1824 h_border: 0
(II) NOUVEAU(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 926 v_border: 0
(II) NOUVEAU(0): Supported detailed timing:
(II) NOUVEAU(0): clock: 101.6 MHz   Image Size:  304 x 190 mm
(II) NOUVEAU(0): h_active: 1440  h_sync: 1488  h_sync_end 1520 h_blank_end 1824 h_border: 0
(II) NOUVEAU(0): v_active: 900  v_sync: 910  v_sync_end 920 v_blanking: 1387 v_border: 0
(II) NOUVEAU(0):  CT008<80>141WP2
(II) NOUVEAU(0): Unknown vendor-specific block 0
(II) NOUVEAU(0): EDID (in hex):
(II) NOUVEAU(0):        00ffffffffffff00320c400100000000
(II) NOUVEAU(0):        00120103901e13780ad7859359548c29
(II) NOUVEAU(0):        22505400000001010101010101010101
(II) NOUVEAU(0):        010101010101b027a08051841a303020
(II) NOUVEAU(0):        360030be1000001ab027a0805184e731
(II) NOUVEAU(0):        3020aa0030be1000001a000000fe0043
(II) NOUVEAU(0):        54303038803134315750320a00000000
(II) NOUVEAU(0):        00000000000000000002010a202000ea
(II) NOUVEAU(0): EDID vendor "LPL", prod id 320
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1440x900"x0.0  101.60  1440 1488 1520 1824  900 903 909 926 +hsync -vsync (55.7 kHz)
(II) NOUVEAU(0): Modeline "1440x900"x0.0  101.60  1440 1488 1520 1824  900 910 920 1387 +hsync -vsync (55.7 kHz)
(II) NOUVEAU(0): Printing probed modes for output LVDS-1
(II) NOUVEAU(0): Modeline "1440x900"x60.2  101.60  1440 1488 1520 1824  900 903 909 926 +hsync -vsync (55.7 kHz)
(II) NOUVEAU(0): Modeline "1440x900"x40.2  101.60  1440 1488 1520 1824  900 910 920 1387 +hsync -vsync (55.7 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x60.0   81.75  1152 1216 1336 1520  864 867 871 897 -hsync +vsync (53.8 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) NOUVEAU(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) NOUVEAU(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) NOUVEAU(0): Modeline "720x400"x59.6   22.25  720 744 808 896  400 403 413 417 -hsync +vsync (24.8 kHz)
(II) NOUVEAU(0): Modeline "640x400"x60.0   20.00  640 664 720 800  400 403 409 417 -hsync +vsync (25.0 kHz)
(II) NOUVEAU(0): Modeline "640x350"x59.8   17.50  640 664 720 800  350 353 363 366 -hsync +vsync (21.9 kHz)[/HTML]Once logged in, the correct resolution is chosen. So the laptop screen is ok.

The external monitor doesn't work though. Here's the boot log:
[HTML](II) NOUVEAU(0): EDID for output DP-1
(II) NOUVEAU(0): Manufacturer: DEL  Model: a008  Serial#: 825439820
(II) NOUVEAU(0): Year: 2004  Week: 17
(II) NOUVEAU(0): EDID Version: 1.3
(II) NOUVEAU(0): Digital Display Input
(II) NOUVEAU(0): Max Image Size [cm]: horiz.: 41  vert.: 31
(II) NOUVEAU(0): Gamma: 2.20
(II) NOUVEAU(0): DPMS capabilities: StandBy Suspend Off
(II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NOUVEAU(0): Default color space is primary color space
(II) NOUVEAU(0): First detailed timing is preferred mode
(II) NOUVEAU(0): redX: 0.638 redY: 0.342   greenX: 0.293 greenY: 0.608
(II) NOUVEAU(0): blueX: 0.146 blueY: 0.067   whiteX: 0.312 whiteY: 0.328
(II) NOUVEAU(0): Supported established timings:
(II) NOUVEAU(0): 720x400@70Hz
(II) NOUVEAU(0): 640x480@60Hz
(II) NOUVEAU(0): 640x480@75Hz
(II) NOUVEAU(0): 800x600@60Hz
(II) NOUVEAU(0): 800x600@75Hz
(II) NOUVEAU(0): 1024x768@60Hz
(II) NOUVEAU(0): 1024x768@75Hz
(II) NOUVEAU(0): 1280x1024@75Hz
(II) NOUVEAU(0): Manufacturer's mask: 0
(II) NOUVEAU(0): Supported standard timings:
(II) NOUVEAU(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NOUVEAU(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) NOUVEAU(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NOUVEAU(0): Supported detailed timing:
(II) NOUVEAU(0): clock: 162.0 MHz   Image Size:  367 x 275 mm
(II) NOUVEAU(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
(II) NOUVEAU(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0
(II) NOUVEAU(0): Serial No: C088144N136L
(II) NOUVEAU(0): Monitor name: DELL 2001FP
(II) NOUVEAU(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 80 kHz, PixClock max 162 MHz
(II) NOUVEAU(0): EDID (in hex):
(II) NOUVEAU(0):        00ffffffffffff0010ac08a04c363331
(II) NOUVEAU(0):        110e010380291f78ee6390a3574b9b25
(II) NOUVEAU(0):        115054a54b008180a940714f01010101
(II) NOUVEAU(0):        010101010101483f403062b0324040c0
(II) NOUVEAU(0):        13006f131100001e000000ff00433038
(II) NOUVEAU(0):        383134344e3133364c20000000fc0044
(II) NOUVEAU(0):        454c4c203230303146500a20000000fd
(II) NOUVEAU(0):        00384c1f5010000a2020202020200082
(II) NOUVEAU(0): Printing probed modes for output DP-1
(II) NOUVEAU(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): EDID for output DP-2
(II) NOUVEAU(0): Output LVDS-1 connected
(II) NOUVEAU(0): Output VGA-1 disconnected
(II) NOUVEAU(0): Output DP-1 connected
(II) NOUVEAU(0): Output DP-2 disconnected
(II) NOUVEAU(0): Using fuzzy aspect match for initial modes
(II) NOUVEAU(0): Output LVDS-1 using initial mode 1152x864
(II) NOUVEAU(0): Output DP-1 using initial mode 1152x864[/HTML]So, at boot nothing appears on the monitor. However xrandr _can_ see it:
[HTML]gravelld@gravelld-laptop:~$ xrandr -q
Screen 0: minimum 320 x 200, current 3040 x 1200, maximum 8192 x 8192
LVDS-1 connected 1440x900+0+300 (normal left inverted right x axis y axis) 304mm x 190mm
   1440x900       60.2*+   40.2  
   1152x864       60.0  
   1024x768       59.9  
   800x600        59.9  
   640x480        59.4  
   720x400        59.6  
   640x400        60.0  
   640x350        59.8  
VGA-1 disconnected (normal left inverted right x axis y axis)
DP-1 connected 1600x1200+1440+0 (normal left inverted right x axis y axis) 367mm x 275mm
   1600x1200      60.0*+
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
DP-2 disconnected (normal left inverted right x axis y axis)[/HTML]As you can see, I have tried to turn on the monitor using the xrandr command line, but it's not showing anything. The monitor is blank. It looks like the virtual screen is correctly configured (the mouse pointer disappears when I move it to where the monitor 'is').

I'm not using xorg.conf. I tried a minimal file but it made no difference.

Any help would be gratefully received.

EDIT: I've noticed this works with VGA. Here's my xorg log:

[HTML](II) NOUVEAU(0): EDID for output VGA-1
(II) NOUVEAU(0): Manufacturer: DEL  Model: a007  Serial#: 825439820
(II) NOUVEAU(0): Year: 2004  Week: 17
(II) NOUVEAU(0): EDID Version: 1.3
(II) NOUVEAU(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) NOUVEAU(0): Sync:  Separate  Composite  SyncOnGreen
(II) NOUVEAU(0): Max Image Size [cm]: horiz.: 41  vert.: 31
(II) NOUVEAU(0): Gamma: 2.20
(II) NOUVEAU(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NOUVEAU(0): Default color space is primary color space
(II) NOUVEAU(0): First detailed timing is preferred mode
(II) NOUVEAU(0): redX: 0.638 redY: 0.342   greenX: 0.293 greenY: 0.608
(II) NOUVEAU(0): blueX: 0.146 blueY: 0.067   whiteX: 0.312 whiteY: 0.328
(II) NOUVEAU(0): Supported established timings:
(II) NOUVEAU(0): 720x400@70Hz
(II) NOUVEAU(0): 640x480@60Hz
(II) NOUVEAU(0): 640x480@75Hz
(II) NOUVEAU(0): 800x600@60Hz
(II) NOUVEAU(0): 800x600@75Hz
(II) NOUVEAU(0): 1024x768@60Hz
(II) NOUVEAU(0): 1024x768@75Hz
(II) NOUVEAU(0): 1280x1024@75Hz
(II) NOUVEAU(0): Manufacturer's mask: 0
(II) NOUVEAU(0): Supported standard timings:
(II) NOUVEAU(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NOUVEAU(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) NOUVEAU(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NOUVEAU(0): Supported detailed timing:
(II) NOUVEAU(0): clock: 162.0 MHz   Image Size:  367 x 275 mm
(II) NOUVEAU(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
(II) NOUVEAU(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0
(II) NOUVEAU(0): Serial No: C088144N136L
(II) NOUVEAU(0): Monitor name: DELL 2001FP
(II) NOUVEAU(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 80 kHz, PixClock max 162 MHz
(II) NOUVEAU(0): EDID (in hex):
(II) NOUVEAU(0):        00ffffffffffff0010ac07a04c363331
(II) NOUVEAU(0):        110e01030e291f78ee6390a3574b9b25
(II) NOUVEAU(0):        115054a54b008180a940714f01010101
(II) NOUVEAU(0):        010101010101483f403062b0324040c0
(II) NOUVEAU(0):        13006f131100001e000000ff00433038
(II) NOUVEAU(0):        383134344e3133364c20000000fc0044
(II) NOUVEAU(0):        454c4c203230303146500a20000000fd
(II) NOUVEAU(0):        00384c1f5010000a20202020202000f5
(II) NOUVEAU(0): Printing probed modes for output VGA-1
(II) NOUVEAU(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): EDID for output DP-1
(II) NOUVEAU(0): EDID for output DP-2
(II) NOUVEAU(0): Output LVDS-1 connected
(II) NOUVEAU(0): Output VGA-1 connected
(II) NOUVEAU(0): Output DP-1 disconnected
(II) NOUVEAU(0): Output DP-2 disconnected[/HTML]
[HTML]gravelld@gravelld-laptop:~$ xrandr -q
Screen 0: minimum 320 x 200, current 3040 x 1596, maximum 8192 x 8192
LVDS-1 connected 1440x900+0+696 (normal left inverted right x axis y axis) 304mm x 190mm
   1440x900       60.2*+   40.2  
   1152x864       60.0  
   1024x768       59.9  
   800x600        59.9  
   640x480        59.4  
   720x400        59.6  
   640x400        60.0  
   640x350        59.8  
VGA-1 connected 1600x1200+1440+0 (normal left inverted right x axis y axis) 367mm x 275mm
   1600x1200      60.0*+
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)[/HTML]
I would obviously prefer DVI though, which is a lot sharper.

---

### Post by Dan Gravell on 2010-06-17
I think the following bug may be the cause: [https://bugs.freedesktop.org/show_bug.cgi?id=27905](https://bugs.freedesktop.org/show_bug.cgi?id=27905)

---

