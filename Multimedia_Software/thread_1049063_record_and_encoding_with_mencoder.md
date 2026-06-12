---
title: "record and encoding with mencoder"
date: 2009-01-24
forum: Multimedia Software
---

### Post by davidtuti on 2009-01-24
Hi,

I would like to record tv signal and if it's possible encoding the signal at the sime time to reduce the file size.

I try the script in this url:
[http://ubuntuforums.org/showthread.php?t=606993](http://ubuntuforums.org/showthread.php?t=606993)

But doesn't works 

 ```
david@defekas:~$ ./p.sh 30 laSexta k
MEncoder 2:1.0~rc2-0ubuntu17 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU          6420  @ 2.13GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: unable to open '/dev/video0': No such file or directory
v4l2: ioctl set mute failed: Bad file descriptor
v4l2: 0 frames successfully processed, 0 frames dropped.
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.
```

---

