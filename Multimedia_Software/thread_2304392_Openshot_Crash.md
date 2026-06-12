---
title: "Openshot Crash"
date: 2015-11-26
forum: Multimedia Software
---

### Post by versus69 on 2015-11-26
Hi,
I'm trying to use Openshot to edit some videos for an e-learning project, but I always have to stop because Openshot is always crashing and the message about this problem is '*Segmentation fault* (*core dumped*)'.: 
You can look here:
```
 
------------------------- ERROR 1 ------------------------------
Failed to import 'from openshot import main'
Error Message: cannot import name main
----------------------------------------------------------------
--------------------------------
   OpenShot (version 1.4.3)
--------------------------------
Process no longer exists: 2851.  Creating new pid lock file.
no more csLADSPA plugins

Detecting formats, codecs, and filters...
---
video_codecs:
  - a64multi
  - a64multi5
  - asv1
  - asv2
  - bmp
  - cljr
  - dnxhd
  - dpx
  - dvvideo
  - ffv1
  - ffvhuff
  - flashsv
  - flv
  - gif
  - h261
  - h263
  - h263p
  - huffyuv
  - jpegls
  - ljpeg
  - mjpeg
  - mpeg1video
  - mpeg2video
  - mpeg4
  - msmpeg4v2
  - msmpeg4
  - pam
  - pbm
  - pcx
  - pgm
  - pgmyuv
  - png
  - ppm
  - prores
  - qtrle
  - rawvideo
  - roqvideo
  - rv10
  - rv20
  - sgi
  - sunrast
  - svq1
  - targa
  - tiff
  - utvideo
  - v210
  - v410
  - wmv1
  - wmv2
  - xbm
  - xwd
  - zlib
  - zmbv
  - libopenjpeg
  - libschroedinger
  - libtheora
  - libvpx
  - libx264
  - libxvid
...
---
audio_codecs:
  - comfortnoise
  - aac
  - ac3
  - ac3_fixed
  - alac
  - eac3
  - flac
  - mp2
  - nellymoser
  - real_144
  - vorbis
  - wmav1
  - wmav2
  - pcm_alaw
  - pcm_f32be
  - pcm_f32le
  - pcm_f64be
  - pcm_f64le
  - pcm_mulaw
  - pcm_s8
  - pcm_s16be
  - pcm_s16le
  - pcm_s24be
  - pcm_s24daud
  - pcm_s24le
  - pcm_s32be
  - pcm_s32le
  - pcm_u8
  - pcm_u16be
  - pcm_u16le
  - pcm_u24be
  - pcm_u24le
  - pcm_u32be
  - pcm_u32le
  - roq_dpcm
  - adpcm_adx
  - g722
  - g726
  - adpcm_ima_qt
  - adpcm_ima_wav
  - adpcm_ms
  - adpcm_swf
  - adpcm_yamaha
  - libfdk_aac
  - libgsm
  - libgsm_ms
  - libmp3lame
  - libopencore_amrnb
  - libopus
  - libspeex
  - libvo_aacenc
  - libvo_amrwbenc
  - libvorbis
...
---
formats:
  - a64
  - ac3
  - adts
  - adx
  - aiff
  - amr
  - asf
  - ass
  - asf_stream
  - au
  - avi
  - avm2
  - cavsvideo
  - crc
  - daud
  - dirac
  - dnxhd
  - dts
  - dv
  - eac3
  - ffm
  - ffmetadata
  - filmstrip
  - flac
  - flv
  - framecrc
  - framemd5
  - g722
  - gif
  - gxf
  - h261
  - h263
  - h264
  - hls
  - ilbc
  - image2
  - image2pipe
  - ipod
  - ismv
  - ivf
  - latm
  - m4v
  - md5
  - matroska
  - matroska
  - mjpeg
  - mlp
  - mmf
  - mov
  - mp2
  - mp3
  - mp4
  - mpeg
  - vcd
  - mpeg1video
  - dvd
  - svcd
  - mpeg2video
  - vob
  - mpegts
  - mpjpeg
  - mxf
  - mxf_d10
  - null
  - nut
  - ogg
  - oma
  - alaw
  - mulaw
  - f64be
  - f64le
  - f32be
  - f32le
  - s32be
  - s32le
  - s24be
  - s24le
  - s16be
  - s16le
  - s8
  - u32be
  - u32le
  - u24be
  - u24le
  - u16be
  - u16le
  - u8
  - psp
  - rawvideo
  - rm
  - roq
  - rso
  - rtp
  - rtsp
  - sap
  - segment
  - smjpeg
  - smoothstreaming
  - sox
  - spdif
  - srt
  - swf
  - 3g2
  - 3gp
  - truehd
  - rcv
  - voc
  - wav
  - webm
  - yuv4mpegpipe
  - alsa
  - oss
...
state saved
[mp3 @ 0x3067700] max_analyze_duration reached
[mp3 @ 0x3086620] max_analyze_duration reached
[mp3 @ 0x30980e0] max_analyze_duration reached
[mp3 @ 0x30d86e0] max_analyze_duration reached
project state modified
state saved
project state modified
state saved
project state modified
state saved
[mp3 @ 0x3081640] max_analyze_duration reached
[mp3 @ 0x30d0380] max_analyze_duration reached
[mp3 @ 0x30cdcc0] max_analyze_duration reached
[mp3 @ 0x30957a0] max_analyze_duration reached
project state modified
state saved
[mp3 @ 0x30c5b80] max_analyze_duration reached
[mp3 @ 0x368fe00] max_analyze_duration reached
[mp3 @ 0x3687b40] max_analyze_duration reached
[mp3 @ 0x3691560] max_analyze_duration reached
project state modified
state saved
[mp3 @ 0x36b4860] max_analyze_duration reached
[mp3 @ 0x36d6700] max_analyze_duration reached
[mp3 @ 0x36aad40] max_analyze_duration reached
[mp3 @ 0x36b3180] max_analyze_duration reached
project state modified
state saved
[mp3 @ 0x36b1b80] max_analyze_duration reached
[mp3 @ 0x30c01c0] max_analyze_duration reached
[mp3 @ 0x3688200] max_analyze_duration reached
[mp3 @ 0x36af800] max_analyze_duration reached
project state modified
state saved
project state modified
state saved
on_tlbImportFiles_clicked called with self.GtkToolButton
project state modified
state saved
project state modified
state saved
project state modified
state saved
project state modified
state saved
project state modified
state saved
project state modified
state saved
project state modified
state saved
project state modified
state saved
project state modified
state saved
project state modified
state saved
project state modified
state saved
project state modified
state saved
on_tlbPlay_clicked called with self.GtkToolButton
[mp3 @ 0x3ca9080] max_analyze_duration reached
[mp3 @ 0x3cadd80] max_analyze_duration reached
[mp3 @ 0x3cc0f20] max_analyze_duration reached
[mp3 @ 0x3d08200] max_analyze_duration reached
[mp3 @ 0x3d541a0] max_analyze_duration reached
[mp3 @ 0x3d565c0] max_analyze_duration reached
[mp3 @ 0x3089a80] max_analyze_duration reached
[mp3 @ 0x308bb60] max_analyze_duration reached
[mp3 @ 0x3757180] max_analyze_duration reached
[mp3 @ 0x3a2db20] max_analyze_duration reached
[mp3 @ 0x7f24305a47a0] max_analyze_duration reached
[mp3 @ 0x7f24326ddaa0] max_analyze_duration reached
[mp3 @ 0x7f24326d91a0] max_analyze_duration reached
[mp3 @ 0x7f24305a47a0] max_analyze_duration reached
on_tlbPlay_clicked called with self.GtkToolButton
project state modified
state saved
project state modified
state saved
project state modified
state saved
project state modified
state saved
[mp3 @ 0x3e77400] max_analyze_duration reached
[mp3 @ 0x3eacb00] max_analyze_duration reached
[mp3 @ 0x3ea81e0] max_analyze_duration reached
[mp3 @ 0x3eab100] max_analyze_duration reached
[mp3 @ 0x3fec7a0] max_analyze_duration reached
[mp3 @ 0x4009d20] max_analyze_duration reached
[mp3 @ 0x401db00] max_analyze_duration reached
Errore di segmentazione (core dump creato)

 
```

Can you help me? 
Thanks

---

### Post by tgalati4 on 2015-11-27
Sometimes you have to start over.  *Openshot* has a habit of this type of crashing.  It could be a bad cache file that will cause the editor to crash, so you have to start fresh and add your tracks and make your cuts.  It's frustrating, but there is no easy way to repair a video that is causing a segmentation fault.

In the meantime, run *memtest* from the GRUB2 menu to check your RAM, in case you have a bad RAM stick.  A failing RAM stick can cause segmentation faults, and *openshot* uses a lot of RAM.

---

