---
title: "Quicktime and other codes"
date: 2011-11-24
forum: Multimedia Software
---

### Post by Quinetiam on 2011-11-24
I am wondering if there is full (wrapper).mov-Quicktime and (codec) mp4/h264/photoJPEG functions in any of the video packages available.

For example, in Quicktime I can convert uncompressed .avi to .mov photoJPEG with control over quality by %.

What I'm looking for is a package with full wrapper and codec functionality especially in HD.

Thanks,

---

### Post by wolfen69 on 2011-11-24
I'm not sure I fully understand you, but I guessing you want codecs? To get just about every possible codec there is, do:
```
sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
then
```
sudo apt-get install non-free-codecs ffmpeg
```

---

### Post by Quinetiam on 2011-11-25
Saving and exporting ([encoding]("http://en.wikipedia.org/wiki/Encoder")) to any of the [codecs]("http://en.wikipedia.org/wiki/Video_codec") supported by QuickTime.

I want to encode h264,mp4, photojpeg etc.

Openshot for example has limited export options, I'm looking for full encode options. From what I see FFmpeg has basic .mov encoding.

---

### Post by wolfen69 on 2011-11-25
Ffmpeg is good if you like using the terminal, but if you want a gui, you can install *winff*.

---

