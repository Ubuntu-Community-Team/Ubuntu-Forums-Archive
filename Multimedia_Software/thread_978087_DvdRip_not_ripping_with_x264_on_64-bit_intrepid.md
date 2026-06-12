---
title: "Dvd::Rip not ripping with x264 on 64-bit intrepid"
date: 2008-11-10
forum: Multimedia Software
---

### Post by reeseslover531 on 2008-11-10
So I have been ripping DVDs for a while on Hardy using DVD::Rip and the ffmpeg x264 codec.  But now that I have installed intrepid, everytime I try to rip something I get a broken pipe error.  I attached a log file, it really makes no sense to me.  Does anyone have any idea?

Thanks so much!

---

### Post by reeseslover531 on 2008-11-11
anyone?

---

### Post by scarf on 2009-01-09
i get the same error.

if i try to type the "Command" on the terminal, some more info pops up, which i hope might be useful in resolving this problem (i removed some long directory names, etc. and replaced with <snip>):

```

$ mkdir -m 0775 -p '<snip>' && cd <snip> && mkdir -p <snip> && execflow -n 19 transcode -H 10 -a 0 -x vob -i <snip> -w 1094,50 -F h264 -A -N 0x2000 --use_rgb -k  -J smartyuv=threshold=10:Blend=1:diffmode=2:highq=1 -f 30,4 -M 2 -Y 5,4,5,4 -Z 504x378 -y ffmpeg -o <snip> --print_status 25 && echo EXECFLOW_OK
EXEC_FLOW_JOB_PID=23138
transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
[transcode] (probe) suggested AV correction -D 1 (33 ms) | AV 66 ms | 33 ms
[transcode] auto-probing source <snip> (ok)
[transcode] V: import format    | MPEG-2  (V=vob|A=vob)
[transcode] V: AV demux/sync    | (2) initial MPEG sequence / enforce frame rate
[transcode] V: import frame     | 352x240  1.47:1  encoded @ 4:3
[transcode] V: zoom             | 504x378  1.33:1 (Lanczos3)
[transcode] V: clip frame (->)  | 496x368
[transcode] V: rgb2bgr          | yes
[transcode] V: bits/pixel       | 0.200
[transcode] V: decoding fps,frc | 29.970,4
[transcode] A: import format    | 0x2000  AC3          [48000,16,2]  128 kbps
[transcode] A: export format    | 0x2000  AC3          [48000,16,2]  128 kbps
[transcode] V: encoding fps,frc | 29.970,4
[transcode] A: bytes per frame  | 6408 (6406.400000)
[transcode] A: adjustment       | -1600@1000
[transcode] V: IA32/AMD64 accel | sse3 (sse3 sse2 sse 3dnowext 3dnow mmxext mmx asm C)
tc_memcpy: using amd64 for memcpy
[transcode] V: video buffer     | 10 @ 504x378
[import_vob.so] v0.6.0 (2003-10-02) (video) MPEG-2 | (audio) MPEG/AC3/PCM | (subtitle)
[transcode] warning : [filter_smartyuv.so] This filter is only capable of YUV mode
[transcode] warning : filter plugin 'smartyuv' returned error - plugin skipped
[export_ffmpeg.so] v0.3.13 (2004-08-03) (video) Lavc51.50.0 | (audio) MPEG/AC3/PCM
[import_vob.so] tccat -i "<snip>" -t vob -d 0 -S 0 | tcdemux -a 0 -x ac3 -S 0 -M 2 -d 0 | tcextract -t vob -a 0 -x ac3 -d 0 | tcextract -t raw -x ac3 -d 0
[import_vob.so] tccat -i "<snip>" -t vob -d 0 -S 0 | tcdemux -s 0x80 -x mpeg2 -S 0 -M 2 -f 29.970030 -P /tmp/filefGJrih   -d 0 | tcextract -t vob -a 0 -x mpeg2 -d 0 | tcdecode -x mpeg2 -d 0
tc_memcpy: using amd64 for memcpy
tc_memcpy: using amd64 for memcpy
tc_memcpy: using amd64 for memcpy
[decode_mpeg2.c] libmpeg2 0.4.0b loop decoder
[decode_mpeg2.c] libmpeg2 acceleration: none (plain C)
(ac3scan.c) AC3 frame 512 (534) bytes | bitrate 128 kBits/s | depsize 6408 | rbytes 534.000000
[export_ffmpeg.so] Could not find a FFMPEG codec for 'h264'.
[transcode] warning : (encoder.c) video export module error: init failed
[transcode] critical: failed to init encoder
$

```

---

### Post by m0rtal on 2009-01-18
I have same error on 32-bit system.
No solution so far :(

---

### Post by raize221 on 2009-01-20
I've been having this same problem too. I'm using 32-bit Intrepid. Only seems to affect the h264 codec, other choices encode just fine for me. Seems odd because it always worked fine for me on Hardy.

Might be useful to note that I run my encodes as a cluster. I haven't tried this without the cluster control. I have attached the log.

Anyway, guess I'll be using xvid for now... :(

---

