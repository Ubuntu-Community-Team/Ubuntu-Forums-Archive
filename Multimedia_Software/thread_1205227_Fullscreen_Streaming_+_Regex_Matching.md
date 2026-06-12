---
title: "Fullscreen Streaming + Regex Matching"
date: 2009-07-05
forum: Multimedia Software
---

### Post by NarcT on 2009-07-05
Hey fellow users,

I have been using Ubuntu since Hardy and ever since then fullscreen flash videos have been a problem.  Now with Jaunty, flash videos are almost perfect with sites like Youtube and G4tv but sites like Hulu still have some problems.  

I have Compiz installed and have narrowed it down to Regex Matching.  Without Regex Matching my videos are perfect with no problems but with it enabled fullscreen videos are slightly choppy at times and screen tearing occurs regularly although its better than previous Ubuntu versions.

Does anyone know of a fix? Or can someone explain what Regex Matching is so I can better understand why I'm getting screen tearing only on sites like Hulu.  

Thanks!

Specs:
HP Pavilion dv9000t
nVidia GeForce Go 7600
NVIDIA Accelerated Graphics Driver (version 180)
Ubuntu 9.04

---

### Post by NarcT on 2009-07-05
So I kinda feel dumb but good news I found a fix...Although its not perfect my CPU usage is almost 35% lower and almost no screen tearing when viewing flash videos online...

The fix was in Compiz Settings Manager under Workarounds.  Check "Force Synchronization between X and GLX" 
This greatly improved my computers performance with flash videos and I'm surprised it was such an easy fix

Does this help anyone else?

---

