---
title: "Ubuntu 9.10, dual display, different resolutions"
date: 2010-02-27
forum: Multimedia Software
---

### Post by diab0lik on 2010-02-27
Hey all.

I have an ATI X850XT PE and 2 Dell screens: a 2405FPW and a 2005FPW. A 1920x1200 res for the first and a 1680x1050 for the 2nd.

I want to run both screens side by side and use the max res for both. I don't seem to be able to do that though. When I look at Xorg.0.log I get this: Note the height too large message.

(II) RADEON(0): Monitor name: DELL 2405FPW
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 81 kHz, PixClo$
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):         00ffffffffffff0010ac10a053364130
(II) RADEON(0):         220f010380342178eeee50a3544c9b26
(II) RADEON(0):         0f5054a54b008180a940714fb3000101
(II) RADEON(0):         010101010101283c80a070b023403020
(II) RADEON(0):         360007442100001a000000ff00543631
(II) RADEON(0):         33333538473041365320000000fc0044
(II) RADEON(0):         454c4c20323430354650570a000000fd
(II) RADEON(0):         00384c1e5111000a202020202020001b
(II) RADEON(0): Panel infos found from DDC detailed: 1920x1200
(II) RADEON(0): EDID vendor "DEL", prod id 40976
(II) RADEON(0): Not using mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output DVI-1
(II) RADEON(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)


And so forth.

If I change my xorg.conf my screen takes a poop and I have to revert. As it is my xorg.conf is basically empty:

Section "Screen"
    Identifier    "Configured Screen Device"
    Device    "Configured Video Device"
    SubSection "Display"
        Virtual    3360 1050
    EndSubSection
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection

And the output from xrandr

Screen 0: minimum 320 x 200, current 3360 x 1050, maximum 3360 x 1050
DVI-1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 519mm x 324mm
   1680x1050      59.9* 
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
   720x400        70.1  
DVI-0 connected 1680x1050+1680+0 (normal left inverted right x axis y axis) 434mm x 270mm
   1680x1050      59.9*+
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
   720x400        70.1  


Has anyone with a similar setup been able to get this working?

Thanks

---

