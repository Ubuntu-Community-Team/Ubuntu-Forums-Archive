---
title: "Help Changing Resolution in Edgy"
date: 2006-11-12
forum: Multimedia &amp; Video
---

### Post by PC1492 on 2006-11-12
After installing Ubuntu for my fourth try and getting my wireless card finally working, I now have come across another problem. My monitor supports up to a 1440x900 resolution, and I can't choose any higher than 1024x768 in the System > Preferences > Screen Resolution dialog. I just got the NVIDIA drivers using Automatix, and by going to Applications > System Tools > NVIDIA Settings, theres nothing about screen resolution there. Any ideas? I'm a complete Linux n00b so I need step-by-step directions, thanks in advance.

Card: NVIDIA GeForce 6800XT
Using: Ubuntu Edgy Eft

---

### Post by john.nicholls on 2006-11-12
From a console, run
sudo dpkg-reconfigure xserver-xorg
If in doubt, accept the defaults. You'll eventually come to a screen where you can indicate the resolutions you want.

John

---

### Post by PC1492 on 2006-11-13
That didn't work. I unchecked every resolution except 1440x900, and it still doesn't show up in the System > Preferences > Screen Resolution menu, only resolutions lower than 1024x768. ](*,) 

Am I doing something wrong?

---

### Post by PC1492 on 2006-11-13
Alright, I got the resolution working, but now I have a font smoothing question. Is this how it's supposed to look? Windows looks much different.

---

