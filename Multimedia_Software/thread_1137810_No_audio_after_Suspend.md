---
title: "No audio after Suspend"
date: 2009-04-25
forum: Multimedia Software
---

### Post by usererror on 2009-04-25
Anyone have any tips for figuring out why I don't have audio after my PC comes back from being in Suspend mode?

If I reboot the PC audio comes back.  I have tried restarting the alsa-utils service no dice.

my audio module is snd-cs46xx :  Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)

If I do

```
dmesg | grep cs46xx
```

I get this line that comes up:

```
[10181.871722] cs46xx: failure waiting for FIFO command to complete
```

But I don't know what to do from there.

Thanks :)

---

### Post by usererror on 2009-06-19
I ended up replacing my soundcard with a SoundBlaster Live! card that I got from another PC that was retiring.  Sound works great after suspend now.  Must have just been an issue with that original Turtle Beach card I was using.

---

