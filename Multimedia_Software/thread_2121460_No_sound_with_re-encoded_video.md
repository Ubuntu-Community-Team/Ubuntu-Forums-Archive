---
title: "No sound with re-encoded video"
date: 2013-03-02
forum: Multimedia Software
---

### Post by alfirdaous on 2013-03-02
Hello everybody,

While re-encoding a specific AVI video, there is no sound on the player, it seems to be an audio codec problem:

```

ffmpeg -i Input.avi -ss 00:00:00 -t 00:00:59 -strict experimental  -vf  "drawtext=fontfile='/usr/share/fonts/truetype/freefont/FreeSansBold.ttf':text='Text':x=5:y=60:fontsize=20:fontcolor=white"  -vcodec libx264 -preset medium -acodec copy Output.mp4

```

After hitting enter:

```

*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[avi @ 0x6319c0] max_analyze_duration reached
Input #0, avi, from 'Input.avi':
  Metadata:
    encoder         : MEncoder Sherpya-SVN-r33488-4.2.5
  Duration: 00:25:56.96, start: 0.000000, bitrate: 436 kb/s
    Stream #0.0: Video: h264 (High), yuv420p, 352x288 [PAR 1:1 DAR 11:9], 25 fps, 25 tbr, 25 tbn, 50 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 128 kb/s
[buffer @ 0x639480] w:352 h:288 pixfmt:yuv420p
[libx264 @ 0x65e720] using SAR=1/1
[libx264 @ 0x65e720] using cpu capabilities: MMX2 SSE2Fast SSSE3 Cache64 SlowCTZ SlowAtom
[libx264 @ 0x65e720] profile Main, level 1.3
[libx264 @ 0x65e720] 264 - core 120 r2151 a3f4407 - H.264/MPEG-4 AVC codec - Copyleft 2003-2011 - http://www.videolan.org/x264.html - options: cabac=1 ref=3 deblock=1:0:0 analyse=0x1:0x111 me=hex subme=7 psy=1 psy_rd=1.00:0.00 mixed_ref=0 me_range=16 chroma_me=1 trellis=1 8x8dct=0 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=1 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=3 b_pyramid=0 b_adapt=1 b_bias=0 direct=1 weightb=0 open_gop=1 weightp=2 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=40 rc=crf mbtree=1 crf=23.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.25 aq=1:1.00
Output #0, mp4, to 'Output.mp4':
  Metadata:
    encoder         : Lavf53.21.1
    Stream #0.0: Video: libx264, yuv420p, 352x288 [PAR 1:1 DAR 11:9], q=-1--1, 25 tbn, 25 tbc
    Stream #0.1: Audio: libmp3lame, 48000 Hz, stereo, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press ctrl-c to stop encoding

```

The same output even for adding:
```

-acodec aac -strict experimental

```





 Thanks in advance

---

### Post by andrew.46 on 2013-03-02
Could you give the full, uncut output? You have snipped  few vital parts :). Unlikely to be a problem with FFmpeg / avconv if the mp3 audio is simply being copied, perhaps the problem is with playback. Can you play mp3 files with vlc, SMPlayer and friends on your system?

---

### Post by alfirdaous on 2013-03-02
I can play movies, MP3 files,... the probleme is coming from some videos only:

input mediainfo:

```

Format                                   : AVI
Format/Info                              : Audio Video Interleave
File size                                : 81.0 MiB
Duration                                 : 25mn 57s
Overall bit rate                         : 436 Kbps
Writing application                      : MEncoder Sherpya-SVN-r33488-4.2.5
Writing library                          : MPlayer

Video
ID                                       : 0
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : High@L5.1
Format settings, CABAC                   : Yes
Format settings, ReFrames                : 3 frames
Codec ID                                 : H264
Duration                                 : 25mn 56s
Bit rate                                 : 303 Kbps
Width                                    : 352 pixels
Height                                   : 288 pixels
Display aspect ratio                     : 1.222
Frame rate                               : 25.000 fps
Standard                                 : PAL
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Bits/(Pixel*Frame)                       : 0.120
Stream size                              : 56.3 MiB (69%)
Writing library                          : x264 core 60 r913bm 64848ff
Encoding  settings                        : cabac=1 / ref=1 / deblock=1:0:0 /  analyse=0x3:0x133 / me=umh / subme=6 / brdo=1 / mixed_ref=0 /  me_range=16 / chroma_me=1 / trellis=1 / 8x8dct=1 / cqm=0 /  deadzone=21,11 / chroma_qp_offset=0 / threads=1 / nr=0 / decimate=1 /  mbaff=0 / bframes=2 / b_pyramid=1 / b_adapt=1 / b_bias=0 / direct=2 /  wpredb=1 / bime=1 / keyint=250 / keyint_min=25 / scenecut=40 / rc=crf /  crf=20.0 / rceq='blurCplx^(1-qComp)' / qcomp=1.00 / qpmin=10 / qpmax=51 /  qpstep=4 / ip_ratio=1.40 / pb_ratio=1.30 / aq=2:1.00

Audio
ID                                       : 1
Format                                   : MPEG Audio
Format version                           : Version 1
Format profile                           : Layer 3
Mode                                     : Joint stereo
Mode extension                           : MS Stereo
Codec ID                                 : 55
Codec ID/Hint                            : MP3
Duration                                 : 25mn 57s
Bit rate mode                            : Constant
Bit rate                                 : 128 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 48.0 KHz
Compression mode                         : Lossy
Stream size                              : 23.8 MiB (29%)
Alignment                                : Split accross interleaves
Interleave, duration                     : 500 ms (12.50 video frames)
Interleave, preload duration             : 500 ms

```

output mediainfo:

```

Format                                   : MPEG-4
Format profile                           : Base Media
Codec ID                                 : isom
File size                                : 41.2 MiB
Duration                                 : 25mn 57s
Overall bit rate                         : 222 Kbps
Writing application                      : Lavf53.21.1

Video
ID                                       : 1
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : Main@L1.3
Format settings, CABAC                   : Yes
Format settings, ReFrames                : 3 frames
Codec ID                                 : avc1
Codec ID/Info                            : Advanced Video Coding
Duration                                 : 25mn 57s
Bit rate                                 : 215 Kbps
Width                                    : 352 pixels
Height                                   : 288 pixels
Display aspect ratio                     : 1.222
Frame rate mode                          : Constant
Frame rate                               : 25.000 fps
Standard                                 : PAL
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Bits/(Pixel*Frame)                       : 0.085
Stream size                              : 39.8 MiB (97%)
Writing library                          : x264 core 120 r2151 a3f4407
Encoding  settings                        : cabac=1 / ref=3 / deblock=1:0:0 /  analyse=0x1:0x111 / me=hex / subme=7 / psy=1 / psy_rd=1.00:0.00 /  mixed_ref=0 / me_range=16 / chroma_me=1 / trellis=1 / 8x8dct=0 / cqm=0 /  deadzone=21,11 / fast_pskip=1 / chroma_qp_offset=-2 / threads=1 /  sliced_threads=0 / nr=0 / decimate=1 / interlaced=0 / bluray_compat=0 /  constrained_intra=0 / bframes=3 / b_pyramid=0 / b_adapt=1 / b_bias=0 /  direct=1 / weightb=0 / open_gop=1 / weightp=2 / keyint=250 /  keyint_min=25 / scenecut=40 / intra_refresh=0 / rc_lookahead=40 / rc=crf  / mbtree=1 / crf=23.0 / qcomp=0.60 / qpmin=0 / qpmax=69 / qpstep=4 /  ip_ratio=1.25 / aq=1:1.00

Audio
ID                                       : 2
Format                                   : MPEG Audio
Format version                           : Version 1
Format profile                           : Layer 3
Mode                                     : Joint stereo
Mode extension                           : MS Stereo
Codec ID                                 : 6B
Duration                                 : 59s 16ms
Bit rate mode                            : Constant
Bit rate                                 : 128 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 48.0 KHz
Compression mode                         : Lossy
Stream size                              : 922 KiB (2%)

```

thx in advance

---

### Post by FakeOutdoorsman on 2013-03-02
What player aer you using? Unfortunately mediainfo outputs are often wrong, and providing the complete ffmpeg command and output is generally more informative.

---

### Post by alfirdaous on 2013-03-03
Totem Movie Player.

This is the FFMPEG command:
```

ffmpeg -i Input.avi -ss 00:00:00 -t 00:00:59 -strict experimental  -vf  "drawtext=fontfile='/usr/share/fonts/truetype/freefont/FreeSansBold.ttf':text='Text':x=5:y=60:fontsize=20:fontcolor=white"  -vcodec libx264 -preset medium -acodec copy Output.mp4

```

This is the output:
```

ffmpeg -i Input.avi -ss 00:00:00 -t 00:00:59 -strict experimental  -vf  "drawtext=fontfile='/usr/share/fonts/truetype/freefont/FreeSansBold.ttf':text='Text':x=5:y=60:fontsize=20:fontcolor=white"  -vcodec libx264 -preset medium -acodec copy Output.mp4


ffmpeg version 0.8.5-4:0.8.5-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jan 24 2013 18:01:36 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[avi @ 0x6319c0] max_analyze_duration reached
Input #0, avi, from 'Input.avi':
  Metadata:
    encoder         : MEncoder Sherpya-SVN-r33488-4.2.5
  Duration: 00:25:56.96, start: 0.000000, bitrate: 436 kb/s
    Stream #0.0: Video: h264 (High), yuv420p, 352x288 [PAR 1:1 DAR 11:9], 25 fps, 25 tbr, 25 tbn, 50 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 128 kb/s
File 'Output.mp4' already exists. Overwrite ? [y/N] y
[buffer @ 0x639480] w:352 h:288 pixfmt:yuv420p
[libx264 @ 0x65e720] using SAR=1/1
[libx264 @ 0x65e720] using cpu capabilities: MMX2 SSE2Fast SSSE3 Cache64 SlowCTZ SlowAtom
[libx264 @ 0x65e720] profile Main, level 1.3
[libx264 @ 0x65e720] 264 - core 120 r2151 a3f4407 - H.264/MPEG-4 AVC codec - Copyleft 2003-2011 - http://www.videolan.org/x264.html - options: cabac=1 ref=3 deblock=1:0:0 analyse=0x1:0x111 me=hex subme=7 psy=1 psy_rd=1.00:0.00 mixed_ref=0 me_range=16 chroma_me=1 trellis=1 8x8dct=0 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=1 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=3 b_pyramid=0 b_adapt=1 b_bias=0 direct=1 weightb=0 open_gop=1 weightp=2 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=40 rc=crf mbtree=1 crf=23.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.25 aq=1:1.00
Output #0, mp4, to 'Output.mp4':
  Metadata:
    encoder         : Lavf53.21.1
    Stream #0.0: Video: libx264, yuv420p, 352x288 [PAR 1:1 DAR 11:9], q=-1--1, 25 tbn, 25 tbc
    Stream #0.1: Audio: libmp3lame, 48000 Hz, stereo, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press ctrl-c to stop encoding
[h264 @ 0x6339a0] Delayed frames seen reenabling low delay requires a codec flush.drop=0    
frame=38925 fps=  6 q=28.0 Lsize=   42219kB time=59.02 bitrate=5860.4kbits/s dup=3 drop=0    
video:40781kB audio:922kB global headers:0kB muxing overhead 1.237481%
frame I:168   Avg QP:20.97  size: 13417
[libx264 @ 0x65e720] frame P:13788 Avg QP:23.29  size:  2266
[libx264 @ 0x65e720] frame B:24969 Avg QP:28.90  size:   331
[libx264 @ 0x65e720] consecutive B-frames:  4.3% 18.5% 36.1% 41.2%
[libx264 @ 0x65e720] mb I  I16..4: 22.5%  0.0% 77.5%
[libx264 @ 0x65e720] mb P  I16..4:  2.2%  0.0%  1.1%  P16..4: 35.9% 15.7%  9.2%  0.0%  0.0%    skip:36.0%
[libx264 @ 0x65e720] mb B  I16..4:  0.2%  0.0%  0.1%  B16..8: 27.3%  6.5%  0.8%  direct: 1.0%  skip:64.3%  L0:32.7% L1:59.2% BI: 8.1%
[libx264 @ 0x65e720] coded y,uvDC,uvAC intra: 43.2% 68.4% 38.4% inter: 8.9% 10.2% 1.2%
[libx264 @ 0x65e720] i16 v,h,dc,p: 39% 36% 17%  9%
[libx264 @ 0x65e720] i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 27% 26% 16%  5%  6%  5%  6%  4%  6%
[libx264 @ 0x65e720] i8c dc,h,v,p: 40% 29% 26%  5%
[libx264 @ 0x65e720] Weighted P-Frames: Y:0.7% UV:0.2%
[libx264 @ 0x65e720] ref P L0: 74.1%  6.1% 12.9%  6.8%  0.0%
[libx264 @ 0x65e720] ref B L0: 88.9% 11.1%
[libx264 @ 0x65e720] kb/s:214.56

```

Thx in advance

---

### Post by alfirdaous on 2013-03-05
anyone have an idea of this issue

---

### Post by FakeOutdoorsman on 2013-03-06
It would be useful to know what the difference is between a file that works and does not work. Please show the output of:
```
ffprobe -show_format -show_streams -i working_file.mp4
ffprobe -show_format -show_streams -i broken_file.mp4
```
The other factor: is it a decoding (Totem) and/or encoding (the libav "ffmpeg") issue? Try a recent, static build of real ffmpeg to rule out the usually buggy libav version of their fake, so-called "ffmpeg". No need to install; just download the archive, extract it, and run the binary: [example instructions](http://ubuntuforums.org/showthread.php?t=2121268&p=12536453&viewfull=1#post12536453) (you can omit the drawtext filter if the static build does not support it).

---

### Post by alfirdaous on 2013-03-06
I downloaded the files from a website with avi extension, the rest I download from youtube and other sources the encoding works, BUT the input file is working fine:

```

~$ ffprobe -show_format -show_streams -i Input.avi 
avprobe version 0.8.5-6:0.8.5-0ubuntu0.12.10.1, Copyright (c) 2007-2012 the Libav developers
  built on Jan 24 2013 14:49:20 with gcc 4.7.2
Unrecognized option 'i'
Failed to set value 'Input.avi' for option 'i'


~$ ffprobe -show_format -show_streams -i Output.mp4 
avprobe version 0.8.5-6:0.8.5-0ubuntu0.12.10.1, Copyright (c) 2007-2012 the Libav developers
  built on Jan 24 2013 14:49:20 with gcc 4.7.2
Unrecognized option 'i'
Failed to set value 'Output.mp4' for option 'i'

```

if I remove the option -i:

Input
```

~$ ffprobe -show_format -show_streams Input.avi 
avprobe version 0.8.5-6:0.8.5-0ubuntu0.12.10.1, Copyright (c) 2007-2012 the Libav developers
  built on Jan 24 2013 14:49:20 with gcc 4.7.2
[avi @ 0x1348b20] max_analyze_duration reached
Input #0, avi, from 'Input.avi':
  Metadata:
    encoder         : MEncoder Sherpya-SVN-r33488-4.2.5
  Duration: 00:25:29.76, start: 0.000000, bitrate: 612 kb/s
    Stream #0.0: Video: h264 (High), yuv420p, 352x288 [PAR 1:1 DAR 11:9], 25 fps, 25 tbr, 25 tbn, 50 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 128 kb/s
[STREAM]
index=0
codec_name=h264
codec_long_name=H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10
codec_type=video
codec_time_base=1/50
codec_tag_string=H264
codec_tag=0x34363248
width=352
height=288
has_b_frames=0
sample_aspect_ratio=1:1
display_aspect_ratio=11:9
pix_fmt=yuv420p
level=13
r_frame_rate=25/1
avg_frame_rate=25/1
time_base=1/25
start_time=0.000000 
duration=1529.760000 
nb_frames=38244
[/STREAM]
[STREAM]
index=1
codec_name=mp3
codec_long_name=MP3 (MPEG audio layer 3)
codec_type=audio
codec_time_base=1/48000
codec_tag_string=U[0][0][0]
codec_tag=0x0055
sample_rate=48000.000000 
channels=2
bits_per_sample=0
r_frame_rate=0/0
avg_frame_rate=125/3
time_base=1/16000
start_time=0.000000 
duration=N/A
nb_frames=24475296
[/STREAM]
[FORMAT]
filename=Input.avi
nb_streams=2
format_name=avi
format_long_name=AVI format
start_time=0.000000 
duration=1529.760000 
size=117142730.000000 
bit_rate=612607.000000 
TAG:encoder=MEncoder Sherpya-SVN-r33488-4.2.5
[/FORMAT]

```

Output:
```

~$ ffprobe -show_format -show_streams Output.mp4 
avprobe version 0.8.5-6:0.8.5-0ubuntu0.12.10.1, Copyright (c) 2007-2012 the Libav developers
  built on Jan 24 2013 14:49:20 with gcc 4.7.2
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Output.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 512
    compatible_brands: isomiso2avc1mp41
    encoder         : Lavf53.21.1
  Duration: 00:25:29.76, start: 0.000000, bitrate: 214 kb/s
    Stream #0.0(und): Video: h264 (Main), yuv420p, 352x288 [PAR 1:1 DAR 11:9], 211 kb/s, 25 fps, 25 tbr, 25 tbn, 50 tbc
    Stream #0.1(und): Audio: mp3, 48000 Hz, stereo, s16, 128 kb/s
[STREAM]
index=0
codec_name=h264
codec_long_name=H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10
codec_type=video
codec_time_base=1/50
codec_tag_string=avc1
codec_tag=0x31637661
width=352
height=288
has_b_frames=1
sample_aspect_ratio=1:1
display_aspect_ratio=11:9
pix_fmt=yuv420p
level=13
r_frame_rate=25/1
avg_frame_rate=25/1
time_base=1/25
start_time=0.000000 
duration=1529.760000 
nb_frames=38244
TAG:language=und
[/STREAM]
[STREAM]
index=1
codec_name=mp3
codec_long_name=MP3 (MPEG audio layer 3)
codec_type=audio
codec_time_base=1/48000
codec_tag_string=mp4a
codec_tag=0x6134706d
sample_rate=48000.000000 
channels=2
bits_per_sample=0
r_frame_rate=0/0
avg_frame_rate=0/0
time_base=1/48000
start_time=0.000000 
duration=5.010000 
nb_frames=208
TAG:language=und
[/STREAM]
[FORMAT]
filename=Output.mp4
nb_streams=2
format_name=mov,mp4,m4a,3gp,3g2,mj2
format_long_name=QuickTime/MPEG-4/Motion JPEG 2000 format
start_time=0.000000 
duration=1529.760000 
size=40997144.000000 
bit_rate=214397.000000 
TAG:major_brand=isom
TAG:minor_version=512
TAG:compatible_brands=isomiso2avc1mp41
TAG:encoder=Lavf53.21.1
[/FORMAT]

```

---

### Post by FakeOutdoorsman on 2013-03-07
> **alfirdaous said:**
> I can play movies, MP3 files,... the probleme is coming from some videos only:

This is why I asked for a broken and working outputs. I assumed that you had some outputs that were working and some that were not. The inputs are less important.

---

### Post by alfirdaous on 2013-03-07
Yes, there is problem with some outputs only, inputs are all OK, that's why I said may the problem is coming from the encoding method

---

