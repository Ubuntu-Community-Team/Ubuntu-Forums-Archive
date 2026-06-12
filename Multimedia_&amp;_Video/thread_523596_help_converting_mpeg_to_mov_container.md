---
title: "help converting mpeg to mov container"
date: 2007-08-12
forum: Multimedia &amp; Video
---

### Post by johnwren on 2007-08-12
I am working on an instructional webpage and want to show some videos.  We have chosen quicktime containers (either .mp4 or .mov) to support as many systems as possible.  One objective of the project is to use only open-source software.

The videos were captured using Kino and exported as mpeg (DVD) files.  I'm learning to use ffmpeg to encode them to .mov containers.  My system is feisty AMD64 and has working copies of ffmpeg (from medibuntu) mencoder and mplayer.  The following works fine:

ffmpeg -i test.mpg -sameq test4.mov

But I am having trouble doing two pass encoding.  I think I just don't understand the syntax for two-pass work.  I tried the following:
	ffmpeg -i test.mpg -sameq -pass 1 temp.mov
	ffmpeg -i test.mpg -sameq -pass 2 test.mov

The ffmpeg2pass-0.log is created on the first pass, but the second pass dies with
johnwren@johnwren-AMD64:~/test$ ffmpeg -i test.mpg -sameq -pass 2 test.mov

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard

  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-mp3lame --enable-faadbin --enable-faad --enable-faac --enable-xvid --enable-x264 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr 

  libavutil version: 0d.49.0.0

  libavcodec version: 0d.51.11.0

  libavformat version: 0d.50.5.0

  built on Mar 25 2007 22:39:13, gcc: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)

Input #0, mpeg, from 'test.mpg':

  Duration: 00:01:21.6, start: 0.184656, bitrate: 2656 kb/s

  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x576, 7500 kb/s, 25.00 fps(r)

  Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, 192 kb/s

Output #0, mov, to 'test.mov':

  Stream #0.0: Video: mpeg4, yuv420p, 720x576, q=2-31, pass 2, 200 kb/s, 25.00 fps(c)

  Stream #0.1: Audio: aac, 48000 Hz, stereo, 64 kb/s

Stream mapping:

  Stream #0.0 -> #0.0

  Stream #0.1 -> #0.1

[mpeg4 @ 0x2b29c483c6d0]removing common factors from framerate

[mpeg4 @ 0x2b29c483c6d0]requested bitrate is to low

Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height


Can anyone help me here?  What am I doing wrong?  Also, if I want to resize the video, something like “-s cif”, how does that interact with the -sameq and pass parameters.  I am pretty much a newbie in these things.

Any help much appreciated.
Thanks

If it is relevant, here is what mplayer shows for the test.mpg file.

johnwren@johnwren-AMD64:~/test$ mplayer test.mpg

MPlayer 1.0rc1-4.1.2 (C) 2000-2006 MPlayer Team

CPU: AMD Athlon(tm) 64 Processor 3000+ (Family: 15, Model: 47, Stepping: 2)

CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1

Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2



Playing test.mpg.

MPEG-PS file format detected.

VIDEO:  MPEG2  720x576  (aspect 2)  25.000 fps  7500.0 kbps (937.5 kbyte/s)

==========================================================================

Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough

VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)

Could not find matching colorspace - retrying with -vf scale...

Opening video filter: [scale]

The selected video_out device is incompatible with this codec.

Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.

VDecoder init failed :(

Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b

Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))

==========================================================================

==========================================================================

Opening audio decoder: [mp3lib] MPEG layer-2, layer-3

AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)

Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)

==========================================================================

AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)

Starting playback...

VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)

VDec: using Planar YV12 as output csp (no 0)

Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.

VO: [xv] 720x576 => 768x576 Planar YV12 

New_Face failed. Maybe the font path is wrong. 2 ??% ??% ??,?% 0 0              

Please supply the text font file (~/.mplayer/subfont.ttf).

subtitle font: load_sub_face failed.

A:  82.1 V:  82.1 A-V:  0.002 ct:  0.050 2051/2051  7%  1%  1.0% 0 0

---

### Post by johnwren on 2007-08-12
I found some help at: [http://www.videohelp.com/forum/archive/need-help-with-ffmpeg-2-pass-vbr-encoding-t251008.html](http://www.videohelp.com/forum/archive/need-help-with-ffmpeg-2-pass-vbr-encoding-t251008.html)
although it is windows based.  What I notice is that he explicitly set many options, rather than using the simple -sameq parameter.  Is this necessary for multi-pass use?  

Any help much appreciated.

Pasted from the previous (window's based) reference:

ffmpeg -i %~n1.mpg -pass 1 -passlogfile %~n1 -b 3000 -minrate 0 -maxrate 8000 -bufsize 224 -vcodec mpeg2video -s 720x480 -r 29.97 -aspect 4:3 -hq -an foo.mpg
del foo.mpg
ffmpeg -i %~n1.mpg -pass 2 -passlogfile %~n1 -b 3000 -minrate 0 -maxrate 8000 -bufsize 224 -vcodec mpeg2video -s 720x480 -r 29.97 -aspect 4:3 -hq -an %~n1(720x480).mpg

---

### Post by Creative2 on 2007-10-09
install mencoder but with mendibuntu repo activated 

then 

```
mencoder -oac faac -faacopts br=192:mpeg=4:object=2 -channels 2 -srate 22050 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=300 -of lavf -lavfopts i_certify_that_my_video_stream_does_not_use_b_frames -o output.mov INPU
```T

---

