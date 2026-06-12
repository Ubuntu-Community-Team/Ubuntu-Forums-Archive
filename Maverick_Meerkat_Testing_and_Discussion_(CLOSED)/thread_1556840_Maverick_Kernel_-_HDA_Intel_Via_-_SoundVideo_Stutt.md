---
title: "Maverick Kernel - HDA Intel Via - Sound/Video Stuttering"
date: 2010-08-20
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by NightwishFan on 2010-08-20
I used the kernel backport of 2.6.35 to Lucid (I will test on Maverick if required, but I assumed this would be the best place to post this anyway). My sound card has noted problems with kernels after 2.6.32, however it works quite well on the backport except at random times the sound will stutter (like the old pulseaudio back in 8.04). It will eventually fix itself, but happens more common after happening once until a reboot.

The real mind boggler is that this also happens with video in totem and even flash video on the web. I think this may be a direct result of the sound card.

Does anyone else have similar problems? My desktop has the backport kernel as well and does not have this issue (hardware specific problem)

The laptop in question also has Intel Graphics if that is a factor.

---

### Post by simosx on 2010-08-20
Follow the advice at 
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)
for the collection of sound card info.
You will be give a link to a report; reply with that link so that we can try to help you.

---

### Post by NightwishFan on 2010-08-20
I filed a bug report here:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/621430](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/621430)

---

