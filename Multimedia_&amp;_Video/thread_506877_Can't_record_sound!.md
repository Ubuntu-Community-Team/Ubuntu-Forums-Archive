---
title: "Can't record sound!"
date: 2007-07-22
forum: Multimedia &amp; Video
---

### Post by eoghanmurray on 2007-07-22
I'm currently preparing to make a podcast with some friends, but I can't record sound! In the sound dialog in Ubuntu Feisty, when I select

Stac92xx

i get:

gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open resource for writing.

I get the same output selecting 'ALSA'

When I select OSS, I get

Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'


Any tips?
I REALLY need this!

---

### Post by grayhammer on 2007-07-22
1. I would choose ALSA in the sound dialog.

2. Double check to be sure no programs are using the sound card. (Any media player of any kind, perhaps gaim, and I would shut down firefox as well.)

3. You might check the repos for a different sound recording program.

---

