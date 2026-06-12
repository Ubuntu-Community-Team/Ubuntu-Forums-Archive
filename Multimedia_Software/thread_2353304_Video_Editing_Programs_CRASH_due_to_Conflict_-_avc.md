---
title: "Video Editing Programs CRASH due to Conflict - avconv - ffmpeg"
date: 2017-02-20
forum: Multimedia Software
---

### Post by Rick St. George on 2017-02-20
My Original Post was here; (CLOSED)
[https://ubuntuforums.org/showthread.php?t=2283702]("https://ubuntuforums.org/showthread.php?t=2283702&highlight=brasero")

Found this thread that seemed to addres the issue, but was unresolved due to no come back by thread starter.
[https://ubuntuforums.org/showthread.php?t=2289501](https://ubuntuforums.org/showthread.php?t=2289501)

Here is my Printout;

```
$ apt-cache policy ffmpeg libav-tools
```
> 
ffmpeg:
  Installed: 7:2.8.8-0ubuntu0.16.04.1
  Candidate: 7:2.8.11-0ubuntu0.16.04.1
  Version table:
     7:2.8.11-0ubuntu0.16.04.1 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/universe amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages
 *** 7:2.8.8-0ubuntu0.16.04.1 100
        100 /var/lib/dpkg/status
     7:2.8.6-1ubuntu2 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages
libav-tools:
  Installed: 7:2.8.8-0ubuntu0.16.04.1
  Candidate: 7:2.8.11-0ubuntu0.16.04.1
  Version table:
     7:2.8.11-0ubuntu0.16.04.1 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/universe amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/universe i386 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages
 *** 7:2.8.8-0ubuntu0.16.04.1 100
        100 /var/lib/dpkg/status
     7:2.8.6-1ubuntu2 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/universe i386 Packages


```
$ apt-cache show ffmpeg
```
> 
Package: ffmpeg
Status: install ok installed
Priority: optional
Section: video
Installed-Size: 1855
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Multi-Arch: foreign
Version: 7:2.8.8-0ubuntu0.16.04.1
Replaces: libav-tools (<< 6:12~~), qt-faststart (<< 7:2.7.1-3~)
Depends: libavcodec-ffmpeg56 (>= 7:2.7) | libavcodec-ffmpeg-extra56 (>= 7:2.7), libavdevice-ffmpeg56 (>= 7:2.6), libavfilter-ffmpeg5 (>= 7:2.4), libavformat-ffmpeg56 (>= 7:2.6), libavresample-ffmpeg2 (>= 7:2.4), libavutil-ffmpeg54 (>= 7:2.5), libc6 (>= 2.14), libpostproc-ffmpeg53 (>= 7:2.4), libsdl1.2debian (>= 1.2.11), libswresample-ffmpeg1 (>= 7:2.4), libswscale-ffmpeg3 (>= 7:2.4), libvdpau1 (>= 0.2), libx11-6
Suggests: ffmpeg-doc
Breaks: libav-tools (<< 6:12~~), qt-faststart (<< 7:2.7.1-3~)
Conffiles:
 /etc/ffserver.conf 81b94256d412c37f0f81214b3737ac53
Description-en: Tools for transcoding, streaming and playing of multimedia files
 FFmpeg is the leading multimedia framework, able to decode, encode, transcode,
 mux, demux, stream, filter and play pretty much anything that humans and
 machines have created. It supports the most obscure ancient formats up to the
 cutting edge.
 .
 This package contains:
  * ffmpeg: a command line tool to convert multimedia files between formats
  * ffserver: a multimedia streaming server for live broadcasts
  * ffplay: a simple media player based on SDL and the FFmpeg libraries
  * ffprobe: a simple multimedia stream analyzer
  * qt-faststart: a utility to rearrange Quicktime files
Description-md5: 032ff4ee68b923f5137379a7857cb8a8
Homepage: [https://ffmpeg.org/](https://ffmpeg.org/)
Original-Maintainer: Debian Multimedia Maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>


```
$ avconv
```
> 
ffmpeg version 2.8.8-0ubuntu0.16.04.1 Copyright (c) 2000-2016 the FFmpeg developers
  built with gcc 5.4.0 (Ubuntu 5.4.0-6ubuntu1~16.04.2) 20160609
  configuration: --prefix=/usr --extra-version=0ubuntu0.16.04.1 --build-suffix=-ffmpeg --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --cc=cc --cxx=g++ --enable-gpl --enable-shared --disable-stripping --disable-decoder=libopenjpeg --disable-decoder=libschroedinger --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmodplug --enable-libmp3lame --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-librtmp --enable-libschroedinger --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxvid --enable-libzvbi --enable-openal --enable-opengl --enable-x11grab --enable-libdc1394 --enable-libiec61883 --enable-libzmq --enable-frei0r --enable-libx264 --enable-libopencv
  WARNING: library configuration mismatch
  avcodec     configuration: --prefix=/usr --extra-version=0ubuntu0.16.04.1 --build-suffix=-ffmpeg --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --cc=cc --cxx=g++ --enable-gpl --enable-shared --disable-stripping --disable-decoder=libopenjpeg --disable-decoder=libschroedinger --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmodplug --enable-libmp3lame --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-librtmp --enable-libschroedinger --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxvid --enable-libzvbi --enable-openal --enable-opengl --enable-x11grab --enable-libdc1394 --enable-libiec61883 --enable-libzmq --enable-frei0r --enable-libx264 --enable-libopencv --enable-version3 --disable-doc --disable-programs --disable-avdevice --disable-avfilter --disable-avformat --disable-avresample --disable-postproc --disable-swscale --enable-libopencore_amrnb --enable-libopencore_amrwb --enable-libvo_aacenc --enable-libvo_amrwbenc
  libavutil      54. 31.100 / 54. 31.100
  libavcodec     56. 60.100 / 56. 60.100
  libavformat    56. 40.101 / 56. 40.101
  libavdevice    56.  4.100 / 56.  4.100
  libavfilter     5. 40.101 /  5. 40.101
  libavresample   2.  1.  0 /  2.  1.  0
  libswscale      3.  1.101 /  3.  1.101
  libswresample   1.  2.101 /  1.  2.101
  libpostproc    53.  3.100 / 53.  3.100

Hyper fast Audio and Video encoder
usage: ffmpeg [options] [[infile options] -i infile]... {[outfile options] outfile}...

Use -h to get full help or, even better, run 'man ffmpeg'


I believe it is obvious there is a conflict between avconv and ffmpeg. But I don't know the proper solution. Thought maybe REMOVE / UNINSTALL all VIDEO programs, REMOVE / UINSTALL FFMPEG, and Re-Install the "Best" Video Editing software for UbuntuStudio v16.04. 

Any ideas or suggestions for everyone?
Thanks!
Rick
):P

---

### Post by Rick St. George on 2017-02-20
Found info regarding removing "ffmpeg". Here is what it shows in terminal prior to removing.

```
 $ sudo apt-get remove ffmpeg 
```

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-59 linux-headers-4.4.0-59-lowlatency
  linux-image-4.4.0-59-lowlatency
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  devede dvdstyler ffmpeg libav-tools
0 upgraded, 0 newly installed, 4 to remove and 4 not upgraded.
After this operation, 6,841 kB disk space will be freed.
Do you want to continue? Y/n 


So if DeVeDe and DVDstyler must be removed, What Video Editor / DVD Creator software is recommended for use with UbuntuStudio v16.04? 
And should I remove "avconv / libav"? 

Edit Note: Removed "libav". I doubt much has changed since one developers post here;
[http://blog.pkh.me/p/13-the-ffmpeg-libav-situation.html](http://blog.pkh.me/p/13-the-ffmpeg-libav-situation.html)

For more History of the fork and confusion between the two, please review the following;
[URL="https://en.wikipedia.org/wiki/Libav"]https://en.wikipedia.org/wiki/Libav
[/URL]

Thanks!
Rick

---

### Post by mc4man on 2017-02-26
May be more useful to show termnal output from crashing app as there is no conflict between ffmpeg & libav-tools/avconv
(- avconv is just a symlink to ffmpeg as libav is no longer in Ubuntu

---

