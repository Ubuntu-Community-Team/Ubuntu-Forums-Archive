---
title: "combined left/right audio"
date: 2011-02-18
forum: Multimedia Software
---

### Post by fliped_Bliss on 2011-02-18
hi, first time I have had a real issue I cant fix looking though manuals or other posts.  
I am using ubuntu 10.10 (now) but in 9.04 there were no issues with audio (checked 10.04 which also had problems with audio but I did not stick around long enough to figure out what).
My left and right audio are being mixed and fed back out as if it were a single channel (for both left and right headphone) when I open sound preferences with music playing and move the slider bar from left to right (for which headphone it should be playing out of) all the music does is get quieter.  when I test each speaker it plays left and right though both sides.

the output for aplay-l:

card 0: CK8S [NVidia CK8S], device 0: Intel ICH [NVidia CK8S]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK8S [NVidia CK8S], device 2: Intel ICH - IEC958 [NVidia CK8S - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

and the sound card portion from lspci -v:

00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
    Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device a551
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    I/O ports at f000 [size=256]
    I/O ports at fb00 [size=128]
    Memory at fdffb000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

I am going to keep looking for solutions, but hope someone has run into this and will be able to steer me in the right direction.

---

