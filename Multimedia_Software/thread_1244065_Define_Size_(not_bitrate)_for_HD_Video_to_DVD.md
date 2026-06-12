---
title: "Define Size (not bitrate) for HD Video to DVD"
date: 2009-08-19
forum: Multimedia Software
---

### Post by zwierbel on 2009-08-19
Hello,

I try to convert a HD video to a DVD. I used ffmpeg. It's working fine, but the file size is not the expected 4,4GB. It's often smaller (3,9GB). I converted it with:
$ ffmpeg -threads 2 -y -i invideo.ts -pass 1 -target pal-dvd -an /dev/null -newaudio
$ ffmpeg -threads 2 -fs 4690000000 -y -i invideo.ts -pass 2  -target pal-dvd -ac 2 -acodec ac3 "outvideo.mpg" -ac 2 -acodec ac3 -newaudio

AFAIK with two-pass-encoding ffmepg should use the variable bitrate to produce a 4,4GB mpg file. Has someone a hint for me?

I also tried mencoder (with the devede-GUI), but there I got a 2,9GB file.

Bye

Daniel

---

### Post by zwierbel on 2009-08-21
> **zwierbel said:**
> but the file size is not the expected 4,4GB. It's often smaller (3,9GB). I converted it with:
[...]
$ ffmpeg -threads 2 -fs 4690000000 -y -i invideo.ts -pass 2  -target pal-dvd -ac 2 -acodec ac3 "outvideo.mpg" -ac 2 -acodec ac3 -newaudio
With an other video I found out that the "-fs" limits the file size. If the video doesn't fit in to the size it will be truncated :-(
How can I tell ffmpeg to calculate the variable bitrate to a specific file size? With two pass encoding it should be easy for ffmpeg to calculate the exact variable bitrate.

Bye

Daniel

---

