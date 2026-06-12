---
title: "Sound Problem: ALSA Could not open resource for reading."
date: 2007-08-01
forum: Multimedia &amp; Video
---

### Post by tommyabroad on 2007-08-01
Hello I am a newbie experiencing the pain of goiung up the learning curve.  It also appears I am part of a very large group who have sound problems.

I am capable of following instructions but bear in mind my commandline vocabulary was not much more than:

```
ls cd 
```

a few weeks ago.

I have a Dell Latitude with an intel based sound card running Ubuntu Dapper.  I was expereincing the limitations of the default OSS sound setup so I tried getting ALSA to work.  After following various instructions online including compiling and installing the latest version of ALSA (1.0.14r4) along the way various things worked and others didn't buit I now have a system with what appears to be working sound ... well ... almost.

I am unable to record or use software which requires sound input.

Gizmo refuses to open because no sound input

Skype complains there is a problem with the sound card

Multimedia Systems Selector gives:

ERROR ALSA - Advanced Linux Sound Architecture: Could not open resource for **reading.**

when I test the default input plugin (pipeline *alsasr*)  Output is fine (*alsasink*)

Can anyone tell me what is wrong and, in simple terms, how to fix it?

Many thanks,

TA

---

### Post by FRuMMaGe on 2007-09-21
Im having the same problem with using alsa to input sound.  However, OSS works fine for the most part if you only use it for recording.

---

