---
title: "ffmpeg does not convert to mp3??"
date: 2009-06-12
forum: Multimedia Software
---

### Post by abhinav90 on 2009-06-12
Hi i currently work on ubuntu 9.04. Earlier my ffmpeg would convert flv to mp3 now after upgrading from 8.10 to 9.04 its had issues with the same. It says unsupported codec. How do i reinstall this mp3 codec.

The error which comes is quoted below:


> 
Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 29.97 (30000/1001)
Input #0, flv, from '/home/abhinav/Desktop/resham_jaisi_raahein.flv':
  Duration: 00:07:26.01, start: 0.000000, bitrate: 320 kb/s
    Stream #0.0: Video: flv, yuv420p, 320x240, 256 kb/s, 29.97 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, mono, s16, 64 kb/s
File '/home/abhinav/Desktop/resham.mp3' already exists. Overwrite ? [y/N] y
Output #0, mp3, to '/home/abhinav/Desktop/resham.mp3':
    Stream #0.0: Audio: 0x0000, 22050 Hz, mono, s16, 64 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
Unsupported codec for output stream #0.0


---

### Post by FakeOutdoorsman on 2009-06-12
What is your FFmpeg command?  You probably need to enable the MP3 encoder in FFmpeg:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

Alternatively, you could copy the audio stream from the input instead of re-encoding:
```
ffmpeg -i input.flv -acodec copy output.mp3
```

---

### Post by lukeiamyourfather on 2009-06-12
Download and build ffmpeg from source and be sure that all of the dependencies are installed. The version of ffmpeg in the Ubuntu repositories has some features disabled due to patent disputes and proprietary codecs. If you do a search here or on a search engine for how to build ffmpeg you should be good to go, its only a few steps. Cheers!

EDIT: FakeOutdoorsman beat me to it, that's a good solution too.

---

