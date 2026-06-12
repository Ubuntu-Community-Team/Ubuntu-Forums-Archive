---
title: "AcidRip Crop detection"
date: 2010-02-09
forum: Multimedia Software
---

### Post by banoncom on 2010-02-09
Help!

Has anyone been having issues with crop detection using acidrip on ubuntu 9.10.

I have been using it on 9.04 with no problems at all, I have tried it on several systems with 9.10 and the crop detection will not work - comes back with the message "crop detection failed - is the DVD loaded?"
Yes! the DVD is loaded, I have tried it with DVD from the dvd drive and also mounted ISO's.
As I said I am currently using acidrip on 9.04 with no problems. I have found very very little info on the forums which makes me think it is not a common problem. - Am i missing something??

PS - it encodes the DVD to divx no problems, just doesn't do the crop detection which is very handy.

Cheers.

---

### Post by plughead on 2010-02-25
Yup, same problem here.  There is a PPC cropping option on the settings page, which I tried.  It at least detects the dvd, but the results are unusable.  I suspect the problem is with mencoder, but I have no idea what do do about it.  Is there another encoder that can replace it?

---

### Post by wdaniels on 2010-07-10
I'm having similar trouble with AcidRip on Lucid. As an example, the debug output for the DVD I'm trying to rip shows this:

```
AcidRip message - Crop detection in progress... please wait
AcidRip message - Running mplayer -vf cropdetect dvd://1 -dvd-device /dev/dvd -nosound -vo null -frames 10 -sstep 59 -nocache
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.

Playing dvd://1.
libdvdread: Using libdvdcss version 1.2.10 for DVD access
There are 8 titles on this DVD.
There are 1 angles in this DVD title.

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000014a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001bf
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000ae4f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x000a8323
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000a8370
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00144eac
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00144ef9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x001df9f3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x001dfa40
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x0027f719
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0027f766
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x0031be60
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x0031bead
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x003bb63d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003bb68a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x003bb72e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x003bb77b
libdvdread: Elapsed time 0
libdvdread: Found 8 VTS's
libdvdread: Elapsed time 0
audio stream: 0 format: ac3 (stereo) language: en aid: 128.
number of audio channels on disk: 1.
subtitle ( sid ): 0 language: en
number of subtitles on disk: 1
MPEG-PS file format detected.
VIDEO:  MPEG2  720x576  (aspect 2)  25.000 fps  9800.0 kbps (1225.0 kbyte/s)
Opening video filter: [cropdetect]
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Opening video filter: [lavc]
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
Audio: no sound
Starting playback...
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
[mpeg1video @ 0x1a511a0]removing common factors from framerate
VO: [null] 720x576 => 768x576 Mpeg PES
[mpeg2video @ 0x1a51900]ac-tex damaged at 44 0
[mpeg2video @ 0x1a51900]Warning MVs not available
[mpeg2video @ 0x1a51900]concealing 1620 DC, 1620 AC, 1620 MV errors
V:   0.0   1/  1 ??% ??% ??,?% 0 0
V:   0.3   2/  2 ??% ??% ??,?% 0 0
V:  59.4   3/  3 ??% ??% ??,?% 0 0
V: 118.4   4/  4 ??% ??% ??,?% 0 0
V: 177.5   5/  5 ??% ??% ??,?% 0 0
V: 236.5   6/  6 ??% ??% ??,?% 0 0
V: 295.6   7/  7 ??% ??% ??,?% 0 0
V: 354.6   8/  8 ??% ??% ??,?% 0 0
V: 413.6   9/  9 ??% ??% ??,?% 0 0
V: 472.7  10/ 10 ??% ??% ??,?% 0 0
V: 531.7  11/ 11 ??% ??% ??,?% 0 0
V: 590.8  12/ 12 ??% ??% ??,?% 0 0
V: 649.8  13/ 13 ??% ??% ??,?% 0 0
V: 708.8  14/ 14 ??% ??% ??,?% 0 0
V: 767.9  15/ 15 ??% ??% ??,?% 0 0
V: 826.9  16/ 16 ??% ??% ??,?% 0 0
V: 886.0  17/ 17 ??% ??% ??,?% 0 0
V: 945.0  18/ 18 ??% ??% ??,?% 0 0
V:1004.0  19/ 19 ??% ??% ??,?% 0 0
V:1063.1  20/ 20 ??% ??% ??,?% 0 0
V:1122.1  21/ 21 ??% ??% ??,?% 0 0
V:1181.2  22/ 22 ??% ??% ??,?% 0 0
V:1240.2  23/ 23 ??% ??% ??,?% 0 0
V:1299.2  24/ 24 ??% ??% ??,?% 0 0
V:1358.3  25/ 25 ??% ??% ??,?% 0 0
V:1417.3  26/ 26 ??% ??% ??,?% 0 0
V:1476.4  27/ 27 ??% ??% ??,?% 0 0
V:1535.4  28/ 28 ??% ??% ??,?% 0 0
V:1594.4  29/ 29 ??% ??% ??,?% 0 0
V:1653.5  30/ 30 ??% ??% ??,?% 0 0
V:   0.0  30/ 30 ??% ??% ??,?% 0 0


Exiting... (End of file)
AcidRip message - Crop detection failed, is the DVD loaded?
```

There's a few different "errors" there, although it seems to rip the title perfectly OK. So I can't quite work out which of those errors is actually what causes the crop detection to fail.

Can anybody help?

---

### Post by gakon77 on 2011-05-11
Hello there!

No really sure what is the purpose of "crop detection" and if it would really improve the quality of my ripping. 

I use Acidrip in Ubuntu 9.10 and the crop detection never worked. It always says "Crop detection failed, is the DVD loaded?"

The best quality it gets here is with three passes and the bitrate set to the highest until bits/px flashes shining flipping red.

Salud y Ubuntu.

---

