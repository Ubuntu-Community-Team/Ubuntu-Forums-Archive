---
title: "v4l2 &gt; vloopback &gt; v4l1 ?"
date: 2008-02-24
forum: Multimedia &amp; Video
---

### Post by deadite66 on 2008-02-24
i have a WinTV pvr usb2 which uses v4l2 and outputs a mpeg2 stream

```
Input #0, mpeg, from '/dev/video0':
  Duration: N/A, bitrate: 8224 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 384x288, 8000 kb/s, 25.00 fps(r)
  Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, 224 kb/s

```

i've tried googling around and found vloopback which i suspect could be half the battle

is thier a way to decode the mpeg2 stream then squirt that back into the vloopback input so i can capture the output in flash for ustream/stickam?

---

