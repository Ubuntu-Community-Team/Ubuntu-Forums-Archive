---
title: "unable to play live stream videos by using Mplayer"
date: 2008-01-04
forum: Multimedia &amp; Video
---

### Post by gchakravarthy on 2008-01-04
Hi,
  I installed mplayer with the following options.
  i downloaded live stream libraries.
  ./configure --enable-gui
  make
  make install
  I am trying to play live stream it is showing the following errors.

 ./gmplayer -V  rtsp://10.50.27.155/sample_100kbit.mov
MPlayer 1.0rc2-4.0.0 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.60GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
X11 opening display: :0.0
vo: X11 color mask:  FFFF  (R:F800 G:7E0 B:1F)
vo: X11 running at 640x480 with depth 16 and 16 bpp (":0.0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
Adding filename sample_100kbit.mov && pathname rtsp://10.50.27.155
get_path('codecs.conf') -> '/root/.mplayer/codecs.conf'
Reading /root/.mplayer/codecs.conf: Can't open '/root/.mplayer/codecs.conf': No such file or directory
Reading /usr/local/etc/mplayer/codecs.conf: Can't open '/usr/local/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --enable-gui
CommandLine: '-V' 'rtsp://10.50.27.155/sample_100kbit.mov'
init_freetype
get_path('font/font.desc') -> '/root/.mplayer/font/font.desc'
font: can't open file: /root/.mplayer/font/font.desc
font: can't open file: /usr/local/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/root/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/root/.mplayer/input.conf'
Can't open input config file /root/.mplayer/input.conf: No such file or directory
Can't open input config file /usr/local/etc/mplayer/input.conf: No such file or directory
Falling back on default (hardcoded) input config
vo: X11 truecolor visual 0x22, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x23, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x24, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x25, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x26, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x27, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x28, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x29, depth 16, R:F800 G:7E0 B:1F
get_path('skins') -> '/root/.mplayer/skins'
get_path('Skin') -> '/root/.mplayer/Skin'
SKIN dir 1: '/root/.mplayer/skins'
SKIN dir 1 (obsolete): '/root/.mplayer/Skin'
SKIN dir 2: '/usr/local/share/mplayer/skins'
SKIN dir 2 (obsolete): '/usr/local/share/mplayer/Skin'
vo: X11 truecolor visual 0x22, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x23, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x24, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x25, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x26, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x27, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x28, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x29, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x22, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x23, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x24, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x25, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x26, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x27, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x28, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x29, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x22, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x23, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x24, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x25, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x26, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x27, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x28, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x29, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x22, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x23, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x24, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x25, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x26, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x27, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x28, depth 16, R:F800 G:7E0 B:1F
vo: X11 truecolor visual 0x29, depth 16, R:F800 G:7E0 B:1F
get_path('subfont.ttf') -> '/root/.mplayer/subfont.ttf'
[x11] NET style stay on top (layer 0). Using state _NET_WM_STATE_ABOVE.
New_Face failed. Maybe the font path is wrong.
Please supply the text font file (~/.mplayer/subfont.ttf).
subtitle font: load_sub_face failed.
get_path('sample_100kbit.mov.conf') -> '/root/.mplayer/sample_100kbit.mov.conf'
get_path('subfont.ttf') -> '/root/.mplayer/subfont.ttf'
[x11] NET style stay on top (layer 0). Using state _NET_WM_STATE_ABOVE.
New_Face failed. Maybe the font path is wrong.
Please supply the text font file (~/.mplayer/subfont.ttf).
subtitle font: load_sub_face failed.

Playing rtsp://10.50.27.155/sample_100kbit.mov.
get_path('sub/') -> '/root/.mplayer/sub/'
STREAM_RTSP, URL: rtsp://10.50.27.155/sample_100kbit.mov
Filename for url is now rtsp://10.50.27.155/sample_100kbit.mov
Filename for url is now rtsp://10.50.27.155/sample_100kbit.mov
Resolving 10.50.27.155 for AF_INET6...
[x11] NET style stay on top (layer 0). Using state _NET_WM_STATE_ABOVE.
Couldn't resolve name for AF_INET6: 10.50.27.155
Connecting to server 10.50.27.155[10.50.27.155]: 554...
[x11] NET style stay on top (layer 0). Using state _NET_WM_STATE_ABOVE.
connect error: Connection refused
Resolving 10.50.27.155 for AF_INET6...
[x11] NET style stay on top (layer 0). Using state _NET_WM_STATE_ABOVE.
Couldn't resolve name for AF_INET6: 10.50.27.155
Connecting to server 10.50.27.155[10.50.27.155]: 7070...
[x11] NET style stay on top (layer 0). Using state _NET_WM_STATE_ABOVE.
connect error: Connection refused
Filename for url is now rtsp://10.50.27.155/sample_100kbit.mov
Filename for url is now rtsp://10.50.27.155/sample_100kbit.mov
STREAM_LIVE555, URL: rtsp://10.50.27.155/sample_100kbit.mov
STREAM: [RTSP and SIP] rtsp://10.50.27.155/sample_100kbit.mov
STREAM: Description: standard RTSP and SIP
STREAM: Author: Ross Finlayson
STREAM: Comment: Uses LIVE555 Streaming Media library.
Stream not seekable!
 file format detected.
Failed to get a SDP description from URL "rtsp://10.50.27.155/sample_100kbit.mov": connect() failed: Connection refused

please help me to solve this issue.

rgds
Chakry G

---

