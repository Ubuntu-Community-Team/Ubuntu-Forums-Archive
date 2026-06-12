---
title: "[SOLVED] audio: why XMMS won't let any other program reproduce audio?"
date: 2008-03-03
forum: Multimedia &amp; Video
---

### Post by Korrontean on 2008-03-03
I've just finished a fresh install of Ubuntu 7.10, the experience was FANTASTIC, the best one so far.

However, I have a tiny issue: if XMMS is open, it won't let any other program reproduce audio.

Any ideas anyone? :(

THANKS!!!

---

### Post by jeffus_il on 2008-03-03
It's not Xmms, It's your sound driver, probably Alsa, it supports only one client program at a time. Use ESD the esound sound driver or newer and better still pulseaudio (more difficult to install). Make sure that XMMS or any other sound producing program is set up to use the driver of your choice (esd of pulseaudio) in it's preferences dialog.

---

### Post by Korrontean on 2008-03-03
Thank you Jeffus!
In fact, the one chose by default was OSS. I tried with eSound, still not working.
I tried with ALSA and it FIXED IT!!! :guitar:
Thank you, I had no idea about what the problem could be. :)

---

