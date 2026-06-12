---
title: "Covert video file to .asf file type?"
date: 2011-01-24
forum: Multimedia Software
---

### Post by rapattack1 on 2011-01-24
Hi I want to be able to play a video file on my pda(Tungsten T5) but from memory the only video file i have seen playable on it was the asf file that is used when it starts up/reboots. I tried other file types in the past that were suggested in maybe a manual or forum or something but they never worked/played. I think it is because of the player installed and i tried installing another player but from memory that didn't install properly or just did not play anything. So if anyone knows of a way to convert files maybe using winff or mencoder i would love that info. I have been googling and have found nothing specific to what i am asking. I do not see anything in winff to convert to asf and cannot remember ever using mencoder.

---

### Post by shantiq on 2011-01-24
ok Rappatack winff is a frontend for ffmpeg  but it does not use all of the options ffmpeg has so to the command-line...



open your terminal and use ffmpeg
   


```
ffmpeg -i filename.mp4   filemame.asf
```


of course change mp4 for the type of file you start from


now you can add refinements for video bitrate and audio bitrate
change numbers to suit you

```
ffmpeg -i filename.mp4  -b 400k   -ab 128k filemame.asf
```



and if you want to do the same in **bulk**



cd to your files then enter


```
for f in *.mp4; do ffmpeg -i "$f" -b 400k -ab 98k "${f%.mp4}.asf"; done
```

again here change mp4 for your original file extension  and adjust video and audio bitrate to suit your needs



Hope this helps

---

### Post by rapattack1 on 2011-01-24
Thanks it seems the filesize is too large for the pda so will try some more tweeking when i have had some sleep! Thanks!!!

---

### Post by shantiq on 2011-01-24
to split you can use


> ffmpeg -i nameoffile.asf   -ss 00:00:00 -t 01:00:00 -vcodec copy -acodec copy  segment1.asf  && ffmpeg -i  nameoffile.asf   -ss 01:00:00  -t 01:10:00 -vcodec copy   -acodec copy  segment2.asf


-ss Hours.Minutes.Seconds  time when you start first cut
-t   length of first section in Hours.Minutes.Seconds




i did a split there of one hour then one hour and 10 on a 2h10 video



that should sort it :KS

---

### Post by FakeOutdoorsman on 2011-01-24
> **shantiq said:**
> to split you can use

```
ffmpeg -i nameoffile.asf -ss 00:00:00 -t 01:00:00 -sameq -ab 96k segment1.asf && ffmpeg -i nameoffile.asf -ss 01:00:00 -t 01:10:00 -sameq -ab 96k segment2.asf 
```


**-sameq** means "same quantizer" which does not necessarily mean "same quality". It's a confusing and poorly documented option which isn't generally recommended.

If you're simply splitting a file, then try **-vcodec copy** and **-acodec copy** instead. These will "copy and paste" the video and audio into a new file without the need to re-encode.

---

### Post by shantiq on 2011-01-24
thank you fakeO    works much better that way    and also WAY FASTER (takes about one minute to split a 2 hour film )  will amend original codeline :KS:KS

---

### Post by rapattack1 on 2011-01-24
OK haven't really had any sleep but here i am. Um i am not really understanding what to do next. The pda doesn't want to play the file and says it is 'either corrupt or the file size is too large'. Does the quality need to be reduced or is that why you suggested to split the file in two? I have to stream it as one file because of what it is. It is 10.8mb in size now and 1.13minutes long. It is a wmv that i made from a avi then i edited in Cinelerra as a dv because it needed some editing(i just did the flip edit).

---

### Post by FakeOutdoorsman on 2011-01-24
Do you have a video that does work with this device? You can investigate a working video with FFmpeg which will reveal more details:
```
ffmpeg -i input.asf
```

---

### Post by rapattack1 on 2011-01-24
```
carla@carla-desktop:~/Desktop$ ffmpeg -i TungstenT5.asf
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3

Seems stream 1 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 12.00 (12/1)
Input #0, asf, from 'TungstenT5.asf':
  Duration: 00:00:31.33, start: 3.000000, bitrate: 661 kb/s
    Stream #0.0: Audio: adpcm_ima_wav, 8000 Hz, stereo, s16, 32 kb/s
    Stream #0.1: Video: mpeg4, yuv420p, 320x480, 12 tbr, 1k tbn, 1k tbc
At least one output file must be specified
carla@carla-desktop:~/Desktop$ 

```
Hope i did this right

---

### Post by shantiq on 2011-01-25
> **rapattack1 said:**
> OK haven't really had any sleep but here i am. Um i am not really understanding what to do next. The pda doesn't want to play the file and says it is 'either corrupt or the file size is too large'. Does the quality need to be reduced or is that why you suggested to split the file in two? I have to stream it as one file because of what it is. It is 10.8mb in size now and 1.13minutes long. It is a wmv that i made from a avi then i edited in Cinelerra as a dv because it needed some editing(i just did the flip edit).

i only suggested cutting it in 2 as you said it gave you a message it might be too long    but clearly that is not the case here    1mn13 cannot be too long :KS:KS   we can rule that one out.


the size on the one you posted which works is 320x480      maybe give your new file that size too    see if that works  could be they all have to be that size on the PDA  


```
ffmpeg -i filename.mp4  -s 320x480  filemame.asf
```


Could you also post the info on the new asf file so it can be compared to the one you have that you know works

See how all the specs differ      Thanx

---

### Post by rapattack1 on 2011-01-25
Damn i got that same error:
Warning
Unable to display this video. It may be too large, corrupted or stored in an incompatible format.

---

