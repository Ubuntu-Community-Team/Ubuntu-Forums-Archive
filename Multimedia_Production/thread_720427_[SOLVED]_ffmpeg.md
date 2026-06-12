---
title: "[SOLVED] ffmpeg"
date: 2008-03-10
forum: Multimedia Production
---

### Post by AlmoG on 2008-03-10
I have just installed FFmpeg on my ubuntu gutsy, and when i try to convert avi to 3gp (so that i will be able to play the video on my mobile phone) it gives me this error:

"Unsupported codec for output stream #0.1"

The command i use is this:
```
 ffmpeg -i movie.avi -s 176x144 -r 10 \
  -ac 1 -b 48 -ab 12 movie.3gp 
```

the complete output is:
```
 $ ffmpeg -i movie.avi -s 176x144 -r 10 \
> -ac 1 -b 48 -ab 12 movie.3gp
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-libogg --enable-dc1394 --enable-libgsm --disable-debug --enable-xvid --enable-pthreads --enable-x264
  libavutil version: 49.3.0
  libavcodec version: 51.38.0
  libavformat version: 51.10.0
  built on Mar 10 2008 16:43:27, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)

Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65534/2733) -> 23.98 (23976024/1000000)
Input #0, avi, from 'movie.avi':
  Duration: 00:21:12.8, start: 0.000000, bitrate: 1153 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 512x384, 23.98 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 128 kb/s
File 'movie.3gp' already exists. Overwrite ? [y/N] y
Output #0, 3gp, to 'movie.3gp':
  Stream #0.0: Video: h263, yuv420p, 176x144, q=2-31, 0 kb/s, 10.00 fps(c)
  Stream #0.1: Audio: 0x0000, 48000 Hz, mono, 0 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec for output stream #0.1 
```

Can anybody help on this one?

---

### Post by marufaberlin on 2008-03-10
have you installed the codecs? could you use a different format than 3gp?

---

### Post by AlmoG on 2008-03-10
What codecs should i install?
And as far as i know 3gp is the only format my phone can play... I have Nokia 6085

---

### Post by marufaberlin on 2008-03-10
try installing gstreamer-*

---

### Post by WinterWeaver on 2008-03-10
the ffmpeg included in ubuntu does not have all the codecs. I've done some research on this topic, and apparently because of all the patent laws on codecs etc, there are 2 versions of ffmpeg. One without proprietary codec's (like 3gp), which is also the one included in Ubuntu, and then there is a version which contain proprietary codecs.

You will have to download the full version of ffmpeg (might have to build it from source yourself).

Here is some usefull links:
ffmpeg homepage: [http://ffmpeg.mplayerhq.hu/](http://ffmpeg.mplayerhq.hu/)
wikipedia page (for more info): [http://en.wikipedia.org/wiki/Ffmpeg](http://en.wikipedia.org/wiki/Ffmpeg)

Hope this helps.

WW

---

### Post by AlmoG on 2008-03-10
nope, that didn't do it...

WinterWeaver: about the other version... i will try that... but im not sure i can do it cuz im kind of new to this
if anybody have a solution for the ubuntu version please help

---

### Post by marufaberlin on 2008-03-10
what didn't do it, the gstreamer codecs or the new version of ffmpeg?

---

### Post by AlmoG on 2008-03-10
The gstreamer codecs didn't help...
As to the new version im not quite sure what i am supposed to do with it... I'm kind of clueless when it comes to source codes

---

### Post by marufaberlin on 2008-03-10
You download the .tar.gz file, and extract it in a new folder (don't forget that, the archivecould be a tarbomb). Then you open a terminal and cd into the folder where the sources are. Then you do this:

```

./configure
make
sudo make install

```

that does the installation for you.

---

### Post by AlmoG on 2008-03-10
The download page doesn't do me much help.. What file is it that i need to download?

---

### Post by marufaberlin on 2008-03-10
well, I see they have a SVN repo. run this:
```
svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg
```

alternatively go here: [http://svn.mplayerhq.hu/ffmpeg/trunk/](http://svn.mplayerhq.hu/ffmpeg/trunk/)

---

### Post by Creative2 on 2008-03-10
omg get ffmpeg from medibuntu repo....
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by srmantis on 2008-03-10
option 1:
download the program mobile media converter from:
[http://www.miksoft.net/products/mmc-lin.tar.gz](http://www.miksoft.net/products/mmc-lin.tar.gz)
this program use the ffmpeg and it includes the support 3gp

option 2:
it causes problems with the program avidemux (incompatibility the library)
you add to the repository:
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) stable main
and to install the key public from synaptic:
debian-multimedia-keyring

now update the system and to install the ffmpeg:
sudo apt-get install ffmpeg
this "new" ffmpeg includes the codec for 3gp

---

### Post by eye208 on 2008-03-10
Umm ... why not use MEncoder? :-k

---

### Post by srmantis on 2008-03-10
> **eye208 said:**
> Umm ... why not use MEncoder? :-k

Mencoder don't support the audio from file 3gp (only video) and ffmpeg support audio and video

---

### Post by eye208 on 2008-03-10
> **srmantis said:**
> Mencoder don't support the audio from file 3gp (only video) and ffmpeg support audio and video
Audio in 3GP files is either AAC or AMR. MEncoder supports both. See [here](http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#menc-feat-enc-libavcodec-audio-codecs).

Edit: It seems in this case Ubuntu's crippled libavcodec affects MEncoder as well as FFMPEG.

---

### Post by AlmoG on 2008-03-10
Srmantis thanks alot for your help! it works perfectly!
Thanks alot for everyone else who tried to help...
And thanks alot to marufaberlin for the quick replies.

Cheers!

---

### Post by marufaberlin on 2008-03-10
Hey, don't forget to mark the thread as solved!

---

### Post by andrew.46 on 2008-03-10
Hi,

Looks like while I was assembling all the following the problem was solved :-) Anyway to install ffmpeg from source with amr support I did the following, first some essential tools:

```
 
$ sudo apt-get install build-essential subversion 

```

Next install amr narrow band:

```
 
$ cd Desktop
$ wget http://ftp.penguin.cz/pub/users/utx/amr/amrnb-7.0.0.0.tar.bz2
$ tar xjvf amrnb-7.0.0.0.tar.bz2
$ cd amrnb-7.0.0.0
$ wget http://www.3gpp.org/ftp/Specs/archive/26_series/26.104/26104-700.zip
$ ./configure  --enable-shared --disable-static
$ make
$ sudo make install

```

Then amr wide band:

```

$ cd Desktop
$ wget http://ftp.penguin.cz/pub/users/utx/amr/amrwb-7.0.0.2.tar.bz2
$ tar xjvf amrwb-7.0.0.2.tar.bz2
$ cd amrwb-7.0.0.2
$ wget http://www.3gpp.org/ftp/Specs/archive/26_series/26.204/26204-700.zip
$ ./configure  --enable-shared --disable-static
$ make
$ sudo make install 

```

And then dev files for ffmpeg:

```

$ sudo apt-get install libogg-dev \
libtheora-dev libvorbis-dev liblame-dev libfaac-dev libfaad-dev \
libxvidcore4-dev liba52-0.7.4-dev libx264-dev checkinstall info2man 

```

And finally download the svn ffmpeg and install:

```

$ cd Desktop
$ svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg
$ cd ffmpeg
$ ./configure \
  --prefix=/usr \
  --mandir=/usr/man \
  --disable-debug \
  --enable-shared \
  --disable-static \
  --enable-pthreads \
  --enable-libtheora \
  --enable-libvorbis \
  --enable-gpl \
  --enable-pp \
  --enable-swscaler \
  --enable-x11grab \
  --enable-libmp3lame \
  --enable-libfaac \
  --enable-libfaad \
  --enable-libxvid \
  --enable-liba52 \
  --enable-libx264 \
  --enable-libamr-nb \
   --enable-libamr-wb \
   --enable-nonfree 
$ make
$ sudo checkinstall -D

```

This certainly worked for me on Hardy Heron, perhaps dev files might be a little different for Gutsy or Feisty?

              Andrew

---

