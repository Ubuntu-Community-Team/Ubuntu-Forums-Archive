---
title: "[SOLVED] Program required to bulk convert Avi to Ogg!"
date: 2008-10-21
forum: Multimedia Software
---

### Post by Rytron on 2008-10-21
Hi,
Does anyone know of a free program to mass convert .avi to .ogg?
I use the great OggConvert for converting single files to .ogg, however this is tedious when converting a folder full of .avi files.

Any advice?

Thanks.

---

### Post by hansdown on 2008-10-21
Hi rytron.

I found this. [https://answers.launchpad.net/ubuntu/+question/13928](https://answers.launchpad.net/ubuntu/+question/13928)

---

### Post by FakeOutdoorsman on 2008-10-21
Ogg is just a container format.  I assume you want video:
```
ffmpeg -i input.avi -acodec vorbis output.ogg
```
If you just want audio:
```
ffmpeg -i input.avi -acodec vorbis -vn output.ogg
```
If you want to convert all videos in a folder:
```
find ~/path/ -iname "*avi" -exec ffmpeg -i {} -acodec vorbis output.ogg ~/newpath/{}.ogg \;
```
I didn't test my batch code example, so it may not actually work.  I've never used ffmpeg2theora before as hansdown has suggested, but you can probably use it like:
```
ffmpeg2theora input.avi
```
batch:
```
find ~/path/ -iname "*avi" -exec ffmpeg2theora {} \;
```

---

