---
title: "Video encoder- .avi to .flv"
date: 2009-05-28
forum: Multimedia Software
---

### Post by Lakeside5 on 2009-05-28
I would appreciate finding an easy to use, good quality video encoder. I need to convert my camera videos, .avi, to .flv mostly. It would be nice to have .mpg, .mov etc as well.  I have tried Avidemux, and Amarok. I enter the info, but nothing seems to happen. I would like to try something else. thanks

---

### Post by xzero1 on 2009-05-28
Install ffmpeg and any required codecs. See this link for more info  [http://ubuntuforums.org/showthread.php?t=1117283&highlight=install+ffmpeg](http://ubuntuforums.org/showthread.php?t=1117283&highlight=install+ffmpeg)


Once you have ffmpeg, run this in a terminal to convert your files:

```
ffmpeg -i name.avi -ar 44100 -sameq name.flv

```

---

### Post by FakeOutdoorsman on 2009-05-29
Why do you want FLV?  I recommend FFmpeg if you don't mind command-line.  By default, not all encoders are available for the repository FFmpeg, but they're very easy to enable:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

