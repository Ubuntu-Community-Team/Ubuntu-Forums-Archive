---
title: "ffmpeg to split and recombine audio and video in mts files"
date: 2010-05-12
forum: Multimedia Software
---

### Post by davemar on 2010-05-12
I'm trying to do some editting of mts (AVCHD 1920x1080) files from my camcorder. I'm aiming to split the video and audio parts, tweak the audio part, then recombine them back into either an mts file, or normal ts file.

Here's what I've tried with ffmpeg (input file called 00012.mts, no audio tweaking done here):
1) Get the video only from the file:
```
ffmpeg -i 00012.mts -an -vcodec copy -f mpegts 00012_video.ts
```
2) Get the audio only from the file:
```
ffmpeg -i 00012.mts -vn -acodec copy -f ac3 00012_audio.ac3
```
3) Recombine the audio and video files:
```
ffmpeg -i 00012_video.ts -i 00012_audio.ac3 -vcodec copy -acodec copy -f mpegts 00012_new.ts
```

I would hope the 000012_new.ts file to play the same as the original 00012.ts but it doesn't. For some reason when I play back the new one in VLC it seem to think it is a very long file (hours rather than a few seconds) and crawls through it.

I think the problem is in stage 1, as the 00012_video.ts file exhibits the same problem, so is there a correct way of generating this file?

---

