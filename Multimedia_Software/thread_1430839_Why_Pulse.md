---
title: "Why Pulse?"
date: 2010-03-15
forum: Multimedia Software
---

### Post by Gingerman on 2010-03-15
I've read all the Byzantine methods people are employing to work around Pulse Audio problems, and I am puzzled.  Why?  Why use a system that doesn't work for so many people?

I have been using Ubuntu for a long time, and now I can't because I can't overcome the audio problems.  

Isn't there some way for me to have an option of using the former audio system, which worked for me?  I've had to change OS because of this, and I don't like the other one very much, but everything works in it.

---

### Post by Chronon on 2010-03-15
Have you tried installing Ubuntu from scratch?  The only problems I have had with Pulse were due to improper configuration after updating from 8.04 to 8.10.

---

### Post by soltanis on 2010-03-16
I suggest you stop using the mess that is Pulseaudio+ALSA altogether and try OSS4. Especially if you have a vanilla sound card (Intel AC97 codec based), this tends to work out really well for everyone involved. A lot of applications support OSS, because it was around before ALSA (but some applications, generally ones with alternatives, insist on ALSA only).

[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

