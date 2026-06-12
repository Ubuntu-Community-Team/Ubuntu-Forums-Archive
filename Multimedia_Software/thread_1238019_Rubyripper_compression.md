---
title: "Rubyripper compression?"
date: 2009-08-12
forum: Multimedia Software
---

### Post by Bartender on 2009-08-12
I'm on a mission to compress mp3's.  Read the Community Documentation, which said LAME was broken and suggested Rubyripper.  But Rubyripper uses LAME too.  RipperX, same thing.

I can rip mp3's several different ways now, but they're all huge files.

Where the heck are the settings for mp3 in Rubyripper?

---

### Post by mc4man on 2009-08-13
Lame isn't broken, possibly gstreamer apps using either libmp3lame or lame itself may be, but certainly not any third party app that uses lame.

Open rr and click on the codecs tab, the lame settings box is right there.
It probably defaults to V 3, the vbr quality numbers range from 0-9 with 0 the highest, 9 the lowest.

Experiment with ripping just one track and see what suits you best.

Any valid lame options can be used in the box, see lame --longhelp if desired.

---

### Post by Bartender on 2009-08-13
Thanks, mc4man.  I found those settings to which you refer, but I'm not familiar with them and didn't want to guess.  I'll go back and tweak a little bit now that you've pointed me in the right direction.

---

