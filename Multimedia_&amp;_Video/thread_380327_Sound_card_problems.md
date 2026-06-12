---
title: "Sound card problems"
date: 2007-03-09
forum: Multimedia &amp; Video
---

### Post by freddyfred on 2007-03-09
I have a weird problem with my Kmix. I recently re-installed Edgy (with a partition) but now I have no sound. Kmix has a big red X and does absolutely nothing... I have looked on quite a few forums about this issue and even tried to install ALSA with no luck. My computer first sees that I do not have a sound card:

....@.....desktop:~$ aplay -l
aplay: device_list:222: no soundcards found...
trent@yine-desktop:~$

But it knows I have one:

....@....-desktop:~$ lspci -v
02:02.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
        Subsystem: Voyetra Technologies Unknown device 3357
        Flags: bus master, slow devsel, latency 64, IRQ 177
        Memory at fe2fd000 (32-bit, non-prefetchable) [size=4K]
        Memory at fe100000 (32-bit, non-prefetchable) [size=1M]
        Capabilities: <access denied>

Probing the card doesn't seem to work either. I am new to Linux and could use some help. Thanks

---

### Post by Markus72 on 2007-03-09
Hi,

did you update lately?
I did it some days ago and before, my sound was fine.
Now, I have the same symptoms.

I just posted a similar thread into the installation forum.

Would you mind trying to boot from the live cd and tell me, if the sound works?
On my machine, it does.

Markus

---

### Post by al1b1 on 2007-03-10
The problem is some of the sound levels. In terminal open "gmix" and bring all the volume levels displayed to the max

---

### Post by freddyfred on 2007-03-12
Yes my sound does work when I boot up from the live CD... I am using Kubuntu Edgy right now but am in the process of moving on to Ubuntu 6.10 (kinda hoping that this won't happen there. Of course there will always be something!).

Thanks for responses and good luck.

---

