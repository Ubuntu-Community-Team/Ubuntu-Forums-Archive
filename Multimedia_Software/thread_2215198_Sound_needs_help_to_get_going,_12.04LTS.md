---
title: "Sound needs help to get going, 12.04LTS"
date: 2014-04-05
forum: Multimedia Software
---

### Post by Taffywiking on 2014-04-05
I  made a clean install of Lubuntu 12.04LTS on a very old IBM ThinkPad A22M.   This has a Cirrus Logic CS-46XX based sound card. Most sound apps but  especially BBC Radio Player don't give any sound at first; this can only  be got going by using the volume control slider to adjust the volume, then the sound arrives.  I have tried;
aplay /user/share/sounds/alsa/Front_Center.wav
and got no result, so i tried
sudo aplay /user/share/sounds/alsa/Front_Center.wav
and it played.  so I added my user to the audio group, but after a reboot it behaved just the same; I don't understand why sound won't start straight away.

If I try and use the on screen volume slider it often results in a horrible  noise, like it gets stuck on playing a single bit over and over and requires a reboot. I've put up with this BS since version 9.04 but all the upgrades and updates don't help and now I'm reaching the end of my tether.   Is there any diagnostic information I can provide which will enable someone to help me?

---

### Post by mörgæs on 2014-04-06
Lubuntu 12.04 is not LTS, in fact it's already out of support.
in stead of struggling with this one I recommend a fresh install of 13.10 as a first step.

---

### Post by Taffywiking on 2014-04-08
Thanks for taking the time to reply mörgæs.  Unfortunately installing 13.10 is easier said than done, the low RAM version install hangs on reboot with an intermittently blinking cursor in the top left hand corner and minor disc activity. I'll get this fixed and come back to this thread if I need to.

---

