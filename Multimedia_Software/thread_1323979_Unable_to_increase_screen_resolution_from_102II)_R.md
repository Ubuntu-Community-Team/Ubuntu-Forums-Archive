---
title: "Unable to increase screen resolution from 102II) RADEON(0)4*768 on Ubuntu 9.10 karmic"
date: 2009-11-12
forum: Multimedia Software
---

### Post by srikumar.b on 2009-11-12
Hi,
I have installed Ubuntu 9.10 karmic on IBM R50 thinkpad. I am not able to changes the resolution of the screen from 1024*768. I looked into to lot of posts of similar issue but nothing worked for me....

Below are VGA details:
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]

As suggested in [http://www.lucidtips.com/2008/05/24/fix-screen-resolution-in-ubuntu-with-ati-radeon-mobility-7500/comment-page-1/#comment-982](http://www.lucidtips.com/2008/05/24/fix-screen-resolution-in-ubuntu-with-ati-radeon-mobility-7500/comment-page-1/#comment-982) i tried to change ht xorg.conf file but the file is not available in 9.10. So, i generated the file using Xorg -configure and added the line 
Option        "NoDDC"           "true"

and restarted the X server. But no use.....I am still not able to see the options.

I still feel that X server is tring with DDC with reference the below logs observed in xorg.conf.0.log



II) RADEON(0): Port0:
  XRANDR name: VGA-0
  Connector: VGA
  CRT1: INTERNAL_DAC1
  DDC reg: 0×60
(II) RADEON(0): Port1:
  XRANDR name: DVI-0
  Connector: DVI-D
  DFP1: INTERNAL_TMDS1
  DDC reg: 0×64
(II) RADEON(0): Port2:
  XRANDR name: LVDS
  Connector: LVDS
  LCD1: INTERNAL_LVDS
  DDC reg: 0×0
(II) RADEON(0): Port3:
  XRANDR name: S-video
  Connector: S-video
  TV1: INTERNAL_DAC2
  DDC reg: 0×0
(II) RADEON(0): I2C device “VGA-0:E-EDID segment register” registered at address 0×60.
(II) RADEON(0): I2C device “VGA-0:ddc2&#8243; registered at address 0xA0.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
finished output detect: 0
(II) RADEON(0): I2C device “DVI-0:E-EDID segment register” registered at address 0×60.
(II) RADEON(0): I2C device “DVI-0:ddc2&#8243; registered at address 0xA0.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
finished output detect: 1
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
finished output detect: 2


Please find the attached xorg.conf & log files and kindly suggest the solution...


thanks in advance...

---sri

---

### Post by Wahngrok on 2009-11-12
Can't look into much detail as I'm in a hurry but you could look into using xrandr.

To query your available modes start with
```
xrandr -q
```

Then you can switch modes using
```
xrandr --output {DisplayAdapterName} --mode {ModeName}
```

For further info I suggest this [link]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2"). It's for xrandr version 1.2 (instead of the 1.3 in Karmic) but it's probably a good start.

---

### Post by srikumar.b on 2009-11-13
My xrandr version is 1.3 and below is the output of command exection


$ xrandr -q
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1024 x 1024
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+   60.0  
   800x600        60.3     59.9  
   640x480        59.9     59.4  

$ xrandr --output LVDS --mode 1280x1024
xrandr: cannot find mode 1280x1024

Please help me how to set the new resolution!!

--sri

---

### Post by Wahngrok on 2009-11-13
You need to setup your new mode with xrandr first.
You can use the tool cvt to get the right syntax. As an example I use the mode 1280x1200@60Hz.
```
cvt 1280 1200 60
```
gives the output
> # 1280x1200 59.85 Hz (CVT) hsync: 74.51 kHz; pclk: 128.75 MHz
Modeline "1280x1200_60.00"  128.75  1280 1368 1504 1728  1200 1203 1213 1245 -hsync +vsync
Use the Modeline output as input for the xrandr like so
```
xrandr --newmode "1280x1200_60.00"  128.75  1280 1368 1504 1728  1200 1203 1213 1245 -hsync +vsync
```
Now you need to attach the mode to your output device
```
xrandr --addmode LVDS 1280x1200_60.00
```
A xrandr query should confirm that your new mode has been added. So finally you can activate the mode with
```
xrandr --output LVDS --mode 1280x1024_60.00
```

HTH

edit: I see you'll run into another problem: Your maximum (virtual) screen size is 1024x1024 (as can bee seen in your xrandr -q output:
> Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1024 x 1024
You need to increase this with help of the **virtual** line in the xorg.conf as specified in the link I provided in my last post.

---

### Post by srikumar.b on 2009-11-16
I am not able to add the mode....Below is the error message  when i try to add it....

$ xrandr --addmode LVDS 1280x1200_60.00
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  27
  Current serial number in output stream:  28


And, How do i edit the xorg.conf in Ubuntu Karmic as this file itself is not available......

Please help me in this....

---

### Post by wolfsong on 2009-11-24
> **srikumar.b said:**
> I am not able to add the mode....Below is the error message  when i try to add it....

$ xrandr --addmode LVDS 1280x1200_60.00
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  27
  Current serial number in output stream:  28


I'm getting the same error. Can't seem to find any solution for this.

---

