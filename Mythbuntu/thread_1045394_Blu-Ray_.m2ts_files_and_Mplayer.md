---
title: "Blu-Ray .m2ts files and Mplayer"
date: 2009-01-20
forum: Mythbuntu
---

### Post by gneville on 2009-01-20
Hello All Again,

Wondering if someone can help me out here.

I have a read a couple of forum posts on how to play a Ripped Blu-ray disk. I have the files unencrypted as a .m2ts format. The largest being about 30GB.

I have been told that Mplayer supports .m2ts straight out the box, however when I use Mplayer I can only hear Audio and no see no Video?

This is what occurs when running without any options:

Command Used : mplayer 00004.m2ts


MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+ (Family: 15, Model: 67, Stepping: 3)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

Playing 00004.m2ts.
TS file format detected.
VIDEO VC1(pid=4113) AUDIO A52(pid=4356) NO SUBS (yet)!  PROGRAM N. 1
Searching for VC1 sequence header... found
VIDEO:  VC-1  1920x1080, 23.976 fps, header len: 33
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
GetOutput r=0x0   size:6220800  align:1
StreamCount r=0x0  1  1
Decoder supports the following formats: YV12 YUY2 UYVY YVYU RGB8 RGB555 RGB565 RGB24 RGB32
Decoder is capable of YUV output (flags 0x1b)
VDec: vo config request - 1920 x 1080 (preferred colorspace: Packed YUY2)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 1920x1080 => 1920x1080 Planar YV12
[ASPECT] Warning: No suitable new res found!
[ASPECT] Warning: No suitable new res found!
[ASPECT] Warning: No suitable new res found!
Selected video codec: [wmvvc1dmo] vfm: dmo (Windows Media Video (VC-1) Advanced Profile Decoder)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [pulse] Failed to connect to server: Connection refused
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
ProcessInputError  r:0xffffff9c=-100 (keyframe: 1)
ProcessInputError  r:0x80004005=-2147467259 (keyframe: 1)0.6% 0 0
ProcessInputError  r:0x80004005=-2147467259 (keyframe: 1)0.7% 0 0
ProcessInputError  r:0x80004005=-2147467259 (keyframe: 1)0.6% 0 0

And these errors continue.


If I use this command which someone recommend I get again Audio but no Video, 


Command: mplayer -fs -zoom -quiet -vo xv -fps 24000/1001 -lavdopts threads=2:fast:skiploopfilter=all -sws 0 -framedrop 00004.m2ts

MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+ (Family: 15, Model: 67, Stepping: 3)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

Playing 00004.m2ts.
TS file format detected.
VIDEO VC1(pid=4113) AUDIO A52(pid=4356) NO SUBS (yet)!  PROGRAM N. 1
Searching for VC1 sequence header... found
VIDEO:  VC-1  1920x1080, 23.976 fps, header len: 33
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
GetOutput r=0x0   size:6220800  align:1
StreamCount r=0x0  1  1
Decoder supports the following formats: YV12 YUY2 UYVY YVYU RGB8 RGB555 RGB565 RGB24 RGB32
Decoder is capable of YUV output (flags 0x1b)
VDec: vo config request - 1920 x 1080 (preferred colorspace: Packed YUY2)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 1920x1080 => 1920x1080 Planar YV12  [fs] [zoom]
[ASPECT] Warning: No suitable new res found!
[ASPECT] Warning: No suitable new res found!
[ASPECT] Warning: No suitable new res found!
[ASPECT] Warning: No suitable new res found!
Selected video codec: [wmvvc1dmo] vfm: dmo (Windows Media Video (VC-1) Advanced Profile Decoder)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [pulse] Failed to connect to server: Connection refused
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
FPS forced to be 23.976  (ftime: 0.042).
Starting playback...
ProcessInputError  r:0xffffff9c=-100 (keyframe: 1)
[ASPECT] Warning: No suitable new res found!
ProcessInputError  r:0x80004005=-2147467259 (keyframe: 0)
ProcessInputError  r:0x80004005=-2147467259 (keyframe: 0)
ProcessInputError  r:0x80004005=-2147467259 (keyframe: 1)
ProcessInputError  r:0x80004005=-2147467259 (keyframe: 1)
ProcessInputError  r:0x80004005=-2147467259 (keyframe: 1)
ProcessInputError  r:0x80004005=-2147467259 (keyframe: 1)

This is the output I get.


Can anyone tell me where I am going wrong here?

I have tried VLC and Xine, but from my understanding only Mplayer supports .m2ts files?

Oh and I understand its also dependant on ffmpeg. Here's my ffmpeg version:

 ffmpeg -version
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
ffmpeg      SVN-rUNKNOWN
libavutil   3212032
libavcodec  3352064
libavformat 3344896


Thanks

Graham

---

### Post by gneville on 2009-01-20
Hmmm.

I just had a thought, could it be that My Graphics Card isnt HDCP and thats why?

---

### Post by gneville on 2009-01-20
Well I have changed my Graphics Card from an 7800GTX which I think is non-HDCP to a 8500GT which has an HDMI port directly on it and is HDCP but same outcome.

---

### Post by utar on 2009-01-21
It's nothing to do with HDCP as the files are unencrypted.  Playback of bluray and HD-DVD content is shaky at best even on the latest mplayer build.  I have some HD-DVD rips that I could play video and sound on but not in sync, and I guess blu-ray wil be much the same.

Try adding "-vc ffvc1" to your mplayer command line.

---

### Post by gneville on 2009-01-21
Well I upgraded ffmpeg today, built from the latest svn.

I tried the command I used first time around and no change.

utar - I tried adding "-vc ffvc1" and now I get both video and audio, it starts ok but after a few seconds theres playback problems.

I'm seeing these errors:

Command used: mplayer -fs -zoom -quiet -vo xv -vc ffvc1 -fps 24000/1001 -lavdopts threads=2:fast:skiploopfilter=all -sws 0 -framedrop 00004.m2ts

Too many video packets in the buffer: (51 in 8489663 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Maybe an AMD Athlon(tm) 64 X2 Dual Core Processor 6000+ with 4gb of RAM is not good enough?

I also see this:

           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.


So i'll try those suggestions...

---

### Post by gneville on 2009-01-21
Right,

I swapped my 8500GT with a 7800GTX and tried a few things best result is this:

an extra "-ni" and "-cache 9999" it plays quite well but does slow down from time to time especially on more action packed scenes.

mplayer -fs -zoom -quiet -vo xv -vc ffvc1 -fps 24000/1001 -lavdopts threads=2:fast:skiploopfilter=all -sws 0 -framedrop -ni -cache 9999 00004.m2ts

Is there any other things I could try? Also I am trying to run this at 1920x1080.

---

### Post by gneville on 2009-01-21
It works fine at 720p res....guess thats better than nothing at all:

mplayer -fs -zoom -x 1280 -y 720 -quiet -vo xv -vc ffvc1 -fps 24000/1001 -lavdopts threads=2:fast:skiploopfilter=all -sws 0 -framedrop -ni -cache 9999 00004.m2ts

---

### Post by utar on 2009-01-22
Decoding HD video is very processor intensive, and I don't think mplayer is very good at using multiple threads so it is not suprising that it won't playback well at 1080p.

There are beta drivers from Nvidia that support accerated video decoding so once these are released and mplayer is patched to provide support playback should be better.

---

### Post by HyRax on 2009-02-15
The Medibuntu version of MPlayer and the associated non-free-codecs package play m2ts files quite happily, but as you've pointed out, this is very CPU intensive and there's a truckload of data to deal with (normally your video card would do all this, not the CPU).

I've played with the VDPAU-enabled version of MPlayer, and while it definitely works (CPU usage is next to nothing because the NVidia video card is doing the work it is designed to do), playback is still not 100% smooth. I've noticed VLC does a much better job overall than MPlayer or Totem at providing smooth playback without any jitter. Jaunty will open the doors to easy VDPAU enablement. It's a bit of a logistic process to get it working under Intrepid because you also have to manually update the NVidia drivers from 177 to 180. Jaunty already includes 180, so that's half the work out of the way right away.

Personally I re-encode my BD rips to a Matroska container with the video running at 4mbps minimum and the audio in its original format. Makes for a 4GB average file which all players can handle far more easily than an m2ts file, and the image quality looks 98% accurate to the original data. Takes 12 hours to encode on a quad-core machine using [Handbrake](apt:handbrake), though... :(

---

### Post by Avuton Olrich on 2009-02-15
Someone gave me a script to convert mkv to m2ts so I can play them easily on my ps3, this can be done in less then a few minutes on a dual core. You need closed source software to make it happen, but it's a small price to pay not to have to trascode to change containers:

See:
[http://www.smlabs.net/tsmuxer_en.html](http://www.smlabs.net/tsmuxer_en.html)

I would like to give the script out, but it's not mine. If I ever get the opportunity I will release it.

Edit: Well, looking again, I see that you wern't talking about that at all, but something totally different. *sigh*

---

### Post by HyRax on 2009-02-20
For NVidia GeForce 8xxx or higher users, if you can't wait for Ubuntu Jaunty for proper VDPAU support to playback all manner of video streams properly using your card's on-board decoder, try out the [VDPAU backports for Ubuntu Intrepid](http://www.avenard.org/media/Home.html) and earlier. This site provides a repository with specially modified versions of MPlayer, MEncoder and MythTV libraries that are VDPAU-enabled, thus enabling you to successfully offload decoding work to your video card instead of doing it all on the CPU. The end result is that the CPU can concentrate on other tasks and it means MPLayer, Totem, VLC and the like can playback your high-definition content (including those pesky .m2ts files) far more effectively than before with less tearing and smoother playback (note that whilst CPU usage is lower, this does not necessarily translate to jitter-free playback - there are other things to consider such as vertical sync and so forth).

Anyway, give it a go (but at your own risk, being a Backport and all) - CPU usage at 3% when playing back an unecrypted Blu-ray movie? Mmmmm!!! :p

The only annoying thing is that the author of the Backport (at the time of this writing) forgot to compile in x264 support into MEncoder, so you might want to hold off upgrading that program.

---

