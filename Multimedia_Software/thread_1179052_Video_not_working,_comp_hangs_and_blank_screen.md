---
title: "Video not working, comp hangs and blank screen"
date: 2009-06-05
forum: Multimedia Software
---

### Post by unknown_killer on 2009-06-05
Whenevr i play any video the screen is blank green colored in mplyayer or vlc player and the comp hangs a bit and i have to struggle to get the mouse pointer to the close button and close it....The video doesnt show up and this is what i get! SOS!

> AVI file format detected.
[aviheader] Video stream found, -vid 0
AVI: No audio stream found -> no sound.
VIDEO:  [IV32]  320x240  24bpp  10.000 fps  965.4 kbps (117.8 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffindeo3] vfm: ffmpeg (FFmpeg Intel Indeo 3.1/3.2)
==========================================================================
Audio: no sound
Starting playback...
VDec: vo config request - 320 x 240 (preferred colorspace: Planar YVU9)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar YVU9 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0xf3a530]SwScaler: using unscaled yuv410p -> yuv420p special converter
VO: [xv] 320x240 => 320x240 Planar YV12 
V:   6.3  64/ 64  1%  0%  0.0% 0 0 

Exiting... (End of file)


---

### Post by Entropy_Sam on 2009-06-05
That happened to me when I tried to play movies after installing a realtime kernel on Ubuntu. Never did figure out why, but switching back to the generic Kernel fixed it...

---

