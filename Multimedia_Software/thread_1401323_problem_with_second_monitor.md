---
title: "problem with second monitor"
date: 2010-02-07
forum: Multimedia Software
---

### Post by neiljansons on 2010-02-07
I have been running ubuntu 9.10 on my Dell inspiron 6400 for a short while not without some issues but generally working quite well.

I had a second monitor set up as an extended desktop and that seemed to work well. The second monitor has a different resolution to the notebook monitor but that was not a problem. I had it positioned above the notebook monitor.

When the second monitor was unplugged everything also worked fine and the display reverted back to the single screen (rather than an extended desktop).

The first problem came one time when I plugged in the external monitor with the notebook still running. Well actually the problem wasn't at the point I plugged it in but rather when I went to System | Preferences | Display and activated the second monitor. Both monitors went black and the spinning clock could be seen half on each black screen but the computer was frozen and had to be cold booted.

I tried playing around with various scenarios in the display configuration but it is now to the point where the only way I can activate the second monitor is if the two monitors are mirrored (and of course running the same resolution). Mirroring the displays is of no value to me.

BTW if the second monitor is plugged in when I boot the laptop both screens display the ubuntu logo during the boot.

I also tried plugging in a different external monitor with the same results. I also want to be able to use a data projector with the laptop. I presume the results will be the same although I haven't been able to test that out.

output from xrandr without an external screen plugged in:
(LVDS1 is the laptop screen, VGA1 is a 17" IBM screen, TV1 is a widescreen 19" screen.)

> Screen 0: minimum 320 x 200, current 1280 x 800, maximum 4096 x 4096
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TV1 disconnected (normal left inverted right x axis y axis)

If I boot the laptop with a second monitor connected I get this:
(if I plug in a second monitor while the notebook is running and execute xrandr it will go to a black screen and freeze - the only thing visible is a frozen mouse pointer)

> Screen 0: minimum 320 x 200, current 1280 x 800, maximum 4096 x 4096
VGA1 connected (normal left inverted right x axis y axis)
   1280x1024      75.0 +
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TV1 disconnected (normal left inverted right x axis y axis)

I have no idea where to go from here

Thanks

---

