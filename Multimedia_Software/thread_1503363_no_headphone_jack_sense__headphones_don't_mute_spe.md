---
title: "no headphone jack sense / headphones don't mute speakers"
date: 2010-06-06
forum: Multimedia Software
---

### Post by dazift on 2010-06-06
acer aspire 6530 running Ubuntu 10.04
I know this is a common problem and many solutions are in the forums but I've tried all of them and NOTHING works! When I plug in my headphones the laptop speakers do not mute. Every once in a while this will work properly but most of the time it does not. If I plug in the headphones before booting, the sound will only come out of the headphones and when unplugged no sound will come out at all. I do not have a "jack sense" option and I do not have a separate headphone volume in alsamixer. I have tried adding the line 'options alsa-hda-intel model=3stack' which completely disables alsa on reboot so that does not work at all. i also tried model=acer-aspire-6530g which doesn't change anything. Please help. this problem is really annoying! If you need more info on my hardware or anything just let me know.

---

### Post by gismo93 on 2010-06-06
What version are you using? I know I had this problem at one time but I upgraded to the latest version and it fixed the problem, If you're on the latest version try installing all updates. Good luck.

---

### Post by dazift on 2010-06-06
I have alsa version 1.0.21. I believe the newest version of alsa is 1.0.23 but the last time I tried upgrading I lost sound for a while until i worked out some bugs. so I am afraid of trying to upgrade. is there a way to back up the alsa configuration and files that i have now?

---

