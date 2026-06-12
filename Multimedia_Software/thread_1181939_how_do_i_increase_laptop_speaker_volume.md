---
title: "how do i increase laptop speaker volume?"
date: 2009-06-08
forum: Multimedia Software
---

### Post by keratos on 2009-06-08
ubuntu jaunty,
kernel 2.6.30rc6 (installed from repos)
snd-hda-intel kernel audio driver that comes with 2.6.30-rc6
ALSA
Intel HD audio
Toshiba Satellite Pro A300

Okay, so the sound works fine however on max volume the perceived audio volume is around 60% of the max volume on XP on the same machine (dual boot).

In ALSA [mixer] and audio properties in Ubuntu, PCM is on max as are Master and all other gains/inputs.

Tried the stock 2.6.28 kernel and drivers, this made no change. 

As I said the sound works fine in terms of clarity but its nowhere near as loud as it can/should be with all the obvious volume and gain inputs on %100.

Any ideas? Thanks.

---

### Post by HappyFeet on 2009-06-08
See [this]("https://help.ubuntu.com/community/HdaIntelSoundHowto").

---

### Post by keratos on 2009-06-08
Sorry, I should have provided S/W versions.

My Alsa is already at 1.0.20 , from the repos , and thus upgrading Alsa is not the solution. 

Nice link though ;)

---

