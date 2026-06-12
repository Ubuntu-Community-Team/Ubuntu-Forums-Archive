---
title: "Dell 700M and Gutsy: Xinerama possible?"
date: 2007-11-07
forum: Multimedia &amp; Video
---

### Post by Oreo on 2007-11-07
I am repeating this thread from Installation and Upgrades, hoping someone here in the Multimedia and Video section will answer!

Does anyone using Gutsy with a Dell 700m laptop have xinerama working on a second monitor? If so please send me your xorg.conf!

I can get Xinerama working if I use the i810 driver and define the 700m display as a plug and play monitor (making that setting using Administration > Screens and Graphics). But I haven't found a setting that will allow the 700m screen to run with its best 1280 by 800 resolution. Also in this mode, it starts out looking fine, but eventually part of my laptop desktop stops being usable (no icons, not able to move windows there).

Or if I delete my xorg.conf and start over, the default xorg.conf that is created makes a good clone monitor setup, and graphics work better. But I fail in getting this changed into a Xinerama setup.

I have tried making a large Virtual screen in the xorg.conf, such as
Virtual 2048 2048
and to use xrandr.
I can't figure out how to use information gleaned with xrander to get xinerama to work. It looks like from the message boards that I do this using Screens and Graphics again.

BUT if I start the Screens and Graphics program after this, it zaps any somewhat-working xorg.conf, and what replaces it often won't work. The replaced xorg.conf also doesn't retain the virtual setting 2048x2048.

Also the message boards mention using the older i810 driver rather than the new intel driver. I assume this means that the i810 driver in Gutsy is still the old one, right?

Thanks for your help!

---

### Post by Oreo on 2007-11-11
See my answer at:

[http://ubuntuforums.org/showthread.php?p=3753963#post3753963](http://ubuntuforums.org/showthread.php?p=3753963#post3753963)

---

