---
title: "A question about ffmpeg and qscale"
date: 2013-05-13
forum: Multimedia Software
---

### Post by lloydh on 2013-05-13
I have been trying to get qscale to work in ffmpeg but I always get the same size of output file no matter what value I give for qscale.          Is qscale codec dependent or maybe I am doing something wrong, my ffmpeg is **ffmpeg version 0.8.6-6:0.8.6-0ubuntu0.12.10.1.**

The following is how I have been testing, the input file is flv but I have also used vob files for the input and always the same result.

```
ffmpeg -i input.flv -vcodec libx264 -qscale 1 -acodec ac3 -ac 2 -ar 48K -ab 224K -async 1 output.mkv
```

In the above example a qscale of 1 and 10 produces identical output files in size and bitrate, I have assumed that increasing the qscale value should give a reduced bitrate in the output file, is my assumption correct.

---

### Post by andrew.46 on 2013-05-13
Rather than me talking about an area I understand poorly have a look here:

[https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide)

where the details are explained.

---

### Post by FakeOutdoorsman on 2013-05-13
The encoder you're using, libx264, ignores "-qscale"; instead use "-crf" (note that the values will be different than typical "-qscale" usage) as shown in the link andrew.46 provided. If you must use "-qscale", then use a different encoder such as: mpeg1video, mpeg2video, mpeg4, mjpeg, msmpeg4v2, msmpeg4, h263, h263p, and flv (the encoder, not the container format).

---

### Post by lloydh on 2013-05-13
Thanks guys for pointing me in the right direction, I have some reading to do.

---

