---
title: "convert videos for powerpoint"
date: 2007-11-21
forum: Multimedia Production
---

### Post by reader4 on 2007-11-21
Seems like a simple problem, but I have spent all day trying to find a good solution and have yet to get this working.

I have to give a couple of presentations in PowerPoint - we are told ahead of time that only AVI and MPG formats are supported using cinepak, mpeg1, mpeg2, msmpeg4, divx 3-5 and indeo formats are allowed.  I have some 70 MB videos that were created using MATLAB as AVIs - 640x480, raw RGB, 30fps, no audio.  I can easily convert them to anything I want using ffmpeg or mencoder with default options (bit rate ~. The file size drops to ~500kB and they look great in mplayer and totem.  The problem is that when I try to view them on Windows Media player in my winXP virtual machine, I get codec errors.  The divx codecs are installed.

If I encode using ffmpeg and -vcodec mpeg1video, they look like garbage.  If I use -vcodec mpeg4, the video is upside down in Win Media Player.

So, can anyone suggest a suitable format that will give me reasonable video AND is compatible with Windows?  I can post my inputs and stills of each trial if it helps.

---

### Post by Creative2 on 2007-11-22
well man i have made some mov suitable for windows with ffmpeg (aac and mpeg4 for codecs)

if you need mpg mpeg i suggest to use ffmpeg to convert them into mpeg formats 

look at this

ffmpeg -i INPUT -r 25 -f mpeg -vcodec mpeg2video -ar 48000 -b 700k -acodec mp3 -ab 192 -s 640x480 -y OUTPUT

---

### Post by reader4 on 2007-12-09
MOV formats were not allowed... I ended up just using ffmpeg with -vcodec mpeg1video.  With a 500k bitrate, the videos were just 750k (originally 109MB AVI) with reasonable quality.

---

