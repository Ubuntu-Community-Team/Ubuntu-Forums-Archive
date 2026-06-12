---
title: "Still no wmv3 encoder for linux"
date: 2014-06-23
forum: Multimedia Software
---

### Post by ben90 on 2014-06-23
Hello there i m trying to encode some video files to wmv3.. unfortunately it seems like there s no way to do so on linux..

Since ffmpeg is deprecated i tried avconv, with no luck.. wmv1 and 2 are no problem, but with wmv3, it say
Uknown encoder wmv3

Anyone knows another way to do so?


Thanks a lot

ben

---

### Post by SeijiSensei on 2014-06-23
A quick check suggests there are no open source encoders for WMV3.  If there were one, I'd expect to find it in ffmpeg.

---

### Post by andrew.46 on 2014-06-23
FFmpeg is most definitely not deprecated! Current state of play with wmv encoding with FFmpeg:

```

andrew@ilium~$**[COLOR="#FF0000"] ffmpeg -encoders 2>/dev/null | grep -i wmv[/COLOR]**
 V..... wmv1                 Windows Media Video 7
 V..... wmv2                 Windows Media Video 8

```

There are alternatives of course...

---

### Post by ben90 on 2014-06-24
Hey, thanks..

I ve checked some alternatives of course, with no luck.. I guess i have to go for windows.. meh. :/

Thanks anyway

---

### Post by MartyBuntu on 2014-06-24
Any reason you're choosing WMV?

---

### Post by ben90 on 2014-06-24
It s for a project, i have to use it though... :/

Personally i d never come up with the idea to use wmv3 ;)

---

### Post by ben90 on 2014-06-24
> **andrew.46 said:**
> FFmpeg is most definitely not deprecated! Current state of play with wmv encoding with FFmpeg:

```

andrew@ilium~$**[COLOR=#FF0000] ffmpeg -encoders 2>/dev/null | grep -i wmv[/COLOR]**
 V..... wmv1                 Windows Media Video 7
 V..... wmv2                 Windows Media Video 8

```

There are alternatives of course...

just saying what my console says...
```

ffmpeg version 0.8.12-4:0.8.12-0ubuntu0.12.04.1, Copyright (c) 2000-2014 the Libav developers
  built on Jun 10 2014 15:32:44 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.

```

---

### Post by andrew.46 on 2014-06-24
The 'deprecated' message is a shameful ploy in an emotional fork from FFmpeg to libav...

---

### Post by monkeybrain20122 on 2014-06-24
Actually in 14.04 there is no longer any ffmpeg package in the repo, if you install it via ppa, e.g [https://bugs.launchpad.net/~mc3man/+archive/trusty-media](https://bugs.launchpad.net/~mc3man/+archive/trusty-media) or [https://launchpad.net/~samrog131/+archive/ppa](https://launchpad.net/~samrog131/+archive/ppa) and type ffmpeg in  the terminal you get the normal outputs instead of the 'deprecated' message.  

In earlier Ubuntu releases there is a fake ffmpeg package which is actually avcon, if you install that and type ffmpeg in the terminal you would get the 'ffmpeg is deprecated' message.  To fix it you can either compile a static copy ffmpeg  yourself (check the tutorial section on this forum) or install ffmpeg, ffmpeg-set-alternatives  using samrog's ppa above and run 'sudo update-alternatives --config ffmpeg" in the terminal to choose the real ffmpeg as default (or install glaternatives and use the gui to switch)

From my Ubuntu 13.10
```
$ ffmpeg
ffmpeg version 2.1.4 Copyright (c) 2000-2014 the FFmpeg developers
  built on Feb 27 2014 17:49:29 with gcc 4.8 (Ubuntu/Linaro 4.8.1-10ubuntu9)
  configuration: --prefix=/opt/ffmpeg --libdir=/opt/ffmpeg/lib/ --enable-shared --disable-stripping --enable-gpl --enable-version3 --enable-runtime-cpudetect --enable-postproc --enable-x11grab --enable-libcdio --enable-vaapi --enable-vdpau --enable-bzlib --enable-gnutls --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-libfaac --enable-libvo-aacenc --enable-nonfree --enable-libmp3lame --enable-libx264 --enable-libxvid --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libfdk_aac --enable-libopus --enable-pthreads --enable-zlib --enable-libvpx --enable-libfreetype --enable-libpulse
  libavutil      52. 48.101 / 52. 48.101
  libavcodec     55. 39.101 / 55. 39.101
  libavformat    55. 19.104 / 55. 19.104
  libavdevice    55.  5.100 / 55.  5.100
  libavfilter     3. 90.100 /  3. 90.100
  libswscale      2.  5.101 /  2.  5.101
  libswresample   0. 17.104 /  0. 17.104
  libpostproc    52.  3.100 / 52.  3.100
Hyper fast Audio and Video encoder
```

---

### Post by QIII on 2014-06-24
"Shameful", "emotional"?  Not by Canonical.

The ffmpeg maintainer for Debian and Ubuntu was the one of the developers who forked the project after internal disputes about the project.  There is nothing shameful or emotional on the part of Canonical.

---

### Post by mc4man on 2014-06-24
> **QIII said:**
> "Shameful", "emotional"?  Not by Canonical.

The ffmpeg maintainer for Debian and Ubuntu was the one of the developers who forked the project after internal disputes about the project.  There is nothing shameful or emotional on the part of Canonical.

It's a bit from one's point of view...
The orig. message was quite inaccurate & misleading. In some attempts to get that changed to a more accurate message all suggested were unacceptable to Reinhard Tartler 
The current message crafted by an Ubuntu dev was finally deemed ok. 
(plus the bug report title & descript were also altered to placate Mr. Tartler

---

### Post by Yellow Pasque on 2014-06-24
> **QIII said:**
> The ffmpeg maintainer for Debian and Ubuntu was the one of the developers who forked the project after internal disputes about the project.  There is nothing shameful or emotional on the part of Canonical.

Canonical could have continued using ffmpeg instead of just following Debian down the libav path, (or at least fixed the warning before releasing). So no, they didn't create the nonsense fork situation or write the warning, but ultimately, they're complicit since they allowed it to be released.
Getting way off topic though...

As for wmv3 encoder, I see there were a few proposed patched for ffmpeg, but they never made it in. I'm not sure if that's for legal reasons (MS didn't release specs for wmv3/9) or because no one ever cared enough to get the patches included.

---

### Post by ben90 on 2014-06-25
at least this thread gets kinda interesting :D

Thanks guys ;)

---

### Post by andrew.46 on 2014-06-25
> **Temüjin said:**
> As for wmv3 encoder, I see there were a few proposed patched for ffmpeg, but they never made it in. I'm not sure if that's for legal reasons (MS didn't release specs for wmv3/9) or because no one ever cared enough to get the patches included.

Back in 2007 by the look of it. Michael Niedermeyer [has some some strong views on wmv3]("http://lists.ffmpeg.org/pipermail/ffmpeg-devel/2007-June/031464.html") by the look of it :).

---

### Post by squakie on 2014-06-25
> **ben90 said:**
> at least this thread gets kinda interesting :D

Thanks guys ;)
Yeah - you should do a search on why ffmpeg has been split.  It appears to me to be one person trying to control the entire project - even including what does or does go into it.  It depends on your point of view when you read everything, but to me it appears some things were held out of ffmpeg due to "it wasn't mine and not done my way".  Perhaps that person is entitled to that I can't judge - I don't enough about any of it to be one to judge.

---

### Post by monkeybrain20122 on 2014-06-25
> **squakie said:**
> Yeah - you should do a search on why ffmpeg has been split.  It appears to me to be one person trying to control the entire project - even including what does or does go into it.  It depends on your point of view when you read everything, but to me it appears some things were held out of ffmpeg due to "it wasn't mine and not done my way".  Perhaps that person is entitled to that I can't judge - I don't enough about any of it to be one to judge.

It gets more dramatic. According to one account ([http://blog.pkh.me/p/13-the-ffmpeg-libav-situation.html](http://blog.pkh.me/p/13-the-ffmpeg-libav-situation.html)) the dictator later reformed himself and is now the good guy, the rebels however continue to carry their rancour and turn their project into their little fiefdom.  I guess there are two main forces that drive people, money and ego. Free software is not so much about money.. :)

---

### Post by squakie on 2014-06-25
If it weren't for some of the problems it causes some people, it would just be amusing! ;)    The human animal can be quite strange at times - that's why I'm just visiting this planet :)

---

