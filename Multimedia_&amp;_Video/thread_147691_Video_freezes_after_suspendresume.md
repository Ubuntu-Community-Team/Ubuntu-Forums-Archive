---
title: "Video freezes after suspend/resume"
date: 2006-03-20
forum: Multimedia &amp; Video
---

### Post by scanez on 2006-03-20
Hello all,

I'm having a problem on my laptop with playing video after suspending/resuming. After resuming, sometimes when I fire up totem (or any other video player) the screen freezes and locks my laptop, forcing a hard reboot; sometimes it doesn't happen. It seems to be totally random as to when it will and won't happen, at least I haven't been able to reproduce it on cue!

I have a dell latitude d610 with integrated video (i915). I had the same problem under Debian (in fact I have had the problem since last June when I got the laptop). I'm using the 915resolution script to get 1400x1050, but I doubt that has anything to do with the problem since it freezes at lower resolution without the script as well. So I imagine it's a bug in the i915 driver or something similar, or maybe some bug in sata suspend/resume. But of course, since it happens totally randomly (or so it appears to me) and I can't reproduce it on cue, I have never filed a bug against anything.

So... anyone else ever had this problem? Or does anyone have an idea of what is actually wrong, and how I can forcibly reproduce it?

Thanks

---

