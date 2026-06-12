---
title: "Help! All Sound stopped working"
date: 2007-01-22
forum: Multimedia &amp; Video
---

### Post by anomalz on 2007-01-22
Well, i just noticed that there is no sound coming out my system. not in the media players or in firefox, or in app's like gaim. also there is no system beep when i backspace in the terminal. It was all working fine last night i didn't do anything new to the system. I have checked the buttons on my laptop, restarted and i have tried using external speakers ( im on a Thinkpad T60 using Kubuntu 6.10) KMix says im at 100 percent and so does my built in buttons on it. and the volume in the applications (amorak) is turned up all the way

---

### Post by dcstar on 2007-01-24
> **anomalz said:**
> Well, i just noticed that there is no sound coming out my system. not in the media players or in firefox, or in app's like gaim. also there is no system beep when i backspace in the terminal. It was all working fine last night i didn't do anything new to the system. I have checked the buttons on my laptop, restarted and i have tried using external speakers ( im on a Thinkpad T60 using Kubuntu 6.10) KMix says im at 100 percent and so does my built in buttons on it. and the volume in the applications (amorak) is turned up all the way

Same thing happened to me a few days ago - and I think it was due to a kernel update (or some other update).

I found that whole module directories were missing, so my sound driver modules were not there to load at boot-up!

My "cure" was to tag my current kernel (and some other "Generic" kernel related files) in Synaptic to be re-installed, and after that completed all is well again.

---

