---
title: "FFMPEG compiling"
date: 2016-08-16
forum: Multimedia Software
---

### Post by alfirdaous on 2016-08-16
Hello everyone,

I change from installing FFMPEG using apt-get install ffmpeg to download it from a website referring to [this link]("https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu"), using the compile method not the apt-get install Item, I faced this problem:


```

ffmpeg -y -i INPUT.mp4 -ss 00:01:23 -t 00:00:10 -strict experimental -vf drawtext=fontfile='/usr/share/fonts/truetype/freefont/FreeSansBold.ttf':text='text':x=10:y=10:fontsize=18:fontcolor=white -vcodec libx264 -preset medium -crf 24 -acodec copy OUTPUT.mp4


ffmpeg version N-81342-gb93e223 Copyright (c) 2000-2016 the FFmpeg developers
  built with gcc 5.4.0 (Ubuntu 5.4.0-6ubuntu1~16.04.2) 20160609
  configuration: 
  libavutil      55. 28.100 / 55. 28.100
  libavcodec     57. 51.102 / 57. 51.102
  libavformat    57. 46.101 / 57. 46.101
  libavdevice    57.  0.102 / 57.  0.102
  libavfilter     6. 51.100 /  6. 51.100
  libswscale      4.  1.100 /  4.  1.100
  libswresample   2.  1.100 /  2.  1.100
Unrecognized option 'preset'.
Error splitting the argument list: Option not found

```

Thank you for your support

[B]EDIT:

I changed it to:

[/B]```

 -c:v libx264 -pre medium -crf 24 -acodec copy

```

Then I've got this:

```

ffmpeg version N-81342-gb93e223 Copyright (c) 2000-2016 the FFmpeg developers
  built with gcc 5.4.0 (Ubuntu 5.4.0-6ubuntu1~16.04.2) 20160609
  configuration: 
  libavutil      55. 28.100 / 55. 28.100
  libavcodec     57. 51.102 / 57. 51.102
  libavformat    57. 46.101 / 57. 46.101
  libavdevice    57.  0.102 / 57.  0.102
  libavfilter     6. 51.100 /  6. 51.100
  libswscale      4.  1.100 /  4.  1.100
  libswresample   2.  1.100 /  2.  1.100
Unrecognized option 'crf'.
Error splitting the argument list: Option not found

```

---

### Post by mc4man on 2016-08-16
Open a terminal, just run command of ffmpeg & post output to see your configuration.

---

### Post by alfirdaous on 2016-08-16
The ffmpeg output is:

```

# ffmpeg
ffmpeg version N-81342-gb93e223 Copyright (c) 2000-2016 the FFmpeg developers
  built with gcc 5.4.0 (Ubuntu 5.4.0-6ubuntu1~16.04.2) 20160609
  configuration: 
  libavutil      55. 28.100 / 55. 28.100
  libavcodec     57. 51.102 / 57. 51.102
  libavformat    57. 46.101 / 57. 46.101
  libavdevice    57.  0.102 / 57.  0.102
  libavfilter     6. 51.100 /  6. 51.100
  libswscale      4.  1.100 /  4.  1.100
  libswresample   2.  1.100 /  2.  1.100
Hyper fast Audio and Video encoder
usage: ffmpeg [options] [[infile options] -i infile]... {[outfile options] outfile}...


Use -h to get full help or, even better, run 'man ffmpeg'

```

and the ffmpeg version is:

```

# ffmpeg -version
ffmpeg version N-81342-gb93e223 Copyright (c) 2000-2016 the FFmpeg developers
built with gcc 5.4.0 (Ubuntu 5.4.0-6ubuntu1~16.04.2) 20160609
configuration: 
libavutil      55. 28.100 / 55. 28.100
libavcodec     57. 51.102 / 57. 51.102
libavformat    57. 46.101 / 57. 46.101
libavdevice    57.  0.102 / 57.  0.102
libavfilter     6. 51.100 /  6. 51.100
libswscale      4.  1.100 /  4.  1.100
libswresample   2.  1.100 /  2.  1.100

```

and the full ffmpeg command is:

```

# ffmpeg -y -i INPUT.mp4 -ss 00:01:23 -t 00:00:10 -strict experimental -vf drawtext=fontfile='/usr/share/fonts/truetype/freefont/FreeSansBold.ttf':text='www.site.com':x=10:y=10:fontsize=18:fontcolor=white -c:v libx264 -pre medium -crf 24 -acodec copy OUTPUT.mp4
ffmpeg version N-81342-gb93e223 Copyright (c) 2000-2016 the FFmpeg developers
  built with gcc 5.4.0 (Ubuntu 5.4.0-6ubuntu1~16.04.2) 20160609
  configuration: 
  libavutil      55. 28.100 / 55. 28.100
  libavcodec     57. 51.102 / 57. 51.102
  libavformat    57. 46.101 / 57. 46.101
  libavdevice    57.  0.102 / 57.  0.102
  libavfilter     6. 51.100 /  6. 51.100
  libswscale      4.  1.100 /  4.  1.100
  libswresample   2.  1.100 /  2.  1.100
Unrecognized option 'crf'.
Error splitting the argument list: Option not found

```

---

### Post by mc4man on 2016-08-17
If you were following that link you need to do it from  top  to bottom of the _page_. Your current build is practically un-configured & of little value. 
So you should start again.
Ex. here on personal build
$ ffmpeg2
ffmpeg version N-80950-g3cdd5f4 Copyright (c) 2000-2016 the FFmpeg developers
  built with gcc 5.3.1 (Ubuntu 5.3.1-14ubuntu2.1) 20160413
  configuration: --extra-libs=-ldl --prefix=/opt/ffmpeg --enable-avresample --disable-debug --enable-nonfree --enable-gpl --enable-version3 --enable-libopencore-amrnb --enable-libopencore-amrwb --disable-decoder=amrnb --disable-decoder=amrwb --enable-libpulse --enable-libfreetype --enable-gnutls --enable-libx264 --enable-libx265 --enable-libfdk-aac --enable-libvorbis --enable-libmp3lame --enable-libopus --enable-libvpx --enable-libspeex --enable-libass --enable-avisynth --enable-libsoxr --enable-libxvid --enable-libvidstab --enable-libtheora --enable-libwavpack --enable-libopenjpeg --enable-libgsm

The configure that link uses is this so that's what you should be seeing
```
./configure \
  --prefix="$HOME/ffmpeg_build" \
  --pkg-config-flags="--static" \
  --extra-cflags="-I$HOME/ffmpeg_build/include" \
  --extra-ldflags="-L$HOME/ffmpeg_build/lib" \
  --bindir="$HOME/bin" \
  --enable-gpl \
  --enable-libass \
  --enable-libfdk-aac \
  --enable-libfreetype \
  --enable-libmp3lame \
  --enable-libopus \
  --enable-libtheora \
  --enable-libvorbis \
  --enable-libvpx \
  --enable-libx264 \
  --enable-libx265 \
  --enable-nonfree
```

Note that recent releases &  the current master no longer needs -strict experimental

---

### Post by alfirdaous on 2016-08-17
So how can I delete all these files and restart from the beginning?

---

### Post by mc4man on 2016-08-18
At the very bottom of your linked page 
>  Updating FFmpeg

Development of FFmpeg is active and an occasional update can give you new features and bug fixes. First you need to delete (or move) the old files:

rm -rf ~/ffmpeg_build ~/ffmpeg_sources ~/bin/{ffmpeg,ffprobe,ffplay,ffserver,vsyasm,x264,x265,yasm,ytasm}
[B]
Now just follow the guide from the beginning[/B].
> Reverting Changes Made by This Guide

rm -rf ~/ffmpeg_build ~/ffmpeg_sources ~/bin/{ffmpeg,ffprobe,ffplay,ffserver,vsyasm,x264,x265,yasm,ytasm}
sudo apt-get autoremove autoconf automake build-essential cmake libass-dev libfreetype6-dev \
  libmp3lame-dev libopus-dev libsdl1.2-dev libtheora-dev libtool libva-dev libvdpau-dev \
  libvorbis-dev libvpx-dev libx264-dev libxcb1-dev libxcb-shm0-dev ibxcb-xfixes0-dev mercurial texinfo zlib1g-dev
sed -i '/ffmpeg_build/c\' ~/.manpath
hash -r
Either one will do the deed.

---

### Post by alfirdaous on 2016-08-19
I still get the same error:

```

# ffmpeg -y -i INPUT.mp4 -ss 00:01:23 -t 00:00:10 -strict experimental -vf drawtext=fontfile='/usr/share/fonts/truetype/freefont/FreeSansBold.ttf':text='www.site.com':x=10:y=10:fontsize=18:fontcolor=white -c:v libx264 -pre medium -crf 24 -acodec copy OUTPUT.mp4
ffmpeg version N-81342-gb93e223 Copyright (c) 2000-2016 the FFmpeg developers
  built with gcc 5.4.0 (Ubuntu 5.4.0-6ubuntu1~16.04.2) 20160609
  configuration: 
  libavutil      55. 28.100 / 55. 28.100
  libavcodec     57. 51.102 / 57. 51.102
  libavformat    57. 46.101 / 57. 46.101
  libavdevice    57.  0.102 / 57.  0.102
  libavfilter     6. 51.100 /  6. 51.100
  libswscale      4.  1.100 /  4.  1.100
  libswresample   2.  1.100 /  2.  1.100
Unrecognized option 'crf'.
Error splitting the argument list: Option not found

```


if I remove that option, I get this error:

```

ffmpeg version N-81342-gb93e223 Copyright (c) 2000-2016 the FFmpeg developers
  built with gcc 5.4.0 (Ubuntu 5.4.0-6ubuntu1~16.04.2) 20160609
  configuration: 
  libavutil      55. 28.100 / 55. 28.100
  libavcodec     57. 51.102 / 57. 51.102
  libavformat    57. 46.101 / 57. 46.101
  libavdevice    57.  0.102 / 57.  0.102
  libavfilter     6. 51.100 /  6. 51.100
  libswscale      4.  1.100 /  4.  1.100
  libswresample   2.  1.100 /  2.  1.100
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Original/alfirdaous.com_MohamadAssayed_SawaedAlEkhae4_001-Original.mp4':
  Metadata:
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: isommp42
    creation_time   : 2016-06-07 11:34:53
  Duration: 00:27:37.09, start: 0.000000, bitrate: 575 kb/s
    Stream #0:0(und): Video: h264 (Constrained Baseline) (avc1 / 0x31637661), yuv420p(tv, bt709), 640x360 [SAR 1:1 DAR 16:9], 476 kb/s, 25 fps, 25 tbr, 25 tbn, 50 tbc (default)
    Metadata:
      handler_name    : VideoHandler
    Stream #0:1(eng): Audio: aac (LC) (mp4a / 0x6134706D), 44100 Hz, stereo, fltp, 95 kb/s (default)
    Metadata:
      creation_time   : 2016-06-07 11:35:10
      handler_name    : IsoMedia File Produced by Google, 5-11-2011
Unknown encoder 'libx264'

```

however, I already compiled the libx264

---

### Post by mc4man on 2016-08-19
Your configuration: is still empty, all of those code boxes in your link, each  are _1 complete command_. I think you may be breaking them up??
Maybe just remove all  & just  go - 
```
sudo apt install ffmpeg
```

---

### Post by alfirdaous on 2016-08-20
Well, everything was messed up, I reinstall the server (test server), and I've got this error while trying to encode a video

```

[mp4 @ 0x28a8320] Codec for stream 1 does not use global headers but container format requires global headers

```

---

### Post by FakeOutdoorsman on 2016-08-24
You should show your command and the complete console output.

---

### Post by alfirdaous on 2016-08-24
This is the command line:

```

ffmpeg -y -i INPUT.mp4 -ss 00:00:55 -t 00:00:10 -strict experimental -vf drawtext=fontfile='/usr/share/fonts/truetype/dejavu/DejaVuSans-Bold.ttf':text='www.alfirdaous.com':x=10:y=5:fontsize=18:fontcolor=white -vcodec libx264 -preset medium -crf 24 -acodec copy -flags -global_header OUTPUT.mp4

```


Console output
```

 handler_name    : IsoMedia File Produced by Google, 5-11-2011
[libx264 @ 0x71d520] using SAR=1/1
[libx264 @ 0x71d520] using cpu capabilities: MMX2 SSE2Fast SSSE3 Cache64 SlowCTZ SlowAtom SlowPshufb
[libx264 @ 0x71d520] profile High, level 3.0
[libx264 @ 0x71d520] 264 - core 148 r2643 5c65704 - H.264/MPEG-4 AVC codec - Copyleft 2003-2015 - http://www.videolan.org/x264.html - options: cabac=1 ref=3 deblock=1:0:0 analyse=0x3:0x113 me=hex subme=7 psy=1 psy_rd=1.00:0.00 mixed_ref=1 me_range=16 chroma_me=1 trellis=1 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=3 lookahead_threads=1 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=3 b_pyramid=2 b_adapt=1 b_bias=0 direct=1 weightb=1 open_gop=0 weightp=2 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=40 rc=crf mbtree=1 crf=24.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.40 aq=1:1.00
[mp4 @ 0x883880] Using AVStream.codec to pass codec parameters to muxers is deprecated, use AVStream.codecpar instead.
    Last message repeated 1 times
Output #0, mp4, to &#8216;OUTPUT.mp4':
  Metadata:
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: isommp42
    encoder         : Lavf57.41.100
    Stream #0:0(und): Video: h264 (libx264) ([33][0][0][0] / 0x0021), yuv420p, 640x360 [SAR 1:1 DAR 16:9], q=-1--1, 25 fps, 12800 tbn, 25 tbc (default)
    Metadata:
      handler_name    : VideoHandler
      encoder         : Lavc57.48.101 libx264
    Side data:
      cpb: bitrate max/min/avg: 0/0/0 buffer size: 0 vbv_delay: -1
    Stream #0:1(eng): Audio: aac (LC) ([64][0][0][0] / 0x0040), 44100 Hz, stereo, 95 kb/s (default)
    Metadata:
      creation_time   : 2016-06-08 09:50:59
      handler_name    : IsoMedia File Produced by Google, 5-11-2011
Stream mapping:
  Stream #0:0 -> #0:0 (h264 (native) -> h264 (libx264))
  Stream #0:1 -> #0:1 (copy)
Press [q] to stop, [?] for help
frame=   54 fps= 11 q=29.0 size=       9kB time=00:00:01.97 bitrate=  38.4kbits/s speed=0.388x    


```

---

### Post by alfirdaous on 2016-08-24
This is the command line:<br>
<br>
```
<br>
ffmpeg -y -i INPUT.mp4 -ss 00:00:55 -t 00:00:10 -strict experimental -vf drawtext=fontfile='/usr/share/fonts/truetype/dejavu/DejaVuSans-Bold.ttf':text='www.alfirdaous.com':x=10:y=5:fontsize=18:fontcolor=white -vcodec libx264 -preset medium -crf 24 -acodec copy -flags -global_header OUTPUT.mp4<br>

```<br>
<br>
<br>
Console output<br>
```
<br>
&nbsp;handler_name &nbsp; &nbsp;: IsoMedia File Produced by Google, 5-11-2011<br>
[libx264 @ 0x71d520] using SAR=1/1<br>
[libx264 @ 0x71d520] using cpu capabilities: MMX2 SSE2Fast SSSE3 Cache64 SlowCTZ SlowAtom SlowPshufb<br>
[libx264 @ 0x71d520] profile High, level 3.0<br>
[libx264 @ 0x71d520] 264 - core 148 r2643 5c65704 - H.264/MPEG-4 AVC codec - Copyleft 2003-2015 - http://www.videolan.org/x264.html - options: cabac=1 ref=3 deblock=1:0:0 analyse=0x3:0x113 me=hex subme=7 psy=1 psy_rd=1.00:0.00 mixed_ref=1 me_range=16 chroma_me=1 trellis=1 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=3 lookahead_threads=1 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=3 b_pyramid=2 b_adapt=1 b_bias=0 direct=1 weightb=1 open_gop=0 weightp=2 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=40 rc=crf mbtree=1 crf=24.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.40 aq=1:1.00<br>
[mp4 @ 0x883880] Using AVStream.codec to pass codec parameters to muxers is deprecated, use AVStream.codecpar instead.<br>
&nbsp;&nbsp; &nbsp;Last message repeated 1 times<br>
Output #0, mp4, to ‘OUTPUT.mp4':<br>
&nbsp;&nbsp;Metadata:<br>
&nbsp;&nbsp; &nbsp;major_brand &nbsp; &nbsp; : mp42<br>
&nbsp;&nbsp; &nbsp;minor_version &nbsp; : 0<br>
&nbsp;&nbsp; &nbsp;compatible_brands: isommp42<br>
&nbsp;&nbsp; &nbsp;encoder &nbsp; &nbsp; &nbsp; &nbsp; : Lavf57.41.100<br>
&nbsp;&nbsp; &nbsp;Stream #0:0(und): Video: h264 (libx264) ([33][0][0][0] / 0x0021), yuv420p, 640x360 [SAR 1:1 DAR 16:9], q=-1--1, 25 fps, 12800 tbn, 25 tbc (default)<br>
&nbsp;&nbsp; &nbsp;Metadata:<br>
&nbsp;&nbsp; &nbsp; &nbsp;handler_name &nbsp; &nbsp;: VideoHandler<br>
&nbsp;&nbsp; &nbsp; &nbsp;encoder &nbsp; &nbsp; &nbsp; &nbsp; : Lavc57.48.101 libx264<br>
&nbsp;&nbsp; &nbsp;Side data:<br>
&nbsp;&nbsp; &nbsp; &nbsp;cpb: bitrate max/min/avg: 0/0/0 buffer size: 0 vbv_delay: -1<br>
&nbsp;&nbsp; &nbsp;Stream #0:1(eng): Audio: aac (LC) ([64][0][0][0] / 0x0040), 44100 Hz, stereo, 95 kb/s (default)<br>
&nbsp;&nbsp; &nbsp;Metadata:<br>
&nbsp;&nbsp; &nbsp; &nbsp;creation_time &nbsp; : 2016-06-08 09:50:59<br>
&nbsp;&nbsp; &nbsp; &nbsp;handler_name &nbsp; &nbsp;: IsoMedia File Produced by Google, 5-11-2011<br>
Stream mapping:<br>
&nbsp;&nbsp;Stream #0:0 -&gt; #0:0 (h264 (native) -&gt; h264 (libx264))<br>
&nbsp;&nbsp;Stream #0:1 -&gt; #0:1 (copy)<br>
Press [q] to stop, [?] for help<br>
frame= &nbsp; 54 fps= 11 q=29.0 size= &nbsp; &nbsp; &nbsp; 9kB time=00:00:01.97 bitrate= &nbsp;38.4kbits/s speed=0.388x &nbsp; &nbsp;<br>
<br>

```

---

### Post by FakeOutdoorsman on 2016-08-25
Unfortunately that's not the complete output. I need to see the complete output from the command.

Why are you adding "-flags -global_header"?

---

