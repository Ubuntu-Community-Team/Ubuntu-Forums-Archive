---
title: "Horizontal lines on monitor"
date: 2008-11-17
forum: Multimedia Software
---

### Post by swr12 on 2008-11-17
Hello,

I need a little help solving a problem. When I launch an application that uses 3d rendering the program runs but anything 3d rendered is not displayed and their are lines across the bottom of the screen. It is really odd I have not been able to find anything on the forums like this. I have intel integrated graphics (i810e) and an compaq mv740 monitor. also the highest resolution my monitor can reach is 1152x864. My monitor is supposedly capable of reaching 1280x1024. I have linked a screen shot for those interested in seeing this. If you stare at the lines long enough you can kind of make out what is suppose to be being rendered. Their is nothing wrong at all with 2d graphics, just really messed up 3d graphics.

Any help is welcomed.

---

### Post by cariboo on 2008-11-17
Check that you have the proper horizintal and vertical refresh rates set in /etc/X11/xorg.conf.

Have a look here for the proper rates:

[http://www.monitorworld.com/Monitors/compaq/mv740.html](http://www.monitorworld.com/Monitors/compaq/mv740.html)

Another thing you may want to do is give the monitor a firm slap on the side to see if the problem disappears. It looks like you may have a problem with cold solder joints.

Jim

---

### Post by swr12 on 2008-11-17
The horizontal and vertical refresh rates are not being set from the xorg.conf file. They are being detected I assume. I looked in the xorg.o.log file and found that x.org is using HorizSync 31-70 and VerteRefresh 50-120. That is roughly what the website said that they should be.

Here are the lines in the xorg.0.log file:
```
(II) intel(0): Configured Monitor: Using hsync range of 31.00-70.00 kHz
(II) intel(0): Configured Monitor: Using vrefresh range of 50.00-120.00 Hz
```

Unfortunately the wack in the side didn't work either.

---

