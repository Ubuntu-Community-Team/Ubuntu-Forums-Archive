---
title: "FFMPEG Scaling Issues"
date: 2011-01-14
forum: Multimedia Software
---

### Post by bieber on 2011-01-14
I've got a 1920x1080 video I've edited and rendered with Cinelerra, and I'm trying to use ffmpeg to transcode it to something smaller.  However, when I use a command like this, for instance:
```

ffmpeg -i input.mov -target dv  -tvstd NTSC -aspect 16:9 -y output.dv

```
I inevitably get some weird green band at the bottom of the frame in the converted video.  I know that there's some weird pixel stretching going on here, because the NTSC standard for 16:9 is 720x480 with rectangular pixels, and the 1080 version has square pixels, so I'm guessing the green band is an artifact of that process?  Does anyone know a solution for this?

---

### Post by BicyclerBoy on 2011-01-14
Always pays to build your own ffmpeg from source because the *buntu versions are so old & stripped.

The aspect ratio is ignored for format DV (bug or feature ?).
Don't use format DV .
Choose your output container & codec explicitly.
 
The -tvstd option relates to video capture/grab from analogue tuner capture cards..
Do not need it ?? 
The only connection between  NTSC & DV is the refresh rate.
The colour-space is different.
DV50 is 50Hz I think.

cmd options crop or cropdetect filters to clip the top & bottom?

---

### Post by FakeOutdoorsman on 2011-01-15
You want something "smaller", but DV video is generally 25 Mbit/s which isn't small. By smaller, so you mean file size or frame size?  However, FFmpeg shouldn't produce a green band for any reason, so it would be nice to figure out if this is a bug or not.  It could also be your video player. Does the green band appear if you play the video with *ffplay*?
```
ffplay output.dv
```
I can give you an example FFmpeg command to give you a "smaller" video, but I am unsure of any requirements or limitations that you may have.

---

