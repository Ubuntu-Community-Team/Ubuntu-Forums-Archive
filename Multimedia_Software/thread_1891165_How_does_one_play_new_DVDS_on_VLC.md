---
title: "How does one play new DVDS on VLC?"
date: 2011-12-05
forum: Multimedia Software
---

### Post by getmeoutofhere on 2011-12-05
I'm using 10.04 and I cannot play legally bought DVDs on it - I have tried Rio and Cars 2 on VLC The Luggage and it won't work.  Rio will work on my Windows version of The Luggage - I haven't tried Cars 2 on it, but I assume it would work.

There was a thread on this earlier, which mentioned a patch:

[http://ubuntuforums.org/showthread.php?t=1845572](http://ubuntuforums.org/showthread.php?t=1845572)

However I haven't a clue how to add a patch to VLC.

Surely this is a major and obvious problem, that lots of people would be confronting?  Or, with the latest encryption technology, has Linux met its match?  I can't really say until I've applied the patch, which is a text file.

---

### Post by BicyclerBoy on 2011-12-05
The windows version of VLC includes libdvdcss.
The linux version dynamically opens libdvdcss if installed..

You need to install restricted extras/formats packages..
Read the DVD playback readme on Ubuntu website.
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

The latest DVDs have a couple more tricks up their sleeves..you need a player built with the latest libdvdnav.

The easiest way on 10.04 is to find a launchpad ppa with recent VLC build.
[https://launchpad.net/~n-muench/+archive/vlc2](https://launchpad.net/~n-muench/+archive/vlc2)

---

### Post by mc4man on 2011-12-05
You should upgrade your libdvdread4 & libdvdnav4 packages to 11.10 versions, can be done easily. This will prove helpful with some of the newer dvd structure protections.

I described here how to do that for 10.04
[http://askubuntu.com/questions/82923/vlc-could-not-read-the-file-error-when-trying-to-play-dvds/83036#83036](http://askubuntu.com/questions/82923/vlc-could-not-read-the-file-error-when-trying-to-play-dvds/83036#83036)

Even so some titles, like cars2, vlc may need some additional help in finding the correct title # for the main movie. In the case of cars2 in Region 1 the title # is 18

this is cars2 specific though you'll likely need to upgrade libdvdread/nav4 first.
[http://ubuntuforums.org/showthread.php?p=11481849#post11481849](http://ubuntuforums.org/showthread.php?p=11481849#post11481849)

Note  - that ppa's vlc, while much better than lucid's vlc version, will just use the libdvdread/nav you have installed, so again you want the newer versions

---

### Post by BicyclerBoy on 2011-12-05
Sorry did not realize that ppa was so package bound.

Is there no VLC ppa that is more self-contained ?
 i.e. statically linked for everything except libdvdcss.

Not asking for myself as I don't use VLC & have libdvdread4/nav4 compiled/installed.

---

### Post by mc4man on 2011-12-05
> **BicyclerBoy said:**
> Sorry did not realize that ppa was so package bound.

Is there no VLC ppa that is more self-contained ?
 i.e. statically linked for everything except libdvdcss.

Not asking for myself as I don't use VLC.

Generally speaking Ubuntu/Debian do not do static linking so unless a source provides it's own then the app will use shared libs. A classic there is mplayer, even then Ubuntu has flip-flopped on using the internel ffmpeg libs or the system shared. (ATM mplayer/mplayer2 use the system libs.

PPa's also follow this so they'd need to provide better libdvdread/nav packages though again they'd be the shared libs

Because there are no real dependency issues one can upgrade libdvdread4/nav4 very easily, the only thing to watch for is if requiring the -dev packages for building against, though easy to upgrade them also.

(I wouldn't doubt that libdvdread in handbrake is updated more often than the repo packages, for the moment though the 11.10 packages are pretty good.

---

### Post by BicyclerBoy on 2011-12-05
Thanks for clarifying.

Mr HandBrake does seem to post at least half the patches for libdvdnav etc..

---

### Post by poltr1 on 2011-12-06
Ubuntu out-of-the-box doesn't include codecs or decryption software in the standard distribution, for legal reasons (copyright, intellectual property laws, export controlled technology, etc.)  But there are packages available to enhance and enable Ubuntu to handle multimedia.

The first step is to install medibuntu, if you can legally do so in your country.  Here's how:
[http://www.unixmen.com/linux-distributions/4-ubuntu/1241-medibuntu-repository-is-available-for-ubuntu-1010-maverick-meerkat](http://www.unixmen.com/linux-distributions/4-ubuntu/1241-medibuntu-repository-is-available-for-ubuntu-1010-maverick-meerkat)

Then install the 4 packages mentioned on this page via sudo apt-get install: 
[https://help.ubuntu.com/10.10/musicvideophotos/C/video-dvd.html](https://help.ubuntu.com/10.10/musicvideophotos/C/video-dvd.html)

Then insert the disc, fire up VLC, select the disc, and it should play.

I just did these steps on a laptop running 11.10, and I can now watch DVDs.

---

