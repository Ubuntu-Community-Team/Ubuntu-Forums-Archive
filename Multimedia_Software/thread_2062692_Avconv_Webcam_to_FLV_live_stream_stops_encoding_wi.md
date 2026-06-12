---
title: "Avconv: Webcam to FLV live stream stops encoding with starting :S"
date: 2012-09-25
forum: Multimedia Software
---

### Post by Fenlig on 2012-09-25
**My command:**
```
sudo avconv -f video4linux2 -i /dev/video0 -r 25 -pix_fmt yuv420p -bt 512k -f flv http://localhost:8090/feed1.flv
```[B]Output:
[/B]```
avconv version 0.8.2-6:0.8.2-1+rpi1+b1, Copyright (c) 2000-2011 the Libav developers
  built on Jun 27 2012 01:07:05 with gcc 4.6.3
[video4linux2 @ 0x111b2e0] Estimating duration from bitrate, this may be inaccurate
Input #0, video4linux2, from '/dev/video0':
  Duration: N/A, start: 6373.829146, bitrate: 147456 kb/s
    Stream #0.0: Video: rawvideo, yuyv422, 640x480, 147456 kb/s, 30 tbr, 1000k tbn, 30 tbc
[buffer @ 0x111d000] w:640 h:480 pixfmt:yuyv422
[avsink @ 0x111c900] auto-inserting filter 'auto-inserted scaler 0' between the filter 'src' and the filter 'out'
[scale @ 0x11109e0] w:640 h:480 fmt:yuyv422 -> w:640 h:480 fmt:yuv420p flags:0x4
Output #0, flv, to 'http://localhost:8090/feed1.flv':
  Metadata:
    encoder         : Lavf53.21.0
    Stream #0.0: Video: flv, yuv420p, 640x480, q=2-31, 200 kb/s, 1k tbn, 25 tbc
Stream mapping:
  Stream #0:0 -> #0:0 (rawvideo -> flv)
Press ctrl-c to stop encoding

```So when i run the command it just passes through instantly without actually streaming.

Anyone have any Ideas?

---

