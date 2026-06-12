---
title: "I can't get mencoder to find divx4 codec"
date: 2007-03-15
forum: Multimedia &amp; Video
---

### Post by grahams on 2007-03-15
Anyone know how encode with mencoder using the Divx4 codec?

The output of 'mencoder -ovc help' shows it isn't available.

MEncoder 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) III Mobile CPU      1000MHz (Family: 6, Model: 11, Stepping: 1)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.

Available codecs:
   copy     - frame copy, without re-encoding. Doesn't work with filters.
   frameno  - special audio-only file for 3-pass encoding, see DOCS.
   raw      - uncompressed video. Use fourcc option to set format explicitly.
   nuv      - nuppel video
   lavc     - libavcodec codecs - best quality!
   vfw      - VfW DLLs, read DOCS/HTML/en/encoding-guide.html.
   qtvideo  - QuickTime DLLs, currently only SVQ1/3 are supported.
   libdv    - DV encoding with libdv v0.9.5
   xvid     - XviD encoding
   x264     - H.264 encoding

If I try -ovc div4 
i get
Couldn't find video filter 'divx4'

My system has the codecs (I think) as xine and mplayer can play Divx encoded files.

partial list 
/usr/lib/codecs/divxa32.acm
/usr/lib/codecs/divx_c32.ax
/usr/lib/codecs/divxc32.dll
/usr/lib/codecs/divxdec.ax
/usr/lib/codecs/divx.dll

any clues

---

### Post by mcduck on 2007-03-15
Why not use xvid codec instead? It produces standard MPEG4 video files just like DivX does.

---

### Post by grahams on 2007-03-15
Thanks for the reply I normally do use xvid, however I found files encoded with mencoder and the xvid codec don't play correctly (checkerboard pixalation) on a Philips dvp5960.

I just found that transcode sees a lot more codecs (including divx4, 5 etc.) I don't understand why mencoder does not pick them up.

I'll see if transcoded encoded file swill play correctly.

---

### Post by grahams on 2007-03-18
transcode can use the codec I needed, I'd prefer to use mencoder as it is easier to understand. 

I'm still confused on why mencoder doesn't see any other codecs.

---

### Post by grahams on 2007-03-27
After more reading & playing, if I use the lavc's mpeg4  codec I can encode using mencoder and create files that play ok if I set fourccs to DIVX for my DVD to play the file. (lavc mpeg4 fourccs = fmp4, which my dvd player doesn't recognise).

---

### Post by asbesto on 2007-07-14
Ok, but this doesn't solve the problem: where are the divx codecs for mplayer ? How can I install them ? Why they disappeared  in this ubuntu feisty ?

:confused: :(

Can someone help please ? tnx!

---

### Post by Major_Kong on 2007-07-14
I didn't know you could encode ot Divx using mencoder. Are you sure you can ?

EDIT: Making mencoder use libavcodec or using ffmpeg is probably a better choice for what you want.

---

