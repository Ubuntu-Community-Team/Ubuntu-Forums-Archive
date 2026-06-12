---
title: "Audacious window sticking to edges of desktop?"
date: 2009-06-16
forum: Multimedia Software
---

### Post by foogoo on 2009-06-16
I had a really weird problem happen to Audacious tonight that literally occurred out of nowhere. I'm running Audacious 1.5.1 on Jaunty. IIRC, I was moving the audacious window out of the way as I usually do and it suddenly starts sticking to the bottom edge of the screen. Now I can only move the Audacious window along the bottom edge of the Desktop and it will 'snap' to the corners if you get close.

I've tried restarting the program and restarting the computer to no avail. Anyone have something similar happen before?

---

### Post by foogoo on 2009-06-18
Alright, I fixed the problem by going to ~/.config/audacious/config and changing "snap_windows" to FALSE. It worked once until I restarted Audacious, and it set itself back to TRUE. Now everytime I change it and restart Audacious, it automatically changes it back. What gives??

---

