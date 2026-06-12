---
title: "mplayer playback problems"
date: 2009-07-21
forum: Multimedia Software
---

### Post by erinspice on 2009-07-21
I'm having a strange problem with mplayer. When I try to play a video, mplayer starts up just fine. The video window comes up and I can see the first frame of the video, but it never plays. No audio or video. I can fast-forward through the video and see still frames throughout the video, but no matter what I do, there's no sound or video.  Any ideas? Rebooting used to fix this problem for me in 8.10, but now I'm using 9.04 and rebooting doesn't help.  Here's mplayer's output:

```
erin@erinlaptop:~/lost-season-5$ mplayer lost.0512.hdtv.xvid-notv.avi 
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: AMD Turion(tm) 64 X2 Mobile Technology TL-50 (Family: 15, Model: 72, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing lost.0512.hdtv.xvid-notv.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  624x352  24bpp  23.976 fps  1037.4 kbps (126.6 kbyte/s)
Clip info:
 Software: transcode-1.0.2
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 64.0 kbit/4.17% (ratio: 8000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 624 x 352 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.77:1 - prescaling to correct movie aspect.
VO: [xv] 624x352 => 624x352 Planar YV12 
No bind found for key 'MOUSE_BTN0'.                         ?% 0 0 
A:  10.9 V:  11.2 A-V: -0.306 ct: -0.026 270/270 ??% ??% ??,?% 0 0 
A:  10.9 V:  11.2 A-V: -0.306 ct: -0.026 270/270 ??% ??% ??,?% 0 0 
No bind found for key 'MOUSE_BTN0'.                         
No bind found for key 'MOUSE_BTN0'.                         
No bind found for key 'MOUSE_BTN0'.                         
A:  10.9 V:  11.2 A-V: -0.306 ct: -0.026 270/270 ??% ??% ??,?% 0 0 
GNOME screensaver enabled.306 ct: -0.026 824/824 ??% ??% ??,?% 0 0 

Exiting... (Quit)
erin@erinlaptop:~/lost-season-5$ 

```

---

### Post by igorzwx on 2009-07-21
why not "make Ubuntu 9.04 multimedia ready"?
google will help

---

### Post by erinspice on 2009-07-21
> **igorzwx said:**
> why not "make Ubuntu 9.04 multimedia ready"?

I'm not sure what this means.

I have googled this, but the keywords are so generic that huge numbers of unrelated problems show up in the search results.

ETA: I am following some instructions now that I found by googling that phrase.

ETAA: No changes. Installing additional non-free codecs did not fix my problem.

---

### Post by igorzwx on 2009-07-21
You are a developer. right?
so the meaning of the comands should no be a problem
[http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html](http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html)

---

### Post by erinspice on 2009-07-21
As stated in my last post, I already did that. Thanks, though. Any other ideas?

---

### Post by igorzwx on 2009-07-21
Does it work with VLC?

---

### Post by erinspice on 2009-07-21
Yes, it does.

---

### Post by igorzwx on 2009-07-21
Are content with sound?
Have you tried Ekiga and Skype?
Have you tried to record something?

---

### Post by erinspice on 2009-07-21
It was a sound problem. Restarting alsa fixed it. Thanks!

---

### Post by igorzwx on 2009-07-21
Do you mean that your sound system is broken?
Or incorrect settings of Mplayer?
Or System -> preferences -> sound

---

### Post by erinspice on 2009-07-21
> **igorzwx said:**
> Do you mean that your sound system is broken?
Not anymore.

---

