---
title: "Could not determine type of stream"
date: 2009-05-10
forum: Multimedia Software
---

### Post by xova02 on 2009-05-10
Hello!

I have this problem with video playback in Ubuntu 9.04. Container is mp4 and when I open it in Movie Player, I get error message "Could not determine type of stream". The file would not play either in VLC or Mplayer. Strange thing is that yesterday, when I downloaded the file, it was working without a problem, therefore the file is not corrupted.

As I am new to Linux, there might had been some changes between yesterday and present time, because I am eager to discover the possibilities of new system and so trying to install various packages etc.

I tried to play the file with mplayer in Terminal and got this:

xova02@xova02:~$ mplayer /home/xova02/Desktop/Scarface.mp4
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz (Family: 6, Model: 23, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/xova02/Desktop/Scarface.mp4.
RAWDV file format detected.
VIDEO:  [DVSD]  720x480  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [dshow] DirectShow video codecs
Win32 LoadLibrary failed to load: qdv.dll, /usr/lib/win32/qdv.dll, /usr/local/lib/win32/qdv.dll
Warning: DS_Filter() could not open DirectShow DLL.  (DLL=qdv.dll, r=0xa9daf50)
Failed to create DirectShow filter
ERROR: Could not open required DirectShow codec qdv.dll.
You need to upgrade/install the binary codecs package.
Go to [http://www.mplayerhq.hu/dload.html](http://www.mplayerhq.hu/dload.html)
VDecoder init failed :(
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffdv] vfm: ffmpeg (FFmpeg DV decoder)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libdv] Raw DV Audio Decoder
Unknown/missing audio format -> no sound
ADecoder init failed :(
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
Cannot find codec 'dvaudio' in libavcodec...
ADecoder init failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x56444152.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar 411P)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar 411P as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 5 -> 4
SwScaler: reducing / aligning filtersize 1 -> 1
SwScaler: reducing / aligning filtersize 9 -> 8
[swscaler @ 0x896d350]SwScaler: BICUBIC scaler, from yuv411p to yuv420p using MMX2
[swscaler @ 0x896d350]SwScaler: using 4-tap MMX scaler for horizontal luminance scaling
[swscaler @ 0x896d350]SwScaler: using 4-tap MMX scaler for horizontal chrominance scaling
[swscaler @ 0x896d350]SwScaler: using 1-tap MMX "scaler" for vertical scaling (YV12 like)
[swscaler @ 0x896d350]SwScaler: 720x480 -> 720x480
VO: [xv] 720x480 => 720x480 Planar YV12 
V:   0.0   2/  2 ??% ??% ??,?% 0 0 
  =====  PAUSE  =====


Maybe it could offer some information about the problem. All other media types (H264 videos included) play with no problem.

Thank you for any suggestion and my apologize if this problem had been already solved somewhere else, I did some search but not found reasonable answer.

Xova

---

### Post by andrew.46 on 2009-05-11
Hi xona02,

> **xova02 said:**
> 

```
Opening video decoder: [dshow] DirectShow video codecs
Win32 LoadLibrary failed to load: qdv.dll, /usr/lib/win32/qdv.dll, /usr/local/lib/win32/qdv.dll
Warning: DS_Filter() could not open DirectShow DLL.  (DLL=qdv.dll, r=0xa9daf50)
Failed to create DirectShow filter
**[COLOR="Red"]ERROR: Could not open required DirectShow codec qdv.dll.[/COLOR]**
You need to upgrade/install the binary codecs package.
Go to [http://www.mplayerhq.hu/dload.html](http://www.mplayerhq.hu/dload.html)
VDecoder init failed :(
```

You are missing the required codec qdv.dll. Good news is that this can be picked up from the Medibuntu repository as part of the w32codec pack. 

> ```
Opening audio decoder: [libdv] Raw DV Audio Decoder
Unknown/missing audio format -> no sound
ADecoder init failed :(
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
**[COLOR="Red"]Cannot find codec 'dvaudio' in libavcodec...[/COLOR]**
ADecoder init failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x56444152.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
```

Looks like your copy of MPlayer is not compiled against libdv4, although I am not completely sure if this is the answer here. I note however that the Medibuntu MPlayer* is *compiled against this library and this should be well worth a try.

All the best,

Andrew

---

### Post by xova02 on 2009-05-11
Well, I did as you suggested and now everything works. Thank you for your help!

---

### Post by andrew.46 on 2009-05-12
Hi xona02,

> **xova02 said:**
> Well, I did as you suggested and now everything works. Thank you for your help!

Excellent news!! This version should serve you well but if you ever wish to get a little deeper into this amazing program you could have a look at 2 guides I have written:

HowTo: Install the very latest MPlayer under Jaunty Jackalope
[http://ubuntuforums.org/showthread.php?t=1081070](http://ubuntuforums.org/showthread.php?t=1081070)

Top 10 Tricks and Tips for the svn MPlayer
[http://ubuntuforums.org/showthread.php?t=1154431](http://ubuntuforums.org/showthread.php?t=1154431)

But the version you have now may very well be enough as it is.

All the best,

Andrew

---

### Post by afrodeity on 2011-02-04
any ideas about flac with same error message in totem?

---

