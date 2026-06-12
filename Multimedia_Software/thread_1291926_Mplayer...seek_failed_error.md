---
title: "Mplayer...seek failed error?"
date: 2009-10-15
forum: Multimedia Software
---

### Post by oxf on 2009-10-15
HI,

I sure this is something fairly basic. I added Mplayer and am trying to play a DVD. When I click on play I get "seek failed" error. So it seems not to find the DVD. Any ideas?
Thanks

---

### Post by oxf on 2009-10-16
bump

---

### Post by oxf on 2009-10-16
OK I presume the fact that no ones answering this is because I've provided insufficient information on the problem. Theres not much more I can give but tell me what info to provide and I will. To reiterate:

DVD's play fine using the default player shipped with Jaunty, i.e. Totum.
But when I added MPlayer I get this error "seek failed" for the drive. I'm wondering if I did not install all the required packages perhaps?

What should I do next?

---

### Post by andrew.46 on 2009-10-16
Hi oxf,

> **oxf said:**
> OK I presume the fact that no ones answering this is because I've provided insufficient information on the problem.

Could you try disabling all desktop effects and running:

```
mplayer -v dvd://
```

This should hopefully generate a detailed look at the error.

Andrew

---

### Post by mc4man on 2009-10-16
I think the repo mplayer (gmplayer) will default to /dev/dvd so if nothing becomes apparent then ck. on the dev links of your drive

```
sudo lshw -C disk
```

---

### Post by oxf on 2009-10-16
> **andrew.46 said:**
> Hi oxf,



Could you try disabling all desktop effects and running:

```
mplayer -v dvd://
```This should hopefully generate a detailed look at the error.

Andrew

Thanks Andrew! Running that with the DVD inserted starts Mplayer running The Code is below. However, I seem to have limited funtions available and only way to pause it is to exit. 

Mike.

mbdb@M2000:~$ mplayer -v dvd://
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: AMD Turion(tm) 64 Mobile Technology ML-30 (Family: 15, Model: 36, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/mbdb/.mplayer/codecs.conf'
Reading /home/mbdb/.mplayer/codecs.conf: Can't open '/home/mbdb/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --enable-runtime-cpudetection --target=i586-linux --prefix=/usr --confdir=/etc/mplayer --mandir=/usr/share/man --win32codecsdir=/usr/lib/win32 --enable-largefiles --disable-libdvdcss-internal --enable-smb --enable-ftp --enable-cdparanoia --enable-radio --enable-lirc --enable-joystick --enable-xf86keysym --disable-tremor-internal --enable-liba52 --enable-musepack --enable-speex --enable-libvorbis --enable-mad --enable-mp3lib --enable-theora --enable-libdv --enable-libmpeg2 --enable-tv-v4l2 --enable-alsa --enable-ossaudio --enable-esd --enable-pulse --enable-nas --enable-xinerama --enable-menu --enable-xv --enable-vm --enable-gl --enable-xmga --enable-mga --enable-3dfx --enable-tdfxfb --enable-sdl --enable-aa --enable-caca --enable-dxr3 --enable-xvmc --with-xvmclib=XvMCW --enable-ggi --enable-fbdev --disable-ivtv --enable-freetype --enable-gif --enable-png --enable-jpeg --enable-liblzo --enable-fribidi --enable-ladspa --enable-gui --enable-mencoder
CommandLine: '-v' 'dvd://'
init_freetype
get_path('font/font.desc') -> '/home/mbdb/.mplayer/font/font.desc'
font: can't open file: /home/mbdb/.mplayer/font/font.desc
font: can't open file: /usr/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/mbdb/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/mbdb/.mplayer/input.conf'
Can't open input config file /home/mbdb/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 81 binds
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('.conf') -> '/home/mbdb/.mplayer/.conf'

Playing dvd://.
get_path('sub/') -> '/home/mbdb/.mplayer/sub/'
URL: dvd://
Reading disc structure, please wait...
There are 2 titles on this DVD.
There are 6 chapters in this DVD title.
There are 1 angles in this DVD title.
DVD successfully opened.
audio stream: 0 format: ac3 (stereo) language: en aid: 128.
number of audio channels on disk: 1.
number of subtitles on disk: 0
DVD start cell: 0  pack: 0x0-0x1268  
DVD start=0 end=33252  
STREAM: [null] dvd://
STREAM: Description: DVD stream
STREAM: Author: 
STREAM: Comment: 
DVD Seek! lba=0x0  cell=0  packs: 0x0-0x1268  
Angle-seek synced by cell/vob IDN search!  
system stream synced at 0xD (13)!
==> Found video stream: 0
MPEG-PS file format detected.
==> Found audio stream: 128
Searching for sequence header... OK!
VIDEO:  MPEG2  720x576  (aspect 2)  25.000 fps  7000.0 kbps (875.0 kbyte/s)
[V] filefmt:2  fourcc:0x10000002  size:720x576  fps:25.00  ftime:=0.0400
get_path('sub/') -> '/home/mbdb/.mplayer/sub/'
X11 opening display: :0.0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1024x768 with depth 24 and 32 bpp (":0.0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
[xv common] Drawing colorkey manually.
[xv common] Using colorkey from Xv (0x010203).
[xv common] Maximum source image dimensions: 2048x2048
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Trying filter chain: vo
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale vo
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
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
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
AO: Description: PulseAudio audio output
AO: Author: Lennart Poettering
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
Starting playback...
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
Trying filter chain: vo
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO Config (720x576->768x576,flags=0,'MPlayer',0x32315659)
VO: [xv] 720x576 => 768x576 Planar YV12 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x41424752 (RGBA) packed
Xvideo image format: 0x54424752 (RGBT) packed
Xvideo image format: 0x32424752 (RGB2) packed
Xvideo image format: 0x0 (    ) packed
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x59565955 (UYVY) packed
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x30323449 (I420) planar
using Xvideo port 57 for hw scaling
[xv] dx: 0 dy: 0 dw: 768 dh: 576
*** [vo] Allocating mp_image_t, 720x576x12bpp YUV planar, 622080 bytes
[xv] dx: 128 dy: 96 dw: 768 dh: 576
*** [vo] Allocating mp_image_t, 720x576x12bpp YUV planar, 622080 bytes
get_path('subfont.ttf') -> '/home/mbdb/.mplayer/subfont.ttf'?% 1 0 
Unicode font: 5009 glyphs.
*** [vo] Allocating (slices) mp_image_t, 720x576x12bpp YUV planar, 622080 bytes
--- END OF CELL !!! ----0.008 ct:  0.091 256/256 12%  0%  2.0% 2 0 
DVD next cell: 1  pack: 0x1269-0x235F  
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
Trying filter chain: vo
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO Config (720x576->768x576,flags=0,'MPlayer',0x32315659)
VO: [xv] 720x576 => 768x576 Planar YV12 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x41424752 (RGBA) packed
Xvideo image format: 0x54424752 (RGBT) packed
Xvideo image format: 0x32424752 (RGB2) packed
Xvideo image format: 0x0 (    ) packed
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x59565955 (UYVY) packed
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x30323449 (I420) planar
using Xvideo port 57 for hw scaling
[xv] dx: 0 dy: 0 dw: 768 dh: 576
[xv] dx: 128 dy: 96 dw: 768 dh: 576
--- END OF CELL !!! --- 0.003 ct:  0.090 470/470 11%  1%  1.8% 2 0 
DVD next cell: 2  pack: 0x2360-0x5DC0  
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
Trying filter chain: vo
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO Config (720x576->768x576,flags=0,'MPlayer',0x32315659)
VO: [xv] 720x576 => 768x576 Planar YV12 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x41424752 (RGBA) packed
Xvideo image format: 0x54424752 (RGBT) packed
Xvideo image format: 0x32424752 (RGB2) packed
Xvideo image format: 0x0 (    ) packed
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x59565955 (UYVY) packed
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x30323449 (I420) planar
using Xvideo port 57 for hw scaling
[xv] dx: 0 dy: 0 dw: 768 dh: 576
[xv] dx: 128 dy: 96 dw: 768 dh: 576
[xv] dx: 128 dy: 96 dw: 768 dh: 5760.104 664/664 13%  4%  2.0% 2 0 
[xv] dx: 128 dy: 96 dw: 768 dh: 5760.095 889/889 15%  7%  2.0% 4 0 
--- END OF CELL !!! --- 0.013 ct:  0.092 1244/1244 17%  7%  2.2% 4 0 
DVD next cell: 3  pack: 0x5DC1-0x69AB  
--- END OF CELL !!! --- 0.013 ct:  0.093 1396/1396 16%  7%  2.1% 4 0 
DVD next cell: 4  pack: 0x69AC-0x81AB  
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
Trying filter chain: vo
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO Config (720x576->768x576,flags=0,'MPlayer',0x32315659)
VO: [xv] 720x576 => 768x576 Planar YV12 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x41424752 (RGBA) packed
Xvideo image format: 0x54424752 (RGBT) packed
Xvideo image format: 0x32424752 (RGB2) packed
Xvideo image format: 0x0 (    ) packed
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x59565955 (UYVY) packed
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x30323449 (I420) planar
using Xvideo port 57 for hw scaling
[xv] dx: 0 dy: 0 dw: 768 dh: 576
[xv] dx: 128 dy: 96 dw: 768 dh: 576
[xv] dx: 128 dy: 96 dw: 768 dh: 5760.097 1598/1598 17%  8%  2.1% 4 0 
Uninit audio filters... 0.002 ct:  0.094 1685/1685 17%  8%  2.1% 4 0 
[libaf] Removing filter dummy 
Uninit audio: liba52
Uninit video: libmpeg2
GNOME screensaver enabled
vo: uninit ...

Exiting... (Quit)
mbdb@M2000:~$

---

### Post by andrew.46 on 2009-10-17
Hi Mike,

You are using a reasonable venerable version of MPlayer but I note that on your terminal output here:

```
Playing dvd://.
get_path('sub/') -> '/home/mbdb/.mplayer/sub/'
URL: dvd://
Reading disc structure, please wait...
There are 2 titles on this DVD.
There are 6 chapters in this DVD title.
There are 1 angles in this DVD title.
DVD successfully opened.
```

you are missing any reference to libdvdread and libdvdcss, normally required for commercial dvd playback. On my own copy (which is a bit more recent than yours) the following is more usually seen:

```
Playing dvd://.
get_path('sub/') -> '/home/andrew/.mplayer/sub/'
URL: dvd://
**[COLOR="Red"]libdvdread: Using libdvdcss version 1.2.10 for DVD access[/COLOR]**
Reading disc structure, please wait...
There are 9 titles on this DVD.
There are 1 angles in this DVD title.

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient
```

Have you installed libdvdread and libdvdcss? 

Andrew

---

### Post by oxf on 2009-10-17
> **andrew.46 said:**
> Hi Mike,

You are using a reasonable venerable version of MPlayer but I note that on your terminal output here:

```
Playing dvd://.
get_path('sub/') -> '/home/mbdb/.mplayer/sub/'
URL: dvd://
Reading disc structure, please wait...
There are 2 titles on this DVD.
There are 6 chapters in this DVD title.
There are 1 angles in this DVD title.
DVD successfully opened.
```you are missing any reference to libdvdread and libdvdcss, normally required for commercial dvd playback. On my own copy (which is a bit more recent than yours) the following is more usually seen:

Andrew

Hi Andrew.

Well I just checked Synaptic and id shouws I have
libdvdread4  and libdvdcss2 both enabled! :confused:

---

### Post by andrew.46 on 2009-10-17
Hi Mike,

In which case I am not entirely clear what the problem might be. There is however always the Gordian Knot approach where you can reinstall MPlayer using a new version and see if this fixes the problem. You can compile your own following one of the guides on these forums or [add RVM's PPA]("https://launchpad.net/~rvm/+archive/mplayer"). Not a very satisfactory way of solving such a problem but it might work. Sorry I cannot see a more definitive answer :(.

Andrew

---

### Post by Oiolosse on 2009-10-27
I also have the same problem, when I try running a DVD *not* using terminal I get the same seek error.

However, if I use command: 

mplayer dvd://

it runs great! the keyboard controls are fantastic, there are many but when learned are far better than
using the GUI imo.

Hope this helps.

---

### Post by vinutux on 2009-10-28
> **Oiolosse said:**
> I also have the same problem, when I try running a DVD *not* using terminal I get the same seek error.

However, if I use command: 

mplayer dvd://

it runs great! the keyboard controls are fantastic, there are many but when learned are far better than
using the GUI imo.

Hope this helps.

new...info..........

---

