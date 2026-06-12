---
title: "ffmpeg vs avconv"
date: 2012-06-21
forum: Multimedia Software
---

### Post by S_p_or_t_o on 2012-06-21
I was working on compiling ffmpeg when I saw this.

```
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.

```

what I am trying to do is a video podcast in which we play (and discuss) open source games. 

Should I continue with ffmpeg for screen capturing or should I pursue avconv?


ubuntu studio 12.04

---

### Post by FakeOutdoorsman on 2012-06-21
The "ffmpeg" you are using is from a fork of FFmpeg. Basically, if you want to use the repository version of "ffmpeg" then use avconv. Alternatively you could [compile FFmpeg](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide) or use [Jon Severinsson's FFmpeg PPA](https://launchpad.net/~jon-severinsson/+archive/ffmpeg) if you don't want to use the fork.

It's confusing. See [Who can tell me the difference and relation between ffmpeg, libav, and avconv](http://stackoverflow.com/a/9477756/1109017) for more information.

---

### Post by S_p_or_t_o on 2012-06-24
the PPA gave me a partial upgrade notice . I installed it via synaptic with the "mark all upgrades". it may have been a bad idea, lol. it removed the gstreamer decoding for the movie player, luckily mplayer still works and it doesn't seem to have affected openshot.

I'm fighting an alsa xrun issue that maybe related to ffmpeg and x264

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

---

