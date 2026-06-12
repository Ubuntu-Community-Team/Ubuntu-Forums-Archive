---
title: "MEncoder fails to find file"
date: 2010-04-05
forum: Multimedia Software
---

### Post by mask13 on 2010-04-05
I have a video that is currently in .mkv format, and I need it in .avi, however, when I attempt to convert it with MEncoder, it cannot find the video. (Please note this is my first attempt to convert anything with MEncoder, or convert any video on Linux). What I entered and my results are as follows - 

mencoder Pocketful_Of_Rainbows.mkv -o Pocketful_Of_Rainbows.avi -ovc xvid -oac mp3lame
MEncoder SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
File not found: 'Pocketful_Of_Rainbows.mkv'
Failed to open Pocketful_Of_Rainbows.mkv.
Cannot open file/device.

Exiting...

Yes, I spelled the name of the video correctly, so what am I doing wrong. I've read [http://en.gentoo-wiki.com/wiki/HOWTO_Mencoder_Introduction_Guide](http://en.gentoo-wiki.com/wiki/HOWTO_Mencoder_Introduction_Guide) almost entirely and cannot find a solution. 

Please help, and thank you.

---

### Post by andrew.46 on 2010-04-05
Hi mask13,

If you are keen to use use commandline transcoding can I suggest that you would be better to use FFmpeg rather than MEncoder? Development of MEncoder is almost non-existent these days while FFmpeg development is flying ahead and FFmpeg syntax is much easier :). If I can convince you that this is a good idea follow the directions on this page:

 HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg 
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

and then interrogate your file as follows:
```

ffmpeg -i Pocketful_Of_Rainbows.mkv
```

If you post the results here I am sure that myself and others can assist in transcoding to the format you wish, perhaps mp4 rather than avi? BTW I suspect your MEncoder command is failing because you have not used the correct path to your file. If you are not sure of the path it can be seen by running:
```

find $HOME -name 'Pocketful_Of_Rainbows.mkv'
```

All the best,

Andrew

---

### Post by mask13 on 2010-04-06
Well, I found my problem with MEncoder. I didn't know I had to use the whole file path, I had the idea I only needed the name of the file. I got what I wanted done, but for the future knowledge, I believe I'll try ffmpeg. My results:

```
mask13@mask13-laptop:~$ ffmpeg -i /home/mask13/Desktop/Pocketful_Of_Rainbows.mkv 
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:15:16, gcc: 4.4.1

Seems stream 0 codec frame rate differs from container frame rate: 47.95 (48000/1001) -> 23.98 (24000/1001)
Input #0, matroska, from '/home/mask13/Desktop/Pocketful_Of_Rainbows.mkv':
  Duration: 01:55:32.30, start: 0.000000, bitrate: N/A
    Stream #0.0(jpn): Video: h264, yuv420p, 1280x720, PAR 1:1 DAR 16:9, 23.98 tbr, 1k tbn, 47.95 tbc
    Stream #0.1(jpn): Audio: dca, 48000 Hz, 5.1, s16
    Stream #0.2(eng): Subtitle: 0x0000
    Stream #0.3: Attachment: 0x0000
    Stream #0.4: Attachment: 0x0000
    Stream #0.5: Attachment: 0x0000
    Stream #0.6: Attachment: 0x0000
    Stream #0.7: Attachment: 0x0000
    Stream #0.8: Attachment: 0x0000
    Stream #0.9: Attachment: 0x0000
    Stream #0.10: Attachment: 0x0000
    Stream #0.11: Attachment: 0x0000
    Stream #0.12: Attachment: 0x0000
    Stream #0.13: Attachment: 0x0000
    Stream #0.14: Attachment: 0x0000
    Stream #0.15: Attachment: 0x0000
    Stream #0.16: Attachment: 0x0000
At least one output file must be specified
```

---

### Post by andrew.46 on 2010-04-06
Hi mask13,

You could of course simply change to the location of your file. I have not had much to do with mpeg4 / xvid encoding to an avi container so I would definitely take the following with a grain or 2 of salt but if you are keen to take FFmpeg for a run you could try try the following on your file:

```

ffmpeg -i /home/mask13/Desktop/Pocketful_Of_Rainbows.mkv \
       -vcodec mpeg4 -vtag XVID -qscale 5 -bf 0 \
       -mbd rd -flags +4mv+aic -trellis 2 -cmp 2 -subcmp 2 -g 300 \
       -acodec libmp3lame -ac 2 -ar 44100 -ab 128k \
       /home/mask13/Desktop/test.avi

```

I expect there are a few holes in this syntax but it certainly worked well enough on my system. You will find better results with an mp4 container and then the video stream from your file could be copied across rather than transcoded as it is h264...

All the best,

Andrew

---

### Post by mask13 on 2010-04-06
Thanks andrew.46! It worked, but it didn't copy the subtitles. You've helped me with my original problem though and MEncoder worked and copied the subtitles. I believe I'll stick with MEncoder for now, and I might try learning ffmpeg in the future. Thanks again.

---

