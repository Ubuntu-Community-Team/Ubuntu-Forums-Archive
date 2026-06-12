---
title: "mencoder -lavcopts error"
date: 2011-05-04
forum: Multimedia Software
---

### Post by Stundon on 2011-05-04
so when I try to convert a file using this code :

mencoder -ovc lavc -oac lavc -of lavf \ -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:\ vbitrate=1000:threads=auto:acodec=libfaac -af \ lavcresample=24000 -vf scale=480:272,harddup \ -lavfopts format=psp -ofps 30000/1001 \ INPUT FILE.avi -o OUTPUTFILE.mp4

I get this response :

 MEncoder 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
File not found: ' -lavcopts'
Failed to open  -lavcopts.
Cannot open file/device.

Where can I download -lavcopts? I checked the Ubuntu Software center and various forums on here and other sites, but haven't had any luck. Any help is much appreciated.

---

### Post by Stundon on 2011-05-04
ok so now, after trying several different options, I got this error :

MEncoder 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
success: format: 0  data: 0x0 - 0x2bbf1e4c
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  624x352  24bpp  23.976 fps  968.6 kbps (118.2 kbyte/s)
[V] filefmt:3  fourcc:0x44495658  size:624x352  fps:23.976  ftime:=0.0417
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
** MUXER_LAVF *****************************************************************
REMEMBER: MEncoder's libavformat muxing is presently broken and can generate
INCORRECT files in the presence of B-frames. Moreover, due to bugs MPlayer
will play these INCORRECT files as if nothing were wrong!
*******************************************************************************
OK, exit.
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [harddup]
Opening video filter: [scale w=368 h=208]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
Audio LAVC, couldn't find encoder for codec libaac.


Any thoughts?

---

