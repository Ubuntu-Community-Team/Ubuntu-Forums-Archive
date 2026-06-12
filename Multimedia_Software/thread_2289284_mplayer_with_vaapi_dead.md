---
title: "mplayer with vaapi dead?"
date: 2015-08-02
forum: Multimedia Software
---

### Post by spot-draves on 2015-08-02
for years I used mplayer with vaapi support and was quite happy with the results.
recently, i was forced to upgrade to 14.10 because the intel drivers require it.
however, mplayer-vaapi PPA has not been updated past 14.04.

i tried using mpv but have found playback glitches sometimes, it's not quite as reliable as good-old mplayer.

is mplayer with vaapi dead?  is there any way to get it?

---

### Post by mc4man on 2015-08-02
mplayer-vaapi (from splitted-desktop) is as dead as they come. 
Ask mplayer to add vaapi support directly.. (2.5 years & counting

Edit: you could maybe make use of libvdpau-va-gl1 instead which should work ok with mplayer, at least on Intel gpu's

Ex. - 
```
env VDPAU_DRIVER=va_gl mplayer -vo vdpau -vc ffh264vdpau Videos/amostviolentyear-nowplaying_h1080p.mkv
```

```
MPlayer SVN-r37401 (C) 2000-2012 MPlayer Team
Playing Videos/amostviolentyear-nowplaying_h1080p.mkv.
libavformat version 56.33.101 (internal)
libavformat file format detected.
[lavf] stream 0: video (h264), -vid 0
[lavf] stream 1: audio (mp3), -aid 0
VIDEO:  [H264]  1920x816  0bpp  23.000 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 encoder: libebml v1.3.0 + libmatroska v1.4.1
 creation_time: 2015-07-25 01:59:35
Load subtitles in Videos/
[VS] Software VDPAU backend library initialized
libva info: VA-API version 0.38.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_0_38
libva info: va_openDriver() returns 0
==========================================================================
Forced video codec: ffh264vdpau
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 56.39.101 (internal)
Selected video codec: [ffh264vdpau] vfm: ffmpeg (FFmpeg H.264 (VDPAU))
==========================================================================
==========================================================================
Opening audio decoder: [mpg123] MPEG 1.0/2.0/2.5 layers I, II, III
AUDIO: 44100 Hz, 2 ch, s16le, 32.0 kbit/2.27% (ratio: 4000->176400)
Selected audio codec: [mpg123] afm: mpg123 (MPEG 1.0/2.0/2.5 layers I, II, III)
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
Movie-Aspect is 2.35:1 - prescaling to correct movie aspect.
VO: [vdpau] 1920x816 => 1920x816 H.264 VDPAU acceleration 
Movie-Aspect is 2.35:1 - prescaling to correct movie aspect.
VO: [vdpau] 1920x816 => 1920x816 H.264 VDPAU acceleration 

```

---

### Post by monkeybrain20122 on 2015-08-03
libvdpau-va-gl as suggested above or use mpv which supports vaapi (I find it better than mplayer, maybe you need to get an up to date version)

You can use libvdpau-va-gl automatically by adding
```
export VDPAU_DRIVER=va_gl
```
  to /etc/environment
and reboot.

So you can use vdpau for flash as well, for example (if enabled)

---

### Post by spot-draves on 2015-08-03
Thanks guys.  I tried installing libvdpau-va-gl from ppa [http://ppa.webupd8.org/post/74056138140/libvdpau-va-gl-031-available-in-ppa](http://ppa.webupd8.org/post/74056138140/libvdpau-va-gl-031-available-in-ppa)
but it was not available for 14.10 or newer, as required by intel drivers :(
but i was able to compile it from source, the instructions on [https://github.com/i-rinat/libvdpau-va-gl](https://github.com/i-rinat/libvdpau-va-gl) seem to work!
but then mplayer still fails with this weird error:

libva info: VA-API version 0.37.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_0_37
libva info: va_openDriver() returns 0
Forced video codec: ffh264vdpau
Cannot find codec 'h264_vdpau' in libavcodec...
Video decoder init failed for codecs.conf entry "ffh264vdpau".
Cannot find codec matching selected -vo and video format 0x34363248.

it seems to be just broken:
[https://bugs.launchpad.net/ubuntu/+source/libav/+bug/1374825](https://bugs.launchpad.net/ubuntu/+source/libav/+bug/1374825)
:(

monkeybrain, i DID try mpv but it has a slight stutter, it drops a few frames about once a minute.
mplayer *never* dropped.

i will take it up with mpv, we might as well move forward fixing bugs instead of trying to revive the dead.

thanks again.

---

### Post by monkeybrain20122 on 2015-08-03
Isn't 14.10 eol already? I would either do a fresh install of 15.04 or 14.04,--with updated driver from e.g oibaf's ppa. I have no issue with either but 14.10 was quite bad on my machine (tested for two weeks on an external drive and decided to stick with 14.04, then installed 15.04 later)

P.s. mpv never has any problem here, on two different machines (Intel with vaapi and AMD with vdpau) and have used it for both 15.04 and 14.04. I used mplayer with the gecko-mediaplayer in 14.04 using libvdpau-va-gl, video and audio were out of sync after a while for some 1080p videos (no issues with mpv firefox addon with vaapi or vdpau-va-gl) But instead of installing from the repo (0.8?) I always get the latest from master.

---

### Post by mc4man on 2015-08-04
> **monkeybrain20122 said:**
> Isn't 14.10 eol already? I would either do a fresh install of 15.04 or 14.04,--with updated driver from e.g oibaf's ppa. 
It should be noted (& I recently got oibaf to make clear on ppa page) that his ppa is only for 14.04 or 14.04.1 image installs. 14.04.2/3/4/5 will fail miserably.

---

### Post by mc4man on 2015-08-04
> **spot-draves said:**
> Thanks guys.  I tried installing libvdpau-va-gl from ppa [http://ppa.webupd8.org/post/74056138140/libvdpau-va-gl-031-available-in-ppa](http://ppa.webupd8.org/post/74056138140/libvdpau-va-gl-031-available-in-ppa)
but it was not available for 14.10 or newer, as required by intel drivers :(
but i was able to compile it from source, the instructions on [https://github.com/i-rinat/libvdpau-va-gl](https://github.com/i-rinat/libvdpau-va-gl) seem to work!
but then mplayer still fails with this weird error:

libva info: VA-API version 0.37.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_0_37
libva info: va_openDriver() returns 0
Forced video codec: ffh264vdpau
Cannot find codec 'h264_vdpau' in libavcodec...
Video decoder init failed for codecs.conf entry "ffh264vdpau".
Cannot find codec matching selected -vo and video format 0x34363248.

it seems to be just broken:
[https://bugs.launchpad.net/ubuntu/+source/libav/+bug/1374825](https://bugs.launchpad.net/ubuntu/+source/libav/+bug/1374825)
:(

monkeybrain, i DID try mpv but it has a slight stutter, it drops a few frames about once a minute.
mplayer *never* dropped.

i will take it up with mpv, we might as well move forward fixing bugs instead of trying to revive the dead.

thanks again.
libav in 14.10 is borked - 
[https://bugs.launchpad.net/ubuntu/+source/libav/+bug/1374825](https://bugs.launchpad.net/ubuntu/+source/libav/+bug/1374825)
If you want a better mplayer in 14.10 (14.10 should be dead & buried) you may still be able to build or get a build from here with embedded ffmpeg. Whether 14.10 repos are still open to satisfy deps is unknown to me as I dumped 14.10 before release - it was that bad...
[https://launchpad.net/~mc3man/+archive/ubuntu/mplayer-test](https://launchpad.net/~mc3man/+archive/ubuntu/mplayer-test)

Better to do as suggested & either use 15.04 or 14.04.x

---

### Post by monkeybrain20122 on 2015-08-04
> **mc4man said:**
> It should be noted (& I recently got oibaf to make clear on ppa page) that his ppa is only for 14.04 or 14.04.1 image installs. 14.04.2/3/4/5 will fail miserably.

Yes, same is true for xorg-edgers. I guess problem is the lts hardware enablement (I started with 14.04 image and added oibaf, then upgraded normally to 14.04.2 with no problem) But I am not able to find any download link for 14.04 or 14.04.1 in Ubuntu's download page, so OP probably have to go 15.04 (which is new  enough for his hardware without oibaf)

---

### Post by Yellow Pasque on 2015-08-04
> i will take it up with mpv, we might as well move forward fixing bugs instead of trying to revive the dead.
That seems like the best idea.

> **monkeybrain20122 said:**
> But I am not able to find any download link for 14.04 or 14.04.1 in Ubuntu's download page

Older LTS point releases get moved to: [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

---

### Post by spot-draves on 2015-08-04
> **monkeybrain20122 said:**
> I would either do a fresh install of 15.04 or 14.04

unfortunately the intel drivers require 14.10: [https://01.org/linuxgraphics/downloads/intel-graphics-installer-linux-1.1.0](https://01.org/linuxgraphics/downloads/intel-graphics-installer-linux-1.1.0)

---

### Post by monkeybrain20122 on 2015-08-05
> **spot-draves said:**
> unfortunately the intel drivers require 14.10: [https://01.org/linuxgraphics/downloads/intel-graphics-installer-linux-1.1.0](https://01.org/linuxgraphics/downloads/intel-graphics-installer-linux-1.1.0)

It says the intel driver is basically the same as 15.04's so there is no need to provide a driver for it.

See last post [https://01.org/linuxgraphics/forum/graphics-installer-discussions/ubuntu-15.04-intel-graphics](https://01.org/linuxgraphics/forum/graphics-installer-discussions/ubuntu-15.04-intel-graphics)

---

### Post by Yellow Pasque on 2015-08-05
> **spot-draves said:**
> unfortunately the intel drivers require 14.10: [https://01.org/linuxgraphics/downloads/intel-graphics-installer-linux-1.1.0](https://01.org/linuxgraphics/downloads/intel-graphics-installer-linux-1.1.0)

Do not use that site. It is a bad idea for end users to install video drivers directly from the manufacturer. It's also a bad idea to use an EOL/insecure release like 14.10.

---

