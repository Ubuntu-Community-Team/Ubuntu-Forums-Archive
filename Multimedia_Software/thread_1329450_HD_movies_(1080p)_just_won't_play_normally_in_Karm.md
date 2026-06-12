---
title: "HD movies (1080p) just won't play normally in Karmic"
date: 2009-11-17
forum: Multimedia Software
---

### Post by Filipek on 2009-11-17
Hello all,

I am just desperate. I have everything set up in my Karmic and working. All the codecs, sound is playing but my concern are HD movies I would like to play.

The problem the play too slowly - video and sound desync immediately upon start and the movie is almost not moving.

You may say I have a slow computer but I don't - I just looked at Conky while playing the 1080p HD movie and the CPU is at 70% maximum. 

I have tried multiple video output in mplayer or VLC (x11, gl, gl2 and the basic of course). I have even tried to play without sound to find out whether that piece is buggy or not. The video was slow again :-(

My parameters are if this helps:

1) latest kernel (2.6.31.14) Ubuntu Karmic
2) 2 GB RAM
3) ATI 3850 - latest original video drivers at spot and working
4) glxgears giving approximately 8000 fps

My HW is definitely capable of playing HD movies since they do in Windows XP like a charm. But that is not a solution for me since I am not confortable in XP system. Something is bad in my system and I hope it is still solvable.

I have read almost everything on this forum available and tried a lot of it... nothing rang any bell so far.

Please, more experienced ones, could please try to solve this issue with me? The only thing that keeps M$ XP on my computer :-( ...

---

### Post by xzero1 on 2009-11-17
Windows probably uses the graphics card hardware for video acceleration. If your card supports UVD or UVD2 then you *might* be able to use hardware for video acceleration under Ubuntu using fglrx. If not, I suggest using mplayer -benchmark... to see how fast your hardware actually is. Your system may not be fast enough. If fast enough, use smplayer to optimize your video settings.

---

### Post by Melcar on 2009-11-17
No hardware acceleration for HD content when using current ATI drivers (either open or close).  Your CPU is doing all the work (hence the high CPU usage), and it seems that it's not fast enough for 1080p material.  Your card has UVD (used to accelerate HD content) which works fine in Windows, but unfortunately that feature will never come to Linux.  
Good news is that there are working on a XvBA implementation using VAAPI, though I don't know when it will be available with the drivers. You can try it yourself.  You will need to install the proper libraries (XvBA and libva), and build a VAAPI enabled mplayer.  I don't think it works with the latest ATI drivers (9.10), so you may want to wait until the 9.11s are out (should be any day now) or hunt for some leaked beta drivers.

[http://www.splitted-desktop.com/~gbeauchesne/xvba-video/]("http://www.splitted-desktop.com/~gbeauchesne/xvba-video/")

There is a [thread]("http://www.phoronix.com/forums/showthread.php?t=19983") about it on Phoronix.

---

### Post by Filipek on 2009-11-17
> **Melcar said:**
> No hardware acceleration for HD content when using current ATI drivers (either open or close).  Your CPU is doing all the work (hence the high CPU usage), and it seems that it's not fast enough for 1080p material.  Your card has UVD (used to accelerate HD content) which works fine in Windows, but unfortunately that feature will never come to Linux.  
Good news is that there are working on a XvBA implementation using VAAPI, though I don't know when it will be available with the drivers. You can try it yourself.  You will need to install the proper libraries (XvBA and libva), and build a VAAPI enabled mplayer.  I don't think it works with the latest ATI drivers (9.10), so you may want to wait until the 9.11s are out (should be any day now) or hunt for some leaked beta drivers.

[http://www.splitted-desktop.com/~gbeauchesne/xvba-video/]("http://www.splitted-desktop.com/~gbeauchesne/xvba-video/")

There is a [thread]("http://www.phoronix.com/forums/showthread.php?t=19983") about it on Phoronix.

Thank you a lot even for the bad news. At least I know I should give up searching for bugs in my installation. This is a huge disappointment.

Do you think you could me more concrete what to do in order to try the above mentioned? I have done some research but I am not sure where to find Mplayer with VAAPI feature to be compile as well as the right libraries. I know I may need to wait for the new Catalyst but I may not have anyone to ask at that time...

---

### Post by Melcar on 2009-11-17
The [9.11]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English") drivers have just been released :).  The link I gave above directing to XvBA also has links for the proper mplayer source (it's easy to build and comes with instructions), as well as the latest required libva libraries.  
Basically what you need to do is install the three libva packages (libva-dev, libva-dbg, libva), install the latest XvBA package, and build mplayer (you need to install all libva packages first for it to compile successfully).  The mplayer folder you download also has instructions on how to actually play videos (there is no gui yet, so it's all by the terminal).
Everything you need is in the above link (no need to get the sources for the libraries as .deb packages are also available).  Keep in mind that since this is beta it may not work (you could always try earlier mplayer builds),  Also, this is for UVD2 (r7xx type cards) and I haven't heard of anyone with a UVD card having tested this yet.  Doesn't hurt to try though.

---

### Post by xzero1 on 2009-11-17
> **Melcar said:**
> No hardware acceleration for HD content when using current ATI drivers (either open or close).  Your CPU is doing all the work (hence the high CPU usage), and it seems that it's not fast enough for 1080p material.  Your card has UVD (used to accelerate HD content) which works fine in Windows, but unfortunately that feature will never come to Linux.  
Good news is that there are working on a XvBA implementation using VAAPI, though I don't know when it will be available with the drivers. You can try it yourself.  You will need to install the proper libraries (XvBA and libva), and build a VAAPI enabled mplayer.  I don't think it works with the latest ATI drivers (9.10), so you may want to wait until the 9.11s are out (should be any day now) or hunt for some leaked beta drivers.

[http://www.splitted-desktop.com/~gbeauchesne/xvba-video/]("http://www.splitted-desktop.com/%7Egbeauchesne/xvba-video/")

There is a [thread]("http://www.phoronix.com/forums/showthread.php?t=19983") about it on Phoronix.

No hardware acceleration for HD content....????
The new XvBA is superior but...

Before XvBA there was XvMC which requires an XvMC enabled player. You might have a better chance of getting that to work than XvBA. I had no trouble viewing 1080p@24 HD content with it even though my Phenom II cpu was running at 800Mhz using the motherboard's built in 3300IGP.


See [http://en.wikipedia.org/wiki/X-Video_Motion_Compensation](http://en.wikipedia.org/wiki/X-Video_Motion_Compensation)
and [http://wiki.cchtml.com/index.php/User_Contributed_Documentation#Video_Overlay_on_AVIVO_cards](http://wiki.cchtml.com/index.php/User_Contributed_Documentation#Video_Overlay_on_AVIVO_cards)

The mplayer mentioned by Melcar I believe is XvMC enabled.
To run with mplayer use mplayer -vo xv......

---

### Post by doas777 on 2009-11-17
I've gotten smooth playback with newer mkv formatted 1080p content on middle-of-the-road amd/ati hardware in karmic, but I did need to install the driver from ati. some older hd mkv's (ones from last year) however do not play as nicely with the w6codecs and everything from the restricted extras.

I do find that mplayer/smplayer are most capable for hd content,  even though the interface is lacking compared to totem. 

I have considered purchasing the CoreAVC codec for mkv (it's like 8$), as I am told that it dramatically smooths hd playback, and has capabilities not available in any of the free implementations (for win or lin or mac).

so sorry for not providing good fixes, but may be worth somthing...

---

### Post by Filipek on 2009-11-17
> **xzero1 said:**
> No hardware acceleration for HD content....????
The new XvBA is superior but...

Before XvBA there was XvMC which requires an XvMC enabled player. You might have a better chance of getting that to work than XvBA. I had no trouble viewing 1080p@24 HD content with it even though my Phenom II cpu was running at 800Mhz using the motherboard's built in 3300IGP.


See [http://en.wikipedia.org/wiki/X-Video_Motion_Compensation](http://en.wikipedia.org/wiki/X-Video_Motion_Compensation)
and [http://wiki.cchtml.com/index.php/User_Contributed_Documentation#Video_Overlay_on_AVIVO_cards](http://wiki.cchtml.com/index.php/User_Contributed_Documentation#Video_Overlay_on_AVIVO_cards)

The mplayer mentioned by Melcar I believe is XvMC enabled.
To run with mplayer use mplayer -vo xv......

XV is default mplayer output so I had definitely tried that before with no effect. However, according to your other post, I have tried to install VAAPI enabled Mplayer from this place: [http://www.splitted-desktop.com/~gbeauchesne/mplayer-vaapi/](http://www.splitted-desktop.com/~gbeauchesne/mplayer-vaapi/) with new patched libraries from this place: [http://www.splitted-desktop.com/~gbeauchesne/libva/](http://www.splitted-desktop.com/~gbeauchesne/libva/) . 

Do you guys have some experience with this one? I have installed everything like a charm but the vaapi enabled Mplayer in this case starts with no video output while the vainfo returns the following: 

```

$ vainfo
libva: libva version 0.31.0-sds3
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/fglrx_drv_video.so
libva error: /usr/lib/va/drivers/fglrx_drv_video.so init failed
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit

```

So I assume there is some problem with my current Catalyst (fglrx driver).

---

### Post by Melcar on 2009-11-17
Did you install XvBA?  And again, I'm not sure if it works on UVD cards, and I don't have one handy to test either.  By the way, while vainfo reports a good status for me, mplayer always segfaults (and I tried several builds).  The whole thing is very beta and doesn't seem to work for everyone.

---

### Post by sdowney717 on 2009-11-17
[http://forums.debian.net/viewtopic.php?t=17783](http://forums.debian.net/viewtopic.php?t=17783)

> News
2009-02-20, Friday :: Video Acceleration and You
posted by Compn

There are several ways to speed up the playback of 1080 H.264 files in MPlayer.

First is to use the newly added VDPAU output. It allows the newer Nvidia video cards to decode the video without using much CPU. It is in SVN MPlayer (Nvidia binary driver 180.37 or newer required), you can find known bugs and report bugs HERE. (Linux, Solaris and FreeBSD only)
How to get the SVN version is described on the download page and snapshot tarballs are available as well.

Second is to use MPlayer with the experimental multithreaded FFmpeg-mt branch, which allows you to use multiple cores/CPU. (all OS and CPU supported)

To install, copy and paste this line:
git clone git://repo.or.cz/mplayer && cd mplayer && git checkout origin/mt && git submodule init && git submodule update && ./configure && make && make install
To enable threading run mplayer -lavdopts threads=N file.mkv where N is the number of threads you want to use.
NOTE: FFmpeg-mt has problems with packed b-frames.

A Windows build of MPlayer using FFmpeg-mt can be found at [http://kovensky.project357.com](http://kovensky.project357.com).

Third is to use the multithreaded CoreAVC codec with the CoreAVC-for-linux project. The CoreAVC decoder costs $15 USD. (Linux ONLY)(Windows users only need this PATCH)

Fourth, FFmpeg has added some optimizations from the x264 project. To fully utilize these you will need to make sure a recent version of YASM is installed and detected by the latest SVN MPlayer when compiling. (32bit x86 CPU only!)

Fifth, using -lavdopts skiploopfilter=all:fast=1 may cause artifacts, but will allow you to play larger files in realtime. (all OS and CPU supported) (use -lavdopts skipframe=nonref:skiploopfilter=all:fast=1 for even more speedup, skipframe also works with VDPAU.)

There is also a rejected PATCH which adds support for the new multithreaded binary VC-1/WMV3 codec.

---

### Post by Filipek on 2009-11-17
> **Melcar said:**
> Did you install XvBA?  And again, I'm not sure if it works on UVD cards, and I don't have one handy to test either.  By the way, while vainfo reports a good status for me, mplayer always segfaults (and I tried several builds).  The whole thing is very beta and doesn't seem to work for everyone.

Reinstalled the latest ATI drivers, vainfo working, Mplayer crashing :-(

I guess at this point I would have to wait for "unbug" the stuff by those who know ... :-)

```

MPlayer SVN-r29834-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing [****name removed by the author*****].mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC) "Video: x264_L4.1 @ 11000 Kbps", -vid 0
[mkv] Track ID 2: audio (A_DTS) "Audio: English DTS 5.1 @ 1.5 Mbps", -aid 0, -alang eng
[mkv] Track ID 3: audio (A_AC3) "Commentary: English Dolby Digital 2.0 @ 192 Kbps", -aid 1, -alang eng
[mkv] Track ID 4: subtitles (S_TEXT/UTF8) "English", -sid 0, -slang eng
[mkv] Track ID 5: subtitles (S_TEXT/UTF8) "English_SDH", -sid 1, -slang eng
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1920x1040  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
libva: libva version 0.31.0-sds3
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/fglrx_drv_video.so
libva: va_openDriver() returns 0
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[VD_FFMPEG] VA API accelerated codec.
[VD_FFMPEG] Trying pixfmt=0.
Unsupported PixelFormat -1
Movie-Aspect is 1.85:1 - prescaling to correct movie aspect.
VO: [vaapi] 1920x1040 => 1920x1040 H.264 VA API Acceleration 
[vo_vaapi] Using 1:1 VA surface mapping
[VD_FFMPEG] XVMC-accelerated MPEG-2.
[VD_FFMPEG] XVMC-accelerated MPEG-2.
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [libdca] DTS decoding with libdca
Stream with high frequencies VQ coding
AUDIO: 48000 Hz, 2 ch, s16le, 1536.0 kbit/100.00% (ratio: 192000->192000)
Selected audio codec: [dts] afm: libdca (DTS-libdca)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
[VD_FFMPEG] XVMC-accelerated MPEG-2.
Movie-Aspect is 1.85:1 - prescaling to correct movie aspect.
VO: [vaapi] 1920x1040 => 1920x1040 H.264 VA API Acceleration 
[vo_vaapi] vaPutSurface(): the requested function is not implemented
[vo_vaapi] vaPutSurface(): the requested function is not implemented
[vo_vaapi] vaPutSurface(): the requested function is not implemented
[vo_vaapi] vaPutSurface(): the requested function is not implemented
[vo_vaapi] vaPutSurface(): the requested function is not implemented
[vo_vaapi] vaPutSurface(): the requested function is not implemented
[vo_vaapi] vaPutSurface(): the requested function is not implemented
[vo_vaapi] vaPutSurface(): the requested function is not implemented
[vo_vaapi] vaPutSurface(): the requested function is not implemented
[vo_vaapi] vaPutSurface(): the requested function is not implemented
[vo_vaapi] vaPutSurface(): the requested function is not implemented
[vo_vaapi] vaPutSurface(): the requested function is not implemented
[vo_vaapi] vaPutSurface(): the requested function is not implemented
[vo_vaapi] vaPutSurface(): the requested function is not implemented
[vo_vaapi] vaPutSurface(): the requested function is not implemented
[vo_vaapi] vaPutSurface(): the requested function is not implemented
[vo_vaapi] vaPutSurface(): the requested function is not implemented
[vo_vaapi] vaPutSurface(): the requested function is not implemented
[vo_vaapi] vaPutSurface(): the requested function is not implemented
[vo_vaapi] vaPutSurface(): the requested function is not implemented
[vo_vaapi] vaPutSurface(): the requested function is not implemented
[vo_vaapi] vaPutSurface(): the requested function is not implemented
[vo_vaapi] vaPutSurface(): the requested function is not implemented
[vo_vaapi] vaPutSurface(): the requested function is not implemented
[vo_vaapi] vaPutSurface(): the requested function is not implemented
[vo_vaapi] vaPutSurface(): the requested function is not implemented
[vo_vaapi] vaPutSurface(): the requested function is not implemented
[vo_vaapi] vaPutSurface(): the requested function is not implemented
[vo_vaapi] vaPutSurface(): the requested function is not implemented
[vo_vaapi] vaPutSurface(): the requested function is not implemented
xvba_video: error: Assertion failed in file xvba_decode.c at line 774


MPlayer interrupted by signal 6 in module: decode video
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

```

---

### Post by doas777 on 2009-11-17
a "not_implemented" exception means that the code has not yet been written. your specific usecase is calling a function that is declared, but is just a stub, so it raises this error, instead of segfaulting. the hard break may imply that your compiler is not of the correct version for what xvba expects, but I'm no expert on video.

---

### Post by xzero1 on 2009-11-17
It is mentioned in the Phoronix thread that future fglrx drivers may not have support for UVD2 .  I have not tried the latest drivers. Try xvinfo to see if AVIVO textured video acceleration is supported. Also check xorg.0.log. 

You should see something like this:
(Note the fglrx version)

```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4770
OpenGL version string: 2.1.9026
``````
xvinfo
X-Video Extension version 2.2
screen #0
  Adaptor #0: "ATI Radeon AVIVO Video"
    number of ports: 4
    port base: 131
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
      depth 24, visualID 0x2b
      depth 24, visualID 0x2c
      depth 24, visualID 0x2d
      depth 24, visualID 0x2e
      depth 24, visualID 0x2f
      depth 24, visualID 0x30
      depth 24, visualID 0x31
      depth 24, visualID 0x32
      depth 24, visualID 0x33
      depth 24, visualID 0x34
      depth 24, visualID 0x35
      depth 24, visualID 0x36
      depth 24, visualID 0x37
      depth 24, visualID 0x38
      depth 24, visualID 0x39
      depth 24, visualID 0x3a
      depth 24, visualID 0x3b
      depth 24, visualID 0x3c
      depth 24, visualID 0x3d
      depth 24, visualID 0x3e
      depth 24, visualID 0x3f
      depth 24, visualID 0x40
      depth 24, visualID 0x41
      depth 24, visualID 0x42
      depth 24, visualID 0x43
      depth 24, visualID 0x44
      depth 24, visualID 0x45
      depth 24, visualID 0x46
      depth 24, visualID 0x47
      depth 24, visualID 0x48
      depth 24, visualID 0x49
      depth 24, visualID 0x4a
      depth 24, visualID 0x4b
      depth 24, visualID 0x4c
      depth 24, visualID 0x4d
      depth 24, visualID 0x4e
      depth 24, visualID 0x4f
      depth 24, visualID 0x50
      depth 24, visualID 0x51
      depth 24, visualID 0x52
      depth 24, visualID 0x53
      depth 24, visualID 0x54
      depth 24, visualID 0x55
      depth 24, visualID 0x56
      depth 24, visualID 0x57
      depth 24, visualID 0x58
      depth 24, visualID 0x59
      depth 24, visualID 0x5a
      depth 24, visualID 0x5b
      depth 24, visualID 0x5c
      depth 24, visualID 0x5d
      depth 24, visualID 0x5e
      depth 24, visualID 0x5f
      depth 24, visualID 0x60
      depth 24, visualID 0x61
      depth 24, visualID 0x62
      depth 24, visualID 0x63
      depth 24, visualID 0x64
      depth 24, visualID 0x65
      depth 24, visualID 0x66
      depth 24, visualID 0x67
      depth 24, visualID 0x68
      depth 24, visualID 0x69
      depth 24, visualID 0x6a
      depth 24, visualID 0x6b
      depth 24, visualID 0x6c
      depth 24, visualID 0x6d
      depth 24, visualID 0x6e
      depth 24, visualID 0x6f
      depth 24, visualID 0x70
      depth 24, visualID 0x71
      depth 24, visualID 0x72
    number of attributes: 10
      "XV_SET_DEFAULTS" (range 0 to 1)
              client settable attribute
      "XV_DOUBLE_BUFFER" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
      "XV_BRIGHTNESS" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_CONTRAST" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_SATURATION" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_COLOR" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_HUE" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_RED_INTENSITY" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_GREEN_INTENSITY" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_BLUE_INTENSITY" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
    maximum XvImage size: 4096 x 4096
    Number of image formats: 4
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
      id: 0x32595559 (YUY2)
        guid: 59555932-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x59565955 (UYVY)
        guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
``````
cat /var/log/Xorg.0.log | grep Textured
(**) fglrx(0): Textured Video is enabled.
```

---

### Post by Filipek on 2009-11-18
Everything you suggested seems to be alright:

```

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3850
OpenGL version string: 2.1.9116

```

```

xvinfo
X-Video Extension version 2.2
screen #0
  Adaptor #0: "ATI Radeon AVIVO Video"
    number of ports: 4
    port base: 131
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
      depth 24, visualID 0x2b
      depth 24, visualID 0x2c
      depth 24, visualID 0x2d
      depth 24, visualID 0x2e
      depth 24, visualID 0x2f
      depth 24, visualID 0x30
      depth 24, visualID 0x31
      depth 24, visualID 0x32
      depth 24, visualID 0x33
      depth 24, visualID 0x34
      depth 24, visualID 0x35
      depth 24, visualID 0x36
      depth 24, visualID 0x37
      depth 24, visualID 0x38
      depth 24, visualID 0x39
      depth 24, visualID 0x3a
      depth 24, visualID 0x3b
      depth 24, visualID 0x3c
      depth 24, visualID 0x3d
      depth 24, visualID 0x3e
      depth 24, visualID 0x3f
      depth 24, visualID 0x40
      depth 24, visualID 0x41
      depth 24, visualID 0x42
      depth 24, visualID 0x43
      depth 24, visualID 0x44
      depth 24, visualID 0x45
      depth 24, visualID 0x46
      depth 24, visualID 0x47
      depth 24, visualID 0x48
      depth 24, visualID 0x49
      depth 24, visualID 0x4a
      depth 24, visualID 0x4b
      depth 24, visualID 0x4c
      depth 24, visualID 0x4d
      depth 24, visualID 0x4e
      depth 24, visualID 0x4f
      depth 24, visualID 0x50
      depth 24, visualID 0x51
      depth 24, visualID 0x52
      depth 24, visualID 0x53
      depth 24, visualID 0x54
      depth 24, visualID 0x55
      depth 24, visualID 0x56
      depth 24, visualID 0x57
      depth 24, visualID 0x58
      depth 24, visualID 0x59
      depth 24, visualID 0x5a
      depth 24, visualID 0x5b
      depth 24, visualID 0x5c
      depth 24, visualID 0x5d
      depth 24, visualID 0x5e
      depth 24, visualID 0x5f
      depth 24, visualID 0x60
      depth 24, visualID 0x61
      depth 24, visualID 0x62
      depth 24, visualID 0x63
      depth 24, visualID 0x64
      depth 24, visualID 0x65
      depth 24, visualID 0x66
      depth 24, visualID 0x67
      depth 24, visualID 0x68
      depth 24, visualID 0x69
      depth 24, visualID 0x6a
      depth 24, visualID 0x6b
      depth 24, visualID 0x6c
      depth 24, visualID 0x6d
      depth 24, visualID 0x6e
      depth 24, visualID 0x6f
      depth 24, visualID 0x70
      depth 24, visualID 0x71
      depth 24, visualID 0x72
    number of attributes: 10
      "XV_SET_DEFAULTS" (range 0 to 1)
              client settable attribute
      "XV_DOUBLE_BUFFER" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
      "XV_BRIGHTNESS" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_CONTRAST" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_SATURATION" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_COLOR" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_HUE" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_RED_INTENSITY" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_GREEN_INTENSITY" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_BLUE_INTENSITY" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
    maximum XvImage size: 4096 x 4096
    Number of image formats: 4
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
      id: 0x32595559 (YUY2)
        guid: 59555932-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x59565955 (UYVY)
        guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)

```

```

cat /var/log/Xorg.0.log | grep Textured
(**) fglrx(0): Textured Video is enabled.

```

Any idea how can I benefit from these above working?

---

### Post by Yellow Pasque on 2009-11-18
The HD video accel is only supported on UVD2 cards (RadeonHD 4x00 or later). No love for your card: [http://www.phoronix.com/scan.php?page=article&item=amd_xvba_vaapi&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_xvba_vaapi&num=1)

---

### Post by xzero1 on 2009-11-18
> **Temüjin said:**
> The HD video accel is only supported on UVD2 cards (RadeonHD 4x00 or later). No love for your card: [http://www.phoronix.com/scan.php?page=article&item=amd_xvba_vaapi&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_xvba_vaapi&num=1)

It really depends on the actual chip on your card. There are different opinions on which card supports what. My best reference is here: [http://www.phoronix.com/forums/showpost.php?p=53818&postcount=45]("http://www.phoronix.com/forums/showpost.php?p=53818&postcount=45")

This could be the ultimate test:
> cat /var/log/Xorg.0.log | grep "XVideo-MotionCompensation"
If there are no errors with loading after this log line, you should be good to go.
To use XvMC, all that was needed with my setup was the proper mplayer using -vo xv driver option.

I mentioned that the mplayer that you compiled should support XvMC because when I use it currently it seems to perform as it previously did on my on board GPU but since I now use a 4770 card, I cannot be sure. The real experts seem to be on the Phoronix forums and even there it seems there are hits and misses with various hardware/software configurations. At the current time accelerated video in linux is "unsupported"  at best.


If you are not willing to give up yet, its possible some xorg option could be the problem. I have posted my old working xorg.conf. Hopefully it will be helpful.

---

### Post by Yellow Pasque on 2009-11-18
> **xzero1 said:**
> It really depends on the actual chip on your card. There are different opinions on which card supports what. My best reference is here: [http://www.phoronix.com/forums/showpost.php?p=53818&postcount=45]("http://www.phoronix.com/forums/showpost.php?p=53818&postcount=45")

Ok, so it's RadeonHD 4x00 and later plus 7x0 IGP's. Still no love for the card in question.

---

### Post by Melcar on 2009-11-18
Hopefully they eventually extend XvBA support to old UVD cards.

---

### Post by Yellow Pasque on 2009-11-18
> **Melcar said:**
> Hopefully they eventually extend XvBA support to old UVD cards.
Don't count on it, but eventually, the older HD cards should have open-source video accel using shaders when Gallium3D matures.

---

### Post by xzero1 on 2009-11-18
Well another option might just be the open source radeon driver which at least seems to accelerate the display part of the video chain and has support for older gpus. Playing a 720p video using 4% cpu ain't bad! See post #48 in this thread:
[http://www.phoronix.com/forums/showthread.php?t=7993](http://www.phoronix.com/forums/showthread.php?t=7993)

I seem to remember playing hd videos with the default Karmic driver during pre-release testing, but that may have been 720p only and I have a pretty fast 3Ghz Phenom II.

I don't know what would be involved getting it to work but note that this is a fairly old thread.

The current driver status is here:

[http://xorg.freedesktop.org/wiki/RadeonFeature](http://xorg.freedesktop.org/wiki/RadeonFeature)

If you decide to try this please let us know how it worked out.

---

### Post by Filipek on 2009-11-19
> **xzero1 said:**
> Well another option might just be the open source radeon driver which at least seems to accelerate the display part of the video chain and has support for older gpus. Playing a 720p video using 4% cpu ain't bad! See post #48 in this thread:
[http://www.phoronix.com/forums/showthread.php?t=7993](http://www.phoronix.com/forums/showthread.php?t=7993)

I seem to remember playing hd videos with the default Karmic driver during pre-release testing, but that may have been 720p only and I have a pretty fast 3Ghz Phenom II.

I don't know what would be involved getting it to work but note that this is a fairly old thread.

The current driver status is here:

[http://xorg.freedesktop.org/wiki/RadeonFeature](http://xorg.freedesktop.org/wiki/RadeonFeature)

If you decide to try this please let us know how it worked out.

I will probably try that. The only things that keeps me reluctant is the fact that everything else in terms of 3D or graphics runs perfectly now. Since I am not that experienced, is there some "clear" way how to:

1) remove the official driver
2) try open one
3) if something else is bad - do it vice versa

I know myself - I will test it :-) But would like to be prepared for the worst...

***Edit:** The list on the link states XvMC always in a TODO status. Am I missing something or this is the feature which should handle the "off-loading" of HD playback to graphic card? Sorry for being lame - I am just trying to get to know the stuff as much as possible while being a layman at the first place.*

---

### Post by Yellow Pasque on 2009-11-19
To try open-source drivers:
[http://ubuntuforums.org/showpost.php?p=8340519&postcount=12](http://ubuntuforums.org/showpost.php?p=8340519&postcount=12)

I don't recommend you do that, though, because it involves installing a new kernel to get 3D acceleration. Lots of things could go wrong there.

---

### Post by xzero1 on 2009-11-19
> **Filipek said:**
> I will probably try that. The only things that keeps me reluctant is the fact that everything else in terms of 3D or graphics runs perfectly now. Since I am not that experienced, is there some "clear" way how to:

1) remove the official driver
2) try open one
3) if something else is bad - do it vice versa

I know myself - I will test it :-) But would like to be prepared for the worst...

***Edit:** The list on the link states XvMC always in a TODO status. Am I missing something or this is the feature which should handle the "off-loading" of HD playback to graphic card? Sorry for being lame - I am just trying to get to know the stuff as much as possible while being a layman at the first place.*

Absolutely correct about XvMC but note that "Textured Xv" and "2d EXA acceleration" are there. The cpu will do the decode work and the rendering will have some hw assist. At least thats how I think it works*. I also note that the mentioned post is old -- about 2 years old. It is possible that this is implemented in the stock Karmic (radeon) driver (just check the excellent Ubuntu documentation:P).

 That makes it easy -- boot from the cd, install the latest mplayer, check for the required options and you should be good to go. If it works removing your current fglrx driver via hardware drivers should revert back to the stock radeon driver.

* See post # 255
[http://www.phoronix.com/forums/showthread.php?t=19983&page=26](http://www.phoronix.com/forums/showthread.php?t=19983&page=26)

If all else fails then to quote Temujin "...Lots of things could go wrong there.":)

---

### Post by Wistful on 2009-11-19
I was able to play H.264 encoded videos using MPlayer as following:  ```
mplayer -framedrop -lavdopts fast:skiploopfilter=all filename.mkv
```

After that to enter FullScreen press **f**

Edit: [https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)

---

### Post by Filipek on 2009-11-23
> **Wistful said:**
> I was able to play H.264 encoded videos using MPlayer as following:  ```
mplayer -fs -framedrop -lavdopts fast:skiploopfilter=all filename.mkv
```

Edit: [https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)

Thank you - will try that out!

---

### Post by xzero1 on 2009-11-23
Since you have a 3850, this post #339 is on point.

> 
Well I finaly got round to trying this and to my suprise it actually works.
Suprise because my card isn't listed as UVD2. It's an rv670 Sapphire radeon HD3850 AGP which according to wikipedia is UVD+, though I thought I'd give it a try as someone else in the thread mentioned success with a 2xxx.

Not all streams work, but broadcast BBC does, it even manages to de-interlace in the MBAFF case which is more that ffmpeg does. It doesn't de-int "normal" interlaced, though.[http://www.phoronix.com/forums/showthread.php?t=19983&page=34](http://www.phoronix.com/forums/showthread.php?t=19983&page=34)

---

### Post by ssivil on 2009-12-12
Using totem, if I choose to watch a 1080p movie, the video size does not change from whatever size the previous movie was.  It the previous video size was set watching a 480p video, then watching a new 1080p movie uses that size too even though I set it to automatically adjust the size in the preferences.

If I use the Gecko Media player plug-in, it adjusts the sizes for all the videos correctly.

I have a fast connection (16755/2106), so choppiness is not an issue with either player .

Can anyone suggest what I might do to get 1080p's movies to size correctly using Totem?

Thank you.

---

