---
title: "ffmpeg and libavfilter"
date: 2010-10-04
forum: Multimedia Software
---

### Post by Mia1990 on 2010-10-04
Hi,

I'm installing ffmpeg with libavfilter using this [guide]("http://ubuntuforums.org/showthread.php?t=1438052") but i can not get the movie filter to compile when passing --enable-avfilter-lavf to ffmpeg i'm using libavfilter r5935 and the test copy of ffmpeg any help please

---

### Post by SeijiSensei on 2010-10-04
What are you trying to do with ffmpeg?  Maybe mplayer or mencoder would work for you instead.  They include the ffmepg code for libraries like libavfilter, libavcodec, libdvdread, etc.  Building mplayer/mencoder from source is pretty simple in Ubuntu.

1) Download a daily build: [http://www.mplayerhq.hu/MPlayer/releases/mplayer-export-snapshot.tar.bz2](http://www.mplayerhq.hu/MPlayer/releases/mplayer-export-snapshot.tar.bz2)

2) sudo apt-get install build-essential

3) sudo apt-get build-dep mplayer

4) Unpack the archive, go into the directory it created, then type 
./configure
make
sudo make install

It will put the binaries in /usr/local/bin.  I just did this the other day on a new Maverick installation.

If you need x264 installed, follow the instructions [here](http://www.mplayerhq.hu/DOCS/HTML/en/codec-installation.html#x264) to compile it first, then add --enable-x264 to the ./configure line for mplayer.

---

### Post by mc4man on 2010-10-04
Don't use the ./configure in linked page, adjust to something like 
```
./configure --enable-gpl --enable-version3 --enable-nonfree \
--enable-postproc --enable-libfaac --enable-libmp3lame \
--enable-libopencore-amrnb --enable-libopencore-amrwb \
--enable-libtheora --enable-libvorbis --enable-libx264 \
--enable-libxvid --enable-x11grab [COLOR="Blue"]--enable-libvpx[/COLOR]
```

--enable-avfilter-lavf  is no longer a valid config option, nor is --enable-faad
note - your libmp3lame version must be 3.98.3 or higher
use blue for vp8 support - supply libvpx-dev

Diff between same config on reg. svn checkout and doing as link shows (checkout.sh

Reg. (filters
```
Enabled filters:
anull			drawbox			pad
anullsink		fifo			pixdesctest
anullsrc		format			pixelaspect
aspect			hflip			scale
blackframe		noformat		slicify
buffer			null			unsharp
color			nullsink		vflip
crop			nullsrc			yadif

```

using avfilter & checkout.sh

```
Enabled filters:
anull			format			pixdesctest
anullsink		fps			pixelaspect
anullsrc		hflip			rotate
aspect			movie			scale
blackframe		negate			setpts
buffer			noformat		slicify
color			null			split
crop			nullsink		transpose
drawbox			nullsrc			unsharp
fade			overlay			vflip
fifo			pad			yadif
```

---

### Post by Mia1990 on 2010-10-04
thank you

i knew --enable-faad was took out of FFmpeg but i didn't know they took --enable-avfilter-lavf out.Thank you so much your a life saver.

---

