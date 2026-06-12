---
title: "No Sound Playing WMA Gnome player"
date: 2010-02-23
forum: Multimedia Software
---

### Post by sandman3838 on 2010-02-23
Hello

I wrote about this issue some time ago but it was for another version of Ubuntu.  I'm now using Ubuntu 9.10 64bit.  

Now all of the WMA files play just fine there is just not sound.  Oh, and I have tried playing them through VLC, Armok, Kaffeine and movie player.

My best results have been through GNOME Player and Mplayer it's just that there is no sound.  

I found a few scripts that might help but they are geared more for Mplayer?

kevin@kj-Linux:~/Desktop$ mplayer -ao esd filename 

HaloWars_ESRB_720p30_ST_8Mbps.wmv
MPlayer UNKNOWN-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing filename.
File not found: 'filename'
Failed to open filename.


Playing HaloWars_ESRB_720p30_ST_8Mbps.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WMV3]  1280x720  24bpp  1000.000 fps  8000.0 kbps (976.6 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Requested video codec family [wmv9dmo] (vfm=dmo) not available.
Enable it at compilation.
Requested video codec family [wmvdmo] (vfm=dmo) not available.
Enable it at compilation.
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[wmv3 @ 0x7fd8c12bca80]Extra data: 8 bits left, value: 0
Selected video codec: [ffwmv3] vfm: ffmpeg (FFmpeg WMV3/WMV9)
==========================================================================
==========================================================================
Requested audio codec family [wma9dmo] (afm=dmo) not available.
Enable it at compilation.
Requested audio codec family [wmadmo] (afm=dmo) not available.
Enable it at compilation.
Cannot find codec for audio format 0x162.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Starting playback...
VDec: vo config request - 1280 x 720 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 1280x720 => 1280x720 Planar YV12 
V: 104.6 2896/2896 19%  1%  0.0% 0 0 

Exiting... (End of file)
kevin@kj-Linux:~/Desktop$ 

kevin@kj-Linux:~/Desktop$ mplayer -ao help
MPlayer UNKNOWN-4.4.1 (C) 2000-2009 MPlayer Team
Available audio output drivers:
	oss	OSS/ioctl audio output
	alsa	ALSA-0.9.x-1.x audio output
	esd	EsounD audio output
	pulse	PulseAudio audio output
	jack	JACK audio output
	nas	NAS audio output
	sdl	SDLlib audio output
	openal	OpenAL audio output
	mpegpes	DVB audio output
	v4l2	V4L2 MPEG Audio Decoder output
	null	Null audio output

---

### Post by mc4man on 2010-02-23
> Cannot find codec for audio format 0x162.
That's wma3 (pro) audio, which can be decoded thru dmo (w32codecs) or libavcodec
On a 64 bit install it will have to be thru libavcodec, unfortunately in karmic mplayer has been stripped of it's built-in ffmpeg libraires.

Your easiest solution is to either install mplayer from a ppa or build
ppa
[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

build
[http://ubuntuforums.org/showthread.php?t=1305181](http://ubuntuforums.org/showthread.php?t=1305181)

---

### Post by Yellow Pasque on 2010-02-23
Unfortunately, the proprietary codecs in Medibuntu's w32codecs package don't work on 64-bit Ubuntu. There's a w64codecs package, but it only has a handful of codecs.

Your best bet is to run a 32-bit mplayer.

EDIT: mc4man beat me to it

---

### Post by mc4man on 2010-02-23
I'm on my 64 bit install where I do have a 32 bit mplayer installed, but that can be a bit of work to build. You really don't need it though for wma3 audio as seen here (forced mplayer to to use libavcodec instead of dmo

> doug@doug-laptop:~$ mplayer '/home/doug/Desktop/TDK_TRL2_1080p.wmv' 
MPlayer SVN-r30479-4.4.1 (C) 2000-2010 MPlayer Team

Playing /home/doug/Desktop/TDK_TRL2_1080p.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WVC1]  1920x1080  24bpp  1000.000 fps  8000.0 kbps (976.6 
Trying to force video codec driver family ffmpeg...
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffvc1] vfm: ffmpeg (FFmpeg WVC1)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 96000 Hz, 2 ch, floatle, 440.0 kbit/7.16% (ratio: 55002->768000)
[COLOR="Blue"]Selected audio codec: [ffwmapro] afm: ffmpeg (WMA Pro audio (FFmpeg))[/COLOR]


For vlc it's also possible but more work on your end (build a static. patched ffmpeg, build vlc

> doug@doug-laptop:~$ vlc -vv /home/doug/Desktop/TDK_TRL2_1080p.wmv
VLC media player 1.0.5 Goldeneye
[0x20c0e48] asf demux debug: found 2 streams
[0x1e9dad8] main input debug: selecting program id=0
[0x20c0e48] asf demux debug: [COLOR="Blue"]added new audio stream(codec:0x162,ID:1)[/COLOR]
[0x20c0e48] asf demux debug: added new video stream(ID:2)
[0x2cc3cd8] avcodec decoder debug: libavcodec initialized (interface 0x343600)
[0x2cc3cd8] avcodec decoder debug: ffmpeg codec (Windows Media Audio Professional) started
[0x20b9708] avcodec decoder debug: ffmpeg codec (Windows Media Video VC1) started

---

### Post by sandman3838 on 2010-02-23
That seems to have done is gentleman!

I went with:
Your easiest solution is to either install mplayer from a ppa or build

ppa
[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

Thank you everyone you were great!

---

### Post by Yellow Pasque on 2010-02-23
Thanks, mc4man, that's good to know.

---

