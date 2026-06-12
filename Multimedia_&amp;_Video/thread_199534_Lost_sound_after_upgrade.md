---
title: "Lost sound after upgrade"
date: 2006-06-18
forum: Multimedia &amp; Video
---

### Post by coolfrood on 2006-06-18
Hi,

I have lost sound on my laptop after upgrading from Breezy to Dapper.  I have an Intel 82801DB-ICH4 card.  I've looked at the usual culprits such as /dev/dsp, esd running, alsactl power on, etc.  What else should I look at?

Update: I have sound on the headphones, but no sound from the speakers.

---

### Post by coolfrood on 2006-06-20
OK, replying to my own post.  I have found a solution.  Turns out, I had to turn off both "Headphone Jack Sense" and "Line Sense" to get sound on the laptop speakers.  I found this to be an old bug in the default setup of ALSA.  I wonder why is started showing up on Dapper.

[http://www.linux-on-laptops.com/forum/showthread.php?t=154&highlight=alsa](http://www.linux-on-laptops.com/forum/showthread.php?t=154&highlight=alsa)

---

