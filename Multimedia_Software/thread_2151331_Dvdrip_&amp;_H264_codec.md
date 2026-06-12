---
title: "Dvdrip &amp; H264 codec"
date: 2013-06-04
forum: Multimedia Software
---

### Post by speartip on 2013-06-04
Has anyone managed to successfully use dvdrip to encode to x264/h264?
If so could you please explain your settings & if you had to install any extra codecs.
When I transcode, it runs through the process, but then spits out error messages at the end.
Any help would be appreciated.

---

### Post by andrew.46 on 2013-06-04
I do not use dvd::rip but I believe that it uses transcode for video processing. Transcode unfortunately has not been developed for some time and a big problem it has is not working terribly well with newer versins of FFmpeg. This could lie at the heart of your problem...

---

### Post by speartip on 2013-06-04
Thanks Andrew,
I think you're probably right. I would use Handbrake but it uses up 100 cpu & temps go through the roof. I like the idea of dvd:rip because, it rips the title 1st, then transcodes, making it a lot less stressful on my system.
But if it can't be done, i'll stick to xvid/avi.

---

### Post by andrew.46 on 2013-06-04
It is a little old fashioned now but I still pull out the script xvidenc from time to time. It uses MEncoder, which is old and unmaintained, but still produces a reasonable result. Best result for x264/h.264 will still come from a current x264 or FFmpeg + x264.

---

