---
title: "Converting DV (from miniDV) to MP4/H.264"
date: 2009-01-04
forum: Multimedia Software
---

### Post by rgrimard on 2009-01-04
I have a stack of miniDVs I'd like to put onto a NAS for future use.  A friend has suggested converting to MP4(H.264).  After some research, it seems this is the way to go.  I've tried using both mencoder and ffmpeg with no success.

"mencoder input.dv -ovc x264 -oac pcm -of rawvideo -o stream.h264"
This fails perhaps due to an old command I've found on the web.  It complains about the ratecontrol method not being specified.  I am going to look into this next.

As for ffmpeg, there are many sample commands on the web but none that seem to fit my need.  The closest (I think) convert to H.264 for iPod and PSP.  If I fail to find the right options for mencoder, I will start reading up on the ffmpeg options.

My sample DV file spec is:
 Duration: 00:00:14.3, start: 0.000000, bitrate: 28771 kb/s
  Stream #0.0: Video: dvvideo, yuv411p, 720x480, 28771 kb/s, 29.97 fps(r)
  Stream #0.1: Audio: pcm_s16le, 32000 Hz, stereo, 1024 kb/s
  Stream #0.2: Audio: pcm_s16le, 32000 Hz, stereo, 1024 kb/s


Again, I simply want to convert from DV to something smaller and usable in the future for perhaps a media center or even just burning to DVD.

Any suggestions would be appreciated.

Thanks!

---

