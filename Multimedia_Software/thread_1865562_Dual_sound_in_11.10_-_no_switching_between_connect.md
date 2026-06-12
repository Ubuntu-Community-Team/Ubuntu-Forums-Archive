---
title: "Dual sound in 11.10 - no switching between connectors"
date: 2011-10-20
forum: Multimedia Software
---

### Post by triple834 on 2011-10-20
I know that quite a few people have had this issue, but alas, there seems to be no answer to this particular variation of it.

In Natty, I could always (more or less) conveniently choose if I wanted to have the sound coming from both my laptop speakers and headphones OR just through my headphones. To do this, I simply had to choose the appropriate option under Sound Settings -> Output -> Connector. For some reason, Oneiric does not provide me with this option, my only choice is Analog Speakers. I tried running Alsamixer, but apparently, it doesn't even recognise my headphones, although they are working fine. This means I can't disable my laptop speakers without completely turning off the sound.

In case it helps:

> Audio device: ATI Technologies Inc RV710/730
    Subsystem: Hewlett-Packard Company Device 3637
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- StepDoes anyone have an idea how this problem could be solved or what I'm doing wrong?

---

### Post by triple834 on 2011-10-20
Hmm... seems I have managed to solve the problem myself. Alsamixer did recognise my headphones all along, so simply turning the speakers down to 00 (instead of actually muting them because this affects the master volume as well) did the job for me. A bit inconvenient, but what the hey. Thanks anyway!

---

