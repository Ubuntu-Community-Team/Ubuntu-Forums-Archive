---
title: "Can Anyone ElsePlay This 1080p File?"
date: 2010-02-14
forum: Multimedia Software
---

### Post by izizzle on 2010-02-14
Here it is: [http://pdl.warnerbros.com/wbmovies/thedarkknight/trailer2/TDK_TRL2_1080p.wmv](http://pdl.warnerbros.com/wbmovies/thedarkknight/trailer2/TDK_TRL2_1080p.wmv)

I am using it to test the playback of 1080pon my fresh 9.10 64 bit ubuntu install. I have installed restricted extras, w64codecs, and have updated the system. Still, this file does not want to play.

When I play it with totem, it says "Internal data stream error". It then proceeds to try and find a WindowsMedia Audio 9 codec, but fails. When I tried with MPlayer, it gives an error (initializing the selected video_out (-vo) device), and then it says "cannot find codec for audio format 0x162)

I know it is a rather large file, but I would really appreciate it if someone can confirm that it works on their Ubuntu install, and maybe lead me in the right direction. 

Thanks.

---

### Post by hxcobd on 2010-02-14
Yup, plays fine here. I'm on 32-bit 9.10, using VLC though, not Totem.

*edit - I take that back; video plays fine, no audio though. Telling me it cannot play audio format "WMAP," and I concur, as I've never heard of that format before.

---

### Post by mc4man on 2010-02-14
Plays fine here in vlc, mplayer, ect. (32 bit
I have my own built versions of both where the audio (wma3pro) is decoded by avcodec (libavcodec

For 64 bit your easiest solution would be to  either [build your own mplayer]("http://ubuntuforums.org/showthread.php?t=1305181") or get one from a [ppa.]("http://smplayer.sourceforge.net/downloads.php") 
( the repo mplayer in karmic is neutered and uses the system ffmpeg libs which don't support wma3 decoding

If you go the ppa then get the mplayer build and if desired smplayer also, if you build you can also use your build with smplayer,

For vlc you'd need to build either a release, 1.0.5 is latest, or a 1.1 git. ( a bit involved but quite doable even in 64 bit

> [0x85ea570] asf demux debug: added new audio stream(codec:0x162,ID:1)
[0x85ea570] asf demux debug: added new video stream(ID:2)
[0x85ea570] main demux debug: using demux module "asf"
[0x85ea570] main demux debug: TIMER module_need() : 14.377 ms - Total 14.377 ms / 1 intvls (Avg 14.377 ms)
[0xb7304818] main decoder debug: looking for decoder module: 33 candidates
[0xb7304818] avcodec decoder debug: libavcodec initialized (interface 0x342a00)
[0xb7304818] avcodec decoder debug: ffmpeg codec (Windows Media Audio Professional) started
[0xb7304818] avcodec decoder debug: Using 196608 bytes output buffer
[0xb7304818] main decoder debug: using decoder module "avcodec"
[0xb7304818] main decoder debug: TIMER module_need() : 71.707 ms - Total 71.707 ms / 1 intvls (Avg 71.707 ms)
[0xb7304818] main decoder debug: thread (decoder) created at priority 5 (input/decoder.c:315)
[0xb7304818] main decoder debug: thread started
[0x860c3a8] main decoder debug: looking for decoder module: 33 candidates
[0x860c3a8] avcodec decoder debug: libavcodec already initialized
[0x860c3a8] avcodec decoder debug: using direct rendering
[0x860c3a8] avcodec decoder debug: ffmpeg codec (Windows Media Video VC1) started
[0x860c3a8] main decoder debug: using decoder module "avcodec"
[0x860c3a8] main decoder debug: TIMER module_need() : 18.643 ms - Total 18.643 ms / 1 intvls (Avg 18.643 ms)
[0x860c3a8] main decoder debug: thread started
[0x860c3a8] main decoder debug: thread (decoder) created at priority 0 (input/decoder.c:315)
[0xb73008d8] main input debug: `/home/doug/Videos/TDK_TRL2_1080p.wmv' successfully opened

---

### Post by izizzle on 2010-02-14
Is there any pre-made software which utilizes all the codecs, and which can play this type of file? Perhaps a DEB for a user compiled VLC or MPlayer?

---

### Post by mc4man on 2010-02-14
> Is there any pre-made software
The ppa I linked above - a bit more verbose/direct

[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

---

### Post by izizzle on 2010-02-14
I added the ppa and ran sudo apt-update, but nothing installs when I run sudo apt-upgrade.
I installed the version from "Ubuntu Software Center" and tried playing the file, but got the same error. Is this right?

---

### Post by izizzle on 2010-02-14
I got t to work by installing Mplayer and running the SMPlayer frontend.

---

### Post by mc4man on 2010-02-14
> Is this right? 
Doesn't appears so if you can't play..
Happen to be on my 64 bit install so I removed my mplayer, added the ppa, installed 'mplayer' and your video plays fine.

Search mplayer in synaptic ans see what is installed ( note that rvm names it mplayer - the ubuntu repo names it mplayer-nogui.

See screen one - to d. check r.click on the package and ck. the properties - should show as screen 2

From terminal
> doug@doug-laptop:~$ mplayer '/home/doug/Desktop/TDK_TRL2_1080p.wmv' 
MPlayer SVN-r29643-Ubuntu-RVM (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/doug/Desktop/TDK_TRL2_1080p.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WVC1]  1920x1080  24bpp  1000.000 fps  8000.0 kbps (976.6 kbyte/s)
Clip info:
 title: 
 author: 
 copyright: 
 comments: 
==========================================================================
Trying to force video codec driver family ffmpeg...
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffvc1] vfm: ffmpeg (FFmpeg WVC1)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 96000 Hz, 2 ch, floatle, 440.0 kbit/7.16% (ratio: 55002->768000)
Selected audio codec: [ffwmapro] afm: ffmpeg (WMA Pro audio (FFmpeg))
==========================================================================
AO: [oss] 96000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 1920 x 1080 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 1920x1080 => 1920x1080 Planar YV12 
A:  19.0 V:  19.0 A-V:  0.002 ct:  0.073 216/216 30%  8%  1.7% 0 0 


---

### Post by izizzle on 2010-02-15
In fact, I didn't even need SMPlayer. I just installed MPlayer with the PPAyou provided, and used GNOME Mplayer as a frontend. Perfect.

---

