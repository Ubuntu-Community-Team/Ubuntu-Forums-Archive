---
title: "Sound"
date: 2009-07-30
forum: Multimedia Software
---

### Post by W4l0ck on 2009-07-30
My sound just suddenly stopped working. somebody help fix.

---

### Post by igorzwx on 2009-07-30
aplay -l

---

### Post by W4l0ck on 2009-07-30
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by igorzwx on 2009-07-30
Do you have an old box?

---

### Post by W4l0ck on 2009-07-30
not really, it worked last week, My computer is 4 yrs old (that i have had it)

---

### Post by igorzwx on 2009-07-30
The best solution for you is OSS4.

I have IMB Notebook (2003),
and an old box of 2001 (for experiments)

IMB -> 00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)

I have Ubuntu 9.04 with OSS4 on both computers.
Fantastic sound.
Skype, Ekiga, Audacity - everything perfect.

Install another Ubuntu 9.04 in dual boot
and try this solution:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

read this too:
[http://en.wikipedia.org/wiki/Open_Sound_System](http://en.wikipedia.org/wiki/Open_Sound_System)

[LIST]
[*][Sorry State of Sound in Linux]("http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html")
[*][State of sound in Linux not so sorry after all]("http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html")
[*][OSS is dead. Long live OSS!]("http://4front-tech.com/hannublog/?p=5")
[/LIST]

---

### Post by W4l0ck on 2009-07-30
Thanks.

---

