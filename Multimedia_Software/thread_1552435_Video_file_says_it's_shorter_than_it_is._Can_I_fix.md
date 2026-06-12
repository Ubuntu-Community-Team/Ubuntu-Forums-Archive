---
title: "Video file says it's shorter than it is. Can I fix it?"
date: 2010-08-13
forum: Multimedia Software
---

### Post by Pogeymanz on 2010-08-13
I have a video file I pulled off of a disc from a camcorder. The file is in .VOB. If I open the file in anything besides VLC, it says that it is 23 seconds long and will either play only the first 23 seconds or play the whole 15 minutes VERY QUICKLY.

So, if I want to put this file into a video editor, I can't do much with it because it either doesn't play at all, or only plays 23 seconds.

I'm guessing there is some metadata in the file that declares how long it is that VLC is just ignoring. How can I access and change that metadata to its actual length? I fired up a hex editor just to see if I could find the number 23 somewhere in the beginning of the file, but I couldn't...

Any ideas?

---

### Post by DanielWaterworth on 2010-08-13
I think it's possible to use VLC to stream to a file. This would be the simplest method.

---

### Post by Bachstelze on 2010-08-13
```
ffmpeg -i foo.vob
```

Output?

---

### Post by Pogeymanz on 2010-08-13
> **Bachstelze said:**
> ```
ffmpeg -i foo.vob
```

Output?

[rob shared ]$  ffmpeg -i Wedding_Disk1_2.VOB
FFmpeg version SVN-r24460, Copyright (c) 2000-2010 the FFmpeg developers
  built on Aug  6 2010 17:19:11 with gcc 4.5.0 20100610 (prerelease)
  configuration: --prefix=/usr --enable-gpl --enable-libmp3lame --enable-libvorbis --enable-libfaac --enable-libxvid --enable-libx264 --enable-libvpx --enable-libtheora --enable-postproc --enable-shared --enable-pthreads --enable-x11grab --enable-libopencore_amrnb --enable-libopencore_amrwb --enable-libschroedinger --enable-libopenjpeg --enable-version3 --enable-nonfree --enable-runtime-cpudetect --disable-debug
  libavutil     50.23. 0 / 50.23. 0
  libavcore      0. 0. 0 /  0. 0. 0
  libavcodec    52.84. 0 / 52.84. 0
  libavformat   52.76. 0 / 52.76. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.26. 1 /  1.26. 1
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
Input #0, mpeg, from 'Wedding_Disk1_2.VOB':
  Duration: 00:00:23.55, start: 0.222222, bitrate: 334924 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480 [PAR 8:9 DAR 4:3], 5017 kb/s, 29.97 fps, 29.97 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x80]: Audio: ac3, 48000 Hz, stereo, s16, 384 kb/s
At least one output file must be specified

---

### Post by Iowan on 2010-08-13
Moved to Multimedia & Video.

---

### Post by Bachstelze on 2010-08-13
ffmpeg apparently gets it right. You could try converting the file to something your editor will like better:

```
ffmpeg -i foo.vob foo.mp4
```

---

### Post by Pogeymanz on 2010-08-13
> **Bachstelze said:**
> ffmpeg apparently gets it right. You could try converting the file to something your editor will like better:

```
ffmpeg -i foo.vob foo.mp4
```

Actually, ffmpeg is getting it wrong. It says it's 23 seconds. It's actually 15 minutes.

And I've tried streaming from VLC into a file, but I feel like no matter what settings I use, the file is not good.

---

### Post by Bachstelze on 2010-08-13
Oh yes, sorry, I read that as 23 minutes. -_-

The I don't know, I generally use DGIndex + AviSynth to work with VOBs.  You could try that if you want, but they're Windows tools so you'd have to install Wine as well (yes, they work in it).

---

### Post by rodrigr2006 on 2010-08-18
im having a similar problem.  my mpeg files i pulled from the net played fine until about the 4th update.  happened with both 9.04 and 10.04 where they played fine and full length at first then got cut short after a few updates.  the file length itself has not changed.

i have no solution im sharing your frustration.

---

### Post by Pogeymanz on 2010-08-18
Here is what I did that fixed it.

```
ffmpeg -i messedupfile.fileextension -sameq betterfile.newextension
```

And ffmpeg through out some errors/warnings here and there (well, obviously because the file is messed up), but it completed. And as a result, I have perfectly good AVIs that know how long they are supposed to be!

---

