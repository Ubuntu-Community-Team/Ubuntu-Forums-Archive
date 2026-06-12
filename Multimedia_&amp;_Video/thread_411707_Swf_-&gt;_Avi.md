---
title: "Swf -&gt; Avi"
date: 2007-04-17
forum: Multimedia &amp; Video
---

### Post by nhandler on 2007-04-17
I need to find a way to convert a swf movie to avi in ubuntu feisty. So far, I haven't been able to find much info on how to do this. I've seen flv -> avi or movie -> swf, but not swf->avi. Any info would be greatly appreciated.

---

### Post by srhlefty on 2007-04-17
swf is Flash, which as far as I know means it is not rendered video in the way that avi is.  And it's not flash video either, as you point out.  What about a program like [xvidcap]("http://xvidcap.sourceforge.net/")?  This is pretty much a brute-force approach, but may do what you want.  I've used it to record games in emulators when no built-in movie capture was provided.

---

### Post by nhandler on 2007-04-20
> **Flantz said:**
> For converting swf to avi I use [Flash to Video Encoder PRO]("http://www.geovid.com/Flash_to_Video_Encoder_PRO/"). In this program I can convert as flv to avi as swf to avi too very easy and I haven't any problem with it.

That program looks to be windows only. I would prefer not using windows to accomplish this task. Is there an alternate linux program out there?

---

### Post by charly4711 on 2007-04-23
Have you actually tried ffmpeg? SWF CAN have video embedded.
Try: ffmpeg -i file.swf file.avi

---

### Post by nhandler on 2007-04-23
> **charly4711 said:**
> Have you actually tried ffmpeg? SWF CAN have video embedded.
Try: ffmpeg -i file.swf file.avi

> $ ffmpeg -i movie.swf movie.avi
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-mp3lame --enable-faadbin --enable-faad --enable-faac --enable-xvid --enable-x264 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Mar 21 2007 14:14:05, gcc: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
Input #0, swf, from 'movie.swf':
  Duration: N/A, bitrate: N/A
  Stream #0.0: Audio: mp3, 11025 Hz, mono
Output #0, avi, to 'movie.avi':
  Stream #0.0: Audio: mp2, 11025 Hz, mono, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
[mp2 @ 0xb7ec1f08]Sampling rate 11025 is not allowed in mp2
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height


That's the output of trying to convert swf to avi using ffmpeg.

---

### Post by ubu-for on 2007-04-23
> **charly4711 said:**
> Have you actually tried ffmpeg? SWF CAN have video embedded.
Try: ffmpeg -i file.swf file.avi

Works great with my .flv files!

But how can I maintain the quality?

THX!

---

### Post by nhandler on 2007-04-23
> **ubu-for said:**
> Works great with my .flv files!

But how can I maintain the quality?

THX!

It should work great with your file. .flv is supported by ffmpeg.

---

### Post by ubu-for on 2007-04-24
> **Cheater said:**
> It should work great with your file. .flv is supported by ffmpeg.

If the quality wouldn't decrease, I would convert them all and could use the time jump again.

---

### Post by charly4711 on 2007-04-24
swf is supported by ffmpeg, too ... for what that statement is worth.
The thing here is: What is the file type and what is the video stream contained therein. 
For the first post with the failure of the swf file, I remember, there is some issue with ffmpeg and decoding swf when there is both video and audio present ... for some reason ffmpeg only extracts the audio bit (as you can see).
As for maintaining quality, try the -sameq parameter

---

### Post by nhandler on 2007-04-24
So, could I somehow convert it twice? Once to get the audio and once to get the video. Then merge them.

---

### Post by charly4711 on 2007-04-25
Don't think it can be done with ffmpeg. If there is another app to get the video, you could get the audio with ffmpeg and put them together lateron. Other apps might be mencoder or transcode, though I think they only use other libraries as their backend and will probably use the libavcodec/-format libs provided with ffmpeg and therefore behave similarly.

---

### Post by pritty on 2008-05-14
Hi:)I prefer Flash to Video Encoder.It`s good prog convert swf to avi:)

---

### Post by videospot on 2008-05-22
I do not think ffmpeg can do swf file which only supports swf format video. I think you can use [magic swf2avi]("http://www.effectmatrix.com/swf2avi") with Wine.

---

