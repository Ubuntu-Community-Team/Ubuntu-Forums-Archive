---
title: "Recover AVI file"
date: 2012-03-08
forum: Multimedia Software
---

### Post by manolomanolo on 2012-03-08
Hi to all.

I generated an AVI file greater than 4GB with a desktop-recording tool on Windows. However, the avi file seems not to be working, I mean I am unable to play it.

What could the problem be?
How to solve it?

Thanks.
Regards

---

### Post by shantiq on 2012-03-10
hi there manolo


can you run   ```
ffmpeg -i yourfile.avi

```


and post results here




**or**



maybe cut five minutes

```
mencoder  -ss 00:00:00  -endpos 00:05:00 -oac copy -ovc copy yourfile.avi -o 5minutes.avi
```


then upload to say rapidshare.com or any free upload site


so we can try it and see:KS what might be problem for Ubuntu

---

### Post by manolomanolo on 2012-03-11
```
ffmpeg version 0.7.3-4:0.7.3-0ubuntu0.11.10.1, Copyright (c) 2000-2011 the Libav developers
  built on Jan  4 2012 16:21:50 with gcc 4.6.1
  configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  avutil      configuration: --extra-version='4:0.7.3ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avcodec     configuration: --extra-version='4:0.7.3ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avformat    configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avdevice    configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay                               
  avfilter    configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay                               
  swscale     configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay                               
  postproc    configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay                               
  libavutil    51.  7. 0 / 51.  7. 0                                                                                                                                               
  libavcodec   53.  6. 0 / 53.  6. 0                                                                                                                                               
  libavformat  53.  3. 0 / 53.  3. 0                                                                                                                                               
  libavdevice  53.  0. 0 / 53.  0. 0                                                                                                                                               
  libavfilter   2.  4. 0 /  2.  4. 0                                                                                                                                               
  libswscale    2.  0. 0 /  2.  0. 0                                                                                                                                               
  libpostproc  52.  0. 0 / 52.  0. 0                                                                                                                                               
Input #0, avi, from '20120208_1539_02.avi':                                                                                                                                        
  Duration: 01:23:16.62, start: 0.000000, bitrate: 6876 kb/s                                                                                                                       
    Stream #0.0: Video: rawvideo, bgr24, 1440x900, 200 tbr, 200 tbn, 200 tbc                                                                                                       
At least one output file must be specified                                                                                                                                         
```

---

### Post by shantiq on 2012-03-11
looks like it is raw video    [also not sure what bgr24 is]

> Stream #0.0: Video: **rawvideo**, **bgr24**, 1440x900, 200 tbr, 200 tbn, 200 tbc


reading around this is meant to work. maybe try this in terminal


```
ffplay -f rawvideo -s 1440x900  YOURFILE.avi
```

this too

> ffmpeg -f audio_device -i /dev/audio -s 1440x900 -f video4linux2 -i /dev/video0 YOURFILE.avi



there is also a player called vooya [**here**]("http://www.upubuntu.com/2012/02/vooya-video-player-for-playing.html") for raw video


**============================**

also **different tack** you could convert your huge file to a more manageable one and onw which would play in normal players


for this **ffmpeg or winff** the GUI version of ffmpeg if you want to avoid messing around with code
or **[handbrake]("http://pasindudps.blogspot.com/2011/11/install-handrake-in-ubuntu-1110-oneiric.html")**

---

### Post by manolomanolo on 2012-03-11
Other results:

> ffplay -f rawvideo -s 1440x900  20120208_1539_02.avi 
ffplay version 0.7.3-4:0.7.3-0ubuntu0.11.10.1, Copyright (c) 2003-2011 the Libav developers
  built on Jan  4 2012 16:21:50 with gcc 4.6.1
  configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  avutil      configuration: --extra-version='4:0.7.3ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avcodec     configuration: --extra-version='4:0.7.3ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avformat    configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avdevice    configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avfilter    configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  swscale     configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  postproc    configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil    51.  7. 0 / 51.  7. 0
  libavcodec   53.  6. 0 / 53.  6. 0
  libavformat  53.  3. 0 / 53.  3. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  4. 0 /  2.  4. 0
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  52.  0. 0 / 52.  0. 0
[IMGUTILS @ 0xb2cbcdb4] Picture size 0x0 is invalid
[IMGUTILS @ 0xb2cbcce4] Picture size 0x0 is invalid                                                                                                                                
[rawvideo @ 0x93f4920] Could not find codec parameters (Video: rawvideo, yuv420p)                                                                                                  
[rawvideo @ 0x93f4920] Estimating duration from bitrate, this may be inaccurate                                                                                                    
20120208_1539_02.avi: could not find codec parameters                                                                

---

### Post by manolomanolo on 2012-03-11
```
ffmpeg -f audio_device -i /dev/audio -s 1440x900 -f video4linux2 -i /dev/video0 20120208_1539_02.avi 
ffmpeg version 0.7.3-4:0.7.3-0ubuntu0.11.10.1, Copyright (c) 2000-2011 the Libav developers
  built on Jan  4 2012 16:21:50 with gcc 4.6.1
  configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  avutil      configuration: --extra-version='4:0.7.3ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avcodec     configuration: --extra-version='4:0.7.3ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avformat    configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avdevice    configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  avfilter    configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  swscale     configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  postproc    configuration: --extra-version='4:0.7.3-0ubuntu0.11.10.1' --arch=i386 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil    51.  7. 0 / 51.  7. 0
  libavcodec   53.  6. 0 / 53.  6. 0
  libavformat  53.  3. 0 / 53.  3. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  4. 0 /  2.  4. 0
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  52.  0. 0 / 52.  0. 0
**Unknown input format: 'audio_device'**

```

---

### Post by shantiq on 2012-03-12
so not picked up by ffplay or ffmpeg :(



maybe try  

 there is also a player called vooya [**here**]("http://www.upubuntu.com/2012/02/vooya-video-player-for-playing.html") for raw video


that should pick up raw

---

### Post by manolomanolo on 2012-03-12
Unfortunately, this is what I get when running vooya

[http://imageupload.org/getfile.php?id=198596&a=9bf61d4bf69ed943ca0e226889 b0bcbc&t=4f5dc47c&o=3525BBBC14108CC212B416026CBA45 2E6039EBBF1C5F8BDB0DB5795E32F159574A25BAA01410&n=s chermata1.png&i=1]("http://imageupload.org/getfile.php?id=198596&a=9bf61d4bf69ed943ca0e226889 b0bcbc&t=4f5dc47c&o=3525BBBC14108CC212B416026CBA45 2E6039EBBF1C5F8BDB0DB5795E32F159574A25BAA01410&n=s chermata1.png&i=1")

[IMG]http://imageupload.org/getfile.php?id=198596&a=9bf61d4bf69ed943ca0e226889 b0bcbc&t=4f5dc47c&o=3525BBBC14108CC212B416026CBA45 2E6039EBBF1C5F8BDB0DB5795E32F159574A25BAA01410&n=s chermata1.png&i=1[/IMG]

---

### Post by shantiq on 2012-03-12
------all my suggestions .  No more ideas   Someone else will come along :]]----------
which program does it play fine on Windows if you do not mind me asking

---

### Post by manolomanolo on 2012-03-12
Hope this image works
[IMG]http://postimage.org/image/6pjwpvqgb/[/IMG]

However, it does not work on Windows too with VLC.

---

### Post by manolomanolo on 2012-03-12
Here it is the image

[IMG]http://s17.postimage.org/9weg9iawd/schermata1.png[/IMG]

---

### Post by shantiq on 2012-03-12
manolo if you have created this file on Windows and it does not play on Windows why do you think that it will play on Ubuntu? :KS:KS  seems optimistic do you not think?

---

