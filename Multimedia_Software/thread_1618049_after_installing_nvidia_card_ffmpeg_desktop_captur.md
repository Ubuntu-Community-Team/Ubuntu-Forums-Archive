---
title: "after installing nvidia card ffmpeg desktop capture fails to work"
date: 2010-11-10
forum: Multimedia Software
---

### Post by shantiq on 2010-11-10
[COLOR=#000000][FONT=Times New Roman][FONT=Verdana] i installed an nvidia graphics card recently and this



[/FONT][/FONT][/COLOR]```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 ./Desktop/mydesktop.mkv
```[COLOR=#000000][FONT=Times New Roman][FONT=Verdana]

does not work anymore any idea why; the image is tearing up ;    i have no idea why 




any thoughts/fixes?

ps screenshot of what i get
[/FONT][/FONT][/COLOR]

---

### Post by shantiq on 2010-11-10
and i know it is not compiz     because    doing


```
metacity --replace
``` changes nothing

---

### Post by shantiq on 2010-11-10
=

---

### Post by shantiq on 2010-11-10
now it seems it had a problem with the lossless setting    any idea why?

this works ok 



```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1280x1024 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre ultrafast -b 2500k -y ./Desktop/mydesktop.mkv
```


if anyone knows why please say    



 thankx

---

### Post by shantiq on 2010-11-11
this is the result i get when i have this tearing video on lossless setting        any clues?

```
shantiq@shantiq-desktop:~$ ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1280x1024  -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast  -y ./Desktop/mydesktop.mkv
FFmpeg version SVN-r25305, Copyright (c) 2000-2010 the FFmpeg developers
  built on Oct  2 2010 08:39:26 with gcc 4.4.5
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50.32. 0 / 50.32. 0
  libavcore      0. 9. 0 /  0. 9. 0
  libavcodec    52.92. 0 / 52.92. 0
  libavformat   52.79. 0 / 52.79. 0
  libavdevice   52. 2. 2 / 52. 2. 2
  libavfilter    1.48. 0 /  1.48. 0
  libswscale     0.12. 0 /  0.12. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[alsa @ 0x9a0d470] capture with some ALSA plugins, especially dsnoop, may hang.
[alsa @ 0x9a0d470] Estimating duration from bitrate, this may be inaccurate
Input #0, alsa, from 'pulse':
  Duration: N/A, start: 1289494996.993972, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 44100 Hz, 2 channels, s16, 1411 kb/s
[x11grab @ 0x9a1f750] device: :0.0 -> display: :0.0 x: 0 y: 0 width: 1280 height: 1024
[x11grab @ 0x9a1f750] shared memory extension  found
[x11grab @ 0x9a1f750] Estimating duration from bitrate, this may be inaccurate
Input #1, x11grab, from ':0.0':
  Duration: N/A, start: 1289494997.114044, bitrate: 1258291 kb/s
    Stream #1.0: Video: rawvideo, bgra, 1280x1024, 1258291 kb/s, 30 tbr, 1000k tbn, 30 tbc
[buffer @ 0x9a2e140] w:1280 h:1024 pixfmt:bgra
[ffmpeg_output @ 0x9a45140] auto-inserting filter 'auto-inserted scaler 0' between the filter 'src' and the filter 'out'
[scale @ 0x9a454f0] w:1280 h:1024 fmt:bgra -> w:1280 h:1024 fmt:yuv420p flags:0xa0000004
[libx264 @ 0x9a2d010] using cpu capabilities: MMX2 SSE2Slow SlowCTZ
[libx264 @ 0x9a2d010] profile High 4:4:4 Predictive, level 3.2, bit depth 8
[libx264 @ 0x9a2d010] 64 - core 106 r1732 b20059a - H.264/MPEG-4 AVC codec - Copyleft 2003-2010 - http://www.videolan.org/x264.html - options: cabac=0 ref=1 deblock=1:0:0 analyse=0x1:0 me=dia subme=0 psy=0 mixed_ref=0 me_range=16 chroma_me=1 trellis=0 8x8dct=0 cqm=0 deadzone=21,11 fast_pskip=0 chroma_qp_offset=0 threads=1 sliced_threads=0 nr=0 decimate=1 interlaced=0 constrained_intra=0 bframes=0 weightp=0 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc=cqp mbtree=0 qp=0
Output #0, matroska, to './Desktop/mydesktop.mkv':
  Metadata:
    encoder         : Lavf52.79.0
    Stream #0.0: Video: libx264, yuv420p, 1280x1024, q=10-51, 200 kb/s, 1k tbn, 30 tbc
    Stream #0.1: Audio: pcm_s16le, 44100 Hz, 2 channels, s16, 1411 kb/s
Stream mapping:
  Stream #1.0 -> #0.0
  Stream #0.0 -> #0.1
Press [q] to stop encoding
frame=   41 fps=  5 q=-1.0 Lsize=    2241kB time=7.47 bitrate=2456.8kbits/s    
video:944kB audio:1287kB global headers:0kB muxing overhead 0.432265%
frame I:1     Avg QP: 0.00  size:333113
[libx264 @ 0x9a2d010] frame P:40    Avg QP: 0.00  size: 15824
[libx264 @ 0x9a2d010] mb I  I16..4: 63.6%  0.0% 36.4%
[libx264 @ 0x9a2d010] mb P  I16..4: 43.6%  0.0%  0.0%  P16..4:  1.0%  0.0%  0.0%  0.0%  0.0%    skip:55.5%
[libx264 @ 0x9a2d010] coded y,uvDC,uvAC intra: 4.0% 6.1% 6.0% inter: 0.8% 1.7% 1.7%
[libx264 @ 0x9a2d010] i16 v,h,dc,p: 98%  2%  0%  0%
[libx264 @ 0x9a2d010] i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 40% 38%  7%  3%  3%  2%  2%  2%  3%
[libx264 @ 0x9a2d010] i8c dc,h,v,p: 86%  5%  9%  0%
[libx264 @ 0x9a2d010] kb/s:986.62
```

---

