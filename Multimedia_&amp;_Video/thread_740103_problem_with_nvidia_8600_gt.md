---
title: "problem with nvidia 8600 gt"
date: 2008-03-30
forum: Multimedia &amp; Video
---

### Post by al_ac on 2008-03-30
Hi

I installed the latest ubuntu 8.04 beta release . It 's a very nice release with lots of improvements but my video card don't work properly.
I have a nvidia 8600 gt video card. When I boot the system after install the nvidia-glx-new driver the computer hangs when try to load X server, the keyboard don't work and the screen goes black. I had the same problem with gusty.

The xorg log shows only the next error:
```
 (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
```

anyone knows what happend? 

ps: the complete log is [here]("http://pastebin.com/f692b497"). The 708 line has the error

---

### Post by chewearn on 2008-03-31
If you look at these lines

322: (II) LoadModule: "nv"
323: (II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
324: (II) Module nv: vendor="X.Org Foundation"

Looks like the nv driver was used, instead of nvidia-glx-new.

---

