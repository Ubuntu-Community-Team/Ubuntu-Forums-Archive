---
title: "record sound clip from movie"
date: 2008-01-11
forum: Multimedia Production
---

### Post by rkakkar on 2008-01-11
i want to record an audio clip from a movie which i run in VLC media player. how can i do so?

---

### Post by Creative2 on 2008-01-11
...why ? 
you can extract audio with ffmpeg ....
try to do this :

```
ffmpeg -i INPUT  -vn -acodec mp3 -ab 128k -y OUTPUT
```


of course you must have ffmpeg installed from MEDIBUNTU REPO.....

try to see this , it can extract audio from movie and many other stuff 


[http://ubuntuforums.org/showthread.php?t=652843](http://ubuntuforums.org/showthread.php?t=652843)

cheers Creative2

---

### Post by rkakkar on 2008-01-11
> **Creative2 said:**
> ...why ? 
you can extract audio with ffmpeg ....
try to do this :

```
ffmpeg -i INPUT  -vn -acodec mp3 -ab 128k -y OUTPUT
```


of course you must have ffmpeg installed from MEDIBUNTU REPO.....

try to see this , it can extract audio from movie and many other stuff 


[http://ubuntuforums.org/showthread.php?t=652843](http://ubuntuforums.org/showthread.php?t=652843)

cheers Creative2

```
$ ffmpeg -i Beer\ League.avi -vn -acodec mp3                                                               -ab 128k -y clip.mp3
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --                                                              enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1                                                              394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jun  3 2007 20:59:25, gcc: 4.1.3 20070528 (prerelease) (Ubuntu 4.1.2-                                                              9ubuntu2)

Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/                                                              2733) -> 23.98 (2997/125)
Input #0, avi, from 'Beer League.avi':
  Duration: 01:26:43.2, start: 0.000000, bitrate: 1130 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 592x320, 23.98 fps(r)
  Stream #0.1: Audio: 0x2000, 48000 Hz, 5:1, 384 kb/s
Output #0, mp2, to 'clip.mp3':
  Stream #0.0: Audio: 0x0000, 48000 Hz, 5:1, 128 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
**Unsupported codec for output stream #0.0**
```

---

### Post by Creative2 on 2008-01-14
multiple errors:

1  your command line is not righ

$ ffmpeg -i Beer\ League.avi -vn -acodec mp3   

```
ffmpeg -i INPUT.AVI -vn -acodec mp3 OUTPUT.MP3
```

2 your ffmpeg is not right.....(you have ffmpeg free so it cannot support every formats like mp3)

[I]1RE- install ffmpeg after you have turned on  medibuntu repo..
see here[/I]

[https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f)

2 after you will be able to use it correctly

---

### Post by fiddledd on 2008-01-14
The easy way to do it, especially if you only want a section of the audio is to use avidemux. You can get the latest version from here:

[http://www.getdeb.net/](http://www.getdeb.net/)

---

### Post by eye208 on 2008-01-14
Why use FFMPEG, Avidemux etc. if it can be done right from within VLC?

Select "Open File" from the "File" menu, choose your movie file, then mark the "Stream/Save" checkbox below, click the "Properties" button, mark the "File" checkbox, chose a filename (e.g. "audio.wav"), choose "WAV" output format and "s16l" audio codec. Confirm by clicking "OK". Instead of playing back the movie, VLC will now extract the audio.

And if you really want to use the command line, there is no need to add the Medibuntu repository. Just use MEncoder like this:

mencoder INPUT.avi -ovc raw -oac mp3lame -of rawaudio -o OUTPUT.mp3

---

### Post by misplaced_ice on 2008-06-18
eye208 - I did a google search to find out how to do this and stumbled across this thread - Yay!
Really useful and brilliant and easy :) :)

---

