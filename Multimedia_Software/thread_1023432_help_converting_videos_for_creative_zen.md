---
title: "help converting videos for creative zen"
date: 2008-12-27
forum: Multimedia Software
---

### Post by jacob01 on 2008-12-27
im trying to convert a video with ffmpeg to put on my 16 gb creative zen but am having a few problems with the player playing the video. 

the video i have that im trying to put on is avi and im trying to convert it to xvid which creative said was compatable [link]("http://us.creative.com/products/product.asp?category=213&subcategory=214&product=16999&nav=1")  but when i try and convert it i get errors

when i enter:  jacob@desktop:~/Videos/Pink Floyd The Wall$ ffmpeg -i pink\ floyd\ the\ wall.avi -f xvid  -b 1000 -s 320x240 Pink\ Floyd\ The\ Wall.xvid

i get this
```
jacob@desktop:~/Videos/Pink Floyd The Wall$ ffmpeg -i pink\ floyd\ the\ wall.avi -f xvid  -b 1000kb/s -s 320x240 Pink\ Floyd\ The\ Wall.xvid
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2

Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65534/2733) -> 23.98 (2997/125)
Input #0, avi, from 'pink floyd the wall.avi':
  Duration: 01:35:09.7, start: 0.000000, bitrate: 1029 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 640x272 [PAR 1:1 DAR 40:17], 23.98 tb(r)
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, 32 kb/s
Unknown input or output format: xvid


```

I have done the same set of commands except for replacing the output format with mpeg and that works fine but then i tried avi and that does not work i get the same error as above. Am i doing something wrong?

-jacob

---

### Post by FakeOutdoorsman on 2008-12-28
First you'll need to install the unstripped Ubuntu libraries to be able to use some restricted codecs:
```
sudo apt-get install libavcodec-unstripped-51
```
Here are several commands to try.  Using ffmpeg's native xvid encoder with aac audio in a mp4 container:
```
ffmpeg -i input.avi -vtag xvid -s 320x240 -b 384k -ab 96k output.mp4
```
Using libxvid with libmp3lame in an avi container:
```
ffmpeg -i input.avi -vcodec libxvid -acodec libmp3lame -s 320x240 -b 384k -ab 96k output.avi
```
Feel free to tweak the bitrates (-b and -ab).

---

