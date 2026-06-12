---
title: "Switching the sound card OSS uses?"
date: 2006-08-05
forum: Multimedia &amp; Video
---

### Post by blackbeastofaarrgh on 2006-08-05
Hey everyone.
I just recently bought myself a Turtle Beach Rivera PCI sound card, as my integrated sound card is a piece of s**t.
Now, I easily was able to set up the sound card for usage is ALSA and ESD, but what I'd like to know is how to set up OSS to use it. Currently, OSS is still using the integrated card.
I know, you might be thinking "why does she want to use OSS?" (yes, I'm female), but it's because for some reason, SDL sound libraries for ESD make the sound delayed in some prograns like SuperTux and ZSNES, and ALSA makes the sound choppy in ZSNES. I know using SDL libraries for OSS fixes this because I've done it on my laptop. Works fine.
So the question is: is there a way to configure OSS to use the Turtle Beach sound card and *not* the integrated piece of crap?

---

### Post by blackbeastofaarrgh on 2006-08-05
Never mind, found a solution.
The alsa-oss package did the trick. :D

---

