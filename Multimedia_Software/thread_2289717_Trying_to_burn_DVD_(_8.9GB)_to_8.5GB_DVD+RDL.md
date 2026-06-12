---
title: "Trying to burn DVD ( 8.9GB) to 8.5GB DVD+RDL"
date: 2015-08-06
forum: Multimedia Software
---

### Post by Dyffo on 2015-08-06
I have a downloaded Video file mpg of the Grand Prix in Hungary. The file size is 8.9GB.
How can I either split this to burn to two DVD'S or edit to reduce the size.
I have tried burning using K3b, Brasseiro and DeVeD - each time it says the file is too large for the DVD even including overburn.

---

### Post by TheFu on 2015-08-06
Transcode the file down to the size you require. ffmpeg, avconv both can do that.

If you don't need MPEG2 video, h.264 video would be much smaller for the same visual outcome - probably about 2G. Use **handbrake** to do that. Handbrake will output either an h.264/aac/mp4 file or h.264/aac/mkv file. Both of these are widely supported by web browsers worldwide on pretty much every platform. However, they will NOT play in a DVD player.  DVD players want MPEG2 in a VOB layout.

There are other audio formats which may be better for non-DVD players too, but AAC is the most supported these days.

---

### Post by Dyffo on 2015-08-08
Hi , thanks for response - however this is the problem:-

[COLOR="#FF0000"]they will NOT play in a DVD player. DVD players want MPEG2 in a VOB layout.[/COLOR]

so my solution has been to re-download the file in Avi format - this reduces the size to just over 7GB, well within the limits of dual layer disk, and burn as a data file.

This will be played on an LG DR389 player which will accept these criteria - I hope !! - so just off to get a disc and try it out.

---

