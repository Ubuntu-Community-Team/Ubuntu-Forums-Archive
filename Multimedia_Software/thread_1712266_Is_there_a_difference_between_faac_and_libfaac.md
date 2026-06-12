---
title: "Is there a difference between faac and libfaac?"
date: 2011-03-22
forum: Multimedia Software
---

### Post by ron999 on 2011-03-22
Hi
Is there a difference between **faac** and **libfaac**?

I have an iPod Shuffle.
One of these:- 

[IMG]http://img140.imageshack.us/img140/9927/shufflex.jpg[/IMG]

It plays m4a tracks created using faac encoder.
Like this:-
```
ffmpeg -i foo.flac -f wav - | faac -o test1.m4a -b 152 -
```

But it won't play tracks created using libfaac.
Like this:-
```
ffmpeg -i foo.flac -acodec libfaac -ab 152k test2.m4a
```

I've compared the MediaInfo for the two files.
They look very similar, faac does a more thorough job of tagging.

Does ffmpeg do something to the file when it's converting or muxing with libfaac to make it unplayable by the Shuffle?

I've uploaded the two files.
test1.m4a is created using faac
test2.m4a is created using libfaac
They are here:- [http://www.mediafire.com/?womxhbv26tk5298]("http://www.mediafire.com/?womxhbv26tk5298")

What's the difference?
:confused:

Using Ubuntu Karmic 9.10
and
FAAC 1.26.1
and
FFmpeg version git-N-28456-g1c31b26

---

### Post by FakeOutdoorsman on 2011-03-22
FFmpeg shows some additional differences:
```

$ ffmpeg -i test1.m4a
FFmpeg version git-N-55253-g2da715c, Copyright (c) 2000-2011 the FFmpeg developers
  built on Mar 22 2011 10:47:21 with gcc 4.5.2 20110127 (prerelease)
  configuration: --prefix=/usr/local --enable-gpl --enable-nonfree --enable-libfaac --enable-libmp3lame --enable-libx264 --enable-x11grab
  libavutil    50. 40. 0 / 50. 40. 0
  libavcodec   52.114. 0 / 52.114. 0
  libavformat  52.103. 0 / 52.103. 0
  libavdevice  52.  3. 0 / 52.  3. 0
  libavfilter   1. 76. 0 /  1. 76. 0
  libswscale    0. 12. 0 /  0. 12. 0
  libpostproc  51.  2. 0 / 51.  2. 0
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'test1.m4a':
  Metadata:
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: mp42isom
    creation_time   : 2011-03-22 16:04:14
    encoder         : FAAC 1.26.1 (Aug 16 2008) UNSTABLE
  Duration: 00:04:01.56, start: 0.023220, bitrate: 153 kb/s
    Stream #0.0(eng): Audio: aac, 44100 Hz, stereo, s16, 151 kb/s
    Metadata:
      creation_time   : 2011-03-22 16:04:14
At least one output file must be specified

$ ffmpeg -i test2.m4a
FFmpeg version git-N-55253-g2da715c, Copyright (c) 2000-2011 the FFmpeg developers
  built on Mar 22 2011 10:47:21 with gcc 4.5.2 20110127 (prerelease)
  configuration: --prefix=/usr/local --enable-gpl --enable-nonfree --enable-libfaac --enable-libmp3lame --enable-libx264 --enable-x11grab
  libavutil    50. 40. 0 / 50. 40. 0
  libavcodec   52.114. 0 / 52.114. 0
  libavformat  52.103. 0 / 52.103. 0
  libavdevice  52.  3. 0 / 52.  3. 0
  libavfilter   1. 76. 0 /  1. 76. 0
  libswscale    0. 12. 0 /  0. 12. 0
  libpostproc  51.  2. 0 / 51.  2. 0
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'test2.m4a':
  Metadata:
    major_brand     : M4A 
    minor_version   : 512
    compatible_brands: isomiso2
    creation_time   : 1970-01-01 00:00:00
    encoder         : Lavf52.103.0
  Duration: 00:04:01.58, start: 0.000000, bitrate: 154 kb/s
    Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16, 151 kb/s
    Metadata:
      creation_time   : 1970-01-01 00:00:00
At least one output file must be specified

```

---

### Post by ron999 on 2011-03-22
> **FakeOutdoorsman said:**
> FFmpeg shows some additional differences:


Thanks.

OK
I've just ran the command again with some instructions to change the metadata.
```
ffmpeg -i foo.flac -acodec libfaac -ab 152k [COLOR="Red"]-metadata major_brand="mp42" -metadata minor_version="0" -metadata Title="whatever" -metadata encoder="FAAC 1.26.1 (Aug 16 2008) UNSTABLE" -metadata compatible_brands="mp42isom"[/COLOR] test97.m4a
```
It's changed the Title OK, but ffmpeg has ignored the ones that matter.:(

Any ideas what to do next?:confused:

```
ron@ubuntu:~$ ffprobe test97.m4a
FFprobe version git-N-28456-g1c31b26, Copyright (c) 2007-2011 the FFmpeg developers
  built on Mar 15 2011 20:38:57 with gcc 4.4.1
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab --disable-encoder=vorbis
  libavutil    50. 39. 0 / 50. 39. 0
  libavcodec   52.114. 0 / 52.114. 0
  libavformat  52.103. 0 / 52.103. 0
  libavdevice  52.  3. 0 / 52.  3. 0
  libavfilter   1. 76. 0 /  1. 76. 0
  libswscale    0. 12. 0 /  0. 12. 0
  libpostproc  51.  2. 0 / 51.  2. 0
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'test97.m4a':
  Metadata:
    major_brand     : [COLOR="Red"]M4A[/COLOR] 
    minor_version   : [COLOR="Red"]512[/COLOR]
    compatible_brands: [COLOR="Red"]isomiso2[/COLOR]
    creation_time   : 1970-01-01 00:00:00
    title           : [COLOR="Red"]whatever[/COLOR]
    encoder         : [COLOR="Red"]Lavf52.103.0[/COLOR]
  Duration: 00:04:01.58, start: 0.000000, bitrate: 154 kb/s
    Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16, 151 kb/s
    Metadata:
      creation_time   : 1970-01-01 00:00:00


```

---

### Post by FakeOutdoorsman on 2011-03-23
> **ron999 said:**
> Any ideas what to do next?:confused:

Not any good ideas. Maybe the iPod would work with a different output format? Perhaps you could try .aac or .mp4 instead of .m4a. You could also investigate the *-atag* option, but I'm not very familiar with that or if it would be useful at all.

---

### Post by ron999 on 2011-03-23
> **FakeOutdoorsman said:**
> ... Maybe the iPod would work with a different output format? Perhaps you could try .aac or .mp4 instead of .m4a. You could also investigate the *-atag* option,..

Hi
I've tried those other two formats.
gtkpod won't let me load aac (unrecognized format).
And the file in mp4 format still won't play when encoded with libfaac.

The atag option is in the ffmpeg documentation, but there's not much information so I don't know which atag formats to try.

In the meantime...
I've found that if I load the non-playing file into EasyTAG-aac v.2.1.5 then change one or more of the fields (any of them) such as changing the filename etc, then SAVE changes and exit. Then the file will load and play OK on the iPod. **Go figure!**;)


EasyTAG puts in some meta information, not just for the changed field.
I've tried messing with AtomicParsley to do the same as EasyTAG does.
I can set them just the same, but it still won't play.

So it looks like EasyTAG is doing something magical to the metadata/atoms - but I don't know what it is.:(
Perhaps ffmpeg/libfaac create the metadata differently that's unfriendly with this particular model of iPod.

This is the MediaInfo from test2.m4a when I've renamed it test3.m4a using EasyTAG.
Notice all the extra fields, though all I did was change the filename and save and exit.

```
Complete name                    : test3.m4a
Format                           : MPEG-4
Format profile                   : Apple audio with iTunes info
Codec ID                         : M4A 
File size                        : 4.46 MiB
Duration                         : 4mn 1s
Overall bit rate                 : 155 Kbps
[COLOR="Red"]Part/Position                    : 0
Part/Total                       : 0
Track name/Position              : 0
Track name/Total                 : 0
Tagged date                      : UTC 2011-03-23 20:45:18[/COLOR]
Writing application              : Lavf52.103.0
[COLOR="Red"]Cover                            : Yes
[/COLOR]
Audio
ID                               : 1
Format                           : AAC
Format/Info                      : Advanced Audio Codec
Format profile                   : LC
Codec ID                         : 40
Duration                         : 4mn 1s
Bit rate mode                    : Variable
Bit rate                         : 152 Kbps
Maximum bit rate                 : 204 Kbps
Channel(s)                       : 2 channels
Channel positions                : Front: L R
Sampling rate                    : 44.1 KHz
Compression mode                 : Lossy
Stream size                      : 4.38 MiB (98%)

```
And ffprobe:-

```
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'test3.m4a':
  Metadata:
    major_brand     : M4A 
    minor_version   : 512
    compatible_brands: isomiso2
    creation_time   : 1970-01-01 00:00:00
    encoder         : Lavf52.103.0
    [COLOR="Red"]title           : 
    artist          : 
    album           : 
    date            : 
    track           : 0
    genre           : 
    comment         : 
    composer        : [/COLOR]
  Duration: 00:04:01.58, start: 0.000000, bitrate: 154 kb/s
    Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16, 151 kb/s
    Metadata:
      creation_time   : 1970-01-01 00:00:00

```

---

### Post by ron999 on 2011-03-30
Hi
This problem's been fixed in FFmpeg git.:D
Information is here:-
[http://git.videolan.org/?p=ffmpeg.git;a=commit;h=93dfda88968c5e4d3f596f35a446fb7c238e96b2]("http://git.videolan.org/?p=ffmpeg.git;a=commit;h=93dfda88968c5e4d3f596f35a446fb7c238e96b2")

Solution is:-
Compile FFmpeg from git.
Instructions are here:- [http://ubuntuforums.org/showthread.php?t=786095&highlight=Upgrading+FFmpeg+x264]("http://ubuntuforums.org/showthread.php?t=786095&highlight=Upgrading+FFmpeg+x264")

---

### Post by FakeOutdoorsman on 2011-03-30
Good job at bringing this to the attention of FFmpeg and getting it fixed.

---

