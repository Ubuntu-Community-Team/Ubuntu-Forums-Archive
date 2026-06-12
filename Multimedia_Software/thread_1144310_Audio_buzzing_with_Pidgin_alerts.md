---
title: "Audio buzzing with Pidgin alerts"
date: 2009-04-30
forum: Multimedia Software
---

### Post by Phasmus on 2009-04-30
When Pidgin sounds an audio alert (contact went on/off line, message sent/received etc.) it is usually (not always) accompanied by an enraging, loud crackling/buzzing noise.  I haven't found any other applications doing this so far.  The crackling usually persists for a split second after the alert sound stops and I've tried turning down my volume, but so far not much has helped.

Any ideas?  Thanks.

---

### Post by quantumstatejim on 2009-05-13
I have also found this happens.  There is a bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/342946](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/342946) which seems to be about this same issue.  There is no fix though.

---

### Post by EgYPaRaDoX on 2009-05-14
I have the same problem, I believe the problem is only in jaunty, I am using dell inspiron 1545.

---

### Post by dullo on 2009-05-25
Same here everyone. It also happens to me and over time it can get very irritating. I did not have this problem when i had hardy installed, is there a fix yet or what?

---

### Post by aramodo on 2009-06-10
I did a little experimentation and I've managed to resolve this issue on my system. I suspect the bug takes place when the driver attempts to resample the sound to the working rate of the sound card. This is what I did:

1. Installed 'play' command - sudo apt-get install sox
2. Changed Pidgin Sound Mode to run this command - play %s -r44100 - instead of using ALSA directly.

The resampling to 44100 appears to be the critical part of this. With the 'play' command alone, it doesn't help.

---

### Post by scratman on 2009-06-15
+1 for fix

I don't know how you worked that out, but it fixes the problem on my machine!

---

### Post by mlejayne on 2010-12-27
Thank you, that solved the problem for me!

The problem started when I switched to Maverick and I'm using a Dell Studio 1555.

---

### Post by mankyd on 2011-03-16
SIMPLER FIX: I was just experiencing the same problem. I was about to apply this fix, when I decided to first try switching the sound mode from "Automatic" to "ALSA" first, just to see what happened. Sure enough, that fixed it.

---

