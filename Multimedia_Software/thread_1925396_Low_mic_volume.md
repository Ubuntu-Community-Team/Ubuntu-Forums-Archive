---
title: "Low mic volume"
date: 2012-02-14
forum: Multimedia Software
---

### Post by rghthndsd on 2012-02-14
ASUS Eee PC
Ubuntu 11.10

Trying to use my mic for the first time, it's built into my Eee PC netbook.  Whether using skype or arecord, it has low volume (can barely make out words).

So far I've tried:

1. System settings
2. PulseAudio Volume control
3. alsmixer

Putting every volume I can find for the mic up to max.  No luck so far.  At this point I'm willing to accept that my mic is most likely physically not functional, but I was just wondering if there was anything else I could try.

---

### Post by Desann243 on 2012-02-14
have you tried reinstalling the driver?

---

### Post by rghthndsd on 2012-02-14
Thanks Desann243!  When I went searching for new drivers, I stumbled upon [http://askubuntu.com/questions/16980/eeepc-internal-microphone-not-working](http://askubuntu.com/questions/16980/eeepc-internal-microphone-not-working) My microphone is mono, but set to stereo, and so (I think) it was counting actual audio as background noise.  Turning my right mic to 0 fixed this.
[]("http://askubuntu.com/questions/16980/eeepc-internal-microphone-not-working")

---

