---
title: "How to play APE ?"
date: 2007-01-22
forum: Multimedia &amp; Video
---

### Post by Physicist on 2007-01-22
What is the best analogue of Foobar 2000 in linux?

---

### Post by crispy_420 on 2007-01-23
have you tried rhythmbox? or banshee?

---

### Post by Magnes on 2007-01-23
Amarok is the best analogue of Foobar2000, it's several times better also. But it wouldn't play APE. The best way to deal with it is to convert all your APE files to FLAC with gnormalize. Very few apps can play APE at all (some old versions of Amarok and XMMS). There were threads about it on this forum, so use "search" function.

---

### Post by geminifire on 2007-01-31
1.check your repositories

2.install beep-media-player and plug-in
sudo apt-get install beep-media-player totem-xine w32codecs libxine-extracodecs
sudo apt-get install mac
sudo apt-get install bmp-mac

3.play .ape with beep-media-player

Have fun!

---

### Post by maddbaron on 2007-02-03
when i tried entering install mac and bmp-mac is said it cannot find it. what repo are you using please?

---

### Post by ajm2005 on 2007-02-05
> **maddbaron said:**
> when i tried entering install mac and bmp-mac is said it cannot find it. what repo are you using please?

mac isn't available in the ubuntu repositories

---

### Post by Physicist on 2008-05-04
One can play .ape files by mplayer.
```

$ mplayer file.ape

``` 
would do.


```

$ mplayer *.ape
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) D CPU 2.80GHz (Family: 15, Model: 4, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing cdimage.ape.
libavformat file format detected.
Invalid APE Tags
[lavf] Audio stream found, -aid 0
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 0.0 kbit/0.00% (ratio: 0->176400)
Selected audio codec: [ffape] afm: ffmpeg (FFmpeg Monkey's Audio decoder)
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:3356.9 (55:56.8) of 3357.4 (55:57.4)  3.3% 

Exiting... (End of file)


```
I am wondering if mplayer has a GUI.

---

