---
title: "FFMPEG and VLC with H.264 and mp4a Support"
date: 2010-03-05
forum: Multimedia Software
---

### Post by ntunney on 2010-03-05
I've read some posts here about building VLC so that it will transcode H.264/AAC (mp4a).  I couldn't get any of them to work properly, so I've compiled the following instructions.  Not sure that all of the packages are needed, but I haven't had time to refine the process yet.  Hope this helps someone out there.

Install the following packages:
```
sudo apt-get install zlib1g-dev libfaad0 libfaad-dev libfaac0 libfaac-dev libmp3lame0 libmp3lame-dev libxvidcore4 libxvidcore4-dev libpopt-dev libbz2-dev libncurses5-dev libpcap0.8-dev cmake libreadline-dev subversion vim g++ yasm libssl-dev libjpeg-dev libtheora-dev build-essential git-core autoconf libtool libhal-dev libmad0-dev libpostproc-dev libgcrypt11-dev gettext liba52-0.7.4-dev libdvbpsi5-dev
```

Build GPAC from source:

```
cd
wget http://downloads.sourceforge.net/project/gpac/GPAC/GPAC%200.4.5/gpac-0.4.5.tar.gz?use_mirror=iweb
tar xzf gpac-0.4.5.tar.gz 
cd gpac/
sudo chmod +x configure
./configure --use-ffmpeg=no
make lib
sudo make install-lib

```

Build x264 from source:

```
cd
git clone git://git.videolan.org/x264.git --depth 1
cd x264/
./configure --enable-mp4-output --enable-shared
make
sudo make install
```

Build ffmpeg from source:

```
git clone git://git.ffmpeg.org/ffmpeg/ --depth 1
cd ffmpeg
git clone git://git.ffmpeg.org/libswscale/ --depth 1
./configure --enable-shared --enable-gpl --enable-nonfree --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid  --enable-pthreads --enable-encoder=mpeg4 --enable-encoder=aac --enable-encoder=ac3
make
sudo make install
```

If you want to test ffmpeg, you must run ldconfig at this time:

```
sudo ldconfig
```

Build Lua from source:

```
wget http://www.lua.org/ftp/lua-5.1.4.tar.gz
tar xzf lua-5.1.4.tar.gz
cd lua-5.1.4
#make local
vi src/Makefile and change gcc -O2 -Wall.. to  gcc -O2 -fpic -Wall...
make linux
sudo make install
```

Build VLC from source:

```
cd
git clone git://git.videolan.org/vlc.git --depth 1
cd vlc
./bootstrap
./configure --enable-faad --enable-merge-ffmpeg --disable-xcb --disable-qt4 --disable-skins2 --enable-libdvdpsi
make
sudo make install
sudo ldconfig
```

I'm using this to transcode a GigE UDP multicast stream (mpeg-2) to H.264 for live internet streaming.

---

