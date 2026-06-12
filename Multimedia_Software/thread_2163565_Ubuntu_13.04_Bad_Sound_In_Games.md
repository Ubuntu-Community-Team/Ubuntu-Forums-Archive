---
title: "Ubuntu 13.04 Bad Sound In Games"
date: 2013-07-18
forum: Multimedia Software
---

### Post by tecknomage on 2013-07-18
I have **Skype** installed and the hardware sound test using _Pulse Audio_ works with no distortion.

I play games where the launcher command HAS TO BE PREFIXED with "padsp" to get any sound at all.  What does "padsp" mean?

My games play with choppy sound. NOTE: **My Ubuntu laptop had no sound issue when I ran Ubuntu 12.10 with the same hardware.**

Is there a prefix to _force games_ to use **Pulse Audio** :confused:  I'm thinking since _Pulse Audio_ works with **Skype**, if I can get games to use it the choppiness would go away.

---

### Post by Yellow Pasque on 2013-07-20
It means to emulate the legacy OSS sound API (which Linux used before ALSA).

> Is there a prefix to force games to use pulseaudio?
It depends on the application. Which games are we talking about here?

---

