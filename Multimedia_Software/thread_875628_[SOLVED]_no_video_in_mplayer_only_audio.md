---
title: "[SOLVED] no video in mplayer only audio"
date: 2008-07-31
forum: Multimedia Software
---

### Post by lgeek on 2008-07-31
i got the following whenever i try to play any video.the audio works fine but there isn't any video..

MPlayer 1.0rc1-4.2.3 (C) 2000-2006 MPlayer Team
CPU: Genuine Intel(R) CPU           T2080  @ 1.73GHz (Family: 6, Model: 14, Stepping: 12)
Cannot test OS support for SSE, disabling to be safe.
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 0 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

Playing /media/MULTIMEDIA/music/english/videoz/ALTER BRIDGE/Alter Bridge- Broken Wings.mpg.
MPEG-PS file format detected.
VIDEO:  MPEG1  352x240  (aspect 12)  29.970 fps  1150.0 kbps (143.8 kbyte/s)
vo_cvidix: No vidix driver name provided, probing available ones (-v option for details)!
[VO_SUB_VIDIX] Couldn't find working VIDIX driver.
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 352 x 240 (preferred colorspace: Mpeg PES)
VDec: using Mpeg PES as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [null] 352x240 => 352x240 Mpeg PES 
Selected video codec: [mpegpes] vfm: mpegpes (MPEG-PES output (.mpg or DXR3/IVTV/DVB card))
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 224.0 kbit/15.87% (ratio: 28000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 352 x 240 (preferred colorspace: Mpeg PES)
VDec: using Mpeg PES as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [null] 352x240 => 352x264 Mpeg PES 
A: 259.2 V: 259.1 A-V:  0.024 ct:  0.067 7758/7758  0%  0%  0.7% 2 0            

also mplayer -vo gives me:

MPlayer 1.0rc1-4.2.3 (C) 2000-2006 MPlayer Team
CPU: Genuine Intel(R) CPU           T2080  @ 1.73GHz (Family: 6, Model: 14, Stepping: 12)
Cannot test OS support for SSE, disabling to be safe.
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 0 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
Error parsing option on the command line: -vo

it doesnot display the available drivers...
so i tried mplayer -vo help and then i gave:
MPlayer 1.0rc1-4.2.3 (C) 2000-2006 MPlayer Team
CPU: Genuine Intel(R) CPU           T2080  @ 1.73GHz (Family: 6, Model: 14, Stepping: 12)
Cannot test OS support for SSE, disabling to be safe.
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 0 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
Available video output drivers:
	cvidix	console VIDIX
	null	Null video output
	mpegpes	Mpeg-PES to DVB card
	yuv4mpeg	yuv4mpeg output for mjpegtools
	tga	Targa output
	pnm	PPM/PGM/PGMYUV file
	md5sum	md5sum of each frame
plz help....

---

### Post by shirilover on 2008-07-31
You don't seem to have some of the normal video output modules available (xv, x11, gl, gl2) that would normally be available.
I would suggest purging and re-installing/re-compiling mplayer.
If re-compiling, make sure you have all the necessary -dev packages installed.
An excellent guide for compiling mplayer can be found here -> [http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)

---

### Post by lgeek on 2008-08-01
hey!!! thnx finally it has started working.the problem was that the x11 headers and other dev packages were not installed.so i downloaded them and did ./configure which showed the support for x11.thnx a lot for your suggestion.:)

---

