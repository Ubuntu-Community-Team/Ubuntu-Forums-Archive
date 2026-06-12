---
title: "Why does nvidia legacy load on boot when I installed nvidia-new?"
date: 2008-04-21
forum: Multimedia &amp; Video
---

### Post by xanas3712 on 2008-04-21
I was wondering if anyone else has this issue.  I installed nvidia-glx-new through apt, but for some reason when the computer boots it loads the nvidia legacy module which I never asked to install (instead of 169.12 it loads 72.xx.xx (not sure of specific version) )

Of course, since I have an 8800 GTS it crashes X constantly (or stalls) and brings up the nice screen to fix X (which also removes nvidia from my xorg.conf if I use it) but the problem is that it's using the wrong module.

So far I've been fixing it by just removing the legacy/nvidia drivers leaving only nvidia-new.  But why does this happen in the first place?  I'm not sure if this is a bug or some weird system-specific oddity (though I have no idea how it came about).  

The only thing else I could think that I would have done to influence this is I do install the nvidia-drivers from nvidia's website myself on occasion.

---

