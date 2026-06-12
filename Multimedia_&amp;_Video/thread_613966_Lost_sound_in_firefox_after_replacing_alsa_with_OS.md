---
title: "Lost sound in firefox after replacing alsa with OSS"
date: 2007-11-15
forum: Multimedia &amp; Video
---

### Post by aashay on 2007-11-15
So I removed ALSA and installed OSS on my system. Even replaced libesd-alsa0 with libesd0. Now, the problem is, firefox has lost all sound. I tried most of the solutions already suggested on the forum like FIREFOX_ESD="aoss" etc in firefoxrc. Sound works good on all other apps. Even system sounds like login logout etc play fine. Seems ff is the only one with the problem.

---

### Post by Metaljaz on 2007-11-15
What version of Ubuntu are you using? Maybe the version of flashplayer that is installed does not support the version of OSS you have installed. When you right click on the volume button make sure the device is showing OSS and not Alsa. Do the same when you double click on the volume button and check under file>change device to make sure it is also set to OSS.
Just suggestions...

---

### Post by aashay on 2007-11-16
Thanks for the reply, but I forgot to post that the problem was fixed. I installed libflashsupport and the rest was automagic. Just some minor synchronization issues that I can live with for now

---

