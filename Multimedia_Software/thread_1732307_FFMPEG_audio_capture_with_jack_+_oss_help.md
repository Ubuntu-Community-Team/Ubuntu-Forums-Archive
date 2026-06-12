---
title: "FFMPEG audio capture with jack + oss help"
date: 2011-04-18
forum: Multimedia Software
---

### Post by TroyWorks on 2011-04-18
I'm looking for help configure a Ubuntu box, we need to capture alsa  output into ffmpeg with jack or OSS but not pulseaudio, as that tends to  glitch badly. 
 
We have things working, but we are sort of hacking around in the dark, we play music :guitar:, but as we aren't linux audio experts ourselves,  need halp.

Happy to paypal or barter webdev for help.

---

### Post by FakeOutdoorsman on 2011-04-18
As far as I can tell FFmpeg from the repository does not support JACK input, but you can compile FFmpeg yourself to get JACK support:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

The following will have some useful info of using JACK or ALSA with FFmpeg:
[list]
[*][HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?t=1392026)
[*][ffmpeg using Jack as an input](http://ubuntuforums.org/showthread.php?t=1556038)
[*][Screencasting with FFmpeg, jack_capture and Xephyr](http://wiki.linuxaudio.org/wiki/screencasttutorial)
[/list]

---

