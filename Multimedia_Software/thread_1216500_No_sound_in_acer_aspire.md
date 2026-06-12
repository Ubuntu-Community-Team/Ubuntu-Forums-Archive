---
title: "No sound in acer aspire"
date: 2009-07-18
forum: Multimedia Software
---

### Post by emotionalBlind on 2009-07-18
I am using ubuntu 9.04. I installed 8.10 first and then upgraded to 9.04. Everything was fine. But but from yesterday. I can't here sound in ubuntu, but when I enter in xp, I can here sound there.

What should I do now?

---

### Post by igorzwx on 2009-07-18
try

aplay -l

see:
man aplay

---

### Post by emotionalBlind on 2009-07-18
Here is the output of aplay -l

**** List of PLAYBACK Hardware Devices ****
E: core-util.c: Home directory /home/arif not ours.
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
-------------------------------------------------------------
what to do now?

---

### Post by igorzwx on 2009-07-18
Now you can read this:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
[http://wiki.archlinux.org/index.php/OSS](http://wiki.archlinux.org/index.php/OSS)

---

### Post by markbuntu on 2009-07-18
Did you check the volume controls?
Sometimes they are muted after updates.

---

