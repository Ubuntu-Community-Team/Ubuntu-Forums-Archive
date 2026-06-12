---
title: "(OpenGL) Performance Regression after upgrade from Ubuntu Precise to Trusty (nvidia)"
date: 2014-10-24
forum: Multimedia Software
---

### Post by B._Bogart on 2014-10-24
I had a well running openframeworks project running on Xubuntu <strike>Lucid</strike> Precise  with opencv 2.4.8, CUDA 5.5 and the associated drivers on my Shuttle  SH87R6 (QC i5-4670) with a GTX 780 (no unity, no compiz, no compositor).  I (idiotically) choose to do the "security" updates, and since then my  rendering time went from 0.033 seconds per frame to 0.2 seconds per  frame. The code has not changed. I tried switching back to the old  kernel, and even did a fresh install of lucid and trusty. After changing  everything I could think of, I ended up with a trusty system with CUDA  6.5, opencv 2.4.10 and beta 343.13 drivers. Still, after all this my  performance has stayed the same. It seems I had some miraculous previous  config that was totally arbitrary (I had not installed any updates in  some time).

I'm not sure how doing the system updates lead to this, so I suspect the  nvidia driver. I've tried 343.13, 340.46 and 340.29 (included with CUDA  6.5), and I could not get 319.76 and 319.37 (CUDA 5.5) to work (could  not find kernel source). I would love to reset, but even a clean lucid  install with only the openframeworks dependencies installed and the same  CUDA 5.5 and nvidia driver still showed slow rendering. Could this be  an interaction between mesa libs and this nvidia driver?

---

