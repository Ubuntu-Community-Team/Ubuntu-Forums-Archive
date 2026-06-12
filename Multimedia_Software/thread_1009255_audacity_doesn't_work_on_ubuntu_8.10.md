---
title: "audacity doesn't work on ubuntu 8.10"
date: 2008-12-12
forum: Multimedia Software
---

### Post by ge0ffrey on 2008-12-12
On 2 new installations of ubuntu 8.10, I installed audacity.
On both, audacity starts up, but it't always records silence when totem or audacious or vlc or whatever is playing.

What's the easiest and quickest way to record on ubuntu 8.10?
Fix audacity (and how) or is there a simple, user-friendly, graphical alternative?

---

### Post by unoodles on 2008-12-12
try starting audacity like this: padsp audacity

---

### Post by ge0ffrey on 2008-12-13
> **unoodles said:**
> try starting audacity like this: padsp audacity
That doesn't make any difference.
I tried switching recording device, but that didn't help either.

---

### Post by ge0ffrey on 2008-12-13
I did get some cryptic output:

...$ padsp audacity
Expression 'ret' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1034
Expression 'AlsaOpen( hostApi, parameters, streamDir, &pcm )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1066
...

---

### Post by khelben1979 on 2008-12-13
Try downloading it directly from sourceforge.net instead.

Look [here]("http://sourceforge.net/project/showfiles.php?group_id=6235").

Maybe it's worth a try?

(I suspect that you might not have all the necessary libraries installed, or something like that..)

---

