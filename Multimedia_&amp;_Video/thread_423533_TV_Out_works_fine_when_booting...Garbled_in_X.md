---
title: "TV Out works fine when booting...Garbled in X"
date: 2007-04-25
forum: Multimedia &amp; Video
---

### Post by atomicfire on 2007-04-25
So when the system is booting, the display looks fantastic on the TV. I can see the bios, I can read all the text, I can see Ubuntu booting. However, as soon as X loads, the display goes nuts. I've tried using 800x600 only, 60Hz refresh rate only, etc etc...only to get a garbeled output.

Out of interest, what display mode is Ubuntu using in console? Maybe if I can set that as the default, the display will work correctly.

Any help apprecieated!

---

### Post by josesanders on 2007-04-26
What kind of video card are you using?

Where do you live?  A garbled TV output might mean that you are using the wrong mode.  If you are in North America, you need NTSC, while in other places you may need PAL.  You can set that in your xorg.conf.

---

