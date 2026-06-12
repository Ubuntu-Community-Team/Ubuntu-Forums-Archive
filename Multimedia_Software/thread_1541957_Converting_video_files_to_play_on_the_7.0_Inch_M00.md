---
title: "Converting video files to play on the 7.0 Inch M001 Google Android tablet"
date: 2010-07-29
forum: Multimedia Software
---

### Post by thomas_toscani on 2010-07-29
I'm talking about this one:

[http://tinyurl.com/38a99fk](http://tinyurl.com/38a99fk)

The player's CPU is underpowered, and in any case will only play mp4 video files.  I've had no luck with trying to get it to play xvid encoded avi files.

Your best chance to get a movie to play on this device is to download Avidemux (available for both Linux and Windows), and convert the file using the following settings:

Video: MPEG-4 ASP (lavc)

Filter: Resize to half size.  312x176 works.

Audio: AAC (Faac)

Format: MP4 (PSP)

The format should be correct, and the resize makes sure that the CPU can handle the video.

Good luck.

---

