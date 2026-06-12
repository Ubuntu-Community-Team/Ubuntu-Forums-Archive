---
title: "Video with VC-1 codec"
date: 2010-03-27
forum: Multimedia Software
---

### Post by gabe17 on 2010-03-27
Hi there!

I have a video in .mkv format which uses Microsoft Windows Media VC-1 codec and I can't play it.   I use Movie player in order to play videos, but I've also tried many other players, but without success. 

Could anybody help me with this problem? Thx.

```

mplayer video.mkv
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing video.mkv.
[mkv] Track ID 1: audio (A_AC3) "CZ AC3 5.1 448Kbps", -aid 0, -alang cze
[mkv] Track ID 2: video (V_MS/VFW/FOURCC), -vid 0
[mkv] Track ID 3: audio (A_DTS) "AN DTS  5.1 1510Kbps", -aid 1, -alang eng
[mkv] Track ID 4: subtitles (S_TEXT/UTF8), -sid 0, -slang cze
[mkv] Track ID 5: subtitles (S_TEXT/UTF8), -sid 1, -slang eng
[mkv] Will play video track 2.
Matroska file format detected.
VIDEO:  [WVC1]  1920x1080  0bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [dmo] DMO video codecs
Win32 LoadLibrary failed to load: wvc1dmod.dll, /usr/lib/codecs/wvc1dmod.dll, /usr/lib/win32/wvc1dmod.dll, /usr/local/lib/win32/wvc1dmod.dll
IMediaObject ERROR: 0x840d7d1  could not open DMO DLL (0x0 : 0)
Failed to create DMO filter
ERROR: Could not open required DirectShow codec wvc1dmod.dll.
You need to upgrade/install the binary codecs package.
Go to http://www.mplayerhq.hu/dload.html
VDecoder init failed :(
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[vc1 @ 0x98e0ae0]Incomplete extradata
Could not open codec.
VDecoder init failed :(
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[VD_FFMPEG] Trying pixfmt=0.
VDec: vo config request - 1920 x 1080 (preferred colorspace: VC1 VDPAU acceleration)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
Unsupported PixelFormat -1
[vc1_vdpau @ 0x98e0ae0]decoding to PIX_FMT_NONE is not supported.
Could not open codec.
VDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x31435657.
Read DOCS/HTML/en/codecs.html!
==========================================================================
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
[pulse] working around probably broken pause functionality,
        see http://www.pulseaudio.org/ticket/440
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...


```

---

### Post by gabe17 on 2010-04-01
Nobody has solved this problem?

---

### Post by mc4man on 2010-04-01
There could be a couple of reasons why you can't play - 
you're on a 64 bit install so mplayer needs to decode vc1 thru ffmpeg (libavcodec
It doesn't appear to be trying, possibly karmic's ffmpeg doesn't support, you could try adding -vc ffvc1 to mplayer command to see.

Also there are known issues with .mkv  with mplayer built with gcc 4.4.1, maybe a factor

Have no issue here with vc1 and mplayer on 64 bit - using a self built version
> Playing /home/doug/Desktop/TDK_TRL2_1080p.wmv.
ASF file format detected.
.......clipped
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffvc1] vfm: ffmpeg (FFmpeg WVC1)


You could try a ppa with a more recent mplayer than karmic (but still using gcc 4.4.1
[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

or build your own with the latest version (and use  gcc-4.3 as in the instructions

[http://ubuntuforums.org/showthread.php?t=1305181](http://ubuntuforums.org/showthread.php?t=1305181)

---

### Post by gabe17 on 2010-04-02
But I use 32-bit, not 64-bit. 
Maybe in Lucid Lynx will be more recent version of mplayer?

---

### Post by mc4man on 2010-04-02
> But I use 32-bit

I'm sorry, glanced too quickly at your error message - just add w32codecs and you should get decoding

[http://packages.medibuntu.org/karmic/w32codecs.html](http://packages.medibuntu.org/karmic/w32codecs.html)

Lucid's mplayer is the same though it uses a compiler that doesn't cause potential issues

Did you try using -vc ffvc1 ? ( I think ffmpeg's vc1 decoder works better than the dmo one (w32codes

Edit: on a lucid tester with the stock ffmpeg and mplayer (uses same sources as karmic), mplayer plays vc1 fine the ffmpeg decoder 
```
mplayer -vc ffvc1 video.mkv
```

---

### Post by gabe17 on 2010-04-04
Using  -vc ffvc1 it doesn't work. But I've installed the w32codecs and it finally works! But I can't understand why it says that my system is too slow to play the video.
```
           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.

```The video is in FULL-HD format. Is overclocked AMD Athlon X2 7750BE (3,0GHz) to slow to play this? I hope that's just a joke. 
And why there aren't any control buttons in mplayer when playing this? 

Anyway, thanks very much for help, I am really happy that it runs.;)

---

### Post by andrew.46 on 2010-04-04
Hi gabe,

> **gabe17 said:**
> And why there aren't any control buttons in mplayer when playing this? 

The commandline player uses keyboard and has a *very* extensive list of commands to control playback. Simply running mplayer with no options hints at some of the possibilities:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer[/COLOR]**
MPlayer SVN-r30994-4.3.3 (C) 2000-2010 MPlayer Team
Usage:   mplayer [options] [url|path/]filename

Basic options: (complete list in the man page)
 -vo <drv>        select video output driver ('-vo help' for a list)
 -ao <drv>        select audio output driver ('-ao help' for a list)
 vcd://<trackno>  play (S)VCD (Super Video CD) track (raw device, no mount)
 dvd://<titleno>  play DVD title from device instead of plain file
 -alang/-slang    select DVD audio/subtitle language (by 2-char country code)
 -ss <position>   seek to given (seconds or hh:mm:ss) position
 -nosound         do not play sound
 -fs              fullscreen playback (or -vm, -zoom, details in the man page)
 -x <x> -y <y>    set display resolution (for use with -vm or -zoom)
 -sub <file>      specify subtitle file to use (also see -subfps, -subdelay)
 -playlist <file> specify playlist file
 -vid x -aid y    select video (x) and audio (y) stream to play
 -fps x -srate y  change video (x fps) and audio (y Hz) rate
 -pp <quality>    enable postprocessing filter (details in the man page)
 -framedrop       enable frame dropping (for slow machines)

Basic keys: (complete list in the man page, also check input.conf)
 <-  or  ->       seek backward/forward 10 seconds
 down or up       seek backward/forward  1 minute
 pgdown or pgup   seek backward/forward 10 minutes
 < or >           step backward/forward in playlist
 p or SPACE       pause movie (press any key to continue)
 q or ESC         stop playing and quit program
 + or -           adjust audio delay by +/- 0.1 second
 o                cycle OSD mode:  none / seekbar / seekbar + timer
 * or /           increase or decrease PCM volume
 x or z           adjust subtitle delay by +/- 0.1 second
 r or t           adjust subtitle position up/down, also see -vf expand

**[COLOR="Red"] * * * SEE THE MAN PAGE FOR DETAILS, FURTHER (ADVANCED) OPTIONS AND KEYS * * *[/COLOR]**


```

All the best,

Andrew

---

### Post by gabe17 on 2010-04-05
Thanks very much to both. Solved. ;)

---

