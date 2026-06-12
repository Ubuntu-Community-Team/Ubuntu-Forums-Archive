---
title: "Mplayer fails to play back some mp4 h264"
date: 2011-03-13
forum: Multimedia Software
---

### Post by Loser777 on 2011-03-13
I currently have mplayer installed with the binary codecs in place, but it seems that mplayer is quite picky with which files it wants to play. 

I have three files that are all mp4 h264 .mkv's. One of them is ~20 minutes long (720p) and mplayer seems to do just fine. Another is around ~90 minutes (1080p) and within seconds the audio gets out of sync. The third file is also around ~90 minutes long (1080p) and refuses to play at all, throwing a mess of:

[h264 @ 0x5fdbac0]AVC: Consumed only 1 bytes instead of 521

Error while decoding frame!

The machine is fairly old (Athlon 64 X2 4200+), but I don't think it's a hardware performance issue. When it was running Windows XP it could handle any HD video I threw at it. Each one of these files plays perfectly on my Windows machine with Media Player Classic Home Cinema + ffmpeg...

Is there something wrong with ffmpeg or is support for h264 just not there yet?

---

### Post by babarosa on 2011-03-14
I use these versions of mplayer and mencoder:
[https://launchpad.net/~motumedia/+archive/mplayer-daily?field.series_filter=](https://launchpad.net/~motumedia/+archive/mplayer-daily?field.series_filter=)

and this of ffmpeg:
[https://launchpad.net/~motumedia/+archive/ffmpeg-daily?field.series_filter=](https://launchpad.net/~motumedia/+archive/ffmpeg-daily?field.series_filter=)

On my machine, they work very fine - maybe on your's too.

---

