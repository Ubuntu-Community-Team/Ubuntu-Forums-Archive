---
title: "xrandr won't resize resolution from 1024x768"
date: 2009-06-17
forum: Multimedia Software
---

### Post by bastones on 2009-06-17
Hi,

I want to resize the screen resolution to 1280x800 - at the moment its on 1024x768 which is too small for me to use Linux Mint on a full time basis. I typed xrandr to see types of resolutions that are available for me - and here's response:

> Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1360 x 1360
VGA connected 1024x768+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0 +
   1024x768       60.0* 
   1024x640       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
TMDS-1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0* 
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right x axis y axis)
  1280x800_60.00 (0xc2)   83.5MHz
        h: width  1280 start 1352 end 1480 total 1680 skew    0 clock   49.7KHz
        v: height  800 start  803 end  809 total  831           clock   59.8Hz
  1280x768_60.00 (0xc3)   79.5MHz
        h: width  1280 start 1344 end 1472 total 1664 skew    0 clock   47.8KHz
        v: height  768 start  771 end  781 total  798           clock   59.9Hz


so, I did: xrandr --output LVDS --mode 1280x800

and, it flickered once seemed like it was adjusting the resolution, but it still seems like 1024x768 resolution. So I entered xrandr to confirm, and regardless how many times I try changing resolution using above command, it still shows: "current 1024 x 768"

am I doing something wrong?

Before this I tried cvt 1280 800 then xrandr --addmode, flickered once as usual to no change.

Any help appreciated.

---

### Post by Yellow Pasque on 2009-06-17
Maybe some helpful error messages will be found in /var/log/Xorg.0.log or ~/.xsession-errors

---

### Post by bastones on 2009-06-17
> **Temüjin said:**
> Maybe some helpful error messages will be found in /var/log/Xorg.0.log or ~/.xsession-errors

the latest at bottom of Xorg.0.log is:

> (II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): EDID vendor "@@@", prod id 0
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.90  1280 1301 1333 1408  800 804 808 816 -hsync -vsync (48.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x640"x60.0   52.83  1024 1072 1176 1328  640 641 644 663 -hsync +vsync (39.8 kHz)
(II) intel(0): EDID vendor "@@@", prod id 0

---

### Post by planetLars on 2009-06-17
your displays are called VGA, TMDS-1 and TV, not LVDS as it is for me. Does xrandr --output VGA --mode 1280x800 help? If not, perhaps the added mode is incorrect. Did --addmode give an error? If not everything should work probably, else you have to create a --newmode before (type xrandr -h to get the syntax, cvt then provides the data for hsync etc.).

Lars

---

### Post by bastones on 2009-06-17
> **planetLars said:**
> your displays are called VGA, TMDS-1 and TV, not LVDS as it is for me. Does xrandr --output VGA --mode 1280x800 help? If not, perhaps the added mode is incorrect. Did --addmode give an error? If not everything should work probably, else you have to create a --newmode before (type xrandr -h to get the syntax, cvt then provides the data for hsync etc.).

Lars

ah, it worked, thanks! I did wonder about this before but didn't realise xrandr --output **LVDS** is a monitor name.

Thanks :).

---

