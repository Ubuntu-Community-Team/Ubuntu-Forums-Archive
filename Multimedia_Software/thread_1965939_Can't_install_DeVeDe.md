---
title: "Can't install DeVeDe"
date: 2012-04-26
forum: Multimedia Software
---

### Post by davesbrain on 2012-04-26
Please help. Can't seem to install DeVeDe via synaptic. Lucid 10.04.  Keep getting dependency error. Below is screen grab of actions it wants to perform:
[ATTACH]216616[/ATTACH] 

...and the resulting error:
```
devede:
 Depends: libavformat-extra-52 but it is not going to be installed
```

---

### Post by matt_symes on 2012-04-26
Hi

Let's see if we can get more info.

Open a terminal and type

```
sudo apt-get install devede
```

Enter your password. It will not be echoed to the screen.

Post the output back here by highlighting the text in the terminal->Right click->copy and pasting it into your next post between code tags like this

[noparse]```
output
```[/noparse]

to get output like this

```
output
```

Also let's take a look at your sources. Post the output of

```
cat /etc/apt/sources.list /etc/apt/sources.list.d/*
```

Kind regards

---

### Post by davesbrain on 2012-04-26
Hi, thanks for replying.  Here is info you requested:

```
davejr@davejr-desktop:~$ sudo apt-get install devede
[sudo] password for davejr: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  devede: Depends: libavformat-extra-52 but it is not going to be installed
E: Broken packages
davejr@davejr-desktop:~$ 

```

...and the sources info:
```
davejr@davejr-desktop:~$ cat /etc/apt/sources.list /etc/apt/sources.list.d/*
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse #Added by software-properties
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu/ lucid-security restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu/ lucid-security restricted main multiverse universe #Added by software-properties
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates restricted main multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates restricted main multiverse universe #Added by software-properties
deb http://us.archive.ubuntu.com/ubuntu/ lucid-proposed restricted main multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-proposed restricted main multiverse universe #Added by software-properties
deb http://packages.medibuntu.org/ lucid free non-free
deb-src http://packages.medibuntu.org/ lucid free non-free
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu lucid main
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu lucid main
deb http://ppa.launchpad.net/c-korn/vlc/ubuntu karmic main
deb http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu lucid main
deb http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu lucid main
deb http://ppa.launchpad.net/conky-companions/ppa/ubuntu lucid main
deb http://ppa.launchpad.net/conky-companions/ppa/ubuntu lucid main
deb http://ppa.launchpad.net/gloobus-dev/covergloobus/ubuntu lucid main
deb http://ppa.launchpad.net/gloobus-dev/covergloobus/ubuntu lucid main
deb http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu lucid main
deb http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu lucid main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main
deb http://ppa.launchpad.net/hrickards/lives/ubuntu lucid main
deb http://ppa.launchpad.net/hrickards/lives/ubuntu lucid main
# channel for the lucid (10.04) partner channel
# 
#:description:This channel contains the partner software for lucid
deb http://archive.canonical.com/ubuntu lucid partner
# channel for the lucid (10.04) partner channel
# 
#:description:This channel contains the partner software for lucid
deb http://archive.canonical.com/ubuntu lucid partner
deb http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu lucid main
deb http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu lucid main
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ lucid free non-free #Medibuntu - Ubuntu 10.04 "lucid lynx"
# deb-src http://packages.medibuntu.org/ lucid free non-free #Medibuntu (source) - Ubuntu 10.04 "lucid lynx"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ karmic free non-free #Medibuntu - Ubuntu 9.10 "karmic koala"
deb-src http://packages.medibuntu.org/ karmic free non-free #Medibuntu (source) - Ubuntu 9.10 "karmic koala"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ lucid free non-free #Medibuntu - Ubuntu 10.04 "lucid lynx"
# deb-src http://packages.medibuntu.org/ lucid free non-free #Medibuntu (source) - Ubuntu 10.04 "lucid lynx"
deb http://ppa.launchpad.net/n-muench/vlc2/ubuntu lucid main
deb http://ppa.launchpad.net/n-muench/vlc2/ubuntu lucid main
deb http://ppa.launchpad.net/nvidia-vdpau/cutting-edge-multimedia/ubuntu karmic main
deb http://ppa.launchpad.net/rvm/mplayer/ubuntu lucid main
deb http://ppa.launchpad.net/rvm/mplayer/ubuntu lucid main
# deb http://ppa.launchpad.net/screenlets-dev/ppa/ubuntu lucid main
# deb http://ppa.launchpad.net/screenlets-dev/ppa/ubuntu lucid main
deb http://ppa.launchpad.net/team-xbmc-svn/ppa/ubuntu lucid main
deb http://ppa.launchpad.net/team-xbmc-svn/ppa/ubuntu lucid main
deb http://ppa.launchpad.net/tiheum/equinox/ubuntu lucid main
deb http://ppa.launchpad.net/tiheum/equinox/ubuntu lucid main
deb http://ppa.launchpad.net/tldm217/tahutek.net/ubuntu lucid main
deb http://ppa.launchpad.net/tldm217/tahutek.net/ubuntu lucid main
davejr@davejr-desktop:~$ 

```

---

### Post by matt_symes on 2012-04-26
Hi

You have some karmic sources in your ppas. Remove them if you can.

Also can you post the output of

```
dpkg -l libavformat-extra-52
```

That's a small L after dpkg.

Kind regards

---

### Post by ajgreeny on 2012-04-26
I suspect that you may need to enable the [medibuntu]("http://www.medibuntu.org/") repositories in order to get the "extra" lib packages that are needed.

---

### Post by lisati on 2012-04-26
> **ajgreeny said:**
> I suspect that you may need to enable the [medibuntu]("http://www.medibuntu.org/") repositories in order to get the "extra" lib packages that are needed.

It might not be necessary to link to the medibuntu repos: there are some "extras" relating to DVDs that can be installed without doing so. The process is described here: [https://help.ubuntu.com/10.04/musicvideophotos/C/video-dvd.html](https://help.ubuntu.com/10.04/musicvideophotos/C/video-dvd.html)

---

### Post by davesbrain on 2012-04-26
OK, removed Karmic from sources list(not sure why that was there). Also removed one for Gnome3(think I'm still Gnome2).
Enabled (checkbox) medibuntu sources(I think there were 3 in the list).
And, here's the output requested:
```
davejr@davejr-desktop:~$ dpkg -l libavformat-extra-52
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  libavformat-ex <none>         (no description available)
davejr@davejr-desktop:~$ 

```

*EDIT- Just tried to install it again after making those changes to sources, getting same error.

---

### Post by matt_symes on 2012-04-27
Hi

Can you post the output of this command
```

apt-cache show libavformat-extra-52
```

Kind regards

---

### Post by davesbrain on 2012-04-30
sure,

```
davejr@davejr-desktop:~$ apt-cache show libavformat-extra-52
Package: libavformat-extra-52
Source: libav-extra
Priority: optional
Section: libs
Installed-Size: 1748
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: 4:0.6.2-1u1~ppa1
Replaces: libavformat52
Depends: libavcodec-extra-52 (>= 4:0.6.2), libavcodec-extra-52 (<< 4:0.6.2-99), libavutil-extra-50 (>= 4:0.6.2), libavutil-extra-50 (<< 4:0.6.2-99), libbz2-1.0, libc6 (>= 2.7), librtmp0 (>= 2.3), zlib1g (>= 1:1.1.4)
Conflicts: libavformat52
Breaks: libavcodec51, mplayer (<< 2:1.0~rc4~)
Filename: pool/main/liba/libav-extra/libavformat-extra-52_0.6.2-1u1~ppa1_i386.deb
Size: 835516
MD5sum: ac0583bc51c4d85a7eb3556ebdcb9d7e
SHA1: dff33576981982c50ac973c17722d90835f64b14
Description: Libav file format library
 This is the demuxer library from the Libav project. It supports most
 existing file formats (AVI, MPEG, OGG, Matroska, ASF...).
 .
 This package contains a unrestricted version of the libavformat shared
 object that should only be used by Debian packages.
Original-Maintainer: Debian multimedia packages maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>

Package: libavformat-extra-52
Source: ffmpeg-extra
Version: 4:0.5.1-1ubuntu1.3+medibuntu1
Architecture: i386
Maintainer: Medibuntu Packaging Team <medibuntu-maintainers@lists.launchpad.net>
Installed-Size: 1528
Depends: libavcodec-extra-52 (>= 4:0.5.1), libavcodec-extra-52 (<< 4:0.5.1-99), libavutil-extra-49 (>= 4:0.5.1), libavutil-extra-49 (<< 4:0.5.1-99), libbz2-1.0, libc6 (>= 2.7), zlib1g (>= 1:1.1.4)
Recommends: apport-hooks-medibuntu
Conflicts: libavformat-unstripped-52 (<< 4:0.5.1-1ubuntu1.3+medibuntu1), libavformat52
Breaks: libavcodec51
Replaces: libavformat-unstripped-52 (<< 4:0.5.1-1ubuntu1.3+medibuntu1), libavformat52
Homepage: http://ffmpeg.org/
Priority: optional
Section: non-free/libs
Filename: pool/non-free/f/ffmpeg-extra/libavformat-extra-52_0.5.1-1ubuntu1.3+medibuntu1_i386.deb
Size: 720672
SHA256: 1941538552495201aaa641a139d7c041407f8dd8f7331a962935f4b9d43ceade
SHA1: 63d023acf35f147ef1977f4fdee9d1785a93a08b
MD5sum: a881fba4144af23a1631d590bb56a8b3
Description: ffmpeg file format library
 This is the demuxer library from the ffmpeg project. It supports most
 existing file formats (AVI, MPEG, OGG, Matroska, ASF...).
 .
 This package contains a unrestricted version of the libavformat shared
 object that should only be used by Debian packages.
Original-Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>

Package: libavformat-extra-52
Priority: optional
Section: multiverse/libs
Installed-Size: 1528
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian multimedia packages maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>
Architecture: i386
Source: ffmpeg-extra
Version: 4:0.5.1-1ubuntu1.3
Replaces: libavformat-unstripped-52 (<< 4:0.5.1-1ubuntu1.3), libavformat52
Depends: libavcodec-extra-52 (>= 4:0.5.1), libavcodec-extra-52 (<< 4:0.5.1-99), libavutil-extra-49 (>= 4:0.5.1), libavutil-extra-49 (<< 4:0.5.1-99), libbz2-1.0, libc6 (>= 2.7), zlib1g (>= 1:1.1.4)
Conflicts: libavformat-unstripped-52 (<< 4:0.5.1-1ubuntu1.3), libavformat52
Breaks: libavcodec51
Filename: pool/multiverse/f/ffmpeg-extra/libavformat-extra-52_0.5.1-1ubuntu1.3_i386.deb
Size: 720604
MD5sum: ff5c1d10a2b5500fdf570d7b7ed23ca8
SHA1: 94812592fdbb7675a416dd3ddbf61fae268952e6
SHA256: fa7d7009405eeb825a8fe4eb22cc92f92c17aa1cd24e8166e07aa1eb9a547406
Description: ffmpeg file format library
 This is the demuxer library from the ffmpeg project. It supports most
 existing file formats (AVI, MPEG, OGG, Matroska, ASF...).
 .
 This package contains a unrestricted version of the libavformat shared
 object that should only be used by Debian packages.
Homepage: http://ffmpeg.org/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

Package: libavformat-extra-52
Priority: optional
Section: multiverse/libs
Installed-Size: 1524
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian multimedia packages maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>
Architecture: i386
Source: ffmpeg-extra
Version: 4:0.5.1-1ubuntu1
Replaces: libavformat-unstripped-52 (<< 4:0.5.1-1ubuntu1), libavformat52
Depends: libavcodec-extra-52 (>= 4:0.5.1), libavcodec-extra-52 (<< 4:0.5.1-99), libavutil-extra-49 (>= 4:0.5.1), libavutil-extra-49 (<< 4:0.5.1-99), libbz2-1.0, libc6 (>= 2.7), zlib1g (>= 1:1.1.4)
Conflicts: libavformat-unstripped-52 (<< 4:0.5.1-1ubuntu1), libavformat52
Breaks: libavcodec51
Filename: pool/multiverse/f/ffmpeg-extra/libavformat-extra-52_0.5.1-1ubuntu1_i386.deb
Size: 719452
MD5sum: 4390f7a1e3e2ffe5f0f21e95b37c0386
SHA1: f4b26de53e0345b96bd1c42ac64b0b85979400b1
SHA256: 0e7b77f12d6c78b50a842516b055441b018319c97781cde86caf2dba86d8a523
Description: ffmpeg file format library
 This is the demuxer library from the ffmpeg project. It supports most
 existing file formats (AVI, MPEG, OGG, Matroska, ASF...).
 .
 This package contains a unrestricted version of the libavformat shared
 object that should only be used by Debian packages.
Homepage: http://ffmpeg.org/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

davejr@davejr-desktop:~$ 

```

---

### Post by matt_symes on 2012-05-01
Hi

Well you have a number of references to libavformat-extra-52. The first one is a higher version and is dependent on different library versions than the rest. This may be your problem.

According to this site below, this version (4:0.5.1-1ubuntu1.3) comes with Lucid.

[http://packages.ubuntu.com/lucid/libavformat-extra-52](http://packages.ubuntu.com/lucid/libavformat-extra-52)
[FONT=monospace]
[/FONT][FONT=monospace]This version ([/FONT]4:0.6.2-1u1~ppa1) is being pulled in from a ppa. 

You also have a version from mediubuntu (4:0.5.1-1ubuntu1.3+medibuntu1).

And you have the original version ([FONT=monospace][/FONT]4:0.5.1-1ubuntu1.3) from the standard repos (multiverse).

I think this is the cause of your problems. Which ppa is pulling in this version (4:0.6.2-1u1~ppa1) ?

Kind regards

---

### Post by davesbrain on 2012-05-02
Pretty sure issues are with upadate manager and sticking 'partial upgrade'.  Somehow, ppa's(and other things) got scrambled perhaps? As shown in screengrab below:
[ATTACH]217128[/ATTACH]

---

### Post by mc4man on 2012-05-02
The ppa packages were orig from here though maybe no longer available
[https://launchpad.net/~n-muench/+archive/vlc2/+build/2307587](https://launchpad.net/~n-muench/+archive/vlc2/+build/2307587)
current state of ppa
[https://launchpad.net/~n-muench/+archive/vlc2/+packages](https://launchpad.net/~n-muench/+archive/vlc2/+packages)

---

