---
title: "Encoding H264 with ffmpeg for Nokia N73/N80?"
date: 2007-01-28
forum: Multimedia &amp; Video
---

### Post by Scraplab on 2007-01-28
Has anyone worked out how to convert to H264 video for the Nokia N73/N80? They both support H264, but I can only make the audio play back - the video just refuses to play. I've been using ffmpeg, doing the following:

ffmpeg -y -i input.avi -v 1 -vcodec h264 -b 175 -s 320x240 -aspect 4:3 -r 15 -acodec aac -ab 96 -ar 48000 -ac 2 -f mp4 output.mp4

They play fine in mplayer on my desktop machine.

Any suggestions?

---

### Post by smooth_b on 2007-03-13
After reading the specs on the H73 I did not see where it supported H264. You can try to use mpeg4 as your video codec.


ffmpeg -y -i input.avi -v 1 -vcodec mpeg4 -b 175 -s 320x240 -aspect 4:3 -r 15 -acodec aac -ab 96 -ar 48000 -ac 2 -f mp4 output.mp4


That should do the trick.

---

### Post by Scraplab on 2007-03-13
Hi smooth_b,

It definitely does support H264. See [http://forum.nokia.com/devices/N73](http://forum.nokia.com/devices/N73) for more info.

---

