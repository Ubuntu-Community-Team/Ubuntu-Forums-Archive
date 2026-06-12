---
title: "Converting AVI to MP4"
date: 2014-08-07
forum: Multimedia Software
---

### Post by mn_voyageur on 2014-08-07
I have several AVI files that I would like to show people on my android smartphone.  However, my phone won't play AVIs.  

I converted it with FFMPEG:  avconv -i ABC.avi ABC.mp4 but the resulting mp4 was full of small boxes.  

What options should I use to create the best mp4 output?

Thanks,
MarkN

---

### Post by papibe on 2014-08-07
Hi mn_voyageur.

This similar thread should help: [What are the correct paramaters for avconv to reduce avi file size?]("http://ubuntuforums.org/showthread.php?t=2226345&highlight=avconv") (answer on post #4).

Let us know how it goes.
Regards.

---

### Post by mn_voyageur on 2014-08-07
Thanks.  I searched for "FFMPEG convert AVI" before I knew that FFMPEG was deprecated.  

Thanks,
MarkN

---

### Post by FakeOutdoorsman on 2014-08-08
ffmpeg from FFmpeg is still under heavy development. The counterfeit and fake "ffmpeg" from Libav, a fork of FFmpeg, was deprecated by the fork for avconv.

Neither the fork nor Debian/Ubuntu maintainers attempted to make this distinction for the general users resulting in additional confusion.

---

