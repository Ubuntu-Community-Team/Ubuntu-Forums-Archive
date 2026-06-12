---
title: "[SOLVED] Alsa and sound problem 8.04.1"
date: 2008-12-07
forum: Multimedia Software
---

### Post by Otto-C on 2008-12-07
I was advised the following:

Open your mixer (gnome-mixer or another one) and make sure that the
recording source is set to the Mic entry. Your problem is a simple mixer
settings related problem.

When I do
 $alsamixer

it shows master (71) 
         PCM    (100)
         Capture(100)
         Capture(100)
         Digital (95)
         Input SO  this appears to be the mic (Just shows "mic")

How to set recording source to mic?

tia
Otto-C

Well partially. From another site "David" provided the following: "Have you got the little speaker icon - usually in the upper right hand corner on Gnome? Double clicking that should bring you up a GUI mixer. Whats in that mixer will depend on your sound card."

Worked ideally on a Dell XPS. Video and sound WORK.
On Dell Inspiron B130 video works great, sound  now works. Ran thru all combinations available. Joy

---

