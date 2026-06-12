---
title: "xruns"
date: 2006-12-05
forum: Multimedia &amp; Video
---

### Post by damu on 2006-12-05
I installed the rt-kernel proposed by Luneo and followed [this procedure]("https://help.ubuntu.com/community/UbuntuStudioPreparation") for Real-Time Support and Timer Resolution.

I remember seeing this settings on Luneo's website too, but as it is down for now, I guessed that the informations given would be the same on the UbuntuStudioPreparation page.

The result is pretty bad with an RME hammerfall and pcmcia. Loads of xruns, even at 23ms. A bit better at 48 khz, but globally far worse than what I had on my previous install with stock kernel.

Another bizarre thing when playing with Zynadd is that when it starts to go wrong (cracks , xruns, etc), It will then crack and pops even on one note. I have to close Zynadd and reopen to have a clean sound.

Where should I check first , to get things right?

---

### Post by luneo on 2006-12-06
try my new kernel ... and try my instructions... there some little things that the wike dosen't tell you... like that you need to create the audio group... and you need to install the realtime-lsm package... and enable realtime in Jack Control and set the priority to 89, and change the server path to jackstart

---

### Post by damu on 2006-12-07
Many thanks  Luneo, I will try that asap :) !

---

