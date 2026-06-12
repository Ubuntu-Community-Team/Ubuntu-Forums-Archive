---
title: "libavformat"
date: 2010-08-24
forum: Multimedia Software
---

### Post by vkcaspervk on 2010-08-24
This lib has been causing me havoc lately, I tried reinstalling ffmpeg, mencoder, mplayer, libavformat, even tried the other extra version with no avail..

```
~$ ffserver
FFserver version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.83. 0
  libavformat   52.31. 0 / 52.74. 0
  libavdevice   52. 1. 0 / 52. 2. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:41:55, gcc: 4.4.3
ffserver: relocation error: ffserver: symbol resolve_host, version LIBAVFORMAT_52 not defined in file libavformat.so.52 with link time reference

``````
~$ mplayer
mplayer: relocation error: mplayer: symbol codec_wav_tags, version LIBAVFORMAT_52 not defined in file libavformat.so.52 with link time reference

``````
~$ mencoder
mencoder: relocation error: mencoder: symbol codec_wav_tags, version LIBAVFORMAT_52 not defined in file libavformat.so.52 with link time reference

```What am I missing? These are all from official repos. =\

 I think my brain is leaking out of my left ear...

---

### Post by mc4man on 2010-08-24
> These are all from official repos.
That may be true depending on what you mean there by 'official'

This doesn't quite add up - see diff. between red and blue - the red are not any 'official' ubuntu versions for lucid

> libavcodec   [COLOR="Blue"] 52.20. 1 [/COLOR]/ [COLOR="Red"]52.83. 0[/COLOR]
  libavformat   [COLOR="Blue"]52.31. 0[/COLOR] /[COLOR="Red"] 52.74. 0[/COLOR]
  libavdevice   [COLOR="Blue"]52. 1. 0[/COLOR] [COLOR="Red"]/ 52. 2. 0[/COLOR]

  libswscale    [COLOR="Blue"] 0. 7. 1 [/COLOR]/ [COLOR="Red"] 0.11. 0[/COLOR]

Did you build a ffmpeg or do /did you have any ppa's enabled?

The errors from mplayer and mencoder indicate that they depend on external ffmpeg libs and the current available ones are incompatible (not the one mplayer was built off of.

(if you build or get a ppa mplayer that uses it's own ffmpeg (internal) libs than that would resolve that - as far as ffmpeg  - remove ffmpeg and **all** ffmpeg libs   and re-install

---

### Post by vkcaspervk on 2010-08-24
The only repos I have added are
[http://ppa.launchpad.net/mangler/mangler/ubuntu](http://ppa.launchpad.net/mangler/mangler/ubuntu) lucid main
[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) lucid main
[http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lucid non-free

Everything else is out of the box. 

I have --purged removed, apt-get clean, then reinstalled, still have the same issues. 


For giggles heres my sources.list
```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
# deb http://archive.canonical.com/ lucid partner
deb http://download.virtualbox.org/virtualbox/debian lucid non-free
# deb http://deb.torproject.org/torproject.org lucid main


```

---

### Post by mc4man on 2010-08-25
I'm not sure if in lucid locate will work this way but maybe see 
```
locate libavcodec.so; locate libavformat.so
```

If nothing is returned, or anyway, what does this show? (don't care about all the libavahi-*  libs 

```
ls /usr/lib/libav*
```
and
```
ls /usr/local/lib
```
```
ls /etc/apt/sources.list.d
```
```
ls /usr/local/bin
```

Edit:
quickly booted to a lucid amd_64 live cd, added all the ubuntu sources, installed ffmpeg and mplayer and all is fine

> ubuntu@ubuntu:~$ ffmpeg
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:41:55, gcc: 4.4.3

(exact same for ffserver

> ubuntu@ubuntu:~$ mplayer
Creating config file: /home/ubuntu/.mplayer/config
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
Usage:   mplayer [options] [url|path/]filename


So you've done/added something, there's nothing wrong by default - you'll just need to figure out and or remember what that is....

---

### Post by vkcaspervk on 2010-08-25
```
~$ locate libavcodec.so; locate libavformat.so
/usr/lib/libavcodec.so
/usr/lib/libavcodec.so.52
/usr/lib/libavcodec.so.52.20.1
/usr/lib/libavcodec.so.52.83.0
/usr/lib/libavformat.so
/usr/lib/libavformat.so.52
/usr/lib/libavformat.so.52.31.0
/usr/lib/libavformat.so.52.74.0

``````
~$ ls /usr/local/lib
python2.6

``````
~$ ls /etc/apt/sources.list.d
mangler-mangler-lucid.list       ubuntu-wine-ppa-lucid.list
mangler-mangler-lucid.list.save  ubuntu-wine-ppa-lucid.list.save

``````
~$ ls /usr/local/bin

```Okay, I just removed ffmpeg, and all libs that go with it, including the libavformat... reran the locate, and I still get this with it uninstalled.
```
~$ locate libavcodec.so; locate libavformat.so
/usr/lib/libavcodec.so
/usr/lib/libavcodec.so.52
/usr/lib/libavcodec.so.52.20.1
/usr/lib/libavcodec.so.52.83.0
/usr/lib/libavformat.so
/usr/lib/libavformat.so.52
/usr/lib/libavformat.so.52.31.0
/usr/lib/libavformat.so.52.74.0

```: scratches head :

Okay from what im looking at I have a second copy...
```
/usr/lib$ ls -l libavformat*
lrwxrwxrwx 1 root root      22 2010-08-25 00:36 libavformat.so.52 -> libavformat.so.52.74.0
-rwxr-xr-x 1 root root 4973555 2010-07-17 02:57 libavformat.so.52.74.0

```
Simple as remove it?

---

### Post by mc4man on 2010-08-25
Si> mple as remove it? 
Basically yes - I think i'd remove all traces and re-install
I'd first d. check in synaptic that you've removed all the ffmpeg libs
libavcodecXX thru libswscaleX

Then go ahead and remove all the remaining ffmpeg lib files in /usr/lib
(also ck. /usr/bin, /usr/include, /usr/share for ffmpeg related files, folders

This would show what's left after  first d. ck'ing in synaptic and uninstalling if needed
)(note - each .so would have 2 links

```
locate libavcodec.so; locate libavformat.so; locate libavdevice.so; \
locate libavfilter.so; locate libavutil.so; locate libswscale.so; \
locate libpostproc.so
```

---

### Post by vkcaspervk on 2010-08-25
Okay I have removed all files related to ffmpeg from the filesystem. 

Tho when I rerun the locate this is what I get.

```
~$ locate libavcodec.so; locate libavformat.so; locate libavdevice.so; locate libavfilter.so; locate libavutil.so; locate libswscale.so; locate libpostproc.so
/usr/lib/libavcodec.so.52
/usr/lib/libavcodec.so.52.83.0
/usr/lib/libavformat.so.52
/usr/lib/libavformat.so.52.74.0
/usr/lib/libavdevice.so
/usr/lib/libavdevice.so.52
/usr/lib/libavdevice.so.52.2.0
/usr/lib/libavfilter.so
/usr/lib/libavfilter.so.1
/usr/lib/libavfilter.so.1.22.0
/usr/lib/libavutil.so.50
/usr/lib/libavutil.so.50.22.0
/usr/lib/libswscale.so
/usr/lib/libswscale.so.0
/usr/lib/libswscale.so.0.11.0

```Although its not on the filesystem...
```
~$ whereis libavcodec.so
libavcodec:
~$ whereis libavformat.so
libavformat:
```ls /usr/lib/libav*
comes up empty...

......

I figured Id try a reinstall and see what happens, Now it all seems to be working, with the right versions. 

```
~$ ffserver
FFserver version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:41:55, gcc: 4.4.3
Wed Aug 25 13:18:27 2010 FFserver started.
```

Locate comes up with:
```
~$ locate libavcodec.so; locate libavformat.so; locate libavdevice.so; locate libavfilter.so; locate libavutil.so; locate libswscale.so; locate libpostproc.so
/usr/lib/libavcodec.so.52
/usr/lib/libavcodec.so.52.83.0
/usr/lib/libavformat.so.52
/usr/lib/libavformat.so.52.74.0
/usr/lib/libavdevice.so
/usr/lib/libavdevice.so.52
/usr/lib/libavdevice.so.52.2.0
/usr/lib/libavfilter.so
/usr/lib/libavfilter.so.1
/usr/lib/libavfilter.so.1.22.0
/usr/lib/libavutil.so.50
/usr/lib/libavutil.so.50.22.0
/usr/lib/libswscale.so
/usr/lib/libswscale.so.0
/usr/lib/libswscale.so.0.11.0

```
Does that look right to you?

---

### Post by mc4man on 2010-08-25
> Does that look right to you? 

~$ ffserver
FFserver version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:41:55, gcc: 4.4.3
Wed Aug 25 13:18:27 2010 [COLOR="Blue"]FFserver started[/COLOR].
Yeah it looks fine and ffmpeg seems to be working now
(I guess I'd ignore what locate is saying - on my abandoned lucid install it's very inconsistent 

Did you try mplayer again? (though you can get a superior one by [building]("http://ubuntuforums.org/showthread.php?t=1542240") or thru a ppa - same for a [static - (standalone) ffmpeg]("http://ubuntuforums.org/showthread.php?t=786095")

What you could ck. - not sure if it matters or worth doing, is to open synaptic -> click on "status" and see if "Not Installed (residual)" shows any other ffmpeg and lib packages - if so remove them

---

### Post by FakeOutdoorsman on 2010-08-25
You may also have to **sudo updatedb** to update your locate database, otherwise it may show non-existent files.  I'm unsure how often the database gets updated in Ubuntu.

---

