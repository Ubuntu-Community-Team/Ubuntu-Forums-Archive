---
title: "Garbled video in ubuntu for mkv.... New to all this"
date: 2010-11-04
forum: Multimedia Software
---

### Post by TravisFo on 2010-11-04
So I have tried a couple other things i read in threads and just cannot get this choppy mkv to play correctly


travisfo@travisfo-Satellite-M35:~$ mplayer -v Dexter.S05E06.720p.HDTV.X264-DIMENSION.mkv
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
CPU vendor name: GenuineIntel  max cpuid level: 2
CPU: Intel(R) Pentium(R) M processor 1400MHz (Family: 6, Model: 9, Stepping: 5)
extended cpuid-level: 4
Detected cache-line size is 64 bytes
Testing OS support for SSE... yes.
Tests of OS support for SSE passed.
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNowExt: 0 SSE: 1 SSE2: 1 SSSE3: 0
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/travisfo/.mplayer/codecs.conf'
Reading /home/travisfo/.mplayer/codecs.conf: Can't open '/home/travisfo/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --prefix=/usr --confdir=/etc/mplayer --enable-xvmc --enable-menu --disable-arts --enable-largefiles --language=all --disable-libdvdcss-internal --disable-dvdread-internal --disable-libavutil_a --disable-libavcodec_a --disable-libavformat_a --disable-libpostproc_a --disable-libswscale_a --target=i586-linux --enable-runtime-cpudetection --enable-debug --enable-mga --enable-3dfx --enable-tdfxfb --disable-gui
CommandLine: '-v' 'Dexter.S05E06.720p.HDTV.X264-DIMENSION.mkv'
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/travisfo/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/travisfo/.mplayer/input.conf'
Can't open input config file /home/travisfo/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 91 binds
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('Dexter.S05E06.720p.HDTV.X264-DIMENSION.mkv.conf') -> '/home/travisfo/.mplayer/Dexter.S05E06.720p.HDTV.X264-DIMENSION.mkv.conf'

Playing Dexter.S05E06.720p.HDTV.X264-DIMENSION.mkv.
get_path('sub/') -> '/home/travisfo/.mplayer/sub/'
File not found: 'Dexter.S05E06.720p.HDTV.X264-DIMENSION.mkv'
Failed to open Dexter.S05E06.720p.HDTV.X264-DIMENSION.mkv.

vo: x11 uninit called but X11 not initialized..

Exiting... (End of file)
travisfo@travisfo-Satellite-M35:~$ mplayer -vo x11 Dexter.S05E06.720p.HDTV.X264-DIMENSION.mkv
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Dexter.S05E06.720p.HDTV.X264-DIMENSION.mkv.
File not found: 'Dexter.S05E06.720p.HDTV.X264-DIMENSION.mkv'
Failed to open Dexter.S05E06.720p.HDTV.X264-DIMENSION.mkv.


Exiting... (End of file)

---

### Post by cchhrriiss121212 on 2010-11-04
Your cpu is too weak to play 720p video smoothly. Check your system monitor when playing which will likely show 100% usage.
You could try switching to a lighter OS like Lubuntu which runs better on older hardware.

---

### Post by wieman01 on 2010-11-04
CPU performance could be one thing, another solution would be to upgrade your kernel. I had terrible video performance on my Intel mobile chip and they disappeared after I had upgraded.

---

### Post by TravisFo on 2010-11-04
how do I upgrade my kernel ?

---

### Post by Decatf on 2010-11-04
Do not use the X11 video output. It is a pure software renderer without any hardware acceleration. Use xv instead.

Anyways a lighter OS won't magically give your hardware the raw performance needed to decode the video. HD videos just barely play on my 1.7GHz Pentium-M. This is with CoreAVC on Windows XP. That's pretty much the fastest configuration for x264 playback on slow systems.

---

### Post by wieman01 on 2010-11-04
> **TravisFo said:**
> how do I upgrade my kernel ?
See post #28 of this thread:

[http://ubuntuforums.org/showthread.php?t=1595818&page=3]("http://ubuntuforums.org/showthread.php?t=1595818&page=3")

---

