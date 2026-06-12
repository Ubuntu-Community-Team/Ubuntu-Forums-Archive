---
title: "No sound"
date: 2018-03-31
forum: Multimedia Software
---

### Post by SimpsonTruckDriver on 2018-03-31
My sound worked when I installed KUbuntu 16.04 and Cinnamon (I ran Plasma for a while, but preferred Cinnamon), now it does not work. I scoured the Internet to find diagnostics (including here), nothing worked. This is a dual-boot system that also has Windows 10, sound works fine in it, which leads me to believe it is software-based.The sound card is seen in the software, just no sound. I also deleted and re-installed both Alsa and PulseAudio using
```
sudo apt-get remove --purge alsa-base pulseaudio
sudo apt-get install alsa-base pulseaudio
```
There is a script that allows the person to get a lot of diagnostics from Alsa, this is the page that is generated

[http://www.alsa-project.org/db/?f=80322356100fc691700a6f6f6fb6b777a6754b5d](http://www.alsa-project.org/db/?f=80322356100fc691700a6f6f6fb6b777a6754b5d)

So what am I missing?

TS

---

### Post by SimpsonTruckDriver on 2018-04-03
Must be a weird software "bug". It all of a sudden started working again. What did I do? Nothing other than reboot.

TS

---

