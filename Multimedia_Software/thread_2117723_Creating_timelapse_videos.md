---
title: "Creating timelapse videos"
date: 2013-02-19
forum: Multimedia Software
---

### Post by xxlray on 2013-02-19
I shot a  set of 400 photos in 1929x1080 each 131.5kB big and I want to combine them to a timelapse video. Unfortunately the movie does not play and its filesize is less than 1MB. Any idea how I can put the images together?

So far I tried the following commands:
```
ffmpeg -f image2 -i Pic*.jpg -sameq movie.mpg
```
```
ffmpeg -r 20 -i Pic*.jpg -sameq -s hd1080 -vcodec libx264 -crf 25 movie.mp4
```
```
ffmpeg -i Pic*.jpg movie.mpeg
```
I furthermore tried mencoder but this gives me an error message I could not resolve:
```
mencoder -nosound -ovc lavc -lavcopts vcodec=mpeg4 -o movie.avi -mf type=jpeg:fps=20 Pic_*
MEncoder svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team
success: format: 0  data: 0x0 - 0x92a79
libavformat version 53.32.100 (external)
Mismatching header version 53.19.0
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

Exiting...
```

```
$ cat /etc/issue
Ubuntu 12.04.2 LTS \n \l

$ ffmpeg -version
ffmpeg version 0.10.6-6:0.10.6-0ubuntu0jon1~precise1
built on Nov 12 2012 13:11:38 with gcc 4.6.3
configuration: --arch=amd64 --enable-pthreads --enable-runtime-cpudetect --extra-version='6:0.10.6-0ubuntu0jon1~precise1' --libdir=/usr/lib/x86_64-linux-gnu --disable-stripping --prefix=/usr --enable-bzlib --enable-libdc1394 --enable-libfreetype --enable-frei0r --enable-gnutls --enable-libgsm --enable-libmp3lame --enable-librtmp --enable-libopencv --enable-libopenjpeg --enable-libpulse --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-vaapi --enable-vdpau --enable-libvorbis --enable-libvpx --enable-zlib --enable-gpl --enable-postproc --enable-libcdio --enable-x11grab --enable-libx264 --shlibdir=/usr/lib/x86_64-linux-gnu --enable-shared --disable-static
libavutil      51. 35.100 / 51. 35.100
libavcodec     53. 61.100 / 53. 61.100
libavformat    53. 32.100 / 53. 32.100
libavdevice    53.  4.100 / 53.  4.100
libavfilter     2. 61.100 /  2. 61.100
libswscale      2.  1.100 /  2.  1.100
libswresample   0.  6.100 /  0.  6.100
libpostproc    52.  0.100 / 52.  0.100

$ mencoder
MEncoder svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team
```

---

### Post by xxlray on 2013-02-19
I just tried a new command:

```
mencoder "mf://*.jpg" -mf fps=20:type=jpg -ovc lavc -lavcopts vcodec=mpeg4:mbd=2:trell -oac copy -o movie.avi
```

It creates a 1MB video which is about ten seconds long (as expected) but only contains one single image.

---

### Post by xxlray on 2013-02-19
Next command which only produced a still:

```
cat *.jpg | ffmpeg -f image2pipe -r 20 -vcodec mjpeg -i - -vcodec libx264 movie.mp4
```

---

### Post by xxlray on 2013-02-19
Could the still be caused by the way I access the files? I saw lots of examples which use %03d instead of * . Anyway I have not success when I change it:
```
$ ffmpeg -f image2 -framerate 20 -i Pic%03d.jpg -s 1920x1080 movie.avi
...
Pic%03d.jpg: No such file or directory
```

I even tried the following which only produced a black video screen:
```
ffmpeg -f image2 -framerate 20 -i $(ls Pic*.jpg) -s 1920x1080 movie.avi
```

---

### Post by xxlray on 2013-02-19
The next two commands which did not work:

Crashes
```
$ convert *jpg movie.mpg
Killed
```

Produced still
```
mencoder mf://./\*.jpg -mf w=1920:h=1080:fps=20:type=jpg -ovc lavc -lavcopts vcodec=mpeg4 -oac copy -o movie.mp4
```

---

### Post by xxlray on 2013-02-19
OK - I fooled myself. I must have made a mistake when cropping the image files to 16_9. all input images are the same. This "might" explain why I only see a still in the final video...

---

### Post by xxlray on 2013-02-19
This command messed up the files (just did it again):
```
ffmpeg -f image2 -i Pic*.jpg -sameq movie.mpg
```
So happy I remembered to back them up.

---

### Post by xxlray on 2013-02-19
Just to complete this thread: I am now very happy using the following command:```
mencoder -nosound -ovc x264 -x264encopts preset=slow:tune=film:crf=20 -o movie.avi mf://*.jpg type=jpeg:fps=20:w=1920:h=1080
```

---

