---
title: "Good flv to ipod converters anyone?"
date: 2010-06-25
forum: Multimedia Software
---

### Post by morbid_bean on 2010-06-25
Looking for any that you personally use,  Im having issues with ffmpeg and handbrake

---

### Post by FakeOutdoorsman on 2010-06-26
What kind of issues are you having with FFmpeg and Handbrake?

Although I don't own an iPod I believe this iPod example in the following thread should work very well:
[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

Although the above link deals with a recent, compiled version of FFmpeg, it doesn't mean that you are required to compile FFmpeg. Just make sure that you:
1. [Enable additional encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283).
2. Use *-vpre hq* instead of *-vpre slow* (as shown in the example) if you use a version of FFmpeg that is too old to use the newer preset names.

---

