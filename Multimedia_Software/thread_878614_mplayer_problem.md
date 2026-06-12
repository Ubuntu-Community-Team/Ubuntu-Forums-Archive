---
title: "mplayer problem"
date: 2008-08-03
forum: Multimedia Software
---

### Post by blkno1 on 2008-08-03
I downloaded the source (apt-get source mplayer) and compiled mplayer with tivo support.  I compiled it with ./configure --enable-vstream

I get audio fine but no video at all, same when I try a reg .avi .mpg etc file too, just audio.


MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ (Family: 15, Model: 35, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2

Playing tivo://192.168.1.229/2517348.
Resolving 192.168.1.229 for AF_INET6...
Couldn't resolve name for AF_INET6: 192.168.1.229
Connecting to server 192.168.1.229[192.168.1.229]: 8074...
TiVo file format detected.
VIDEO:  MPEG2  480x480  (aspect 2)  29.970 fps  15000.0 kbps (1875.0 kbyte/s)
Can't open /dev/fb0: No such file or directory
[fbdev2] Can't open /dev/fb0: No such file or directory
VO: [v4l2] No such file or directory
vo_cvidix: No vidix driver name provided, probing available ones (-v option for details)!
[cyberblade] Error occurred during pci scan: Operation not permitted
[mach64] Error occurred during pci scan: Operation not permitted
[mga] Error occurred during pci scan: Operation not permitted
[mga] Error occurred during pci scan: Operation not permitted
[nvidia_vid] Error occurred during pci scan: Operation not permitted
[pm3] Error occurred during pci scan: Operation not permitted
[radeon] Error occurred during pci scan: Operation not permitted
[rage128] Error occurred during pci scan: Operation not permitted
[savage_vid] Error occurred during pci scan: Operation not permitted
[SiS] Error occurred during pci scan: Operation not permitted
[unichrome] Error occurred during pci scan: Operation not permitted
[VO_SUB_VIDIX] Couldn't find working VIDIX driver.
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 480 x 480 (preferred colorspace: Mpeg PES)
VDec: using Mpeg PES as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [null] 480x480 => 480x480 Mpeg PES 
Selected video codec: [mpegpes] vfm: mpegpes (MPEG-PES output (.mpg or DXR3/IVTV/DVB/V4L2 card))
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 480 x 480 (preferred colorspace: Mpeg PES)
VDec: using Mpeg PES as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [null] 480x480 => 640x480 Mpeg PES 
A:   9.0 V:   9.0 A-V:  0.000 ct: -0.033 270/270  0%  0%  0.7% 0 0

---

### Post by Orfintain on 2008-08-14
I'm getting couldn't resolve name as well for an audio stream , though not all real audio streams, I think it depends on source format some...not sure

---

