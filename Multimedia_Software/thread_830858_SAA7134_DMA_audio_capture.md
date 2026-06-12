---
title: "SAA7134 DMA audio capture"
date: 2008-06-16
forum: Multimedia Software
---

### Post by lucac81 on 2008-06-16
Hi guys
I'm using an Asus My Cinema P-7131 Hybrid on my PC under Hardy Heron

The card works fairly well out of the box with DVB-T (the only caveat is downloading the correct firmware and a little of hand work is involved to do tuning) but with Analog TV and Composite input I get no sound from the device without using dirty tricks that involve arecord/aplay or sox, for my experience the card is capable of doing DMA audio, but there is no app that does this.
mplayer seems capable to do that, but not in realtime (I need to use the immediatemode=0 option to get audio) so using it with a game console it's a no go! using the arecord/aplay trick it's good, but after some time the audio lags too much.
Without using a passthru cable, someone has been able to get audio without lag from that card?

---

