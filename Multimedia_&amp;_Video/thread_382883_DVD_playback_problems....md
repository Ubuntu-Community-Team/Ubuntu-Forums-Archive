---
title: "DVD playback problems..."
date: 2007-03-12
forum: Multimedia &amp; Video
---

### Post by vkkim on 2007-03-12
So I had set up DVD playback using Automatix a long time ago, but I never had the chance to actually play one until now.  I am using a fully updated Edgy install.  It doesn't look like it is a decoding issue as all the CSS keys are properly retrieved, but rather something with X.  Any help would be greatly appreciated.  Here are the outputs of various programs when I try to play a DVD:

Totem (with totem-xine):
```
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 89 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

VLC:
```
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  85
  Current serial number in output stream:  86

```

MPlayer:
```
Playing dvd://.
Reading disc structure, please wait...
There are 22 titles on this DVD.
There are 2 chapters in this DVD title.
There are 1 angles in this DVD title.
DVD successfully opened.
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 3)  29.970 fps  9800.0 kbps (1225.0 kbyte/s)
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
AC3: 2.0 (dolby)  48000 Hz  192.0 kbit/s
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
open: No such file or directory
Couldn't open: /dev/mga_vid
open: No such file or directory
Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
alsa-init: using device default
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 854x480 Planar YV12 
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0 


MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

```

---

### Post by jackrobinson on 2007-03-12
I would say reinstall automatix2 and install the DVD package again. It might have some updates and resolve your issue.

---

### Post by vkkim on 2007-03-12
The same error messages happen...

---

### Post by panch0 on 2007-03-13
Do you get this for DVD only? Can you play video files like avi or mpg?

What happens if you try

mplayer -vo x11 dvd://

---

### Post by vkkim on 2007-03-13
I can play every other type of video file.  But when I do 

mplayer -vo x11 dvd://

it works!!!  So how do I do this permanently for other programs (preferably system-wide)?

Also, it does not full-screen when I am playing with that command.

---

### Post by panch0 on 2007-03-14
Well the X11 video output is actually not great at all, it slows your system down a whole lot, and you will be getting a/v desync on many movies. The best you can do is try to enable the XVideo extension on your X server. To start with run

xvinfo

and post the output you get.

---

### Post by vkkim on 2007-03-14
Thanks for helping out...

```
X-Video Extension version 2.2
screen #0
  Adaptor #0: "Intel(R) Video Overlay"
    number of ports: 1
    port base: 73
    operations supported: PutImage 
    supported visuals:
      depth 24, visualID 0x23
      depth 24, visualID 0x24
      depth 24, visualID 0x25
      depth 24, visualID 0x26
      depth 24, visualID 0x27
      depth 24, visualID 0x28
      depth 24, visualID 0x29
      depth 24, visualID 0x2a
    number of attributes: 10
      "XV_COLORKEY" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 66051)
      "XV_BRIGHTNESS" (range -128 to 127)
              client settable attribute
              client gettable attribute (current value is -58)
      "XV_CONTRAST" (range 0 to 255)
              client settable attribute
              client gettable attribute (current value is 86)
      "XV_DOUBLE_BUFFER" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
      "XV_GAMMA0" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 526344)
      "XV_GAMMA1" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 1052688)
      "XV_GAMMA2" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 2105376)
      "XV_GAMMA3" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 4210752)
      "XV_GAMMA4" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 8421504)
      "XV_GAMMA5" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 12632256)
    maximum XvImage size: 1920 x 1080
    Number of image formats: 4
      id: 0x32595559 (YUY2)
        guid: 59555932-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x32315659 (YV12)
        guid: 59563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x30323449 (I420)
        guid: 49343230-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x59565955 (UYVY)
        guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
  Adaptor #1: "Intel(R) Textured Video"
    number of ports: 16
    port base: 74
    operations supported: PutImage 
    supported visuals:
      depth 24, visualID 0x23
      depth 24, visualID 0x24
      depth 24, visualID 0x25
      depth 24, visualID 0x26
      depth 24, visualID 0x27
      depth 24, visualID 0x28
      depth 24, visualID 0x29
      depth 24, visualID 0x2a
    number of attributes: 2
      "XV_BRIGHTNESS" (range -128 to 127)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_CONTRAST" (range 0 to 255)
              client settable attribute
              client gettable attribute (current value is 0)
    maximum XvImage size: 2048 x 2048
    Number of image formats: 4
      id: 0x32595559 (YUY2)
        guid: 59555932-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x32315659 (YV12)
        guid: 59563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x30323449 (I420)
        guid: 49343230-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x59565955 (UYVY)
        guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)

```

---

### Post by panch0 on 2007-03-14
Hmm... I don't see anything wrong with your xvideo, so maybe you should run

mplayer -v -vo xv dvd://

and post the output on the mplayer-users list, so someone can give you a hand with this.

In the meantime you can run MPlayer full screen like this:

mplayer -vo x11 -fs -zoom dvd://

Or get KPlayer which is a very nice GUI for MPlayer and tell it to use the X11 video output under Settings - Configure KPlayer - Video if the XVideo output still doesn't work.

---

### Post by binneypl on 2007-03-27
I am suffering the same sort of problem and not even your [FONT="Courier New"]mplayer -vo x11 dvd://[/FONT] solution seems to work.

I'm staggered that it is so hard to find an fix for this, and regret I have to go on using Windows which runs everything fine on the same laptop (see [my original thread]("http://ubuntuforums.org/showthread.php?t=327030")).

I've tried totem and VLC - both of which fail with 'BadAlloc (insufficient resources for operation)'.

mplayer just flashes and crashes. Sample run below:

```
peter@toshGCb:~$ mplayer -v -vo xv dvd://
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Celeron 2/Pentium III Coppermine,Geyserville (Family: 6, Stepping: 3)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.


get_path('codecs.conf') -> '/home/peter/.mplayer/codecs.conf'
Reading /home/peter/.mplayer/codecs.conf: Can't open '/home/peter/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: 91 audio & 204 video codecs
CommandLine: '-v' '-vo' 'xv' 'dvd://'
init_freetype
get_path('font/font.desc') -> '/home/peter/.mplayer/font/font.desc'
font: can't open file: /home/peter/.mplayer/font/font.desc
font: can't open file: /usr/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Using nanosleep() timing
get_path('input.conf') -> '/home/peter/.mplayer/input.conf'
Can't open input config file /home/peter/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 59 binds
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
get_path('.conf') -> '/home/peter/.mplayer/.conf'
Playing dvd://.
get_path('sub/') -> '/home/peter/.mplayer/sub/'
URL: dvd://
libdvdread: Using libdvdcss version 1.2.9 for DVD access
Reading disc structure, please wait...
There are 1 titles on this DVD.
There are 2 chapters in this DVD title.
There are 1 angles in this DVD title.
Please send bug report - no VTS_TMAPT ??

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000143
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0
DVD successfully opened.
[open] audio stream: 0 audio format: ac3 (stereo) language: en aid: 128
[open] number of audio channels on disk: 1.
[open] number of subtitles on disk: 0
DVD start cell: 0  pack: 0x0-0x80
DVD start=0 end=128
STREAM: [null] dvd://
STREAM: Description: DVD stream
STREAM: Author:
STREAM: Comment:
DVD Seek! lba=0x0  cell=0  packs: 0x0-0x80
Angle-seek synced by cell/vob IDN search!
Checking for YUV4MPEG2
ASF_check: not ASF guid!
Checking for NuppelVideo
Checking for REAL
Checking for SMJPEG
Searching demuxer type for filename dvd:// ext: (null)
DVD Seek! lba=0x0  cell=0  packs: 0x0-0x80
Angle-seek synced by cell/vob IDN search!
Checking for Nullsoft Streaming Video
DVD Seek! lba=0x0  cell=0  packs: 0x0-0x80
Angle-seek synced by cell/vob IDN search!
Checking for MOV
Checking for VIVO
header block 1 size: 0
AVS: avs_check_file - attempting to open file dvd://
AVS: File is too big, aborting...
Checking for PVA
Checking for MPEG-TS...
TRIED UP TO POSITION 86338, FOUND 47, packet_size= 0, SEEMS A TS? 0
DVD Seek! lba=0x2A  cell=0  packs: 0x0-0x80
Angle-seek synced by cell/vob IDN search!
DVD Seek! lba=0x0  cell=0  packs: 0x0-0x80
Angle-seek synced by cell/vob IDN search!
Checking for LMLM4 Stream Format
Invalid packet in LMLM4 stream: ch=0 size=1140851708
LMLM4 Stream Format not found
system stream synced at 0xD (13)!
==> Found video stream: 0
MPEG-PS file format detected.
==> Found audio stream: 128
Searching for sequence header... OK!
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  8000.0 kbps (1000.0 kbyte/s)
[V] filefmt:2  fourcc:0x10000002  size:720x576  fps:25.00  ftime:=0.0400
get_path('sub/') -> '/home/peter/.mplayer/sub/'
get_path('default.sub') -> '/home/peter/.mplayer/default.sub'
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
dec_audio: Allocating 3840 bytes for input buffer.
dec_audio: Allocating 6144 + 65536 = 71680 bytes for output buffer.
Using SSE optimized IMDCT transform
AC3: 2.0 (stereo)  48000 Hz  192.0 kbit/s
A52 flags before a52_frame: 0x2A
A52 flags after a52_frame: 0x2
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
X11 opening display: :0.0
vo: X11 color mask:  FFFF  (R:F800 G:7E0 B:1F)
vo: X11 running at 1280x1024 with depth 16 and 16 bpp (":0.0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
Disabling DPMS
DPMSDisable stat: 1
[xv common] Drawing colorkey manually.
[xv common] Using colorkey from Xv (0x00083e).
[xv common] Maximum source image dimensions: 1024x1024
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Trying filter chain: vo
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale vo
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
alsa-init: requested format: 48000 Hz, 2 channels, 9
alsa-init: compiled for ALSA-1.0.10
alsa-init: setup for 1/2 channel(s)
alsa-init: 1 soundcard found, using: default
alsa-init: pcm opend in block-mode
alsa-init: chunksize set to 1024
alsa-init: fragcount=16
alsa-init: got buffersize=65536
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
AO: Description: ALSA-0.9.x-1.x audio output
AO: Author: Alex Beregszaszi, Zsolt Barat <joy@streamminister.de>
AO: Comment: under developement
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
Starting playback...
alsa-space: free space = 65536, prepared --
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
Trying filter chain: vo
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO Config (720x576->1024x576,flags=0,'MPlayer',0x32315659)
VO: [xv] 720x576 => 1024x576 Planar YV12
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x30323449 (I420) planar
Xvideo image format: 0x35315652 (RV15) packed
Xvideo image format: 0x36315652 (RV16) packed
Xvideo image format: 0x31313259 (Y211) packed
using Xvideo port 64 for hw scaling
[xv] dx: 0 dy: 0 dw: 1024 dh: 614
*** [vo] Allocating mp_image_t, 720x576x12bpp YUV planar, 622080 bytes
[xv] dx: 0 dy: 0 dw: 1024 dh: 614
alsa-space: xrun of at least 1305.367 msecs. resetting stream% 1 0
alsa-space: free space = 0, xrun --
--- END OF CELL !!! ---
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)
EOF code: 1   0.0 A-V:  0.654 ct:  0.004   1/  1 ??% ??% ??,?% 1 0

Uninit audio filters...
[libaf] Removing filter dummy
uninit audio: liba52
uninit video: libmpeg2
Successfully enabled DPMS
alsa-uninit: pcm closed
vo: uninit ...

Exiting... (End of file)
peter@toshGCb:~$

```

---

