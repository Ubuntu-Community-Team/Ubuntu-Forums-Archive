---
title: "headphone output not working..."
date: 2008-11-07
forum: Multimedia Software
---

### Post by pgag45 on 2008-11-07
Hey there,

I have read previous threads with this issue (through google), but none seemed to help me... After upgrading to 8.10 my headphone jack stopped working. I went through all the volume controls and none are muted (as well as alsa mixer through the terminal) and all seemed ok. When in Windows the headphone jack works fine, and in Ubuntu the onboard laptop speakers work fine. I have to assume this is a driver issue... however, my knowledge of drivers with Ubuntu is extremely limited. I have a Gateway M-Series laptop. 

Any help would be appreciated! Again, sorry if this is a repeat post!

---

### Post by pgag45 on 2008-11-12
It's using STAC9205 ... tried all the guides, still nothing working. All volume controls up.

Still no sound out of headphone jack...

---

### Post by NCX001 on 2008-12-06
I have this same problem. However I can edit /etc/modprobe.d/alsa-base and add a line like:
```
options snd-hda-intel model=dell-m42
```

But it only works once per session, after a restart I have to do it agian, and I have to change model to something else. There is a list of models to try but I can't ever seem to find it when I need to. 

I spent about an hour in IRC trying to figure this out and no one could help. Hopefully someone can figure out something.

---

