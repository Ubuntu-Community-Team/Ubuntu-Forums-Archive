---
title: "How to create an avi with two languages starting from two avi in a different language"
date: 2011-06-21
forum: Multimedia Software
---

### Post by tanoloco on 2011-06-21
Hello,

let's say I've got one .avi video with a film with its original audio language (e.g. english) and another one .avi video with the same film but with a second audio language (e.g. re-dubbed in italian).
Is it possible to get only one .avi video with the film and the two audio languages selectable?

Thanks!

---

### Post by FakeOutdoorsman on 2011-06-21
This FFmpeg command should work for you:
```
$ ffmpeg -i input -vcodec copy -acodec copy output.mkv -newaudio -i input2 -acodec copy
```

---

### Post by tanoloco on 2011-06-22
Thank you!

This works like a charm! and very quick too!

Only one more problem now, maybe you can help:
the second audio added in this manner is not correctly synchronized with the audio, maybe because the two files differ by a small amount of size.

Is there a way to add the second audio with a delay (or in advance just in case)?

Thank you for your help, really appreciated!

---

### Post by tanoloco on 2011-06-22
I've found the answer by myself!

[http://howto-pages.org/ffmpeg/#delay]("http://howto-pages.org/ffmpeg/#delay")

Thanks again for your help!

---

### Post by tanoloco on 2011-06-22
... mmm ...

I think I need some more help! I can't figure out how to sync them.
I spent the whole day over that without luck.

first avi:
```
ffmpeg -i arg.avi
```
> 
ffmpeg version N-30954-gb6bde8c, Copyright (c) 2000-2011 the FFmpeg developers
  built on Jun 22 2011 21:28:48 with gcc 4.4.5
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil    51.  9. 1 / 51.  9. 1
  libavcodec   53.  7. 0 / 53.  7. 0
  libavformat  53.  4. 0 / 53.  4. 0
  libavdevice  53.  1. 1 / 53.  1. 1
  libavfilter   2. 23. 0 /  2. 23. 0
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  51.  2. 0 / 51.  2. 0
[mpeg4 @ 0x95f21e0] Invalid and inefficient vfw-avi packed B frames detected

Seems stream 0 codec frame rate differs from container frame rate: 30000.00 (30000/1) -> 25.00 (25/1)
Input #0, avi, from 'arg.avi':
  Duration: 01:50:22.80, start: 0.000000, bitrate: 883 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 512x256 [PAR 1:1 DAR 2:1], 25 fps, 25 tbr, 25 tbn, 30k tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 128 kb/s
At least one output file must be specified



Here is the second one:
```
ffmpeg -i ita.avi
```
> 
ffmpeg version N-30954-gb6bde8c, Copyright (c) 2000-2011 the FFmpeg developers
  built on Jun 22 2011 21:28:48 with gcc 4.4.5
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil    51.  9. 1 / 51.  9. 1
  libavcodec   53.  7. 0 / 53.  7. 0
  libavformat  53.  4. 0 / 53.  4. 0
  libavdevice  53.  1. 1 / 53.  1. 1
  libavfilter   2. 23. 0 /  2. 23. 0
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  51.  2. 0 / 51.  2. 0
[mp3 @ 0xa8c0340] Header missing

Seems stream 0 codec frame rate differs from container frame rate: 30000.00 (30000/1) -> 25.00 (25/1)
Input #0, avi, from 'ita.avi':
  Duration: 01:50:17.56, start: 0.000000, bitrate: 905 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 560x304 [PAR 1:1 DAR 35:19], 25 fps, 25 tbr, 25 tbn, 30k tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 128 kb/s
At least one output file must be specified


As ita.avi is bigger, I want to use ita.avi as video, arg.avi ad first audio and ita.avi as second audio.
I used this command:
```
ffmpeg -i arg.avi -i ita.avi -vcodec copy -acodec copy -map 1:0 -map 0:1 output.avi -acodec libmp3lame -ab 128k -map 1:1 -newaudio

```

The result is:
```
ffmpeg -i output.avi
```
> ffmpeg version N-30954-gb6bde8c, Copyright (c) 2000-2011 the FFmpeg developers
  built on Jun 22 2011 21:28:48 with gcc 4.4.5
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil    51.  9. 1 / 51.  9. 1
  libavcodec   53.  7. 0 / 53.  7. 0
  libavformat  53.  4. 0 / 53.  4. 0
  libavdevice  53.  1. 1 / 53.  1. 1
  libavfilter   2. 23. 0 /  2. 23. 0
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  51.  2. 0 / 51.  2. 0

Seems stream 0 codec frame rate differs from container frame rate: 30000.00 (30000/1) -> 25.00 (25/1)
Input #0, avi, from 'output.avi':
  Metadata:
    encoder         : Lavf53.4.0
  Duration: 01:50:22.80, start: 0.000000, bitrate: 1044 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 560x304 [PAR 1:1 DAR 35:19], 25 fps, 25 tbr, 25 tbn, 30k tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 128 kb/s
    Stream #0.2: Audio: mp3, 48000 Hz, stereo, s16, 128 kb/s
At least one output file must be specified

Video is ok.
First audio is late.
Second audio is right (it seems in sync)

I tried to use the option -itsoffset in many points of the command but without luck.

If I remember well I tried for example between many
```
ffmpeg **-itsoffset** 00:00:10.5 -i arg.avi -i ita.avi -vcodec copy -acodec copy -map 1:0 -map 0:1 output.avi -acodec libmp3lame -ab 128k -map 1:1 -newaudio

```
and everything goes out of sync

```
ffmpeg -i arg.avi **-itsoffset** 00:00:10.5 -i ita.avi -vcodec copy -acodec copy -map 1:0 -map 0:1 output.avi -acodec libmp3lame -ab 128k -map 1:1 -newaudio

```
no changes! It seems it doesn't work!

I tried negatives without luck.

Anyone can help me?

---

### Post by gordintoronto on 2011-06-22
Does this work: switch the videos and specify a delay for the English?

---

### Post by tanoloco on 2011-06-23
Hello!

Thank you for your suggestion. I'm sure I tried it with no success.
Anyhow I did the trick !!!!

:P

I solved using the option -async 1
So the final working code for me is:
```
ffmpeg -i input_eng.avi -itsoffset 00:00:1.4 -i input_ita.avi -async 1 -vcodec copy -acodec copy -map 1:0 -map 0:1 output.avi -async 1 -acodec libmp3lame -ab 128k -map 1:1 -newaudio

```

It's important to note that, according to the documentation
[http://www.ffmpeg.org/ffmpeg-doc.html#SEC8]("http://www.ffmpeg.org/ffmpeg-doc.html#SEC8")
all the parameters for the second audio must be specified *before* the -newaudio option .. so you have to repeat also the -async 1 parameter, otherwise also the second audio will be out of sync ignoring the -itsoffset parameter.

I suppose one has to repeat all the needed parameters (and so -async 1) for any eventual further audio track.


Now, I will put the tag *solved* to the thread but I have one more follow-up question:
is it possible to add a human readable name for the audio tracks?
for example
Audio Track 1 -> "Chinese (ac3)"
Audio Track 2 -> "Arab (mp3 128)"

Thanks for any suggestion!

---

### Post by FakeOutdoorsman on 2011-06-23
Perhaps the **-alang** option will do this:
```
-alang eng
```

---

### Post by tanoloco on 2011-06-27
no way for me to make it work, but it doesn't really matter for me because I want to create avi with only two languages.
However many thanks to FakeOutdoorsman for having pointed me to the right path! :) And of course thanks to all for your help!

That's enough for me.

---

