---
title: "converting mpeg and AVI video to IPod .mov files"
date: 2011-06-17
forum: Multimedia Software
---

### Post by cybrsaylr on 2011-06-17
Can anyone recommend a good program that will convert mpeg and AVI video files to .mov and mp4 files that can be played on an iphone or ipod?

---

### Post by shantiq on 2011-06-17
[handbrake]("http://ubuntuforums.org/showpost.php?p=10657166&postcount=10") is very good for this kind of task

---

### Post by cybrsaylr on 2011-06-17
Thanks for the tip.

Will FFmpeg and WinFF do this also?

---

### Post by shantiq on 2011-06-17
yes easy there too   install winff

click on presets    choose ipod format you wish for and Bob's your uncle

these are the specs while converting to ipod nano widescreen for example


```
  Metadata:
    encoder         : Lavf52.64.2
    Stream #0.0: Video: mpeg2video, yuv420p, 176x128 [PAR 152:121 DAR 19:11], q=2-31, 256 kb/s, 90k tbn, 25 tbc
    Stream #0.1: Audio: libmp3lame, 44100 Hz, stereo, s16, 128 kb/s


```


Handbrake does it too and will also turn dvds into video files with little fuss


your choice:KS

---

### Post by FakeOutdoorsman on 2011-06-17
> **cybrsaylr said:**
> Will FFmpeg and WinFF do this also?

Yes. Depending on your FFmpeg your commands may vary. What version of Ubuntu are you using? I can give you an example command.

---

### Post by cybrsaylr on 2011-06-17
I'm using 64 bit Natty Narwhal.

---

### Post by FakeOutdoorsman on 2011-06-17
This should do it:
```
ffmpeg -i input -vcodec libx264 -vpre medium -vpre ipod640 -crf 24 -threads 0 \
-s 640xfoo -acodec aac -strict experimental -ab 128k -ac 2 -metadata title="Your Title" \
output.mp4
```
Replace *-s 640xfoo* with a correct width, such as 640x480 or 640x360, or drop the -s option entirely. I added it to the example in case your device only handles a certain size.

---

### Post by cybrsaylr on 2011-06-18
FakeOutdoorsman, thanks for the code.

---

