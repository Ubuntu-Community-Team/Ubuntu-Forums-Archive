---
title: "Crackling audio at the left channel [Fixed]"
date: 2011-05-29
forum: Multimedia Software
---

### Post by dither on 2011-05-29
I was experiencing crackling audio at the left channel, on my mac mini 2.1 (mid 2007 core 2 duo model). I've read every possible fix posted on the subject, but nothing could fix my problem.
 
 Until and including Maverick Meerkat, I was able to solve the problem temporarily with the command “alsa-utils reset” after every boot, but now with Natty this doesn't do the trick any more.
 
 I've noticed that audio through jack was playing back normally, so it was evident that pulseaudio was the issue. Fortunately, there is a solution that I would like to share with you in case someone has the same problem.
 
 I was not convinced by other's claims on similar issues that the crackling is occurring by internal audio levels being set too high. The cracking at the left channel sounded like audio was played back in 8bit resolution.  
 
 So I opened the pulseudio configuration file:
 gedit /etc/pulse/daemon.conf
 
 And uncommented the line that sets playback resolution to 16 bits.
 default-sample-format = s16le
 
 That's it, audio works perfectly now !  

:guitar:

---

### Post by remcoj on 2011-12-29
Works for me too, thanks for posting!

---

