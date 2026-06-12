---
title: "convert jpg to mpg with ffmpeg"
date: 2008-10-02
forum: Multimedia Software
---

### Post by hendoc on 2008-10-02
I have a directory with image files named 1.jpg thru 18.jpg. I have tried to convert them to mpg(any video format would do) using a tutorial I found with Google.  

 
Turn X images to a video sequence

ffmpeg -f image2 -i image%d.jpg video.mpg

This command will transform all the images from the current directory (named image1.jpg, image2.jpg, etc…) to a video file named video.mpg.

I get the following error message:

hendoc@Axena:~$ cd image2
hendoc@Axena:~/image2$ ffmpeg -f 1.jpg -i 18.jpg vid.mpg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Unknown input or output format: 1.jpg
hendoc@Axena:~/image2$ 

I am missing something basic. Any ideas?

---

### Post by FakeOutdoorsman on 2008-10-03
You're running the command incorrectly.  Navigate to the folder containing the images and try:
```
ffmpeg -f image2 -i %d.jpg video.mpg
```

---

### Post by hendoc on 2008-10-03
That's progress, FakeOutdoorsman. It created an mpg, but it plays at hyperspeed. I Believe I will be be able to change the speed myself. In any event, Your reply is greatly appreciated. The tutorial I have is much clearer on bitrates, etc. Thanks again for your time.

---

### Post by mister_p_1998 on 2012-05-09
I've got an mp3 I've converted to an mpg to post on Youtube, how do I get it to display one jpg image all the way through the track? (Its audio only at the moment)

---

### Post by FakeOutdoorsman on 2012-05-11
You didn't specify your Ubuntu version, so I will give you current FFmpeg syntax:
```
ffmpeg -r 1 -loop 1 -i input.jpg -i input.mp3 -shortest -c:v libx264 -preset veryslow -tune stillimage -crf 18 -c:a copy output.mkv
```
Older ffmpeg or the version from the repository will probably use:
```
ffmpeg -r 1 -loop_input -i input.jpg -i input.mp3 -shortest -vcodec libx264 -preset veryslow -crf 18 -acodec copy output.mkv
```
Even older syntax:
```
ffmpeg -r 1 -loop_input -i input.jpg -i input.mp3 -shortest -vcodec libx264 -vpre veryslow -crf 18 -acodec copy output.mkv
```

---

