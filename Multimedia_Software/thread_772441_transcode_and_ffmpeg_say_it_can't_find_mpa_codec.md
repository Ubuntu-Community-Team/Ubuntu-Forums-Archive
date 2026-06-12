---
title: "transcode and ffmpeg say it can't find mpa codec"
date: 2008-04-28
forum: Multimedia Software
---

### Post by rocketman768 on 2008-04-28
Transcode fails with the following command on A.MOV, but succeeds with B.avi.

```
transcode -i A.MOV -y ffmpeg --export_prof dvd-ntsc --export_asr 2 -o A -m A.ac3 -J modfps=clonetype=3 --export_fps 29.97
```

Here is the error message from A.MOV
```
transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
[transcode] (probe) suggested AV correction -D 0 (0 ms) | AV 0 ms | 0 ms
[transcode] auto-probing source DSCN0197.MOV (ok)
[transcode] V: import format    | MJPG QuickTime (V=mov|A=mov)
[transcode] V: import frame     | 320x240  1.33:1  
XXX: zoom=yes pre_clip=no
[transcode] V: zoom             | 720x480  1.50:1 (Lanczos3)
[transcode] V: bits/pixel       | 0.347
[transcode] V: decoding fps,frc | 15.000,13
[transcode] V: Y'CbCr           | YV12/I420
[transcode] A: import format    | 0x1     PCM          [8000,16,1]
[transcode] A: export format    | 0x55    MPEG layer-3 [8000,16,1]  128 kbps
[transcode] V: encoding fps,frc | 29.970,4
[transcode] A: bytes per frame  | 534 (533.866667)
[transcode] A: adjustment       | -132@1000
[transcode] V: IA32/AMD64 accel | sse2 (sse2 sse mmxext mmx asm C)
tc_memcpy: using sse for memcpy
[transcode] V: video buffer     | 10 @ 720x480
[import_mov.so] v0.1.2 (2002-05-16) (video) * | (audio) *
[filter_modfps.so] v0.10 (2003-08-18) plugin to modify framerate
[filter_modfps.so] converting from 15.0000fps to 29.9700fps
[export_ffmpeg.so] v0.3.13 (2004-08-03) (video) Lavc1d.51.38.0 | (audio) MPEG/AC3/PCM
[import_mov.so] codec=ulaw, rate=8000 Hz, bits=16, channels=1, samples=291276
[import_mov.so] VIDEO: codec=jpeg, fps=15.000, width=320, height=240, frames=548
[export_ffmpeg.so] Using FFMPEG codec 'mpeg2video' (FourCC 'mpg2', MPEG2 compliant video).
[export_ffmpeg.so]: INFO: Selected dvd profile, ntsc video type for video
[export_ffmpeg.so]: INFO: Set interlacing to bottom-first
[export_ffmpeg.so]: INFO: Set frame rate to 29.97
[export_ffmpeg.so]: INFO: Set video bitrate to 5000
[export_ffmpeg.so]: INFO: Set GOP size to 18
[export_ffmpeg.so] Neither './ffmpeg.cfg' nor '~/.transcode/ffmpeg.cfg'
[export_ffmpeg.so] found. Default settings will be used instead.
[export_ffmpeg.so]: INFO: Starting 1 thread(s)
[export_ffmpeg.so]: INFO: Display aspect ratio calculated as 1.333333
[export_ffmpeg.so]: INFO: Sample aspect ratio calculated as 0.888889
[export_ffmpeg.so]: INFO: Selected dvd profile for audio
[export_ffmpeg.so]: INFO: Resampling filter inactive
[export_ffmpeg.so]: INFO: Set number of audio channels to 2
[export_ffmpeg.so]: INFO: Set number of audio bits to 16
[export_ffmpeg.so]: WARNING: Set audio sample rate to 48000 Hz, input rate is 8000 Hz
[export_ffmpeg.so]: WARNING:    loading resample plugin
[filter.c] Filter "resample" with args (resample)
[filter.c] Filter "resample" not loaded. Loading ...
[filter.c] Loading (resample) ..
[filter_resample.so] v0.1.4 (2003-08-22) audio resampling filter plugin
[filter_resample.so] options=(null)
[export_ffmpeg.so]: INFO: Set audio bit rate to 224 kbps
[export_ffmpeg.so]: INFO: Set audio codec to ac3
[encode_ffmpeg] could not open mpa codec !
[transcode] warning : (encoder.c) audio export module error: init failed
[transcode] critical: failed to init encoder

```

However, when I remove the option "--export_fps 29.97", everything proceeds, although the framerate is screwed up. What is up?

Here is the description of A.MOV provided by mplayer.
```
Playing A.MOV.
Quicktime/MOV file format detected.
ID_VIDEO_ID=0
[mov] Video stream found, -vid 0
Warning! pts=291276  length=292266
ID_AUDIO_ID=1
[mov] Audio stream found, -aid 1
VIDEO:  [jpeg]  320x240  24bpp  15.000 fps    0.0 kbps ( 0.0 kbyte/s)
ID_FILENAME=A.MOV
ID_DEMUXER=mov
ID_VIDEO_FORMAT=jpeg
ID_VIDEO_BITRATE=0
ID_VIDEO_WIDTH=320
ID_VIDEO_HEIGHT=240
ID_VIDEO_FPS=15.000
ID_VIDEO_ASPECT=0.0000
ID_AUDIO_FORMAT=ulaw
ID_AUDIO_BITRATE=0
ID_AUDIO_RATE=8000
ID_AUDIO_NCH=1
ID_LENGTH=36.53
```

And for good measure, here is B.avi which succeeds.
```
Playing B.avi.
AVI file format detected.
ID_VIDEO_ID=0
[aviheader] Video stream found, -vid 0
ID_AUDIO_ID=1
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  624x352  12bpp  23.976 fps  1046.8 kbps (127.8 kbyte/s)
Clip info:
 Software: Nandub v1.0rc2
ID_CLIP_INFO_NAME0=Software
ID_CLIP_INFO_VALUE0=Nandub v1.0rc2
ID_CLIP_INFO_N=1
ID_FILENAME=B.avi
ID_DEMUXER=avi
ID_VIDEO_FORMAT=XVID
ID_VIDEO_BITRATE=1046760
ID_VIDEO_WIDTH=624
ID_VIDEO_HEIGHT=352
ID_VIDEO_FPS=23.976
ID_VIDEO_ASPECT=0.0000
ID_AUDIO_FORMAT=85
ID_AUDIO_BITRATE=133144
ID_AUDIO_RATE=0
ID_AUDIO_NCH=0
ID_LENGTH=2460.92

```

---

