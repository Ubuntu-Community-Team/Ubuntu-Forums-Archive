---
title: "AC97 - scratchy output"
date: 2006-12-06
forum: Multimedia &amp; Video
---

### Post by cohort on 2006-12-06
Primary sound is scratchy.

onboard VIA 82xx AC97

If I set up xmms to use 'hw(0,1)', the sound output is crystal clear, but I can't figure out how to tell the rest of the system to use the same thing or get it to probe the subcompunents differently.

---

### Post by etaham on 2006-12-06
My audio also sounded bad. run:
```
alsamixer
```
and lower the pcm volume to under 50

---

