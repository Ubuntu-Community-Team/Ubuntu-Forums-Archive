---
title: "Having problems watching avi videos"
date: 2008-03-12
forum: Multimedia &amp; Video
---

### Post by Masteroc on 2008-03-12
Before flaming, i have searched and i have followed the instructions on the wiki about installing restricted codecs, etc. My problem is that i am trying to access some .avi's off an older hard drive and neither totem nor vlc is playing them. The specific error i get with totem is "The playback of this movie requires a video/x-avi-unknown decoder plugin which is not installed." With vlc it just doesnt play. Any advice....again i have installled all the restricted codecs from the ubuntu wiki.

---

### Post by xc3RnbFO8P on 2008-03-12
Try Avidemux.
If you can play it, save it by using copy video and sound.

[http://www.getdeb.net/app/Avidemux]("http://www.getdeb.net/app/Avidemux")

---

### Post by Masteroc on 2008-03-12
didn't work.....will nothing linux play this??

---

### Post by xc3RnbFO8P on 2008-03-13
First copy the .avi to your home folder.

In terminal:

> ffmpeg -v 5 -i /home/your folder/??????.avi -f null -

Show the output.

---

### Post by xc3RnbFO8P on 2008-03-13
You could try [**divfix++**]("http://3v1n0.tuxfamily.org/apt-repository/pool/feisty/3v1n0/divfix++_0.26+3v1ubuntu0_i386.deb")

---

### Post by Masteroc on 2008-03-13
The output of the above command is:

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jun  3 2007 20:59:25, gcc: 4.1.3 20070528 (prerelease) (Ubuntu 4.1.2-9ubuntu2)
Input #0, avi, from '/home/masteroc/WoW.avi':
  Duration: 00:00:03.5, start: 0.000000, bitrate: 117729 kb/s
  Stream #0.0, 1001/30000: Video: fraps, yuv420p, 1024x768, 1001/30000, 29.97 fps(r)
Output #0, null, to 'pipe:':
  Stream #0.0, 1/90000: Video: rawvideo, yuv420p, 1024x768, 1001/30000, q=2-31, 200 kb/s, 29.97 fps(c)
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
frame=   22 q=0.0 size=       0kB time=0.7 bitrate=   0.0kbits/s dup=0 drop=0   frame=   44 q=0.0 size=       0kB time=1.5 bitrate=   0.0kbits/s dup=0 drop=0   frame=   68 q=0.0 size=       0kB time=2.3 bitrate=   0.0kbits/s dup=0 drop=0   frame=   91 q=0.0 size=       0kB time=3.0 bitrate=   0.0kbits/s dup=0 drop=0   frame=  107 q=0.0 Lsize=       0kB time=3.6 bitrate=   0.0kbits/s dup=0 drop=0    
video:0kB audio:0kB global headers:0kB muxing overhead nan%

---

### Post by xc3RnbFO8P on 2008-03-14
It looks like your file is damage,( you are missing some codec and update to) :

> FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Dec 20 2007 21:25:50, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)

Did you install medibuntu?

> sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

> wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

> sudo apt-get install w32codecs

In Synaptic Package Manager check if you got:

> libavifile,   avifile-mad-plugin,   libxine1,   libxine1-all-plugins,   libxine1-dev  (transcode  and  mencoder)

Then try to run it again.

---

### Post by Masteroc on 2008-03-14
still doesnt work :(( give me the same error

---

### Post by xc3RnbFO8P on 2008-03-14
Is your hard drive a windows partition.

---

### Post by Masteroc on 2008-03-14
yes, but i just copied the file directly to my ubuntu partition and tried to run it and it wouldnt work.

---

### Post by xc3RnbFO8P on 2008-03-14
It could be that your hard drive is damage, can you run a chkdsk on it ( using windows)?

---

