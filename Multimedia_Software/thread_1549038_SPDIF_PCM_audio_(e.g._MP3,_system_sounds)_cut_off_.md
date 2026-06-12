---
title: "SPDIF: PCM audio (e.g. MP3, system sounds) cut off at beginning"
date: 2010-08-09
forum: Multimedia Software
---

### Post by The Bright Side on 2010-08-09
Hey!

I am using the Creative X-Fi Surround sound card and a Samsung 5.1 Home Theater system. When I play back MP3s, or system sounds are played, the beginning of the audio is cut off.

The nature of the cut-off is that audio fades in instead of just starting. It's only the fraction of a second, but whenever sound is played after a silence (i.e. also in songs that have short silent breaks, like Roxette's "The Look"), the beginning of the audio quickly fades in.

So in "The Look", instead of playing

Na na na na na, na na na na na, na na na na na na she's got the look

It plays:

[%fade in]a na na na na, na na na na na, na na na na na na she's got the look

Any ideas what is causing this? I already turned off the suspend option for Pulse audio, but it happens whether I use Pulse or ALSA for output.

Hope you can help me!!

Thanks so much in advance :-)

---

### Post by ol1v3r on 2010-09-14
I'm afraid that's how it is with SPDIF. I have it hooked up to my Logitech Z-5500s and get exactly the same problem.

On Windows there is an application called SPDIF Keep Alive, which allows me to play MP3s and system sounds without delay, because it plays a silent noise to keep the amp locked onto the signal. Not sure if anything is available for Ubuntu that does this though.

---

### Post by The Bright Side on 2010-09-14
Yeah, that's be nice. I connected my amp with analogue cables now to eliminate the problem and use SPDIF for movies/Doly Digital only.

Thanks!

---

### Post by CHAMÆLEO on 2011-08-26
I have the same problem, but I’m using a normal audio jack.  I’ve noticed the problem since I upgraded to Ubuntu 11.04.

‘Cut off’ is a bad way of describing it.  It smoothly fades in, in such a way that this cannot possibly be a bug.  Some insane person at some point decided that it would be a great idea to enforce fade-ins.  It actually sounds good for a lot of audio; it’s just infuriating if the first second of the file is important.

I’ve put up with this for months, hoping that an update would fix this insane behaviour, but to no avail.  Please, I beg you, tell me how to turn this imbecilic feature off.

---

