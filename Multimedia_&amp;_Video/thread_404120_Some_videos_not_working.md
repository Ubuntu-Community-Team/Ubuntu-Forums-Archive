---
title: "Some videos not working"
date: 2007-04-08
forum: Multimedia &amp; Video
---

### Post by Fireblend on 2007-04-08
Hey, I've been having trouble with *some* videos lately. Most work, but some (they're all .mkv, although I have other ones that work in the same format) make the Movie Player window close immediately after it's open, (the same thing happens with VLC). I can actually hear the audio playing before the window closes. They play fine on my Windows computer tho. Also, I opened it in Xine and it seemed to work, but there was no video and the screen was huge. Could this be a resolution problem?

Anyone have any idea of what could be wrong? any help would be greatly appreciated! Thanks.

---

### Post by krussell on 2007-04-08
Hello :-)
To play *.mkv format, you need the codecs which can be found here (if you are using edgy):
[http://packages.ubuntu.com/edgy/libdevel/libebml-dev](http://packages.ubuntu.com/edgy/libdevel/libebml-dev)
[http://packages.ubuntu.com/edgy/libdevel/libmatroska-dev](http://packages.ubuntu.com/edgy/libdevel/libmatroska-dev)

Sorry my last answer was not correct, i was moving too fast before checking ubuntu repositories.

---

### Post by the_mouse on 2007-04-10
I installed w32codecs, but I experience very choppy playback of mkv files, almost as a slideshow. My CPU speed is 1566MHz, but I think it's enough to play movies with such resolution (1280x720), because I have one wmv Spider Man 3 trailer with such hi-res and it runs smoothly. So I assume the problem is with the codecs, I installed the above packages with no change...
When I play the file with mplayer, I get:
```
[mkv] Track ID 1: audio (A_AC3), -aid 0, -alang und
[mkv] Track ID 2: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Will play video track 2
[mkv] Will play audio track 1
Matroska file format detected.
VIDEO:  [avc1]  1280x720  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
AC3: 5.1 (3f+2r+lfe)  48000 Hz  384.0 kbit/s
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
Starting playback...
VDec: vo config request - 1280 x 720 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1280x720 => 1280x720 Planar YV12
alsa-space: xrun of at least 240.671 msecs. resetting stream?% 0 0 7%
Error while decoding frame!33 ct:  0.008   3/  3 ??% ??% ??,?% 2 0 16%
alsa-space: xrun of at least 131.397 msecs. resetting stream?% 4 0 17%
Error while decoding frame!48 ct:  0.108  27/ 27 323% 11%  4.6% 26 0 30%
alsa-space: xrun of at least 40.174 msecs. resetting stream4.2% 29 0 30%
**Error while decoding frame!17 ct:  0.196  48/ 48 230%  6%  3.2% 47 0 44%**
A:   4.0 V:   2.1 A-V:  1.913 ct:  0.213  52/ 52 219%  6%  3.1% 50 0 47%
```

And many other "Error decoding frame"
What should I do?

---

### Post by the_mouse on 2007-04-12
Doesn't anyone known how to fix that.
Do you install something other to play mkv files?

---

