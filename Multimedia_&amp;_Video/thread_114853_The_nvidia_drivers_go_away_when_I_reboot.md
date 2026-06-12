---
title: "The nvidia drivers go away when I reboot"
date: 2006-01-09
forum: Multimedia &amp; Video
---

### Post by bannerboy on 2006-01-09
due to the fact that I am using xinerama, I have to have the latest nvidia drivers installed, so I used the official nvidia installer, and installed the drivers that way. this works just fine, except that I have to reinstall them after every reboot because the drivers go away. can anyone explain this? I would really like to not have to reinstall the drivers every time I start my system.

---

### Post by MartinG on 2006-01-09
This is almost certainly because you have not removed the (K)Ubuntu drivers and kernel module.  Before installing the new drivers you need to remove anything with nvidia in its name (nvidia-glx and others), AND the package linux-restricted-modules (this is probably the source of your problem).

See the following threads:
[http://www.ubuntuforums.org/showthread.php?t=103030](http://www.ubuntuforums.org/showthread.php?t=103030)
[http://www.ubuntuforums.org/showthread.php?t=105097](http://www.ubuntuforums.org/showthread.php?t=105097)

---

### Post by bannerboy on 2006-01-09
none of them are installed

---

### Post by MartinG on 2006-01-09
I'm stuck then.  Maybe this is linked to your hardware? (Mine is only a lowly 32-bit single-core Athlon 2200+, he says, slightly green with envy :)  )

---

### Post by Omnios on 2006-01-09
For 5.04 there was a wiki walk around to this problem you might want to check there

---

### Post by bannerboy on 2006-01-09
as it turns out, there's a rather simple fix for this anoying problem. you have to turn off the nvidia-glx or nvidia-glx-legacy boot-up script.

---

