---
title: "Ffmpeg says sound was recorded but I don't hear anything..."
date: 2014-02-26
forum: Multimedia Software
---

### Post by vivienneanthony on 2014-02-26
Hello,

I spent the last couple of minutes and a whole day trying to get ffmpeg to record my desktop sound. I rebuilt ffmpeg, x264, and yasm. I run Ubuntu 12.04 on a system. Could someone  assist because I'm at a lost. I've read the FFMPEG manual but I should not be having problems. It seems to be a simple fix but I don't what. 

I posted the results of the command line.

Vivienne


Vivienne@vivienne-System-Product-Name:~$ ffmpeg -f alsa -ac 2 -i plughw:0,0 -f x11grab -r 100 -s 1440x900 -i :0.0 -acodec pcm_s16le -vcodec libx264 -preset ultrafast -threads 5 output.mkv
ffmpeg version 2.1.4 Copyright (c) 2000-2014 the FFmpeg developers
  built on Feb 26 2014 02:08:53 with gcc 4.6 (Ubuntu/Linaro 4.6.3-1ubuntu5)
  configuration: --enable-gpl --enable-libx264 --enable-x11grab --enable-libpulse
  libavutil      52. 48.101 / 52. 48.101
  libavcodec     55. 39.101 / 55. 39.101
  libavformat    55. 19.104 / 55. 19.104
  libavdevice    55.  5.100 / 55.  5.100
  libavfilter     3. 90.100 /  3. 90.100
  libswscale      2.  5.101 /  2.  5.101
  libswresample   0. 17.104 /  0. 17.104
  libpostproc    52.  3.100 / 52.  3.100
Guessed Channel Layout for  Input Stream #0.0 : stereo
Input #0, alsa, from 'plughw:0,0':
  Duration: N/A, start: 1393436235.476264, bitrate: 1536 kb/s
    Stream #0:0: Audio: pcm_s16le, 48000 Hz, stereo, s16, 1536 kb/s
[x11grab @ 0x3233040] device: :0.0 -> display: :0.0 x: 0 y: 0 width: 1440 height: 900
[x11grab @ 0x3233040] shared memory extension found
Input #1, x11grab, from ':0.0':
  Duration: N/A, start: 1393436235.489139, bitrate: N/A
    Stream #1:0: Video: rawvideo (BGR[0] / 0x524742), bgr0, 1440x900, -2147483 kb/s, 100 tbr, 1000k tbn, 100 tbc
File 'output.mkv' already exists. Overwrite ? [y/N] y
[swscaler @ 0x32030c0] deprecated pixel format used, make sure you did set range correctly
No pixel format specified, yuv444p for H.264 encoding chosen.
Use -pix_fmt yuv420p for compatibility with outdated media players.
[libx264 @ 0x3255160] using cpu capabilities: MMX2 SSE2Fast SSSE3 SSE4.2 AVX
[libx264 @ 0x3255160] profile High 4:4:4 Predictive, level 4.2, 4:4:4 8-bit
[libx264 @ 0x3255160] 264 - core 142 r2389 956c8d8 - H.264/MPEG-4 AVC codec - Copyleft 2003-2014 - [http://www.videolan.org/x264.html](http://www.videolan.org/x264.html) - options: cabac=0 ref=1 deblock=0:0:0 analyse=0:0 me=dia subme=0 psy=1 psy_rd=1.00:0.00 mixed_ref=0 me_range=16 chroma_me=1 trellis=0 8x8dct=0 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=6 threads=5 lookahead_threads=1 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=0 weightp=0 keyint=250 keyint_min=25 scenecut=0 intra_refresh=0 rc=crf mbtree=0 crf=23.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.40 aq=0
Output #0, matroska, to 'output.mkv':
  Metadata:
    encoder         : Lavf55.19.104
    Stream #0:0: Video: h264 (libx264) (H264 / 0x34363248), yuv444p, 1440x900, q=-1--1, 1k tbn, 100 tbc
    Stream #0:1: Audio: pcm_s16le ([1][0][0][0] / 0x0001), 48000 Hz, stereo, s16, 1536 kb/s
Stream mapping:
  Stream #1:0 -> #0:0 (rawvideo -> libx264)
  Stream #0:0 -> #0:1 (pcm_s16le -> pcm_s16le)
Press [q] to stop, [?] for help
[alsa @ 0x32212a0] ALSA buffer xrun.
[alsa @ 0x32212a0] ALSA buffer xrun. 357kB time=00:00:02.27 bitrate=1285.7kbits/s    
frame= 4233 fps=101 q=-1.0 Lsize=   25553kB time=00:00:43.93 bitrate=4764.1kbits/s    
video:17880kB audio:7613kB subtitle:0 global headers:0kB muxing overhead 0.232233%
[libx264 @ 0x3255160] frame I:17    Avg QP:16.18  size:217815
[libx264 @ 0x3255160] frame P:4216  Avg QP:19.07  size:  3464
[libx264 @ 0x3255160] mb I  I16..4: 100.0%  0.0%  0.0%
[libx264 @ 0x3255160] mb P  I16..4:  0.6%  0.0%  0.0%  P16..4:  8.0%  0.0%  0.0%  0.0%  0.0%    skip:91.4%
[libx264 @ 0x3255160] coded y,u,v intra: 26.6% 5.9% 5.0% inter: 2.4% 0.6% 0.6%
[libx264 @ 0x3255160] i16 v,h,dc,p: 34% 40% 10% 16%
[libx264 @ 0x3255160] kb/s:3460.20

---

### Post by FakeOutdoorsman on 2014-02-26
What player(s) are you using? How do you know there is no audio? Please use the [code tag](http://ubuntuforums.org/misc.php?do=bbcode#code) next time to format your command and console output. You've enabled the [pulse input device](http://ffmpeg.org/ffmpeg-devices.html#pulse), but you're using the [alsa input device](http://ffmpeg.org/ffmpeg-devices.html#alsa-1). Does it make a difference if you change "-f alsa" to "-f pulse"? Does arecord capture the audio properly?

---

### Post by vivienneanthony on 2014-02-26
> **FakeOutdoorsman said:**
> What player(s) are you using? How do you know there is no audio? Please use the [code tag]("http://ubuntuforums.org/misc.php?do=bbcode#code") next time to format your command and console output. You've enabled the [pulse input device]("http://ffmpeg.org/ffmpeg-devices.html#pulse"), but you're using the [alsa input device]("http://ffmpeg.org/ffmpeg-devices.html#alsa-1"). Does it make a difference if you change "-f alsa" to "-f pulse"? Does arecord capture the audio properly?

I tried Banshee, Dragon, Movie, and VLC player. I also tried Blender video editor. I hear no sound no matter which one I choose. The files says audio is recorded but I get nothing.

---

### Post by Yellow Pasque on 2014-02-26
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by vivienneanthony on 2014-02-26
> **FakeOutdoorsman said:**
> What player(s) are you using? How do you know there is no audio? Please use the [code tag]("http://ubuntuforums.org/misc.php?do=bbcode#code") next time to format your command and console output. You've enabled the [pulse input device]("http://ffmpeg.org/ffmpeg-devices.html#pulse"), but you're using the [alsa input device]("http://ffmpeg.org/ffmpeg-devices.html#alsa-1"). Does it make a difference if you change "-f alsa" to "-f pulse"? Does arecord capture the audio properly?

This gives me some audio but there is a high pitch or feedback that I get using this method.

```

 ffmpeg -f pulse -i default -f x11grab -r 100 -s 1440x900 -i :0.0 -acodec vorbis -strict -2 -ab 192 -aq 4 -vcodec libx264 -threads 0 output.mkv
ffmpeg version 2.1.4 Copyright (c) 2000-2014 the FFmpeg developers
  built on Feb 26 2014 02:08:53 with gcc 4.6 (Ubuntu/Linaro 4.6.3-1ubuntu5)
  configuration: --enable-gpl --enable-libx264 --enable-x11grab --enable-libpulse
  libavutil      52. 48.101 / 52. 48.101
  libavcodec     55. 39.101 / 55. 39.101
  libavformat    55. 19.104 / 55. 19.104
  libavdevice    55.  5.100 / 55.  5.100
  libavfilter     3. 90.100 /  3. 90.100
  libswscale      2.  5.101 /  2.  5.101
  libswresample   0. 17.104 /  0. 17.104
  libpostproc    52.  3.100 / 52.  3.100
Guessed Channel Layout for  Input Stream #0.0 : stereo
Input #0, pulse, from 'default':
  Duration: N/A, start: 0.307605, bitrate: 1536 kb/s
    Stream #0:0: Audio: pcm_s16le, 48000 Hz, stereo, s16, 1536 kb/s
[x11grab @ 0x22b2b40] device: :0.0 -> display: :0.0 x: 0 y: 0 width: 1440 height: 900
[x11grab @ 0x22b2b40] shared memory extension found
Input #1, x11grab, from ':0.0':
  Duration: N/A, start: 1393442051.275833, bitrate: N/A
    Stream #1:0: Video: rawvideo (BGR[0] / 0x524742), bgr0, 1440x900, -2147483 kb/s, 100 tbr, 1000k tbn, 100 tbc
File 'output.mkv' already exists. Overwrite ? [y/N] y
[swscaler @ 0x229b120] deprecated pixel format used, make sure you did set range correctly
No pixel format specified, yuv444p for H.264 encoding chosen.                                                                        
Use -pix_fmt yuv420p for compatibility with outdated media players.                                                                  
[libx264 @ 0x22d1d20] using cpu capabilities: MMX2 SSE2Fast SSSE3 SSE4.2 AVX
[libx264 @ 0x22d1d20] profile High 4:4:4 Predictive, level 4.2, 4:4:4 8-bit
[libx264 @ 0x22d1d20] 264 - core 142 r2389 956c8d8 - H.264/MPEG-4 AVC codec - Copyleft 2003-2014 - http://www.videolan.org/x264.html - options: cabac=1 ref=3 deblock=1:0:0 analyse=0x3:0x113 me=hex subme=7 psy=1 psy_rd=1.00:0.00 mixed_ref=1 me_range=16 chroma_me=1 trellis=1 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=4 threads=12 lookahead_threads=2 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=3 b_pyramid=2 b_adapt=1 b_bias=0 direct=1 weightb=1 open_gop=0 weightp=2 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=40 rc=crf mbtree=1 crf=23.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.40 aq=1:1.00
[vorbis @ 0x22d2a20] Bitrate 192 is extremely low, maybe you mean 192k
Output #0, matroska, to 'output.mkv':
  Metadata:
    encoder         : Lavf55.19.104
    Stream #0:0: Video: h264 (libx264) (H264 / 0x34363248), yuv444p, 1440x900, q=-1--1, 1k tbn, 100 tbc
    Stream #0:1: Audio: vorbis (oV[0][0] / 0x566F), 48000 Hz, stereo, fltp
Stream mapping:
  Stream #1:0 -> #0:0 (rawvideo -> libx264)
  Stream #0:0 -> #0:1 (pcm_s16le -> vorbis)
Press [q] to stop, [?] for help
frame= 4782 fps= 97 q=-1.0 Lsize=    5807kB time=00:00:47.80 bitrate= 995.3kbits/s    
video:4361kB audio:1398kB subtitle:0 global headers:3kB muxing overhead 0.791445%
[libx264 @ 0x22d1d20] frame I:20    Avg QP:21.51  size:121653
[libx264 @ 0x22d1d20] frame P:1285  Avg QP:22.16  size:  1324
[libx264 @ 0x22d1d20] frame B:3477  Avg QP:36.50  size:    95
[libx264 @ 0x22d1d20] consecutive B-frames:  2.9%  0.3%  0.2% 96.6%
[libx264 @ 0x22d1d20] mb I  I16..4: 32.0% 30.8% 37.1%
[libx264 @ 0x22d1d20] mb P  I16..4:  0.5%  0.4%  0.3%  P16..4:  1.1%  0.4%  0.2%  0.0%  0.0%    skip:97.1%
[libx264 @ 0x22d1d20] mb B  I16..4:  0.0%  0.0%  0.0%  B16..8:  0.9%  0.0%  0.0%  direct: 0.0%  skip:99.0%  L0:40.6% L1:59.1% BI: 0.3%
[libx264 @ 0x22d1d20] 8x8 transform intra:32.6% inter:63.4%
[libx264 @ 0x22d1d20] coded y,u,v intra: 30.8% 4.7% 4.2% inter: 0.2% 0.0% 0.0%
[libx264 @ 0x22d1d20] i16 v,h,dc,p: 32% 64%  2%  1%
[libx264 @ 0x22d1d20] i8 v,h,dc,ddl,ddr,vr,hd,vl,hu: 38% 19% 31%  2%  2%  2%  2%  2%  3%
[libx264 @ 0x22d1d20] i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 34% 33% 12%  2%  3%  4%  4%  3%  4%
[libx264 @ 0x22d1d20] Weighted P-Frames: Y:0.4% UV:0.3%
[libx264 @ 0x22d1d20] ref P L0: 72.1% 15.0% 10.3%  2.6%  0.0%
[libx264 @ 0x22d1d20] ref B L0: 65.1% 34.0%  0.9%
[libx264 @ 0x22d1d20] ref B L1: 97.0%  3.0%
[libx264 @ 0x22d1d20] kb/s:746.93



```

---

### Post by vivienneanthony on 2014-02-26
> **Temüjin said:**
> [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

I was able to get the sound to come through using pulseaudio but I get a lot of high pitch or feedback like the audio is in the distance.

---

### Post by FakeOutdoorsman on 2014-02-26
Are you sure you chose the correct pulse device? See [HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?p=8746719#post8746719) for a description of using pavucontrol.

---

### Post by vivienneanthony on 2014-02-26
> **FakeOutdoorsman said:**
> Are you sure you chose the correct pulse device? See [HOWTO: Proper Screencasting on Linux]("http://ubuntuforums.org/showthread.php?p=8746719#post8746719") for a description of using pavucontrol.

Thank you. That helped a lot.

---

