---
title: "Problem running FFmpeg on xUbuntu"
date: 2009-06-24
forum: Multimedia Software
---

### Post by TouchDown on 2009-06-24
Hello all!

I'm a totally newbie using linux, so I googled a lot of hours trying to solve my problem, but I can't found nothing.

I explain my problem.
I am using xubuntu 9.04 in a vmware machine, because I am developing a website that needs ffmpeg extension and my hosting company doesn't allow this. So I use it to test the website before to pay for a dedicated server.

I've installed an FTP server and Apache with php and works fine. I tryied to install FFmpeg and seems that is installed correctly. To do this I used lots of How-To's that I found on the internet.

One of many How-To's used is [**HOWTO: Install and use the latest FFmpeg and x264**]("http://ubuntuforums.org/showthread.php?t=786095") and after I used this **[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg]("http://ubuntuforums.org/showthread.php?t=1117283"). **

When I try to convert a video file, I use **ffmpeg -i entrada.mpg salida.avi** and I receive this:

> FFmpeg version SVN-r19244, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.32. 0 / 52.20. 0
  libavformat   52.34. 0 / 52.31. 0
  libavdevice   52. 2. 0 / 52. 1. 0
  libswscale     0. 7. 1 /  0. 7. 1
  built on Jun 23 2009 16:33:20, gcc: 4.3.3

Seems stream 0 codec frame rate differs from container frame rate: 50.00 (50/1) -> 25.00 (25/1)
Input #0, mpeg, from 'entrada.mpg':
  Duration: 00:00:35.96, start: 0.200000, bitrate: 3766 kb/s
    Stream #0.0[0x1e0], 1/90000: Video: mpeg2video, yuv420p, 720x576 [PAR 16:15 DAR 4:3], 1/50, 15000 kb/s, 25 tbr, 90k tbn, 50 tbc
    Stream #0.1[0x1c0], 1/90000: Audio: mp2, 48000 Hz, stereo, s16, 192 kb/s
ffmpeg: symbol lookup error: ffmpeg: undefined symbol: avcodec_channel_layout_num_channelsI can't find information about this error: [B]ffmpeg: symbol lookup error: ffmpeg: undefined symbol: avcodec_channel_layout_num_channels

[/B]Can anyone help me?
Please, tell me what I have to do in an easy way that a beginner like me can understand.

Thank you all!

---

### Post by enthdegree on 2009-10-15
Was having the same problem and I just found a fix.
Try:```

sudo apt-get install libavcodec52  libavutil49
```
then run:```

export LD_LIBRARY_PATH=/usr/local/lib/
```
It should get rid of libavcodec-unstripped-52 and libavcodec-unstripped49 if you have them installed at all. 
Grubby little problem, it's really hard to google/irc for. )c:<

---

### Post by hellocatfood on 2009-12-14
Thanks for that solution, but doing so would mean I have to uninstall quite a lot of packages (such as Blender, which I use regularly)

Is there any other way to do it?

---

### Post by BioG on 2010-01-07
> **hellocatfood said:**
> Thanks for that solution, but doing so would mean I have to uninstall quite a lot of packages (such as Blender, which I use regularly)

Is there any other way to do it?

hi,
for me it works just using only the second command:

```
export LD_LIBRARY_PATH=/usr/local/lib/
```iam using ubuntu 9.10

cheers, BioG

---

### Post by bobbiescap on 2010-04-30
Thanks guys, 

I dashed off without reading the rest of the posts and removed a few packages I needed so reinstalled them and ran the second command and have it working now. My fault for rushing and not reading the terminal output. I am very relieved to have the issue fixed and the two minutes I lost by deleting the packages was nothing to the time I have spent trying to troubleshoot this issue.

Such a simple fix, so much hassle finding it, I am very grateful to you all.

---

