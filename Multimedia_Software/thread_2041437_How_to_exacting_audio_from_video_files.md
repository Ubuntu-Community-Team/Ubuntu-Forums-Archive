---
title: "How to exacting audio from video files"
date: 2012-08-12
forum: Multimedia Software
---

### Post by siniavine on 2012-08-12
I have a bunch of video files from which I want to extract their audio tracks. I could do it by using ffmpeg and converting them all to ogg files for example: 
```
ffmpeg -i video -vn audio.ogg
```
But is there a way to extract the audio without having to re-encode it again.

---

### Post by evilsoup on 2012-08-12
Yes, just use -acodec copy

ffmpeg -i input.mp4 -acodec copy -vn output.m4a

Of course, depending on what the audio stream is, you will need to use different file extensions. If the audio is AAC (most MP4 and FLV files use AAC), then m4a will be perfectly fine. Obviously, if the audio track is an MP3, just use the mp3 extension. If in doubt, you can use .mka, which should allow any kind of audio stream.

You can find out what the audio stream is by looking at the properties in nautilus file manager (under the audio/video tab) or by reading the output of

ffmpeg -i input.mp4

---

### Post by ads52 on 2012-08-12
As evilsoup has suggested you need to identify the audio codec first before extracting the audio stream. When you use a *bare* commandline as you have demonstrated you run the risk of exposing your audio stream to the sometimes unsympathetic FFmpeg defaults. Meaning your audio stream may be inappropriately lowered in quality.

---

