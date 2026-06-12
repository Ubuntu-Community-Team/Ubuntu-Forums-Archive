---
title: "No sound - VIA miniITX system with via8235 embedded sound card"
date: 2009-03-13
forum: Mythbuntu
---

### Post by cgull on 2009-03-13
I'm trying to set up an older VIA miniITX system as a MythTV frontend.  I installed Mythbuntu 8.10, which went fine, except I have no sound.  Using cat to send something to /dev/dsp doesn't work, so it's a general sound problem, not a problem with mythfrontend.

I ran alsamixer and found the main channel was muted, so I unmuted it, but it didn't help.  I went through an unmuted every channel and turned them all the way up, but I still have no sound.  I'm out of ideas and I'm hoping someone will point out what I've overlooked.

/proc/asound/cards:
```
 0 [V8235          ]: VIA8233 - VIA 8235
                      VIA 8235 with VT1616i at 0xe400, irq 10

```
/proc/asound/modules:
```
 0 snd_via82xx

```

---

