---
title: "Need help with 5.1 sound"
date: 2008-12-27
forum: Multimedia Software
---

### Post by Dasota on 2008-12-27
There have been numerous posts on issues with sound, and getting 5.1 surround sound to work, and sound cards, and not a single one of them has been able to solve my problem.  I'm running a fresh copy of Ubuntu 8.10, and have tried doing the PulseAudio setup, reinstalling Alsa, and various other solutions.  I'm using a creative labs X-Fi Xtreme Audio card.  When I go into the volume control, the only "Device" that works is the CA0106 (Alsa Mixer).  Additionally, in the Preferences, the only mixers that adjust my speakers are the Analog Center/LFE, Analog Front, and Analog Rear.  I tried doing as one person suggested and running a soundtest:

"
5.1 channel surround:
speaker-test -Dplug:surround51 -c6 -l1 -twav
"

When I perform this test, every speaker functions properly, and I can adjust the individual sounds in the volume control.  However, if I play any other sound in ubuntu, whether it be an alert, a ding, an mp3, a movie, the only speakers that work are the Front Left and Front Right (adjustable only with the Analog Front mixer.  No other mixer works for these sounds).  Also, the microphone does not work at all.  

If I could get some help with this, it would be greatly appreciated.  Thank you.

---

### Post by Dasota on 2008-12-29
Shameless bump

---

### Post by markbuntu on 2008-12-29
Some people with X-FI cards have had success with the new driver from creative

[http://ubuntuforums.org/showthread.php?t=870001](http://ubuntuforums.org/showthread.php?t=870001)

---

