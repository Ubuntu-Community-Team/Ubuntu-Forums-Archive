---
title: "ffmpeg video to audio"
date: 2009-10-02
forum: Multimedia Software
---

### Post by mystmaiden on 2009-10-02
I've been trying to sort out ffmpeg but so far most of what I have read is either directed at doing something other than what I am attempting or is just plain way over my head. I have  ffmpeg installed. What I would like to do is convert a video file to an audio mpg file. Is that even possible? (and if anyone knows where I can find instructions point me there, pretty please?). I'm running Ubuntu 9.04

mystmaiden

---

### Post by FakeOutdoorsman on 2009-10-02
Show the output of:
```
ffmpeg -i input.mpg
```
Where *input.mpg* is the name of whatever video file you want to take the audio from.  This will output some useful information that will help in coming up with a good FFmpeg command.

---

### Post by mystmaiden on 2009-10-02
Thanks, quick question first though. Wouldn't I want to input the name of the .flv file I want to convert? And do I need to navigate to the file containing the flv first - seems like I read that somewhere but didn't know how to do it. 

mystmaiden

---

### Post by FakeOutdoorsman on 2009-10-02
> **mystmaiden said:**
> Thanks, quick question first though. Wouldn't I want to input the name of the .flv file I want to convert?
Yes.  For example, if I wanted to convert a file called pantaloons.flv, I would enter:
```
ffmpeg -i pantaloons.flv
```
> And do I need to navigate to the file containing the flv first - seems like I read that somewhere but didn't know how to do it. 

mystmaiden
Yes, you would either navigate to the location of the file, or you could include the path to the file in your command.  My file is located in the Desktop directory of my home folder.  Then I open a terminal I would first navigate to the Desktop directory:
```
cd Desktop
```
Then run FFmpeg:
```
ffmpeg -i pantaloons.flv
```
Or I could tell FFmpeg where my file is in the command:
```
ffmpeg -i ~/Desktop/pantaloons.flv
```
The **~/** is a shortcut which represents my home directory.

---

### Post by mystmaiden on 2009-10-05
Thanks Outdoorsman, this is the result I got (just changed the file name to pantaloons cause I got a giggle out of it :) 


```
mystmaiden@hal:~/Desktop$ ffmpeg -i pantaloons.flv
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:18:41, gcc: 4.3.3

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 29.97 (30000/1001)
Input #0, flv, from 'pantaloons.flv':
  Duration: 00:03:54.93, start: 0.000000, bitrate: 164 kb/s
    Stream #0.0: Video: flv, yuv420p, 320x240, 100 kb/s, 29.97 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, mono, s16, 64 kb/s
At least one output file must be specified
mystmaiden@hal:~/Desktop$ 
```

sorry I was so slow to reply, life is getting in the way of my computing!

---

### Post by FakeOutdoorsman on 2009-10-05
> **mystmaiden said:**
> Thanks Outdoorsman, this is the result I got (just changed the file name to pantaloons cause I got a giggle out of it :) 


```
mystmaiden@hal:~/Desktop$
Input #0, flv, from 'pantaloons.flv':
  Duration: 00:03:54.93, start: 0.000000, bitrate: 164 kb/s
    Stream #0.0: Video: flv, yuv420p, 320x240, 100 kb/s, 29.97 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, mono, s16, 64 kb/s

```

sorry I was so slow to reply, life is getting in the way of my computing!

The output shows that the audio in pantaloons.flv is in mp3 format.  You have two choices here: just copy the audio directly, or re-encode it to another format.  If you don't mind the audio format that your input file already is, then the best choice is copying because it doesn't lower the quality through re-encoding to another (possibly lossy) format:
```
ffmpeg -i pantaloons.flv -acodec copy output.mp3
```

---

### Post by SuperSonic4 on 2009-10-05
> **FakeOutdoorsman said:**
> The output shows that the audio in pantaloons.flv is in mp3 format.  You have two choices here: just copy the audio directly, or re-encode it to another format.  If you don't mind the audio format that your input file already is, then the best choice is copying because it doesn't lower the quality through re-encoding to another (possibly lossy) format:
```
ffmpeg -i pantaloons.flv -acodec copy output.mp3
```

I always thought you had to pass the -nv flag 

```
ffmpeg -i epic_song.flv -vn -acodec copy output.mp3
```

edit: wow, you don't need it, although it wouldn't recognise the -ab 128k flag on my audio lol

---

### Post by FakeOutdoorsman on 2009-10-05
> **SuperSonic4 said:**
> I always thought you had to pass the -nv flag 

```
ffmpeg -i epic_song.flv -vn -acodec copy output.mp3
```

edit: wow, you don't need it, although it wouldn't recognise the -ab 128k flag on my audio lol

You need the *-vn* option to ignore the video if your output file can contain both audio and video such as mp4.  The *-ab* (audio bitrate) option is not compatible with the *-acodec copy* option (copy the audio directly) because that would require re-encoding.  The *-acodec copy* option is similar to copying and pasting text from one txt file to another.  You're just copying it directly from one [container format](http://en.wikipedia.org/wiki/Container_format_%28digital%29) to another.

---

### Post by SuperSonic4 on 2009-10-05
> **FakeOutdoorsman said:**
> You need the *-vn* option to ignore the video if your output file can contain both audio and video such as mp4.  The *-ab* (audio bitrate) option is not compatible with the *-acodec copy* option (copy the audio directly) because that would require re-encoding.  The *-acodec copy* option is similar to copying and pasting text from one txt file to another.  You're just copying it directly from one [container format](http://en.wikipedia.org/wiki/Container_format_%28digital%29) to another.

I converted mine to m4a with libfaac though. Ah well, it's not important :)

---

### Post by mystmaiden on 2009-10-05
Thanks so much, Outdoorsman, that worked perfectly. Yay!

myst

---

### Post by suitedaces on 2009-10-09
Just stumbled across this, this is brilliant!!

---

