---
title: "random question about encoding video files to 1080p"
date: 2007-08-24
forum: Multimedia &amp; Video
---

### Post by jasonwatkins on 2007-08-24
if it's even possible.

i was just wondering if i'd be able to play around with ripping a DVD (that i own legal fans :)) and re-encoding it to 1080p - or even 720p - so I could essentially manually upscale it to play it on my PC monitor - which, along with my graphics card, can play HD no problem.

the "super" tool for windows apparently delivers reasonable stable 1080p conversions (not that i'd know how to do it just yet ..) but i wondered if it's something someone has actually tried ??

---

### Post by stevejesus on 2008-02-13
You can do this with Mencoder, but be warned, if your player doesn't have good post-processing, then your 1080p wideo with look like poop.  When upscaling, you are essentially bringing out the worst from a DVD.  You should notice compression atrifacts that you would not normally notice in 480p.
With mencoder, just specify your resolution output.  This should work for any type of video format as a source.

---

### Post by jexxie on 2008-02-13
Is there a good series of encoder options that would process the video to look better, so the player doesn't need to?

---

### Post by stevejesus on 2008-02-13
probably, but it wont look much better than the source DVD...  All you will REALLY be doing is creating a 15gig videofile...  Thats not worth it.

---

### Post by disturbedite on 2008-02-13
yes, it is impossible to make media better quality than its source.  i wouldn't even do what you're considering doing unless i had to.  you're only making the quality worse by upscaling it.  (i hate dvd players that do that).
but if you must upscale, use a program that is capable of using the lanczos filter, it is produces better results when upscaling.  (if you use avidemux, you can add a lanczos filter with the rescale filter).

---

### Post by xzero1 on 2008-02-13
> yes, it is impossible to make media better quality than its source.

But when playing back the media the source will be 'upscaled' unless the display format is native to the source. This upscaling must happen real time and quality could suffer. By upscaling ahead of time processing and filtering could be applied that would not happen in real time. The end result is a better quality file (as far as the target display is concerned). If you want the highest quality, upscale to your target display format, not necessarily 1080p.

---

### Post by disturbedite on 2008-02-14
thats not true, its a placebo effect.  yes, resource-wise, you're right, you can cut out the overhead by upscaling it first, but it does not provide better quality.

---

### Post by xzero1 on 2008-02-15
Quality is subjective. I dont want to argue, but think about the logic of what I said.

---

### Post by disturbedite on 2008-02-15
well i don't want to argue either, but the fact remains, you're stretching pixels to abnormal sizes, degradation occurs, its unavoidable.

---

### Post by xzero1 on 2008-02-17
> **disturbedite said:**
> thats not true, its a placebo affect.  yes, resource-wise, you're right, you can cut out the overhead by upscaling it first, but it does not provide better quality.

The fact remains you are missing my point.

---

