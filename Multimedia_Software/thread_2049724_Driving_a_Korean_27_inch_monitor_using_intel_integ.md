---
title: "Driving a Korean 27 inch monitor using intel integrated graphics on a laptop"
date: 2012-08-29
forum: Multimedia Software
---

### Post by Malfernion on 2012-08-29
Hi,

I've recently purchased a First FSM-270YG 27 inch monitor from ebay, and have been having troubles gettint it to play nicely as a second monitor for my Toshiba portege R830-13C.

When starting the laptop with the monitor plugged in (using an dvi-d to hdmi cable), the second monitor isn't used. I managed to use xrandr to get it to display a strange tiled view which seems to be 4 views at the same size as my laptops 1366x768 monitor using the following modeline:

xrandr --newmode "2560x1440_60.0"  311.83  2560 2744 3024 3488  1440 1441 1444 1490  -HSync +Vsync

xrandr --addmode HDMI1 2560x1440_60.0

which gives the view shown in the image, that makes no sense to me...

I have seen the luck people have had on this forum using twinview with Nvidia cards (
[http://ubuntuforums.org/showthread.php?p=12159781](http://ubuntuforums.org/showthread.php?p=12159781)), but haven't seen somebody get it working in this configuration yet.
For fun, I have attached the output from xrandr --verbose.

Any help anyone can give me in getting the monitor working properly/understanding this problem would be really appreciated!

---

### Post by Malfernion on 2012-08-30
(bump)

Had more of a play, looking at using edid-rw and parse-edid for the monitor in question, and it looks like it's reporting the correct mode. 

Maybe the fact that I'm using a dvi-d to hdmi cable means nouveau isn't reading the edid correctly, but I can't see why, when I give xrandr the correct modes it does that weird tiling thing shown in the picture in the last post..

any ideas?

EDIT: Also, here is the hopefully relevant part of my /var/log/Xorg.0.log file, if that helps


[    26.744] (II) intel(0): Output LVDS1 has no monitor section
[    26.744] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    26.744] (II) intel(0): Output VGA1 has no monitor section
[    27.922] (II) intel(0): Output HDMI1 has no monitor section
[    27.968] (II) intel(0): Output DP1 has no monitor section
[    27.972] (II) intel(0): Output HDMI2 has no monitor section
[    27.977] (II) intel(0): Output HDMI3 has no monitor section
[    28.024] (II) intel(0): Output DP2 has no monitor section
[    28.072] (II) intel(0): Output DP3 has no monitor section
[    28.072] (II) intel(0): EDID for output LVDS1
[    28.072] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    28.072] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    28.072] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    28.072] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    28.072] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    28.072] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    28.072] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    28.072] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    28.072] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    28.072] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    28.072] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    28.072] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    28.072] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    28.072] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    28.072] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    28.072] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    28.072] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    28.072] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    28.072] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    28.072] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    28.072] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    28.072] (II) intel(0): Printing probed modes for output LVDS1
[    28.072] (II) intel(0): Modeline "1366x768"x60.2   77.00  1366 1401 1513 1641  768 769 771 780 -hsync -vsync (46.9 kHz)
[    28.072] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    28.072] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[    28.072] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    28.072] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    28.072] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    28.072] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    28.072] (II) intel(0): EDID for output VGA1
[    29.237] (II) intel(0): EDID for output HDMI1
[    29.237] (II) intel(0): Manufacturer: HYO  Model: 49b  Serial#: 0
[    29.237] (II) intel(0): Year: 2011  Week: 40
[    29.237] (II) intel(0): EDID Version: 1.3
[    29.237] (II) intel(0): Digital Display Input
[    29.237] (II) intel(0): DFP 1.x compatible TMDS
[    29.237] (II) intel(0): Max Image Size [cm]: horiz.: 60  vert.: 34
[    29.237] (II) intel(0): Gamma: 2.20
[    29.237] (II) intel(0): DPMS capabilities: Off
[    29.237] (II) intel(0): Supported color encodings: RGB 4:4:4 
[    29.237] (II) intel(0): First detailed timing is preferred mode
[    29.237] (II) intel(0): redX: 0.653 redY: 0.334   greenX: 0.300 greenY: 0.620
[    29.237] (II) intel(0): blueX: 0.146 blueY: 0.050   whiteX: 0.312 whiteY: 0.329
[    29.237] (II) intel(0): Manufacturer's mask: 0
[    29.237] (II) intel(0): Supported detailed timing:
[    29.237] (II) intel(0): clock: 241.5 MHz   Image Size:  597 x 336 mm
[    29.237] (II) intel(0): h_active: 2560  h_sync: 2608  h_sync_end 2640 h_blank_end 2720 h_border: 0
[    29.237] (II) intel(0): v_active: 1440  v_sync: 1443  v_sync_end 1448 v_blanking: 1481 v_border: 0
[    29.237] (II) intel(0): Monitor name: FS-270D
[    29.237] (II) intel(0): Monitor name: 
[    29.237] (II) intel(0): Monitor name: 
[    29.237] (II) intel(0): EDID (in hex):
[    29.237] (II) intel(0):     00ffffffffffff00232f9b0400000000
[    29.237] (II) intel(0):     28150103a53c2278226fb1a7554c9e25
[    29.237] (II) intel(0):     0c505400000001010101010101010101
[    29.237] (II) intel(0):     010101010101565e00a0a0a029503020
[    29.237] (II) intel(0):     350055502100001a000000fc0046532d
[    29.237] (II) intel(0):     323730440a2020202020000000fc000a
[    29.237] (II) intel(0):     202020202020202020202020000000fc
[    29.237] (II) intel(0):     000a2020202020202020202020200085
[    29.237] (II) intel(0): No remaining probed modes for output HDMI1
[    29.284] (II) intel(0): EDID for output DP1
[    29.288] (II) intel(0): EDID for output HDMI2
[    29.293] (II) intel(0): EDID for output HDMI3
[    29.340] (II) intel(0): EDID for output DP2
[    29.388] (II) intel(0): EDID for output DP3
[    29.388] (II) intel(0): Output LVDS1 connected
[    29.388] (II) intel(0): Output VGA1 disconnected
[    29.388] (II) intel(0): Output HDMI1 connected
[    29.388] (II) intel(0): Output DP1 disconnected
[    29.388] (II) intel(0): Output HDMI2 disconnected
[    29.388] (II) intel(0): Output HDMI3 disconnected
[    29.388] (II) intel(0): Output DP2 disconnected
[    29.388] (II) intel(0): Output DP3 disconnected
[    29.388] (II) intel(0): Using sloppy heuristic for initial modes
[    29.388] (II) intel(0): Output LVDS1 using initial mode 1366x768
[    29.388] (EE) intel(0): Output HDMI1 enabled but has no modes
[    29.388] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.

---

