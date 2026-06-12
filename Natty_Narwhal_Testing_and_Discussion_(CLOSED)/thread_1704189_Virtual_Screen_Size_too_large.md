---
title: "Virtual Screen Size too large"
date: 2011-03-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Gorlist on 2011-03-10
Hi, just installed 11.04 A3, for some reason my desktop is larger than the physical screen size (resolution is 1920 x 1200, running ATI HD4900), so at the moment the unity bar on the left, and top bar is just off the edge of the screen.

I assume its down to what use to be "virtual" setting in the xorg - Ive had the problem size 10.04, but after install the drivers it curred itself. 

Ive tried following this guide to modify xrandr by using the -fb command. No improvement. [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Help!

Best Regards,

---

### Post by dino99 on 2011-03-10
if xorg.conf exist, remove it

otherwise:

metacity --replace &
compiz --replace &

---

### Post by Gorlist on 2011-03-10
checked, no xorg. Ran the two commands and no improvement.

xrandr output.

```
james@James-Desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1200, maximum 8192 x 8192
HDMI-0 disconnected (normal left inverted right x axis y axis)
VGA-0 disconnected (normal left inverted right x axis y axis)
DIN disconnected (normal left inverted right x axis y axis)
DVI-0 connected 1920x1200+0+0 (normal left inverted right x axis y axis) 593mm x 371mm
   1920x1200      60.0*+
   1920x1080      50.0  
   1680x1050      60.0  
   1400x1050      60.0  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  

```

thanks,



**Solved, silly problem - all I had todo was reset the HDMI on my monitor!**

---

