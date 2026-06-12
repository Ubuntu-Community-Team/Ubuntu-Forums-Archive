---
title: "Generic MP5 Player plays AVI video problem"
date: 2009-02-17
forum: Multimedia Software
---

### Post by kdavies on 2009-02-17
Hi

I have a generic MP4 player that plays avi format video.

I would like to be able to convert flv files to play in avi format.

I am not well versed in video conversion.

I use Ubuntu 8.04. Video codecs from media ubuntu.

There is a sample video file called avi.avi

I have run this through avidemux copy with resulting file plays on player.

I have tried to run this trough avidemux with settings for conversion to Mpeg-4 ASP (Xvid)

Does not play on player.

Output from ffmpeg:
ffmpeg -i avi.avi
Input #0, avi, from 'avi.avi':
  Duration: 00:00:54.3, start: 0.000000, bitrate: 750 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 320x240, 20.00 fps(r)
  Stream #0.1: Audio: mp2, 44100 Hz, stereo, 128 kb/s
Must supply at least one output file

Output from conversion:Input #0, avi, from 'avidemuxavi.avi':
  Duration: 00:00:54.3, start: 0.000000, bitrate: 747 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 320x240, 20.00 fps(r)
  Stream #0.1: Audio: mp2, 44100 Hz, stereo, 128 kb/s

Are their other settings I should adjust or other software available?

---

