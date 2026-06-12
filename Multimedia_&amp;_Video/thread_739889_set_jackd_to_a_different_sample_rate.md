---
title: "set jackd to a different sample rate"
date: 2008-03-30
forum: Multimedia &amp; Video
---

### Post by marioquark on 2008-03-30
hi,
i am using jack audio.
i would have a sample rate of 41000 Hz, but even if i start jackd like this:
```
jackd -d alsa -p 512 **-r 41000** -P -S -s
```
then both command line and qjackctl interface tell me **48000** Hz being used.
can anyone explain me this situation and how to force 41000 Hz?!
thanx :)

---

### Post by ametade on 2008-05-04
Hi there,

I'm having exactly the same problem... Really strange. BTW, I'm using a hda intel sound card.

---

