---
title: "Mencoder started encoding very slowly with xvid?"
date: 2009-09-27
forum: Multimedia Software
---

### Post by Jose Catre-Vandis on 2009-09-27
I run a 2 pass script to encode recorded TV using the xvid codec with mencoder. I demux the video and audio using projectx and then remux after the video encode to keep the A/V sync. When I first started doing this I was getting 25fps+ encoding on each pass. This has now suddenly dropped to @ 4fps so it is taking @ 6 hours to encode 1 hour of video. Can anyone shed any light on what might have happened? AFAIK there have been no significant changes to my system.

Encode script:
```
#FIRST PASS ON VIDEO FILE TO CREATE LOG FILE
mencoder "input.m2v" -idx -vf pp=lb -ovc xvid -xvidencopts vhq=1:chroma_opt:quant_type=mpeg:aspect=16/9:bitrate=600:pass=1 -o /dev/null 

#SECOND PASS ON VIDEO FILE ACTUAL ENCODE
mencoder "input.m2v" -idx -vf pp=lb -ovc xvid -xvidencopts vhq=1:chroma_opt:quant_type=mpeg:aspect=16/9:bitrate=600:pass=2 -o "output.avi"


#ENCODE AUDIO TO MP3 128
ffmpeg -i input.mp2 -acodec libmp3lame -ac 2 -ab 96k -ar 44100 output.avi

#MUX VIDEO AND AUDIO
mencoder "output.avi" -ovc copy -oac copy -audiofile "output.mp3" -o "final.avi"
```

As I say this has run at almost real time previously so am guessing its a system problem as opposed to anything in the parameters of the script.

This is on an up to date 9.04 command line system, using MEncoder 2:1.0~rc2-0ubuntu19 from the repos, so first off I might try SVN? EDIT Tried this on another PC with SVN Mplayer with the same result. Has the raw video content changed in any way coming down from BBC?

More info, the command line outputs from a test encode using SVN MPlayer

1st pass
```
Encoding test.m2v
MEncoder SVN-r29328-4.3.3 (C) 2000-2009 MPlayer Team
success: format: 0  data: 0x0 - 0x2b92ee4
MPEG-ES file format detected.
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  6318.8 kbps (789.9 kbyte/s)
[V] filefmt:1  fourcc:0x10000002  size:720x576  fps:25.000  ftime:=0.0400
xvid: using library version 1.2.1 (build xvid-1.2.1)
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [pp=lb]
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
[PP] Using external postprocessing filter, max q = 6.
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
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
[PP] Using external postprocessing filter, max q = 6.
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
videocodec: XviD (720x576 fourcc=44495658 [XVID])
xvid: par=64/45 (ext), displayed=1024x576, sampled=720x576
xvid: bitrate setting is ignored during first pass
xvid: 2Pass Rate Control -- 1st pass
Writing header...1f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
ODML: vprp aspect is 16:9.
Writing header...
ODML: vprp aspect is 16:9.
Pos:  93.2s   2332f (99%)  5.83fps Trem:   0min  62mb  A-V:0.000 [5639:0]
Flushing video frames.
Writing index...
Writing header...
ODML: vprp aspect is 16:9.

Video stream: 5640.229 kbit/s  (705028 B/s)  size: 65736874 bytes  93.240 secs  2332 frames 
```
[ATTACH]129935[/ATTACH]

2nd pass
```
MEncoder SVN-r29328-4.3.3 (C) 2000-2009 MPlayer Team
success: format: 0  data: 0x0 - 0x2b92ee4
MPEG-ES file format detected.
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  6318.8 kbps (789.9 kbyte/s)
[V] filefmt:1  fourcc:0x10000002  size:720x576  fps:25.000  ftime:=0.0400
xvid: using library version 1.2.1 (build xvid-1.2.1)
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [pp=lb]
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
[PP] Using external postprocessing filter, max q = 6.
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
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
[PP] Using external postprocessing filter, max q = 6.
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
videocodec: XviD (720x576 fourcc=44495658 [XVID])
xvid: par=64/45 (ext), displayed=1024x576, sampled=720x576
xvid: 2Pass Rate Control -- 2nd pass -- bitrate=600kbit/s
Writing header...1f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
ODML: vprp aspect is 16:9.
Writing header...
ODML: vprp aspect is 16:9.
Pos:  93.2s   2332f (99%)  3.16fps Trem:   0min   6mb  A-V:0.000 [598:0]]
Flushing video frames.
Writing index...
Writing header...
ODML: vprp aspect is 16:9.

Video stream:  598.788 kbit/s  (74848 B/s)  size: 6978870 bytes  93.240 secs  2332 frames 
```
[ATTACH]129936[/ATTACH]

Audio Encode and Mux (this part is nice and quick)
```
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:18:41, gcc: 4.3.3
Input #0, mp3, from 'test.mp2':
  Duration: 00:01:33.26, start: 0.000000, bitrate: 256 kb/s
    Stream #0.0: Audio: mp2, 48000 Hz, stereo, s16, 256 kb/s
Output #0, mp3, to 'test.mp3':
    Stream #0.0: Audio: libmp3lame, 44100 Hz, stereo, s16, 96 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=    1094kB time=93.31 bitrate=  96.0kbits/s    
video:0kB audio:1093kB global headers:0kB muxing overhead 0.002858%
MEncoder SVN-r29328-4.3.3 (C) 2000-2009 MPlayer Team
success: format: 0  data: 0x0 - 0x6b6c3a
AVI file format detected.
[aviheader] Video stream found, -vid 0
VIDEO:  [XVID]  720x576  12bpp  25.000 fps  598.8 kbps (73.1 kbyte/s)
Audio only file format detected.
[V] filefmt:65536  fourcc:0x44495658  size:720x576  fps:25.000  ftime:=0.0400
videocodec: framecopy (720x576 12bpp fourcc=44495658)
audiocodec: framecopy (format=55 chans=2 rate=44100 bits=16 B/s=12000 sample-0)
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing index...31f (100%)  0.00fps Trem:   0min   7mb  A-V:0.040 [598:96]
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream:  598.788 kbit/s  (74848 B/s)  size: 6978870 bytes  93.240 secs  2331 frames

Audio stream:   96.000 kbit/s  (12000 B/s)  size: 1119713 bytes  93.309 secs  
```

Also, should I be worried about the errors issued in this section, they have always been there in some form or other ever since I have began using mplayer/mencoder

```
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Unsupported PixelFormat -1 
```

EDIT: Doing some more testing and it has got worse, down to 1 (one) fps !!

---

### Post by Major_Kong on 2009-09-27
Try using the rc3, you can get it from this ppa - [http://ppa.launchpad.net/rvm/mplayer/ubuntu](http://ppa.launchpad.net/rvm/mplayer/ubuntu) .

PS: Use instead avibox to mux the audio and video track.

---

### Post by Jose Catre-Vandis on 2009-09-27
Thanks, I'll give it a whirl:
Direct links:
[http://ppa.launchpad.net/rvm/mplayer/ubuntu/pool/main/m/mplayer/mencoder_1.0~rc3+svn20090904-0jaunty2_i386.deb](http://ppa.launchpad.net/rvm/mplayer/ubuntu/pool/main/m/mplayer/mencoder_1.0~rc3+svn20090904-0jaunty2_i386.deb)
[http://ppa.launchpad.net/rvm/mplayer/ubuntu/pool/main/m/mplayer/mplayer_1.0~rc3+svn20090904-0jaunty2_i386.deb](http://ppa.launchpad.net/rvm/mplayer/ubuntu/pool/main/m/mplayer/mplayer_1.0~rc3+svn20090904-0jaunty2_i386.deb)

Not having any problems with the remux (speed or otherwise), what are the benefits of avibox over what I am doing?

---

### Post by Jose Catre-Vandis on 2009-09-28
Tried rc3 - didn't make any difference. Have dug up some encoding options for libavcodec that give as good a quality for file size with first pass running at 50fps and 2nd pass at 12fps, so will give up with xvid for now
```
mencoder "input.m2v" -idx -ovc lavc -lavcopts vcodec=mpeg4:aspect=16/9:vbitrate=600:mbd=2:trell:v4mv:last_pred=2:dia=-1:vmax_b_frames=2:vb_strategy=1:cmp=3:subcmp=3:precmp=0:vqcomp=0.6:turbo:vpass=1 -vf pp=lb -o /dev/null


mencoder "input.m2v" -idx -ovc lavc -lavcopts vcodec=mpeg4:aspect=16/9:vbitrate=600:mbd=2:trell:v4mv:last_pred=2:dia=-1:vmax_b_frames=2:vb_strategy=1:cmp=3:subcmp=3:precmp=0:vqcomp=0.6:turbo:vpass=2 -vf pp=lb -o "output.avi"
```

---

### Post by Major_Kong on 2009-09-28
> **Jose Catre-Vandis said:**
> Thanks, I'll give it a whirl:
Direct links:
[http://ppa.launchpad.net/rvm/mplayer/ubuntu/pool/main/m/mplayer/mencoder_1.0~rc3+svn20090904-0jaunty2_i386.deb](http://ppa.launchpad.net/rvm/mplayer/ubuntu/pool/main/m/mplayer/mencoder_1.0~rc3+svn20090904-0jaunty2_i386.deb)
[http://ppa.launchpad.net/rvm/mplayer/ubuntu/pool/main/m/mplayer/mplayer_1.0~rc3+svn20090904-0jaunty2_i386.deb](http://ppa.launchpad.net/rvm/mplayer/ubuntu/pool/main/m/mplayer/mplayer_1.0~rc3+svn20090904-0jaunty2_i386.deb)

Not having any problems with the remux (speed or otherwise), what are the benefits of avibox over what I am doing?

I find avibox more reliable than mplayer for muxing.

EDIT: Did you check mplayer's dependencies ?

---

### Post by Jose Catre-Vandis on 2009-09-28
Didn't give up the search for a solution, and hopefully found one over on the SUSE forums.

1. Install nasm (needs to be 2.05+, which it is in Jaunty)
```
sudo apt-get install nasm
```

2. Recompile xvid 1.21, from the xvidcore/build/generic directory
```
./configure
make
sudo make install
```

This brought encoding speeds up to 30fps for 1st pass and 25fps for 2nd pass.

I'll mark as solved for now :)

---

