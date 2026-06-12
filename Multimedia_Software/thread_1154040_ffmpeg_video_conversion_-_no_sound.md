---
title: "ffmpeg video conversion - no sound"
date: 2009-05-09
forum: Multimedia Software
---

### Post by Geffers on 2009-05-09
I'm a wee bit baffled over a conversion I have done using FFMPEG.

Following advice in this forum I installed the 'bleeding edge' version and have successfully converted some quick time movies into mpeg-1 to view on a TV device. Same mpeg-1 files play fine if burnt to a DVD.

For a different purpose I wanted a higher quality image so used WinFF to convert originals to DVD quality.  Now my problem, after burning output to a DVD I get good quality video but no sound on my modern, but low cost Goodmans TV with built in DVD player. Same DVD gives image and sound on an old stand alone DVD player.  Same file converted to mpeg-1 gives sound and video on both devices.

I'm thinking this may be an audio codec problem, the successful (but low quality video) file shows audio details as MPEG 1 Audio, Layer 2 whereas the better quality files with no sound shows AC-3 audio.

Any suggestions aprreciated.

Geffers

---

### Post by FakeOutdoorsman on 2009-05-11
What FFmpeg commands and/or WinFF presets did you use?

---

### Post by xzero1 on 2009-05-11
AC-3 is digital audio typically 5.1. Is it possible that the tv dvd player cannot downconvert this to surround sound or stereo for playback? Check if there is an option that allows this. If not you may want to include another audio track with the ac3 audio on the dvd. Most dvds have additional sound tracks most likely for this purpose.

---

