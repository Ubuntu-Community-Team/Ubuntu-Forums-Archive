---
title: "pick more than 1 recording source?"
date: 2007-07-14
forum: Multimedia Production
---

### Post by liquid boy on 2007-07-14
can alsa use more than one input source? 

i'm thinking of getting an audigy, and was wanting to use the line in and aux in to record 4 mono (2 stereo) tracks. can alsa handle this?

---

### Post by fredj on 2007-07-14
It depends on what you mean by more than one recording source. If your soundcard allows it then alsa can
do the following.
1. record from a single source e.g. mic, line in, CD etc.
2. Record the stereo mix e.g. if you are playing a CD and at the same time playing a synthesiser track and
recording a vocal into a mic, then you will be able to record all of these into a mono or stereo track. 
However this is not the same as recording 4 separate mono inputs into 4 separate mono tracks. So think
carefully about what you want to do before you buy a sound card.

---

### Post by liquid boy on 2007-07-15
i want to use the 2 stereo inputs (the aux in an the line in) to record 4 mono tracks simultaneously. 
in windows i've been able to record 2 mono tracks at the same time, using the stereo line-in on my soundblaster live! card using the asio4all drivers. (selecting left channel for track one and right channel for track 2).
i'm wanting to do this with 2 stereo inputs, to have 4 seperate mono tracks.

does that make sence?

this is possible in windows, using the [kx drivers]("http://kxproject.lugosoft.com"), but i'm wondering if i could use linux instead (it's open source, plus the kx drivers can only work in 16bit with asio)

---

