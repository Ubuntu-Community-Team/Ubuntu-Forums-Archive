---
title: "A/V sync problems when encoding videos"
date: 2009-06-30
forum: Multimedia Software
---

### Post by varan on 2009-06-30
I have a videos made with Canon digital camera. I want to re-encode them using h264 for smaller size (using mencoder). The trouble that I've ran into is A/V sync. If I simply copy audio stream along with re-encoding video, its fine. So far i've tried FAAC and MP3LAME codecs and both have sync problems. I believe it has to do with a weird audio rate that original video has.

Here's the info on original video:
VIDEO:  [MJPG]  640x480  24bpp  30.000 fps  14950.9 kbps (1825.1 kbyte/s)
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 11024 Hz, 1 ch, u8, 88.2 kbit/100.00% (ratio: 11024->11024)


The command i used is:
mencoder mvi_4999.avi -o 2009.06.11-mvi_4999.avi -oac faac -faacopts quality=80 -ovc x264 -x264encopts crf=23:subq=4:bframes=2:b_pyramid:weight_b -endpos 00:00:20

The output has A/V sync problem.

THen, I also tried mp3lame, the command is the same, except the audio codec part is like this:
-oac mp3lame -lameopts vbr=2:q=5

Mencoder complains:
Cannot set LAME options, check bitrate/samplerate, some very low bitrates
(<32) need lower samplerates (i.e. -srate 8000).

So, if I add -srate 11024 to the above command, it proceeds, but the resulting output has A/V sync problems.

Anybody has any ideas how to fix this?
thx

---

