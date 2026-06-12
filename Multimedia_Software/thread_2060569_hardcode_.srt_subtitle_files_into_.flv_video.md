---
title: "hardcode .srt subtitle files into .flv video"
date: 2012-09-20
forum: Multimedia Software
---

### Post by hislordship on 2012-09-20
help please:-) !! 
I have been trying to encode an .srt subtitle file into a .flv video using mencoder and avidemux - without success so far.

This is the input I did as well as the output I got: 

earthling@earthling ~ $ mencoder ./t4IDy-0CJbE.flv -sub ./iranium/iraniumger.srt  -font Arial -subfont-text-scale 3 -oac copy -ovc lavc vcodec=mpeg4:mbd=2:trell:vpass=2 -of mpeg -o film_sub.mpg MEncoder svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team success: format: 0  data: 0x0 - 0x158be338 libavformat version 53.21.0 (external) Mismatching header version 53.19.0 libavformat file format detected. [flv @ 0x725f00]Estimating duration from bitrate, this may be inaccurate [lavf] stream 0: video (h264), -vid 0 [lavf] stream 1: audio (aac), -aid 0 VIDEO:  [H264]  752x480  0bpp  29.970 fps  728.9 kbps (89.0 kbyte/s) [V] filefmt:44  fourcc:0x34363248  size:752x480  fps:29.970  ftime:=0.0334 PACKET SIZE: 2048 bytes, deltascr: 245760 libavcodec version 53.35.0 (external) Mismatching header version 53.32.2 Opening video filter: [expand osd=1] Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1 ========================================================================== Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264) ========================================================================== Audio format 0x4134504d is incompatible with '-oac copy', please try '-oac pcm' instead or use '-fafmttag' to override it.  Exiting... 


I have a video in flv format and subtitles in srt format. Can anyone give me instructions in how I can turn that into a video with subtitles embetted into it?

---

