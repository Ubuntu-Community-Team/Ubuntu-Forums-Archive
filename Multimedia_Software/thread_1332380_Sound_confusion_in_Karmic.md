---
title: "Sound confusion in Karmic"
date: 2009-11-20
forum: Multimedia Software
---

### Post by yniotis on 2009-11-20
Hi, i have recently installed the Karmic Coala and i have some matters with the sound i did not have in previous releases. I dont know weather they did not exist or i had not found because i started experimenting with such things after i installed Karmic.

On the sound preferences i set my speaker arrangement to "analog 5.1 sourround output/analog mono input". At first i noticed that songs were skipping using audacious. I changed the mixer in audacious to pulseaudio and everything was fine (i had it at alsa on jaunty). The same with xine where i have perfect surround sound setting the mixer to pulseaudio on the settings.

However when i try to play games the sound either stutters or goes off and some games crash when exiting. I can only solve this problem setting the speaker settings to "analog stereo duplex". This happens in both native games that crash (supertux, frozen bubble), that may not crash but still have troubled sound (etwq, savage2) and in wine games (wow, warcraft 3). Also i cant change the sound settings on etqw to anything but 2.0.

Is there any possibility that i can have surround on players without having to change it for games?

Also, can i have surround on at least native linux games?

Btw, my sound card is SB Audigy 2 ZS

Thanks a priori and sorry for my English, they will never improve

---

### Post by Vadi on 2009-11-20
See this report: [https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/485488](https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/485488)

---

### Post by yniotis on 2009-11-23
Thanks for your reply. I noticed that the  sound on the games randomly crashed sometimes even in analog stereo duplex so i decided to test the committed fix on the launchpad entry. I have the same problem with 5.1 surround but seems like the problems in analog stereo duplex have gone away. I do not leave a message in launchpad because i want to test it a few more times to be sure.

---

### Post by Vadi on 2009-11-23
Alright. Do report it eventually though please.

---

### Post by yniotis on 2009-11-23
After sometime playing savage 2 i experienced troubled sound when a lot of gunfire was up however the sound did not completely crash. I have to find some time and further test it. As soon as i am sure i will post on launchpad.

---

### Post by yniotis on 2009-11-28
The sound still stutters even after applying the ppa fix. The sound crashes seem to have stopped

---

### Post by ashu. on 2009-11-28
for me sound output is reduced n hell lot of multimedia probs

---

