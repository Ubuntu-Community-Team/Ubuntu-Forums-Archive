---
title: "Ack, I broke my video driver!  Can Gutsy re-detect?"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by bieber on 2007-10-21
I just upgraded to Gutsy, and it detected my video card and driver perfectly, got everything running, etc.  So, being a little too curious, I decided to try the "Open Source Driver" out, and see how it was working, but it turns out I just broke it.  Now I get the "Ubuntu is in low video mode" dialog every time I boot up, and for some reason just selecting the fglrx driver (which I was using before) from the Screens and Graphics window won't fix the problem.  Is there some way to just have Gutsy re-do the initial autodetection it did when I installed in the first place?

---

### Post by napsilan on 2007-10-21
try

sudo dpkg-reconfigure xserver-xorg

---

