---
title: "mythdvd transcode fails"
date: 2007-09-05
forum: Multimedia &amp; Video
---

### Post by pgcudahy on 2007-09-05
I've been trying to rip a dvd using mythdvd. It works fine on the "perfect" setting and I get a .vob file. When I try it on "good" everything goes well until its time to transcode, then the rip/transcode module exits to a "no jobs" screen. mtd.log only says "a client socket has been closed" and I don't know where the transcode program keeps its log. In mtd.log it also tells you the command it issued to "transcode", so I tried that from the command line and got ```
pgcudahy@Catalonia:~$ transcode -i /var/lib/mythtv/videos/MIAMI_VICE.vob -g 720x480 -f 0,1 -M 2 -V -y divx5 -o /var/lib/mythtv/videos/MIAMI_VICE.avi
*** WARNING: The option -V is deprecated. ***
*** Transcode internal frame handling is now in YV12 / YUV420 ***
*** format by default because most codecs can only handle this format, ***
*** otherwise leading to unnecessary time and quality wasting conversions. ***
*** If you want to have to "old" behaviour (RGB24 as internal format), ***
*** then please use the new -1/--use_rgb option ***
transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
[transcode] (probe) suggested AV correction -D 0 (0 ms) | AV 0 ms | 0 ms
[transcode] auto-probing source /var/lib/mythtv/videos/MIAMI_VICE.vob (ok)
[transcode] V: import format    | MPEG-2  (V=vob|A=vob)
[transcode] V: AV demux/sync    | (2) initial MPEG sequence / enforce frame rate
[transcode] V: import frame     | 720x480  1.50:1  encoded @ 16:9
[transcode] V: bits/pixel       | 0.217
[transcode] V: decoding fps,frc | 23.976,1
[transcode] V: Y'CbCr           | YV12/I420
[transcode] A: import format    | 0x2000  AC3          [48000,16,2]  448 kbps
[transcode] A: export format    | 0x55    MPEG layer-3 [48000,16,2]  128 kbps
[transcode] V: encoding fps,frc | 23.976,1
[transcode] A: bytes per frame  | 8008 (8008.000000)
[transcode] A: adjustment       | 0@1000
[transcode] V: IA32/AMD64 accel | sse (sse 3dnowext 3dnow mmxext mmx asm C)
tc_memcpy: using sse for memcpy
[transcode] V: video buffer     | 10 @ 720x480
[import_vob.so] v0.6.0 (2003-10-02) (video) MPEG-2 | (audio) MPEG/AC3/PCM | (subtitle)
[export_divx5.so] v0.1.8 (2003-07-24) (video) DivX 5.xx | (audio) MPEG/AC3/PCM
[import_vob.so] tccat -i "/var/lib/mythtv/videos/MIAMI_VICE.vob" -t vob -d 0 -S 0 | tcdemux -a 0 -x ac3 -S 0 -M 2 -d 0 | tcextract -t vob -a 0 -x ac3 -d 0 | tcdecode -x ac3 -d 0 -s 1.000000,1.000000,1.000000 -A 0
[import_vob.so] tccat -i "/var/lib/mythtv/videos/MIAMI_VICE.vob" -t vob -d 0 -S 0 | tcdemux -s 0x80 -x mpeg2 -S 0 -M 2 -f 23.976024 -P /tmp/fileyP5juC   -d 0 | tcextract -t vob -a 0 -x mpeg2 -d 0 | tcdecode -x mpeg2 -d 0 -y yv12
tc_memcpy: using sse for memcpy
tc_memcpy: using sse for memcpy
[decode_mpeg2.c] libmpeg2 0.4.0b loop decoder
[decode_mpeg2.c] libmpeg2 acceleration: 3dnow
[export_divx5.so] *** Warning: DivX is broken and support for it is ***
[export_divx5.so] *** obsolete in transcode. Sooner or later it  ***
[export_divx5.so] *** will be removed from transcode. Don't use ***
[export_divx5.so] *** DivX. Use xvid or ffmpeg -F mpeg4 instead ***
[export_divx5.so] *** for all your mpeg4 encodings. ***
[export_divx5.so] libdivxencore.so.0: cannot open shared object file: No such file or directory
[transcode] warning : failed to init DivX 5.0 Codec
[transcode] warning : (encoder.c) video export module error: init failed
[transcode] critical: failed to init encoder

```

Running "apt-cache search libdivxencore" returned "avifile-divx-plugin". I installed that but still get the same error.
Anyone have an idea of what do try next?

---

