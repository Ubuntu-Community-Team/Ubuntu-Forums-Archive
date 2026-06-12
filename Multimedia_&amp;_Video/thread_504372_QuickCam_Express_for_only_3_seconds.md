---
title: "QuickCam Express for only 3 seconds"
date: 2007-07-19
forum: Multimedia &amp; Video
---

### Post by KevinRJohnson on 2007-07-19
Hey All,

I've been fussing with a Logitech QuickCam Express for the last few days.  I can view the video stream off of the webcam for about 3 seconds with mplayer and other webcam software, but only for about 1 to 3 seconds before it freezes the program.  I've tried to install the stock drivers with synaptic, and using the instructions here [http://ubuntuforums.org/showthread.php?t=500114&highlight=quickcam](http://ubuntuforums.org/showthread.php?t=500114&highlight=quickcam) (this guide went flawlessly) but no luck on getting more than 3 seconds off the stream.

Here's the dmesg output after loading the driver from above:
[29197.072000] ubuntu/media/gspcav1/gspca_core.c: driver gspca deregistered
[29265.884000] Linux video capture interface: v2.00
[29266.016000] ubuntu/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(SPCA561A)
[29266.020000] usbcore: registered new interface driver gspca
[29266.020000] ubuntu/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered

The Mplayer messages when viewing the stream:
```

 mplayer -v -v tv:// -tv driver=v4l:width=160:height=120:noaudio:device=/dev/video

MPlayer 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 Mobile CPU 1.60GHz (Family: 15, Model: 2, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Adding file tv://
this_opt = option: tv
Checking tv=driver=v4l:width=160:height=120:noaudio:device=/dev/video
Config pushed level is now 2
Config pushed level is now 3
Setting tv=driver=v4l:width=160:height=120:noaudio:device=/dev/video
get_path('codecs.conf') -> '/home/kevin/.mplayer/codecs.conf'
Reading /home/kevin/.mplayer/codecs.conf: Can't open '/home/kevin/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
CommandLine: '-v' '-v' 'tv://' '-tv' 'driver=v4l:width=160:height=120:noaudio:device=/dev/video'
init_freetype
get_path('font/font.desc') -> '/home/kevin/.mplayer/font/font.desc'
font: can't open file: /home/kevin/.mplayer/font/font.desc
font: can't open file: /usr/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
Using nanosleep() timing
get_path('input.conf') -> '/home/kevin/.mplayer/input.conf'
Can't open input config file /home/kevin/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 67 binds
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('.conf') -> '/home/kevin/.mplayer/.conf'

[[[init getch2]]]

Playing tv://.
get_path('sub/') -> '/home/kevin/.mplayer/sub/'
STREAM: [tv] tv://
STREAM: Description: TV Input
STREAM: Author: Benjamin Zores, Albeu
STREAM: Comment: 
s->pos=0  newpos=0  new_bufpos=0  buflen=0  
TV file format detected.
Selected driver: v4l
 name: Video 4 Linux input
 author: Alex Beregszaszi
 comment: under development
Video fd: 3, 0x8a66e58
Selected device: Logitech QuickCam Express II
 Capabilites: capture 
 Device type: 1
 Supported sizes: 160x120 => 352x288
 Inputs: 1
  0: SPCA561:  (tuner:0, norm:pal)
mbuf: size=2457616, frames=2
our buffer: 0xb5c0b000

debug: control(priv=0x8a6a9a0, cmd=2, arg=(nil))

debug: control(priv=0x8a6a9a0, cmd=264, arg=0x89362dc)

debug: control(priv=0x8a6a9a0, cmd=1026, arg=0x896f23c)
Using input 'SPCA561'

debug: control(priv=0x8a6a9a0, cmd=1025, arg=0xbfcad220)
Selected norm: pal

debug: control(priv=0x8a6a9a0, cmd=518, arg=0x8a67930)

debug: control(priv=0x8a6a9a0, cmd=272, arg=0x89362d4)
Requested width: 160

debug: control(priv=0x8a6a9a0, cmd=273, arg=0x89362d4)

debug: control(priv=0x8a6a9a0, cmd=275, arg=0x89362d8)
Requested height: 120

debug: control(priv=0x8a6a9a0, cmd=276, arg=0x89362d8)

debug: control(priv=0x8a6a9a0, cmd=3, arg=(nil))
Selected input hasn't got a tuner!
==> Found video stream: 0

debug: control(priv=0x8a6a9a0, cmd=262, arg=0x8a6797c)
Output format: Planar YV12

debug: control(priv=0x8a6a9a0, cmd=257, arg=0xbfcad2d4)

debug: control(priv=0x8a6a9a0, cmd=4, arg=(nil))

debug: control(priv=0x8a6a9a0, cmd=265, arg=0x8a67a58)

debug: control(priv=0x8a6a9a0, cmd=274, arg=0x8a67a5c)
Picture values:
 Depth: 12, Palette: yuv420p (Format: Planar YV12)
 Brightness: 27136, Hue: 0, Colour: 0, Contrast: 11264
buffer: 0 => 0x8a67948
buffer: 1 => 0x8a67958
Using a ring buffer for maximum 2 frames, 0 MB total size.

debug: control(priv=0x8a6a9a0, cmd=278, arg=0xbfcad278)

debug: control(priv=0x8a6a9a0, cmd=286, arg=(nil))

debug: control(priv=0x8a6a9a0, cmd=280, arg=0xbfcad278)

debug: control(priv=0x8a6a9a0, cmd=286, arg=(nil))

debug: control(priv=0x8a6a9a0, cmd=282, arg=0xbfcad278)

debug: control(priv=0x8a6a9a0, cmd=286, arg=(nil))

debug: control(priv=0x8a6a9a0, cmd=284, arg=0xbfcad278)

debug: control(priv=0x8a6a9a0, cmd=286, arg=(nil))
[V] filefmt:9  fourcc:0x32315659  size:160x120  fps:25.00  ftime:=0.0400
get_path('sub/') -> '/home/kevin/.mplayer/sub/'
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
X11 opening display: :0.0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1600x1200 with depth 24 and 32 bpp (":0.0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
Disabling DPMS
DPMSDisable stat: 1
[xv common] Drawing no colorkey.
[xv common] Maximum source image dimensions: 2046x2046
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 160 x 120 (preferred colorspace: Planar YV12)
Trying filter chain: vo
vo_debug: query(Planar YV12) returned 0x437 (i=0) 
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO Config (160x120->160x120,flags=0,'MPlayer',0x32315659)
VO: [xv] 160x120 => 160x120 Planar YV12 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x59565955 (UYVY) packed
Xvideo image format: 0x30323449 (I420) planar
Xvideo image format: 0x3 (   ) packed
using Xvideo port 158 for hw scaling
[xv] dx: 0 dy: 0 dw: 160 dh: 120
Selected video codec: [rawyv12] vfm: raw (RAW YV12)
==========================================================================
Audio: no sound
Freeing 0 unused audio chunks.
Starting playback...

debug: control(priv=0x8a6a9a0, cmd=2, arg=(nil))

fps = -1.000000, interval = 0.000000, a_skew = 0.000000, corr_skew = 0.000000
vcnt = 0, acnt = 0

debug: control(priv=0x8a6a9a0, cmd=2, arg=(nil))

fps = 25.000000, interval = 0.040000, a_skew = 0.000000, corr_skew = 0.000000
vcnt = 0, acnt = 0
*** [vo] Exporting mp_image_t, 160x120x12bpp YUV planar, 28800 bytes
(imgfmt: 32315659, planes: (nil),(nil),(nil) strides: 0,0,0, chroma: 80x60, shift: h:1,v:1)
get_path('subfont.ttf') -> '/home/kevin/.mplayer/subfont.ttf'
Unicode font: 255 glyphs.

fps = 25.000000, interval = 0.080000, a_skew = 0.000000, corr_skew = 0.000000
vcnt = 0, acnt = 0
OSD chg: 3  V: no  pb:-1  
OSD chg: 2  V: no  pb:-1  
[xv] dx: 0 dy: 0 dw: 160 dh: 120
V:   0.0   1/  1 ??% ??% ??,?% 0 0 
debug: control(priv=0x8a6a9a0, cmd=2, arg=(nil))

fps = 25.000000, interval = 0.120000, a_skew = 0.000000, corr_skew = 0.000000
vcnt = 0, acnt = 0
V:   0.0   2/  2 ??% ??% ??,?% 0 0 
debug: control(priv=0x8a6a9a0, cmd=2, arg=(nil))
V:   0.1   3/  3 ??% ??% ??,?% 0 0 
debug: control(priv=0x8a6a9a0, cmd=2, arg=(nil))

fps = 25.000000, interval = 0.160000, a_skew = 0.000000, corr_skew = 0.000000
vcnt = 0, acnt = 0
V:   0.1   4/  4 ??% ??% ??,?% 0 0 
debug: control(priv=0x8a6a9a0, cmd=2, arg=(nil))

fps = 25.000000, interval = 0.200000, a_skew = 0.000000, corr_skew = 0.000000
vcnt = 0, acnt = 0
V:   0.2   5/  5 ??% ??% ??,?% 0 0 
debug: control(priv=0x8a6a9a0, cmd=2, arg=(nil))

fps = 25.000000, interval = 0.240000, a_skew = 0.000000, corr_skew = 0.000000
vcnt = 0, acnt = 0
V:   0.2   6/  6 ??% ??% ??,?% 0 0 
debug: control(priv=0x8a6a9a0, cmd=2, arg=(nil))

fps = 25.000000, interval = 0.280000, a_skew = 0.000000, corr_skew = 0.000000
vcnt = 0, acnt = 0
V:   0.2   7/  7 ??% ??% ??,?% 0 0 
debug: control(priv=0x8a6a9a0, cmd=2, arg=(nil))

fps = 25.000000, interval = 0.320000, a_skew = 0.000000, corr_skew = 0.000000
vcnt = 0, acnt = 0
V:   0.3   8/  8 ??% ??% ??,?% 0 0 
debug: control(priv=0x8a6a9a0, cmd=2, arg=(nil))

fps = 25.000000, interval = 0.360000, a_skew = 0.000000, corr_skew = 0.000000
vcnt = 0, acnt = 0
V:   0.3   9/  9 ??% ??% ??,?% 0 0 
debug: control(priv=0x8a6a9a0, cmd=2, arg=(nil))

fps = 25.000000, interval = 0.400000, a_skew = 0.000000, corr_skew = 0.000000
vcnt = 0, acnt = 0
V:   0.4  10/ 10 ??% ??% ??,?% 0 0 
debug: control(priv=0x8a6a9a0, cmd=2, arg=(nil))

fps = 25.000000, interval = 0.440000, a_skew = 0.000000, corr_skew = 0.000000
vcnt = 0, acnt = 0
V:   0.4  11/ 11 ??% ??% ??,?% 0 0 
debug: control(priv=0x8a6a9a0, cmd=2, arg=(nil))

fps = 25.000000, interval = 0.480000, a_skew = 0.000000, corr_skew = 0.000000
vcnt = 0, acnt = 0
V:   0.4  12/ 12 ??% ??% ??,?% 0 0 
debug: control(priv=0x8a6a9a0, cmd=2, arg=(nil))

fps = 25.000000, interval = 0.520000, a_skew = 0.000000, corr_skew = 0.000000
vcnt = 0, acnt = 0
V:   0.5  13/ 13 ??% ??% ??,?% 0 0 
debug: control(priv=0x8a6a9a0, cmd=2, arg=(nil))

fps = 25.000000, interval = 0.560000, a_skew = 0.000000, corr_skew = 0.000000
vcnt = 0, acnt = 0
V:   0.5  14/ 14  0% 36%  0.0% 0 0 
debug: control(priv=0x8a6a9a0, cmd=2, arg=(nil))

fps = 25.000000, interval = 0.600000, a_skew = 0.000000, corr_skew = 0.000000
vcnt = 0, acnt = 0
V:   0.6  15/ 15  0% 33%  0.0% 0 0 
debug: control(priv=0x8a6a9a0, cmd=2, arg=(nil))

fps = 25.000000, interval = 0.640000, a_skew = 0.000000, corr_skew = 0.000000
vcnt = 0, acnt = 0
V:   0.6  16/ 16  0% 31%  0.0% 0 0 
debug: control(priv=0x8a6a9a0, cmd=2, arg=(nil))

fps = 25.000000, interval = 0.680000, a_skew = 0.000000, corr_skew = 0.000000
vcnt = 0, acnt = 0
V:   0.6  17/ 17  0% 29%  0.0% 0 0 
debug: control(priv=0x8a6a9a0, cmd=2, arg=(nil))

fps = 25.000000, interval = 0.720000, a_skew = 0.000000, corr_skew = 0.000000
vcnt = 0, acnt = 0
V:   0.7  18/ 18  0% 27%  0.0% 0 0 
debug: control(priv=0x8a6a9a0, cmd=2, arg=(nil))

fps = 25.000000, interval = 0.760000, a_skew = 0.000000, corr_skew = 0.000000
vcnt = 0, acnt = 0
V:   0.7  19/ 19  0% 26%  0.0% 0 0 
debug: control(priv=0x8a6a9a0, cmd=2, arg=(nil))

fps = 25.000000, interval = 0.800000, a_skew = 0.000000, corr_skew = 0.000000
vcnt = 0, acnt = 0
V:   0.8  20/ 20  0% 24%  0.0% 0 0 
debug: control(priv=0x8a6a9a0, cmd=2, arg=(nil))

fps = 25.000000, interval = 0.840000, a_skew = 0.000000, corr_skew = 0.000000
vcnt = 0, acnt = 0
V:   0.8  21/ 21  0% 23%  0.0% 0 0 
debug: control(priv=0x8a6a9a0, cmd=2, arg=(nil))


MPlayer interrupted by signal 2 in module: video_read_frame

*** uninit(0xAC9)
Uninit video: raw
DEMUXER: freeing demuxer at 0x8a6a128
Waiting for threads to finish... 

MPlayer interrupted by signal 2 in module: free_demuxer

*** uninit(0xC9)
Successfully enabled DPMS

[[[uninit getch2]]]
vo: uninit ...
max framesize was 28800 bytes

```

{( I had to exit manually via double Ctrl+C)}

Oh, and lsusb's output:
Bus 002 Device 002: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:0928 Logitech, Inc. Quickcam Express
Bus 001 Device 001: ID 0000:0000  

Hopefully some one who has gotten this worked out will let me in on the secret.

Thanks,
Kevin

---

### Post by wolfen69 on 2007-07-19
this  [https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech)  may be of some help

---

