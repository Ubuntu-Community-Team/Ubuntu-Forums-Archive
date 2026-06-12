---
title: "MPlayer &amp; flv"
date: 2006-12-12
forum: Multimedia &amp; Video
---

### Post by Decoy on 2006-12-12
*Hi everyone,*

  What should I install to make mplayer play flash movies? **Instead of sound I can hear only noise...** :(

```
$ mplayer test-speech.flv
MPlayer 1.0rc1-3.4.6 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Celeron(R) CPU 2.40GHz (Family: 15, Model: 3, Stepping: 3)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing test-speech.flv.
libavformat file format detected.
[flv @ 0x8641fe0]Unsupported audio codec (6)
==========================================================================
Opening audio decoder: [alaw] aLaw/uLaw audio decoder
AUDIO: 44100 Hz, 1 ch, s16le, 352.8 kbit/50.00% (ratio: 44100->88200)
Selected audio codec: [alaw] afm: alaw (aLaw)
==========================================================================
AO: [alsa] 48000Hz 1ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A: 113.9 (01:53.8) of 114.2 (01:54.2)  0.7%

Exiting... (End of file)
```
By the way, there's no video stream in test-speech.flv, only audio...

---

### Post by dolphinholmer on 2006-12-12
Not sure, but have you tried the new Flash Player 9 beta for linux?
[http://labs.adobe.com/downloads/flashplayer9.html](http://labs.adobe.com/downloads/flashplayer9.html)

---

### Post by Decoy on 2006-12-12
Flash Player is OK, I'd like to play flv-files with mplayer...

---

