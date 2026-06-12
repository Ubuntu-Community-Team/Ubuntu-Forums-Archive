---
title: "How can I extract the meta tags from an audio file?"
date: 2011-03-16
forum: Multimedia Software
---

### Post by ron999 on 2011-03-16
Hi
If I convert an audio file to a different format (such as mp3) using a pipe I lose the tags.:(
```
ffmpeg -i <filename> -f wav - | lame - output.mp3
```
If I knew the tags of the input file I could put them back using a program such as id3v2 like this:-
```
id3v2 -t Something -a "The Beatles" -A "Abbey Road" output.mp3
```

> Complete name                    : output.mp3
Format                           : MPEG Audio
File size                        : 2.78 MiB
Duration                         : 3mn 2s
Overall bit rate                 : 128 Kbps
Album                            : Abbey Road
Track name                       : Something
Performer                        : The Beatles
Writing library                  : LAME3.98r


But how can I capture the tags from the input file? :confused:
Is there a method that would give me the tags of an input file like this:- $title $artist $Album

---

### Post by FakeOutdoorsman on 2011-03-16
The easiest method would be to use a recent FFmpeg and not pipe it. FFmpeg now attempts to transfer all metadata:
```
$ ffmpeg -i 2007_6744_1_A.mp4 -aq 4 out.mp3
...
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '2007_6744_1_A.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 512
    compatible_brands: isomiso2avc1mp41
    creation_time   : 2011-03-16 02:50:00
    title           : transect 1, camera A
    artist          : ADF
    date            : 2007
    encoder         : Lavf52.103.0
    comment         : Alpha
  Duration: 00:36:47.43, start: 0.000000, bitrate: 677 kb/s
    Chapter #0.0: start 0.146000, end 2207.438567
    Metadata:
      title           : 
    Stream #0.0(und): Video: h264 (High), yuv420p, 720x480 [PAR 8:9 DAR 4:3], 615 kb/s, 29.97 fps, 29.97 tbr, 30k tbn, 59.94 tbc
    Metadata:
      creation_time   : 2011-03-16 02:50:00
    Stream #0.1(und): Audio: aac, 32000 Hz, stereo, s16, 57 kb/s
    Metadata:
      creation_time   : 2011-03-16 02:50:00
Output #0, mp3, to 'out.mp3':
  Metadata:
    major_brand     : isom
    minor_version   : 512
    compatible_brands: isomiso2avc1mp41
    TDEN            : 2011-03-16 02:50:00
    TIT2            : transect 1, camera A
    TPE1            : ADF
    TDRL            : 2007
    comment         : Alpha
    TSSE            : Lavf52.103.0
```

---

### Post by ron999 on 2011-03-16
> **FakeOutdoorsman said:**
> The easiest method would be to use a recent FFmpeg and not pipe it.
    
Yes, but I want to pipe ffmpeg into an oddball encoder.
I only used lame as an example in my post above.

---

### Post by andrew.46 on 2011-03-17
> **ron999 said:**
> Yes, but I want to pipe ffmpeg into an oddball encoder.

Which encoder? Depending on how your encoder places the tags it would be fairly straightforward to script stripping and replacement of the tags.

---

### Post by ron999 on 2011-03-17
> **andrew.46 said:**
> ...it would be fairly straightforward to script stripping ... of the tags.
Hi andrew
How would I script stripping of tags such as Track Name, Performer and Album from an audio file?

---

### Post by andrew.46 on 2011-03-17
> **ron999 said:**
> How would I script stripping of tags such as Track Name, Performer and Album from an audio file?

I used to trim some big ogg music files and copy across the meta tags in the following manner:

```

ffmpeg -i input.ogg \
       -ss 00:07:19 -t 02:00:03 \
       -acodec copy \
       **[COLOR="Red"]-metadata title[/COLOR]**="$(vorbiscomment --list \
       finput.ogg | grep 'title' | cut -d '=' -f 2)" \
       **[COLOR="Red"]-metadata artist[/COLOR]**="$(vorbiscomment --list \
       input.ogg | grep 'artist' | cut -d '=' -f 2)" \
       **[COLOR="Red"]-metadata album=[/COLOR]**"$(vorbiscomment --list \
       input.ogg | grep 'album' | cut -d '=' -f 2)" \
       output.ogg

```

when the FFmpeg meta tag remapping option was a bit of a hit and miss affair. This example uses vorbiscomment to extract the meta tags, grep and cut to trim them a little and finally the result is wrapped in a variable. It is not very polished as it is for my own personal use but it shows the way perhaps :).

Andrew

---

### Post by ron999 on 2011-03-17
Hi
When I use command:-
```
ffprobe -show_format Something.mp3
```

It gives result:-

> ron@ubuntu:~$ ffprobe -show_format Something.mp3
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
[mp3 @ 0x8eecfc0] max_analyze_duration reached
Input #0, mp3, from 'Something.mp3':
  Metadata:
    title           : Something
    artist          : The Beatles
    album           : Abbey Road
    genre           : Rock/Classic Rock/Pop
    copyright       : © EMI Records Ltd
    track           : 2
    disc            : 1/1
  Duration: 00:03:02.30, start: 0.000000, bitrate: 122 kb/s
    Stream #0.0: Audio: mp3, 44100 Hz, stereo, s16, 119 kb/s
[FORMAT]
filename=Something.mp3
nb_streams=1
format_name=mp3
format_long_name=MPEG audio layer 2/3
start_time=0.000000 
duration=182.308571 
size=2785000.000000 
bit_rate=122210.000000 
[COLOR="Red"]TAG:title=Something[/COLOR]
[COLOR="Red"]TAG:artist=The Beatles[/COLOR]
[COLOR="Red"]TAG:album=Abbey Road[/COLOR]
TAG:genre=Rock/Classic Rock/Pop
TAG:copyright=© EMI Records Ltd
TAG:track=2
TAG:disc=1/1
[/FORMAT]

Is there a way that I could extract this information to get such as this:- $title $artist $album

---

### Post by ron999 on 2011-03-17
Ok, I can extract that information with ffprobe.:)
Maybe it will tidy up a bit.:rolleyes:

This is my test:-

```
file=Something.mp3 && \
title=`ffprobe 2> /dev/null -show_format $file | grep TAG:title= | cut -d '=' -f 2` && \
artist=`ffprobe 2> /dev/null -show_format $file | grep TAG:artist= | cut -d '=' -f 2` && \
album=`ffprobe 2> /dev/null -show_format $file | grep TAG:album= | cut -d '=' -f 2` && \
echo && \
echo $title  && \
echo $artist  && \
echo $album
```


This is the result:-

> ron@ubuntu:~$ file=Something.mp3 && \
> title=`ffprobe 2> /dev/null -show_format $file | grep TAG:title= | cut -d '=' -f 2` && \
> artist=`ffprobe 2> /dev/null -show_format $file | grep TAG:artist= | cut -d '=' -f 2` && \
> album=`ffprobe 2> /dev/null -show_format $file | grep TAG:album= | cut -d '=' -f 2` && \
> echo && \
> echo $title  && \
> echo $artist  && \
> echo $album

Something
The Beatles
Abbey Road
ron@ubuntu:~$ 

:P

---

