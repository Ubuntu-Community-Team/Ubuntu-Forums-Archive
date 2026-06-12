---
title: "avconv re-encode to 64kbit/s but metadata shows 32k"
date: 2013-01-18
forum: Multimedia Software
---

### Post by UranUtan on 2013-01-18
Hi,

I reencode an mp3 from 128kbps to 64kbps. I suppose it works OK as I see the resulting MP3 is about half the size of the original MP3. However, the metadata reports bitrate as 32 kbps/s as seen in various media tools (Exaile, Puddletag).

Can you please help me to pinpoint what was wrong?
Thanks in advance

```
$ avconv -i "MyFile.mp3" -codec:a libmp3lame -b 64k "BR64K/MyFile.mp3"

SCREEN OUTPUT:

Input #0, mp3, from 'MyFile.mp3':
  Metadata:
    title           : Test-ReEncoding
    album           : My AlbumName
    track           : 1/2
    genre           :
    TCMP            : 1
    artist          : Linux and al.
    date            : 2011
  Duration: 00:06:49.97, start: 0.000000, bitrate: 128 kb/s
    Stream #0.0: Audio: mp3, 44100 Hz, stereo, s16, 128 kb/s
Output #0, mp3, to 'BR64K/MyFile.mp3':
  Metadata:
    TIT2            : Test-ReEncoding
    TALB            : My AlbumName
    TRCK            : 1/2
    TCON            :
    TCMP            : 1
    TPE1            : Linux and al.
    TDRL            : 2011
    TSSE            : Lavf53.21.0
    Stream #0.0: Audio: libmp3lame, 44100 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (mp3 -> libmp3lame)
Press ctrl-c to stop encoding
size=    3173kB time=406.07 bitrate=  64.0kbits/s    
video:0kB audio:3172kB global headers:0kB muxing overhead 0.009635%

```


version info:
```
avconv version 0.8.4-6:0.8.4-0ubuntu0.12.10.1, Copyright (c) 2000-2012 the Libav developers
  built on Nov  6 2012 16:51:11 with gcc 4.7.2
avconv 0.8.4-6:0.8.4-0ubuntu0.12.10.1
libavutil    51. 22. 1 / 51. 22. 1
libavcodec   53. 35. 0 / 53. 35. 0
libavformat  53. 21. 0 / 53. 21. 0
libavdevice  53.  2. 0 / 53.  2. 0
libavfilter   2. 15. 0 /  2. 15. 0
libswscale    2.  1. 0 /  2.  1. 0
libpostproc  52.  0. 0 / 52.  0. 0
```

lame MP3 encoder used:
```
$ sudo apt-get install libavcodec-extra-53
```

---

### Post by FakeOutdoorsman on 2013-01-18
Test with a recent [FFmpeg static build](http://ffmpeg.org/download.html#LinuxBuilds). If it works you will know that it was a bug that was already fixed (in FFmpeg at least, but perhaps not the fork that you're using).

---

### Post by UranUtan on 2013-01-18
> **FakeOutdoorsman said:**
> Test with a recent [FFmpeg static build](http://ffmpeg.org/download.html#LinuxBuilds). If it works you will know that it was a bug that was already fixed (in FFmpeg at least, but perhaps not the fork that you're using).

Can you please show me the instructions to install this? This page [URL="https://launchpad.net/~jon-severinsson/+archive/ffmpeg"]
Jon Severinsson's FFmpeg PPA[/URL] says "For precise (12.04) and quantal (12.10) this PPA only provides FFmpeg 0.10, as Ubuntu no longer contain any packages depending on the old ABI"

Using avconv or ffmpeg is no importance to me. All I want is something that works. Thanks.

---

### Post by ManamiVixen on 2013-01-18
rather than using "64k", use the full BIT count instead and report back hear if it works or not.

 BTW, 64KB equals 65536 bits. 64 x 1,024, 1,024 being equal to 1 kilobyte.

---

### Post by FakeOutdoorsman on 2013-01-18
> **UranUtan said:**
> Can you please show me the instructions to install this? This page [URL="https://launchpad.net/~jon-severinsson/+archive/ffmpeg"]
Jon Severinsson's FFmpeg PPA[/URL] says "For precise (12.04) and quantal (12.10) this PPA only provides FFmpeg 0.10, as Ubuntu no longer contain any packages depending on the old ABI"

Using avconv or ffmpeg is no importance to me. All I want is something that works. Thanks.

I was wondering if that was going to be confusing... I meant the static builds mentioned in the link and not the PPA. You can try this:

1. Get the static build archive file:
```
wget http://ffmpeg.gusari.org/static/64bit/ffmpeg.static.64bit.2012-12-01.tar.gz
```
2. Extract the archive:
```
tar xzvf ffmpeg.static.64bit.2012-12-01.tar.gz
```
3. Run the static build version of ffmpeg:
```
./ffmpeg -i "MyFile.mp3" -c:a libmp3lame -b:a 64k "BR64K/MyFile.mp3"
```

Note the ./ before the ffmpeg; if omitted it will assume you want your installed version of "ffmpeg".

> **ManamiVixen said:**
> rather than using "64k", use the full BIT count instead and report back hear if it works or not.

 BTW, 64KB equals 65536 bits. 64 x 1,024, 1,024 being equal to 1 kilobyte.

I don't think that should matter since -b takes a value in bits anyway.

---

### Post by UranUtan on 2013-01-18
Hi,

FIXED: using static build. Now the re-encoded file reports 64 kbps as expected. Thanks. Can you please show me how to make this static ffmpeg permanent?

BTW, before attempting the static build of ffmpeg, I had tried avconv by replacing **-b 64k** by **-b 65536**. Same issue.

---

### Post by FakeOutdoorsman on 2013-01-18
You can [compile ffmpeg](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide), move the binary to a location in your $PATH, or use checkinstall and "install" to install it:
```
sudo apt-get remove ffmpeg libav-tools
sudo checkinstall --pkgname=ffmpeg --pkgversion="$(date +%Y%m%d%H%M)-git" --backup=no \
  --deldoc=yes --fstrans=no --default install -Dm755 ffmpeg \
  /usr/local/bin/ffmpeg
```
Or you could simply execute the binary by specifying the full path with running it or with ./ as I showed earlier.

Seems to be YAAB: Yet Another Avconv Bug.

---

### Post by UranUtan on 2013-01-19
Oh wow, a little bit too complicate. As I re-encode rarely, I'll go with the fullpath syntax for now. Thanks very much for your help.

---

### Post by Lynch on 2013-04-03
Thank you FakeOutdoorsman, using the static build fixes it for me too! :)

Anyhow, has any of you found an open bug report at [https://bugzilla.libav.org/](https://bugzilla.libav.org/) or elsewhere? (I haven't)
I'm currently developing an add-on for firefox which relies on ffmpeg/avconv and after all I cannot assume that every Ubuntu user downloads the static binary.

Cheers, Flo

---

### Post by FakeOutdoorsman on 2013-04-03
Perhaps it would be easiest for you to distribute the ffmpeg binary with your plugin. Then you wouldn't have to support buggy libav products or various version differences of ffmpeg.

---

### Post by Lynch on 2013-04-07
Yeah... I might just do that. It wouldn't exactly be a platform independent solution. But on the other hand, relying on ffmpeg/avconv is pretty platform dependent in the first place ;-)

---

### Post by evilsoup on 2013-04-07
FYI, ffmpeg (and avconv) is available on Linux OSX and Windows...

---

### Post by andrew.46 on 2013-04-07
Details here:

[http://ffmpeg.org/platform.html](http://ffmpeg.org/platform.html)

---

