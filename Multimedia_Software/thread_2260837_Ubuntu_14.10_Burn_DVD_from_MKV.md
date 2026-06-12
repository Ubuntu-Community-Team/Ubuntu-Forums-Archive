---
title: "Ubuntu 14.10 Burn DVD from MKV"
date: 2015-01-14
forum: Multimedia Software
---

### Post by Chad_Marshall on 2015-01-14
I've run into a spot of bother w/ burning MKV files to DVD.

First, I attempted to install DeVeDe and found a number of dependencies were missing. I then attempted to follow a guide I found online that was dated, so I won't go into that here.

My basic question is this: Is there a guide, or recommended approach to ensure that all the right code (ffmpeg, avi, etc) are installed without running into "dependency hell"? What is the recommended approach here?

---

### Post by speartip on 2015-01-16
Devede is in the software centre. All the dependencies should install automatically.
Just make sure that ubuntu-restricted-extras is installed as well and you should be good to go.

---

### Post by vinnywright on 2015-01-16
> **speartip said:**
> Devede is in the software centre. All the dependencies should install automatically.
Just make sure that ubuntu-restricted-extras is installed as well and you should be good to go.+1 on that .........

 

```
vinny@vinny-Bonobo-Extreme:~$ apt show devede
Package: devede
Priority: optional
[COLOR=#ff0000]Section: multiverse/utils[/COLOR]
Installed-Size: 3,987 kB
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Multimedia Maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>
Version: 3.23.0~ds1-5ubuntu1
Depends: dvdauthor, genisoimage, imagemagick, libav-tools, libavcodec-extra-54, libvorbis0a, libvorbisfile3, mplayer2 | mpv, python-cairo, python-dbus, python-gobject, python-gtk2 (>= 2.16.0), ttf-freefont, vcdimager, python:any (>= 2.7.1-0ubuntu2)
Recommends: libmp3lame0
Suggests: mencoder
Download-Size: 1,893 kB
Homepage: http://www.rastersoft.com/programas/devede.html
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
APT-Manual-Installed: yes
APT-Sources: http://us.archive.ubuntu.com/ubuntu/ trusty/multiverse amd64 Packages
Description: simple application to create Video DVDs
 DeVeDe is a program to create video DVDs, suitables for home players, from
 any number of video files, in any of the formats supported by Mplayer.
 .
 It allows user to create subtitles and even menus.

```

VINNY

---

