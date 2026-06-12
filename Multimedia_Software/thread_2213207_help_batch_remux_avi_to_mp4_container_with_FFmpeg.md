---
title: "help batch remux avi to mp4 container with FFmpeg"
date: 2014-03-25
forum: Multimedia Software
---

### Post by polardude1983 on 2014-03-25
Hello,

I have a bunch of avi files that i want to remux into the mp4 container with ffmpeg. I want the video to be the same, but I want to change the audio to AAC format. Also I would like the output mp4 file to have the same name as the avi file and be placed in the same directory. But having trouble finding this through different websites.

any help would be appreciated.

---

### Post by FakeOutdoorsman on 2014-03-25
Please show some information about your inputs. Are they all using the same video and audio formats? The complete ffmpeg console output will suffice:
```
ffmpeg -i example_input_file.avi
```

---

### Post by polardude1983 on 2014-03-25
Same video. All avi Xvid and mpeg4. Audio is different on input files. Some are mp3, some ac3

---

### Post by jejeman on 2014-03-27
Just do
```
ffmpeg -i file.avi -vcodec copy -ab 192K file.mp4
```
Set the audio bitrate as you like.

---

