---
title: "Touchscreen support not intuative"
date: 2010-07-15
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by macroshaft on 2010-07-15
Finally after what seems like an eternity of waiting my HP TX1000 works out of the box. Previously it has taken days of banging my head against a wall to get touch screen working, even then it was a bit iffy and sometimes would stop working so wasn't really worth the effort and I just left it.

However I was very pleased to notice that Lucid reacts to touch with no fiddling about required. Unfortunately wherever you touch the cursor jumps to the top left corner and clicks so it's useless. I can see this is a known fault and didn't seem to be able to get around it without bogging myself down with compiling code and following guides so out of curiosity I upgraded to Maverick just to see if the latest kernel has been fixed in this respect, it has! Now I have a fully functioning touchscreen but the calibration is poor, it works in the centre of the screen but by the time you reach the edge the cursor lags behind, making it impossible to use the scrollbar or panels.

My problem is that to all intents and purposes there appears to be no calibrate tool. I'm sure it's there but there is nothing to tell me what it's called or where to find it so for average Joe user that's a huge stumbling block. Can anyone tell me is there a plan in motion to either make the calibration unnecessary or make the tool easy to locate? Also anyone who can advise how to do the calibration would make me very happy! :p

---

### Post by 4leite on 2010-07-16
bump

also interested in how to calibrate.

Cheers

---

### Post by Favux on 2010-07-18
Usually Xorg.0.log in /var/log has generic coordinates when the driver, evtouch or eGalax?, initiates the touchscreen.  You could try [xinput calibrator]("http://www.freedesktop.org/wiki/Software/xinput_calibrator").

---

