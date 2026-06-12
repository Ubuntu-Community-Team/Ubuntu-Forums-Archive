---
title: "ffmpeg and audacity conflicting libavutil"
date: 2009-08-19
forum: Multimedia Software
---

### Post by herchu on 2009-08-19
This morning I discovered I had not ffmpeg installed, which I was needing. So I installed, but with the following packages installs/removals:

apt-get install ffmpeg:
```
The following extra packages will be installed:
  libamrwb3 libavcodec51 libavdevice52 libavformat52 libavutil49 libdc1394-22 libswscale0
The following packages will be REMOVED:
  libavcodec-unstripped-52 libavutil-unstripped-49 libpostproc-unstripped-51 libxine1-ffmpeg libxine1-plugins
The following NEW packages will be installed:
  ffmpeg libamrwb3 libavcodec51 libavdevice52 libavformat52 libavutil49 libdc1394-22 libswscale0
0 upgraded, 8 newly installed, 5 to remove and 19 not upgraded.
```

I installed it anyway. Now I wanted to install audacity, and I found this:

apt-get install audacity:
```
The following extra packages will be installed:
  audacity-data libavcodec52 libavutil-unstripped-49 libsoundtouch1c2
Suggested packages:
  ladspa-plugin
The following packages will be REMOVED:
  ffmpeg libavcodec51 libavdevice52 libavformat52 libavutil49 libswscale0
The following NEW packages will be installed:
  audacity audacity-data libavcodec52 libavutil-unstripped-49 libsoundtouch1c2
0 upgraded, 5 newly installed, 6 to remove and 20 not upgraded.
```

I guess that the 'unstripped' versions of libavutil (here used by audacity) conflict with the regular versiones (used by ffmpeg). I am sure there has to be something wrong in my setup... how I can find it out?

And by the way: What's this "unstripped" thing?

Thanks in advance -- Hernan.

---

### Post by mc4man on 2009-08-19
If you are running jaunty then you shouldn't be getting an ffmpeg that depends on libavcodec51 (the jaunty ver. uses libavcodec52, as does your audacity.

If on intrepid then what did you do to get libavcodec52, ect.

Ck or post your sources.list and what's in /etc/apt/sources.list.d if anything

```
cat /etc/apt/sources.list
```

---

### Post by herchu on 2009-08-19
Thanks mc4man, for your very prompt reply! You put me on the right path. Suspecting of ffmpeg, I found this line right away: ```
deb http://www.debian-multimedia.org stable main
```

I removed that source, installed audacity (losing the installed ffmpeg) reinstalled ffmpeg from Ubuntu repositories, and they are both installed now.


The problem now is that I had added that repository, if I remember correctly, looking for a ffmpeg version that supports AMR format/codecs. This is what I get now if I try to use it on the files I am working with (which come from a cellphone, I wish I could choose a different format...)
```
$ ffmpeg -i test.amr -acodec wmav1 -ar 22050 test.wma
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:18:41, gcc: 4.3.3
Input #0, amr, from 'test.amr':
  Duration: N/A, bitrate: N/A
    Stream #0.0: Audio: samr / 0x726D6173, 8000 Hz, mono, s16
Output #0, asf, to 'test.wma':
    Stream #0.0: Audio: wmav1, 22050 Hz, mono, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Unsupported codec (id=73728) for input stream #0.0
```

Do you know how to get support for this codec from Ubuntu repositories?

---

### Post by mc4man on 2009-08-19
While it may be possible to use debian-multimedia as a source in all likelihood at some point it will create an issue.( dm updates ffmpeg almost weekly, at some point you may not satisfy some new versions of the install depends
If you were going to try to intergrate you'd need to use the **sid** branch, not stable (and be prepared to add new versions of packages. If you needed to go to a debian repo for them then trouble would most likely occur.

(( far better to build your own ffmpeg and shared/static libraries as debian packages if there is a need to stay absolutely current

Anyway try adding the jaunty medibuntu repo and installing the amr libs from there (libamrnb3, libamrwb3 (search libamr in your package manager 

to install repo

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Also in your package manager search ffmpeg and install the  unstripped versions of the ffmpeg libraries (libavcode52-unstripped, ect.

I'm not familiar with the package manager in kubuntu, in synaptic this is easy

Or possibly, after adding medibuntu as a repo source and running a sudo apt-get update try this
```
sudo apt-get install non-free-codecs
```

((personally I'd prefer to add packages manually, the above will install quite a lot.

Can't 100% say this will resolve, I use a self built svn ffmpeg and it's libs (shared and static) as mentioned above in a hardy install

Edit:
taking a quick look at the jaunty ffmpeg source, and the unstripped .diff, while it will enable several codecs the amr don't seem to be included

If that's the case (most likely) read here to build your own ffmpeg (static) for encoding/decoding and the 2nd link explains the deal with unstripped

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

(( to make more confusing the above link (how to build ffmpeg) does not include enabling the amr libraries. To do so you'd need to add to the configure and install the proper amr libraries. If inclined say so and will advise (or someone else will

---

### Post by herchu on 2009-08-19
Thanks mc4man, your post was really helpful. I have moved to libavutil-unstripped-52 and evaluated ubuntu-restricted-extras (which would not add anything helpful other than libavutil*). I had a couple of funny issues with two libraries that I had to uninstall and install again, just to get the right source, but this might be related to my old debian repository.

I am going through the path of compiling ffmpeg. I read the posts you pointed to, and [this one]("http://ubuntuforums.org/showthread.php?t=491885") too.  To make things funny, ffmpeg [dropped support for AMR via libamr]("http://ubuntuforums.org/showpost.php?p=7584660&postcount=409"), and now they use libopenamr -- a good idea, I think... but bad for install things today! 

I was able to download and compile x264, and downloaded ffmpeg... but I can't compile it until I have installed openamr. And the sourceforge repo seems to be broken?
```
$ git clone --depth=1 git://opencore-amr.git.sourceforge.net/gitroot/opencore-amr
Initialized empty Git repository in /home/herchu/tmp/ffmpeg/opencore-amr/.git/
fatal: The remote end hung up unexpectedly
```
That does not give too much info... I have a sourceforge account so I can try the ssh (non-anonymous) access.
```
git clone --depth=1 ssh://MYUSER@opencore-amr.git.sourceforge.net/gitroot/opencore-amr
Initialized empty Git repository in /home/herchu/ffmpeg/opencore-amr/.git/
MYUSER@opencore-amr.git.sourceforge.net's password: XXX
fatal: '/gitroot/opencore-amr': unable to chdir or not a git archive
fatal: The remote end hung up unexpectedly
```
I can't find any info about this error... but I will keep trying tomorrow. I just wanted to post this in case someone else is poking at the same problem. If I can finally compile this I will post an update...

PS: After installing libavutil-unstripped-52 (I think) I have support for AMR in mplayer.... that's great, I can at least listen the sound files I had recorded in my phone. But I still want to get ffmpeg to work!

---

### Post by mc4man on 2009-08-19
In this case debian-mutimedia will be good to get either the 4 .debs or the orig. source which works just fine. (there are other ways also,

for the .debs
 here for i386, **direct download** the libs and install, then the -devs (139 - 142
[http://debian-multimedia.org/dists/unstable/main/binary-i386/](http://debian-multimedia.org/dists/unstable/main/binary-i386/)

or amd_64 (144 - 147
[http://debian-multimedia.org/dists/unstable/main/binary-amd64/](http://debian-multimedia.org/dists/unstable/main/binary-amd64/)

The source is here, but needs some work and probably best built off of the debian/rules (this source has had the debian folder removed, is meant to be patched with the diff just above it

[http://debian-multimedia.org/pool/main/o/opencore-amr/opencore-amr.php](http://debian-multimedia.org/pool/main/o/opencore-amr/opencore-amr.php)

[COLOR="Red"](([/COLOR] you'll be fine just using the 4 .debs from above links, they are no issue nor will cause an issue to install - I done both ways (building packages and using the prebuilt debs) to compare, no difference

I'll edit back in a link that has some additional info and something else you may be interested in,

edit:
of maybe some interest
[http://ubuntuforums.org/showthread.php?t=1081070](http://ubuntuforums.org/showthread.php?t=1081070)

page21 -22 have some info on the opencore libs, though I'm sure in this instance you'll be ok the the dm packages

---

### Post by herchu on 2009-08-19
It worked!

I downloaded the 4 debs from Debian Multimedia, then compiled and installed ffmpeg -- the time it took to compile is what I just delayed in replying. This notebook is still pretty hot after stressing cpu...

I can now finally transcode my AMR files:```
ffmpeg -i test.amr -acodec libmp3lame -ar 22050 test.mp3
...
    Stream #0.0: Audio: libopencore_amrnb, 8000 Hz, 1 channels, s16

```
Cool! Now I need to remember why I wanted this ;)

Thanks mc4man for all your help! I will post a summary of this for others to understand it; by tomorrow -- hoping I understand my notes by then.

PS: Does the ")" symbol work on your keyboard? you will eventually overflow your stack! ;)

---

### Post by herchu on 2009-08-21
For the record, I just blogged the procedure that I followed to get ffmpeg+amr working:

[http://daily-hacking.blogspot.com/2009/08/ffmpeg-with-amr-support-on-ubuntu.html](http://daily-hacking.blogspot.com/2009/08/ffmpeg-with-amr-support-on-ubuntu.html)

Thanks again mc4man!

---

