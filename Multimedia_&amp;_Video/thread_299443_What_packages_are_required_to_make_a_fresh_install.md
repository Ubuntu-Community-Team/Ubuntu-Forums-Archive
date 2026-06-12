---
title: "What packages are required to make a fresh install of Edgy play all codecs and flash?"
date: 2006-11-14
forum: Multimedia &amp; Video
---

### Post by aneeshm on 2006-11-14
I want to install Edgy for a friend who doesn't have an interent connection. I want to give him another CD with the packages, along with all their dependencies, which are needed to make a fresh install of Edgy play all non-free and win32 codecs, along with the non-free flash player and the Mozilla plug-in for the same, in case he ever chooses to get connected to the internet.

I have three questions:

1) Which packages should I download?
2) Where should I download them from?
3) In which order should they be installed?

---

### Post by 23meg on 2006-11-14
```
gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs flashplayer-mozilla
```Get them from [http://packages.ubuntu.com](http://packages.ubuntu.com) .

---

### Post by aneeshm on 2006-11-14
> **23meg said:**
> ```
gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs flashplayer-mozilla
```Get them from [http://packages.ubuntu.com](http://packages.ubuntu.com) .

Thanks for the list!

I have three things left to ask.

1) Does this include all the dependencies that will be encountered when installing on a fresh system?
2) Why are there no universe packages for gstreamer? Or am I being completely ignorant? Forgive me if I am, because I know next to nothing about this - I just installed them once and forgot about them. I can't check this myself, because my system is 64 bit, whereas my friend's system is 32 bit.
3) What about the win32 codecs? Are they included?

---

### Post by 23meg on 2006-11-14
> 1) Does this include all the dependencies that will be encountered when installing on a fresh system?I think it does, since it says [here]("https://help.ubuntu.com/community/RestrictedFormats#head-74857744ddf74499c6447a19c7e94a2fcb382e0c") "install the following packages".

> 2) Why are there no universe packages for gstreamer?[There are some]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gstreamer&searchon=names&subword=1&version=edgy&release=universe"). You can always do a search in [http://packages.ubuntu.com](http://packages.ubuntu.com) for a specific repository and release to learn what package in what release is in what repository.
> 3) What about the win32 codecs? Are they included?No. You can get the package with ```
wget http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb
```
and your friend can install it with a double click, or ```
sudo dpkg -i w32codecs_20061022-0.0_i386.deb
```

---

### Post by aneeshm on 2006-11-14
Thanks.

I checked out the repos, and it seems that I'll have to manually download the dependencies - the instructions assume that the package manager will handle them automatically, but in this case, we have a human being as a package manager - me!

I've already downloaded libdvdcss2 from the unofficial repository given in the script that comes with the distribution (/usr/share/doc/whatever). I'm also going to be downloading ogle.


EDIT: On second thought, to hell with ogle. It has too many dependencies for me to manually handle.

---

