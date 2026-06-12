---
title: "transcoded shows display a green screen"
date: 2009-08-17
forum: Mythbuntu
---

### Post by peterhocking on 2009-08-17
Hi

I'm using XBMC running under Windows XP as a frontend for my Mythbuntu PC.

If I transcode any recorded TV shows, they display a green screen when played back under XBMC. Audio is OK.

Playing the transcoded shows back under MyTHTV is fine.

Any ideas?

TIA

Peter

---

### Post by peterhocking on 2009-08-17
> **peterhocking said:**
> Hi

I'm using XBMC running under Windows XP as a frontend for my Mythbuntu PC.

If I transcode any recorded TV shows, they display a green screen when played back under XBMC. Audio is OK.

Playing the transcoded shows back under MyTHTV is fine.

Any ideas?

TIA

Peter

Since posting the above I've discovered what is causing the problem.

The transcoded files are now being transcoded to .nuv instead of .mpg files. I don't know whats changed, I've changed nothing.

I'm running 0.21.0+fixes21261-0ubuntu0+mythbuntu3 64 bitversion 64 bit Athlon 2800.

Any ideas on how to fix this?

TIA

Peter

---

### Post by mgag on 2009-08-26
Start MythTV frontend, go to the "Utilites/Setup- Setup - TV Settings - Recording Profiles - Software Encoders (if you have not mpeg2 tuner card)". Then manage profile for Live TV: set codec MPEG4 instead of RTjpeg.

It's OK ?

And edit other profiles, if you need.

P.S. Please, sorry for my English...

---

