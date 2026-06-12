---
title: "CMUS m4a playback issue"
date: 2014-05-22
forum: Multimedia Software
---

### Post by apark46 on 2014-05-22
Whenever I play an m4a file I get lots of static and distorted noise.
Then I get a segmentation fault (core dumped) error.
What's going wrong? How do I fix this?
They work through other players.

---

### Post by Yellow Pasque on 2014-05-22
[https://bugs.launchpad.net/ubuntu/+source/cmus/+bug/1311337](https://bugs.launchpad.net/ubuntu/+source/cmus/+bug/1311337)

---

### Post by apark46 on 2014-05-22
Awesome. Thank you.

---

### Post by apark46 on 2014-05-22
Actually... I have no idea what to do with this information.

---

### Post by Yellow Pasque on 2014-05-22
Build your own cmus from git or hope it appears in Ubuntu 14.10

---

### Post by vladimirtsoi on 2014-11-01
> **Temüjin said:**
> Build your own cmus from git or hope it appears in Ubuntu 14.10

I've built latest cmus but it just doesn't show m4a files (

---

### Post by mc4man on 2014-11-01
> **vladimirtsoi said:**
> I've built latest cmus but it just doesn't show m4a files (

It's probable that the ffmpeg plugin for cmus is garbage or close to it.
(may not have even been built 
 But for aac (.m4a) shouldn't need it. 
Try adding libmp4v2-dev,  then clean your cmus source, configure & build again.

from configure -
> checking for header <mp4v2/mp4v2.h>... yes
checking for header <neaacdec.h>... yes
checking for MP4_LIBS (-lmp4v2 -lfaad -lm)... yes
checking for header <neaacdec.h>... yes
checking for AAC_LIBS (-lfaad -lm)... yes


---

### Post by andrew.46 on 2014-11-02
cmus has an interesting idea of 'Priority' for its plugins:

```

andrew@ilium~$ **[COLOR="#FF0000"]cmus --plugins[/COLOR]**
Input Plugins: /usr/lib64/cmus/ip
  mad:
    Priority: 55
    File Types: mp3 mp2
    MIME Types: audio/mpeg audio/x-mp3 audio/x-mpeg
  aac:
    Priority: 50
    File Types: aac
    MIME Types: audio/aac audio/aacp
  cdio:
    Priority: 50
    File Types:
    MIME Types: x-content/audio-cdda
  vorbis:
    Priority: 50
    File Types: ogg oga ogx
    MIME Types: application/ogg audio/x-ogg
  wavpack:
    Priority: 50
    File Types: wv
    MIME Types: audio/x-wavpack
  mp4:
    Priority: 50
    File Types: mp4 m4a m4b
    MIME Types:
  opus:
    Priority: 50
    File Types: opus
    MIME Types:
  flac:
    Priority: 50
    File Types: flac fla
    MIME Types:
  wav:
    Priority: 50
    File Types: wav
    MIME Types:
  ffmpeg:
    Priority: 30
    File Types: ac3 aif aifc aiff ape au mka shn tta wma aac fla flac m4a m4b mp+ mp2 mp3 mp4 mpc mpp ogg wav wv
    MIME Types:

Output Plugins: /usr/lib64/cmus/op
  alsa
  oss
  ao
andrew@ilium~$ 

```

And it looks like aac files have a few possible plugins available to them with different priorities, I guess aac files can live as *.aac*, *.m4a* and even .*mp4*. I could not find documentation on the 'Priority' system unfortunately...

---

### Post by mc4man on 2014-11-02
> **andrew.46 said:**
> cmus has an interesting idea of 'Priority' for its plugins:
...

I'm gathering that it uses faad to decode aac (in the absence of the ffmpeg plugin) but needs mp4v2 if the aac is in a .m4a or .mp4
(- many players will accept video file & just playback the audio.

As far as the current state of the ffmpeg plugin in 14.04 I can't really (cleanly) test,  but on a vivid install it seems quite broken. (vivid would = utopic in this case
Between Debian & Ubuntu there has been a real lack of paying attention as of late when it comes to many 3rd party media apps, ie. if it builds from source then it's ok.

---

### Post by andrew.46 on 2014-11-02
I confess that I compiled cmus on my 'other' distro where it does not have a package as such simply [a script]("http://slackbuilds.org/repository/14.1/audio/cmus/"). I will test some of the formats that *exclusively* use the FFmpeg plugin however and see how it goes. Just for interest.....

---

### Post by mc4man on 2014-11-02
> **andrew.46 said:**
> I confess that I compiled cmus on my 'other' distro where it does not have a package as such simply [a script]("http://slackbuilds.org/repository/14.1/audio/cmus/"). I will test some of the formats that *exclusively* use the FFmpeg plugin however and see how it goes. Just for interest.....
At least here 2.6.0 during the configure will be -   "checking for successful build of ffmpeg.c... no" so in that case no plugin will be built
(read heading to ./scripts/ffmpeg_test.sh to see why..

In 2.5+ there is no ck. so the plugin is built (and worthless with libav10/11 & likely similar FFmpeg) though it may work or work to some extent with libav9

---

### Post by andrew.46 on 2014-11-03
Tested cmus with my *luckynight torture test *and all played well, including the problematic m4a files, so the FFmpeg plugin works well :). I attach a screenshot. I also bumped into a slightly annoying error which could do with a fix:

warning breaks cmus layout #191 
[https://github.com/cmus/cmus/issues/191](https://github.com/cmus/cmus/issues/191)

Warming to cmus quite a bit....

---

### Post by mc4man on 2014-11-03
> **andrew.46 said:**
> Tested cmus with my *luckynight torture test *and all played well, including the problematic m4a files, so the FFmpeg plugin works well :). I attach a screenshot. I also bumped into a slightly annoying error which could do with a fix:

warning breaks cmus layout #191 
[https://github.com/cmus/cmus/issues/191](https://github.com/cmus/cmus/issues/191)

Warming to cmus quite a bit....
I just checked on a live 14.04.1 session. While cmus will attempt playback thru ffmpeg plugin only .tta is good. 
.m4a, .ac3, .wma, & .ape all play with various degrees of audio distortion. (an issue with avresample?

How does this work in slack?, is ffmpeg static or shared & if the later what version (major) of libavcodec/libavformat

---

### Post by andrew.46 on 2014-11-03
> **mc4man said:**
> How does this work in slack?, is ffmpeg static or shared & if the later what version (major) of libavcodec/libavformat

This is my standard system install of a shared only FFmpeg (* --enable-shared --disable-static*):

```

  libavutil      54. 11.100 / 54. 11.100
  libavcodec     56. 10.100 / 56. 10.100
  libavformat    56. 11.100 / 56. 11.100
  libavdevice    56.  2.100 / 56.  2.100
  libavfilter     5.  2.100 /  5.  2.100
  libswscale      3.  1.101 /  3.  1.101
  libswresample   1.  1.100 /  1.  1.100
  libpostproc    53.  3.100 / 53.  3.100

```

This is latest git. Sound is as clear as a bell...

---

### Post by mc4man on 2014-11-03
> **andrew.46 said:**
> This is my standard system install of a shared only FFmpeg (* --enable-shared --disable-static*):

```

  libavutil      54. 11.100 / 54. 11.100
  libavcodec     56. 10.100 / 56. 10.100
  libavformat    56. 11.100 / 56. 11.100
  libavdevice    56.  2.100 / 56.  2.100
  libavfilter     5.  2.100 /  5.  2.100
  libswscale      3.  1.101 /  3.  1.101
  libswresample   1.  1.100 /  1.  1.100
  libpostproc    53.  3.100 / 53.  3.100

```

This is latest git. Sound is as clear as a bell...
So the difference is that in Debian/Ubuntu - 
libav is currently built with only libavresample (either 1 or 2), ex. here with libav11,  same would be seen in default 14.04 only w/ libav9 versions
> avconv -version
avconv version 11-6:11-1~ppa, Copyright (c) 2000-2014 the Libav developers
  built on Sep 28 2014 12:30:08 with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)
avconv 11-6:11-1~ppa
libavutil     54.  3. 0 / 54.  3. 0
libavcodec    56.  1. 0 / 56.  1. 0
libavformat   56.  1. 0 / 56.  1. 0
libavdevice   55.  0. 0 / 55.  0. 0
libavfilter    5.  0. 0 /  5.  0. 0
libavresample  2.  1. 0 /  2.  1. 0
libswscale     3.  0. 0 /  3.  0. 0


A shared build here of FFmpeg following the new Debian example, (libavcodec-ffmpegXX, ect.)  would have both libavresample & libswresample - 

> $ ffmpeg
ffmpeg version 2.4.2-1 Copyright (c) 2000-2014 the FFmpeg developers
  built on Oct 10 2014 15:27:21 with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)
....
libavutil      54.  7.100 / 54.  7.100
  libavcodec     56.  1.100 / 56.  1.100
  libavformat    56.  4.101 / 56.  4.101
  libavdevice    56.  0.100 / 56.  0.100
  libavfilter     5.  1.100 /  5.  1.100
  libavresample   2.  1.  0 /  2.  1.  0
  libswscale      3.  0.100 /  3.  0.100
  libswresample   1.  1.100 /  1.  1.100
  libpostproc    53.  0.100 / 53.  0.100

(static builds here always have both, though not a factor for cmus

So maybe I'll try rebuilding cmus to use ffmpeg shared & see if it uses libswresample better vs.  libavresample ...

Edit: that would also pose the question - does Slack purposely not build libavresample or what?

---

### Post by mc4man on 2014-11-03
> **mc4man said:**
> 

So maybe I'll try rebuilding cmus to use ffmpeg shared & see if it uses libswresample vs.  libavresample ...


so that works & cmus is ok (- 2.6.0 as 2.5.x is 'in-between', needs swresample patches but not the libav10/11 avresample patches
So all work & sound good with libswresample 

 ```
ldd  /usr/local/lib/cmus/ip/ffmpeg.so
	linux-vdso.so.1 =>  (0x00007fff5e90b000)
	libavformat-ffmpeg.so.56 => /usr/lib/x86_64-linux-gnu/libavformat-ffmpeg.so.56 (0x00007f0b9156d000)
	libswresample-ffmpeg.so.1 => /usr/lib/x86_64-linux-gnu/libswresample-ffmpeg.so.1 (0x00007f0b91353000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fd945e7e000)
	libavcodec-ffmpeg.so.56 => /usr/lib/x86_64-linux-gnu/libavcodec-ffmpeg.so.56 (0x00007fd944c85000)
	libavutil-ffmpeg.so.54 => /usr/lib/x86_64-linux-gnu/libavutil-ffmpeg.so.54 (0x00007fd944a29000)

       ....ect.

```

As far as the plugin in 14.04 - it doesn't appear to link to either resampler & in 15.04 it does but cmus segfaults on most ffmpeg plugin files (exception .tta
Ex. 15.04 - 
```
ldd /media/doug/f892b7c3-d1b7-4ee5-88d1-2e6db4362d2c/usr/lib/cmus/ip/ffmpeg.so |grep resample
	libavresample.so.2 => /usr/lib/x86_64-linux-gnu/libavresample.so.2 (0x00007f7bd68be000)
```

---

### Post by andrew.46 on 2014-11-03
> **mc4man said:**
> Edit: that would also pose the question - does Slack purposely not build libavresample or what?

There is no 'official' script or package for FFmpeg in Slackware, I actually use my own :). In my ignorance I thought it was a case of one or the other with libavresample and libswresample but I have been wrong many times before. I am not at home for the moment but I will check my script in a few hours, is there perhaps a ./configure option to build both? Mind you my system has managed without the libav tool for a long time....

**Edit:** Home now and I see that by default libavresample is *not* built:

```

  --enable-avresample      enable libavresample build [no]

```

I might leave it that way just for the moment...

---

### Post by mc4man on 2014-11-04
> **andrew.46 said:**
> 

**Edit:** Home now and I see that by default libavresample is *not* built:

```

  --enable-avresample      enable libavresample build [no]

```

I might leave it that way just for the moment...
I don't now why libav  maintainers choose to only enable avresample, could be anything almost.

The advantage as I have here with ffmpeg shared is that either of the  -dev's can be used as appropriate to the source, ie. either libavresample-ffmpeg-dev or libswresample-ffmpeg-dev.
So here, (cmus), the libav patching for, among other things, avresample is not working out but swresample is good & can be used instead.

(- as the re-emergence of ffmpeg shared proceeds some apps will be available for either libav or ffmpeg in separate versions. The near term would be a default of libav with ffmpeg version packages 
The shared libs of either can co-exist, for -dev's only one or the other at a time. By themselves the ffmpeg libs would only support ffmpeg but sources could be built off of specifically. small [ex]("https://launchpad.net/~mc3man/+archive/ubuntu/ffmpeg-test2").

---

### Post by andrew.46 on 2014-11-04
So how can this all help our slightly neglected OP? ( Looks like you and I have cmus humming along :).) Will you add something to your steadily growing PPAs? Might be popular as there seems to be some discontent online with aac + cmus in the Ubuntu world...

---

### Post by mc4man on 2014-11-04
> **andrew.46 said:**
> So how can this all help our slightly neglected OP? ( Looks like you and I have cmus humming along :).) Will you add something to your steadily growing PPAs? Might be popular as there seems to be some discontent online with aac + cmus in the Ubuntu world...
Not really sure yet.
It appears Libav has totally removed swresample so unless They fix a lost cause. 
As far as aac in cmus users (of libav),  they could just rebuild with libmp4v2-dev which would give pretty full aac coverage  ( or hope the maintainers do, there's a Debian bug asking for that..

As far as ffmpeg shared I just may add that though in that case it would only be part of a libav11 upgrade for trusty. Reason there would be I'd likely keep the possibly overblown current config (+ 1

This is the current as in sid, using the 2.4.2 release. I added blue as they are only using the native aac encoder in ffmpeg shared, the red is one reason for libav11 connection  - 
ffmpeg version 2.4.2-1 Copyright (c) 2000-2014 the FFmpeg developers
  built on Oct 10 2014 15:27:21 with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)
  configuration: --prefix=/usr --extra-version=1 --build-suffix=-ffmpeg --toolchain=hardened --extra-cflags= --extra-cxxflags= --libdir=/usr/lib/x86_64-linux-gnu --shlibdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --enable-gpl --enable-shared --disable-stripping --enable-avresample --enable-avisynth --enable-fontconfig --enable-frei0r --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libcaca --enable-libcdio --enable-libflite --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmodplug --enable-libmp3lame [COLOR="#FF0000"]--enable-libopencv[/COLOR] --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-librtmp --enable-libschroedinger --enable-libshine --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx264 --enable-openal --enable-opengl --enable-x11grab --enable-libxvid --enable-nonfree [COLOR="#0000CD"]--enable-libfdk-aac[/COLOR] --enable-libdc1394 --enable-libiec61883 --enable-libzvbi --enable-libzmq --enable-libbs2b
  libavutil      54.  7.100 / 54.  7.100
  libavcodec     56.  1.100 / 56.  1.100
  libavformat    56.  4.101 / 56.  4.101
  libavdevice    56.  0.100 / 56.  0.100
  libavfilter     5.  1.100 /  5.  1.100
  libavresample   2.  1.  0 /  2.  1.  0
  libswscale      3.  0.100 /  3.  0.100
  libswresample   1.  1.100 /  1.  1.100
  libpostproc    53.  0.100 / 53.  0.100

So the question currently here is - to what advantage?
A shared ffmpeg vs. a somewhat leaner static (edge here to later
-dev packages to use for self builds of using sources ( some value there maybe.
As far as pre-built ppa packages not sure I'd want to do competing packages, chose one or the other type deal
Ex. mpv (libav) or mpv-ffmpeg, vlc-whatever (libav) or vlc-whatever-ffmpeg, ect, ect.
(- I'd lean more toward ffmpeg versions as upgrades instead though that's possibly not fair to users so hesitant there

---

