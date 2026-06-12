---
title: "Can't open a particular video"
date: 2011-11-11
forum: Multimedia Software
---

### Post by CrimpJiggler on 2011-11-11
I downloaded a 200Mb .wmv video file but I can't open it for some reason. Movie Player says "An error occured: Could not determine type of stream. VLC gives no error message. They're the only media players I have but I tried opening it with avidemux and it just says "Cannot open the file". If I run avidemux with the terminal then try open the video, heres what the terminal says:
> 39b7177e -> 39b7177e
Probing : /home/crimpjiggler/Downloads/video.wmv
There was several files, but dont append was forced

Simple loading: 
 file: /home/crimpjiggler/Downloads/video.wmv, size: 245867252
 found 1 files 
Done 
Cannot identify /home/crimpjiggler/Downloads/video.wmv as mpeg (4/0)
Cannot identify as H264 ES (0/50)

 unrecognized file detected...
~&#65533;9 (39B7177E)


I have no idea what any of that means though. When I have a problem like this, usually one of those 3 programs (mplayer, vlc, avidemux) can open the video. Are there any other programs I should try loading the video with? Is there some kinda video diagnostic program you can get that is made for diagnosing and repairing video files? I usually use avidemux for that kinda thing but thats a video editing program so its probably not designed for the sort of thing.

---

### Post by Rubykuby on 2011-11-11
Convert it.

This is just one site I've found that I believe can convert .wmv files:

[http://www.mediaconverter.org/](http://www.mediaconverter.org/)

---

### Post by FakeOutdoorsman on 2011-11-11
What does FFmpeg say about the video?
```
ffmpeg -i video.wmv
```
Does ffplay work correctly?
```
ffplay video.wmv
```

---

### Post by CrimpJiggler on 2011-11-11
ffmpeg says "video.wmv: Invalid data found when processing input"

---

### Post by FakeOutdoorsman on 2011-11-12
I'm guessing that the input is corrupt or broken in some way, but it's hard to say. Can you provide the complete terminal output that includes that message? Can you also provide the file if it isn't too big? Mediafire is a good place to upload it if it's under 200 MB, if I recall correctly.

---

### Post by gordintoronto on 2011-11-12
Can you open other wmv files? Did you install the restricted extras? What version of Ubuntu? 64-bit or 32? Some versions also require non-free-codecs from Medibuntu.

---

### Post by CrimpJiggler on 2011-11-18
Sorry for not replying earlier. I can run other WMVs with all my media players, I don't know what was wrong with this one. I got fed up and just deleted it. There must be some kinda video doctor program that will tell you whats wrong with a video file though. Also I regularly wanna find out what codec a video file uses but I don't know how to do it, even with avidemux. There must be a simple way to find out what codec a video is with Ubuntu. Any of you know of one?

---

### Post by ron999 on 2011-11-18
> **CrimpJiggler said:**
> There must be a simple way to find out what codec a video is with Ubuntu. Any of you know of one?
Hi
MediaInfo does a good job.
Look here --> [http://mediainfo.sourceforge.net/en]("http://mediainfo.sourceforge.net/en")

---

### Post by SeijiSensei on 2011-11-18
Play the file from the command line with mplayer (e.g., "mplayer /path/to/file.mkv").  Use "mplayer -v" to get even more information.

---

### Post by FakeOutdoorsman on 2011-11-18
Another method is FFmpeg (assuming the file isn't broken):
```
$ ffmpeg -i IronMan.mkv 
ffmpeg version N-34884-g7575980, Copyright (c) 2000-2011 the FFmpeg developers
  built on Nov 15 2011 11:51:13 with gcc 4.6.2
  configuration: --prefix=/usr --enable-gpl --enable-libx264
  libavutil    51. 25. 0 / 51. 25. 0
  libavcodec   53. 34. 0 / 53. 34. 0
  libavformat  53. 20. 0 / 53. 20. 0
  libavdevice  53.  4. 0 / 53.  4. 0
  libavfilter   2. 48. 1 /  2. 48. 1
  libswscale    2.  1. 0 /  2.  1. 0
  libpostproc  51.  2. 0 / 51.  2. 0

Seems stream 0 codec frame rate differs from container frame rate: 47.95 (10000000/208541) -> 23.98 (24000/1001)
Input #0, matroska,webm, from 'IronMan.mkv':
  Duration: 00:01:48.50, start: 0.000000, bitrate: 4141 kb/s
    Stream #0:0: Video: **h264** (High), yuv420p, 1280x720, SAR 115:87 DAR 1840:783, 23.98 fps, 23.98 tbr, 1k tbn, 47.95 tbc (default)
    Stream #0:1: Audio: **aac**, 48000 Hz, stereo, s16 (default)
```

---

