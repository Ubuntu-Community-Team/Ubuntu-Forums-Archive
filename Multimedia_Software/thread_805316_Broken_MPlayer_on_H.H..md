---
title: "Broken MPlayer on H.H."
date: 2008-05-23
forum: Multimedia Software
---

### Post by realn on 2008-05-23
I just installed H.H. AMD64. Then I installed nvidia restricted drivers. Then mplayer. It DOESN'T work. Please help.

here's what I get when I do mplayer cccc.avi
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  624x352  24bpp  23.976 fps  1012.4 kbps (123.6 kbyte/s)
Clip info:
 Software: transcode-1.0.2
Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".
xscreensaver_disable: Could not find XScreenSaver window.
[VO_XV] It seems there is no Xvideo support for your video card available.
[VO_XV] Run 'xvinfo' to verify its Xv support and read
[VO_XV] DOCS/HTML/en/video.html#xv!
[VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
[VO_XV] Try -vo x11.
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] Failed to connect to server: Connection refused
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  11.5 (11.5) of 2538.1 (42:18.1)  1.0%

It worked out of the box on Gutsy, now i'm back to middle age. :confused:

And yes, I tried also -vo xv, -vo x11

Please help.
Thanks.

---

