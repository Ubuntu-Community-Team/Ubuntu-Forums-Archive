---
title: "[SOLVED] convert rmvb's linux"
date: 2008-12-24
forum: Multimedia Software
---

### Post by Xombie207 on 2008-12-24
Does anyone know of a linux program that can convert rmvb files to...anything?; does anyone know of a wine supported windows program that can?

---

### Post by tech0007 on 2008-12-25
Mencoder can convert rmvb to avi.  From avi, you can convert it to almost any format:

```

sudo apt-get update
sudo apt-get install mencoder
mencoder input.rmvb -oac mp3lame -lameopts preset=128 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1200 -ofps 25 -of avi -o output.avi

```

---

### Post by Xombie207 on 2008-12-28
Thank you for your help...now I can erase windows and just run ubuntu.

---

### Post by belerophonte on 2009-01-10
Sorry, but you can watch rmvb's on linux. =)

---

### Post by etereo on 2009-01-14
> **belerophonte said:**
> Sorry, but you can watch rmvb's on linux. =)

With what program?  I've tried to play a movie with Totem to no avail.

Also I tried the command listed in the previous post, but it gives the following error:

MEncoder 2:1.0~rc2-0ubuntu17 (C) 2000-2007 MPlayer Team
CPU: AMD Turion(tm) 64 X2 TL-62 (Family: 15, Model: 104, Stepping: 2)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x15947bad
REAL file format detected.
Stream description: Audio Stream
Stream mimetype: audio/x-pn-realaudio
[real] Audio stream found, -aid 0
Stream description: Video Stream
Stream mimetype: video/x-pn-realvideo
[real] Video stream found, -vid 1
Stream mimetype: logical-fileinfo
VIDEO:  [RV40]  512x240  24bpp  23.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:11  fourcc:0x30345652  size:512x240  fps:23.00  ftime:=0.0435
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 64.1 kbit/4.54% (ratio: 8010->176400)
Selected audio codec: [ffcook] afm: ffmpeg (FFmpeg COOK audio decoder)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [realvid] RealVideo decoder
Error: /usr/lib/codecs/drvc.so: cannot open shared object file: No such file or directory
Win32 LoadLibrary failed to load: drvc.so, /usr/lib/win32/drvc.so, /usr/local/lib/win32/drvc.so
Error loading dll
ERROR: Could not open required DirectShow codec drvc.so.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Opening video decoder: [realvid] RealVideo decoder
Win32 LoadLibrary failed to load: drvc.dll, /usr/lib/win32/drvc.dll, /usr/local/lib/win32/drvc.dll
Error loading dll
ERROR: Could not open required DirectShow codec drvc.dll.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Opening video decoder: [realvid] RealVideo decoder
Error: /usr/lib/codecs/drv4.so.6.0: cannot open shared object file: No such file or directory
Win32 LoadLibrary failed to load: drv4.so.6.0, /usr/lib/win32/drv4.so.6.0, /usr/local/lib/win32/drv4.so.6.0
Error loading dll
ERROR: Could not open required DirectShow codec drv4.so.6.0.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Opening video decoder: [realvid] RealVideo decoder
Win32 LoadLibrary failed to load: drv43260.dll, /usr/lib/win32/drv43260.dll, /usr/local/lib/win32/drv43260.dll
Error loading dll
ERROR: Could not open required DirectShow codec drv43260.dll.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Opening video decoder: [realvid] RealVideo decoder
Error: /usr/lib/codecs/drvc.bundle/Contents/MacOS/drvc: cannot open shared object file: No such file or directory
Win32 LoadLibrary failed to load: drvc.bundle/Contents/MacOS/drvc, /usr/lib/win32/drvc.bundle/Contents/MacOS/drvc, /usr/local/lib/win32/drvc.bundle/Contents/MacOS/drvc
Error loading dll
ERROR: Could not open required DirectShow codec drvc.bundle/Contents/MacOS/drvc.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x30345652.
Read DOCS/HTML/en/codecs.html!
==========================================================================

Exiting...

---

### Post by andrew.46 on 2009-01-15
Hi etereo,

> **etereo said:**
> With what program?  I've tried to play a movie with Totem to no avail.

The svn MPlayer will certainly play such files. I used a [sample file on the MPlayer samples site]("http://samples.mplayerhq.hu/real/AC-cook/cook_5.1/hotel_california_ra5.1_640x480_30s.rmvb") and played it as follows with MPlayer:

```

andrew@skamandros~/Desktop$ [B][COLOR="Red"]mplayer -vc rv40 -ac ra10cook \
> hotel_california_ra5.1_640x480_30s.rmvb[/COLOR][/B]
MPlayer dev-SVN-r28288-4.2.4 (C) 2000-2009 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz (Family: 6, Model: 15, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

Playing hotel_california_ra5.1_640x480_30s.rmvb.
REAL file format detected.
Stream description: Video Stream
Stream mimetype: video/x-pn-realvideo
[real] Video stream found, -vid 0
Stream description: Audio Stream
Stream mimetype: audio/x-pn-realaudio
[real] Audio stream found, -aid 1
Stream mimetype: logical-fileinfo
VIDEO:  [RV40]  640x480  24bpp  30.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Forced video codec: rv40
Opening video decoder: [realvid] RealVideo decoder
**[COLOR="Red"]Selected video codec: [rv40] vfm: realvid (Linux RealPlayer 9 RV40 decoder)[/COLOR]**
==========================================================================
==========================================================================
Forced audio codec: ra10cook
Opening audio decoder: [realaud] RealAudio decoder
AUDIO: 44100 Hz, 6 ch, s16le, 183.3 kbit/4.33% (ratio: 22911->529200)
**[COLOR="Red"]Selected audio codec: [ra10cook] afm: realaud (RealPlayer 10 COOK audio)[/COLOR]**
==========================================================================
AO: [oss] 44100Hz 6ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 640 x 480 (preferred colorspace: Planar I420)
VDec: using Planar I420 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 640x480 => 640x480 Planar I420 
A:  29.9 V:  29.9 A-V:  0.003 ct:  0.006 899/899 19%  2%  2.9% 0 0 

Exiting... (End of file)

```

I manually selected the audio and video codecs as by default MPlayer does a bit of searching with this particular file to find the appropriate ones :-). Beautiful quality on that snippet of video by the way...

Andrew

---

### Post by tricolorpoa on 2009-07-15
Try to install media ubuntu repositories

[http://www.linuxparatodos.com.br/artigos/tutorial-multimedia-ubuntu-intrepid-ibex-810](http://www.linuxparatodos.com.br/artigos/tutorial-multimedia-ubuntu-intrepid-ibex-810)

:p

---

### Post by dank91 on 2009-08-07
google Real Player linux

---

