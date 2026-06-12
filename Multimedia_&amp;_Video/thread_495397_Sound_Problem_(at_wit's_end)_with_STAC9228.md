---
title: "Sound Problem (at wit's end) with STAC9228"
date: 2007-07-08
forum: Multimedia &amp; Video
---

### Post by osarusan on 2007-07-08
Hi, first off, let me say I have read through the forums, and I have gone through [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) to search for the solution. I've gone through all the steps, and it all seems successful except that sound still doesn't work. Sound isn't muted, the computer detects my card, it should be using the snd-hda-intel driver... everything seems exactly right. It just doesn't work... :-\

I'm using a Fujitsu Stylistic ST5112 tablet pc, with a SigmaTel STAC9228 sound card.

aplay -l and lspc -v correctly identify my card.
sudo modprobe snd-hda-intel runs without error.
I've even tried removing and reinstalling alsa, and recongifuring it. I've tried everything in the guide.
Using alsamixer shows my card properly, and everything looks kosher.

Please, if someone has experience with this card or driver, or has any other ideas of things to try, I would really appreciate some help! Thanks.

---

### Post by scholzilla on 2007-07-08
If you're using 7.04, try reinstalling OS but do not accept upgrades to the kernel (security upgrades listed first in update manager). This is a known bug:  see launchpad #121105. You can also use <apt-get upgrade> from term to do your upgrades, as this automatically withholds kernel updates. Very frustrating, and who knows if anyone is working on it or cares.

---

### Post by osarusan on 2007-11-05
Sadly the problem still hasn't been fixed... I've seen tons of post about the STAC9228, but none of the solutions have worked for me. Even reporting to the alsa team didn't get me any response... I really hope it's being worked on... :(

---

