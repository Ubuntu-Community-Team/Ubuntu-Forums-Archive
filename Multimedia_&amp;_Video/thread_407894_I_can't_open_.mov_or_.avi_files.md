---
title: "I can't open .mov or .avi files"
date: 2007-04-12
forum: Multimedia &amp; Video
---

### Post by Xshady on 2007-04-12
Hello,


I have a lot of .mov and .avi videos that i'd like to watch on my ubuntu dapper, but every time I try to open one with mplayer or vlc it window closes after one seconde, 
I have instralled the w32codecs but it dose'nt work, here the error message that I get with mplayer :

MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium 4/Celeron 4 Northwood; Pentium 4 EE/Xeon Prestonia,Gallatin (Family: 15, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing test.mov.
Quicktime/MOV file format detected.
Compressed header uses zlib algo!
Compressed header size: 8612 / 17660
--------------
MOV track #0: 1246 chunks, 1246 samples
MOV: Found MPEG4 movie Elementary Stream Descriptor atom (86)!
Image size: 800 x 600 (32 bpp)
Display size: 800 x 600
Fourcc: mp4v  Codec: '3ivx D4 4.5.1 Pro'
--------------
MOV track #1: 831 chunks, 0 samples
Audio bits: 16  chans: 1  rate: 22050
Audio extra header: len=76  fcc=0x77617665
MOV: Found unknown audio atom &#65533;Fourcc: ms
--------------
MOV: longest streams: A: #1 (831 samples)  V: #0 (1246 samples)
VIDEO:  [mp4v]  800x600  32bpp  3.000 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
name: test
author: test
copyright: 1996-2004
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 22050 Hz, 2 ch, s16le, 32.0 kbit/4.54% (ratio: 4000->88200)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
Building audio filter chain for 22050Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 22050 Hz/2 channels/4 bpf/30104 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 22050Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 22050Hz/2ch/s16le -> 22050Hz/2ch/s16le...
Starting playback...
VDec: vo config request - 800 x 600 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 800x600 => 800x600 Planar YV12
alsa-space: xrun of at least 4.743 msecs. resetting stream?,?% 0 0
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0


MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
alsa-uninit: pcm close

thanks for your help.

---

### Post by goghgoner on 2007-04-12
Many times I need to reboot for VLC to work properly.

---

### Post by stefangr1 on 2007-04-13
One thing you could do is install Automatix, and use that to automatically install the commercial and the most often used codec packages. After that the programs might work.

---

### Post by Xshady on 2007-04-13
Hello ,

Thanx goghgoner and stefangr1 for your replies, I installed Automatix and downloaded all the codecs that I've found in there even though I already had some of them, but the problem still persist, and when I try opening any .avi or .mov file the player closes suddenly after one second,
it's really frustrating not being able to to watch them , I'm forced to use windows every time I want to , so please if someone could help me, I'm desperate :( ...

---

### Post by bashologist on 2007-04-13
I don't know if this will work, but since you're desperate, maybe you would wanna try it.

sudo apt-get install --reinstall mplayer

if which mplayer; then cd /tmp; if wget [noparse]http://www1.mplayerhq.hu/MPlayer/releases/codecs/all-20061022.tar.bz2[/noparse]; then tar -xvjf all-20061022.tar.bz2; sudo mkdir /usr/lib/win32; sudo mv all-20061022/* /usr/lib/win32/; fi; else echo "install mplayer first"; fi

#Then try different video codecs:
mplayer -vo xmga /data/more/beryl_vidcap.avi
mplayer -vo xv /data/more/beryl_vidcap.avi
mplayer -vo help

---

### Post by Xshady on 2007-04-14
Hi, 

I did what your told me bashologist, but it does'nt work,  well I guess I just have to keep looking  maybe one day a miracle will happen and I'll be able to watch any video under ubuntu

---

