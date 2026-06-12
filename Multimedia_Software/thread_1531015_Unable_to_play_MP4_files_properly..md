---
title: "Unable to play MP4 files properly."
date: 2010-07-14
forum: Multimedia Software
---

### Post by ashwinrao on 2010-07-14
Hi, For some reason, audio and video doesn't sync while playing MP4 video files. I have tried many MP4 files to confirm this is not specific file related issue. I have tried both VLC and Mplayer. Sound track doesn't sync with video track. Could you please guide me what I am missing. Thank you!

---

### Post by ashwinrao on 2010-07-15
Is there any thing extra I need to install to play the .mp4 format smoothly using GMplayer? The video freezes and the audio doesn't sync with video. Please anybody provide more information regarding this issue.

---

### Post by magiclinux on 2010-07-15
try smplayer u will like it

```
sudo apt-get install smplayer
```

and the sitting for audio output driver = user defined
video output driver= gl
if u have ATI use gl fast ati card

---

### Post by sharath.puranik on 2010-07-15
please mention your hardware configuration, a slow CPU or old graphics card can cause the problems that you are facing.

---

### Post by kukker32 on 2010-07-15
are you sure you have installed ubuntu restricted extras??

use the software center..

maybe it help with installing that

---

### Post by ashwinrao on 2010-07-15
Thank you for your replies. I'm not using any Graphics card. It's a on board nvidia 6100 chip set. I have tried SMplayer and installed restricted extras. Is my GIGABYTE GA-K8N51GMF-9 motherboard with AMD-64 Athlon is too old to play .mp4 properly?

---

### Post by Yellow Pasque on 2010-07-15
> It's a on board nvidia 6100 chip set. I have tried SMplayer and installed restricted extras. Is my GIGABYTE GA-K8N51GMF-9 motherboard with AMD-64 Athlon is too old to play .mp4 properly?
You'll probably need a dual-core processor to handle HD decoding without help from the video card. Geforce 6-series does not have HD video decode acceleration. Adding a Geforce 210 or GT220 card would help very much.

---

### Post by ashwinrao on 2010-07-16
> **Temüjin said:**
> You'll probably need a dual-core processor to handle HD decoding without help from the video card. Geforce 6-series does not have HD video decode acceleration. Adding a Geforce 210 or GT220 card would help very much.

Thank you! I'll go for graphics card in near future. I'm not using my PC for much gaming and entertainment purpose. Hence, I have missed this part before. Once again thank you for your prompt reply.

---

### Post by mohshami on 2010-07-16
Hey guys,

I have an AMD Athlon 64 X2 Dual Core Processor 3600+ on my PC and I still can't play large HD movies. Only one of the cores goes up to 100% usage. am I missing something?

Thanks

---

