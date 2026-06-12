---
title: "Audacity Record distorted/Choppy/Slow Audio"
date: 2006-10-01
forum: Multimedia &amp; Video
---

### Post by bluesplat on 2006-10-01
My PCI 128 SB Live (Ensoniq 5880) plays and records very well except when I choose "Play other tracks".

When I play one track and simultaeously record, the wave form is distorted and is about 40% slower than the master track.  Looking at the recorded wave form, it shows clear breaks in a sine wave (almost quantizing).

If I turn off the "play other track" - the wave form records perfectly clear.

It is almost like there is an interrupt interfering.

Ironically, I can play the first track in XMMS and simulanteously record the second track in Audacity and it works great -- Full duplex sound.  This means the PC is fast enough.

I have tried recording from 44100 down to 8k with the same issue.

I have only the PCI card and the NIC on the PCI bus.  No ISA cards in the computer.

I have read the OSS/ALSA sites and with no luck.  Hence I post to the gurus of gurus for consideration.

Thanks,

Bluespat.

---

### Post by Cylence on 2006-10-23
I too have the same issue. Quite an annoying problem. I also tried different recording options with no luck.

I'm now using Rosegarden (with Jack). I'd much prefer working in Audacity though...

---

### Post by Cylence on 2006-10-27
Solved thanks to this guide:

[http://lwn.net/Articles/202851/](http://lwn.net/Articles/202851/)

It appears that mono recording is broken. I switched to stereo recording and everything was fine, even in 32-bit float.

---

