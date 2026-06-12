---
title: "Problems with gnome-screensaver"
date: 2009-02-10
forum: Multimedia Software
---

### Post by Pitboss on 2009-02-10
Hi. After I installed the new Catalyst 9.1 drivers although the first seemingly better graphical performance with compiz now I experience some strange problems. Ubuntu totally crashed several times while I was trying to change my screensaver last night. First I thought that this was just a coincidence, but today I tried to play a movie with mplayer, and it started very slowly. When I ran it in the terminal I had to type ctrl + c two times in order for it to get running. And the problems seems to be with the screensaver or something. I can't tell because I'm new to linux. Here is the code after running mplayer, hope someone can help.

```

pitboss@swamp:~/railscasts$ gmplayer 084_cookie_based_session_store.mov 
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 5400+ (Family: 15, Model: 107, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
^C/home/pitboss/.fonts/arial.ttf doesn't look like a bitmap font description, ignoring.
Cannot load bitmap font: /home/pitboss/.fonts/arial.ttf
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/pitboss/railscasts/084_cookie_based_session_store.mov.
ISO: File Type Major Brand: Original QuickTime
Quicktime/MOV file format detected.
[mov] Audio stream found, -aid 0
[mov] Video stream found, -vid 1
VIDEO:  [rle ]  800x600  24bpp  3.746 fps    0.0 kbps ( 0.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffqtrle] vfm: ffmpeg (QuickTime Animation (RLE))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
AUDIO: 44100 Hz, 2 ch, s16le, 96.0 kbit/6.80% (ratio: 12000->176400)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio) decoder)
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 800 x 600 (preferred colorspace: RGB 24-bit)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using RGB 24-bit as output csp (no 1)
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0x89652b0]SwScaler: using unscaled rgb24 -> rgb32 special converter
VO: [x11] 800x600 => 800x600 BGRA  [zoom]
No bind found for key ''.                         3%  3%  0.9% 0 0              
GNOME screensaver enabled.078 ct:  0.018  12/ 12  1%  2%  0.6% 0 0              

Exiting... (Quit)

```

The only way I figured of getting around this was turning the "stop screensaver" option in gmplayer off. But then I should turn the screensaver off manually every time I play something. I'll appreciate any advice.

---

### Post by Pitboss on 2009-02-11
Interestingly enough if I kill the gnome-screensaver the problem persists. Mplayer crashes after this message:

```
pitboss@swamp:~/railscasts$ mplayer 084_cookie_based_session_store.mov 
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 5400+ (Family: 15, Model: 107, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing 084_cookie_based_session_store.mov.
ISO: File Type Major Brand: Original QuickTime
Quicktime/MOV file format detected.
[mov] Audio stream found, -aid 0
[mov] Video stream found, -vid 1
VIDEO:  [rle ]  800x600  24bpp  3.746 fps    0.0 kbps ( 0.0 kbyte/s)
**xscreensaver_disable: Could not find XScreenSaver window.**

```

And I have to type ctrl+c for it to run normally.

---

### Post by Pitboss on 2009-02-11
I finally managed to resolve the problem. If anybody has the same problem here is how I did it. Previously I was installing the mplayer from repository and the problem stayed, and now I just got and built one from the svn.

```

sudo apt-get remove --purge mplayer
svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
./configure 
make
make install

```

Of course most of you will know this, I'm just a newbie but I'm writing this if somebody like me falls in the same trap. Well now I have some trouble with the config but at least I have a working mplayer. :)

---

### Post by andrew.46 on 2009-02-11
Hi Pitboss,

> **Pitboss said:**
> I finally managed to resolve the problem. If anybody has the same problem here is how I did it. Previously I was installing the mplayer from repository and the problem stayed, and now I just got and built one from the svn.

Good to see you have fixed your own problem, this is usually a sign that you will do well in Linux :-).

Ubuntu is not a particularly great environment for compiling and I suspect that the MPlayer you have compiled may be lacking in a few features because of this. There is a guide for [compiling a fuller svn MPlayer]("http://ubuntuforums.org/showthread.php?t=1024592") on these forums which might allow you to have fuller functionality.

Andrew

---

