---
title: "Auto convert nuv to xvid?"
date: 2008-06-14
forum: Mythbuntu
---

### Post by saab_biopower on 2008-06-14
Hi,

I have problem with autoconvert in Mythtv. 

This works ok! Both in mythtv jobque and in terminal:
nuvexport-xvid --mencoder --nice 8 --input="/home/mythtv/1009_20080612093000.nuv"

I want this to work, but it doesnt (not in mythtv or terminal/shell. Why?
nuvexport-xvid --mencoder --nice 8 --input="%FILE%"

I found a nice "how to" thread in this forum, but i found no answer on this problem.

All helps are thankful!

BR
Mike

---

### Post by ian dobson on 2008-06-14
Hi,

Maybe this might help you :- [http://garett.harnish.ca/scripts/nuv2xvid.html](http://garett.harnish.ca/scripts/nuv2xvid.html)

Regards
Ian Dobson

---

### Post by saab_biopower on 2008-06-14
Thx for a fast answer, but i tried it without success. "21: Syntax error ..."

Does it work for you? How does your jobque command looks like?

BR
Mike

---

### Post by ian dobson on 2008-06-15
Hi,

When I was playing about with Myth before I setup my full system, I played with an old analog card (I'm now using a PVR-150 and a DVB-C card).

I played with the script and it appeared to work for me. If you want I'll put on my Hackers Hat this afternoon and have a look at it.

Regards
Ian Dobson

---

### Post by ian dobson on 2008-06-15
Hi,

can you try converting a nuv file using mencoder, from the command line, something like:-

mencoder -oac mp3lame -ovc lavc -lavcopts vcodec=mpeg4:vstrict=1:vhq:keyint=0:vbitrate=750 -vf scale=1024:576,lavcdeint -endpos 1500 -ffourcc DX50 -o "/tmp/output.avi" imput.nuv

or maybe this:-
mencoder test.nuv -ovc xvid -xvidencopts bitrate=687 -oac mp3lame -o out.avi

Note I don't have a nuv file here to test it but I think this should work.

Regards
Ian Dobson

---

### Post by saab_biopower on 2008-06-15
> **ian dobson said:**
> If you want I'll put on my Hackers Hat this afternoon and have a look at it.


Hehe, i wish i had that hackers hat :)

Thx for helping! My outputs:

$ mencoder 2048_20080614233000.nuv -ovc xvid -xvidencopts bitrate=687 -oac mp3lame -o out.avi
MEncoder 2:1.0~rc2-0ubuntu13 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(R) CPU 2.40GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x6cfec26b
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [RJPG]  480x576  10bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:44  fourcc:0x47504A52  size:480x576  fps:25.00  ftime:=0.0400
==========================================================================
Cannot find codec for audio format 0x41574152.
Read DOCS/HTML/en/codecs.html!
==========================================================================
xvid: using library version 1.1.2 (build xvid-1.1.2)
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffnuv] vfm: ffmpeg (NuppelVideo)
==========================================================================
VDec: vo config request - 480 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar I420 as output csp (no 0)
Movie-Aspect is 1.11:1 - prescaling to correct movie aspect.
videocodec: XviD (480x576 fourcc=44495658 [XVID])
xvid: par=0/0 (vga11), displayed=640x576, sampled=480x576
xvid: CBR Rate Control -- bitrate=687kbit/s
Writing header...
ODML: vprp aspect is 16384:14745.
Writing header...
ODML: vprp aspect is 16384:14745.
Pos:  47.4s   1187f ( 2%) 14.66fps Trem:  53min 156mb  A-V:0.000 [677:0]]
Too many audio packets in the buffer: (2048 in 8388608 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Flushing video frames.
Writing index...
Writing header...
ODML: vprp aspect is 16384:14745.

Video stream:  676.980 kbit/s  (84622 B/s)  size: 4017878 bytes  47.480 secs  1187 frames
$ 

and

$ mencoder 2048_20080614233000.nuv -ovc xvid -xvidencopts bitrate=687 -oac mp3lame -o out.avi
MEncoder 2:1.0~rc2-0ubuntu13 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(R) CPU 2.40GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x6cfec26b
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [RJPG]  480x576  10bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:44  fourcc:0x47504A52  size:480x576  fps:25.00  ftime:=0.0400
==========================================================================
Cannot find codec for audio format 0x41574152.
Read DOCS/HTML/en/codecs.html!
==========================================================================
xvid: using library version 1.1.2 (build xvid-1.1.2)
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffnuv] vfm: ffmpeg (NuppelVideo)
==========================================================================
VDec: vo config request - 480 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar I420 as output csp (no 0)
Movie-Aspect is 1.11:1 - prescaling to correct movie aspect.
videocodec: XviD (480x576 fourcc=44495658 [XVID])
xvid: par=0/0 (vga11), displayed=640x576, sampled=480x576
xvid: CBR Rate Control -- bitrate=687kbit/s
Writing header...
ODML: vprp aspect is 16384:14745.
Writing header...
ODML: vprp aspect is 16384:14745.
Pos:  47.4s   1187f ( 2%) 12.86fps Trem:  61min 156mb  A-V:0.000 [677:0]]
Too many audio packets in the buffer: (2048 in 8388608 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Flushing video frames.
Writing index...
Writing header...
ODML: vprp aspect is 16384:14745.

Video stream:  676.980 kbit/s  (84622 B/s)  size: 4017878 bytes  47.480 secs  1187 frames
$ 

hmmm, ???

/Mike

---

### Post by ian dobson on 2008-06-15
Hi,

Can you upload a small NUV file to some web space, I don't have any NUV files here to play with and although it's good start somethings not quite right.  It looks as if my hackers hat doesn't quite fit :)

If you don't have any web space PM me and I'll create an FTP account on my server for you.

Regards
Ian Dobson

---

