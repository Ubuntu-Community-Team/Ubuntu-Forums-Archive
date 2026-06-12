---
title: "Problem with dvdrip (makes no progress at 0%)"
date: 2009-02-08
forum: Multimedia Software
---

### Post by altonbr on 2009-02-08
Using dvdrip in Intrepid and Jaunty, I am having problems backing up one of my movies.

I "ripped the title" (as it's called) and then tried to transcode it using it's default settings (xvid, double pass 2x700MB, ac3 audio) but it didn't seem to make any progress.

I saw in the log that there was a certain command it was running, so I tried it myself and got the same result. It gets stuck on > (ac3scan.c) AC3 frame 1024 (1068) bytes | bitrate 256 kBits/s | depsize 6408 | rbytes 1068.000000

```
$ mkdir -m 0775 -p '/home/brett/dump/scarce/tmp' && cd /home/brett/dump/scarce/tmp && mkdir -p /home/brett/dump/scarce/avi/001 && execflow -n 19 transcode -H 10 -a 0 -x vob -i \/home\/brett\/dump\/scarce\/vob\/001\/ -w 1295,50 -A -N 0x2000 -f 30,4 -M 2 -Y 58,4,62,4 -B 1,11,8 -R 1 -y xvid,null --psu_mode --nav_seek /home/brett/dump/scarce/tmp/scarce-001-nav.log --no_split  -o /dev/null --print_status 25 && echo EXECFLOW_OK
EXEC_FLOW_JOB_PID=14191
transcode v1.0.7 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg, 2004-2008 Transcode Team
[transcode] (probe) suggested AV correction -D 14 (467 ms) | AV 482 ms | 15 ms
[transcode] auto-probing source /home/brett/dump/scarce/vob/001/ (ok)
[transcode] V: import format    | MPEG-2  (V=vob|A=vob)
[transcode] V: AV demux/sync    | (2) initial MPEG sequence / enforce frame rate
[transcode] V: import frame     | 720x480  1.50:1  encoded @ 4:3
[transcode] V: new aspect ratio | 632x472  1.34:1 (-B)
[transcode] V: clip frame (->)  | 624x352
[transcode] V: bits/pixel       | 0.197
[transcode] V: decoding fps,frc | 29.970,4
[transcode] V: multi-pass       | (mode=1) writing data (pass 1) to divx4.log
[transcode] V: Y'CbCr           | YV12/I420
[transcode] A: import format    | 0x2000  AC3          [48000,16,2]  256 kbps
[transcode] A: export           | disabled
[transcode] V: encoding fps,frc | 29.970,4
[transcode] A: bytes per frame  | 6408 (6406.400000)
[transcode] A: adjustment       | -1600@1000
[transcode] V: IA32/AMD64 accel | sse2 (sse2 sse mmxext mmx asm C)
[transcode] V: IA32/AMD64 accel | using sse memcpy
[transcode] V: video buffer     | 10 @ 720x480
[import_vob.so] v0.6.0 (2003-10-02) (video) MPEG-2 | (audio) MPEG/AC3/PCM | (subtitle)
[export_null.so] v0.1.2 (2001-08-17) (video) null | (audio) null
[export_xvid4.so] v0.0.6 (2007-08-11) (video) XviD 1.0.x series (aka API 4.0) | (audio) MPEG/AC3/PCM
[export_xvid4.so] Neither './xvid4.cfg' nor '~/.transcode/xvid4.cfg'
[export_xvid4.so] found. Default settings will be used instead.
(split.c) reading auto-split information from file "/home/brett/dump/scarce/tmp/scarce-001-nav.log"
(split.c) done reading 177405 entries
(split.c) chunk 0/0 PU=0 (-L 0 -c 840-210) mapped onto (-L 9858 -c 1--629)
skipping PSU 0 with -630 frame(s)
(split.c) reading auto-split information from file "/home/brett/dump/scarce/tmp/scarce-001-nav.log"
(split.c) done reading 177405 entries
(split.c) chunk 0/0 PU=1 (-L 0 -c 255-375) mapped onto (-L 13578 -c 1-121)
[import_vob.so] tccat -i "/home/brett/dump/scarce/vob/001/" -t vob -d 0 -S 13578 | tcdemux -a 0 -x ac3 -S 0,0-122 -M 2 -d 0 | tcextract -t vob -a 0 -x ac3 -d 0 | tcextract -t raw -x ac3 -d 0
[import_vob.so] tccat -i "/home/brett/dump/scarce/vob/001/" -t vob -d 0 -S 13578 | tcdemux -s 0x80 -x mpeg2 -S 0,0-122 -M 2 -f 29.970030 -P /tmp/fileSKSQ3w   -d 0 | tcextract -t vob -a 0 -x mpeg2 -d 0 | tcdecode -x mpeg2 -d 0 -y yv12
(demuxer.c) seeking to sequence 0:0 ...
[decode_mpeg2.c] libmpeg2 acceleration: none (plain C)(demuxer.c) seeking to sequence 0:0 ...
(ac3scan.c) AC3 frame 1024 (1068) bytes | bitrate 256 kBits/s | depsize 6408 | rbytes 1068.000000
```

Does anyone know what's going wrong here? Any suggestions?

---

### Post by mgolden on 2009-02-19
I ran into this problem as well.  I am very far from knowing what I am doing with this, but when you leave off the --psu_mode flag from the transcode at least it doesn't hang.  Maybe someone else can tell us what we need to do.

---

