---
title: "Odd audio problem"
date: 2007-07-05
forum: Multimedia &amp; Video
---

### Post by jpardey on 2007-07-05
Hello,

Little technical problem with audio. With the majority of similar problems being related to the high volume problem, I found it hard to search for this. Sorry if this is a duplicate.

Just installed Ubuntu AMD64 7.04 on a new computer (AMD Athlon 64 bit dual core 6000+ (3.01 ghz), new GeForce using drivers from envy, 2 gigs DDR2 ram, 7200 rpm 250 gig SATA drive, nForce motherboard (I might have heard of some problem with them), etc etc. I can be more specific if necessary). I bought a PCI soundcard for it, an Audigy LS.

Under Windows (XP pro 32 bit) audio sounded great. Bit of a system hum, but only in very rare occasions, and never while any sound was playing.

Under Ubuntu, the starting or stopping of a sound causes one or more pops in the left channel. No sign of it in the right at all. Not particularly loud, but definitely audible through my headphones (plugged directly into the card). Sounds roughly like an old amplifier being turned on.

This happens for OSS, ALSA, and eSound (all) output in xmms, as well as output from ZynAddSubFX (OSS). System sounds do the same. The problem exists in all audio I have heard on the machine, and has more problems in OpenArena (a constant crackle, both channels, volume level independent, it isn't that problem, but I don't care about that at the moment) Starting two xmmses at once, I find that if I have them both playing at once (I use eSound for this, problems otherwise) the click goes away for one that I stop and start. I gather from this that my problem is when the channel is opened or closed.

Does anyone have any idea how to fix this, or what is causing this? I hope to use this computer for audio work eventually. Again, this only affects the left channel, there were no problems on Windows, and I have not heard any similar effects on my previous ubuntu install on another computer.

Thanks a lot for any advice.

---

### Post by Steveway on 2007-07-05
Are you sure that your headphones are ok?

---

### Post by jpardey on 2007-07-05
Tested them, they are working fine. Thanks though.

---

### Post by jpardey on 2007-07-10
For the record, I fixed the problem by putting in another sound card I had in an old machine. It works fine, but has never had much in the way of output, and gets distorted at high volume like other systems. I would rather use the other card, so if someone could give any advice, that would be great, but for now this works fine.

---

