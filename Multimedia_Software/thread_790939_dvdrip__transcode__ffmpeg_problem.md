---
title: "dvd::rip / transcode / ffmpeg problem"
date: 2008-05-11
forum: Multimedia Software
---

### Post by rowan on 2008-05-11
Hit an odd error using dvd::rip and googling around hasn't helped. Has anyone seen this before?

```

rowan@mungbean:~/Videos/dvdrip/scarface/tmp$ transcode -u 4,2 -Y -5,0,-5,0 -s 4.043 -R 1 --use_rgb -w 9000,100 -k -i /home/rowan/Videos/dvdrip/scarface/vob/001/ -y ffmpeg,null -Z 320x138 --print_status 25 -F mpeg4 --a52_drc_off -j 74,0,70,6 -x vob,null -b 128,0,3 -a 0 -o /dev/null -H 10 -c 1200-1800 -f 25.000 -J extsub=1:70:0:0:0
transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
[transcode] (probe) suggested AV correction -D 7 (280 ms) | AV 304 ms | 24 ms
[transcode] auto-probing source /home/rowan/Videos/dvdrip/scarface/vob/001/ (ok)
[transcode] V: import format    | MPEG-2  (V=vob|A=null)
[transcode] V: AV demux/sync    | (1) sync AV at initial MPEG sequence
[transcode] V: import frame     | 720x576  1.25:1  encoded @ 16:9
[transcode] V: clip frame (<-)  | 714x432
[transcode] V: zoom             | 320x138  1.75:1 (Lanczos3)
[transcode] V: clip frame (->)  | 320x148
[transcode] V: rgb2bgr          | yes
[transcode] V: bits/pixel       | 7.601
[transcode] V: decoding fps,frc | 25.000,0
[transcode] V: multi-pass       | (mode=1) writing data (pass 1) to divx4.log
[transcode] A: import format    | 0x2000  AC3          [48000,16,2]  384 kbps
[transcode] A: export           | disabled
[transcode] V: encoding fps,frc | 25.000,3
[transcode] A: bytes per frame  | 7680 (7680.000000)
[transcode] A: adjustment       | 0@1000
[transcode] A: rescale stream   | 4.043
[transcode] V: IA32/AMD64 accel | sse3 (sse3 sse2 sse 3dnowext 3dnow mmxext mmx asm C)
tc_memcpy: using sse for memcpy
[transcode] V: video buffer     | 4 @ 720x576
[import_null.so] v0.2.0 (2002-01-19) (video) null | (audio) null
[import_vob.so] v0.6.0 (2003-10-02) (video) MPEG-2 | (audio) MPEG/AC3/PCM | (subtitle)
[filter_extsub.so] 0.3.5 (2003-10-15) DVD subtitle overlay plugin
[filter_extsub.so] options=1:70:0:0:0
[filter_extsub.so] extracting subtitle 0x21
[import_vob.so] tccat -i "/home/rowan/Videos/dvdrip/scarface/vob/001/" -t vob -d 0 -S 0 | tcdemux -a 1 -x ps1 -S 0 -M 1 -d 0 | tcextract -t vob -a 0x21 -x ps1 -d 0
(subproc.c) extracting subtitle stream 1
tc_memcpy: using sse for memcpy
[export_null.so] v0.1.2 (2001-08-17) (video) null | (audio) null
[export_ffmpeg.so] v0.3.13 (2004-08-03) (video) Lavc1d.51.38.0 | (audio) MPEG/AC3/PCM
[import_vob.so] tccat -i "/home/rowan/Videos/dvdrip/scarface/vob/001/" -t vob -d 0 -S 0 | tcdemux -s 0x80 -x mpeg2 -S 0 -M 1 -d 0 | tcextract -t vob -a 0 -x mpeg2 -d 0 | tcdecode -x mpeg2 -d 0
[export_ffmpeg.so] Using FFMPEG codec 'mpeg4' (FourCC 'DIVX', MPEG4 compliant video).
[export_ffmpeg.so]: WARNING: Interlacing parameters unknown, use --encode_fields
[export_ffmpeg.so]: INFO: No profile selected
[export_ffmpeg.so] Neither './ffmpeg.cfg' nor '~/.transcode/ffmpeg.cfg'
[export_ffmpeg.so] found. Default settings will be used instead.
[export_ffmpeg.so]: INFO: Starting 1 thread(s)
tc_memcpy: using sse for memcpy
[export_ffmpeg.so]: INFO: Set display aspect ratio to input
[mpeg4 @ 0xb2fea9a8]removing common factors from framerate
[decode_mpeg2.c] libmpeg2 0.4.0b loop decoder
[decode_mpeg2.c] libmpeg2 acceleration: 3dnow
failed to write U plane of frame
clean up | frame threads | unload modules | cancel signal | internal threads | done
[transcode] encoded 0 frames (0 dropped, 0 cloned), clip length   0.00 s

```

---

