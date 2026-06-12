---
title: "mplayer, ALSA, pulse..."
date: 2010-01-03
forum: Multimedia Software
---

### Post by matt90 on 2010-01-03
Hi,

I'm trying to get mplayer to recognize ALSA and/or pulse audio server, preferably both.  On my laptop, mplayer works fine -- mplayer -ao help lists oss, alsa, pulse, and jack, among others.  But here's the output of mplayer -ao help on the computer I'm trying to set up:

MPlayer SVN-r30131-snapshot-4.4.1 (C) 2000-2009 MPlayer Team
Available audio output drivers:
	oss	OSS/ioctl audio output
	mpegpes	DVB audio output
	v4l2	V4L2 MPEG Audio Decoder output
	null	Null audio output
	pcm	RAW PCM/WAVE file writer audio output

ALSA and pulse are both installed, and pulse is running -- ps -A | grep pulse gives:

 3627 ?        00:00:00 pulseaudio

Yet, mplayer fails to realize this.  I'm sure I'm doing something wrong that's really simple...but what?

Thanks, everyone.

---

### Post by mc4man on 2010-01-04
It would appear that your mplayer (whether you built or someone/somewhere else) was built without pulse and alsa support 

libpulse-dev and libasound2-dev need to be installed prior to building

A rather complete list of build-deps for** karmic** is shown [here]("http://ubuntuforums.org/showthread.php?t=1305181")

---

### Post by matt90 on 2010-01-04
I went to the page you linked, and followed the instructions there to the letter.  Worked like a charm!  Thank you so much!

Why do I have to download and manually compile the source -- shouldn't using apt-get work as well?  (It didn't.)

---

