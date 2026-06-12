---
title: "mplayer compiled with --enable-vdpau doesn't work"
date: 2009-07-29
forum: Multimedia Software
---

### Post by biggerben on 2009-07-29
Sooooo
After 3 hours of trying to get my 1080p mkv videos to play smoothly I've given up on the idea that I can do that without help.

My System: Quadcore, GeForce 9400 GT, kubuntu karmic, nvidia accelerated graphics driver version 180, Linux version 2.6.31-4-generic.

I downloaded the newest mplayer (svn), ran ./configure with --enable-vdpau, make -j4 and make install. it compiles and installes fine. I even get "vdpau" in the -vo help list. But when I want to run mplayer, even without vdpau:

```
ben@serenity:~/movies$ /usr/local/bin/mplayer movie.1080p.x264.mkv -ss 32:40 -vo xv -ao null 
MPlayer SVN-r29455-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing movie.1080p.x264.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_DTS), -aid 0, -alang und
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1920x800  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [libdca] DTS decoding with libdca


MPlayer interrupted by signal 11 in module: init_audio_codec
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

```

I would be really really grateful if someone could tell me what I'm doing wrong. Please don't just point me to a 2 year old HOWTO. I've tried them all, they didn't work :(

---

### Post by andrew.46 on 2009-07-29
Hi biggerben,

> **biggerben said:**
> I downloaded the newest mplayer (svn), ran ./configure with --enable-vdpau, make -j4 and make install. it compiles and installes fine. I even get "vdpau" in the -vo help list.

It is usually better idea not to specify *--enable-vdpau* in your ./configure string as when compiling MPlayer, the process will almost always work better with auto-detection. Can I ask what method you used to compile MPlayer, in particular how you assembled the required libraries?

All the best,

Andrew

---

### Post by mc4man on 2009-07-29
I don't have any capable hardware but I wouldn't think -vo xv is what you want to do.

Several threads floating around, I'll edit one in.


here's one, shows an example command down the post a ways

[http://ubuntuforums.org/showthread.php?t=1037625](http://ubuntuforums.org/showthread.php?t=1037625)

---

### Post by biggerben on 2009-07-30
andrew: hey, you're the guy that wrote a howto a while back on this subject! :)
the latest thing I've tried is the following:

```
git clone git://repo.or.cz/mplayer && cd mplayer && git checkout origin/mt && git submodule init && git submodule update && ./configure && make -j4
```

from [http://ubuntuforums.org/archive/index.php/t-1104967.html](http://ubuntuforums.org/archive/index.php/t-1104967.html)

the good news is that it now works. it even uses multithreaded decoding which (on 4 cores) means smooth playback even for sick 1080p action scenes (one of the sickest I've found yet is 32:45 into the simsons movie where the camera pans through the mob wielding torches).

but: vdpau is not enabled

if i enable it with --enable-vdpau it compiles, i can even play files with -vo vdpau. but one core is peaks at 100% and mplayer then complains (**** Your system is too SLOW to play this!  ****). 

My hardware, plus my nvidia driver should be good enough for vdpau, no?

---

### Post by Arup on 2009-07-30
I have compiled using Andrew's method and it works out fine, I also compile ffmpeg and x264 using Fake Outdoorsman's method. I have vdpau enabled on my cheap nvidia 8400GS using latest beta 190.18 drivers, smplayer shows me vpdau codec used and cpu usage is never an issue here. Make sure to select vdpau as output for smplayer or gnomeplayer.

---

### Post by rvm4000 on 2009-07-30
biggerben, if you have trouble compiling mplayer, I suggest to try these packages from this PPA:
[https://launchpad.net/~rvm/+archive/testing](https://launchpad.net/~rvm/+archive/testing)

---

### Post by andrew.46 on 2009-07-30
Hi biggerben,

> **biggerben said:**
> andrew: hey, you're the guy that wrote a howto a while back on this subject! :)

Well strictly speaking I never really dealt with FFmpeg-MT and vdpau in the howto you have seen and my knowledge of both is not great. RVM's PPA is a place many are heading to now so perhaps this would be worth a go?

Andrew

---

