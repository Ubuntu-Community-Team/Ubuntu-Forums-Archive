---
title: "FFmpeg multi threading"
date: 2007-09-07
forum: Multimedia Production
---

### Post by SeanTater on 2007-09-07
I've been using FFMpeg and Avidemux to edit and save some TV recordings recently, and I noticed that neither ever used both cores on my Dual Core AMD X2 processor.  The -threads option of FFMpeg brings me closer and closer to 100% utilization on one core, but never uses the second core.. I looked in htop and it does indeed have several threads running, but they total to 100% processor utilization, whereas they should each be 100%. So I recompiled FFMpeg, making sure to add in --enable-pthreads, even though -version said it was enabled. The result, of course, was no difference. But it does not make sense to me why multiple threads would be sharing one cpu.. Is there any explanation of this?

BTW: I'm using MPEG2, which is apparently supported for multi-threading..

---

### Post by arsenic23 on 2008-04-29
I'm having the same problems with ffmpeg - no matter what I do I can't get it to use more then one core of my Q6600, a processor I bought because of ffmpeg multicore benchmarks.

---

