---
title: "Rescaling Volume, fixing sliders?"
date: 2012-01-28
forum: Multimedia Software
---

### Post by Sir G on 2012-01-28
Hi, 

I just got an old Trust surround USB Headset to work on Ubuntu 11.10.
However, the volume controls are bugged. Touching a slider in the taskbar or banshee in any way (even sliding it to the lower end) would set the volume to about 5000%. This usually causes me to jank the headset right off my head.

There is no gradient whatsoever in the slider. There are three volume it can serve.
One: no sound (this takes up the largest part of the slider)
Two: a one pixel wide region of a bearable volume
Three: nuclear blast

After messing around for some time I found that I can control the volume correctly using the command :

amixer -c 1 set Speaker X%.

acceptable volumes are within the 0 - 10% region of the control.

So my question is: is there any way that I can fix these volume sliders in the taskbar, banshee... to control that particular amixer setting, and make it so that the slider varies between 0% to about 15%?

Thanks

---

