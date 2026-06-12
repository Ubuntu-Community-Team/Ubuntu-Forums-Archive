---
title: "Some help with svn mplayer?"
date: 2007-09-17
forum: Multimedia &amp; Video
---

### Post by andrew.46 on 2007-09-17
Hi,
 
 I have been working at installing the latest svn mplayer and I was keen to get a little experienced advice to say if I am heading in the right direction :-)

 I am happy with downloading the svn mplayer:

```
svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
```

 and equally happy with downloading the codecs:

```
wget http://www.mplayerhq.hu/MPlayer/releases/codecs/all-20061022.tar.bz2
```

 and then placing the codecs in /usr/local/lib/codecs/ But the thing that puzzles me a little is the immense number of -dev files required to give mplayer the most options, to make it more of a 'Swiss Army Knife' player. For Dapper I have loaded:

```
sudo apt-get install  liblame-dev libdvdread3-dev libdvdnav-dev libogg-dev libvorbis-dev \ 
libxv-dev libtheora-dev libpng12-dev libmpcdec-dev libcdparanoia0-dev libxinerama-dev \ 
x11proto-xinerama-dev libjpeg62-dev libgdk-pixbuf-dev libfreetype6-dev libexpat1-dev \
libfontconfig1-dev libcaca-dev libfaac-dev libmp4v2-dev libaa1-dev libavcodec-dev  \ 
libavifile-0.7-dev libsdl1.2-dev libesd0-dev libfaad2-dev libice-dev libmatroska-dev \ 
libmad0-dev libmp4v2-dev libmikmod2-dev libpostproc-dev libspeex-dev libxvidcore4-dev \ 
libxvidcore4 avifile-xvid-plugin avifile-divx-plugin ladspa-sdk libsvga1-dev libsvga1 \ 
libungif4-dev libungif4g libenca-dev libdfb++-0.9-22 libdfb++-dev libdirectfb-0.9-22 \ 
libdirectfb-dev libavformat-dev libfame-0.9 libfame-dev zlib1g-dev liblivemedia-dev \ 
libfribidi-dev libdvdnav4 libdvdplay0 libasound2-dev \
libdv4-dev libpopt-dev zlib1g-dev  xlibs-dev 
```

 This seems to get most things available to mplayer, at least on my system and then I compile:

```
./configure \
--enable-largefiles \
--codecsdir=/usr/local/lib/codecs/ 
```

 So my question is: are there any flaws in this setup? I have a suspiion that mplayer by its nature can soak up a lot of dependencies but I would like to hear from other viewpoints.

             Thanks,

                 Andrew

---

### Post by ddrichardson on 2007-09-18
There are no flaws, it's just one of the issues with compiling from source, sometimes a huge number of dependancies are required.

---

### Post by andrew.46 on 2007-09-20
Hi,

 Can I say that it is well worth the effort though. Instant playback of all windows media files, quicktime files and real audio files. Plus the ability to convert to and from a host of formats. Downside is the gui is a bit primitive so I have compiled without, which is actually the default in a show of no-confidence by the developers :-)

                             Andrew

---

