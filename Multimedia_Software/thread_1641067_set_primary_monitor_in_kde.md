---
title: "set primary monitor in kde"
date: 2010-12-08
forum: Multimedia Software
---

### Post by davidtuti on 2010-12-08
Hi,
I have Kubuntu and I have a monitor and a TV LCD connected in format extended.
I'm trying to change the primary monitor but it seems that the command doesn't do nothing.
Could you help me please?
Many thanks and sorry for my english!

```

xrandr
Screen 0: minimum 320 x 200, current 2464 x 900, maximum 2464 x 1776
DFP1 connected 1024x768+1440+0 (normal left inverted right x axis y axis) 160mm x 90mm
   1024x768       60.0*+
   1776x1000      50.0     59.9     25.0     25.0     24.0     30.0     30.0  
   1280x720       60.0  
   1152x648       50.0     59.9  
   800x600        60.0  
   720x480        60.0  
   640x480        60.0  
DFP2 connected 1440x900+0+0 (normal left inverted right x axis y axis) 408mm x 255mm
   1440x900       59.9*+
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1280x800       60.0  
   1152x864       75.0  
   1280x768       60.0  
   1280x720       60.0  
   1024x768       75.0     70.1     60.0  
   800x600        75.0     60.3     56.2  
   640x480        75.0     59.9  
CRT1 disconnected (normal left inverted right x axis y axis)
CRT2 disconnected (normal left inverted right x axis y axis)
  

xrandr --output DFP1 --primary


```

---

