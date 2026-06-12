---
title: "Gutsy Mplayer No XV or Alsa"
date: 2007-10-19
forum: Multimedia &amp; Video
---

### Post by cor2y on 2007-10-19
First it was a regular upgrade using the download repos.
When that broke/uninstalled a lot of things i opted for a clean install.
So far nothing on this system has been custom compiled or even used the dreaded automatix.
Instead all of the addons and install came via synapttic.
However Mplayer my media player of choice is refusing to run any videos in XV or with alsa audio although i see for myself via synaptic and using apt-get
that the required files are already installed.
A quick check 
 ```

xvinfo
X-Video Extension version 2.2
screen #0
 no adaptors present

```Reveled for some reason my video card is not being detected as having xv (ATI X850XT) so i removed compiz and installed the closed drivers
```

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON X850 XT
OpenGL version string: 2.0.6473 (8.37.6)

```
Yet trying to play a video in mplayer from the desktop or terminal gives these errors
```

mplayer pool.avi
MPlayer 2:1.0~rc1-0ubuntu13 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) XP 2800+ (Family: 6, Model: 10, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing 060912_pool.avi.
AVI file format detected.
VIDEO:  [XVID]  1280x720  12bpp  29.970 fps  2788.1 kbps (340.3 kbyte/s)
It seems there is no Xvideo support for your video card available.
Run 'xvinfo' to verify its Xv support and read DOCS/HTML/en/video.html#xv!
See 'mplayer -vo help' for other (non-xv) video out drivers. Try -vo x11
Error opening/initializing the selected video_out (-vo) device.


Exiting... (End of file)

```Only using x11 is there any playback but i lack alsa playback as well when using x11
```

mplayer -vo x11 pool.avi
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
alsa-lib: confmisc.c:1286:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix.device'
alsa-lib: conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
alsa-lib: conf.c:3982:(snd_config_expand) Evaluate error: No such file or directory
alsa-lib: pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
```
So what could be causing this is it bad config settings somewhere?

---

### Post by mbradlcu on 2007-10-25
I'm seeing the same issue with 710 but while running ETQW.. hope we get a fix soon

---

