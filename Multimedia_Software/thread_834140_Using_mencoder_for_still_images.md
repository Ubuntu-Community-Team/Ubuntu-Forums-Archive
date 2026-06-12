---
title: "Using mencoder for still images"
date: 2008-06-19
forum: Multimedia Software
---

### Post by secretservgy on 2008-06-19
Hello, I'm trying to make a 'movie' of these frames from a lightning storm. 

```
root@ubuntuBoxx:~/peppers/lightning# mencoder 0003.jpeg 0004.jpeg 0005.jpeg 0006.jpeg 0007.jpeg 0006.jpeg 0005.jpeg 0004.jpeg 0003.jpeg -mf fps=.8 -o output.avi -ovc lavc -lavcopts vcodec=mpeg4
MEncoder 2:1.0~rc2-0ubuntu13 (C) 2000-2007 MPlayer Team
CPU: Mobile AMD Athlon(tm) 64 Processor 3700+ (Family: 15, Model: 36, Stepping: 2)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0xa4d7
libavformat file format detected.
[mp3 @ 0x86f0c54]Could not find codec parameters (Audio: mp1, 32 kb/s)
LAVF_header: av_find_stream_info() failed
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

Exiting...
```

How can I get it to work, I know I can use (and tried) mf://*.jpeg - but I want all the photos and then all of them reveresed as I printed out above. Any ideas?

---

### Post by eye208 on 2008-06-19
You can do that with Blender. See [here](http://wiki.blender.org/index.php/Manual/VSE_Examples) how to make a slideshow from an image sequence. You can reverse the frame order of the image sequence by clicking "Reverse Frames" in the strip properties (see [here](http://wiki.blender.org/index.php/Manual/Using_VSE#Strip_Properties)).

---

