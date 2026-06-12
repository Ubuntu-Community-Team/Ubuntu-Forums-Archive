---
title: "problem transcoding with dvd::rip"
date: 2009-05-05
forum: Multimedia Software
---

### Post by ledererster on 2009-05-05
I am using dvd::rip to rip a dvd.
I successfully ripped the title that I want but when I try to transcode it, I get this error:
```
Job 'Transcode video - title #1, pass 1' failed with error message:
Command exits with failure code:
Command: mkdir -m 0775 -p '/home/justin/dvdrip-data/producers/tmp' && cd /home/justin/dvdrip-data/producers/tmp && mkdir -p /home/justin/dvdrip-data/producers/avi/001 && execflow -n 19 transcode -H 10 -a 0 -x vob -i \/home\/justin\/dvdrip\-data\/producers\/vob\/001\/ -w 588,50 -b 128,0,2 -s 1.653 --a52_drc_off -f 24,1 -M 2 -Y 52,0,52,0 -B 15,10,8 -R 1 -y xvid,null --psu_mode --nav_seek /home/justin/dvdrip-data/producers/tmp/producers-001-nav.log --no_split  -o /dev/null --print_status 25 && echo EXECFLOW_OK

Output: transcode v1.0.7 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg, 2004-2008 Transcode Team
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Couldn't find device name.
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
[import_vob.so] v0.6.0 (2003-10-02) (video) MPEG-2 | (audio) MPEG/AC3/PCM | (subtitle)
[export_null.so] v0.1.2 (2001-08-17) (video) null | (audio) null
[export_xvid4.so] v0.0.6 (2007-08-11) (video) XviD 1.0.x series (aka API 4.0) | (audio) MPEG/AC3/PCM
[export_xvid4.so] No libxvidcore API4 found
[transcode] warning : (encoder.c) video export module error: init failed
[transcode] (probe) suggested AV correction -D 0 (0 ms) | AV 0 ms | 0 ms
[transcode] auto-probing source /home/justin/dvdrip-data/producers/vob/001/ (ok)
[transcode] V: import format    | MPEG-2  (V=vob|A=vob)
[transcode] V: AV demux/sync    | (2) initial MPEG sequence / enforce frame rate
[transcode] V: import frame     | 720x480  1.50:1  encoded @ 16:9
[transcode] V: new aspect ratio | 640x360  1.78:1 (-B)
[transcode] V: clip frame (->)  | 640x256
[transcode] V: bits/pixel       | 0.150 (low)
[transcode] V: decoding fps,frc | 23.976,1
[transcode] V: multi-pass       | (mode=1) writing data (pass 1) to divx4.log
[transcode] V: Y'CbCr           | YV12/I420
[transcode] A: import format    | 0x2000  AC3          [48000,16,2]  448 kbps
[transcode] A: export           | disabled
[transcode] V: encoding fps,frc | 23.976,1
[transcode] A: bytes per frame  | 8008 (8008.000000)
[transcode] A: adjustment       | 0@1000
[transcode] A: rescale stream   | 1.653
[transcode] V: IA32/AMD64 accel | sse2 (sse2 sse mmxext mmx asm C)
[transcode] V: IA32/AMD64 accel | using sse memcpy
[transcode] V: video buffer     | 10 @ 720x480
[transcode] critical: failed to init encoder

--------------------------------------------------------------------------------

```

Anybody know what's going on?

---

### Post by disturbed1 on 2009-05-05
[U][I][B]export_xvid4.so] No libxvidcore API4 found
[transcode] warning : (encoder.c) video export module error: init failed
[/B][/I][I][B][transcode] critical: failed to init encoder


[/B][/I][/U]

---

### Post by ledererster on 2009-05-05
What do I need to do to fix that?

---

### Post by disturbed1 on 2009-05-05
[U][I][B]libxvidcore :confused:

[/B][/I][/U]Your error log states you are missing libxvidcore. Therefore I would deduce perhaps installing libxvidcore might solve the problem.

Try doing a search with apt, aptitude, packages.ubuntu.com, or synaptic for libxvidcore.

---

### Post by mc4man on 2009-05-05
Try installing libxvidcore4 and possibly xvid4conf (in synaptic or here

[http://packages.ubuntu.com/jaunty/libxvidcore4](http://packages.ubuntu.com/jaunty/libxvidcore4)

[http://packages.ubuntu.com/jaunty/xvid4conf](http://packages.ubuntu.com/jaunty/xvid4conf)

I'm using 1.1.2 so don't exactly know about the jaunty version - at some point in 1.xx xvid needed to be enabled in the build, can't imagine they didn't do so if needed for repo version (can ck. the jaunty rules file if above doesn't help


Edit : you should be ok, the 1.0.x versions don't need xvid configured in, 1.1.x do

---

