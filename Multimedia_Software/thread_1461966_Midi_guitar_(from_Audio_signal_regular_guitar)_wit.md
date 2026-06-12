---
title: "Midi guitar (from Audio signal regular guitar) with Linux Software?  Can I do it?"
date: 2010-04-24
forum: Multimedia Software
---

### Post by JayPeeJay on 2010-04-24
I was wondering if there is any software that will transform an audio signal (which would be my guitar) to midi data, therefore making a midi guitar without buying one.  I know there are guitar tuners, and vocoders, so why not?  I am sure there is but can't seem to find one.

I should mention that I never got JACk working so if it works with ALSA or OSS that would be even better, but if not I can do a little digging and probably try to get JACK working.

---

### Post by cchhrriiss121212 on 2010-04-25
I'm fairly certain that an analogue guitar signal cannot just be switched into midi using software. If you get jack going, you can use a virtual midi keyboard and connect it to whatever you like.
What are you getting stuck with when using jack?

---

### Post by JayPeeJay on 2010-05-27
Nevermind, JACK works, I just have to tell it to use ALSA as the backend when I run (jackd -d alsa).

Yes!!!  There are two possibilities for converting incoming audio into midi in realtime with JACk.

The first is Midingsolo, which gave me a little trouble when trying to compile (something about font errors?  Not sure if this was text font or if it was looking for a sound font (which I do have).

Anyway, I didn't get midingsolo working, but lucky for me there is a second option.

Rakarrack, which is also a great effects processor btw, has a midi out option.  I downloaded, compiled, and had up in running with no problems in about 2 minutes, and it's everything I wanted it to be.  I should mention that you can't do chords, but I am actually using it with my bass, so that isn't an issue for me.  I was impressed with the low latency.

---

