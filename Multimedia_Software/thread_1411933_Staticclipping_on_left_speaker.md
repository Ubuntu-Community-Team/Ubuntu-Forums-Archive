---
title: "Static/clipping on left speaker?"
date: 2010-02-20
forum: Multimedia Software
---

### Post by DOS4dinner on 2010-02-20
Ubuntu 9.04
Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

Regardless of what I'm playing, what speakers I'm using (I've tried 3, including earbuds), I always get a small amount of static (kind of like clipping) on the left speaker. The right one is always perfectly clear. My sound settings don't appear to be weird, and messing with them did not make any difference.
 
Oddly, after a kernel upgrade, the sound was perfect on both...until I rebooted. After that, and since then, I get the weird static on the left speaker.

Ideas? Thanks in advance!

---

### Post by mörgæs on 2010-02-21
There are some known bugs regarding the left channel, for example 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/266927/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/266927/)

I do not know of a fix other than what is written there, but if you confirm the bug it might push it a little step towards a solution.

---

