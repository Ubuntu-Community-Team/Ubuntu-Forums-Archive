---
title: "1080p playback performance in i7-620M vs. i7-840QM"
date: 2010-08-31
forum: Multimedia Software
---

### Post by penyuan on 2010-08-31
Hello,  I am preparing to purchase a new laptop, with Ubuntu 10.04 built in, from System76 with 8.0 GB DDR3 1333 MHz RAM, ATI 4570 graphics with 512 MB GDDR2 memory, 500 GB 7200 RPM SATA II hard drive, and I get to choose a CPU.  I am wondering:  1) Would I get better 1080p video playback performance with a dual core Core i7-620M or quad core Core i7-840QM CPU?  2) What is the best playback software in Ubuntu that takes full advantage of such a CPU, and also the GPU?  Thank you!

---

### Post by tripmix on 2010-08-31
I'm not familiar with the laptop models you are talking about and I don't really have time right now to check them out. But as a general rule GPU is more important that CPU when it comes to HD playback, in linux nvidia usually works better as the nvidia drivers for linux are usually better. Make sure the GPU has native HD video acceleration (it probably does if it has 1080p resolution but not for sure), it's called vdpau on nvidia cards (google it). I use vdpau in xbmc on my laptop and it plays 1080p on a 46" screen connected trough hdmi while using kde with full effects on the laptop screen also 1080p without problems even though the cpu (dual-core) is not very fast. On my stationary box I had (it broke) a really fast dual-core cpu but the nvidia card was 8800gtm which don't have HD acceleration and that barely played 720p video. vdpau was developed by nvidia especially for nix systems, I don't know if ati has anything equivalent as I never use ati myself.

---

### Post by penyuan on 2010-09-01
Turns out, though, that the models I am looking at only have ATI graphics. Therefore, does anyone know of:

1) Another company that makes Ubuntu laptops w/ Nvidia cards built in (that can handle HD)?

OR

2) A way to maximise performance on a machine w/ ATI GPU?

OR

3) Whether if it is better to have a dual core VS quad core i7 CPU?

Thanks!

---

### Post by tripmix on 2010-09-02
1) I don't know but I use a HP HDX 16 and installing ubuntu was a breeze, all hardware detected and working, has a tv-card 2 remotes hdmi 1080p res nvidia card geared towards HD video but most games play at full settings like Dragon Age. Only minor configuration required like updating nvidia drivers and configuring the remote buttons.

2) Don't know, sry. EDIT: you might want to look into vaapi, it seems to be an alternative to vdpau for ati.

3) Quad core i7 CPU is obviously better than dual core but it depends on what you are using it for, many video codecs and applications for example can only use one core so it will simply choose the core that has the least to do at the moment while others can use several cores at the same time. I for example had a lot of trouble a while back to get the x264 codec to use both cores to render HD video on an older box, I expect they got that working now though. If you need to compile code or analyses data and that kind of thing the CPU matters but for HD video and 3D rendering not so much anymore as thats been taken over by the GPU. My box only use about 10% of the CPU when rendering HD video with the GPU, some more when playing games.

---

