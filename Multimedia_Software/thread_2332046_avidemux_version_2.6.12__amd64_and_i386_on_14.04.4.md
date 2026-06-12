---
title: "avidemux version 2.6.12  amd64 and i386 on 14.04.4 LTS"
date: 2016-07-27
forum: Multimedia Software
---

### Post by rmstock2 on 2016-07-27
On Ubuntu avidemux can be installed but you are stuck with an older 
version : 2.5.4 which has limited capabilities. I created a set of 
debian packages for both i386 and amd64 for version 2.6.12. Before 
installing avidemux one first needs to install ffmpeg , see e.g.

ffmpeg version 2.5.8 on ubuntu 14.04
[https://ubuntuforums.org/showthread.php?t=2296134](https://ubuntuforums.org/showthread.php?t=2296134)

Download is at [http://crashrecovery.org/avidemux/DEB/ubuntu1404/](http://crashrecovery.org/avidemux/DEB/ubuntu1404/)
or at [ftp://ftp.crashrecovery.org/pub/linux/avidemux/DEB/ubuntu1404/](ftp://ftp.crashrecovery.org/pub/linux/avidemux/DEB/ubuntu1404/)

For installation see : [http://crashrecovery.org/avidemux/DEB/ubuntu1404/installation-log.html](http://crashrecovery.org/avidemux/DEB/ubuntu1404/installation-log.html)

For Building and Installing see : [http://crashrecovery.org/avidemux/DEB/ubuntu1404/README.html]("http://www2.crashrecovery.org/avidemux/DEB/ubuntu1404/README.html")

DTS audio encoding by selecting the audio stream in COPY modus finally 
works with 2.6.12. Encoding DTS audio from an AAC, mp3 or PCM audio  
source(s) should still be regarded as experimental :

[IMG]http://s32.postimg.org/krqu146g5/avidemux_2_6_12_s.png[/IMG]

Here's screenshot with a typical avidemux job of creating a small clip :

[IMG]http://s32.postimg.org/efbora3dx/avidemux_2_6_12_2s.png[/IMG]

---

### Post by rmstock2 on 2016-07-28
avidemux 2.6.12 together with the bare bones dts encoder dcenc
can create DTS audio from other input audio formats.
It can however not invent new audio channels. If your input
is stereo, you DTS audio will be stereo as well :


[IMG]http://s32.postimg.org/6rqpvi1id/dts1.png[/IMG]

[IMG]http://s32.postimg.org/bnyy0xr1h/dts2.png[/IMG]

[IMG]http://s31.postimg.org/ao7xtkjiz/dts3.png[/IMG]

---

### Post by yoshii on 2016-07-29
Thanks so much, and by the way, how does one create .DEB packages?
This interests me...?

---

### Post by rmstock2 on 2016-07-29
General instructions for building a .deb package are here
[http://www.avidemux.org/admWiki/doku.php?id=build:install_2.6](http://www.avidemux.org/admWiki/doku.php?id=build:install_2.6) .

The maintainer of avidemux has however embedded the creation of debian
binary packages inside the tar source itself : avidemux_2.6.12.tar.gz through
a mechanism called  bootStrap.bash  :

```
bash bootStrap.bash --deb --enable-qt5 --with-cli  > bootstraplog-amd64.txt 2>&1[SIZE=2][/SIZE]
```

After running the bootStrap.bash command successfully a subdirectory
debs is created with the binary .deb files inside. This implicates that
the creation of a debian source package with
**avidemux_2.6.12.orig.tar.gz** , **avidemux_2.6.12-0ubuntu14.dsc** and
**avidemux_2.6.12-0ubuntu14.debian.tar.gz**, to be submitted to ubuntu
upstream is not a straightforward task. Most certainly as
bootStrap.bash in particular thoroughly examines the installed version
of ffmpeg, by doing some tests and subsequently creates patches which
then are applied dynamicly to the avidemux_2.6.12 source tree. As an
illustration of this examine

[http://crashrecovery.org/avidemux/DEB/ubuntu1404/amd64/bootstraplog-amd64.txt](http://crashrecovery.org/avidemux/DEB/ubuntu1404/amd64/bootstraplog-amd64.txt)

---

