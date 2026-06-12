---
title: "Convert Ogv to Avi?"
date: 2009-05-30
forum: Multimedia Software
---

### Post by James Wilson on 2009-05-30
Hello,
 
I need to convert the container of my video file from ogg(ogv) to AVI, while retaining the Theora compressed core. 
Is this possible? I've already tried FFMPEG, no luck. VLC, no luck.
 
Thanks, 
James

---

### Post by FakeOutdoorsman on 2009-05-31
I don't know if OGG Theora in an AVI container is a real or "standard" format, but it can probably be done with FFmpeg:
```
ffmpeg -i input.ogg -acodec copy -vcodec copy output.avi
```

---

### Post by andrew.46 on 2009-05-31
Hi FakeOutdoorsman,

> **FakeOutdoorsman said:**
> I don't know if OGG Theora in an AVI container is a real or "standard" format, but it can probably be done with FFmpeg:
```
ffmpeg -i input.ogg -acodec copy -vcodec copy output.avi
```
 
According to my favorite wiki page:

Comparison of container formats
[http://en.wikipedia.org/wiki/Comparison_of_container_formats#Media_supported](http://en.wikipedia.org/wiki/Comparison_of_container_formats#Media_supported)

the theora video should be ok but the audio will more than likely be vorbis which could be a problem.

[**Off Topic:** Congrats on your guide featuring in the /TOPIC on #ffmpeg :-).]

Andrew

---

### Post by James Wilson on 2009-05-31
I'm not bundling audio with my video, so that's not a problem.
No luck with FFmpeg still, I did that and it made a 8 KB file that wouldn't play.
Tried Mencoder just now, no luck there either. Any ideas?

---

