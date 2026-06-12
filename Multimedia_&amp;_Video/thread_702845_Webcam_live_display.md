---
title: "Webcam live display?"
date: 2008-02-20
forum: Multimedia &amp; Video
---

### Post by Ianallan on 2008-02-20
Im currently using the command

> mencoder tv:// -tv driver=v4l:width=320:height=240:device=/dev/video0:forceaudio:adevice=/dev/dsp1 -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o webcam.avi

to record my webcam video and sound to an avi

is there anyway i can concurrently watch what the webcam is recording?

programs like canorama wont open since the webcam is already in use,

thanks,
ian

---

### Post by FrankVdb on 2008-02-21
Cheese.

It's in the repos.

---

### Post by sisco311 on 2008-02-21
Hi

>  mencoder tv:// -tv driver=v4l:width=320:height=240:device=/dev/video0 :forceaudio:adevice=/dev/dsp1 -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o >( tee webcam.avi | mplayer - )will do the trick.

---

### Post by Ianallan on 2008-02-21
Sisco: that worked for awhile but now I sometime get this,

> MEncoder 2:1.0~rc2-0ubuntu1~gutsy1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing -.
Reading from stdin...
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l
 name: Video 4 Linux input
 author: Alex Beregszaszi
 comment: under development
unable to open '/dev/video0': No such device
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

Exiting...
ian@Mainframe:~$ Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll


Exiting... (End of file)

ian@Mainframe:~$ 

I can only seem to fix this by restarting...

as well the avi files it outputs are no longer playing the sound (im not sure if this might not be related to other sound problems im having and have nothing to do with this)

Thanks for your help

---

