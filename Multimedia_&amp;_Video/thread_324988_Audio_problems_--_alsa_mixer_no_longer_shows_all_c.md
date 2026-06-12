---
title: "Audio problems -- alsa mixer no longer shows all connections!"
date: 2006-12-24
forum: Multimedia &amp; Video
---

### Post by ChicoMakani on 2006-12-24
Recently I noticed that spdif output isn't working anymore.  I looked at my mixer and it's completely differnent than it used to be.  Now it only shows controls for Main, and PCM.  I used to see all the controls that are available on my nVidia/Realtek ALC861 including the digital output.  I'm running Ubuntu Dapper.  The problem may have started when I upgraded the kernel from 2.6.15-16-k7 to 2.6.15-17-k7.  I tried the audio solutions guide but couldn't find anything wrong.  Any ideas on how to fix this?  Thanks.

---

### Post by hemlut on 2006-12-26
> **ChicoMakani said:**
> Recently I noticed that spdif output isn't working anymore.  I looked at my mixer and it's completely differnent than it used to be.  Now it only shows controls for Main, and PCM.  I used to see all the controls that are available on my nVidia/Realtek ALC861 including the digital output.  I'm running Ubuntu Dapper.  The problem may have started when I upgraded the kernel from 2.6.15-16-k7 to 2.6.15-17-k7.  I tried the audio solutions guide but couldn't find anything wrong.  Any ideas on how to fix this?  Thanks.

I have the same problem, wrote a bugreport about it:
[https://bugs.launchpad.net/distros/ubuntu/+source/linux-meta/+bug/77184](https://bugs.launchpad.net/distros/ubuntu/+source/linux-meta/+bug/77184)

Please feel free to add to the bugreport, its good if somebody else confirms the problem.

---

