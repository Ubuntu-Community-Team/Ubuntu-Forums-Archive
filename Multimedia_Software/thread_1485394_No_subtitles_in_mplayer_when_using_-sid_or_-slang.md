---
title: "No subtitles in mplayer when using -sid or -slang"
date: 2010-05-16
forum: Multimedia Software
---

### Post by wwwookie on 2010-05-16
Edit - please ignore the Heron in my profile - I'm using Lucid

Hi, when I try to show dvd subtitles with mplayer using the options **-sid 0** or **-slang en** I get a movie but no subtitles are shown.

```
wookie@wookie-lucid:~$ mplayer dvd://2 -sid 0
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://2.
libdvdread: Using libdvdcss version 1.2.10 for DVD access
There are 5 titles on this DVD.
There are 1 angles in this DVD title.

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000012a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00002fdb
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00002fdb)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00002fe0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x00002fe0)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00003024
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000030f0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00178be1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00178be6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x0018a240
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0018a245
libdvdread: Elapsed time 0
libdvdread: Found 4 VTS's
libdvdread: Elapsed time 0
audio stream: 0 format: ac3 (stereo) language: it aid: 128.
number of audio channels on disk: 1.
subtitle ( sid ): 0 language: en
number of subtitles on disk: 1
MPEG-PS file format detected.
VIDEO:  MPEG2  720x576  (aspect 2)  25.000 fps  9800.0 kbps (1225.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
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
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 768x576 Planar YV12 
[mpeg2video @ 0x7934ac0]ac-tex damaged at 22 7
[mpeg2video @ 0x7934ac0]Warning MVs not available
[mpeg2video @ 0x7934ac0]concealing 1305 DC, 1305 AC, 1305 MV errors
No bind found for key 'MOUSE_BTN0'.                         4% 7 0 
No bind found for key 'MOUSE_BTN0'.                         2.2% 7 0 
A:  57.7 V:  57.6 A-V:  0.006 ct:  0.095 1437/1437 32%  3%  2.1% 7 0 
Exiting... (Quit)

```


I can fix this with the interactive keyboard control - pressing v gives me "subtitles disabled" and pressing again gives me "subtitles enabled", but no subs. Pressing j gives me "subtitles disabled" and again gives me "subtitles: (0) en" and the subtitles appear. This would be ok but I want to use mencoder from a shell script, not view films interactively.

This problem did not occur on the same machine running hardy. I'm having a little trouble with the Nvidia driver, so I checked the output file from mencoder with the same results, which makes me think it's not a display/x11 problem.

Ubuntu 10.4
P4 1.6G
512 MB RAM
Geforce 6600

---

### Post by Keith Hedger on 2010-05-19
Having exactly the same problem on mint and debian, the svn version seems to be ok but only uses a bitmap font for the subtitles and seems to ignore ~/.mplayer/subfont.ttf

Any ideas?

---

### Post by wwwookie on 2010-05-21
Just a bit more info - thought I'd try copying the dvd to a hard drive with "dvdbackup -M -o <directory>, to see if it was a problem with reading a physical disk. "mplayer dvd:// -sid 0 -dvd-device <directory>" gave exactly the same result - no subs until you use the interactive control.

---

### Post by lucio.torre on 2010-05-28
try adding " -ifo *.IFO "

---

### Post by wwwookie on 2010-05-29
Thanks, tried that, and specified the .IFO file explicitly but got the same results

```

mplayer dvd://1 -sid 0 -ifo /media/<dvd_title>/VIDEO_TS/VTS_01_0.IFO

```

Oddly enough, when you deliberately specify a non-existent .IFO, you get the same result too.

---

### Post by wwwookie on 2010-09-15
Hi, It's been a while - seems the bug is in the repo version of mplayer

I got a subversion snapshot of mplayer from [http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html) , compiled it and hey presto - problem solved!

---

