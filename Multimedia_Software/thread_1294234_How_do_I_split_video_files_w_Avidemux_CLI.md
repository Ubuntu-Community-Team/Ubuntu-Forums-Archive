---
title: "How do I split video files w/ Avidemux CLI?"
date: 2009-10-18
forum: Multimedia Software
---

### Post by sr_guy on 2009-10-18
What is the syntax to use with Avidemux CLI to split videos by start and end times? For instance, mencoder can split by start/end times with this:

mencoder -oac copy -ovc copy -ss 00:00 -endPos 04:00 test.avi -o test_a.avi

Is there an equivelent Avidemux command to do the same?

---

### Post by sr_guy on 2009-10-18
no one?

---

### Post by dream_coder on 2009-10-18
Just use the GUI, select point a then b and save the part you have cut out, you can cut any part of the movie you want, plenty of guides on using avidemux around just search google.

---

### Post by sr_guy on 2009-10-18
I know how to split via the gui. I wanted to explore the option of splitting from Avidemux CLI so I can setup cron jobs to split videos, or split via openssh at work rather then using remote desktop

---

