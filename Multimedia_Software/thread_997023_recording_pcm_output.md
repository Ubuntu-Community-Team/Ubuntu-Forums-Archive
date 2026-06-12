---
title: "recording pcm output"
date: 2008-11-29
forum: Multimedia Software
---

### Post by redxine on 2008-11-29
Is there any way to record what is outputted to the soundcard in audacity or some other editing program without using Jack?

---

### Post by mocha on 2008-11-29
Yes, use PulseAudio.  There is a thread on these forums that explains how to setup PulseAudio.  Then you just open the PulseAudio volume control and "route" the audio coming out of your speakers to the capture device, then you use audacity or arecord or whatever program to record it.

This is the thread
[http://ubuntuforums.org/showthread.php?t=843012]("http://ubuntuforums.org/showthread.php?t=843012")

---

