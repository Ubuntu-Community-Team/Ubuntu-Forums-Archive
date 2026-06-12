---
title: "HELP ME! urgent. Mplayer doesnt function"
date: 2008-04-16
forum: Multimedia &amp; Video
---

### Post by ann pic on 2008-04-16
ann@ann-desktop:~$ mplayer /dev/video0
when i run mplayer i got output like this...


MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz (Family: 6, Model: 15, Stepping: 11)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /dev/video0.
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll


Exiting... (End of file)
ann@ann-desktop:~$

---

### Post by ann pic on 2008-04-16
when i run this command: mplayer /dev/vbi0, got screen displayed but do not have any images can be seen

AC EOB marker is absent pos=64
AC EOB marker is absent pos=66
AC EOB marker is absent pos=64
AC EOB marker is absent pos=64
AC EOB marker is absent pos=64
Cannot seek backward in linear streams!
Seek failed
V:   1.5 1447/1447 138%  9%  0.0% 0 0 
gnome_screensaver_control()
Exiting... (End of file)
ann@ann-desktop:~$

---

### Post by ezramorris on 2008-05-21
Try
```
mplayer tv:// -tv driver=v4l:width=640:height=480:device=/dev/video0
```
Replacing /dev/video with your video device

---

### Post by justineve on 2008-05-22
Sorry, friend.
I can't help you I don't have any idea of that.

---

