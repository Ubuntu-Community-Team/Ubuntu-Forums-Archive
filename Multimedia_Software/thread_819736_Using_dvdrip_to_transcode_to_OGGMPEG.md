---
title: "Using dvd::rip to transcode to OGG/MPEG"
date: 2008-06-05
forum: Multimedia Software
---

### Post by happy-and-lost on 2008-06-05
I'm having some problems transcoding using dvd::rip. Ideally, I'd like to use the OGG or MPEG container, as the size:quality ratios are better than AVI. However, when I attempt to transcode as an MPEG, dvd::rip freezes up and gives the following error:

```
Job 'Transcode video - title #1, single pass' failed with error message:
Command exits with failure code:
Command: mkdir -m 0775 -p '/home/jo/Videos/dvdrip/ReturnToOz/tmp' && cd /home/jo/Videos/dvdrip/ReturnToOz/tmp && mkdir -p /home/jo/Videos/dvdrip/ReturnToOz/avi/001 && execflow -n 19 transcode -H 10 -a 0 -x vob -i \/home\/jo\/Videos\/dvdrip\/ReturnToOz\/vob\/001\/ -w 2600,50 -F 5,'-B 182 -I 0 -S 10000  -g 6 -G 15' --export_asr 3 -b 128 -s 1.142 --a52_drc_off -f 25.000 -Y 8,0,8,0 -Z 768x432 -y mpeg2enc,mp2enc -E 44100 -o /home/jo/Videos/dvdrip/ReturnToOz/avi/001/ReturnToOz-001 --print_status 25 && echo EXECFLOW_OK

Output: transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
tc_memcpy: using sse for memcpy
[transcode] (probe) suggested AV correction -D 6 (240 ms) | AV 248 ms | 8 ms
[transcode] auto-probing source /home/jo/Videos/dvdrip/ReturnToOz/vob/001/ (ok)
[transcode] V: import format    | MPEG-2  (V=vob|A=vob)
[transcode] V: AV demux/sync    | (1) sync AV at initial MPEG sequence
[transcode] V: import frame     | 720x576  1.25:1  encoded @ 16:9
[transcode] V: zoom             | 768x432  1.78:1 (Lanczos3)
[transcode] V: clip frame (->)  | 768x416
[transcode] V: bits/pixel       | 0.326
[transcode] V: decoding fps,frc | 25.000,0
[transcode] V: Y'CbCr           | YV12/I420
[transcode] A: import format    | 0x2000  AC3          [48000,16,2]  192 kbps
[transcode] A: export format    | 0x50    MPEG layer-2 [44100,16,2]  128 kbps
[transcode] V: encoding fps,frc | 25.000,3
[transcode] A: bytes per frame  | 7680 (7680.000000)
[transcode] A: adjustment       | 0@1000
[transcode] A: rescale stream   | 1.142
[transcode] V: IA32/AMD64 accel | sse2 (sse2 sse mmxext mmx asm C)
[transcode] V: video buffer     | 10 @ 768x5[import_vob.so] v0.6.0 (2003-10-02) (video) MPEG-2 | (audio) MPEG/AC3/PCM | (subtitle)
[export_mp2enc.so] v1.0.10 (2004-09-27) (audio) MPEG 1/2
[export_mpeg2enc.so] v1.1.10 (2003-10-30) (video) MPEG 1/2
[export_mpeg2enc.so] *** init-v *** !
[export_mp2enc.so] *** init-v *** !
[transcode] ERROR: The 'mpeg2enc' program could not be found. 
[transcode]        Please check your installation.
[transcode] warning : (encoder.c) video export module error: open failed
76
[import_vob.so] tccat -i "/home/jo/Videos/dvdrip/ReturnToOz/vob/001/" -t vob -d 0 -S 0 | tcdemux -a 0 -x ac3 -S 0 -M 1 -d 0 | tcextract -t vob -a 0 -x ac3 -d 0 | tcdecode -x ac3 -d 0 -s 1.000000,1.000000,1.000000 -A 1
[import_vob.so] tccat -i "/home/jo/Videos/dvdrip/ReturnToOz/vob/001/" -t vob -d 0 -S 0 | tcdemux -s 0x80 -x mpeg2 -S 0 -M 1 -d 0 | tcextract -t vob -a 0 -x mpeg2 -d 0 | tcdecode -x mpeg2 -d 0 -y yv12
[transcode] critical: failed to open output
tc_memcpy: using sse for memcpy
tc_memcpy: using sse for memcpy
[decode_mpeg2.c] libmpeg2 0.4.0b loop decoder
[decode_mpeg2.c] libmpeg2 acceleration: mmxext
(decode_ac3.c) write failed
failed to write Y plane of frame(demuxer.c) write program stream packet: Broken pipe

--------------------------------------------------------------------------------

```

:(

---

