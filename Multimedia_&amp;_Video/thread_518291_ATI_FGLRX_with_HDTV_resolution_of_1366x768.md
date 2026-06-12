---
title: "ATI FGLRX with HDTV resolution of 1366x768"
date: 2007-08-05
forum: Multimedia &amp; Video
---

### Post by gspr on 2007-08-05
Hi.

I have a Radeon 9700 (using the proprietary ATI drivers) connected via a DVI-HDMI cable to a Tatung 32" TV with a native resolution of 1366x768 @ 60 Hz. I've tried putting the res. and refresh rate into the common modeline calculator, but no luck. A resolution of 640x480 works if it's the only one specified.

I see a lot of people have got their TVs working after a lot of fiddling with modelines. Any good ideas? Can the ATI drivers be told to ignore EDID info, like nvidia's?

---

### Post by gspr on 2007-08-09
After finding the right page in the TV's manual (not the page called specifications, but the one before... d'oh), [http://www.tkk.fi/Misc/Electronics/faq/vga2rgb/calc.html](http://www.tkk.fi/Misc/Electronics/faq/vga2rgb/calc.html) generated a modeline that gave me the full 1360x768 resolution.

With the ATI I suffered an incorrectable screen offset, so I went back to using an older nvidia card, and things are working great.

---

