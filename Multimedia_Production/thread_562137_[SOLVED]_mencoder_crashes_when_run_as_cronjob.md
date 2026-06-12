---
title: "[SOLVED] mencoder crashes when run as cronjob"
date: 2007-09-28
forum: Multimedia Production
---

### Post by Ossipon on 2007-09-28
I'm trying to record iptv and encode it using 2-pass x264 encoding. The script I use looks like this:
```

#!/bin/bash
TEMPFILE=`date +%V`

nice --10 mplayer udp://233.81.233.165:10302 -dumpstream -dumpfile "$TEMPFILE.mpg" &
MPID=$!
sleep 4000
kill -TERM $MPID
mencoder -nosound -ovc x264 -x264encopts pass=1:turbo=1:bframes=3 -noskip "$TEMPFILE.mpg" -o /dev/null
mencoder -oac copy -ovc x264 -x264encopts pass=2:bitrate=1800:subq=7:frameref=6:bframes=3:b_pyramid:qcomp=0.8:weight_b -vf yadif=0:0,scale=1024:576 -aspect 16:9 -noskip "$TEMPFILE.mpg" -o "$TEMPFILE.avi"
echo $?
exit 0

```

This script runs fine when I execute it manually, but it fails when I run it as a cronjob. The problem lies with the second encoding pass. Here is the output of the logfile:

```
Video stream:  476.029 kbit/s  (59503 B/s)  size: 461748 bytes  7.760 secs  196 frames
MEncoder 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3200+ (Family: 15, Model: 12, Stepping: 0)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x877000
TS file format detected.
VIDEO MPEG2(pid=1001) AUDIO MPA(pid=1002) NO SUBS (yet)!  PROGRAM N. 1
VIDEO:  MPEG2  720x576  (aspect 2)  25.000 fps  15000.0 kbps (1875.0 kbyte/s)
[V] filefmt:29  fourcc:0x10000002  size:720x576  fps:25.00  ftime:=0.0400
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 256.0 kbit/16.67% (ratio: 32000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [scale w=1024 h=576]
Opening video filter: [yadif=0:0]
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
141

```

It doesn't really say what went wrong, also, mencoder seems to exit with exit status 141, however I can't find what that means anywhere.
Oddly enough, the first encoding works just fine.

---

### Post by Ossipon on 2007-11-04
This seems to have been fixed in gutsy:)

---

