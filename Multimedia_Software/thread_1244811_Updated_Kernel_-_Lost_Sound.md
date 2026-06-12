---
title: "Updated Kernel - Lost Sound"
date: 2009-08-19
forum: Multimedia Software
---

### Post by bailunrui on 2009-08-19
Like many others who upgraded from 9.04 from 8.10, I had sound issues. HOWEVER, I was able to solve those issues by updating my alsa-base.conf file with a different model (HP-DV5).

NOW, since kernel 2.6.28-14 was released, my system hasn't given me sound. ](*,) Luckily, I still have the 2.6.28-12 kernel to fall back on, but if new kernels are being released, there's a reason. I don't want to rely on an outdated kernel just because my sound is acting wonky.

Let me know if there is any output that I should post to aid in your help.

---

### Post by enz1m3 on 2009-08-21
The same way you fixed it for 2.6.28-12 doesn't work for recent kernels? Have you filed a bug about it? If you don't file a bug, people don't know there's a problem, and thus can't fix it :)

---

### Post by bailunrui on 2009-08-21
**enz1m3**, thanks for the suggestion - I will file a bug report. I just don't know what could have changed between 2.6.28-12 and 2.6.28-13+ that could have affected my sound.

---

### Post by bailunrui on 2009-08-21
Let me clarify one thing - I can actually get sound on 2.6.28-13, but I don't use it (thus forgot about it) because my wireless network isn't detected in that release (although this has been fixed in recent kernel releases). That's why I use 2.6.28-12.

---

