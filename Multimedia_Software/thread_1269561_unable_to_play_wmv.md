---
title: "unable to play wmv"
date: 2009-09-18
forum: Multimedia Software
---

### Post by DarkDancer on 2009-09-18
I;m at a friends house and he has a video he would like to play. It's a .wmv, I can play it at home on my Ubuntu box but when he tries, movie player comes up sits there for a moment acts like it's about to play, then closes. Is this some sort of codec issue or something else?

---

### Post by Lampi on 2009-09-18
You miss w32codecs - you get them from the Medibuntu repository:

```
~$ apt-cache policy w32codecs
w32codecs:
  c: 20071007-0medibuntu4
  candidate: 20071007-0medibuntu4
  version:
 *** 20071007-0medibuntu4 0
        500 http://packages.medibuntu.org jaunty/non-free Packages
        100 /var/lib/dpkg/status
```

---

### Post by DarkDancer on 2009-09-18
Thanks! That helped, I actually already ha the w32, but needed the nonfree, they came up when I searched the w32.

---

### Post by DarkDancer on 2009-09-18
Woops, I was wrong. It played 2 times then went back to the old behaviour, any other ideas?

---

### Post by Lampi on 2009-09-18
I'd start the player from a terminal like this:
```
gmplayer videofile.wmv 
```
now you should see what is going wrong

---

### Post by blur xc on 2009-09-18
have you tried vlc player?  

BM

---

### Post by DarkDancer on 2009-09-18
vlc has the same behaviour. If I try the command line it says that it failed to open. If I then dismiss that error and drag the file onto the player, it closes. And yes I am in the same directory when I try the command line and I did substitute the actual name of the file (and checked for typos).

---

### Post by DarkDancer on 2009-09-18
Whoops, wasn't in the right directory changed to it and tried again, no errors, it just opened then closed.

---

### Post by DarkDancer on 2009-09-18
Oh wait, I see, duh! ;)

Here's what the terminal said:

MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(R) CPU 2.53GHz (Family: 15, Model: 4, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/joe/Desktop/ThisIsDancingbcm.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WMV3]  640x480  24bpp  1000.000 fps  340.0 kbps (41.5 kbyte/s)
Clip info:
 name: 
 author: 
 copyright: 
 comments: 
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
GetOutput r=0x0   size:921600  align:1
StreamCount r=0x0  1  1
Decoder supports the following formats: YV12 YUY2 UYVY YVYU RGB8 RGB555 RGB565 RGB24 RGB32 
Decoder is capable of YUV output (flags 0x1b)
VDec: vo config request - 640 x 480 (preferred colorspace: Packed YUY2)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 640x480 => 640x480 Planar YV12 
Selected video codec: [wmv9dmo] vfm: dmo (Windows Media Video 9 DMO)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 64.0 kbit/4.54% (ratio: 8005->176400)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
[ws] Error in display.
[ws]  Error code: 11 ( BadAlloc (insufficient resources for operation) )
[ws]  Request code: 132
[ws]  Minor code: 19
[ws]  Modules: flip_page

---

### Post by andrew.46 on 2009-09-18
Hi DarkDancer,

Try the following:

```
mplayer -vo x11 /home/joe/Desktop/ThisIsDancingbcm.wmv
```

Andrew

---

### Post by DarkDancer on 2009-12-03
Sorry it took so long to get back...that works great.....andrew.46

---

