---
title: "problem making avi's with cinelerra"
date: 2009-11-02
forum: Multimedia Software
---

### Post by Murdoc_of_puts on 2009-11-02
Hi, 
So I'm making my shot at making some movies. I'm using cinelerra.  It was having trouble making avi's through ffmpeg.(the manual says to export into .mov-then convert over to avi through 2 runs throughffmpeg). I recently upgraded all of my codecs for mplayer via [this]("http://ubuntuforums.org/showthread.php?t=1081070&highlight=install+ffmpeg&page=01"), only it didn't work, and I'm still getting the same problem that I was getting before I followed the guide; which is this.
> dingus@dingus-laptop:~/Desktop/steel$ mencoder yo2.mov -ovc xvid -xvidencopts bitrate=600:pass=1 -vf scale=320:240 -oac mp3lame -lameopts abr:br=64 -o output.avi
MEncoder 2:1.0~rc2-0ubuntu19+medibuntu1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) M processor 2.00GHz (Family: 6, Model: 13, Stepping: 8)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x2dfa8771
Quicktime/MOV file format detected.
[mov] Video stream found, -vid 0
VIDEO:  [yuv2]  720x480  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:7  fourcc:0x32767579  size:720x480  fps:29.97  ftime:=0.0334
xvid: using library version 1.1.2 (build xvid-1.1.2)
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [scale w=320 h=240]
==========================================================================
Cannot find codec matching selected -vo and video format 0x32767579.
Read DOCS/HTML/en/codecs.html!
==========================================================================

Exiting...
  I would greatly appreciate any help that I can get.  Thanks in advance.

---

