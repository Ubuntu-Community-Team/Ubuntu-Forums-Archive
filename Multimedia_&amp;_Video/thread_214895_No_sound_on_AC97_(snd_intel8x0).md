---
title: "No sound on AC97 (snd_intel8x0)"
date: 2006-07-13
forum: Multimedia &amp; Video
---

### Post by R32 on 2006-07-13
It seems like a new kernel came with the last lot of updates. All went well enough, then when I rebooted, I couldn't log in. I figured out that any user in the AUDIO group couldn't get to the Gnome desktop.

It seems like the kernel modules (snd_intel8x0, snd_ac97_codec) are in fact loaded, judging from lsmod and when Ubuntu gets to the login screen, the drumbeat sounds plays. I just cannot get any sound because as soon as I add anyone to the AUDIO group, the Gnome desktop never appears. Just hangs.

Has anyone had and solved this problem? Or have any ideas how I can fix this?

Thanks

---

### Post by R32 on 2006-07-13
Fixed now.

---

