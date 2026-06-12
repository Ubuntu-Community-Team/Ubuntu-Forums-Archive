---
title: "Cannot set 1680*1050 on external monitor"
date: 2009-09-14
forum: Multimedia Software
---

### Post by zorofroozo on 2009-09-14
Hello, I'm trying to get my acer aspire one and my samsung 22' screen to work together. But I can't seem to get the native resolution to run. I tried with xrandr, but it always errors out

first i looked if the resolution was supported by issuing```
xrandr
``` in terminal, i got the folowing output: ```
Screen 0: minimum 320 x 200, current 800 x 600, maximum 1360 x 1360
VGA connected 800x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3* 
   640x480        59.9  
LVDS connected 800x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x600       60.0 +
   800x600        85.1     72.2     75.0     60.3*    56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1 
```

so, 1680*1050 was not there, so I tried adding a new displat resolution like this:
```
zorofroozo@Zorofroozo-nettop:~$ gtf 1680 1050 60
  # 1680x1050 @ 60.00 Hz (GTF) hsync: 65.22 kHz; pclk: 147.14 MHz
  Modeline "1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync

```
now i had all the needed information so i fed it to xrandr,
```
xrandr --newmode "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
```
but that didn't work at all, it just showed an error
```
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  16 ()
  Serial number of failed request:  23
  Current serial number in output stream:  23
```

i tried googling the error, and parts of the error, but i failed to get any solution. I really hope you guys can help me. 800*600 on a 22' isn't really nice to look at

---

### Post by tgalati4 on 2009-09-14
What type of graphics chip is on the Acer?  If it's Intel, it probably can't support the horizontal refresh required to paint 1680 pixels.  

xrandr says 1360x1360 max which implies that it can only go to 1360 pixels horizontally.

What does the following say:

cat /var/log/Xorg.0.log

---

### Post by zorofroozo on 2009-09-14
I got it working.

```
xrandr --fb 1680x1050 --output VGA --mode 1680x1050 --output LVDS --mode 1024x600 --panning 1680x1050+0+0
``` did the trick

thx for your help

---

