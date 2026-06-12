---
title: "[SOLVED] Question about using ffmpeg"
date: 2008-06-07
forum: Multimedia Software
---

### Post by ghindo on 2008-06-07
I'm trying to use ffmpeg to convert .avi files into .mp3 files.  I searched the forums and found one solution:```
ffmpeg -i INPUT.avi -vn OUTPUT.mp3
```This works alright, but I noticed that the resulting mp3 is always at 64kbps, not matter what quality the audio in the video is.  How do I get the quality of the resulting audio file to match the quality of the video?

---

### Post by bug80 on 2008-06-07
For example:

ffmpeg -i input.avi -acodec mp3 -ab 192k output.mp3

or, if you want to copy the audio stream bit for bit (the movie should contain mp3 audio in that case!):

ffmpeg -i input.avi -acodec copy output.mp3

---

### Post by ghindo on 2008-06-07
> **bug80 said:**
> For example:

ffmpeg -i input.avi -acodec mp3 -ab 192k output.mp3

or, if you want to copy the audio stream bit for bit (the movie should contain mp3 audio in that case!):

ffmpeg -i input.avi -acodec copy output.mp3Thanks, that did the trick!

---

