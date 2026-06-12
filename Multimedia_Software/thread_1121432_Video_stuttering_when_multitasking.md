---
title: "Video stuttering when multitasking"
date: 2009-04-10
forum: Multimedia Software
---

### Post by MistaED on 2009-04-10
Ok this has been a little annoyance ever since I've used GNU/Linux or Ubuntu in general, and that is when you multi-task while trying to view a video or something else at the same time, it stutters!

I'll give you an example of what I'm talking about, try using firefox like you normally would by spawning tabs, scrolling sites, or minimising/maximising windows, or running nautilus with scrolling. Do this while you have another window open like totem/vlc/kaffeine or mplayer playing back video. Does the video stutter at all? If it does, this is exactly what I'm getting at. This is with or without compiz, running a regular metacity does the same exact thing. The videos I play are xvid (MPEG4-ASP) SD videos, SD or HD streams from my tv tuners in the athlon & core2 machines (MPEG2), or h.264 (MPEG4-AVC)'s in HD resolutions. Also it uses Xv on all three. These stutters also appear with opengl like glxgears so it's not dependent on video playback, it's just a lot more noticeable :)

I have 3 machines which I've tested this on. My desktop is ubuntu 9.04 beta 64-bit running on top of an intel core2quad at 2.5ghz with 8gb ram and an 8800gt 1gb video card with the 180.44 nvidia drivers, default kernel. The other machine is running ubuntu 8.10 32-bit running on top of an athlon 64 3200+ at 2.2ghz, 1gb ram, nvidia 6800gt 256mb with the nvidia binary driver as well (not 100% sure which one) default kernel. The third one is an acer aspire one with 9.04 32-bit, 1gb ram, integrated intel video (945gm?) with Exa acceleration default kernel.

All 3 machines show this stutter, and I've experienced it on earlier ubuntu revisions as well. The CPU has moderate use on the netbook and athlon machines when playing back SD video but my main desktop isn't breaking any sweat. About 1-2 years ago I tried the CFS scheduler from here [http://ubuntuforums.org/showthread.php?t=538068](http://ubuntuforums.org/showthread.php?t=538068) to cure this issue on the athlon machine and it was actually _very_ successful! The stutter was _completely gone_. But then I heard the scheduler was coming in as default so I thought the next ubuntu should have this kernel so I don't have to maintain it. It did come in but it didn't solve the stutter issue :(

So I'm wondering, what did this patched-for-CFS kernel have which was different that cured the issue but the newer kernels that have CFS as default don't? Is it a special little config tweak which puts priority to interactive programs?

Thank you for your inputs on this narking issue I have.

---

### Post by markbuntu on 2009-04-10
I don't have this problem, but I am using a ati HD36501GB with a AMD6000X2+ cpu and 6 GB DDR2 800 ram with the latest 9.3 driver.

Did you try it with compiz off?

---

### Post by jaymzw on 2009-11-25
Try playing with your power management settings as detailed in this thread:

[http://ubuntuforums.org/showthread.php?t=1312185](http://ubuntuforums.org/showthread.php?t=1312185)

---

