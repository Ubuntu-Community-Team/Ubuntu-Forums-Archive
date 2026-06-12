---
title: "Help with MP4Box/MPlayer encoding from avi to MPEG4"
date: 2007-05-27
forum: Multimedia &amp; Video
---

### Post by kromix on 2007-05-27
Ok So I am attempting to get my .avi (Xvid/Divx) Files converted over for use with my XBox360 through Media Extender.........


This is what I used:;;

mplayer -vo null -vc dummy -ao pcm:fast:file=temp.wav ORIGINALAVI.avi ; faac -b 160 temp.wav -o temp.aac ; MP4Box -add ORIGINALAVI.avi#video OUTPUTAVI.mp4 ; MP4Box -add temp.aac OUTPUTAVI.mp4 ; rm temp.aac temp.wav

to convert the file, but it still wasn't picked up by the xbox360, I guess because it was just remuxed and was still xvid right? What can I change/add to that long command list that worked great to re-encode the video into something the XBox 360 Can play?

This is what It CAN play:

----------------------------------------------------------------------------------------------------------------
2.    What exactly does the Xbox 360 support for MPEG-4 Part 2?

Xbox 360 supports the following for MPEG-4:

·         File Extensions: .mp4, .m4v, .mp4v, .mov

·         Containers: MPEG-4, QuickTime

·         Video Profiles: Simple (including Simple profile content mislabeled as Advanced Simple)

·         Video Bitrate: 5 Mbps with resolutions of 1280 x 720 at 30fps. See question number 6 for more information.

·         Audio Profiles: 2 channel AAC low complexity (LC)

·         Audio Max Bitrate: No restrictions. See question number 6 for more information.
----------------------------------------------------------------------------------------------------------------

6.    What is the "real" max bit rate, resolution, and frames per second that you support for all the different formats?

Xbox 360 does not specifically block video from playing based on a maximum bit rate, resolution, or frames per second. The maximums listed above for each codec are what we have tested for various video playback sources. Higher rated content will not be blocked, but playback may be less then optimal. Use higher bitrates at your own risk.


--------------------------------------------------------------------------------------------------------------------

---

### Post by endersshadow on 2007-05-27
I'm, well, I'm going to go out on a limb and suggest something a tad self-promotional. Okay, a lot self-promotional, but I think that it'll help you out greatly.

1. Install the good version of ffmpeg.  If you don't currently have the medibuntu repository enabled, do this:

```
sudo su -c 'echo deb http://packages.medibuntu.org/ feisty free non-free >> /etc/apt/sources.list'
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Once that's done (or if you already had it) run this command:

```
sudo apt-get install ffmpeg
```

2. Use this command to do it:

```
ffmpeg -f mp4 -vcodec mpeg4 -acodec aac -maxrate 5000k -i /path/to/originalavi.avi /path/to/newmov.mov
```

3. If you'd like a GUI to be it (self promotional part, coming up), check out the latest SVN checkout of [Vive](http://vive.sourceforge.net).  It's the GUI frontend to ffmpeg that I write and/or maintain.

Cheers.

---

### Post by 3rods on 2007-05-27
I installed vive and it tells me some garbage about some parameter being wrong no matter what container/codec I choose. 

```
root@xxxxxx:/home/xxxxxx/Desktop/vive# ffmpeg -f mp4 -vcodec mpeg4 -acodec aac -maxrate 5000k -i /home/xxxx/Desktop/xxxxx.ogg /home/xxxxx/Desktop/newmov.mov
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-mp3lame --enable-faadbin --enable-faad --enable-faac --enable-xvid --enable-x264 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Mar 21 2007 14:14:05, gcc: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
[theora @ 0xb7ec3f08]Theora bitstream version 30200
[theora @ 0xb7ec3f08]544 bits left in packet 81
[theora @ 0xb7ec3f08]7 bits left in packet 82
Input #0, ogg, from '/home/xxxxx/Desktop/xxxxx.ogg':
  Duration: 00:05:27.1, start: 0.000000, bitrate: 127 kb/s
  Stream #0.0: Video: theora, yuv420p, 640x480, 29.97 fps(r)
  Stream #0.1: Audio: vorbis, 48000 Hz, stereo, 128 kb/s
Output #0, mov, to '/home/rowan/Desktop/newmov.mov':
  Stream #0.0: Video: mpeg4, yuv420p, 640x480, q=2-31, 200 kb/s, 29.97 fps(c)
  Stream #0.1: Audio: aac, 48000 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[mpeg4 @ 0xb7ec3f08]a vbv buffer size is needed, for encoding with a maximum bitrate
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
```

Is the error between the keyboard and chair?

During playback from within vive I get:

```
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

Playing /home/xxxxx/Desktop/xxxxx.ogg.
[Ogg] stream 0: video (Theora v3.2.0), -vid 0
[Ogg] stream 1: audio (Vorbis), -aid 0
Ogg file format detected.
VIDEO:  [theo]  640x480  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
VDecoder init failed :(
Opening video decoder: [theora] Theora/VP3
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 640x480 => 640x480 Planar YV12
Selected video codec: [theora] vfm: theora (Theora (free, reworked VP3))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis decoder)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
```






Future feature request: Add standardized presets for codecs and the acceptable encoding ranges so it autofills/changes the input boxes when you select a new/different codec. No one should have to devote the max bit rates and resolutions for all the codecs to memory. :(  *just a suggestion*

---

### Post by endersshadow on 2007-05-28
Ah, I see the problem.  I didn't realize this, but you can't set a maxrate w/o setting a buffer size.  So just add the buffer size of 4096 (or, in the command line, -bufsize 4096) and all should be good.

As per the codecs question, I had not even thought about that, but I shall look into it.

Oh, and just noticed, your video is only at 127kb/s (and the audio at 128kb/s), so you don't even have to worry about the maxrate.  Woohoo!

---

### Post by Cuppa-Chino on 2007-05-28
Vive will not compile on my Feisty it claims GTK version not right:

```
vive-2.0.0-beta1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for ffmpeg... yes
checking for vobcopy... yes
checking for mplayer... yes
checking for prefix by checking for ffmpeg... /usr/bin/ffmpeg
checking whether DVD is enabled... yes
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 2.0.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error: GTK is not version >= 2.0.0.  Please update GTK.
johnny@johnny-desktop:~/Desktop/vive-2.0.0-beta1$ make
make: *** No targets specified and no makefile found. Stop.

```

what next ? as said I am using Feisty Fawn - AMD64

---

### Post by endersshadow on 2007-05-29
Chuppa: Run this:

```
sudo apt-get install libgtk2.0-dev libvte-dev libdvdnav-dev libdvdread-dev libdvdcss2-dev
```

That should get you all you need to compile.  Cheers.

---

