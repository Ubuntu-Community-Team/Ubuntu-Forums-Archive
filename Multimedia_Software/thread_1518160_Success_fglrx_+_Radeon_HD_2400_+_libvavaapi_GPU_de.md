---
title: "Success: fglrx + Radeon HD 2400 + libva/vaapi GPU decoding"
date: 2010-06-26
forum: Multimedia Software
---

### Post by der_hede on 2010-06-26
Hi,

I'm owning an old single Core AMD (Opteron 148, like Athlon 64 3200+), it can't play h264 1080p-Videos without framedrops in active scenes.

I'm also owning an not so old AMD/Ati Radeon HD 2400. It's not an UVD2 card, it's not even UVD+, its UVD i.e. UVD1.

All articles regarding GPU h264 decoding I've found so far are saying "for vaapi gpu decoding on linux you need to have a UVD2 card". That's wrong! My UVD1-Card is playing fine some demo movies. :-D

Setup:
Ubuntu "Lucid" 10.4
"deb http://ppa.launchpad.net/nvidia-vdpau/cutting-edge-multimedia/ubuntu lucid main" in /etc/apt/sources.list.d/cutting-edge-multimedia.list
libva1 0.31.0+sds13-1~multimediappa2
mplayer 1.0~rc3+svn20100602-0ubuntu1~lucid~multimediappa1
xvba-video_0.6.11-1_amd64.deb from [http://www.splitted-desktop.com/~gbeauchesne/xvba-video/](http://www.splitted-desktop.com/~gbeauchesne/xvba-video/)
fglrx 8.732-0ubuntu1 (Catalyst 10.5 from amd.com)

(With the original Ubuntu Lucid fglrx (8.723) there's some error, I don't remember the words. It doesn't work for me)

It's working. I can play h.264 HD Videos with mplayer and decode it with a Radeon GPU. vlc 1.2 not working so far. It seems it's decoding fine, but screen remains green.

[_Here's a screenshot, no fake!_]("http://www.der-he.de/data/HD-Video-decoding-with-linux-and-HD2400.png") 
It's a two Monitor setup with fglrx' big Desktop. On the right there's running a movie Trailer (I Am Legend) and on the left there's some status info. Quality is not perfect (as you can see, horizontal displacement), but it's basically working.

---

### Post by der_hede on 2010-06-26
vainfo:
$ vainfo 
libva: libva version 0.31.0-sds6
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA API version: 0.31
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA API - 0.6.11
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :	VAEntrypointIDCT
      VAProfileMPEG2Main              :	VAEntrypointIDCT
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD

---

### Post by forumache on 2010-07-01
Great news!

I have a HD3450 (UVD+) and I'm going to try this.

Thanks.

---

### Post by nesquik on 2010-10-23
Got it working, too (Radeon HD 4200).

---

### Post by nesquik on 2010-10-23
Even VLC works. Nice.

---

