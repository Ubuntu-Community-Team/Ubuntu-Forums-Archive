---
title: "Win32 LoadLibrary failed to load: vp7vfwLOC.dll, /usr/lib/win32/vp7vfwLOC.dll, /usr/l"
date: 2009-08-15
forum: Multimedia Software
---

### Post by dlublink on 2009-08-15
SOLVED!!

Hey,

I received a video I am trying to play, and I get the following issue :

```

short_video.avi 
MPlayer 1.0rc2-4.2.4 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) M processor 1.60GHz (Family: 6, Model: 13, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing short_video.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [VP70]  576x384  12bpp  23.976 fps  916.9 kbps (111.9 kbyte/s)
Clip info:
 Software: FairUse Wizard - http://fairusewizard.com
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [vfwex] Win32/VfWex video codecs
Loading codec DLL: 'vp7vfw.dll'
Win32 LoadLibrary failed to load: vp7vfwLOC.dll, /usr/lib/win32/vp7vfwLOC.dll, /usr/local/lib/win32/vp7vfwLOC.dll
Loaded DLL driver vp7vfw.dll at 10000000
VDec: vo config request - 576 x 384 (preferred colorspace: Packed YUY2)
[PP] Using codec's postprocessing, max q = 9.
VDec: using Packed YUY2 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 576x384 => 576x384 Packed YUY2 
Selected video codec: [vp7] vfm: vfwex (On2 VP7 Personal Codec)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
A:   0.0 V:   0.2 A-V: -0.166 ct: -0.013   5/  5 ??% ??% ??,?% 0 0 


```

But, 

```

david@david-laptop:/usr/lib/win32$ mplayer -vc help | grep vp7
vp7         vfwex     working   On2 VP7 Personal Codec  [vp7vfw.dll]

```

What's funny, is that when I search for the codec name as mentioned by mplayer, I find two french websites. I wonder if Ubuntu is confusing my computer with a french computer ( french language pack is installed, but not active ) and is trying to find a local file ? LOC sounds like local.

Although I do not hear sound, the sound seems to be properly detected as MP3.

Any ideas why I can't listen to this video ?

Thanks,

David

---

### Post by dlublink on 2009-08-15
I was write, it was a locale problem. I opened up the "Language support" option in System => admin, and it immediately found that there were two locale packs for english missing, it installed and the video immediately played.

So if you have this problem, try opening that menu option, it might solve your problem.

---

### Post by Unright Entity on 2009-10-31
I'm Trying to get Mencoder via acidrip to convert some vp7 files to xvid, and i am getting the exact same error... Mplayer will play the files fine in their current form, while everything else just plays audio. Also, no language setting issues. Any ideas?

---

