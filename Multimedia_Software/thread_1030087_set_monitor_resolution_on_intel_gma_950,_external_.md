---
title: "set monitor resolution on intel gma 950, external lcd"
date: 2009-01-04
forum: Multimedia Software
---

### Post by discord on 2009-01-04
Hello,

I have a panasonic cf-y5 laptop with the intel gma 950 chipset inside. The laptop lcd has a 4:3 ratio with a 1400x1050 resolution. I want to connect my 22" acer with a resolution of 1680x1050. However I do not find that resolution available for selection for my monitor.

```
 sudo xrandr -q
[sudo] password for discord: 
Screen 0: minimum 320 x 200, current 1152 x 864, maximum 1400 x 1400
VGA connected 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0* 
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
LVDS connected 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1400x1050      60.0 +   85.0     74.8     70.0     60.0  
   1280x1024      85.0     75.0     60.0  
   1280x960       85.0     60.0  
   1360x768       59.8  
   1152x864      100.0     85.1     85.0     75.0     75.0     70.0     60.0* 
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  

```

Can anybody help me to set my external monitor resolution?

---

### Post by densou on 2009-01-05
you must add on xrandr that resolution .... errrr, I don't remember how to do it. 

(read guides) [http://www.x.org/wiki/Projects/XRandR](http://www.x.org/wiki/Projects/XRandR)

or if you look to my old posts you could find a thread where it is described that 'how to' (not posted by me anyway)

---

### Post by discord on 2009-01-06
Hey that looks like what I needed, thanks!

---

### Post by densou on 2009-01-12
whoops, I forgot to paste this in addiction:
[http://www.intellinuxgraphics.org/dualhead.html](http://www.intellinuxgraphics.org/dualhead.html)
(could be useful for managing both laptop screen and the external one)

farewell ):P

---

