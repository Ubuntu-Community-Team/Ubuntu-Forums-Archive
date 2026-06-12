---
title: "Video Encoding Server Package?"
date: 2009-11-29
forum: Multimedia Software
---

### Post by gateway69 on 2009-11-29
I'm running the latest ubuntu server and was thinking of setting up a complete video encoding service with web interface, video queuing, converting to various formats etc.. 

Before I do this and spend all this time I wanted to know if similar packages already exist , I would rather not re-create the wheel.

I would use open source encoders

ffmpeg
mencoder
mp4box for hinting

Prob code the UI in PHP, with the encoder part running perl or python.

Anyone know of such a system?

If not anyone care to help out?

---

### Post by FakeOutdoorsman on 2009-11-30
These packages all exist in the Ubuntu repository.  FFmpeg from the repository does not have "restricted" encoders enabled by default, but they are easy to enable:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

MP4Box is part of the **gpac** package in the repository.

---

