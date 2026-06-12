---
title: "psp h264 does't work"
date: 2007-08-14
forum: Multimedia &amp; Video
---

### Post by stpg on 2007-08-14
i want to encode video for psp using h264 codec.
i've build ffmpeg from source (apt-get source ffmpeg...) with h264 support.
Encoding goes without errors but my psp (firmware update 3.40) refuse to play this video (it says "unsupported data")
I was trying to encode with different options but without any success.
When i use direct copy of already h264 encoded video - my psp accept it.

Can someone suggest me how to encode video. Any help will be highly appreciated.

PS. Sorry for my bad english

Additional info:

This is my first attempt of encoding video (PSP refuse to play it)

```
stpg@stpgubuntu:~/tmp$ ffmpeg -i Pan&#8217;s\ Labyrinth.mp4  -acodec aac -ab 32kb -vcodec h264  -b 128kb -ar 48000 -mbd 2 -coder 1 -cmp 2 -subcmp 2 -s 320x240 -r 30000/1001 -title X -f psp -flags loop -trellis 2 -partitions parti4x4+parti8x8+partp4x4+partp8x8+partb8x8 output.mp4
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-liba52 --enable-libdts --enable-dc1394 --enable-libgsm --disable-debug --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-shared --prefix=/usr
  libavutil version: 49.3.0
  libavcodec version: 51.38.0
  libavformat version: 51.10.0
  built on Aug 14 2007 09:51:24, gcc: 4.1.3 20070812 (prerelease) (Ubuntu 4.1.2-15ubuntu2)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Pan&#8217;s Labyrinth.mp4':
  Duration: 00:00:31.4, start: 0.000000, bitrate: 876 kb/s
  Stream #0.0(eng): Audio: aac, 48000 Hz, stereo
  Stream #0.1(eng): Video: h264, yuv420p, 320x240, 29.97 fps(r)
File 'output.mp4' already exists. Overwrite ? [y/N] y
Output #0, psp, to 'output.mp4':
  Stream #0.0: Video: h264 (hq), yuv420p, 320x240, q=2-31, 128 kb/s, 29.97 fps(c)
  Stream #0.1: Audio: aac, 48000 Hz, stereo, 32 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
[h264 @ 0xb7e86188]using cpu capabilities MMX MMXEXT SSE SSE2 
Press [q] to stop encoding
frame=  941 q=-10872864.7 Lsize=    1090kB time=31.3 bitrate= 285.2kbits/s    
video:825kB audio:244kB global headers:0kB muxing overhead 1.894985%
[h264 @ 0xb7e86188]slice I:79    Avg QP:25.42  size:  3438
[h264 @ 0xb7e86188]slice P:862   Avg QP:27.34  size:   665
[h264 @ 0xb7e86188]mb I  I16..4: 61.1%  0.0% 38.9%
[h264 @ 0xb7e86188]mb P  I16..4:  7.4%  0.0%  2.7%  P16..4: 27.1%  5.1%  0.8%  0.1%  0.0%    skip:56.9%
[h264 @ 0xb7e86188]final ratefactor: 29.36
[h264 @ 0xb7e86188]SSIM Mean Y:0.9738843
[h264 @ 0xb7e86188]kb/s:215.3

```

Simplified version - same result.

```

stpg@stpgubuntu:~/tmp$ ffmpeg -i Pan&#8217;s\ Labyrinth.mp4  -acodec aac -ab 32kb -ar 48000 -vcodec h264  -title X -f psp output.mp4
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-liba52 --enable-libdts --enable-dc1394 --enable-libgsm --disable-debug --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-shared --prefix=/usr
  libavutil version: 49.3.0
  libavcodec version: 51.38.0
  libavformat version: 51.10.0
  built on Aug 14 2007 09:51:24, gcc: 4.1.3 20070812 (prerelease) (Ubuntu 4.1.2-15ubuntu2)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Pan&#8217;s Labyrinth.mp4':
  Duration: 00:00:31.4, start: 0.000000, bitrate: 876 kb/s
  Stream #0.0(eng): Audio: aac, 48000 Hz, stereo
  Stream #0.1(eng): Video: h264, yuv420p, 320x240, 29.97 fps(r)
File 'output.mp4' already exists. Overwrite ? [y/N] y
Output #0, psp, to 'output.mp4':
  Stream #0.0: Video: h264, yuv420p, 320x240, q=2-31, 200 kb/s, 29.97 fps(c)
  Stream #0.1: Audio: aac, 48000 Hz, stereo, 32 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
[h264 @ 0xb7ea4188]using cpu capabilities MMX MMXEXT SSE SSE2 
Press [q] to stop encoding
frame=  941 q=-10873968.7 Lsize=    1438kB time=31.3 bitrate= 376.1kbits/s    
video:1173kB audio:244kB global headers:0kB muxing overhead 1.441450%
[h264 @ 0xb7ea4188]slice I:79    Avg QP:23.89  size:  4394
[h264 @ 0xb7ea4188]slice P:862   Avg QP:25.90  size:   991
[h264 @ 0xb7ea4188]mb I  I16..4: 52.7%  0.0% 47.3%
[h264 @ 0xb7ea4188]mb P  I16..4: 10.4%  0.0%  0.0%  P16..4: 36.0%  0.0%  0.0%  0.0%  0.0%    skip:53.5%
[h264 @ 0xb7ea4188]final ratefactor: 27.56
[h264 @ 0xb7ea4188]SSIM Mean Y:0.9744073
[h264 @ 0xb7ea4188]kb/s:306.0

```

But with direct copy of video stream psp accept this file!!!

```

stpg@stpgubuntu:~/tmp$ ffmpeg -i Pan&#8217;s\ Labyrinth.mp4  -acodec aac -ab 32kb -ar 48000 -vcodec copy  -title X -f psp output.mp4
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-liba52 --enable-libdts --enable-dc1394 --enable-libgsm --disable-debug --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-shared --prefix=/usr
  libavutil version: 49.3.0
  libavcodec version: 51.38.0
  libavformat version: 51.10.0
  built on Aug 14 2007 09:51:24, gcc: 4.1.3 20070812 (prerelease) (Ubuntu 4.1.2-15ubuntu2)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Pan&#8217;s Labyrinth.mp4':
  Duration: 00:00:31.4, start: 0.000000, bitrate: 876 kb/s
  Stream #0.0(eng): Audio: aac, 48000 Hz, stereo
  Stream #0.1(eng): Video: h264, yuv420p, 320x240, 29.97 fps(r)
Output #0, psp, to 'output.mp4':
  Stream #0.0: Video: h264, yuv420p, 320x240, q=2-31, 29.97 fps(c)
  Stream #0.1: Audio: aac, 48000 Hz, stereo, 32 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
Press [q] to stop encoding
frame=  941 q=0.0 Lsize=    3123kB time=31.3 bitrate= 817.0kbits/s    
video:2853kB audio:244kB global headers:0kB muxing overhead 0.834057%

```

---

### Post by forgeflow on 2007-09-21
You can also use mEncoder to encode your video for the PSP to h264 format. Here's a recipe:

```
mencoder INPUT -sws 9 -vf scale=480:-10,harddup,unsharp=l3x3:0.7,expand=480:272 -oac faac -faacopts br=128:mpeg=4:object=2:raw -ovc x264 -x264encopts bitrate=650:global_header:partitions=all:trellis=1:vbv_maxrate=768:vbv_bufsize=2000:level_idc=30 -of lavf -lavfopts format=psp -o OUTPUT
```

Of course you'll have to put in all the appropriate parameters for your type of INPUT and for film or video frame rates:

film:
```
-vf pullup,softskip,scale=480:-10,harddup,unsharp=l3x3:0.7,expand=480:272 -ofps 24000/1001
```
video:
```
-vf pp=lb,scale=480:-10,harddup,unsharp=l3x3:0.7,expand=480:272 -fps 30000/1001 -ofps 30000/1001
```

The important parts here are the global_header and level_idc=30 parameters - without these the PSP will refuse to recognize what kind of video stream is in your file. I threw the unsharp mask filter in the filter chain because it makes the resulting video look really nice on the PSP's screen.

[http://videogeek.shacknet.nu]("http://videogeek.shacknet.nu")

---

