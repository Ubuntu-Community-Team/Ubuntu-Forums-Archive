---
title: "Console beep issues?"
date: 2010-05-04
forum: Multimedia Software
---

### Post by eckscalibur on 2010-05-04
I recently installed Kubuntu 10.04 64 bit edition on my Inspiron 15n, and all was to my satisfaction with one slight exception: I want to change the pitch for the console beep.  I have no internal speaker, so it must be virtually produced through speakers/headphones.  When I activated it, I was unhappy with its unusually sound (nowhere close to 400 Hz).  I used the the system bell settings in the notifications menu to change the pitch, but every value I could put in (from 186 to 2000 Hz) gave the same pitch whenever I hit 'Test'.  Changing the volume worked, but it also changed the duration of the sound produced.  Modifying the duration did not seem to work properly, either.  Applying changes did not actually change the duration of the system bell, nor any of the other changes I made.

So I figured I'd use the shell command beep -f 440 to make the pitch I desire--the only problem is that the beep command seems to have the wrong frequencies, too.  I tried various frequencies, but changing the frequency acted very unpredictably.  Occasionally, it took doubling the frequency to cause a half tone higher pitch; in others, merely going from 10749 to 10750 would cause roughly the same change in pitch (these were the two closest values I could put in to get close to 440 Hz (compared to reference recording on YouTube).  But at least the pitch managed to change in the range from 186 to 2000, unlike the system bell modification in the first part.

My sound system works perfectly otherwise.  I could probably just make a sound file that makes the sound I want, but I'd rather just use the default system notification, and I'm puzzled why it won't work.

---

