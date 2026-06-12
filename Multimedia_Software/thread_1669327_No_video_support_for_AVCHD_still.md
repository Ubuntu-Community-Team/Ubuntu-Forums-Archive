---
title: "No video support for AVCHD still?"
date: 2011-01-17
forum: Multimedia Software
---

### Post by tehowe on 2011-01-17
I've been trying to view the footage I have in 1080i AVCHD on my new system but can only view it in VLC, and then only when hardware acceleration is turned off, and there's still a bit of shearing with a hexcore and a Radeon 5850.

Is there a trick to get it to play and/or preview in Mplayer/OpenShot/PiTiVi ? I've tried them all, and I can hear sound but no video. Maybe there's a system-wide way to shut off video decode acceleration.

I guess what I'm asking is, can anyone play/preview/edit in these applications with AVCHD or is it something with my new system? Everything else seems to work great. Maybe I need to try turning off compiz compositing?

Unfortunately, I bought the damn thing to do exactly this kind of video editing, and don't want to have to drop back into Win 7 to use Vegas.

Thanks;

---

### Post by cotcot on 2011-01-17
I can edit AVCHD with Blender (2.5 beta). There is still an issue with the fact that my video camera (Canon HF100) gives 1080i 50 frames but I found a workaround (loading video clips in 50 fps; render in 25 fps). Playback with VLC is OK as well.
Ffmpeg is capable to deal with AVCHD. Blender uses ffmpeg.
Converting AVCHD to for instance mp4 with ffmpeg is OK. 
For simple editing I use blender directly on the AVCHD clips. For more complex editing (titles, effects, keyframes) I convert to mp4 or mpeg be loading the clips in Blender.

Kdenlive also claims editing AVCHD. I have tried it. It works.

---

### Post by tehowe on 2011-01-18
Well, this is a wider problem - I can't play anything in Mplayer with video. I can hear the audio, but .avi, .mp4, everything fails to work. And it's not compositing, I tried turning it off. Tried replacing the libavcodec-extra-52 file with the one marked with the official little ubuntu icon and that didn't help either. What the hell. Guess I need to start a different thread.

---

### Post by no2498 on 2011-01-18
try your mp4's in smplayer
type it in a terminal it tells you how to install it

---

### Post by mc4man on 2011-01-18
> I can't play anything in Mplayer with video
Have you used any ppa's? What does mplayer show from cli, like 
mplayer /path/to/anyvideo
or 
mplayer -v /path/to/anyvideo

You may wish to condider using a current mplayer that doesn't use the shared ffmpeg libraries
[You can build ]("http://ubuntuforums.org/showthread.php?t=1542240")or find a ppa
This is a good ppa, I'm sure there are some others that enable vaapi in mplayer if desired
[https://launchpad.net/~motumedia/+archive/mplayer-daily](https://launchpad.net/~motumedia/+archive/mplayer-daily)

---

### Post by BicyclerBoy on 2011-01-18
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
add medibuntu to your ppa lists.

install ubuntu-restricted-extras

Medibuntu must be re-enabled after upgrades.

---

### Post by tehowe on 2011-01-19
> **BicyclerBoy said:**
> [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
add medibuntu to your ppa lists.

install ubuntu-restricted-extras

Medibuntu must be re-enabled after upgrades.

I could have sworn Mplayer installed some such codecs on its own in 10.04, now that I think of it. :confused:
First thing I get home tonight, this PPA is going in, thanks.

---

### Post by no2498 on 2011-01-19
smplayer does

I could have sworn Mplayer installed some such codecs on its own in 10.04, now that I think of it.

---

### Post by no2498 on 2011-01-19
smplayer does

I could have sworn Mplayer installed some such codecs on its own in 10.04, now that I think of it.

---

### Post by tehowe on 2011-01-19
> **mc4man said:**
> Have you used any ppa's? What does mplayer show from cli, like 
mplayer /path/to/anyvideo
or 
mplayer -v /path/to/anyvideo

^^^ That's a good idea!

Story so far, based on the advice in this thread 


[LIST]
[*]medibuntu is now definitely installed along with the ubuntu-restricted-extras package, if it wasn't before
[*]w64codecs is installed, all using the bash commands found on help.ubuntu.com
[*]I've tried smplayer as well and no dice
[*]fglrx 2:8.780-0ubuntu2 (version packaged with Maverick) is installed
[/LIST]
Here's the mplayer readouts. They have a bunch of errors scattered through them, and in the end mplayer tries playing this simple avi file as RAW! Here are the highlights...

VIDEO:  []  320x240  24bpp  29.970 fps  54827.5 kbps (6692.8 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1

This is a Radeon 5850, so odd it's trying to call vdpau... (I checked, libva1 and libva-x11-1 are installed) Reading around online makes it sound like mga_vid is deprecated

Then from the verbose readout, there's 

get_path('codecs.conf') -> '/home/tehowe/.mplayer/codecs.conf'
Reading /home/tehowe/.mplayer/codecs.conf: Can't open '/home/tehowe/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.

The rest follows... not sure which is the most important lead. Thanks for the help so far!

```
tehowe@here:/media/Data/Media/Video$ mplayer 2007_AikidoClass.avi
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing 2007_AikidoClass.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
AVI: ODML: Building ODML index (2 superindexchunks).
Detected NON-INTERLEAVED AVI file format.
VIDEO:  []  320x240  24bpp  29.970 fps  54827.5 kbps (6692.8 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Opening video filter: [flip]
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0xc09860]using unscaled bgr24 -> yuv420p special converter
VO: [xv] 320x240 => 320x240 Planar YV12 
Selected video codec: [rawbgr24flip] vfm: raw (RAW BGR24)
==========================================================================
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 1411.2 kbit/100.00% (ratio: 176400->176400)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
A:   6.1 V:   6.1 A-V:  0.002 ct: -0.064 184/184  0%  2%  7.4% 28 0 
Exiting... (Quit)

```Here's the verbose version...

```
tehowe@here:/media/Data/Media/Video$ mplayer -v 2007_AikidoClass.avi
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
CPU vendor name: AuthenticAMD  max cpuid level: 6
CPU: AMD Phenom(tm) II X6 1090T Processor (Family: 16, Model: 10, Stepping: 0)
extended cpuid-level: 27
extended cache-info: 33587520
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNowExt: 1 SSE: 1 SSE2: 1 SSSE3: 0
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/tehowe/.mplayer/codecs.conf'
Reading /home/tehowe/.mplayer/codecs.conf: Can't open '/home/tehowe/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --prefix=/usr --confdir=/etc/mplayer --enable-xvmc --enable-menu --disable-arts --enable-largefiles --language=all --disable-libdvdcss-internal --disable-dvdread-internal --disable-libavutil_a --disable-libavcodec_a --disable-libavformat_a --disable-libpostproc_a --disable-libswscale_a --enable-runtime-cpudetection --enable-debug --enable-mga --enable-3dfx --enable-tdfxfb --disable-gui
CommandLine: '-v' '2007_AikidoClass.avi'
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/tehowe/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/tehowe/.mplayer/input.conf'
Can't open input config file /home/tehowe/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 91 binds
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('2007_AikidoClass.avi.conf') -> '/home/tehowe/.mplayer/2007_AikidoClass.avi.conf'

Playing 2007_AikidoClass.avi.
get_path('sub/') -> '/home/tehowe/.mplayer/sub/'
[file] File size is 10623984128 bytes
STREAM: [file] 2007_AikidoClass.avi
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
LAVF_check: AVI format
AVI file format detected.
list_end=0xFE50
======= AVI Header =======
us/frame: 33366  (fps=29.971)
max bytes/sec: 7049757
padding: 512
MainAVIHeader.dwFlags: (2064) HAS_INDEX TRUST_CKTYPE
frames  total: 45200   initial: 0
streams: 2
Suggested BufferSize: 230408
Size:  320 x 240
==========================
list_end=0x7ED4
==> Found video stream: 0
[aviheader] Video stream found, -vid 0
====== STREAM Header =====
Type: vids   FCC: DIB  (20424944)
Flags: 0
Priority: 0   Language: 0
InitialFrames: 0
Rate: 30000/1001 = 29.970
Start: 5   Len: 45186
Suggested BufferSize: 230408
Quality 0
Sample size: 0
==========================
Found 'bih', 40 bytes of 40
======= VIDEO Format ======
  biSize 40
  biWidth 320
  biHeight 240
  biPlanes 1
  biBitCount 24
  biCompression 0=''
  biSizeImage 230400
===========================
====== AVI Super Index Header ========
  FCC (indx) dwSize (32248) wLongsPerEntry(4)
  bIndexSubType (0) bIndexType (0)
  nEntriesInUse (12) dwChunkId (00db)
  dwReserved[0] (0) dwReserved[1] (0) dwReserved[2] (0)
===========================
ODML (00db): [0] 0x0000000000010000 0x7e00 4028
ODML (00db): [1] 0x0000000038d6ea00 0x7e00 4028
ODML (00db): [2] 0x0000000071b49200 0x7e00 4028
ODML (00db): [3] 0x00000000a6f96e00 0x7e00 4028
ODML (00db): [4] 0x00000000dfc44a00 0x7e00 4028
ODML (00db): [5] 0x0000000118a14200 0x7e00 4028
ODML (00db): [6] 0x00000001517dbc00 0x7e00 4028
ODML (00db): [7] 0x0000000189671a00 0x7e00 4028
ODML (00db): [8] 0x00000001c2400e00 0x7e00 4028
ODML (00db): [9] 0x00000001fb1c8600 0x7e00 4028
ODML (00db): [10] 0x0000000233f97e00 0x7e00 4028
ODML (00db): [11] 0x000000026cd5f800 0x7e00 878
list_end=0xFD44
==> Found audio stream: 1
[aviheader] Audio stream found, -aid 1
====== STREAM Header =====
Type: auds   FCC:  (0)
Flags: 0
Priority: 0   Language: 0
InitialFrames: 0
Rate: 176400/4 = 44100.000
Start: 0   Len: 66568950
Suggested BufferSize: 88208
Quality 0
Sample size: 4
==========================
Found 'wf', 18 bytes of 18
======= WAVE Format =======
Format Tag: 1 (0x1)
Channels: 2
Samplerate: 44100
avg byte/sec: 176400
Block align: 4
bits/sample: 16
cbSize: 0
==========================================================================
====== AVI Super Index Header ========
  FCC (indx) dwSize (32248) wLongsPerEntry(4)
  bIndexSubType (0) bIndexType (0)
  nEntriesInUse (3) dwChunkId (01wb)
  dwReserved[0] (0) dwReserved[1] (0) dwReserved[2] (0)
===========================
ODML (01wb): [0] 0x0000000000017e00 0x7e00 27099450
ODML (01wb): [1] 0x0000000100347000 0x7e00 26812800
ODML (01wb): [2] 0x00000002003c7800 0x7e00 12656700
list_end=0xFE50
AVI: dmlh found (size=248) (total_frames=45186)
list_end=0x3FBEF800
Found movie at 0x10000 - 0x3FBEF800
Reading INDEX block, 4831 chunks for 45200 frames (fpos=1069479944).
Additional RIFF header...
list_end=0x7F82D600
Found movie at 0x10000 - 0x7F82D600
Additional RIFF header...
list_end=0xBF453000
Found movie at 0x10000 - 0xBF453000
Additional RIFF header...
list_end=0xFF05B400
Found movie at 0x10000 - 0xFF05B400
Additional RIFF header...
list_end=0x3EC6B600
Found movie at 0x10000 - 0x3EC6B600
Additional RIFF header...
list_end=0x7E891E00
Found movie at 0x10000 - 0x7E891E00
Additional RIFF header...
list_end=0xBE4BCE00
Found movie at 0x10000 - 0xBE4BCE00
Additional RIFF header...
list_end=0xFE0CD000
Found movie at 0x10000 - 0xFE0CD000
Additional RIFF header...
list_end=0x3DCDD200
Found movie at 0x10000 - 0x3DCDD200
Additional RIFF header...
list_end=0x793D2200
Found movie at 0x10000 - 0x793D2200
AVI: ODML: Building ODML index (2 superindexchunks).
====== AVI Standard Index Header ========
  FCC (ix00) dwSize (32248) wLongsPerEntry(2)
  bIndexSubType (0) bIndexType (1)
  nEntriesInUse (4028) dwChunkId (00db)
  qwBaseOffset (0x1FC00) dwReserved3 (0)
===========================
====== AVI Standard Index Header ========
  FCC (ix00) dwSize (32248) wLongsPerEntry(2)
  bIndexSubType (0) bIndexType (1)
  nEntriesInUse (4028) dwChunkId (00db)
  qwBaseOffset (0x38D76800) dwReserved3 (0)
===========================
====== AVI Standard Index Header ========
  FCC (ix00) dwSize (32248) wLongsPerEntry(2)
  bIndexSubType (0) bIndexType (1)
  nEntriesInUse (4028) dwChunkId (00db)
  qwBaseOffset (0x71B51000) dwReserved3 (0)
===========================
====== AVI Standard Index Header ========
  FCC (ix00) dwSize (32248) wLongsPerEntry(2)
  bIndexSubType (0) bIndexType (1)
  nEntriesInUse (4028) dwChunkId (00db)
  qwBaseOffset (0xA6F9EC00) dwReserved3 (0)
===========================
====== AVI Standard Index Header ========
  FCC (ix00) dwSize (32248) wLongsPerEntry(2)
  bIndexSubType (0) bIndexType (1)
  nEntriesInUse (4028) dwChunkId (00db)
  qwBaseOffset (0xDFC4C800) dwReserved3 (0)
===========================
====== AVI Standard Index Header ========
  FCC (ix00) dwSize (32248) wLongsPerEntry(2)
  bIndexSubType (0) bIndexType (1)
  nEntriesInUse (4028) dwChunkId (00db)
  qwBaseOffset (0x118A1C000) dwReserved3 (0)
===========================
====== AVI Standard Index Header ========
  FCC (ix00) dwSize (32248) wLongsPerEntry(2)
  bIndexSubType (0) bIndexType (1)
  nEntriesInUse (4028) dwChunkId (00db)
  qwBaseOffset (0x1517E3A00) dwReserved3 (0)
===========================
====== AVI Standard Index Header ========
  FCC (ix00) dwSize (32248) wLongsPerEntry(2)
  bIndexSubType (0) bIndexType (1)
  nEntriesInUse (4028) dwChunkId (00db)
  qwBaseOffset (0x189679800) dwReserved3 (0)
===========================
====== AVI Standard Index Header ========
  FCC (ix00) dwSize (32248) wLongsPerEntry(2)
  bIndexSubType (0) bIndexType (1)
  nEntriesInUse (4028) dwChunkId (00db)
  qwBaseOffset (0x1C2408C00) dwReserved3 (0)
===========================
====== AVI Standard Index Header ========
  FCC (ix00) dwSize (32248) wLongsPerEntry(2)
  bIndexSubType (0) bIndexType (1)
  nEntriesInUse (4028) dwChunkId (00db)
  qwBaseOffset (0x1FB1D0400) dwReserved3 (0)
===========================
====== AVI Standard Index Header ========
  FCC (ix00) dwSize (32248) wLongsPerEntry(2)
  bIndexSubType (0) bIndexType (1)
  nEntriesInUse (4028) dwChunkId (00db)
  qwBaseOffset (0x233F9FC00) dwReserved3 (0)
===========================
====== AVI Standard Index Header ========
  FCC (ix00) dwSize (32248) wLongsPerEntry(2)
  bIndexSubType (0) bIndexType (1)
  nEntriesInUse (878) dwChunkId (00db)
  qwBaseOffset (0x26CD67600) dwReserved3 (0)
===========================
====== AVI Standard Index Header ========
  FCC (ix01) dwSize (32248) wLongsPerEntry(2)
  bIndexSubType (0) bIndexType (1)
  nEntriesInUse (1229) dwChunkId (01wb)
  qwBaseOffset (0x21B200) dwReserved3 (0)
===========================
====== AVI Standard Index Header ========
  FCC (ix01) dwSize (32248) wLongsPerEntry(2)
  bIndexSubType (0) bIndexType (1)
  nEntriesInUse (1216) dwChunkId (01wb)
  qwBaseOffset (0x10034EE00) dwReserved3 (0)
===========================
====== AVI Standard Index Header ========
  FCC (ix01) dwSize (32248) wLongsPerEntry(2)
  bIndexSubType (0) bIndexType (1)
  nEntriesInUse (574) dwChunkId (01wb)
  qwBaseOffset (0x2003CF600) dwReserved3 (0)
===========================
AVI index offset: 0x0 (movi=0x10000 idx0=0x1FBF8 idx1=0x1FBF8)
Auto-selected AVI video ID = 0
Auto-selected AVI audio ID = 1
Detected NON-INTERLEAVED AVI file format.
ChunkID mismatch! raw= idx=00db  
AVI: Searching for audio stream (id:1)
XXX initial  v_pts=0.000  a_pos=0 (0.000) 
AVI video size=10332979200 (45186) audio size=266275800 (66568950)
VIDEO:  []  320x240  24bpp  29.970 fps  54827.5 kbps (6692.8 kbyte/s)
Auto-selected AVI audio ID = 1
[V] filefmt:3  fourcc:0x0  size:320x240  fps:29.970  ftime:=0.0334
get_path('sub/') -> '/home/tehowe/.mplayer/sub/'
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
X11 opening display: :0.0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 3840x1080 with depth 24 and 32 bpp (":0.0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
[VO_XV] Using Xv Adapter #0 (ATI Radeon AVIVO Video)
[xv common] Drawing no colorkey.
[xv common] Maximum source image dimensions: 4096x4096
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 320 x 240 (preferred colorspace: BGR 24-bit)
Trying filter chain: vo
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale vo
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 320 x 240 (preferred colorspace: BGR 24-bit)
Trying filter chain: vo
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale vo
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 320 x 240 (preferred colorspace: BGR 24-bit)
Trying filter chain: vo
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale vo
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 320 x 240 (preferred colorspace: BGR 24-bit)
Trying filter chain: vo
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale vo
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 320 x 240 (preferred colorspace: BGR 24-bit)
Trying filter chain: vo
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale vo
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 320 x 240 (preferred colorspace: BGR 24-bit)
Trying filter chain: vo
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale vo
VDec: using BGR 24-bit as output csp (no 0)
Opening video filter: [flip]
Movie-Aspect is undefined - no prescaling applied.
VO Config (320x240->320x240,flags=8,'MPlayer',0x42475218)
[swscaler @ 0x22e9860]using unscaled bgr24 -> yuv420p special converter
REQ: flags=0x437  req=0x0  
REQ: flags=0x437  req=0x400  
VO: [xv] 320x240 => 320x240 Planar YV12 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x30323449 (I420) planar
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x59565955 (UYVY) packed
using Xvideo port 143 for hw scaling
Selected video codec: [rawbgr24flip] vfm: raw (RAW BGR24)
==========================================================================
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
dec_audio: Allocating 2048 + 65536 = 67584 bytes for output buffer.
AUDIO: 44100 Hz, 2 ch, s16le, 1411.2 kbit/100.00% (ratio: 176400->176400)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
Building audio filter chain for 44100Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 44100Hz/2ch/s16le
[dummy] Was reinitialized: 44100Hz/2ch/s16le
Trying preferred audio driver 'pulse', options '[none]'
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
AO: Description: PulseAudio audio output
AO: Author: Lennart Poettering
Building audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
[dummy] Was reinitialized: 44100Hz/2ch/s16le
[dummy] Was reinitialized: 44100Hz/2ch/s16le
Starting playback...
Increasing filtered audio buffer size from 0 to 46144
ChunkID mismatch! raw= idx=00db  
*** [scale] Exporting mp_image_t, 320x240x24bpp BGR packed, 230400 bytes
*** [vo] Allocating mp_image_t, 320x240x12bpp YUV planar, 115200 bytes
*** [flip] Direct Rendering mp_image_t, 320x240x12bpp YUV planar, 115200 bytes
Unicode font: 5103 glyphs.
Unicode font: 5103 glyphs.
Uninit audio filters...-0.001 ct: -0.067  95/ 95  0%  2%  0.1% 0 0 
[libaf] Removing filter dummy 
Uninit audio: pcm
Uninit video: raw
vo: uninit ...

Exiting... (Quit)

```

---

### Post by tehowe on 2011-01-21
Apparently AMD is putting out a new Catalyst driver, 11.1, on January 26th or thereabouts. 
 
Be the first to know: [[FONT=Calibri][SIZE=3][COLOR=#800080]http://feeds.amd.com/catalystlinux/[/COLOR][/SIZE][/FONT]]("http://feeds.amd.com/catalystlinux/")
 
Here's a rather optimistic report on bug fixes, and some explanation of why my experience has been so terrible: [http://www.downloadatoz.com/driver/articles/keep-away-from-amd-catalyst-10-12-bugs-amd-catalyst-11-1-upcoming.html](http://www.downloadatoz.com/driver/articles/keep-away-from-amd-catalyst-10-12-bugs-amd-catalyst-11-1-upcoming.html)
 
Release date report: [http://forums.amd.com/game/messageview.cfm?catid=279&threadid=145425](http://forums.amd.com/game/messageview.cfm?catid=279&threadid=145425)
 
So I guess I'll wait with bated breath with the rest of the community and see if that fixes the issues with overlay on 5850 and Ubuntu 10.10.
 
Failing that, I guess I can always give up, go out and get a GTX 470... bonus earplugs and saucepan to cook eggs on it not included. Though I see people complaining about (Nvidia overlay) vpdau support on the Phoronix forums as well, so I guess this is just part of the 'enthusiast' experience.

---

### Post by tehowe on 2011-01-27
The new 11.1 Radeon driver's out, I'll cover how my install went in this more suitable thread:

[http://ubuntuforums.org/showthread.php?p=10401979#post10401979](http://ubuntuforums.org/showthread.php?p=10401979#post10401979)

---

### Post by hugmenot on 2011-01-27
install and run vainfo.

That determines if H264 accel is enabled.

Then you need to configure mplayer to use vaapi:

mplayer -vo vaapi -va vaapi filetoplay.mp4

---

### Post by tehowe on 2011-01-28
Here's what I get from vainfo

libva: libva version 0.31.1-sds1
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/fglrx_drv_video.so
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_openDriver() returns 0
vainfo: VA API version: 0.31
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8.pre1
vainfo: Supported profile and entrypoints
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileVC1Advanced            :    VAEntrypointVLD


I'm getting over 9000 fps in glx gears so the new Catalyst driver seems to be working. But VA-API? Not so much. I've tried going though the instructions on all of these pages, in order...

[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Hardware_Video_Decode_Acceleration_.28EXPERIMENTAL.29](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Hardware_Video_Decode_Acceleration_.28EXPERIMENTAL.29)

[http://www.splitted-desktop.com/~gbeauchesne/libva/](http://www.splitted-desktop.com/~gbeauchesne/libva/)
[http://www.splitted-desktop.com/~gbeauchesne/xvba-video/](http://www.splitted-desktop.com/~gbeauchesne/xvba-video/)
[http://www.splitted-desktop.com/~gbeauchesne/mplayer-vaapi/](http://www.splitted-desktop.com/~gbeauchesne/mplayer-vaapi/)  (also apparently patches ffmpeg)

The above links were the closest thing to best practices I could find online to get vaapi installed. And with some hiccups, things seemed to go in (eg; building mplayer complained about some 'yasm' compiler not being installed half way through, so I did an apt-get for yasm and tried again...)

Now, running a command like

> ~/Downloads/mplayer-vaapi/mplayer -vo vaapi -va vaapi MOVIE.avi

Brings up the special version of mplayer but it's extremely flickery and picks and chooses what formats it wants to play.

Using the flag for GL

> ~/Downloads/mplayer-vaapi/mplayer -vo vaapi:gl -va vaapi MOVIE.avi

Results in a slew of errors that indicates video_out is broken

> MPlayer SVN-r32819-4.4.5 (C) 2000-2011 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing 2007_AikidoClass.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
AVI: ODML: Building ODML index (2 superindexchunks).
Detected NON-INTERLEAVED AVI file format.
VIDEO:  []  320x240  24bpp  29.970 fps  54827.5 kbps (6692.8 kbyte/s)
Load subtitles in ./
[vo_vaapi] Using OpenGL rendering
libva: libva version 0.31.1-sds1
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/fglrx_drv_video.so
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_openDriver() returns 0
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Opening video filter: [flip]
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0x185a0a0] using unscaled bgr24 -> yuv420p special converter
VO: [vaapi] 320x240 => 320x240 Planar YV12 
[vo_vaapi] vaCreateSurfaceGLX(): resource allocation failed
FATAL: Cannot initialize video driver.
VDecoder init failed :(
Opening video decoder: [raw] RAW Uncompressed Video
Opening video filter: [flip]
Movie-Aspect is undefined - no prescaling applied.
VO: [vaapi] 320x240 => 320x240 Planar YV12 
mplayer: ../../src/xcb_io.c:452: _XReply: Assertion `!dpy->xcb->reply_data' failed.


MPlayer interrupted by signal 6 in module: init_video_codec
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.


So, I don't know... VLCPlayer still won't work with Hardware acceleration enabled. The FFMpeg patching doesn't seem to enable PiTiVi to play any video and there's no instructions on how to compile the gstreamer patch at [http://www.splitted-desktop.com/~gbeauchesne/gstreamer-vaapi/](http://www.splitted-desktop.com/~gbeauchesne/gstreamer-vaapi/)

Maybe forcibly inserting this XFree86-DRI file into the system somewhere would help. But synaptic says libxxf86vm1 is already installed! Help, anyone please? I just want to play and edit video on this high end box I bought and it's making it very difficult :confused:

---

### Post by hugmenot on 2011-01-28
Perhaps you should try this new mplayer daily PPA:
[https://launchpad.net/~motumedia/+archive/mplayer-daily](https://launchpad.net/~motumedia/+archive/mplayer-daily)

---

### Post by hugmenot on 2011-01-28
Also, what is in 2007_AikidoClass.avi?

This doesn’t look like an H.264 video at all. Video accel only works for H.264 on your card, as vainfo has told you.

And I haven’t used an ATI card before, but Xfree86 intuitively sounds wrong.

---

### Post by tehowe on 2011-01-28
> **hugmenot said:**
> Perhaps you should try this new mplayer daily PPA:
[https://launchpad.net/~motumedia/+archive/mplayer-daily]("https://launchpad.net/%7Emotumedia/+archive/mplayer-daily")

Are they building VAAPI support in now?

I got gstreamer-vaapi to compile btw by entering

> apt-get install [libgstreamer0.10-dev]("http://packages.ubuntu.com/libgstreamer0.10-dev") [libgstreamer-plugins-base0.10-dev]("http://packages.ubuntu.com/libgstreamer-plugins-base0.10-dev")

before ./configure

gstreamer-vaapi then installs okay but not video! For any container. Hopefully there's some simple thing tying all these issues together.

---

### Post by tehowe on 2011-01-28
> **hugmenot said:**
> Also, what is in 2007_AikidoClass.avi?

This doesn’t look like an H.264 video at all. Video accel only works for H.264 on your card, as vainfo has told you.

And I haven’t used an ATI card before, but Xfree86 intuitively sounds wrong.

Okay, I tried this one instead which is h.264

> ~/Downloads/mplayer-vaapi/mplayer -vo vaapi -va vaapi 2007_AikidoClass_h264.mov

That reulted in sound, but no video and a lot of this line repeated

[vo_vaapi] vaPutSurface(): resource allocation failed
xvba_video: XVBA_CreateGLSharedSurface(): status 11% 11%  0.1% 3 0

So I tried the GL flag as well and no dice...

> ~/Downloads/mplayer-vaapi/mplayer -vo vaapi:gl -va vaapi 2007_AikidoClass_h264.mov

MPlayer SVN-r32819-4.4.5 (C) 2000-2011 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing 2007_AikidoClass_h264.mov.
libavformat file format detected.
[lavf] stream 0: audio (pcm_s16le), -aid 0, -alang eng
[lavf] stream 1: video (h264), -vid 0
VIDEO:  [H264]  720x480  24bpp  24.000 fps  2030.2 kbps (247.8 kbyte/s)
Clip info:
 major_brand: qt  
 minor_version: 537199360
 compatible_brands: qt  
 creation_time: 2008-06-04 03:24:41
Load subtitles in ./
[vo_vaapi] Using OpenGL rendering
libva: libva version 0.31.1-sds1
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/fglrx_drv_video.so
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_openDriver() returns 0
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[VD_FFMPEG] VA API accelerated codec.
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 0.0 kbit/0.00% (ratio: 0->176400)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
[AO OSS] audio_setup: Can't open audio device /dev/dsp: No such file or directory
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
Unsupported PixelFormat 61
[VD_FFMPEG] Trying pixfmt=1.
Movie-Aspect is undefined - no prescaling applied.
VO: [vaapi] 720x480 => 720x480 H.264 VA-API Acceleration 
[vo_vaapi] vaCreateSurfaceGLX(): resource allocation failed
FATAL: Cannot initialize video driver.
Unsupported PixelFormat 61
[VD_FFMPEG] Trying pixfmt=0.
Unsupported PixelFormat 61
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
[VD_FFMPEG] Trying pixfmt=2.
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
[VD_FFMPEG] Trying pixfmt=3.
Movie-Aspect is undefined - no prescaling applied.
VO: [vaapi] 720x480 => 720x480 Planar YV12 
mplayer: ../../src/xcb_io.c:452: _XReply: Assertion `!dpy->xcb->reply_data' failed.

Oh well, got to head off to work, put in another night on this tonight I guess.

---

### Post by BicyclerBoy on 2011-01-28
Go back to the beginning & go step by step.

vainfo tells you the video acceleration is not possible because dri module did not load.
Video decode is not GLX 3d.
Video presentation acc need dri loaded.

I don't know how ATI driver provides VA-API.

---

### Post by tehowe on 2011-02-01
> **BicyclerBoy said:**
> Go back to the beginning & go step by step.

vainfo tells you the video acceleration is not possible because dri module did not load.
Video decode is not GLX 3d.
Video presentation acc need dri loaded.

I don't know how ATI driver provides VA-API.

I'd come to this conclusion as well - the Catalyst driver only deals with 3D OpenGL, and to get gstreamer working properly eg; to use PiTiVi I'd need to install the VA-API 2D acceleration driver layer. That's not quite working yet.

So I'm not sure where the beginning is in this case but looking at our best guess so far as to the culprit

> Xlib:  extension "XFree86-DRI" missing on display ":0.0".

I'd Google the name of the driver and end up finding dispiriting threads like this one from [a guy with the same problem back in 2007]("http://www.linuxforums.org/forum/gentoo-linux/101617-notorious-xfree86-dri-missing-problem.html"). 
It wasn't even clear what DRI was until I found the developer's website here

[http://dri.freedesktop.org/wiki/](http://dri.freedesktop.org/wiki/) or is it here
[http://www.x.org/wiki/](http://www.x.org/wiki/) as 2D drivers were pushed upstream by the DRI project

So what does this mean? Should I consider a forced reinstall of Mesa? X? I think figuring out what package contains XFree86-DRI is probably my next step. I'm a former Windows user, dammit - please tell me what I should reinstall. :D

---

### Post by BicyclerBoy on 2011-02-02
Sorry I don't know for ATI/AMD GPU.
Those other posters are the experts.
I just know it's broken.

---

### Post by tehowe on 2011-02-09
> **BicyclerBoy said:**
> Sorry I don't know for ATI/AMD GPU.
Those other posters are the experts.
I just know it's broken.

I don't know - has anyone had a painless experience for video playing/editing with an NVIDIA GTX-470 or GTX-480? If so, I may just go buy one. Even if it is loud and hot.

But I may not need to as mysteriously Mplayer/Totem started playing a very few selected file formats... It still won't play an .avi but I accidentally played a .mov video encoded with h.264 and this time around, it worked!

The only thing I can think of is that I launched KDEnlive a few minutes prior and closed it again. Could it have sorted something out? 

SMPlayer now has a 'vaapi' entry under output drivers, and works though I'll stick with VLC as it's faster for video playback for now.

The only obstacle then to Ubuntu bliss is to get PiTiVi or equivalent working. I figured PiTiVi should be the easiest one to get going as it runs off of Gstreamer, so I went and compiled and installed the gstreamer-vaapi driver, which was easier than I thought despite the fact the author didn't include compile instructions on that page, a standard ./configure, make, and sudo checkinstall worked fine.

However when I drag the h264 video onto PiTiVi it says "No packages with the requested plugins found. The requested plugins are: video/x-vaapi-surface-encoder"

Dragging an .mts file, or AVCHD as it's otherwise known, over to PiTiVi resulted in 

> URI:00045-9CE13D9B.MTS
Problem:An internal error occurred while analyzing this file: Internal data flow error.
Extra information:gstbasesrc.c(2550): gst_base_src_loop (): /GstPipeline:Discoverer-file:///media/Data/Media/Video/20101227_ScienceCentre/00045-9CE13D9B.MTS/GstFileSrc:src-file:///media/Data/Media/Video/20101227_ScienceCentre/00045-9CE13D9B.MTS:
streaming task paused, reason not-negotiated (-4)

I think I'm getting closer. It may not look it, but since Ubuntu sees fit to start working arbitrarily I feel entitled to to have a gut feeling about it. :p

---

### Post by BicyclerBoy on 2011-02-10
Every nvidia/mythtv XBMC user has had mostly painless experiences of HD video playback for the last 2 years.

I have only used PiTiVi for mpeg2 video files..

Editing is not the same as playing when you are using hardware for video decode playback..
All the VAAPI stuff is a waste of time for editing..& 2nd rate for playback.
It only lets you reduce the CPU load.
The best playback PQ comes from VDPAU or full CPU decode with post-filters.

The FOSS for non-linear editing of H264 using video GPU for decode/encode is a way off.
So a over-powered GPU may be pointless, you are better off with 64 bit multi-core & lots of RAM.
Nvidia GPU Vdpau may not go faster than x2.. an i5 CPU should do x4 real-time.

Some argue the gains are will never be so great due to volume of data to move back out the frame buffer to system RAM.

H264 video is highly compressed & it is only easy to cut at a key (I) frame.
Converting video to an intermediate format of all I frames will be faster to edit but huge!
AFAIK Professional non-linear video editing is not done using H264.

AVI is just a container & not a very good one for seeking.
m2ts is the container commonly used by handi-cams.

From what I have read, the data streams made by the some cameras are not correct, bad time info non-monotonic time stamps etc..

Did you try to re-mux the files with VLC or ffmpeg into the same container ?

I have an idea that ffmpeg will not re-mux with (-vcodec copy) H264 full-stop.

---

### Post by tehowe on 2011-02-17
> **BicyclerBoy said:**
> Every nvidia/mythtv XBMC user has had mostly painless experiences of HD video playback for the last 2 years.

I have only used PiTiVi for mpeg2 video files..
...
The FOSS for non-linear editing of H264 using video GPU for decode/encode is a way off.
So a over-powered GPU may be pointless, you are better off with 64 bit multi-core & lots of RAM.
Nvidia GPU Vdpau may not go faster than x2.. an i5 CPU should do x4 real-time.
...
AFAIK Professional non-linear video editing is not done using H264.

AVI is just a container & not a very good one for seeking.
m2ts is the container commonly used by handi-cams.


I'll try that, thanks. Happily, I did buy a fast CPU, the only PITA is that I've several gigs of video to edit, batch converting (remuxing) them to a seperate location is going to be huge in MPEG2. Time for a new drive...

> All the VAAPI stuff ... only lets you reduce the CPU load.
The best playback PQ comes from VDPAU or full CPU decode with post-filters.

I infer that there's some functional difference between VA-API and VDPAU then? I thought they did the same thing but had different levels of support.

> From what I have read, the data streams made by the some cameras are not correct, bad time info non-monotonic time stamps etc..

I hope that's not the case with this Sony. Or maybe it's set up this way to force you to buy Vegas :/

---

### Post by BicyclerBoy on 2011-02-17
I'm not sure/don't know what the best video format is for editing..

The editing problem with H264 is that cuts can only be made at I frames unless you recompute a new I frame & following P & B frames.
Maybe a H264 format with no B frames ?

Cinelerra looks to be the most powerful Linux video editing app.

AFAIK
VA-API playback with VLC (for example) can not control the feature set C VDPAU options of hqscaling, denoise, sharpen, colorspace or buffersize.

I think VLC with full CPU decode is far superior to VA-API cos you can use yadifx2 lancroz or bicubic scaling & other filters etc.

I think it is possible that some of the non-monotonic data packet errors could be just poorly (simple) implemented parsing/demuxing.

---

