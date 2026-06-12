---
title: "[SOLVED] [HELP]Mencoder doesnt wrok after update!!"
date: 2007-11-21
forum: Multimedia &amp; Video
---

### Post by chacham23 on 2007-11-21
It worked great for some time and now after I run the "update manager" it gave me this error when I try to convert mkv to mp4(for my psp)

```

:~/Torrent/The.Departed.2006.HD.DVDRip.720p.x264.AC3-5.1-iLL/!sample$ mencoder The.Departed.2006.HD.DVDRip.720p.x264.AC3-5.1-iLL.sample.mkv -oac lavc -ovc lavc -of lavf -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:vbitrate=500:acodec=libaac -af lavcresample=24000 -vf scale=368:208,harddup -lavfopts format=psp -ofps 30000/1001 -of lavf -lavfopts format=psp -o  try.mp4
MEncoder 2:1.0~rc2-0ubuntu1~gutsy1 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3200+ (Family: 15, Model: 47, Stepping: 2)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x42d18b7
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_AC3), -aid 0, -alang eng
[mkv] Track ID 3: subtitles (S_TEXT/UTF8), -sid 0, -slang eng
[mkv] Track ID 4: subtitles (S_TEXT/UTF8), -sid 1, -slang fre
[mkv] Track ID 5: subtitles (S_TEXT/UTF8), -sid 2, -slang spa
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1280x528  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:31  fourcc:0x31637661  size:1280x528  fps:23.98  ftime:=0.0417
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
** MUXER_LAVF *****************************************************************
REMEMBER: MEncoder's libavformat muxing is presently broken and can generate
INCORRECT files in the presence of B frames. Moreover, due to bugs MPlayer
will play these INCORRECT files as if nothing were wrong!
*******************************************************************************
OK, exit
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [harddup]
Opening video filter: [scale w=368 h=208]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
Audio LAVC, couldn't find encoder for codec libaac.

Exiting...

```

I tried to ask here: [http://ubuntuforums.org/showthread.php?t=567016](http://ubuntuforums.org/showthread.php?t=567016)
but no answer...
please help :confused:

---

### Post by eye208 on 2007-11-21
Try changing "acodec=libaac" to "acodec=libfaac" or use -oac faac instead of -oac lavc.

---

### Post by chacham23 on 2007-11-21
OK I succeded with changing the "aac" to "libfaac" thanks m8!!!

---

