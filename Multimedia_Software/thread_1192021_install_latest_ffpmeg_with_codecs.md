---
title: "install latest ffpmeg with codecs"
date: 2009-06-19
forum: Multimedia Software
---

### Post by unclecameron on 2009-06-19
It took me awhile to figure out how to compile all the codec/libraries I needed for my conversion purposes, this is a down-and-dirty cut/paste howto on it, YMMV, but it's about the fastest way to get a working pretty current ffpmeg install with current source stuff.
```

  apt-get install yasm gcc elinks g++ build-essential subversion automake libtool
  mkdir /usr/src/ffmpeg
  cd /usr/src/ffmpeg
  wget http://downloads.xiph.org/releases/ogg/libogg-1.1.3.tar.gz
  tar xfvz libogg-1.1.3.tar.gz
  cd libogg-1.1.3
  ./configure
  make
  make install 
  cd ../
  svn co http://svn.xiph.org/trunk/theora
  cd theora
  ./autogen.sh
  make
  make install
  cd ..
  elinks ftp://ftp.videolan.org/pub/videolan/x264/snapshots/
  page to bottom and save latest download, they change all the time
  q
  tar xjvf x264-snapshotxxxxxxxxxxxxxx.bz2
  cd x264-snapshotxxxxxxxxxxxxxx
  make
  make install
  cd ..
  wget http://superb-west.dl.sourceforge.net/sourceforge/lame/lame-398-2.tar.gz
  tar xfvz lame-398-2.tar.gz
  cd lame-398-2
  ./configure
  make
  make install
  cd ..
  elinks http://www.audiocoding.com/downloads.html
  follow link FAAC Source Version 1.28 bootstrapped TAR.GZ package
  follow "click here to download Freeware Advanced Audio Coder manually"
  save download as what it says
  q
  tar xfvz faac-1.28.tar.gz
  cd faac-1.28
  ./configure
  make 
  make install
  wget http://downloads.xvid.org/downloads/xvidcore-1.2.1.tar.gz
  tar xfvz xvidcore-1.2.1.tar.gz
  cd xvidcore/build/generic
  ./configure
  make
  make install
  cd /usr/src/ffmpeg
  svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg
  cd ffmpeg
  ./configure --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-pthreads --enable-gpl --enable-libfaac --enable-nonfree
  make
  make install
  ldconfig
  ffmpeg
   (should give you similar output to this)
   FFmpeg version SVN-r19227, Copyright (c) 2000-2009 Fabrice Bellard, et al.
   configuration: --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-pthreads --enable-gpl --enable-libfaac --enable-nonfree
   libavutil     50. 3. 0 / 50. 3. 0
   libavcodec    52.32. 0 / 52.32. 0
   libavformat   52.34. 0 / 52.34. 0
   libavdevice   52. 2. 0 / 52. 2. 0
   libswscale     0. 7. 1 /  0. 7. 1
   built on Jun 19 2009 13:44:01, gcc: 4.3.2

```
to update it later
```

  make distclean
  svn update

```
hope it helps someone else, the documentation for doing this really stinks for a "quick" install of the latest stuff compiled from source, which changes VERY often so if you installed using apt-get you'd get very old stuff, plus if you can figure out all the steps and somehow miss one or get them in the wrong order things might not work. Confession, I did this on Debian, but it should work the same on Ubuntu, let me know if something doesn't work.

---

