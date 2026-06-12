---
title: "Inverted colours, nVidia drivers"
date: 2010-03-06
forum: Multimedia Software
---

### Post by airtacable on 2010-03-06
Hi all,

For some streamed Internet videos, eg [http://www.rte.ie/live/](http://www.rte.ie/live/) using windows media player file , the colours are inverted. This "fixes itself" whenever I open the nvidia control panel (*System > Administration > NVIDIA X server settings*). I didn't have this problem on 9.04 and just wandering if there's something I forgot to set up after the update (not a fresh install).

It's not a show stopper, but it would be nice to have it working as before.

I suppose I could schedule the nvidia control panel to open on startup, but there must be a simpler solution.

Any ideas?

---

### Post by jerrrys on 2010-03-06
did you install ubuntu restricted extras?

---

### Post by airtacable on 2010-03-06
Yes, double checked that. And medibuntu.

---

### Post by airtacable on 2010-03-06
I found the fix in this thread:

[http://ubuntuforums.org/showthread.php?t=769209&highlight=playback+black+white](http://ubuntuforums.org/showthread.php?t=769209&highlight=playback+black+white)

Many thanks to cor2y

It seems there is some problem with the hue value in the nvidia drivers. To fix it open totem and go to Edit > Preferences > Display and adjust the hue value till it works.

---

