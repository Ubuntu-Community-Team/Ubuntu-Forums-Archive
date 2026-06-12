---
title: "help with ffmpeg under Ubuntu feisty"
date: 2007-06-13
forum: Multimedia &amp; Video
---

### Post by jingdejun on 2007-06-13
I plan to use ffmpeg for converting videos. Since I am new to linux, I have a few question about using ffmpeg:

(1) After a fresh install of Ubuntu, is ffmpeg automatically binded or not? How to check this?

(2) Following the instruction on the ffmpeg project website, I used following command:
svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg
then, I found a 'ffmpeg' folder was downloaded to my computer. There is a install file there, but I don't know how to install it. Anyone use this kind of method to install ffmpeg? How to proceed?

(3) What's the best way to install ffmpeg under Ubuntu Feisty? I need ffmpeg mainly for converting some videos (in avi, mov, mpg..) to FLV video.

Thanks for any advise.

---

### Post by dannyboy79 on 2007-06-13
you should always use your package manager to install stuff. it's called synaptic, it can be found within system, admin, BUT if you want to convert to FLV I don't think the version of ffmpeg is in the repositories. Here's a guide for bleeding edge ffmpeg:

[http://po-ru.com/diary/bleeding-edge-ffmpeg-on-ubuntu-feisty](http://po-ru.com/diary/bleeding-edge-ffmpeg-on-ubuntu-feisty)

---

### Post by raptor2552 on 2007-06-13
dannyboy is right open the synaptec package manager and search for ffmpeg then click install AND to save you the trouble of trying to make sense of ffmpeg's command line options, search for and install winff in synaptec manager as well. Winff wraps a GUI around ffmpeg, very easy to use.

---

### Post by blueb73 on 2007-07-11
> **raptor2552 said:**
> dannyboy is right open the synaptec package manager and search for ffmpeg then click install AND to save you the trouble of trying to make sense of ffmpeg's command line options, search for and install winff in synaptec manager as well. Winff wraps a GUI around ffmpeg, very easy to use.

im not finding winff.  has it been removed?

---

### Post by dannyboy79 on 2007-07-11
sorry, after looking for winff, I don't find it either. If you want a great program for converting video's, check out avidemux, devede or kino. Good luck

---

### Post by raptor2552 on 2007-07-11
I don't know which repository it's in so you'll have to compare your  /etc/apt/sources.list file with mine:
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://archive.ubuntu.com/ubuntu/ feisty-updates main universe
deb http://giss.tv/~vale/ubuntu32 ./
deb-src http://giss.tv/~vale/ubuntu32 ./

## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb http://archive.ubuntu.com/ubuntu/ feisty-backports restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ feisty-proposed restricted main multiverse universe
deb http://www.virtualbox.org/debian feisty non-free

```

---

### Post by dannyboy79 on 2007-07-11
> **raptor2552 said:**
> I don't know which repository it's in so you'll have to compare your  /etc/apt/sources.list file with mine:
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://archive.ubuntu.com/ubuntu/ feisty-updates main universe
[B]deb http://giss.tv/~vale/ubuntu32 ./
deb-src http://giss.tv/~vale/ubuntu32 ./[/B]

## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb http://archive.ubuntu.com/ubuntu/ feisty-backports restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ feisty-proposed restricted main multiverse universe
deb http://www.virtualbox.org/debian feisty non-free

```

I am strongly strongly against using untrusted repositories but you can do as you like as it's your machine. There are always risks with using 3rd party repo's that can have untrusted packages in them, which can then give some1 access to your machine and turn it into whatever they want, bot etc etc. Anyway, I thought I would merely point it out.

---

