---
title: "RecordMyDesktop"
date: 2009-03-06
forum: Multimedia Software
---

### Post by janie70 on 2009-03-06
someone please help.......
i cannot figure out how to get my recordmydesktop screencasts into kino.  how do i change from .ogg to mpeg?

I did what it says at this page...

[http://www.ghacks.net/2009/02/23/creating-screencasts-in-linux-with-gtk-recordmydesktop/](http://www.ghacks.net/2009/02/23/creating-screencasts-in-linux-with-gtk-recordmydesktop/)

and i get this message:

janie@janie-desktop:~$ ffmpeg -i input_ftp.ogg ouput_ftp.mpg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
input_ftp.ogg: I/O error occured
Usually that means that input file is truncated and/or corrupted.
janie@janie-desktop:~$


after trying for the entire day to get this working, i finally got it.
i went and got mencoder from the synaptic and used this terminal line

mencoder filename.ogg -oac lavc -ovc lavc -lavcopts abitrate=160 -o filename.avi

and it worked.

---

### Post by janie70 on 2009-03-06
ok.  now in kino, the end of the video is chopped off?  what....????????

---

### Post by janie70 on 2009-03-10
would anyone know why kino is cutting off the last bit of my videos?

---

### Post by janie70 on 2009-03-15
i ended up getting devede from synaptic pkg mgr to encode my videos and that worked best.  my videos are not being cut off now.  But--

once my video is edited, how do i save it for youtube?

i cannot find info on this that is helping.

---

### Post by inobe on 2009-03-15
convert it to flv

use mmc

scroll and notice the link for the deb [http://ubuntuforums.org/showthread.php?t=1092106](http://ubuntuforums.org/showthread.php?t=1092106)

consider using command line as well, just change from mp4 to flv at end of line ;)

---

### Post by janie70 on 2009-03-18
janie@janie-desktop:~$ ffmpeg -i completedwelcomejoomlavideoblog002.avi -vcodec libx264 -s 480x320 -r 24  -b 100k -acodec libfaac -ac 2 -ar 32000 -ab 128k -qscale 1 completed.flv
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 16 2009 21:16:26, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
Input #0, avi, from 'completedwelcomejoomlavideoblog002.avi':
  Duration: 00:00:15.0, start: 0.000000, bitrate: 30336 kb/s
  Stream #0.0: Video: dvvideo, yuv420p, 720x576, 28800 kb/s, 25.00 fps(r)
  Stream #0.1: Audio: pcm_s16le, 48000 Hz, stereo, 1536 kb/s
Unknown codec 'libx264'
janie@janie-desktop:~$ 


It did not work.
I thought youtube videos had to be MP4--i really just know nothing--all guesswork.

---

### Post by janie70 on 2009-03-18
what is mmc

---

### Post by janie70 on 2009-03-19
janie@janie-desktop:~$ ffmpeg -i final002.avi -vcodec h264 -s 480x320 -r 24  -b 100k -acodec libfaac -ac 2 -ar 32000 -ab 128k -qscale 1 final002.flv
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 16 2009 21:16:26, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
Input #0, avi, from 'final002.avi':
  Duration: 00:08:05.4, start: 0.000000, bitrate: 30336 kb/s
  Stream #0.0: Video: dvvideo, yuv420p, 720x576, 28800 kb/s, 25.00 fps(r)
  Stream #0.1: Audio: pcm_s16le, 48000 Hz, stereo, 1536 kb/s
Unknown codec 'libfaac'
janie@janie-desktop:~$ 


i changed lib264 to h264 and got this error.
what am i missing?

---

