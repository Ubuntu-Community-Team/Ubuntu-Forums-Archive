---
title: "MTS to AVI converter for ubuntu?"
date: 2010-09-17
forum: Multimedia Software
---

### Post by webdevelopment on 2010-09-17
i'm looking for a MTS to AVI converter for ubuntu 9.04

MTS is a sony format (from a sony hd video camera) that is similar to AVI but playback is jumpy so i need to convert it to AVI first...

WinFF tries to convert it but gives a "Unknown encoder 'libmp3lame'" error:

Input #0, mpegts, from '/home/admin1/Pictures/AVCHD/BDMV/STREAM/00000.MTS':
  Duration: 00:04:56.32, start: 1.000067, bitrate: 17173 kb/s
  Program 1 
    Stream #0.0[0x1011]: Video: h264, yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], 59.94 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x1100]: Audio: ac3, 48000 Hz, stereo, s16, 256 kb/s
Unknown encoder 'libmp3lame'
Press Enter to Continue

---

### Post by webdevelopment on 2010-09-17
solution was to download winff then install the medibuntu codecs

---

