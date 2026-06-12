---
title: "mplayer and wavpack"
date: 2008-08-13
forum: Multimedia Software
---

### Post by shadow999 on 2008-08-13
I've have this mkv video that I simply cannot play with any player. Totem just exits and claims a "Segmentation fault". MPlayer at least gets far enough to play the video, but without any audio.

From the messages I'm guessing it's an issue with wavpack, but I have both wavpack and libwavpack1 installed. I'm really out of ideas what to try by now. Any help would be greatly appreciated.

```

[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Unknown/unsupported audio codec ID 'A_WAVPACK4' for track 2 or missing/faulty
[mkv] private codec data.
[mkv] Track ID 2: audio (A_WAVPACK4), -aid 0, -alang jpn
[mkv] Unknown/unsupported audio codec ID 'A_WAVPACK4' for track 3 or missing/faulty
[mkv] private codec data.
[mkv] Track ID 3: audio (A_WAVPACK4), -aid 1, -alang eng
[mkv] Will play video track 1.
[mkv] No audio track found/wanted.
Matroska file format detected.
VIDEO:  [avc1]  1440x1080  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
Audio: no sound
Starting playback...
VDec: vo config request - 1440 x 1080 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 1440x1080 => 1440x1080 Planar YV12 
```

---

