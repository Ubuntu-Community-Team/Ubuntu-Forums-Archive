---
title: "ffmpeg script stopped working"
date: 2012-03-31
forum: Multimedia Software
---

### Post by ibn4n on 2012-03-31
Hi folks,
 
Fairly new to all this, so I'm sorry if this turns out to be something silly on my part.
 
I spent a lot of time trying to get a script for auto transcoding mkvs to mp4s (converting ac3 or dts to aac). I eventually found a script with a tutorial that was working amazingly well... then it suddenly stopped. I've stepped through the script, and I have found my problem. Now I'm hoping someone can help me fix it.
 
Here's the problem code:
 
```
ffmpeg -i "$pathNoExt".ac3 -acodec pcm_s161e -ac 2 -f wav - | neroAacEnc -lc -br 160000 -ignorelength -if - -of "$pathNoExt".aac
```
 
Here's what I get:
 
```
-bash: /usr/local/bin/neroAacEnc: No such file or directory
FFmpeg version 0.6.4-4:0.6.4-0ubuntu0.11.04.1, Copyright (c) 2000-2010 the Libav developers
  built on Jan  4 2012 16:13:16 with gcc 4.5.2
  configuration: --extra-version=4:0.6.4-0ubuntu0.11.04.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6.4-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavcodec  configuration: --extra-version=4:0.6.4-1ubuntu1+medibuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 --enable-vaapi --enable-libopenjpeg --enable-libfaac --enable-nonfree --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavformat configuration: --extra-version=4:0.6.4-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavdevice configuration: --extra-version=4:0.6.4-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libswscale  configuration: --extra-version=4:0.6.4-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libpostproc configuration: --extra-version=4:0.6.4-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[ac3 @ 0x2343670]max_analyze_duration reached
[ac3 @ 0x2343670]Estimating duration from bitrate, this may be inaccurate
Input #0, ac3, from '/htpc/Transcode/TestFile.ac3':
  Duration: 01:55:00.92, bitrate: 640 kb/s
    Stream #0.0: Audio: ac3, 48000 Hz, 5.1, s16, 640 kb/s
Unknown encoder 'pcm_s161e'
```
 
So the things that stand out are:
 
```
-bash: /usr/local/bin/neroAacEnc: No such file or directory
```
 
- This has me perplexed because it seems to be there:
 
```
username@imagination:/usr/local/bin$ ls -la
total 1536
drwxr-xr-x  2 root root   4096 2011-12-20 19:10 .
drwxr-xr-x 10 root root   4096 2011-03-04 21:19 ..
-rwxr-xr-x  1 root root 395236 2012-03-31 19:20 neroAacDec
-rwxr-xr-x  1 root root 910988 2012-03-31 19:20 neroAacEnc
-rwxr-xr-x  1 root root 251620 2012-03-31 19:20 neroAacTag
```
 
There's also this line:
 
```
WARNING: library configuration mismatch
```
 
And finally, this stands out:
 
```
Unknown encoder 'pcm_s161e'
```
 
Any ideas? Any help would be much appreciated!

---

### Post by BicyclerBoy on 2012-03-31
The cmd line changes at the time..makes little sense that the sample format was a codec setting.. wav is raw data..

These may lead to a solution..
ffmpeg -i inputfile -sample_fmt s16 -ac 2 -f wav output.wav

ffmpeg -i inputfile -ac 2 -format s16le - | pipe-to-app

You do realise you are down converting 5.1 to 2.0 ?

If your AC3 has extended bitstream info you maybe able to control downmix
[http://ffmpeg.org/ffmpeg.html#toc-Extended-Bitstream-Information](http://ffmpeg.org/ffmpeg.html#toc-Extended-Bitstream-Information)
The latest ffmpeg allows you to pick using: 
&#8216;-dmix_mode mode&#8217;
mode =&#8216;ltrt&#8217; dolby surround stereo downmix & other options see documentation.

---

### Post by jmasterfunk on 2012-03-31
That's very interesting.  I am also rebuilding my "server" and I am having the same trouble with nero encoder.

I happen to be running 12.04, are you?

---

### Post by ibn4n on 2012-03-31
Thanks for the response! That works! I have a wave file. (The command is crazy fast too). I am doing all this remotely from a hotel, so I can't listen to it, but everything looks good.
 
Now I just gotta figure out why the nero encoder can't be seen. Once I can do that, I think the WAF will be back to normal :)
 
(About the down-converting... the script ultimately imports the original ac3 file into the mp4 container too. But the downconverted aac track allows it to play on more of our devices.)
 
Thanks again! Once I figure out what how to get nero working, I'll post that and set this to solved.

---

### Post by ibn4n on 2012-03-31
> **jmasterfunk said:**
> That's very interesting. I am also rebuilding my "server" and I am having the same trouble with nero encoder.
 
I happen to be running 12.04, are you?
 
No, I'm on 11.04. I did pull down the latest updates from apt-get, though. Maybe that's when the script broke. I don't use it daily, so I'm not sure.

---

### Post by jmasterfunk on 2012-03-31
I happen to be running a 64 bit version where I only had a 32 bit version of ubuntu before.

Anyways.  Looks like we're missing some libraries.  Here's what I just did:

apt-get install gcc-multilib
sudo apt-get install ia32-libs

This seemed to work.  That last package is the big hammer solution and maybe just try running this one instead:

sudo apt-get install libstdc++6:i386

---

### Post by BicyclerBoy on 2012-03-31
I edited my post added

ffmpeg -i inputfile -ac 2 -format s16le - | pipe-to-app
this may not work because nero only accepts wav..

fmpeg -i inputfile -sample_fmt s16 -ac 2 -f wav -| pipe-to-app

Your script is piping the ffmpeg output to input of Nero AAC encoder.
The error is caused (I think) by ffmpeg cmd line options changing..

Or do you guys think the Nero encoder is broken ?
What happens if you run it from terminal
neroAacEnc --help

The ia32-libs have always been needed to run 32bit app on 64 bit linux..

Have you updated nero & gotten a 32bit version?
Was there ever a 64bit version ?

---

### Post by ibn4n on 2012-03-31
Thanks to everyone who helped me fix this... it is now working again!
 
It seems that the ffmpeg thing was a red herring. The libs that jmasterfunk added, as best I can tell, allowed the 32bit version of neroAacEnc (they don't seem to have a 64bit version) work.
 
Thanks to both jmasterfunk and BicyclerBoy for their help!!

---

