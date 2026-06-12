---
title: "Mplayer has stopped working :("
date: 2008-04-13
forum: Multimedia &amp; Video
---

### Post by baz.g on 2008-04-13
for some reason mplayer has suddenly stopped working, i have it set to the default player when i insert a dvd but i have just found that it fails, i tried to run it from terminal and got this:

```
bazgrant@bazgrant-desktop:~$ mplayer dvd://
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4800+ (Family: 15, Model: 107, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://.
There are 5 titles on this DVD.
There are 8 chapters in this DVD title.
There are 1 angles in this DVD title.
audio stream: 0 format: ac3 (5.1) language: en aid: 128.
number of audio channels on disk: 1.
subtitle ( sid ): 0 language: en
number of subtitles on disk: 1
MPEG-PS file format detected.
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  7500.0 kbps (937.5 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.


MPlayer interrupted by signal 11 in module: preinit_libvo
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
```

please help! :D

many thanks in advance,

---

### Post by mc4man on 2008-04-13
You could read here and see if it applies
[http://ubuntuforums.org/showthread.php?t=599453](http://ubuntuforums.org/showthread.php?t=599453)
i've had no issues using self built versions on gutsy or hardy

---

### Post by xc3RnbFO8P on 2008-04-13
Try this in terminal:
>  killall gnome-screensaver
[https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/159861]("https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/159861")
[http://ubuntuforums.org/showthread.php?t=599453]("http://ubuntuforums.org/showthread.php?t=599453")
Great mc4man :)

---

