---
title: "How do I send a program to tv-out?"
date: 2008-12-13
forum: Multimedia Software
---

### Post by graabein on 2008-12-13
I have tv-out going on my nVidia GeForce 6600 GT. How do I send vlc and a video file to screen 1 (monitor is screen 0) from the command line? I know it's DISPLAY something but I can't figure it out. Help would be appreciated!


**Update:** More info:
```
$ DISPLAY=0.1 mplayer Louis\ Armstrong\ -\ St.\ James\ Infirmary.flv 
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.00GHz (Family: 15, Model: 2, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Louis Armstrong - St. James Infirmary.flv.
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [FLV1]  320x240  0bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
vo: couldn't open the X11 display (0.1)!
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 22050 Hz, 1 ch, s16le, 64.0 kbit/18.14% (ratio: 8000->44100)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
E: client-conf-x11.c: XOpenDisplay() failed
AO: [pulse] 22050Hz 1ch s16le (2 bytes per sample)
Video: no video
Starting playback...
```

Can't get **VLC** to show fullscreen on screen 1 either. Video output module is set to *XVideo extension video output*.

---

### Post by graabein on 2009-01-17
Still can't get vlc to show fullscreen on screen1 while playing a movie on screen0. 

I did figure out how to start vlc on screen1 though:

```
DISPLAY=:0.1; vlc
```

If I can write a script with the movie as input parameter and a switch to go fullscreen that would be about the same thing...

---

### Post by stderr on 2009-01-17
The fullscreen switch is -f, and you just pass the file as you did to mplayer

DISPLAY=:0.1; vlc -f /path/to/movie

any good?

---

### Post by graabein on 2009-02-03
Thanks, I've managed to write a bash script and put it in the script folder for GNOME. Now I can right click a movie and run it on screen1 in fullscreen :D

> #!/bin/bash
DISPLAY=:0.1; vlc "$1" --fullscreen

---

