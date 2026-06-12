---
title: "ffmpeg using variable bit rate , how do you do it!"
date: 2013-01-13
forum: Multimedia Software
---

### Post by sdowney717 on 2013-01-13
I have no idea. I did a lot of googling and lots of talk about what it is in ffmpeg and not much examples. Lots of people wanted to use cbr and examples for that were given.
I want VBR on my encodes.

Here is what I have for encoding from inside kdenlive.

This does 3000 bit something, I have no idea if it is variable or constant.

The line vb=3000k sets a bit rate.

f=mp4 hq=1 acodec=aac ab=%audiobitrate+'k' ar=48000 pix_fmt=yuv420p vcodec=libx264 minrate=0 vb=3000k g=250 bf=3 b_strategy=1 subcmp=2 cmp=2 coder=1 flags=+loop flags2=dct8x8 qmax=51 subq=7 qmin=10 qcomp=0.6 qdiff=4 trellis=1 aspect=%dar pass=%passes movflags=faststart

---

### Post by evilsoup on 2013-01-14
Use [Constant Rate Factor](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide#crf) for the x264 video.  The native AAC encoder does not support a VBR/quality-based mode, but both libfaac and libfdk_aac (use the latter if you have it) do - see the [AAC Encoding Guide](https://ffmpeg.org/trac/ffmpeg/wiki/AACEncodingGuide).

---

