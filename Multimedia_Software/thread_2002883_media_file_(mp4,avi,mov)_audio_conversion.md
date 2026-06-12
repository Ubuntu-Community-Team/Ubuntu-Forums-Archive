---
title: "media file (mp4,avi,mov) audio conversion"
date: 2012-06-13
forum: Multimedia Software
---

### Post by Snarf0 on 2012-06-13
I'm looking for a tool that can strip-off the left OR the right audio channel of all kind of media files (wmv,mp4,avi,mov).
So: test.mov -> test-leftaudio.mov (left audio channel only) + test-rightaudio.mov (right audio channel only)
 
Thanks in advance,
regards,
Snarf0

---

### Post by evilsoup on 2012-06-13
Have you tried Audacity?

---

### Post by Snarf0 on 2012-06-14
Yep, muting one audio channel with Audacity works fine. 
I 'm able to save the audio in a seperate audio file.
I didn't find how to save the movie file with the new sound.
Any idea ?

---

### Post by FakeOutdoorsman on 2012-06-14
FFmpeg can do this with *-map_channel*. I don't use the version from the repository, so I'm unsure if it will work for you:

Just the audio:
```
ffmpeg -i input -map_channel 0.1.0 left.wav -map_channel 0.1.1 right.wav
```
Or if you want the video in the output as well:
```
ffmpeg -i input -map_channel 0.1.0 -vcodec copy left.mkv -map_channel 0.1.1 -vcodec copy right.mkv
```

I don't think *-acodec copy* will allow you to strip one channel, so you probably have to re-encode, but I may be wrong. You should double-check and see if I labeled the outputs correctly. You may have to compile FFmpeg if *-map_channel* is unavailable:

[How To Compile FFmpeg and x264 on Ubuntu](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)

---

