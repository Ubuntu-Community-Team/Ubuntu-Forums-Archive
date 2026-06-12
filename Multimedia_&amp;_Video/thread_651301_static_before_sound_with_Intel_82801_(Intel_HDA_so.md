---
title: "static before sound with Intel 82801 (Intel HDA sound)"
date: 2007-12-27
forum: Multimedia &amp; Video
---

### Post by mblind on 2007-12-27
I have a Dell D830 with a little problem.

The Audio controller is a intel 82801h (Intel HDA) which did not work with the intial install of Ubuntu..
I was able to fix this problem by doing this:
sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

Ok, After I did that .. Voila! Sound then worked..  But everytime, right before a sound plays I get static coming out of the speakers. Any program does this. Also When I run a program like the Hydrogen Drum Machine.. I just get MEGA static with the sounds breaking up through out.

Any Ideas on how to fix this. Generally it's usable but just annoying. 

Thanks for your help

Update: Anyone? No one uses the Intel HDA sound chip with Alsa and has Static before sound plays?

---

### Post by mblind on 2007-12-28
anyone.. Please!!

---

### Post by mblind on 2007-12-28
sorry to be a bother.. But is this the right forum?

---

