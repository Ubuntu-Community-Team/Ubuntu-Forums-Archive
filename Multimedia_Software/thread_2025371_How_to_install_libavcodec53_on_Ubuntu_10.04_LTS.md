---
title: "How to install libavcodec53 on Ubuntu 10.04 LTS?"
date: 2012-07-14
forum: Multimedia Software
---

### Post by resander on 2012-07-14
I have libavcodec52 (ffmpeg codec library) on the system but I need to run an application (that I have to build from source) that depends on version libavcodec53. This library is available for Ubuntu 12.04 and 11.10 but not for Ubuntu 10.04. I checked with Synaptic manager on 10.04 and it does not does not show libavcodec53 as a choice, only libavcodec52.

I cannot move away from Ubuntu 10.04 LTS (because of the Long Term Support).


Q1. libavcodec53 contains a codec for video standard H264. Are there Ubuntu applications that use H264 (or other codecs in libavcodec53) that I can try to install from Ubuntu 10.04 using Synaptic or the Ubuntu Software Centre? I assume installation of such applications would pull in libavcodec53 automatically.   

Q2. so far I have only used the Ubuntu Update Manager for upgrading packages so I lack knowledge about how to obtain them in other ways.

Advice would be most appreciated.

---

### Post by jmfal on 2012-07-14
That file is from the medibuntu repo

---

### Post by FakeOutdoorsman on 2012-07-14
> **resander said:**
> Q1. libavcodec53 contains a codec for video standard H264.
ffmpeg from the repository can decode H.264 without any additional packages. To enable libx264 (the H.264 encoder) then you must install **libavcodec-extra-52**.

> **resander said:**
> Are there Ubuntu applications that use H264 (or other codecs in libavcodec53) that I can try to install from Ubuntu 10.04 using Synaptic or the Ubuntu Software Centre?
There is no libavcodec53 available in the official repository for 10.04. If you need a newer ffmpeg than what the repository offers you can compile ffmpeg: [Compile FFmpeg on Ubuntu Lucid Lynx 10.04 LTS](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuideLucid). [Jon Severinsson's FFmpeg PPA](https://launchpad.net/~jon-severinsson/+archive/ffmpeg) may also provide a newer ffmpeg. Static Linux builds are also available (where you simply download and run): [FFmpeg Static Builds by Burek](http://ffmpeg.gusari.org/static/) or [FFmpeg Static Builds by Relaxed](dl.dropbox.com/u/24633983/ffmpeg/index.html).

> **resander said:**
> Q2. so far I have only used the Ubuntu Update Manager for upgrading packages so I lack knowledge about how to obtain them in other ways.
I generally open Terminal and use *apt-get*:
```
sudo apt-get install ffmpeg libavcodec-extra-52
```

> **jmfal said:**
> That file is from the medibuntu repo

Medibuntu does not provide libavcodec53 for 10.04 and it is not a good idea to mix packages from different Ubuntu versions.

---

