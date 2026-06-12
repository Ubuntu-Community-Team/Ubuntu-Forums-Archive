---
title: "How to make my sound works ?"
date: 2009-08-20
forum: Multimedia Software
---

### Post by pumber on 2009-08-20
I am running AMD 64 with Ubuntu 9.0.4 amd 64 bit version.

My motherboard is gigabyte MA78GM-US2H, which uses the chip Realtek ALC889A.

However, the sound doesn't work after I installed the OS.

How to fix it ? Thank you !

---

### Post by madurst on 2009-08-20
this is what fixed my muted sound for me..
First go into system- preferences- sound (the second one)
and on the sound playback line hit test, to have that running in the background so you know if it works
 in the terminal type 

```
alsamixer
```

and make sure everything is up 100% and unmuted
use the arrow keys to move over and the m to unmute...

What eventually fixed it for me was after everything was up 100% and unmuted, i muted the "external" or external speaker option in the far right of alsa mixer, and it then sent the sound to my normal built in speakers. Hope this helps.

Matt

---

### Post by pumber on 2009-08-24
I've tried but it still didn't work. Any idea ?

Thank you !

---

### Post by count_alucard on 2009-08-24
have u try upgrading ur alsa to the latest version? maybe this would help.. >> [ALSA GUIDE]("http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/")

---

