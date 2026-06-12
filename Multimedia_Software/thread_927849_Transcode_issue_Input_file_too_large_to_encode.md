---
title: "Transcode issue: Input file too large to encode"
date: 2008-09-23
forum: Multimedia Software
---

### Post by radcc07 on 2008-09-23
I'm have a problem trying to encode a VRO file to a more 'editable' format.  

It appears that I can encode a VRO file of about 2GB (roughly 1hour) without problem with this command

transcode -i <VRO File> -o <Mpg file> -y ffmpeg -F mpeg4

Simple, yeah but it works.

The problem comes when I try to convert a 4GB VRO file (2 hours).  I get the following error.

[I]transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
(scan_pes.c) looks like an elementary stream - not program stream
[transcode] (probe) suggested AV correction -D 0 (0 ms) | AV 0 ms | 0 ms
[transcode] auto-probing source VR_MOVIE.VRO (ok)
[transcode] V: import format    | MPEG    (V=null|A=null)
[transcode] V: AV demux/sync    | (0) sync AV at PTS start - demuxer disabled
[transcode] V: import frame     | disabled
[transcode] V: bits/pixel       | 0.000 (unknown)
[transcode] V: decoding fps,frc | 25.000,0
[transcode] V: Y'CbCr           | YV12/I420
[transcode] A: import           | disabled
[transcode] A: export           | disabled
[transcode] V: encoding fps,frc | 25.000,3
[transcode] A: bytes per frame  | 0 (0.000000)
[transcode] A: adjustment       | 0@1000
[transcode] V: IA32/AMD64 accel | sse2 (sse2 sse mmxext mmx asm C)
tc_memcpy: using sse for memcpy
[transcode] V: video buffer     | 10 @ 0x0
[import_null.so] v0.2.0 (2002-01-19) (video) null | (audio) null
[export_null.so] v0.1.2 (2001-08-17) (video) null | (audio) null
[export_ffmpeg.so] v0.3.13 (2004-08-03) (video) Lavc1d.51.38.0 | (audio) MPEG/AC3/PCM
[export_ffmpeg.so] Using FFMPEG codec 'mpeg4' (FourCC 'DIVX', MPEG4 compliant video).[/I]
[COLOR="Red"]picture size invalid (0x0)
[export_ffmpeg.so] Could not allocate enough memory.[/COLOR]
[I][transcode] warning : (encoder.c) video export module error: init failed
[transcode] critical: failed to init encoder[/I]

My question, is there a way to increase the video buffer size which I'm guessing is the problem here?

---

### Post by NT4usB on 2008-09-23
[wag] Is there enough room wherever ffmpeg is writing it's temp files?
Maybe it's running out of room, failing, then cleaning up after itself so the directory doesn't show full when it's all done.

---

### Post by radcc07 on 2008-09-24
That could be a possibility.  I was wondering if there is a temp buffer I could readjust.  Could you direct me as to where I can check this regarding ffmpeg?

---

### Post by johnjoe on 2008-12-22
Hi
I had  a similar problem with .VRO files on a DVD-RAM disk from  a video recorder which I needed to edit and transfer to a DVD-R video disk. 

Below is the method I used, it may be of use to you.
I did try avidemux but had sound sync problems.

Ubuntu Studio 7.10 (Kernel 2.6.22-14-rt)  (gutsy) with VLC installed

Programs 
(1)vrosplit  vrosplit_0.12_i386.deb(command line program)
(2)dvbcut_0.5.4_i386.deb
(3)qdvdauthor_1.0.0~rc1-0ubuntu1_i386.deb

1.I googled  vrosplit and found an altair site which when translated in google gave access to a deb file and the source code. There was also instructions which I could only take a screen photo of to get a copy.  I installed the deb file without problems and after working out the syntax have been able to extract to .mpg files for processing. 
2.
IMPORTANT NOTE  dvbcut can work directly on the .VRO file  but it needs to write an index file and will CORUPT the file system on the DVD-RAM disk. If you copy the .VRO file to a hard drive you can then make the whole file into mpg or split it accordingly.
 
I am only six weeks into Linux and I could not compile the source, but I did compile it on PCLinuxOS2007 and it worked.

     2.  I downloaded the other two programs and their dependencies and have had no trouble so far
		   
     3.  I have used qdvdauthor to make DVD's from these files

Hope this is of some use
Regards john

---

### Post by johnjoe on 2008-12-22
Further to my previous post

NOTE 
I have found that if the VRO file has been edited with the original recorder it is more difficult to process.

John

---

