---
title: "Headphones mute when plugged in (ubuntu 13.10)"
date: 2014-04-04
forum: Multimedia Software
---

### Post by ai555 on 2014-04-04
When plugging my headphones in, my speakers mute but the headphones give no sound either.  I set  in Alsamixer to Disabled but there is no change. It detects the headphones are plugged in, but has "MM" and no volume bar above it.  Prior to the latest update the week of March 31, 2014, I had no problems.My Alsa information is here: [http://www.alsa-project.org/db/?f=086ad63816e4176370d6e3a24a1b9a4030dfc8d8](http://www.alsa-project.org/db/?f=086ad63816e4176370d6e3a24a1b9a4030dfc8d8)

---

### Post by ajgreeny on 2014-04-04
Look in pulseaudio volume control, Output devices and on the dropdown box for Port: you may well find two outputs available, one for the main eg **Analogue output**, and the second for **Headphones**, where you may need to set volume, rather than in alsamixer.

---

### Post by ai555 on 2014-04-04
Thank you for the help, that gave me sound in the headphones.  So that combined with enabling Auto-Mute in Alsamixer to shut off the speakers when headphones are plugged in seems to have done the trick.  Problem solved.

---

### Post by ajgreeny on 2014-04-04
Great!

Can you mark as SOLVED from **Thread tools** menu at the top of this thread.

---

