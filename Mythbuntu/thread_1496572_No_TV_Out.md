---
title: "No TV Out"
date: 2010-05-29
forum: Mythbuntu
---

### Post by jayco on 2010-05-29
Hey all,
 
I updgraded my MythBuntu 9.10 box a couple of nights ago to 10 using one of the package managers.  Everything seems to have upgraded correctly, but I don't have any output on my Hauppauge PVR-350 card.
 
The screen initializes and turns black, like I would expect, but then nothing ever appears.
 
If I VNC into the box, I get a "normal" screen complete with my MythBuntu screens etc.
 
There are no other monitors connected to this particular PC, so it shouldn't be auto-detecting anything.
 
Any ideas?
 
Thanks,
Jim

---

### Post by jayco on 2010-05-29
I was able to solve my problem...  the upgrade script had removed my xorg.conf.  On top of that, the framebuffer device number changed with the upgrade (from 0 to 1).
 
After editing both, I'm back to showing X on the TV.
 
However...  I have no remote control and no sound...  any ideas on those?
 
Thanks,
Jim

---

