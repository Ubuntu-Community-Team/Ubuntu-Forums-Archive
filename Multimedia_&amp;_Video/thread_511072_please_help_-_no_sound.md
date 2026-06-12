---
title: "please help - no sound"
date: 2007-07-27
forum: Multimedia &amp; Video
---

### Post by abadfish on 2007-07-27
some background:
- computer:  Dell Latitude D830 laptop
- kernel: 2.6.22-8

I was loading a video file.  A window popped-up saying I needed some codecs.  The media player went to the internet to find them, asked me to install them, I complied.  Now I don't have sound.  When I try to adjust the volume, a window pops up saying Gstream coudn't find a device or I have the wrong Gstream.

Sound was working before this, how do I undo this and get back to my original state???  Or how can I fix the current state??

Thanks.

---

### Post by Total_Biscuit on 2007-07-28
With apologies to the fabulous Goodies:

> Do, do, do the Gutsy Gibbon
(The Gutsy Gibbon)
We are here to show you how
(Oo oo oo)
Oo oo oo, the Gutsy Gibbon
(The Gutsy Gibbon)
It's just like you,
So come on and do
The Gutsy Gibbon now.

If you're running a 2.6.22-8 kernel then my guess is that you must be using Gutsy.  You've possibly found a bug that needs to be reported to the developers before it gets released!

---

### Post by scholzilla on 2007-07-28
there seem to be a lot of sound-disabling bugs in ubuntu. It's my only complaint and one that never seems to get addressed despite many bug reports...

---

### Post by Total_Biscuit on 2007-07-30
> **scholzilla said:**
> there seem to be a lot of sound-disabling bugs in ubuntu. It's my only complaint and one that never seems to get addressed despite many bug reports...

Gstreamer could certainly do with a little improvement.  Usual trick is to completely uninstall then reinstall the gstreamer plugins, make a small offering to the gods of sound reproduction and high fidelity, and then reboot once (or twice if it doesn't work the first time).

---

