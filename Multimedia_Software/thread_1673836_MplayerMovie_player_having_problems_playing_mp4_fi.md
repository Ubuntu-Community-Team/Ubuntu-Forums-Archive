---
title: "Mplayer/Movie player having problems playing mp4 file"
date: 2011-01-23
forum: Multimedia Software
---

### Post by jbenalluch on 2011-01-23
Hello,

I have the following problem:

I have some mp4 files that I want to play on my media box (Running ubuntu 10.10). Now when I play them sound seems fine but video displays some of the image along with altered colors and lots of garbage; I also get an error message (shown below). 

This file however plays fine when using VLC.

I have another box (my laptop) also running ubuntu 10.10 on which the files are played with no problems with mplayer, Movie player and VLC.

I'm not quite sure what is going on or why the files are getting being played wrong on my media box.

Any help would be greatly appreciated.


```

MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team

Playing Disc 1- Main Course Part One.mp4.
libavformat file format detected.
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x9b2d400]Could not find codec parameters (Video: mpeg4)
LAVF_header: av_find_stream_info() failed
ISO: File Type Major Brand: ISO/IEC 14496-1 (MPEG-4 system) v2
Quicktime/MOV file format detected.
[mov] Video stream found, -vid 0
Warning! pts=433173504  length=433174528
[mov] Audio stream found, -aid 1
VIDEO:  [mp4v]  640x480  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
AUDIO: 44100 Hz, 2 ch, s16le, 125.5 kbit/8.89% (ratio: 15690->176400)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
[mpeg4 @ 0x1c8ec00]hmm, seems the headers are not complete, trying to guess time_increment_bits
[mpeg4 @ 0x1c8ec00]my guess is 5 bits ;)
[mpeg4 @ 0x1c8ec00]looks like this file was encoded with (divx4/(old)xvid/opendivx) -> forcing low_delay flag
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 640x480 => 640x480 Planar YV12 
[mpeg4 @ 0x1c8ec00]I cbpy damaged at 0 0
[mpeg4 @ 0x1c8ec00]Error at MB: 0
[mpeg4 @ 0x1c8ec00]concealing 1200 DC, 1200 AC, 1200 MV errors
[mpeg4 @ 0x1c8ec00]ac-tex damaged at 0 0   1/  1 ??% ??% ??,?% 0 0 
[mpeg4 @ 0x1c8ec00]Error at MB: 0
[mpeg4 @ 0x1c8ec00]concealing 1200 DC, 1200 AC, 1200 MV errors
[mpeg4 @ 0x1c8ec00]ac-tex damaged at 0 0   2/  2 ??% ??% ??,?% 1 0 
[mpeg4 @ 0x1c8ec00]Error at MB: 0
[mpeg4 @ 0x1c8ec00]concealing 1200 DC, 1200 AC, 1200 MV errors
[mpeg4 @ 0x1c8ec00]ac-tex damaged at 0 0   3/  3 ??% ??% ??,?% 2 0 
[mpeg4 @ 0x1c8ec00]Error at MB: 0
[mpeg4 @ 0x1c8ec00]concealing 1200 DC, 1200 AC, 1200 MV errors
[mpeg4 @ 0x1c8ec00]ac-tex damaged at 0 0   4/  4 ??% ??% ??,?% 2 0 
[mpeg4 @ 0x1c8ec00]Error at MB: 0
[mpeg4 @ 0x1c8ec00]concealing 1200 DC, 1200 AC, 1200 MV errors
[mpeg4 @ 0x1c8ec00]ac-tex damaged at 0 0   5/  5 ??% ??% ??,?% 3 0 
[mpeg4 @ 0x1c8ec00]Error at MB: 0
[mpeg4 @ 0x1c8ec00]concealing 1200 DC, 1200 AC, 1200 MV errors
[mpeg4 @ 0x1c8ec00]ac-tex damaged at 0 0   6/  6 ??% ??% ??,?% 3 0 
[mpeg4 @ 0x1c8ec00]Error at MB: 0
[mpeg4 @ 0x1c8ec00]concealing 1200 DC, 1200 AC, 1200 MV errors
[mpeg4 @ 0x1c8ec00]ac-tex damaged at 0 0   7/  7 ??% ??% ??,?% 3 0 
[mpeg4 @ 0x1c8ec00]Error at MB: 0
[mpeg4 @ 0x1c8ec00]concealing 1200 DC, 1200 AC, 1200 MV errors
[mpeg4 @ 0x1c8ec00]ac-tex damaged at 0 0   8/  8 ??% ??% ??,?% 3 0 
[mpeg4 @ 0x1c8ec00]Error at MB: 0
[mpeg4 @ 0x1c8ec00]concealing 1200 DC, 1200 AC, 1200 MV errors
[mpeg4 @ 0x1c8ec00]ac-tex damaged at 0 0   9/  9 ??% ??% ??,?% 3 0 
[mpeg4 @ 0x1c8ec00]Error at MB: 0
[mpeg4 @ 0x1c8ec00]concealing 1200 DC, 1200 AC, 1200 MV errors
[mpeg4 @ 0x1c8ec00]ac-tex damaged at 0 0  10/ 10 ??% ??% ??,?% 3 0 
[mpeg4 @ 0x1c8ec00]Error at MB: 0
[mpeg4 @ 0x1c8ec00]concealing 1200 DC, 1200 AC, 1200 MV errors
[mpeg4 @ 0x1c8ec00]ac-tex damaged at 0 0  11/ 11 ??% ??% ??,?% 3 0 
[mpeg4 @ 0x1c8ec00]Error at MB: 0
[mpeg4 @ 0x1c8ec00]concealing 1200 DC, 1200 AC, 1200 MV errors
[mpeg4 @ 0x1c8ec00]ac-tex damaged at 0 0  12/ 12 ??% ??% ??,?% 3 0 
[mpeg4 @ 0x1c8ec00]Error at MB: 0
[mpeg4 @ 0x1c8ec00]concealing 1200 DC, 1200 AC, 1200 MV errors
[mpeg4 @ 0x1c8ec00]ac-tex damaged at 0 0  13/ 13 ??% ??% ??,?% 3 0 
[mpeg4 @ 0x1c8ec00]Error at MB: 0
[mpeg4 @ 0x1c8ec00]concealing 1200 DC, 1200 AC, 1200 MV errors

```

---

### Post by jbenalluch on 2011-01-23
Sorry for double posting.

Here is the output of mplayer on the system that works:

```

Creating config file: /home/jamil/.mplayer/config
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Disc 1- Main Course Part One.mp4.
libavformat file format detected.
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x966f8f0]Could not find codec parameters (Video: mpeg4, yuv420p)
LAVF_header: av_find_stream_info() failed
ISO: File Type Major Brand: ISO/IEC 14496-1 (MPEG-4 system) v2
Quicktime/MOV file format detected.
[mov] Video stream found, -vid 0
Warning! pts=433173504  length=433174528
[mov] Audio stream found, -aid 1
VIDEO:  [mp4v]  640x480  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
[VO_XV] Could not grab port 71.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
AUDIO: 44100 Hz, 2 ch, s16le, 125.5 kbit/8.89% (ratio: 15690->176400)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
[mpeg4 @ 0x1442860]hmm, seems the headers are not complete, trying to guess time_increment_bits
[mpeg4 @ 0x1442860]my guess is 15 bits ;)
[mpeg4 @ 0x1442860]looks like this file was encoded with (divx4/(old)xvid/opendivx) -> forcing low_delay flag
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 640x480 => 640x480 Planar YV12 
A:  50.2 V:  50.2 A-V:  0.000 ct:  0.023 1505/1505  8%  0%  5.0% 3 0 
Exiting... (Quit)

```

---

### Post by jbenalluch on 2011-01-23
never mind it seems my non working system was running 10.04, upgrading it to 10.10 did the trick.

---

