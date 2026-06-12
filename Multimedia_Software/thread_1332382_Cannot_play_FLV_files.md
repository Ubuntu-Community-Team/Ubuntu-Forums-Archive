---
title: "Cannot play FLV files"
date: 2009-11-20
forum: Multimedia Software
---

### Post by Mgiacchetti on 2009-11-20
This has NOTHING TO DO WITH YOUTUBE.

I am unable to play ANY flv file after a FRESH install of Ubuntu Karmic.

I get this when I run totem from cli, then try to open an FLV file...

```

michael@michael-pc:~$ totem

** Message: Error: GStreamer encountered a general supporting library error.
gstffmpegdemux.c(1243): gst_ffmpegdemux_open (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstDecodeBin2:decodebin20/ffdemux_swf:ffdemux_swf0:
Input/output error

```

I can play youtube videos in firefox, i can even play Hulu movies in firefox.   I cannot play youtube videos in totem.

However, YOUTUBE IS NOT THE PROBLEM.

```

michael@michael-pc:~$ sudo cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse
deb http://www.geekconnection.org/remastersys/repository karmic/

```

Please don't tell me to install w32codecs, cause I already have em.

---

### Post by andrew.46 on 2009-11-20
Hi Mgiacchetti,

Unless you are simply keen to get Totem running with these files perhaps you could try running RVMs MPlayer and SMPlayer on these files? If so you could add the following to your system's Software Sources:

```
ppa:rvm/mplayer
ppa:rvm/smplayer
```

and the corresponding keys:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 03E02400
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com E4A4F4F4
```

and then:

```
sudo apt-get mplayer smplayer
```

and this would get you software that should have no problems with you .flvs. Unfortunately I have no great knowledge of Totem and gstreamer so if you are actually quite keen to get Totem working others may have to assist :(.

Andrew

---

