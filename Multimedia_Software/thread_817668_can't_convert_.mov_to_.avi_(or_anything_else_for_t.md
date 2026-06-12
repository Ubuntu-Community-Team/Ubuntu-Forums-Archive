---
title: "can't convert .mov to .avi (or anything else for that matter)"
date: 2008-06-03
forum: Multimedia Software
---

### Post by dev.null on 2008-06-03
I've got a .mov I want to eventually convert into a .flv to play on the web. I'm thinking first I take it to something like .avi then ffmpeg can convert it to flv. Here's what `file` says it is:

> rpickett@romeo1:~/video$ file intro.mov 
intro.mov: ISO Media, Apple QuickTime movie


here's the attempt with ffmpeg:

> rpickett@romeo1:~/video$ ffmpeg -i intro.mov intro.avi 
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Dec 20 2007 21:25:50, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Richard Pickett 06-02-08 intro.mov':
  Duration: 00:00:44.9, start: 0.000000, bitrate: 89691 kb/s
  Stream #0.0(eng): Audio: pcm_s16be, 48000 Hz, stereo, 1536 kb/s
  Stream #0.1(eng): Video: Apple Intermediate Codec, 1440x1080, 29.97 fps(r)
File 'Richard Pickett 06-02-08 intro.avi' already exists. Overwrite ? [y/N] y
Output #0, avi, to 'Richard Pickett 06-02-08 intro.avi':
  Stream #0.0: Video: mpeg4, yuv420p, 1440x1080, q=2-31, 200 kb/s, 29.97 fps(c)
  Stream #0.1: Audio: mp2, 48000 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
**Unsupported codec (id=0) for input stream #0.1**


mencoder:

> $ mencoder -ovc copy -oac pcm -o "intro.avi" "intro.mov"
MEncoder 2:1.0~rc2-0ubuntu1~gutsy1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) M processor 1.60GHz (Family: 6, Model: 13, Stepping: 8)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x1e08d590
ISO: File Type Major Brand: Original QuickTime
Quicktime/MOV file format detected.
[mov] Audio stream found, -aid 0
[mov] Video stream found, -vid 1
VIDEO:  [icod]  1440x1080  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:7  fourcc:0x646F6369  size:1440x1080  fps:29.97  ftime:=0.0334
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 48000 Hz, 2 ch, s16be, 1536.0 kbit/100.00% (ratio: 192000->192000)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
videocodec: framecopy (1440x1080 24bpp fourcc=646f6369)
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing index...47f ( 0%) 16.71fps Trem:   0min   0mb  A-V:0.033 [88153:1535]
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream: 88153.025 kbit/s  (11019128 B/s)  size: 495254108 bytes  44.945 secs  1347 frames

Audio stream: 1536.000 kbit/s  (191999 B/s)  size: 8629120 bytes  44.943 secs


but when I play the avi with xine (among others), it says "Video codec: unavailable (icod)" if I play anyway there is no video. Here's what `file` says about the avi:

> rpickett@romeo1:~/video$ file intro.avi 
intro.avi: RIFF (little-endian) data, AVI, 1440 x 1080, ~30 fps, video:, audio: uncompressed PCM (stereo, 48000 Hz)


I know this is a missing codec issue, but in all my searching I can't find any codec that allows ffmpeg or any other tool to convert this .mov file into another format.

Any suggestions?

Any help is greatly appreciated.

---

### Post by wolfen69 on 2008-06-03
it was suggested on winff's website that you should add the medibuntu repos before installing any codec packages. i guess they are more complete than the standard ubuntu repos.

---

### Post by Prospero2006 on 2008-06-04
I use ffmpeg and mencoder a lot myself. Generally, I get the command right, save it to a script, and then forget about it. Thus, I'm not too sharp on remembering exactly what arguments are required.

However, 
[http://zamzar.com](http://zamzar.com)

Try that site.

---

### Post by dev.null on 2008-06-04
> **wolfen69 said:**
> it was suggested on winff's website that you should add the medibuntu repos before installing any codec packages. i guess they are more complete than the standard ubuntu repos.

I did that one already, it didn't make a difference. Thanks anyway.

---

