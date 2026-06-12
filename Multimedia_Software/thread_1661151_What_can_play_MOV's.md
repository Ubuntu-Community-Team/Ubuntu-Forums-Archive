---
title: "What can play MOV's?"
date: 2011-01-06
forum: Multimedia Software
---

### Post by FinalShot on 2011-01-06
I'm trying to play a .mov with the SVQ3 codec, but VLC fails ( 1.0.6 and 1.1.2 ). What media players can play it?

---

### Post by RikardSvenningsen on 2011-01-06
I play .mov with Totem, out of the box.

---

### Post by FinalShot on 2011-01-06
Thanks, but it didn't work.

---

### Post by ron999 on 2011-01-06
Hi
I can play mov files with VLC.
But your mov files use a different codec.
Try using **ffplay** from the command line, like this:-
[SIZE="4"]```
[FONT="Courier New"]ffplay yourfilename.mov[/FONT]
```[/SIZE]

---

### Post by FinalShot on 2011-01-06
Plays audio, but no video, just like VLC and xine :(

---

### Post by realzippy on 2011-01-06
kaffeine.

---

### Post by inobe on 2011-01-06
someone needs the ubuntu restricted extras.

---

### Post by FinalShot on 2011-01-06
> **realzippy said:**
> kaffeine.

I said Xine didn't work...

> **inobe said:**
> someone needs the ubuntu restricted extras.

Already have it.

---

### Post by ron999 on 2011-01-06
Hi
When I use command:-
[FONT="Courier New"][SIZE="5"]```
ffmpeg -codecs
```[/SIZE][/FONT]
it shows svq3 codec on the list, how about you? 
 > D VSD  svq3            Sorenson Vector Quantizer 3 / Sorenson Video 3 / SVQ3

---

### Post by FinalShot on 2011-01-06
Yeah it's there.

---

### Post by andrew.46 on 2011-01-06
Looks like MPlayer should play these, either through libavcodec or through a windows codec:

```

andrew@skamandros~$ mplayer -vc help | grep -i SVQ3
ffsvq3      ffmpeg    working   FFmpeg Sorenson Video v3 (SVQ3)  [svq3]
qtsvq3      qtvideo   working   Win32/QuickTime SVQ3  [QuickTimeEssentials.qtx]

```

There is a nice example here which demonstrates MPlayer in action:

```
wget http://samples.mplayerhq.hu/V-codecs/SVQ3/shrek2_tsr_qt_480.mov
```

Andrew

---

### Post by FinalShot on 2011-01-06
Tried it, but it just spits out text.

There is more before that, let me know if it could help.
```
[svq3 @ 0xb643eac0]top block unavailable for requested intra mode at 0 0
[svq3 @ 0xb643eac0]check_intra_pred_mode = -1
[svq3 @ 0xb643eac0]error while decoding MB 0 0
Error while decoding frame!

Too many audio packets in the buffer: (4096 in 748983 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:   0.0 V:   0.0 A-V:  0.046 ct:  0.000   0/  0 ??% ??% ??,?% 0 0 

Exiting... (End of file)
``````
$ mplayer -vc help | grep -i SVQ3
ffsvq3      ffmpeg    working   FFmpeg Sorenson Video v3 (SVQ3)  [svq3]

qtsvq3      qtvideo   working   Win32/QuickTime SVQ3  [QuickTimeEssentials.qtx]
```

---

### Post by andrew.46 on 2011-01-06
Perhaps try this:

```
mplayer -demuxer mov shrek2_tsr_qt_480.mov
```

Andrew

---

### Post by FinalShot on 2011-01-06
The audio plays now, but the video is just black. This is exactly what VLC is doing.

---

### Post by andrew.46 on 2011-01-06
Hi FinalShot,

> **FinalShot said:**
> The audio plays now, but the video is just black. This is exactly what VLC is doing.

In that case I suspect this will work:

```
mplayer -demuxer mov -vo x11 shrek2_tsr_qt_480.mov
```

If this works try altering your video out device in vlc as well from Tools --> Preferences --> Video --> Output.

Andrew

---

### Post by FinalShot on 2011-01-06
Unfortunately it didn't work, but I appreciate your help.

---

### Post by andrew.46 on 2011-01-06
Can you give the full terminal output for the following:

```
mplayer -v -demuxer mov shrek2_tsr_qt_480.mov
```

Hopefully some hints in there...

Andrew

---

### Post by FinalShot on 2011-01-06
Haha, that shrek clip works fine. I've been doing all commands on my clip.

I noticed in VLC that there are 2 video streams, I don't know if that's helpful.

Terminal output, on my clip ( I can do it on Shrek clip if you want ).
```
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
CPU vendor name: GenuineIntel  max cpuid level: 13
CPU: Pentium(R) Dual-Core  CPU      E5300  @ 2.60GHz (Family: 6, Model: 23, Stepping: 10)
extended cpuid-level: 8
extended cache-info: 134242368
Detected cache-line size is 64 bytes
Testing OS support for SSE... yes.
Tests of OS support for SSE passed.
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNowExt: 0 SSE: 1 SSE2: 1 SSSE3: 1
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/scott/.mplayer/codecs.conf'
Reading /home/scott/.mplayer/codecs.conf: Can't open '/home/scott/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --prefix=/usr --confdir=/etc/mplayer --enable-xvmc --enable-menu --enable-largefiles --language=all --disable-libdvdcss-internal --disable-dvdread-internal --disable-libavutil_a --disable-libavcodec_a --disable-libavformat_a --disable-libpostproc_a --disable-libswscale_a --target=i586-linux --enable-runtime-cpudetection --enable-debug --enable-mga --enable-3dfx --enable-tdfxfb --disable-gui
CommandLine: '-v' '-demuxer' 'mov' 'Section1.mov'
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/scott/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/scott/.mplayer/input.conf'
Can't open input config file /home/scott/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 89 binds
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('Section1.mov.conf') -> '/home/scott/.mplayer/Section1.mov.conf'

Playing Section1.mov.
get_path('sub/') -> '/home/scott/.mplayer/sub/'
[file] File size is 1384011550 bytes
STREAM: [file] Section1.mov
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
Checking for MOV
ISO: File Type Major Brand: Original QuickTime
ISO: File Type Minor Version: 537199360
ISO: File Type Compatible Brand #0: qt  
ISO: File Type Compatible Brand #1: 
ISO: File Type Compatible Brand #2: 
ISO: File Type Compatible Brand #3: 
MOV: Movie header found!
MOV: 'WIDE' chunk found!
MOV: Movie DATA found!
Quicktime/MOV file format detected.
MOV: Movie header (100 bytes): tscale=1500  dur=13561625
--------------
MOV: Track #0:
MOV:  Track header!
tkhd len=84 ver=0 flags=0x0 id=1 dur=18900 lay=0 vol=0
MOV:  Edit atom!
MOV:   Edit list table (1 entries) (ver:0,flags:0)
MOV:     entry#0: duration: 18900  start time: 0  speed: 1.0x
MOV:  Media stream!
MOV:   Media header!
MOV:   Handler header: mhlr/vide (appl) Apple Video Media Handler
MOV:   Media info!
MOV:    Video header!
MOV:    Handler header: dhlr/alis (appl) Apple Alias Data Handler
MOV: unknown chunk: dinf 28
MOV:    Sample info!
MOV:     Description list! (cnt:1)
MOV:      desc #0: SVQ3  (95 bytes)
MOV:     Sample duration table! (1 blocks)
MOV:     Syncing samples (keyframes) table! (7 entries) (ver:0,flags:0)
MOV:     Sample->Chunk mapping table!  (27 blocks) (ver:0,flags:0)
MOV:     Sample size table! (entries=189 ss=0) (ver:0,flags:0)
MOV:     Chunk offset table! (51 chunks)
MOV track #0: 51 chunks, 189 samples
pts=189  scale=15  time=12.600
EL#0: pts=0  1st_sample=0  frames=189 (12.600s)  pts_offs=0
==> Found video stream: 0
[mov] Video stream found, -vid 0
MOV: Found unknown movie atom SMI  (21)!
Image size: 916 x 686 (24 bpp)
Display size: 916 x 686
Fourcc: SVQ3  Codec: 'Sorenson Video 3'
--------------
MOV: Track #1:
MOV:  Track header!
tkhd len=84 ver=0 flags=0x0 id=2 dur=13560200 lay=65535 vol=0
MOV:  Edit atom!
MOV:   Edit list table (2 entries) (ver:0,flags:0)
MOV:     entry#0: duration: 18900  start time: -1  speed: 1.0x
MOV:     entry#1: duration: 13541300  start time: 0  speed: 1.0x
MOV:  Media stream!
MOV:   Media header!
MOV:   Handler header: mhlr/vide (appl) Apple Video Media Handler
MOV:   Media info!
MOV:    Video header!
MOV:    Handler header: dhlr/alis (appl) Apple Alias Data Handler
MOV: unknown chunk: dinf 28
MOV:    Sample info!
MOV:     Description list! (cnt:1)
MOV:      desc #0: SVQ3  (95 bytes)
MOV:     Sample duration table! (1 blocks)
MOV:     Syncing samples (keyframes) table! (5009 entries) (ver:0,flags:0)
MOV:     Sample->Chunk mapping table!  (18092 blocks) (ver:0,flags:0)
MOV:     Sample size table! (entries=135413 ss=0) (ver:0,flags:0)
MOV:     Chunk offset table! (36128 chunks)
MOV track #1: 36128 chunks, 135413 samples
pts=135413  scale=15  time=9027.533
EL#1: pts=0  1st_sample=0  frames=135413 (9027.533s)  pts_offs=0
==> Found video stream: 1
[mov] Video stream found, -vid 1
MOV: Initial Video-Delay: 12.600 sec
MOV: Found unknown movie atom SMI  (21)!
Image size: 916 x 686 (24 bpp)
Display size: 916 x 686
Fourcc: SVQ3  Codec: 'Sorenson Video 3'
--------------
MOV: Track #2:
MOV:  Track header!
tkhd len=84 ver=0 flags=0x0 id=3 dur=13561625 lay=65534 vol=256
MOV:  Edit atom!
MOV:   Edit list table (1 entries) (ver:0,flags:0)
MOV:     entry#0: duration: 13561625  start time: 0  speed: 1.0x
MOV:  Media stream!
MOV:   Media header!
MOV:   Handler header: mhlr/soun (appl) Apple Sound Media Handler
MOV:   Media info!
MOV:    Sound header!
MOV:    Handler header: dhlr/alis (appl) Apple Alias Data Handler
MOV: unknown chunk: dinf 28
MOV:    Sample info!
MOV:     Description list! (cnt:1)
MOV:      desc #0: .mp3  (112 bytes)
MOV:     Sample duration table! (1 blocks)
MOV:     Sample->Chunk mapping table!  (33622 blocks) (ver:0,flags:0)
MOV:     Sample size table! (entries=346104 ss=0) (ver:0,flags:0)
MOV:     Chunk offset table! (36448 chunks)
MOV track #2: 36448 chunks, 346104 samples
pts=199355904  scale=22050  time=9041.084
EL#0: pts=0  1st_sample=0  frames=346104 (9041.083s)  pts_offs=0
==> Found audio stream: 2
[mov] Audio stream found, -aid 2
Audio bits: 16  chans: 1  rate: 22050
Audio header: samp/pack=576 bytes/pack=182 bytes/frame=182 bytes/samp=2  
Audio extra header: len=76  fcc=0x77617665
ourcc: .mp3unknown audio atom X
--------------
Quicktime Clip Info:
MOV: longest streams: A: #2 (346104 samples)  V: #1 (135413 samples)
VIDEO:  [SVQ3]  916x686  24bpp  15.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:7  fourcc:0x33515653  size:916x686  fps:15.000  ftime:=0.0667
get_path('sub/') -> '/home/scott/.mplayer/sub/'
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
X11 opening display: :0.0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1440x900 with depth 24 and 32 bpp (":0.0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
[VO_XV] Using Xv Adapter #0 (NV17 Video Texture)
[xv common] Drawing no colorkey.
[xv common] Maximum source image dimensions: 2046x2046
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
INFO: libavcodec init OK!
Selected video codec: [ffsvq3] vfm: ffmpeg (FFmpeg Sorenson Video v3 (SVQ3))
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
dec_audio: Allocating 4608 + 65536 = 70144 bytes for output buffer.
mp3lib: using SSE optimized decore!
MP3lib: init layer2&3 finished, tables done
MPEG 2.0, Layer III, 22050 Hz 56 kbit Single-Channel, BPF: 183
Channels: 1, copyright: No, original: No, CRC: Yes, emphasis: 0
AUDIO: 22050 Hz, 2 ch, s16le, 56.0 kbit/7.94% (ratio: 7000->88200)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
Building audio filter chain for 22050Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 22050Hz/2ch/s16le
[dummy] Was reinitialized: 22050Hz/2ch/s16le
Trying preferred audio driver 'pulse', options '[none]'
AO: [pulse] 22050Hz 2ch s16le (2 bytes per sample)
AO: Description: PulseAudio audio output
AO: Author: Lennart Poettering
Building audio filter chain for 22050Hz/2ch/s16le -> 22050Hz/2ch/s16le...
[dummy] Was reinitialized: 22050Hz/2ch/s16le
[dummy] Was reinitialized: 22050Hz/2ch/s16le
Starting playback...
Increasing filtered audio buffer size from 0 to 24064
[ffmpeg] aspect_ratio: 0.000000
VDec: vo config request - 916 x 686 (preferred colorspace: Planar YV12)
Trying filter chain: vo
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO Config (916x686->916x686,flags=0,'MPlayer',0x32315659)
VO: [xv] 916x686 => 916x686 Planar YV12 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x59565955 (UYVY) packed
Xvideo image format: 0x30323449 (I420) planar
using Xvideo port 310 for hw scaling
*** [vo] Allocating (slices) mp_image_t, 928x688x12bpp YUV planar, 957696 bytes
```

After this there is just a bunch of "Error while decoding frame".

---

### Post by RikardSvenningsen on 2011-01-07
I am not an expert but from time to time you get stuff you cant play.
I usually use Avidemux to play those clip. You can find it in synaptic.

---

### Post by andrew.46 on 2011-01-07
Hi FinalShot,

Are you running these commands from the bare commandline or though SMPlayer?

Andrew

---

### Post by FinalShot on 2011-01-07
Bare command line.

---

### Post by andrew.46 on 2011-01-07
Hmmmm...... perhaps you could try selecting the video track manually, using *-vid 0* added to the commandline. I am not sure if the first track should be specified as 0 or 1 but it should be easy enough to experiment :). Can you post this problem file somewhere? I would be keen to have a look at it...

Andrew

---

### Post by FinalShot on 2011-01-07
It's over 1GB so I think that might be a problem. And with -vid 0 still black frame and errors in terminal.

---

### Post by gordintoronto on 2011-01-07
Is the video available on the Internet, so others might try playing it?

Did you install the non-free-codecs from the medibuntu repository?

---

### Post by FinalShot on 2011-01-07
No and yes.

---

### Post by andrew.46 on 2011-01-07
Hi FinalShot,

I am afraid that I am out of ideas, sorry I cannot be of much help with this one :(.

Andrew

---

### Post by FinalShot on 2011-01-07
Ok thanks man.

---

### Post by foxmulder881 on 2011-01-07
What's the trouble? I use Totem, MPlayer and Xine and they all play MOV files with no dramas.

---

### Post by FinalShot on 2011-01-07
With the same codec and 2 video streams?

---

### Post by foxmulder881 on 2011-01-07
> **FinalShot said:**
> With the same codec and 2 video streams?

What do you mean 2 video streams?

I tested on my system with a sample video and it surprised me actually. MPlayer and Xine would play audio only and no video, yet it worked perfect in worked in Totem.

---

### Post by andrew.46 on 2011-01-08
Hi FinalShot,

Have you considered running the latest svn MPlayer? There are guides scattered through these forums for various versions of Ubuntu...

Andrew

---

### Post by Waraqa on 2011-12-07
I have the same problem. Unable to play certain mov files with the following players:
1. mplayer 1.0rc4
2. ffplay 0.6
3. vlc 1.1.10

I have uploaded a file so that anyone can try to discover how to play it.

[[IMG]http://dc467.4shared.com/img/BRn3icqt/0.3741846817149369/CO-21-TranLS10.mov[/IMG]](http://www.4shared.com/video/BRn3icqt/CO-21-TranLS10.html)

---

### Post by ubuntu27 on 2011-12-07
> **andrew.46 said:**
> 
There is a nice example here which demonstrates MPlayer in action:

```
wget http://samples.mplayerhq.hu/V-codecs/SVQ3/shrek2_tsr_qt_480.mov
```

Andrew

I can play that video well. Using Totem Plugin

> **Waraqa said:**
> 

I have uploaded a file so that anyone can try to discover how to play it.

[[IMG]http://dc467.4shared.com/img/BRn3icqt/0.3741846817149369/CO-21-TranLS10.mov[/IMG]](http://www.4shared.com/video/BRn3icqt/CO-21-TranLS10.html)

But, I cannot play this video properly. The screen is black in both VLC and Totem with GStreamer.

---

