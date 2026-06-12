---
title: "own build of unstripped libraries"
date: 2009-11-02
forum: Multimedia Software
---

### Post by barna on 2009-11-02
Hi,

I installed the unstripped libraries for ffmpeg, but still libfaac is disabled, so I thought I recompile the whole thing, and enable everything. In order to keep package management consistent, I have modified ffmpeg-*/debian/confflags, added many --enable-* options, and rebuilt the package. However, the rebuilt packages are named for example libavcodec-52, and not libavcodec-unstripped-52, etc, and they were conflicting with the -unstripped versions, so I removed the unstripped versions - however, this then removed many other packages depending on the unstripped versions as well, for example dvd-slideshow, and others. 

How can I rebuild the ffmpeg+libraries packages such that they are called -unstripped, and therefore do not remove other useful packages depending on the -unstripped libraries? Or what is the right way to go?

Thanks

---

### Post by barna on 2009-11-02
Sorry. There is an ffmpeg-extra source package (but no binary, this is why I have not bounced into it, and wrote the previous post). One should get this source package (apt-get source ffmpeg-extra), and compile that one.

---

### Post by barna on 2009-11-02
There is still one thing I don't understand: when running debuild -us -uc in the ffmpeg-extra source directory, it said there are unmet dependencies, for example libavcodec-dev is needed. Why? The ffmpeg-extra source directory has its own version of libavcodec, which is going to be build right now... Why is it then needed? 
Thanks.

---

### Post by mc4man on 2009-11-02
> apt-get source ffmpeg-extra)

A few thoughts... I've been using my own ffmpeg package sets since hardy and would never use the ubuntu diffs, they're fine for the repo and possibly if building the repo source, but tend to be a mess lately

There is only one ffmpeg source in the ubuntu repo, but 2 different .diffs ( the ffmpeg one and the ffmpeg-extra

The ffmpeg-extra diff has depends on the -devs and won't build -dev packages, so if you want to rebuild using the repo sources and .diffs you'd need to build and install the ffmpeg source and packages including the -dev's, then build and install the extra source.

You may find it easier to just build the ffmpeg ( which will build 'unstripped') and hack the deb's of the few apps that have a depend of the 'extra versions'

By hack I mean dl the troulbesome .deb, and thru a small script edit the control file, then install.

Ex. of a modded devede I made for someone ( changed the dep on the extra and added a mplayer, mplayer-nogui option

> Package: devede
Version: 3.14.0-0ubuntu5-1
Architecture: all
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Installed-Size: 3560
Depends: python, python-support (>= 0.90.0), python-glade2, mencoder, dvdauthor, genisoimage, vcdimager, imagemagick, mplayer-nogui | mplayer, libavcodec52, libavformat52, libavutil49, libpostproc51, libswscale0

You may also find that if you don't make a small change to version in the changelog that after installing your new packages, some of the repo versions will be seen as an upgrade.

---

### Post by barna on 2009-11-02
In the meantime I have compiled and successfully installed the libs from the ffmpeg-extra source package. I think this is the easiest way to go, for me at least. I have now libfaac available, can encode for the iPod, etc, and dvd-slideshow and other packs depending on the extras are also happy. 

I also noticed that the repo packages are seen as upgrades, if I do not change the version number. That's no problem, I anyway want to lock the version of these packages so that later upgrades do not overwrite my own version. 

Thanks

---

