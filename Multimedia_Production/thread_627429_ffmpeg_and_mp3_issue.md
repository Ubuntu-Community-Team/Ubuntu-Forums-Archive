---
title: "ffmpeg and mp3 issue"
date: 2007-11-30
forum: Multimedia Production
---

### Post by pieroxy on 2007-11-30
First of all, I've read (almost) everything on the subject. For instance, I know that I need a version of ffmpeg compiled with the --enable-libmp3lame option, such as the one in medibuntu.

So here is what I have done:
1. Enabled medibuntu
2. uninstall ffmpeg
3. reinstall ffmpeg from the medibuntu repo

And still, no luck. ffmpeg -formats shows only D & A for mp3.

I have another Gutsy at work in which that works perfectly fine. Both are up to date gutsy releases. ffmpeg executable are the same. The only difference I can find is when I execute "ldd /usr/bin/ffmpeg"

On the machine at work:
```
ldd /usr/bin/ffmpeg
        linux-gate.so.1 =>  (0xffffe000)
        libavformat.so.1d => /usr/lib/libavformat.so.1d (0xb7ebc000)
        libavcodec.so.1d => /usr/lib/libavcodec.so.1d (0xb79e2000)
        libavutil.so.1d => /usr/lib/libavutil.so.1d (0xb79d7000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb79b2000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb799a000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7850000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb783b000)
        libogg.so.0 => /usr/lib/libogg.so.0 (0xb7836000)
        libdc1394_control.so.13 => /usr/lib/libdc1394_control.so.13 (0xb7826000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7822000)
        libgsm.so.1 => /usr/lib/libgsm.so.1 (0xb7812000)
        libmp3lame.so.0 => /usr/lib/libmp3lame.so.0 (0xb777d000)
        libtheora.so.0 => /usr/lib/libtheora.so.0 (0xb7744000)
        libvorbis.so.0 => /usr/lib/libvorbis.so.0 (0xb771b000)
        libvorbisenc.so.2 => /usr/lib/libvorbisenc.so.2 (0xb7622000)
        libxvidcore.so.4 => /usr/lib/libxvidcore.so.4 (0xb750c000)
        libx264.so.54 => /usr/lib/libx264.so.54 (0xb7481000)
        libfaac.so.0 => /usr/lib/libfaac.so.0 (0xb7470000)
        /lib/ld-linux.so.2 (0xb7f57000)
        libraw1394.so.8 => /usr/lib/libraw1394.so.8 (0xb746a000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7376000)
        libmp4v2.so.0 => /usr/lib/libmp4v2.so.0 (0xb72cc000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb72c1000)
```

On the machine at home:
```
ldd /usr/bin/ffmpeg
        linux-gate.so.1 =>  (0xffffe000)
        libavformat.so.1d => /usr/lib/libavformat.so.1d (0xb7e72000)
        libavcodec.so.1d => /usr/lib/libavcodec.so.1d (0xb7a17000)
        libavutil.so.1d => /usr/lib/libavutil.so.1d (0xb7a0d000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb79e8000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb79d0000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7886000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7870000)
        libogg.so.0 => /usr/lib/libogg.so.0 (0xb786b000)
        libdc1394_control.so.13 => /usr/lib/libdc1394_control.so.13 (0xb785c000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7858000)
        libgsm.so.1 => /usr/lib/libgsm.so.1 (0xb7848000)
        libtheora.so.0 => /usr/lib/libtheora.so.0 (0xb780e000)
        libvorbis.so.0 => /usr/lib/libvorbis.so.0 (0xb77e6000)
        libvorbisenc.so.2 => /usr/lib/libvorbisenc.so.2 (0xb76ed000)
        /lib/ld-linux.so.2 (0xb7f10000)
        libraw1394.so.8 => /usr/lib/libraw1394.so.8 (0xb76e7000)

```

So the library /usr/lib/libmp3lame.so.0 exists in both systems and is the same file...
Any ideas ?

---

### Post by eye208 on 2007-11-30
> **pieroxy said:**
> ffmpeg executable are the same.
How can they be the same if their library dependencies differ?

---

### Post by pieroxy on 2007-11-30
> **eye208 said:**
> How can they be the same if their library dependencies differ?

Well, that's where I coudn't go any further. Unless they show a (rare) collision in md5sum, their md5sum is the very same. So I assumed the files are identical. I tested only ffmpeg and libmp3lame.so.0...

I am at a loss to get anywhere from here.

---

### Post by eye208 on 2007-11-30
If you post the version number or .deb file name of the Medibuntu ffmpeg, I will download and compare it to the Ubuntu one here and post the MD5 sums I get. This way we may be able to identify the problem.

---

### Post by pieroxy on 2007-12-01
> **eye208 said:**
> If you post the version number or .deb file name of the Medibuntu ffmpeg, I will download and compare it to the Ubuntu one here and post the MD5 sums I get. This way we may be able to identify the problem.

Sure thing:

```
apt-cache policy ffmpeg
ffmpeg:
  Installed: 3:0.cvs20070307-5ubuntu4+medibuntu2
  Candidate: 3:0.cvs20070307-5ubuntu4+medibuntu2
  Version table:
 *** 3:0.cvs20070307-5ubuntu4+medibuntu2 0
        500 http://fr.packages.medibuntu.org gutsy/free Packages
        100 /var/lib/dpkg/status
     3:0.cvs20070307-5ubuntu4 0
        500 http://de.archive.ubuntu.com gutsy/universe Packages

```

```
apt-cache policy liblame0
liblame0:
  Installed: 3.97-0.0
  Candidate: 3.97-0.0
  Version table:
 *** 3.97-0.0 0
        500 http://de.archive.ubuntu.com gutsy/multiverse Packages
        100 /var/lib/dpkg/status

```

```
ls -l /usr/lib/libmp3lame.so.0
lrwxrwxrwx 1 root root 19 2007-11-30 10:47 /usr/lib/libmp3lame.so.0 -> libmp3lame.so.0.0.0

```

```
md5sum /usr/lib/libmp3lame.so.0
a9e044f00237f7854d0469d573bd9f02  /usr/lib/libmp3lame.so.0
```

```
md5sum /usr/bin/ffmpeg
78b903b58116d5804b3b4c9993fb6527  /usr/bin/ffmpeg
```

---

### Post by eye208 on 2007-12-01
I think the cause of the problem is not ffmpeg, but libavcodec. The ldd command lists dependencies recursively. Ubuntu's libavcodec does not link to libmp3lame, but Medibuntu's one does. I guess ffmpeg itself does not link to libmp3lame at all, only to libavcodec, which in turn may or may not link to libmp3lame.

If you install the libavcodec package from Medibuntu too, things should be fine.

---

### Post by pieroxy on 2007-12-01
> **eye208 said:**
> I think the cause of the problem is not ffmpeg, but libavcodec. The ldd command lists dependencies recursively. Ubuntu's libavcodec does not link to libmp3lame, but Medibuntu's one does. I guess ffmpeg itself does not link to libmp3lame at all, only to libavcodec, which in turn may or may not link to libmp3lame.

If you install the libavcodec package from Medibuntu too, things should be fine.

Thanks for the input. I will look at my work's system as soon as I get back there. In the meantime, I can tell that I have the medibuntu version of libavcodec (as far as I can tell that is):

```
apt-cache policy libavcodec1d
libavcodec1d:
  Installed: 3:0.cvs20070307-5ubuntu4+medibuntu2
  Candidate: 3:0.cvs20070307-5ubuntu4+medibuntu2
  Version table:
 *** 3:0.cvs20070307-5ubuntu4+medibuntu2 0
        500 http://fr.packages.medibuntu.org gutsy/free Packages
        100 /var/lib/dpkg/status
     3:0.cvs20070307-5ubuntu4 0
        500 http://de.archive.ubuntu.com gutsy/main Packages

```

And it doesn't looks like ldd lists dependencies recursively as ```
ldd /usr/lib/libavcodec.so.1d
        linux-gate.so.1 =>  (0xffffe000)
        libavutil.so.1d => /usr/lib/libavutil.so.1d (0xb7a84000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7a5f000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7a4a000)
        libgsm.so.1 => /usr/lib/libgsm.so.1 (0xb7a3a000)
        libmp3lame.so.0 => /usr/lib/libmp3lame.so.0 (0xb79a5000)
        libtheora.so.0 => /usr/lib/libtheora.so.0 (0xb796c000)
        libvorbis.so.0 => /usr/lib/libvorbis.so.0 (0xb7943000)
        libvorbisenc.so.2 => /usr/lib/libvorbisenc.so.2 (0xb784a000)
        libxvidcore.so.4 => /usr/lib/libxvidcore.so.4 (0xb7734000)
        libx264.so.54 => /usr/lib/libx264.so.54 (0xb76a9000)
        libfaac.so.0 => /usr/lib/libfaac.so.0 (0xb7698000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7694000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb767b000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7531000)
        /lib/ld-linux.so.2 (0x80000000)
        libogg.so.0 => /usr/lib/libogg.so.0 (0xb752c000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7439000)
        libmp4v2.so.0 => /usr/lib/libmp4v2.so.0 (0xb738f000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7383000)

```

... That one is linked with libmp3lame .... but ffmpeg doesn't show the link with ldd.

---

### Post by eye208 on 2007-12-02
> **pieroxy said:**
> That one is linked with libmp3lame .... but ffmpeg doesn't show the link with ldd.
Indeed.

I downloaded your ffmpeg executable too and checked both its checksum and dependencies. The checksum is identical, and ldd does not show any link to libmp3lame.

The file on your computer at work must be a different one.

---

