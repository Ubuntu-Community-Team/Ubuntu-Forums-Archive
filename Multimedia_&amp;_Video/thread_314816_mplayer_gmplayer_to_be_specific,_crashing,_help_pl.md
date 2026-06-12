---
title: "mplayer: gmplayer to be specific, crashing, help plz"
date: 2006-12-08
forum: Multimedia &amp; Video
---

### Post by yasha on 2006-12-08
Ok, I've spent a couple hours on this one, and I believe I'm close to what the problem is but see no visable way to fix it.

When playing back the same file I get this for mplayer and the other for gmplayer, so I think something's missing for lib/include on build, but I don't know what exactly. Packaged version of gmplayer works fine....and yes, extmod is enabled, but I'm using the Xgl/compiz eyecandy addition to my Xorg, from [here](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FCompiz_.28Nvidia.29)

It will work with the x11 (Ximage/Shm) driver(which of course isn't resizeable), just not with xv, gl,gl2, xvidix or xvmc. Doing fullscreen from command prompt "gmplayer -fs .." keeps it from outright bombing, but that's it, just shows up as a fullscreen of yellow.

I know it's something wrong with my build, as I've tested not only the svn, but the last stable release source as well with the same end result below for mplayer and then gmplayer:
[quote=plain mplayer with gl2 driver]
MPlayer dev-SVN-r21535-4.1.2 (C) 2000-2006 MPlayer Team
CPU: Genuine Intel(R) CPU           T2500  @ 2.00GHz (Family: 6, Model: 14, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

Playing /home/yasha/Desktop/bleh.wmv.
ASF file format detected.
VIDEO:  [WMV3]  640x480  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 name: 
 author: 
 copyright: 
 comments: 
Xlib:  extension "XFree86-VidModeExtension" missing on display ":0.0".
==========================================================================
Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
GetOutput r=0x0   size:921600  align:1
StreamCount r=0x0  1  1
Decoder supports the following formats: YV12 YUY2 UYVY YVYU RGB8 RGB555 RGB565 RGB24 RGB32 
Decoder is capable of YUV output (flags 0x1b)
VDec: vo config request - 640 x 480 (preferred colorspace: Packed YUY2)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 640x480 => 640x480 Planar YV12 
Selected video codec: [wmv9dmo] vfm: dmo (Windows Media Video 9 DMO)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16005->176400)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))[/quote]



[quote=gmplayer using gl2]MPlayer dev-SVN-r21535-4.1.2 (C) 2000-2006 MPlayer Team
CPU: Genuine Intel(R) CPU           T2500  @ 2.00GHz (Family: 6, Model: 14, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
Xlib:  extension "XFree86-VidModeExtension" missing on display ":0.0".
Xlib:  extension "XFree86-VidModeExtension" missing on display ":0.0".

Playing /home/yasha/Desktop/bleh.wmv.
ASF file format detected.
VIDEO:  [WMV3]  640x480  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 name: 
 author: 
 copyright: 
 comments: 
==========================================================================
Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
GetOutput r=0x0   size:921600  align:1
StreamCount r=0x0  1  1
Decoder supports the following formats: YV12 YUY2 UYVY YVYU RGB8 RGB555 RGB565 RGB24 RGB32 
Decoder is capable of YUV output (flags 0x1b)
VDec: vo config request - 640 x 480 (preferred colorspace: Packed YUY2)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
SwScaler: using unscaled yuv420p -> bgr24 special converter
VO: [gl2] 640x480 => 640x480 BGR 24-bit 
[ws] Error in display.
[ws]  Error code: 2 ( BadValue (integer parameter out of range for operation) )
[ws]  Request code: 12
[ws]  Minor code: 0
[ws]  Modules: init_video_codec
[/quote]

---

### Post by taurus on 2006-12-08
What happens if you just add this line to your ~/.mplayer/config to get full screen?

```

zoom=yes

```

---

### Post by yasha on 2006-12-08
](*,) 

Same, the x11 shim driver is re-sizeable then of course, but that's it. Same error for all the other drivers which should function, and DID function from the built package that's available.

---

### Post by yasha on 2006-12-10
no one?

---

### Post by yasha on 2006-12-12
alrighty then...

---

