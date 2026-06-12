---
title: "ffmpeg Audio Codec Error"
date: 2007-11-04
forum: Multimedia Production
---

### Post by coolboarderguy on 2007-11-04
Hi All,

mm trying to create an .mp4 file from an .avi so I can listen on my realplayer on my Nokia N95 here in Australia. Below is what I get with ffmpeg,


sudo ffmpeg -i /mnt/sharefat/japanese/yua/yua01.avi -vcodec mpeg4 -s 320x240 -b 300k -r 23.98 -acodec mp3 -ar 48000 -ab 112k /mnt/sharefat/japanese/yua/yua01.mp4
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
configuration: --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
libavutil version: 0d.49.0.0
libavcodec version: 0d.51.11.0
libavformat version: 0d.50.5.0
built on Sep 20 2006 00:26:15, gcc: 4.1.2 20060906 (prerelease) (Ubuntu 4.1.1-13ubuntu2)

Seems that stream 0 comes from film source: 30000.00 (30000/1) -> 23.98 (24000/1001)
Input #0, avi, from '/mnt/sharefat/japanese/yua/yua01.avi':
Duration: 00:28:38.1, start: 0.000000, bitrate: 1134 kb/s
Stream #0.0: Video: mpeg4, yuv420p, 640x480, 23.98 fps(r)
Stream #0.1: Audio: mp3, 48000 Hz, stereo, 112 kb/s
File '/mnt/sharefat/japanese/yua/yua01.mp4' already exists. Overwrite ? [y/N] y
Output #0, mp4, to '/mnt/sharefat/japanese/yua/yua01.mp4':
Stream #0.0: Video: mpeg4, yuv420p, 320x240, q=2-31, 300 kb/s, 23.98 fps(c)
Stream #0.1: Audio: 0x0000, 48000 Hz, stereo, 112 kb/s
Stream mapping:
Stream #0.0 -> #0.0
Stream #0.1 -> #0.1
Unsupported codec for output stream #0.1


I guess there is a codec not supported with regards to audio. Which one though? Is it a generic non-supported issue or the source file issue in this case? Bit confused here.

---

### Post by matthew on 2007-11-04
The ffmpeg package that is in the standard Ubuntu repos was compiled without support for mp3 because of some legal gray areas. There is a community supported repository (read "non-official") called Medibuntu that has a version of ffmpeg with all the codecs enabled.

[This page will tell you how to enable the repo]("https://help.ubuntu.com/community/Medibuntu").

[This page tells you a bit more about the group responsible.]("http://www.medibuntu.org/")

There are a few other really useful packages there as well that might interest you. Make sure you read first, so you know what the legal issues are...that said, I have never heard of anyone having a legal problem because they used any of these packages, but I am not a lawyer. :)

If you enable the Medibuntu repos, you can just upgrade the ffmpeg package using apt-get, synaptic, or your favorite method.

---

### Post by coolboarderguy on 2007-11-07
HI All,

matthew, great stuff. Thank you.

---

### Post by Creative2 on 2007-11-07
error in command line
112k 

read man ffmpeg 

-ab bitrate
           Set the audio bitrate in kbit/s (default = 64).

ffmpeg need of k only in video bitrate  instead in audio bitrate no
so example

ffmpeg -i snatch_1.vob -f avi -vcodec mpeg4 -b 800k -g 300 -bf 2 -acodec mp3 -ab 128 snatch.avi

for you :

sudo ffmpeg -i /mnt/sharefat/japanese/yua/yua01.avi -vcodec mpeg4 -s 320x240 -b 300k -r 23.98 -acodec mp3 -ar 48000 -ab 112 /mnt/sharefat/japanese/yua/yua01.mp4

---

