---
title: "mencoder/mplayer reach EOF before end of DVD"
date: 2014-03-10
forum: Multimedia Software
---

### Post by antony4 on 2014-03-10
Hello,

I am trying to rip my DVDs for my media server collection. I have it working for most of them, but I have hit a problem with one disc where the encoding stops before the actual movies finishes, leaving me with only a partial movie. The same issue happens if I use mplayer to play the DVD - it just quits near the end. I can't play any chapters beyond the 41st (though it is correctly identified as having 51 chapters in total). The same happens in VLC if I use that to play the DVD.

I suspect it's either a codec or css issue, but it's way beyond my knowledge to work out.
The DVD is the digitally mastered Star Wars Episode VI - Return of the Jedi ... DVD9 Dual Layer Region 2 (is layer transition going to be an issue??)

Here is the command and  output of mplayer when playing the last "playable" chapter (41), which it aborts:

mad@LinuxMint ~ $ mplayer dvd://1 -chapter 41
MPlayer svn r34540 (Ubuntu), built with gcc-4.7 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://1.
libdvdread: Using libdvdcss version 1.2.13 for DVD access
There are 17 titles on this DVD.
There are 5 angles in this DVD title.

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00006dcb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000710c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0004e18a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x003ca0c0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x003ca124
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x003cf092
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x003cf104
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x003d21f9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x003d225d
libdvdread: Elapsed time 0
libdvdread: Found 4 VTS's
libdvdread: Elapsed time 0
audio stream: 0 format: ac3 (5.1) language: en aid: 128.
audio stream: 1 format: ac3 (stereo) language: en aid: 129.
audio stream: 2 format: ac3 (stereo) language: en aid: 130.
number of audio channels on disk: 3.
subtitle ( sid ): 1 language: en
subtitle ( sid ): 3 language: da
subtitle ( sid ): 5 language: fi
subtitle ( sid ): 7 language: no
subtitle ( sid ): 9 language: sv
subtitle ( sid ): 11 language: en
subtitle ( sid ): 13 language: en
subtitle ( sid ): 15 language: en
number of subtitles on disk: 8

MPEG-PS file format detected.
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  9800.0 kbps (1225.0 kbyte/s)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 53.35.0 (external)
Mismatching header version 53.32.2
Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
[ac3 @ 0x7fa9ee5df340]frame sync error
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [ffac3] afm: ffmpeg (FFmpeg AC-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
Unsupported PixelFormat 61
Unsupported PixelFormat 53
Unsupported PixelFormat 81
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [vdpau] 720x576 => 1024x576 Planar YV12 
A:2880.4 V:2880.4 A-V: -0.000 ct: -0.208 1624/1624  6%  3%  0.8% 1 0 
[ac3 @ 0x7fa9ee5df340]incomplete frame
A:2880.6 V:2880.8 A-V: -0.255 ct: -0.237 1635/1635  6%  3%  0.8% 1 0 


Exiting... (End of file)

---

