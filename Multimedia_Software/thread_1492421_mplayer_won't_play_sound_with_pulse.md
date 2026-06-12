---
title: "mplayer won't play sound with pulse"
date: 2010-05-24
forum: Multimedia Software
---

### Post by Rogue Jedi X on 2010-05-24
I'm trying to get mplayer working with pulse. I have "ao=pulse" in my config and I even tried starting it with -ao pulse. Unfortunately, I get video, but no sound. This is the error that comes up:

```
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  640x352  12bpp  23.976 fps  1014.7 kbps (123.9 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.10.1 (build 2366/release)
Couldn't open video filter '***'.
***: cannot add video filter
[***] Init
[***] Updating font cache.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
[COLOR="Red"]AO: [pulse] Init failed: Connection refused
Failed to initialize audio driver 'pulse'
Could not open/initialize audio device -> no sound.
Audio: no sound[/COLOR]
Starting playback...

```

Any ideas?

---

