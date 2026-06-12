---
title: "ffmpeg/libvpx error in stopmotion"
date: 2012-06-22
forum: Multimedia Software
---

### Post by yadingus on 2012-06-22
I'm using[ stopmotion]("http://linuxstopmotion.org/") and I have not been able to successfully export the animation as a movie.

Here is the error I receive:
 ```
ffmpeg version 0.10.2 Copyright (c) 2000-2012 the FFmpeg developers
 built on Jun 22 2012 11:58:29 with gcc 4.6.1
 configuration: --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-nonfree --enable-version3 --enable-x11grab
 libavutil 51. 35.100 / 51. 35.100
 libavcodec 53. 61.100 / 53. 61.100
 libavformat 53. 32.100 / 53. 32.100
 libavdevice 53. 4.100 / 53. 4.100
 libavfilter 2. 61.100 / 2. 61.100
 libswscale 2. 1.100 / 2. 1.100
 libswresample 0. 6.100 / 0. 6.100
 libpostproc 52. 0.100 / 52. 0.100
 Please use -b:a or -b:v, -b is ambiguous
 /home/piq/.stopmotion/packer/joy/images/%06d.jpg: No such file or directory
```Any suggestions/insights? I can't figure out what the issue is. I'm running precise pangolin by the way.

Thanks

---

### Post by Yurral on 2013-04-28
In settings the command line is ->

ffmpeg -r 10 -b 1800 -i "$IMAGEPATH/%06d.jpg" "$VIDEOFILE"

in your folder you may uses .JPG with cap letters

rename the command line to 

ffmpeg -r 10 -b 1800 -i "$IMAGEPATH/%06d.JPG" "$VIDEOFILE"

or rename the existing files in your folder to .jpg

---

