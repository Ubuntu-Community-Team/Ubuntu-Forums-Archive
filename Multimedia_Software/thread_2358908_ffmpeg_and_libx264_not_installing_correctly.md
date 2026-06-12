---
title: "ffmpeg and libx264 not installing correctly"
date: 2017-04-18
forum: Multimedia Software
---

### Post by cyocum on 2017-04-18
I am on Xubuntu 17.04 (recently updated but this has been going on for a while) and when I install ffmpeg via apt and try to run it I get the following error:

```

ffmpeg: error while loading shared libraries: libx264.so.142: cannot open shared object file: No such file or directory

```

When I do ldd on the ffmpeg installed I see:

```

libx264.so.142 => not found

```

I checked my ldconfig to see what it thought was installed I get:

```

	libx264.so.148 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libx264.so.148
	libx264.so (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libx264.so

```

So, I have absolutely no idea where or why ffmpeg when installed via apt thinks that there should be a libx264.so.142.  I have also done a find in /usr and cannot find libx264.so.142 anywhere on my system.  Does anyone have any suggestions on what I should try next?

---

### Post by mc4man on 2017-04-18
post 
```
apt-cache policy ffmpeg
```
```
apt-cache show ffmpeg
```
```
which ffmpeg
```

---

### Post by cyocum on 2017-04-19
apt-cache policy ffmpeg

```

ffmpeg:
  Installed: 7:3.2.4-1build2
  Candidate: 7:3.2.4-1build2
  Version table:
 *** 7:3.2.4-1build2 500
        500 http://gb.archive.ubuntu.com/ubuntu zesty/universe amd64 Packages
        100 /var/lib/dpkg/status


```

apt-cache show ffmpeg

```

Package: ffmpeg
Priority: optional
Section: universe/video
Installed-Size: 2107
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Multimedia Maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>
Architecture: amd64
Version: 7:3.2.4-1build2
Replaces: libav-tools (<< 6:12~~), qt-faststart (<< 7:2.7.1-3~)
Depends: libavcodec57 (>= 7:3.2.4) | libavcodec-extra57 (>= 7:3.2.4), libavdevice57 (>= 7:3.2.4), libavfilter6 (>= 7:3.2.4) | libavfilter-extra6 (>= 7:3.2.4), libavformat57 (>= 7:3.2.4), libavresample3 (>= 7:3.2.4), libavutil55 (>= 7:3.2.4), libc6 (>= 2.14), libpostproc54 (>= 7:3.2.4), libsdl2-2.0-0 (>= 2.0.4), libswresample2 (>= 7:3.2.4), libswscale4 (>= 7:3.2.4), libva1 (>= 1.7.3)
Suggests: ffmpeg-doc
Breaks: libav-tools (<< 6:12~~), qt-faststart (<< 7:2.7.1-3~)
Filename: pool/universe/f/ffmpeg/ffmpeg_3.2.4-1build2_amd64.deb
Size: 1491842
MD5sum: cebdbc22a636ed789ed3229f6aca2b0d
SHA1: 9885d22de58a098f888a8fc363d6194719e9432f
SHA256: e98cbea2be6dbee849bd57d70587973056282576cd2c816e7342981da5767124
Description-en_GB: Tools for transcoding, streaming and playing of multimedia files
 FFmpeg is the leading multimedia framework, able to decode, encode,
 transcode, mux, demux, stream, filter and play pretty much anything that
 humans and machines have created. It supports the most obscure ancient
 formats up to the cutting edge.
 .
 This package contains:
  * ffmpeg: a command line tool to convert multimedia files between formats
  * ffserver: a multimedia streaming server for live broadcasts
  * ffplay: a simple media player based on SDL and the FFmpeg libraries
  * ffprobe: a simple multimedia stream analyzer
  * qt-faststart: a utility to rearrange Quicktime files
Description-md5: 032ff4ee68b923f5137379a7857cb8a8
Multi-Arch: foreign
Homepage: https://ffmpeg.org/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Task: edubuntu-desktop-gnome, ubuntustudio-video, ubuntustudio-audio, ubuntukylin-desktop, ubuntu-budgie-desktop

```

which ffmpeg
```

/usr/local/bin/ffmpeg

```

---

### Post by mc4man on 2017-04-19
You have installed an older unpackaged version of ffmpeg to /usr/local/bin so get rid of it. Also check in /usr/local/* for any other ffmpeg files to remove.
To test as is run this, ffmpeg (repo version) will start
```
/usr/bin/ffmpeg
```

---

### Post by cyocum on 2017-04-19
Great.  Thanks.  I removed the /usr/local/bin version and a few other ffmpeg related files but I am still getting the same error just with the /usr/bin/ffmpeg now.

---

### Post by mc4man on 2017-04-19
what do these show
```
ls -R /usr/local/lib |grep libavcodec
```
```
ls -R /usr/lib |grep libavcodec
```
```
ldd /usr/bin/ffmpeg
```

---

### Post by cyocum on 2017-04-21
I finally got the hint from your questions that I had even more old libraries from a bad old ffmpeg compile installed in /usr/local/lib so I removed them and now it works.  Thanks!

---

