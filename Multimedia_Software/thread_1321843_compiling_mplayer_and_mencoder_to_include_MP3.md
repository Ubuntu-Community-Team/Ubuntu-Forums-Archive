---
title: "compiling mplayer and mencoder to include MP3"
date: 2009-11-10
forum: Multimedia Software
---

### Post by sdowney717 on 2009-11-10
use this guide but modify a few key parts to include mencoder, (take off the mention about mencoder)
working on karmic

[http://ubuntuforums.org/showthread.php?t=1305181](http://ubuntuforums.org/showthread.php?t=1305181)

add in libmp3lame-dev from synaptic
I ran the configure script and looked for the no's, adding in several more dev file using synaptic. (Trying to get it all there for the compile)


> $ cd $HOME/mplayer
$ ./configure --cc=gcc-4.3 --confdir=/etc/mplayer 
$ make
$ sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/Desktop" \
   --pkgname mplayer-nogui --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default \
   --pkgversion "3:1.0~svn-`grep "#define VERSION" version.h | cut -d"-" -f2`"
$ make distclean


(on the checkinstall line, leave out the "\" slashes)

and it works and the file plays in my dsm 320 media player

(make sure vqmax=31 line makes sense etc... or you will get lavcopt errors, the ubuntu forums seems to mess up that line)

> scott@scott-desktop:~/Videos$ mencoder test.mpg -o output.divx -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1100:mbd=2:vpass=2:vqmin=2:vqmax=31:keyint=30 -ffourcc DIVX -oac mp3lame 
MEncoder SVN-r29882-4.3.4 (C) 2000-2009 MPlayer Team

WARNING: OUTPUT FILE FORMAT IS _AVI_. See -of help.
success: format: 0  data: 0x0 - 0xa0c71f
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  8000.0 kbps (1000.0 kbyte/s)
[V] filefmt:2  fourcc:0x10000002  size:720x480  fps:29.970  ftime:=0.0334
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 224.0 kbit/14.58% (ratio: 28000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 0
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Unsupported PixelFormat -1
Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
==========================================================================
Forcing output FourCC to 58564944 [DIVX].
MP3 audio selected.
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
videocodec: libavcodec (720x480 fourcc=58564944 [DIVX])
[VE_LAVC] High quality encoding selected (non-realtime)!
Writing header...1f ( 4%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   0.7s     22f ( 7%)  0.00fps Trem:   0min   2mb  A-V:0.068 [0:182]
Skipping frame!
Pos:  14.3s    431f (100%) 148.21fps Trem:   0min   2mb  A-V:0.055 [1106:182]
Flushing video frames.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream: 1106.079 kbit/s  (138259 B/s)  size: 1979093 bytes  14.314 secs  431 frames

Audio stream:  182.865 kbit/s  (22858 B/s)  size: 328608 bytes  14.376 secs
scott@scott-desktop:~/Videos$ 

---

### Post by andrew.46 on 2009-11-10
Hi sdowney717,

I can perhaps suggest a few small things. The first is to look at the *./configure *process which will tell you if checks for dependencies are satisfied or not. The line you are looking for should read:

```
Checking for libmp3lame ... yes (in libavcodec: yes)
```

If something is flagged as *fail* you can then look at configure.log which should record why MPlayer failed to find the relevant headers. The mp3 section should start as follows:

```

============ Checking for libmp3lame ============

```

All the best,

Andrew

---

### Post by sdowney717 on 2009-11-13
what i would like to figure out is how to encode the audio always as 

mpeg1 layer three(mp3) and not mpeg2 layer 3(mp3)

this line works, but the audio needs to always be mpeg1 layer3(mp3) and sometimes on transcoding it comes out mpeg2(layer3)

 mencoder evening_broadcast1109_720.mp4 -o 122aoutputmpeg.divx -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1100:mbd=2:vpass=1:vqmin=2:vqmax=31:keyint=30 -ffourcc DIVX -oac mp3lame 

the picture shows what i mean.

---

