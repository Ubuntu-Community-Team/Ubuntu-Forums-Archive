---
title: "codec for the most portability"
date: 2007-09-20
forum: Multimedia Production
---

### Post by kroiz on 2007-09-20
I am using DVD::rip to rip DVDs. 
With what video codec should I transcode so that the output file will be play on most DVD Players?

The options I get are:
divx4
divx5
xvid
xvid2
xvid3
xvid4
ffmpeg
fame
af6

---

### Post by orange2k on 2007-09-20
Older DVD players cannot play ANY of the formats you mentioned and most new DVD players can probably play ALL the formats on your list...
(not sure about ffmpeg, fame and af6)
If you want your videos to play on EVERY DVD player thats out there, including the old ones, then you should probably encode to SVCD format...

---

### Post by kroiz on 2007-09-20
when I use divx5 I get:
> Job 'Transcode video - title #1, pass 1' failed with error message:
Command exits with failure code:
Command: mkdir -m 0775 -p '/home/kroiz/dvdrip/db/Three/tmp' && cd /home/kroiz/dvdrip/db/Three/tmp && mkdir -p /home/kroiz/dvdrip/db/Three/avi/001 && execflow -n 19 transcode -H 10 -a 1 -x vob,null -i \/home\/kroiz\/dvdrip\/db\/Three\/vob\/001\/ -w 2877,50 -b 128,0,2 -s 3.090 --a52_drc_off -f 25.000 -Y 4,0,4,0 -B 27,10,8 -R 1 -y divx5,null -o /dev/null --print_status 25 && echo EXECFLOW_OK

Output: transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
tc_memcpy: using sse for memcpy
[transcode] (probe) suggested AV correction -D 0 (0 ms) | AV 0 ms | 0 ms
[transcode] auto-probing source /home/kroiz/dvdrip/db/Three/vob/001/ (ok)
[transcode] V: import format    | MPEG-2  (V=vob|A=null)
[transcode] V: AV demux/sync    | (1) sync AV at initial MPEG sequence
[transcode] V: import frame     | 720x576  1.25:1  encoded @ 16:9
[transcode] V: new aspect ratio | 640x360  1.78:1 (-B)
[transcode] V: clip frame (->)  | 640x352
[transcode] V: bits/pixel       | 0.511
[transcode] V: decoding fps,frc | 25.000,0
[transcode] V: multi-pass       | (mode=1) writing data (pass 1) to divx4.log
[transcode] V: Y'CbCr           | YV12/I420
[transcode] A: import format    | 0x2000  AC3          [48000,16,2]  384 kbps
[transcode] A: export           | disabled
[transcode] V: encoding fps,frc | 25.000,3
[transcode] A: bytes per frame  | 7680 (7680.000000)
[transcode] A: adjustment       | 0@1000
[transcode] A: rescale stream   | 3.090
[transcode] V: IA32/AMD64 accel | sse2 (sse2 sse mmxext mmx asm C)
[transcode] V: v[import_null.so] v0.2.0 (2002-01-19) (video) null | (audio) null
[import_vob.so] v0.6.0 (2003-10-02) (video) MPEG-2 | (audio) MPEG/AC3/PCM | (subtitle)
[export_null.so] v0.1.2 (2001-08-17) (video) null | (audio) null
[export_divx5.so] v0.1.8 (2003-07-24) (video) DivX 5.xx | (audio) MPEG/AC3/PCM
[export_divx5.so] *** Warning: DivX is broken and support for it is ***
[export_divx5.so] *** obsolete in transcode. Sooner or later it  ***
[export_divx5.so] *** will be removed from transcode. Don't use ***
[export_divx5.so] *** DivX. Use xvid or ffmpeg -F mpeg4 instead ***
[export_divx5.so] *** for all your mpeg4 encodings. ***
tc_memcpy: using sse for memcpy
[[COLOR=Red]export_divx5.so] libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory[/COLOR]
[transcode] warning : failed to init DivX 5.0 Codec
ideo buffer     | 10 @ 720x576
[import_vob.so] tccat -i "/home/kroiz/dvdrip/db/Three/vob/001/" -t vob -d 0 -S 0 | tcdemux -s 0x81 -x mpeg2 -S 0 -M 1 -d 0 | tcextract -t vob -a 0 -x mpeg2 -d 0 | tcdecode -x mpeg2 -d 0 -y yv12
[transcode] warning : (encoder.c) video export module error: init failed
[transcode] critical: failed to init encoder
[decode_mpeg2.c] libmpeg2 0.4.0b loop decoder
[decode_mpeg2.c] libmpeg2 acceleration: mmxext
failed to write Y plane of frame(demuxer.c) write program stream packet: Broken pipe

--------------------------------------------------------------------------------
I tried to locate the file libstdc++-libc6.2-2.so.3
but the closest I found is:

/usr/lib/libapt-inst-libc6.4-6.so.1.1
/usr/lib/libapt-inst-libc6.4-6.so.1.1.0
/usr/lib/libapt-pkg-libc6.4-6.so.3.53
/usr/lib/libapt-pkg-libc6.4-6.so.3.53.0

---

