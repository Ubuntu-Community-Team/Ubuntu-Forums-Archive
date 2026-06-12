---
title: "Decoding interlaced MTS (PAFF interlacing)"
date: 2008-10-01
forum: Multimedia Software
---

### Post by Geekkit on 2008-10-01
I came across some threads (in Ubuntu forums and other places) that suggested ffmpeg's PAFF interlacing support was recently added, however I am using Ubuntu 7.10 with ffmpeg built on Aug 10 2008 (with libavutil version: ld.49.3.0, libavcodec version: 1d.51.38.0, libavformat version: 1d.51.10.0) and I still get the following error message when attempting to decode MTS files from my Panasonic HDC SD100 camcorder:

[FONT="Courier New"][h264 @ 0xb7e8fa68]PAFF interlacing is not implemented[/FONT]

Anyone know if there's support or coming soon support for MTS PAFF interlacing with FFMPEG?

---

### Post by Geekkit on 2008-10-02
*bump*

So, no one using HD video with MTS file format with newer HD camcorders under Linux that are doing 1920 x 1080 interlaced?

---

### Post by Geekkit on 2008-10-02
Figured it out ...

Go to ffmpeg web site, download current snapshot here:

[http://ffmpeg.mplayerhq.hu/ffmpeg-checkout-snapshot.tar.bz2](http://ffmpeg.mplayerhq.hu/ffmpeg-checkout-snapshot.tar.bz2)

Compile by running configure, make, make install. Then follow the instructions from this page:

[http://www.bitboysblog.com/?tag=m2ts](http://www.bitboysblog.com/?tag=m2ts)

Which is:

> Step 1:  Extract the audio from the m2ts file to output.wav using mplayer

mplayer -vc null -vo null -ao pcm:fast:waveheader:file=output.wav xxx.m2ts

Step 2: Extract the video from the m2ts file to output.avi using ffmpeg

ffmpeg -i xxx.m2ts -vcodec mpeg2video -sameq -s 1920×1080  -r 23.976 -an -f avi -copyts -benchmark output.avi

Step 3: Create a final .avi file by merging the audio and video using mencoder

mencoder output.avi -o final.avi -ovc copy -oac copy -audiofile output.wav

And voila! You have your MTS file converted into AVI at which point you can change it to whatever you want at this point.

---

### Post by CrazyPheel on 2008-10-02
Omg thank you!

---

