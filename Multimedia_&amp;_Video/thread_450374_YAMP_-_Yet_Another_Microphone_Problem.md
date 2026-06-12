---
title: "YAMP - Yet Another Microphone Problem"
date: 2007-05-21
forum: Multimedia &amp; Video
---

### Post by popacsek on 2007-05-21
Hi!

I installed Ubuntu Feisty a few days ago. Everything went OK, except that after Skype was installed, I realized that the microphone is not working. I also tried to make a sound capture, but it failed too, however I can hear myself in the headset when I un-mute the microphone.
The previous distro was a Gentoo Linux, and Skype (and the microphone) worked correctly. Maybe  I  haven't set the sound options correctly, but after a several hours of "setting game" I have no idea what is the solution.

The motherboard is an  nforce3 chipset based MSI motherboard, and the sound card is an on-board Realtek ALC-850 card (NVidia CK8S).

(I attached the output of the amixer utility)

Please help me!

---

### Post by GingerRed on 2007-05-21
Hi Popacsek

Didn't you forget to switch to OSS in skype's options/sound devices?
I know it's a bit of a stupid question, seeing that you've allready worked with skype but it did happen to me!

GingerRed

---

### Post by arimed on 2007-05-21
I have the same problem. I switched to OSS in skype, but still have the problem:
working with ubuntu 7.04, can hear the mic in the headset, but not in skype or sound recorder.

---

### Post by popacsek on 2007-05-22
I set Skype using OSS, but in vain, the problem still exists.
Anyway, under Gentoo Skype was set up to use ALSA, and that worked flawlessly.

---

### Post by popacsek on 2007-05-23
I tested Skype (after it was set up to use OSS) using the Skype test call. Somehow it was failed, but yesterday someone called me, and I realized, that my microphone is working! 
Thank you GingerRed, that was the solution! I didn't even think abouit it, because under Gentoo, Skype was set up to use alsa.

---

### Post by GingerRed on 2007-05-27
Arimed,

Did you check your microphone capture, not the line in capture? In my alsa mixer I had add this one using the edit/preferences. It didn't show in the 'orginal' settings.

GingerRed

---

