---
title: "mp4 to flv using ffmpeg on Ubuntu server 10.04"
date: 2010-11-06
forum: Multimedia Software
---

### Post by tapas_mishra on 2010-11-06
I am doing a conversion of mp4 to flv on a GUI less server where I have only SSH access.( I tried winff and X forwarding that had hanged while doing this conversion so winff is not possible for me)

I do not have any idea of the 
codecs,bitrate of this mp4 video.
Some one had converted from an m4v to mp4 and then uploaded this on the server.

When I tried converting on command line 
as follows

```

ffmpeg -i stats_estimation.mp4 out.flv
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:41:55, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 29.94 (5000/167) -> 44.92 (539/12)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'stats_estimation.mp4':
  Duration: 02:47:05.56, start: 0.000000, bitrate: 237 kb/s
    Stream #0.0(eng): Video: h264, yuv420p, 320x240, 44.92 tbr, 14.97 tbn, 29.94 tbc
    Stream #0.1(eng): Audio: aac, 32000 Hz, stereo, s16
Output #0, flv, to 'out.flv':
    Stream #0.0(eng): Video: flv, yuv420p, 320x240, q=2-31, 200 kb/s, 90k tbn, 44.92 tbc
    Stream #0.1(eng): Audio: adpcm_swf, 32000 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[adpcm_swf @ 0xa4ef60]Sample rate must be 11025, 22050 or 44100
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height

```
I have above error.
I checked this page
[http://www.ffmpeg.org/ffmpeg-doc.html](http://www.ffmpeg.org/ffmpeg-doc.html)
but I could not understand much.
Can some one help to figure out what should I be doing to get this video to flv in this case?
The OS is Ubuntu 10.04 64 bit server edition and
aptitude install winff 
was what  I had used to get ffmpeg or any thing else.

---

### Post by lykeion on 2010-11-06
Try with something like this:
```
ffmpeg -i stats_estimation.mp4 -ar 22050 -acodec libmp3lame -ab 32K -r 25 -s 320x240 -vcodec flv out.flv
```

However this line may indicate something wrong with your input file:> Seems stream 0 codec frame rate differs from container frame rate: 29.94 (5000/167) -> 44.92 (539/12)

---

### Post by andrew.46 on 2010-11-06
Hi tapas_mishra,

Your problem is that you have left the conversion to flv with the FFmpeg *defaults *and a little tweaking is required for the adpcm_swf sound. However the existing codecs for your file (h.264 video and aac sound) will also work in an flv container so your best option might be the following:

```
ffmpeg -i stats_estimation.mp4 -acodec copy -vcodec copy stats_estimation.flv
```

Andrew

---

### Post by tapas_mishra on 2010-11-08
Thanks for pointing the errors
> **lykeion said:**
> 
However this line may  indicate something wrong with your input file:
Can you elaborate this a bit  more?


> ffmpeg -i stats_estimation.mp4 -ar 22050 -acodec libmp3lame -ab 32K -r 25  -vcodec flv out.flv
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:41:55, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 29.94 (5000/167) -> 44.92 (539/12)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'stats_estimation.mp4':
  Duration: 02:47:05.56, start: 0.000000, bitrate: 237 kb/s
    Stream #0.0(eng): Video: h264, yuv420p, 320x240, 44.92 tbr, 14.97 tbn, 29.94 tbc
    Stream #0.1(eng): Audio: aac, 32000 Hz, stereo, s16
Unknown encoder 'libmp3lame'
Then I tried 
```

sudo aptitude install libmp3lame
 libmp3lame0 

```Which happened successfully then I tried

> ffmpeg -i stats_estimation.mp4 -ar 22050 -acodec libmp3lame -ab 32K -r 25  -vcodec flv out.flv
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:41:55, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 29.94 (5000/167) -> 44.92 (539/12)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'stats_estimation.mp4':
  Duration: 02:47:05.56, start: 0.000000, bitrate: 237 kb/s
    Stream #0.0(eng): Video: h264, yuv420p, 320x240, 44.92 tbr, 14.97 tbn, 29.94 tbc
    Stream #0.1(eng): Audio: aac, 32000 Hz, stereo, s16
Unknown encoder 'libmp3lame'
The same error.

> **lykeion said:**
> 
However this line may  indicate something wrong with your input file:
Seems stream 0 codec frame rate differs from container frame rate: 29.94 (5000/167) -> 44.92 (539/12)                      

 I could not understand this part completely.Since I have not shot these videos myself so can not say about it completely though I am getting a little bit of what you are saying.Can you elaborate this point as what you wanted me to understand?
and the other command which Andrew suggested I tried

```
ffmpeg -i stats_estimation.mp4 -acodec copy -vcodec copy stats_estimation.flv
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:41:55, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 29.94 (5000/167) -> 44.92 (539/12)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'stats_estimation.mp4':
  Duration: 02:47:05.56, start: 0.000000, bitrate: 237 kb/s
    Stream #0.0(eng): Video: h264, yuv420p, 320x240, 44.92 tbr, 14.97 tbn, 29.94 tbc
    Stream #0.1(eng): Audio: aac, 32000 Hz, stereo, s16
Output #0, flv, to 'stats_estimation.flv':
    Stream #0.0(eng): Video: 0x0000, yuv420p, 320x240, q=2-31, 90k tbn, 14.97 tbc
    Stream #0.1(eng): Audio: 0x0000, 32000 Hz, stereo, s16
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame=150083 fps=21001 q=-1.0 Lsize=  295035kB time=10025.48 bitrate= 241.1kbits/s    
video:190797kB audio:96213kB global headers:0kB muxing overhead 2.796174%

```

---

### Post by nothingspecial on 2010-11-08
You might need to do this

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by tapas_mishra on 2010-11-08
I did try that link you gave me and followed the instructions there 
I did this at mylaptop which is 10.04 
> E: Couldn't find package libjack-jackd2-dev

Your link talks about 10.10 and the same link redirects to [Here. ]("http://ubuntuforums.org/showthread.php?t=786095")
for 10.04 64 bit.
Where as I see
[http://packages.ubuntu.com/search?keywords=libjack-jackd2-dev](http://packages.ubuntu.com/search?keywords=libjack-jackd2-dev)
is for Maverick only.

---

### Post by ron999 on 2010-11-08
..

---

### Post by FakeOutdoorsman on 2010-11-08
> **tapas_mishra said:**
> I did try that link you gave me and followed the instructions there 
I did this at mylaptop which is 10.04 

Your link talks about 10.10 and the same link redirects to [Here. ]("http://ubuntuforums.org/showthread.php?t=786095")
for 10.04 64 bit.
Where as I see
[http://packages.ubuntu.com/search?keywords=libjack-jackd2-dev](http://packages.ubuntu.com/search?keywords=libjack-jackd2-dev)
is for Maverick only.

The guide you followed is for Maverick only. On that same page is a link to the Lucid version.

Although it is an excellent option you don't need to compile FFmpeg to enable MP3 encoding.  You can still use the old FFmpeg from the repository:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by tapas_mishra on 2010-11-09
I followed your  link to  guide 
[http://ubuntuforums.org/showpost.php?p=9868359&postcount=1289](http://ubuntuforums.org/showpost.php?p=9868359&postcount=1289)
```

sudo apt-get remove ffmpeg x264 libx264-dev
sudo apt-get update
sudo apt-get install build-essential subversion git-core checkinstall yasm texi2html libfaac-dev libopencore-amrnb-dev libopencore-amrwb-dev libsdl1.2-dev libtheora-dev libvorbis-dev libx11-dev libxfixes-dev libxvidcore-dev zlib1g-dev
cd
git clone git://git.videolan.org/x264.git
cd x264

```
upto above instructions from the guide worked well.

When I did 
```
./configure --enable-libmp3lame
```
I get this error
```
Unknown option --enable-libmp3lame, ignored
```

Suggest a remedy for the above so that if some one comes across this thread should help them.

But the second link you gave
has worked great
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)
this is the link I am referring to and I can see that my video was converted 
by this command as some one pointed out above

```
ffmpeg -i stats_estimation.mp4 -ar 22050 -acodec libmp3lame -ab 32K -r 25 -s 320x240 -vcodec flv out.flv
```
and that too with ultra fast speed.
The same video on another Operating System (Not windows) took 7 hours to be converted from m4v to mp4 (1.2GB file)
The same file to convert from mp4 to flv just took 30 minutes by following the guides you people mentioned.
I am really surprised at this can you help to figure out the reason behind this?

---

