---
title: "Audio Jack sense in Gutsy"
date: 2007-10-19
forum: Multimedia &amp; Video
---

### Post by loopeando on 2007-10-19
Today I've installed Gutsy and found out that the an issue solved in Feisty was again a problem in Gutsy, the audio jack sense on my Lenovo 3000 N100.

It's as simple as this, when you plug in speakers or headphones on the audio jack the crappy internal speakers are still enabled.

Is there a solution available for this?, because I suspect it has something to do with the kernel change but I'm nowhere near as experienced to deal with that.

Thx a lot!

---

### Post by loopeando on 2007-10-19
Bump

---

### Post by Antimethod on 2007-10-20
i've got the same laptop and same problem.
no solution though.

---

### Post by loopeando on 2007-10-20
I really don't understand why this is happening because it was a bug in Edgy then fixed in Feisty then broken again with the 2.6.20-16 kernel upgrade for Feisty and finally it remains broken with Gutsy.

Is there any way to install Feisty's default kernel (2.6.20-15) in Gutsy?

---

### Post by flightless bird on 2007-10-24
I have exactly the same issue on an HP G5056

---

### Post by stonhaus on 2007-10-28
Same problem here as well. I was using feisty .15 for some time for just this reason.

Can anyone find the original post for the feisty issue on launchpad? I searched looking for the original fix, but came up empty handed.

---

### Post by loopeando on 2007-10-28
> **stonhaus said:**
> Same problem here as well. I was using feisty .15 for some time for just this reason.

Can anyone find the original post for the feisty issue on launchpad? I searched looking for the original fix, but came up empty handed.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/134146](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/134146)

And two more related to Lenovo N100 series

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/88546](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/88546)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136810](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136810)

---

### Post by crisofilas on 2007-11-14
I've an HP compaq nc4200, and the gutsy installation does not turns on the audiosense, but I was able to do it through alsamixer.
Hope this helps.

---

### Post by earache on 2008-01-04
Still NOT working on 2.6.22-14-generic. Recompiling ALSA does nothing. Updating LUM does nothing. Pretty annoying bug that is.

---

