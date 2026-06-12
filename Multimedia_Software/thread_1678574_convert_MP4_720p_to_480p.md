---
title: "convert MP4 720p to 480p"
date: 2011-01-30
forum: Multimedia Software
---

### Post by dumble on 2011-01-30
iv got some video documentary files in this format
Mp4 1280x720p 25 frames/sec
Audio is aac 2ch variable bitrate around 128 Kbps.


My netbook can not handle to play this 720p files.. so i want to convert the files from 720p to 480p

I think I can use mencoder, but I dont know the command

---

### Post by dumble on 2011-02-01
bump

---

### Post by peppeprof on 2011-02-01
I don't know in mencoder, but Avidemux can do it. Open the file, in the video section, instead of **copy** choose appropriate codec, e.g. MPEG_4 ASP (Xvid). Then configure as you need a MPlayer Resize Filter. At last **Save**.

---

### Post by FakeOutdoorsman on 2011-02-01
> **dumble said:**
> iv got some video documentary files in this format
Mp4 1280x720p 25 frames/sec
Audio is aac 2ch variable bitrate around 128 Kbps.


My netbook can not handle to play this 720p files.. so i want to convert the files from 720p to 480p

I think I can use mencoder, but I dont know the command

Using FFmpeg:

1. Enable additional encoders:
[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

2. Encode:
```
ffmpeg -i input -vcodec libx264 -vpre medium -crf 22 -threads 0 -s 852x480 -acodec copy output.mp4
```

If you chose **Option B** from the above link then change *medium* to *normal*. You can adjust *-s* to whatever size you want, such as *-s 640x360* if you wanted it smaller than my example.

---

