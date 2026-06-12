---
title: "WinFF to convert MTS MPEG4 HD 1080p 30fps full bitrate"
date: 2010-10-01
forum: Multimedia Software
---

### Post by webdevelopment on 2010-10-01
I'm trying to use WinFF to convert a Sony MTS MPEG4 to a non-proprietary MPEG4 with the same bitrate, pixels, fps, audio.  Just the same video in a non-proprietary format.

WinFF works great once the Medibuntu codecs are loaded (don't forget this) but doesn't come loaded with full HD presets.

Here is the MPEG4 preset in WinFF.

> <?xml version="1.0"?>
<presets>
  <x264HQWS>
    <label>MP4 Widescreen</label>
    <params>-f mp4 -r 29.97 -vcodec libx264 -s 704x384 -b 1000kb  -aspect 16:9 -flags +loop -cmp +chroma -deblockalpha 0 -deblockbeta 0 -b  1250k -maxrate 1500k -bufsize 4M -bt 256k -refs 1 -bf 3 -coder 1  -me_method umh -me_range 16 -subq 7 -partitions  +parti4x4+parti8x8+partp8x8+partb8x8 -g 250 -keyint_min 25 -level 30  -qmin 10 -qmax 51 -qcomp 0.6 -trellis 2 -sc_threshold 40 -i_qfactor 0.71  -acodec libfaac -ab 112kb -ar 48000 -ac 2</params>
    <extension>mp4</extension>
    <category>MPEG4</category>
  </x264HQWS>
</presets>Where can I find one that is for 1080p HD MPEG4?  Or how can I just edit this to be the same as the source in quality?

---

