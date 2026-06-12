---
title: "how to compile mplayer?"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by adameye on 2007-05-07
my mplayer has problem and can not play anything, I followed the steps on [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs)
however, still have problem.
I searched online [http://lists.mplayerhq.hu/pipermail/mplayer-users/2006-November/064112.html](http://lists.mplayerhq.hu/pipermail/mplayer-users/2006-November/064112.html)
they said it is necessary for the people who compiled mplayer to have the
codecs in the proper directory and include those codecs with the
package. [COLOR="Red"]**but how to complie mplayer? I only know sudo ***^_^**[/COLOR]


when I use [COLOR="Red"]**gmplayer -vo x11**[/COLOR]
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Genuine Intel(R) CPU           T2080  @ 1.73GHz (Family: 6, Model: 14, Stepping: 12)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.


[COLOR="Red"]**when I open one rmvb file:**[/COLOR]
REAL file format detected.
Stream description: Audio Stream
Stream mimetype: audio/x-pn-realaudio
Stream description: Video Stream
Stream mimetype: video/x-pn-realvideo
Stream mimetype: logical-fileinfo
VIDEO:  [RV40]  640x352  24bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 name: &#65533;&#65533;5&#65533;&#65533;DVD &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#315;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#1444; [&#65533;&#65533;&#65533;&#1460;&#56223;&#56633;&#65533;].Open.Season.2006
 author: &#65533;&#65533;&#1264;&#65533;&#1269;&#1785;&#65533;CNXP&#65533;
 copyright: [www.cnxp.com(C)2006](www.cnxp.com(C)2006)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
Xv: could not grab port 65
Could not find free Xvideo port - maybe another process is already using it.
Close all video applications, and try again. If that does not help,
see 'mplayer -vo help' for other (non-xv) video out drivers.
==========================================================================
Opening video decoder: [realvid] RealVideo decoder
Error: /usr/lib/win32/drvc.so: cannot open shared object file: No such file or directory
Win32 LoadLibrary failed to load: drvc.so, /usr/lib/win32/drvc.so, /usr/local/lib/win32/drvc.so
Error loading dll
ERROR: Could not open required DirectShow codec drvc.so.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Opening video decoder: [realvid] RealVideo decoder
Error: /usr/lib/win32/drv4.so.6.0: cannot open shared object file: No such file or directory
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
Error: /usr/lib/win32/drvc.bundle/Contents/MacOS/drvc: cannot open shared object file: No such file or directory
Win32 LoadLibrary failed to load: drvc.bundle/Contents/MacOS/drvc, /usr/lib/win32/drvc.bundle/Contents/MacOS/drvc, /usr/local/lib/win32/drvc.bundle/Contents/MacOS/drvc
Error loading dll
ERROR: Could not open required DirectShow codec drvc.bundle/Contents/MacOS/drvc.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x30345652.
Read DOCS/HTML/en/codecs.html!
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 64.1 kbit/4.54% (ratio: 8010->176400)
Selected audio codec: [ffcook] afm: ffmpeg (FFmpeg COOK audio decoder)
==========================================================================
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
[AO ESD] esd_open_sound failed: Connection reset by peer
[AO OSS] audio_setup: Can't open audio device /dev/dsp: No such file or directory
alsa-lib: pcm_hw.c:1242:(snd_pcm_hw_open) open /dev/snd/pcmC0D0p failed: No such file or directory
alsa-lib: pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
alsa-init: playback open error: No such file or directory
mcop warning: user defined signal handler found for SIG_PIPE, overriding
Link points to "/tmp/ksocket-wyf"
can't create mcop directory

---

### Post by adameye on 2007-05-07
in usr/lib/win32 is empty, so I cp everything from usr/lib/codecs to here,
however..still have problem, I also found the terminal died after the command [COLOR="Red"]mplayer *.rmvb[/COLOR]..

---

