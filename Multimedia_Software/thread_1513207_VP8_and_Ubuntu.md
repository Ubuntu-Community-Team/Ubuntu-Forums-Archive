---
title: "VP8 and Ubuntu"
date: 2010-06-19
forum: Multimedia Software
---

### Post by Emanuele_Z on 2010-06-19
Hi guys, 

does anyone have compiled ffmpeg/mplayer with VP8 support and has released packages?

Just curious to see it in action!

Cheers,

---

### Post by Linuxforall on 2010-06-19
I did a few days back, runs fine, I used excellent andrew46's tutorial to compile mplayer and used Fake Outdoorsman's instructions to compile x264 and ffmpeg, both are available in the tutorial section. The web8 demo vid played without any glitches.

---

### Post by Emanuele_Z on 2010-06-19
> **Linuxforall said:**
> I did a few days back, runs fine, I used excellent andrew46's tutorial to compile mplayer and used Fake Outdoorsman's instructions to compile x264 and ffmpeg, both are available in the tutorial section. The web8 demo vid played without any glitches.
A link to this tutorial?

Cheers,

---

### Post by Florian Reinhard on 2010-06-19
you can get ffmpeg 0.6 there:
[https://launchpad.net/~nvidia-vdpau/+archive/cutting-edge-multimedia](https://launchpad.net/~nvidia-vdpau/+archive/cutting-edge-multimedia)

---

### Post by Emanuele_Z on 2010-06-19
> **Florian Reinhard said:**
> you can get ffmpeg 0.6 there:
[https://launchpad.net/~nvidia-vdpau/+archive/cutting-edge-multimedia](https://launchpad.net/~nvidia-vdpau/+archive/cutting-edge-multimedia)

Thanks mate.
I'm looking for libav* compiled with VP8 support as well.
Are these laying around somewhere?

Cheers,

---

### Post by Linuxforall on 2010-06-19
> **Emanuele_Z said:**
> A link to this tutorial?

Cheers,

ffmpeg, libvpx and x264 here at [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

mplayer here at [http://ubuntuforums.org/showthread.php?t=1305181&highlight=mplayer](http://ubuntuforums.org/showthread.php?t=1305181&highlight=mplayer)

For mplayer ignore gcc 3 and use command sudo apt-get install build-essential subversion checkinstall

also follow mac4man's advice on this page [http://ubuntuforums.org/showthread.php?t=1305181&highlight=mplayer&page=25](http://ubuntuforums.org/showthread.php?t=1305181&highlight=mplayer&page=25)

---

### Post by mc4man on 2010-06-19
> you can get ffmpeg 0.6 there:
[https://launchpad.net/~nvidia-vdpau/...dge-multimedia](https://launchpad.net/~nvidia-vdpau/...dge-multimedia)

That is a fairly interesting ppa, could prove useful to those who wish new builds of mplayer and vlc and don't wish to do themselves.

If using one should d. check that other apps that depend on ffmpeg shared libs aren't broken. (though he does provide some replacements.

---

### Post by Emanuele_Z on 2010-06-20
Well guys,

thanks for your hints, and thanks to that cutting edge repo I've done this quick analysis between VP8 and x264:
[http://qpsnr.youlink.org/vp8_x264/VP8_vs_x264.html](http://qpsnr.youlink.org/vp8_x264/VP8_vs_x264.html)

Please do tell me what you think!

Cheers,

---

### Post by pHr34kY on 2010-07-25
> **Emanuele_Z said:**
> Well guys,

thanks for your hints, and thanks to that cutting edge repo I've done this quick analysis between VP8 and x264:
[http://qpsnr.youlink.org/vp8_x264/VP8_vs_x264.html](http://qpsnr.youlink.org/vp8_x264/VP8_vs_x264.html)

Please do tell me what you think!

Cheers,

I like it!

Also, a REALLY good source video for doing this sort of thing is Big Buck Bunny:

[http://www.bigbuckbunny.org/index.php/download/](http://www.bigbuckbunny.org/index.php/download/)

There's a h.264 version there that goes for 9 minutes and is 700mb (stupidly high bitrate). If that's not enough, you can download every frame as a PNG, and the audio as FLAC.

---

### Post by andrew.46 on 2010-08-14
I have a reasonably complex guide which builds the development version of vlc with playback for WebM files (VP8 + Ogg):

Howto: Build the development version of vlc under Ubuntu
[http://ubuntuforums.org/showthread.php?t=1398119](http://ubuntuforums.org/showthread.php?t=1398119)

I attach a screenshot of a demo WebM file running in vlc-git...

Andrew

---

