---
title: "No sound with JWPlayer"
date: 2012-12-11
forum: Multimedia Software
---

### Post by alfirdaous on 2012-12-11
Hello everybody,

While encoding a youtube video, playing it in the browser it works, but if I use [JWPlayer]("http://ubuntuforums.org/www.longtailvideo.com") there is no sound on the video, the encoding code is:

It is the ONLY video that does NOT work

```

ffmpeg -i 001-Original.flv -vf "drawtext=fontfile='/usr/share/fonts/truetype/freefont/FreeSans.ttf':text='test':x=20:y=30:fontsize=20:fontcolor=white" -vcodec libx264 -preset medium -crf 24 -acodec copy 001-Out.mp4

```Thanks for your help

---

### Post by FakeOutdoorsman on 2012-12-11
Please show the complete ffmpeg console output. Also, consider passing the ffmpeg output file through qt-faststart or adding "-movflags faststart" as an output option. This will allow the file to begin playback before it is completely downloaded.

---

### Post by alfirdaous on 2012-12-11
this is the input info:

```

General
Complete name                    : 001.avi
Format                           : AVI
Format/Info                      : Audio Video Interleave
File size                        : 41.8 MiB
Duration                         : 8mn 35s
Overall bit rate                 : 680 Kbps
Writing application              : VirtualDubMod 1.5.10.3 Fr | www.virtualdub-fr.org ||  (build 2550/release)
Writing library                  : VirtualDubMod build 2550/release

Video
ID                               : 0
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : High@L1.3
Format settings, CABAC           : Yes
Format settings, ReFrames        : 3 frames
Codec ID                         : H264
Duration                         : 8mn 35s
Bit rate                         : 542 Kbps
Width                            : 352 pixels
Height                           : 288 pixels
Display aspect ratio             : 1.222
Frame rate                       : 25.000 fps
Original frame rate              : 50.000 fps
Resolution                       : 8 bits
Colorimetry                      : 4:2:0
Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.214
Stream size                      : 33.3 MiB (80%)
Writing library                  : x264 core 115 r1955bm 06f5fa5
Encoding settings                : cabac=1 / ref=3 / deblock=1:0:0 / analyse=0x3:0x113 / me=hex / subme=7 / psy=1 / psy_rd=1.00:0.00 / mixed_ref=1 / me_range=16 / chroma_me=1 / trellis=1 / 8x8dct=1 / cqm=0 / deadzone=21,11 / fast_pskip=1 / chroma_qp_offset=-2 / threads=2 / sliced_threads=1 / slices=2 / nr=0 / decimate=1 / interlaced=0 / bluray_compat=0 / constrained_intra=0 / bframes=0 / weightp=2 / keyint=250 / keyint_min=25 / scenecut=40 / intra_refresh=0 / rc=crf / mbtree=0 / crf=20.0 / qcomp=0.60 / qpmin=0 / qpmax=69 / qpstep=4 / ip_ratio=1.40 / aq=1:1.00

Audio
ID                               : 1
Format                           : MPEG Audio
Format version                   : Version 1
Format profile                   : Layer 3
Format_Settings_Mode             : Joint stereo
Format_Settings_ModeExtension    : MS Stereo
Codec ID                         : 55
Codec ID/Hint                    : MP3
Duration                         : 8mn 35s
Bit rate mode                    : Constant
Bit rate                         : 128 Kbps
Channel(s)                       : 2 channels
Sampling rate                    : 48.0 KHz
Stream size                      : 7.86 MiB (19%)
Alignment                        : Split accross interleaves
Interleave, duration             : 40 ms (1.00 video frame)
Interleave, preload duration     : 500 ms


```

output:

```

General
Complete name                    : output.mp4
Format                           : MPEG-4
Format profile                   : Base Media
Codec ID                         : isom
File size                        : 3.07 MiB
Duration                         : 1mn 0s
Overall bit rate                 : 429 Kbps
Writing application              : Lavf53.32.100

Video
ID                               : 1
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : High@L1.3
Format settings, CABAC           : Yes
Format settings, ReFrames        : 4 frames
Codec ID                         : avc1
Codec ID/Info                    : Advanced Video Coding
Duration                         : 1mn 0s
Bit rate mode                    : Variable
Bit rate                         : 296 Kbps
Width                            : 352 pixels
Height                           : 288 pixels
Display aspect ratio             : 1.222
Frame rate mode                  : Constant
Frame rate                       : 25.000 fps
Resolution                       : 8 bits
Colorimetry                      : 4:2:0
Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.117
Stream size                      : 2.12 MiB (69%)
Writing library                  : x264 core 120 r2151 a3f4407
Encoding settings                : cabac=1 / ref=3 / deblock=1:0:0 / analyse=0x3:0x113 / me=hex / subme=7 / psy=1 / psy_rd=1.00:0.00 / mixed_ref=1 / me_range=16 / chroma_me=1 / trellis=1 / 8x8dct=1 / cqm=0 / deadzone=21,11 / fast_pskip=1 / chroma_qp_offset=-2 / threads=6 / sliced_threads=0 / nr=0 / decimate=1 / interlaced=0 / bluray_compat=0 / constrained_intra=0 / bframes=3 / b_pyramid=2 / b_adapt=1 / b_bias=0 / direct=1 / weightb=1 / open_gop=0 / weightp=2 / keyint=250 / keyint_min=25 / scenecut=40 / intra_refresh=0 / rc_lookahead=40 / rc=crf / mbtree=1 / crf=24.0 / qcomp=0.60 / qpmin=0 / qpmax=69 / qpstep=4 / ip_ratio=1.40 / aq=1:1.00

Audio
ID                               : 2
Format                           : MPEG Audio
Format version                   : Version 1
Format profile                   : Layer 3
Format_Settings_Mode             : Joint stereo
Format_Settings_ModeExtension    : MS Stereo
Codec ID                         : 6B
Duration                         : 1mn 0s
Bit rate mode                    : Constant
Bit rate                         : 128 Kbps
Channel(s)                       : 2 channels
Sampling rate                    : 48.0 KHz
Stream size                      : 938 KiB (30%)


```

the code used:

```

ffmpeg -i 001.avi -ss 00:00:00 -t 00:01:00 -vf "drawtext=fontfile='/usr/share/fonts/truetype/freefont/FreeSans.ttf':text='test':x=20:y=30:fontsize=20:fontcolor=white" -vcodec libx264 -preset medium -crf 24 -acodec copy output.mp4

```

thx in advance

---

### Post by FakeOutdoorsman on 2012-12-11
Please show the complete ffmpeg console output that shows up after you run your ffmpeg command.

---

### Post by alfirdaous on 2012-12-12
here you are:

```

ffmpeg -i 001.avi -ss 00:00:00 -t 00:01:00 -vf "drawtext=fontfile='/usr/share/fonts/truetype/freefont/FreeSans.ttf':text='test':x=20:y=30:fontsize=20:fontcolor=white" -vcodec libx264 -preset medium -crf 24 -acodec copy output.mp4
ffmpeg version 0.10.4-6:0.10.4-0ubuntu0jon2~lucid2 Copyright (c) 2000-2012 the FFmpeg developers
  built on Jun 21 2012 13:03:15 with gcc 4.4.3
  configuration: --extra-version='6:0.10.4-0ubuntu0jon2~lucid2' --arch=i386 --prefix=/usr --disable-stripping --enable-vdpau --enable-bzlib --enable-gnutls --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-libfreetype --enable-libpulse --enable-gpl --enable-postproc --enable-x11grab --enable-libcdio --enable-version3 --enable-libdc1394 --enable-shared --disable-static
  avutil      configuration: --extra-version='6:0.10.4.0ubuntu0jon2~lucid1' --arch=i386 --prefix=/usr --disable-stripping --enable-vdpau --enable-bzlib --enable-gnutls --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-libfreetype --enable-libpulse --enable-libopenjpeg --enable-libmp3lame --enable-frei0r --enable-gpl --enable-postproc --enable-x11grab --enable-libcdio --enable-libx264 --enable-version3 --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay --disable-ffprobe --disable-ffserver
  avcodec     configuration: --extra-version='6:0.10.4.0ubuntu0jon2~lucid1' --arch=i386 --prefix=/usr --disable-stripping --enable-vdpau --enable-bzlib --enable-gnutls --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-libfreetype --enable-libpulse --enable-libopenjpeg --enable-libmp3lame --enable-frei0r --enable-gpl --enable-postproc --enable-x11grab --enable-libcdio --enable-libx264 --enable-version3 --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay --disable-ffprobe --disable-ffserver
  avformat    configuration: --extra-version='6:0.10.4-0ubuntu0jon2~lucid2' --arch=i386 --prefix=/usr --disable-stripping --enable-vdpau --enable-bzlib --enable-gnutls --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-libfreetype --enable-libpulse --enable-gpl --enable-postproc --enable-x11grab --enable-libcdio --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay --disable-ffprobe --disable-ffserver
  avdevice    configuration: --extra-version='6:0.10.4-0ubuntu0jon2~lucid2' --arch=i386 --prefix=/usr --disable-stripping --enable-vdpau --enable-bzlib --enable-gnutls --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-libfreetype --enable-libpulse --enable-gpl --enable-postproc --enable-x11grab --enable-libcdio --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay --disable-ffprobe --disable-ffserver
  avfilter    configuration: --extra-version='6:0.10.4-0ubuntu0jon2~lucid2' --arch=i386 --prefix=/usr --disable-stripping --enable-vdpau --enable-bzlib --enable-gnutls --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-libfreetype --enable-libpulse --enable-gpl --enable-postproc --enable-x11grab --enable-libcdio --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay --disable-ffprobe --disable-ffserver
  swscale     configuration: --extra-version='6:0.10.4-0ubuntu0jon2~lucid2' --arch=i386 --prefix=/usr --disable-stripping --enable-vdpau --enable-bzlib --enable-gnutls --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-libfreetype --enable-libpulse --enable-gpl --enable-postproc --enable-x11grab --enable-libcdio --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay --disable-ffprobe --disable-ffserver
  swresample  configuration: --extra-version='6:0.10.4-0ubuntu0jon2~lucid2' --arch=i386 --prefix=/usr --disable-stripping --enable-vdpau --enable-bzlib --enable-gnutls --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-libfreetype --enable-libpulse --enable-gpl --enable-postproc --enable-x11grab --enable-libcdio --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay --disable-ffprobe --disable-ffserver
  postproc    configuration: --extra-version='6:0.10.4-0ubuntu0jon2~lucid2' --arch=i386 --prefix=/usr --disable-stripping --enable-vdpau --enable-bzlib --enable-gnutls --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-libfreetype --enable-libpulse --enable-gpl --enable-postproc --enable-x11grab --enable-libcdio --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay --disable-ffprobe --disable-ffserver
  libavutil      51. 35.100 / 51. 35.100
  libavcodec     53. 61.100 / 53. 61.100
  libavformat    53. 32.100 / 53. 32.100
  libavdevice    53.  4.100 / 53.  4.100
  libavfilter     2. 61.100 /  2. 61.100
  libswscale      2.  1.100 /  2.  1.100
  libswresample   0.  6.100 /  0.  6.100
  libpostproc    52.  0.100 / 52.  0.100
[avi @ 0x806f020] max_analyze_duration 5000000 reached at 5016000
Input #0, avi, from '001.avi':
  Metadata:
    encoder         : VirtualDubMod 1.5.10.3 Fr | www.virtualdub-fr.org ||  (build 2550/release)
  Duration: 00:08:43.28, start: 0.000000, bitrate: 595 kb/s
    Stream #0:0: Video: h264 (High) (H264 / 0x34363248), yuv420p, 352x288 [SAR 1:1 DAR 11:9], 25 fps, 25 tbr, 25 tbn, 50 tbc
    Stream #0:1: Audio: mp3 (U[0][0][0] / 0x0055), 48000 Hz, stereo, s16, 128 kb/s
File 'output.mp4' already exists. Overwrite ? [y/N] y
w:352 h:288 pixfmt:yuv420p tb:1/1000000 sar:1/1 sws_param:
[libx264 @ 0x807a3a0] using SAR=1/1
[libx264 @ 0x807a3a0] using cpu capabilities: MMX2 SSE2Fast SSSE3 FastShuffle Cache64
[libx264 @ 0x807a3a0] profile High, level 1.3
[libx264 @ 0x807a3a0] 264 - core 120 r2151 a3f4407 - H.264/MPEG-4 AVC codec - Copyleft 2003-2011 - http://www.videolan.org/x264.html - options: cabac=1 ref=3 deblock=1:0:0 analyse=0x3:0x113 me=hex subme=7 psy=1 psy_rd=1.00:0.00 mixed_ref=1 me_range=16 chroma_me=1 trellis=1 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=6 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=3 b_pyramid=2 b_adapt=1 b_bias=0 direct=1 weightb=1 open_gop=0 weightp=2 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=40 rc=crf mbtree=1 crf=24.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.40 aq=1:1.00
Output #0, mp4, to 'output.mp4':
  Metadata:
    encoder         : Lavf53.32.100
    Stream #0:0: Video: h264 (![0][0][0] / 0x0021), yuv420p, 352x288 [SAR 1:1 DAR 11:9], q=-1--1, 25 tbn, 25 tbc
    Stream #0:1: Audio: mp3 (i[0][0][0] / 0x0069), 48000 Hz, stereo, 128 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (h264 -> libx264)
  Stream #0:1 -> #0:1 (copy)
Press [q] to stop, [?] for help
frame= 1500 fps= 24 q=-1.0 Lsize=    2949kB time=00:00:59.92 bitrate= 403.2kbits/s    
video:1976kB audio:938kB global headers:0kB muxing overhead 1.242996%
[libx264 @ 0x807a3a0] frame I:7     Avg QP:18.12  size: 14076
[libx264 @ 0x807a3a0] frame P:1099  Avg QP:25.24  size:  1672
[libx264 @ 0x807a3a0] frame B:394   Avg QP:29.81  size:   219
[libx264 @ 0x807a3a0] consecutive B-frames: 60.4% 12.3%  4.4% 22.9%
[libx264 @ 0x807a3a0] mb I  I16..4: 31.1% 12.0% 56.9%
[libx264 @ 0x807a3a0] mb P  I16..4:  1.9%  0.4%  0.3%  P16..4: 27.7% 11.5%  8.1%  0.0%  0.0%    skip:50.0%
[libx264 @ 0x807a3a0] mb B  I16..4:  0.2%  0.0%  0.0%  B16..8: 18.0%  1.8%  0.5%  direct: 0.6%  skip:78.8%  L0:37.5% L1:57.1% BI: 5.4%
[libx264 @ 0x807a3a0] 8x8 transform intra:14.6% inter:45.7%
[libx264 @ 0x807a3a0] coded y,uvDC,uvAC intra: 26.9% 35.1% 21.7% inter: 14.3% 14.8% 2.0%
[libx264 @ 0x807a3a0] i16 v,h,dc,p: 58% 34%  5%  3%
[libx264 @ 0x807a3a0] i8 v,h,dc,ddl,ddr,vr,hd,vl,hu: 11% 26% 36%  3%  4%  3%  5%  4%  7%
[libx264 @ 0x807a3a0] i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 23% 26% 16%  5%  6%  6%  6%  5%  6%
[libx264 @ 0x807a3a0] i8c dc,h,v,p: 61% 28%  9%  2%
[libx264 @ 0x807a3a0] Weighted P-Frames: Y:21.8% UV:7.4%
[libx264 @ 0x807a3a0] ref P L0: 67.8% 19.0%  9.9%  2.3%  0.9%
[libx264 @ 0x807a3a0] ref B L0: 90.9%  7.8%  1.3%
[libx264 @ 0x807a3a0] ref B L1: 96.0%  4.0%
[libx264 @ 0x807a3a0] kb/s:269.64


```

---

### Post by FakeOutdoorsman on 2012-12-12
I guess JW Player doesn't like MP3 audio in MP4 container. Try re-encoding the audio to AAC. I think your only option within your ffmpeg from Jon's PPA is:
```
-acodec aac -strict experimental -ab 192k
```
Or you could pipe to an external encoder (faac, neroAacEnc) and then mux with ffmpeg.
```
ffmpeg -i input -f wav - | neroAacEnc -ignorelength -if - -of audio.mp4
ffmpeg -i video -i audio.mp4 -vcodec copy -acodec copy -map 0:0 -map 1:0 output-temp.mp4
qt-faststart output-temp.mp4 output.mp4

```

---

### Post by alfirdaous on 2012-12-13
Oh thx it works.

I used this:

```

-acodec aac -strict experimental -ab 128k

```

is qt-faststart same as MP4Box?

---

### Post by FakeOutdoorsman on 2012-12-13
> **alfirdaous said:**
> is qt-faststart same as MP4Box?

All qt-faststart does is move some info in the mp4 file so it can begin playback before it is completely downloaded. MP4Box, part of the **gpac** package, can also do this and much more. Either one is fine for this purpose as far as I know. This MP4Box example should do the same:

```
MP4Box -add input.mp4 output.mp4
```

---

### Post by alfirdaous on 2012-12-13
thx [FakeOutdoorsman]("http://ubuntuforums.org/member.php?u=162846"), I use this command:

```
MP4Box -add INPUT OUPUT
```

---

