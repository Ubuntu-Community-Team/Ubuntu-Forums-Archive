---
title: "static before sound with Intel 82801 (Intel HDA sound)"
date: 2008-01-04
forum: Multimedia &amp; Video
---

### Post by mblind on 2008-01-04
I have a Dell D830 with a little problem.

The Audio controller is a intel 82801h (Intel HDA) which did not work with the intial install of Ubuntu..
I was able to fix this problem by doing this:
sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

Ok, After I did that .. Voila! Sound then worked.. But everytime, right before a sound plays I get static coming out of the speakers. Any program does this. Also When I run a program like the Hydrogen Drum Machine.. I just get MEGA static with the sounds breaking up through out.

Any Ideas on how to fix this. Generally it's usable but just annoying.

Thanks for your help

Update: Anyone? No one uses the Intel HDA sound chip with Alsa and has Static before sound plays?

---

### Post by diodoros on 2008-01-09
I have a related problem. I have Gutsy installed on a Thinkpad T61p, which includes AD1984 sound hardware. Audio playback of MP3s and video is just fine. But the static produced in Hydrogen is terrible. Any advice on troubleshooting would be much appreciated.

---

### Post by diodoros on 2008-01-09
Correction. I also have the Intel 82801H audio chipset.

I've read in various places that certain sound troubles are caused by using alsa 1.0.14 (default on Gutsy) with this chipset but can be alleviated by upgrading to 1.0.15. There is no Gutsy package for the latter version, so I haven't had time to try it yet. Here is a thread on installing it: [http://ubuntuforums.org/showthread.php?t=612605](http://ubuntuforums.org/showthread.php?t=612605)

---

### Post by manimal347 on 2008-01-10
I' have a thought as to what the problem is. I remember recently poking around the ALSA wiki and reading about how some soundcards would power off after a period of inactivity. When they'd re-engage, a pop, thump or burst of static would result, much like when you turn on a cheap or old amplifier.

No link as it's 2:00 AM and Google is failing me. Sorry.

---

