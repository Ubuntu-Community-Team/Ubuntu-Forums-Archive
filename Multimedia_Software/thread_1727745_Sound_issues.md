---
title: "Sound issues"
date: 2011-04-12
forum: Multimedia Software
---

### Post by mindwarpusa on 2011-04-12
i'm having a problem, I switched my htpc from windows xp to  ubuntu 10.10 and since i switched my audio no longer works. these are my current stats. Please help im new to Linux so im not sure quite what to do. 



[http://www.alsa-project.org/db/?f=bb...10c560704f487c]("http://www.alsa-project.org/db/?f=bb3d7d6dd85bd9ef343ced27a010c560704f487c")

---

### Post by lidex on 2011-04-13
Your hdmi is the default output - is that intended?

---

### Post by mindwarpusa on 2011-04-14
no i am using just the 3.5mm stereo output

---

### Post by lidex on 2011-04-17
Try adding this to your alsa-base.conf:
```
alias snd-card-0 snd_intel8x0
alias sound-slot-0 snd_intel8x0
alias snd-card-1 snd_hda_intel
alias sound-slot-1 snd_hda_intel
```
Just add it at the bottom of this file:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Save. Close. Reboot. Check your mixers and sound preferences.

---

### Post by mindwarpusa on 2011-04-17
Thanks for all your help

---

### Post by lidex on 2011-04-18
You're welcome. All fixed then?

---

