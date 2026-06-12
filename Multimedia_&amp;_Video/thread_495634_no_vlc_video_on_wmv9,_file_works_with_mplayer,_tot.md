---
title: "no vlc video on wmv9, file works with mplayer, totem, xfmedia"
date: 2007-07-08
forum: Multimedia &amp; Video
---

### Post by secdroid on 2007-07-08
Posted this on the videolan (vlc) linux forums, but got no replies.  Help!!!  :)

I appear to have a wmv9 file in a non-DRM asf wrapper.  VLC can't play the .wmv file that plays perfectly with mplayer, totem, and xfmedia. The file is said to be compatible with vlc on all platforms, but I haven't verified that contention. However, that makes me think that there is something wrong my Ubuntu Dapper vlc config, particularly since the other media players have no problem on this box.  VLC does seem to work well with .avi, .mpeg, etc.  VLC problem is .wmv-unique 

Judging from the "mplayer -identify" info below, mplayer (like totem and xfmedia) had no trouble identifying the proper video codec, while vlc failed to either properly identify the file or locate the codec.

I strongly suspect that I have somehow misconfigured or misinstalled vlc.  Debug suggestions would be greatly appreciated.

My vlc info --
VLC media player 0.8.6a (wxWidgets interface)
...
Compiled by [email]videolan@altair.via.ecp.fr[/email].
Compiler: gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5).

***

VLC plays audio, but no video window when I try to play the file.

VLC log excerpt --
main debug: looking for decoder module: 24 candidates
ffmpeg debug: libavcodec initialized (interface 3276800 )
ffmpeg debug: ffmpeg codec (Windows Media Audio 2) started
main debug: using decoder module "ffmpeg"
main debug: thread 2960878512 (decoder) created at priority 0 (input/decoder.c:159)
main debug: looking for decoder module: 24 candidates
main error: no suitable decoder module for fourcc `WMV3'.
VLC probably does not support this sound or video format.
main debug: killing decoder fourcc `WMV3', 0 PES in FIFO
main debug: `T.wmv' successfully opened

main error: no suitable decoder module for fourcc `WMV3'.
VLC probably does not support this sound or video format.

***

Here's what mplayer & ffmpeg think --

mplayer -identify T.wmv
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
...
91 audio & 204 video codecs
...
Playing T.wmv.
ASF file format detected.
ID_AUDIO_ID=1
ID_VIDEO_ID=2
VIDEO: [WMV3] 480x360 24bpp 1000.000 fps 0.0 kbps ( 0.0 kbyte/s)
...
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 65.6 kbit/4.65% (ratio: 8205->176400)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
ID_FILENAME=T.wmv
ID_DEMUXER=asf
ID_VIDEO_FORMAT=WMV3
ID_VIDEO_BITRATE=0
ID_VIDEO_WIDTH=480
ID_VIDEO_HEIGHT=360
ID_VIDEO_FPS=1000.000
ID_VIDEO_ASPECT=0.0000
ID_AUDIO_CODEC=ffwmav2
ID_AUDIO_FORMAT=353
ID_AUDIO_BITRATE=65640
ID_AUDIO_RATE=44100
ID_AUDIO_NCH=2
ID_LENGTH=80.00
==========================================================================
Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
GetOutput r=0x0 size:518400 align:1
StreamCount r=0x0 1 1
Decoder supports the following formats: YV12 YUY2 UYVY YVYU RGB8 RGB555 RGB565 RGB24 RGB32
Decoder is capable of YUV output (flags 0x1b)
VDec: vo config request - 480 x 360 (preferred colorspace: Packed YUY2)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 480x360 => 480x360 Planar YV12
Selected video codec: [wmv9dmo] vfm: dmo (Windows Media Video 9 DMO)
==========================================================================
ID_VIDEO_CODEC=wmv9dmo
...
Starting playback...

---

### Post by secdroid on 2007-07-09
Problem solved.  It turns out that the latest version of vlc for Dapper/6.06 is 0.8.6a which _can not_ play this .wmv file.  I tested vlc 0.8.6.c (current version) under Windows XP and it could play the file properly.

Jean-Baptiste Kempf, vlc developer/site admin said:
> hmmmm... Okay. That is just because the dapper version is too old... I should make a new one.

You can't really do anything about it, except re-compiling, upgrading or waiting for a new package.
I tested that assertion by installing Xubuntu Feisty/7.04 on a test box, updating the install, and then installing vlc from the universe repository (per [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)).  It played the file correctly.

Therefore, if you are having trouble with .wmv files (when .wmv3 is logged and/or wmv 9 has a .wmv in an asf wrapper), vlc 0.8.6a _will not work_.  

Given that vlc 0.8.6c has a security update, it is preferred.

Gory details at [http://forum.videolan.org/viewtopic.php?f=13&t=38899](http://forum.videolan.org/viewtopic.php?f=13&t=38899)

---

