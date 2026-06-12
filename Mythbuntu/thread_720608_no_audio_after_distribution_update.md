---
title: "no audio after distribution update"
date: 2008-03-10
forum: Mythbuntu
---

### Post by nickblame on 2008-03-10
After fresh install of mythbuntu 8.04 Alpha 3 the vnc password setting on the mythbuntu control center is not setting the password correctly.

after updating a distribution partial update was prompted. after that the vnc pass setting is working but no sound is configured!
alsa is broken completely for my onboard sis audio chipset. I even inserted an another audio card which is not detected correclty either.
dmesg is full of
[ 37.586301] snd: Unknown symbol unregister_sound_special
[ 37.586558] snd: Unknown symbol register_sound_special_device
[ 37.587270] snd: Unknown symbol sound_class
[ 37.588336] snd: Unknown symbol unregister_sound_special
and so on.

am i not supposed to update mythbuntu?

---

### Post by laga on 2008-03-10
> **nickblame said:**
> 
am i not supposed to update mythbuntu?

You're not supposed to update to an unstable version of Mythbuntu unless you expect things to break :) I saw similar error messages today when I booted one of my computers, but I don't need sound there.

Maybe this is the correct bug report? [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/192559](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/192559)

---

### Post by Al_Vampyre on 2008-03-10
Same for me as per this thread [http://ubuntuforums.org/showthread.php?t=720329](http://ubuntuforums.org/showthread.php?t=720329)

---

