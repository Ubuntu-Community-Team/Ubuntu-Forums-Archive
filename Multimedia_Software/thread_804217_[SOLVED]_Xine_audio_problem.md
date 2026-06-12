---
title: "[SOLVED] Xine audio problem"
date: 2008-05-22
forum: Multimedia Software
---

### Post by Awperator on 2008-05-22
Hello,

I have an odd Xine problem. With some files, there is no audio. The video plays fine, but there is no audio, no matter what driver I choose (alsa, pulseadio, oss, etc). I am currently trying to figure out which file types this occurs in (so far it seems its H264 encoded files, but I'm not sure.) I am trying to use xine in mythtv, but even with the regular desktop it has this problem. The same video files play fine in mplayer and vlc, but I need xine to work.

Any ideas please? I have tried using mplayer, but for some reason it lags on some of my videos; the audio is delayed from the video track on some videos, not all. I can't use vlc either because it chokes with subtitles on .mkv files.
Thank you for your time. If you need any information I will be happy to provide more.

UPDATE: It seems that files with Vorbis audio encoding are affected.

---

### Post by Awperator on 2008-05-23
I think I might have to compile the latest Xine from source. When I try to do this using [these]("http://xinehq.de/index.php/faq#BUILDING") instructions, I run into problems with the XShm extension not being available, or debuild not working (says i'm not in source tree). 

I would really appreciate some help.

Thanks.

---

### Post by Awperator on 2008-05-23
For anyone that is interested, I have solved my problem. Basically, I started out with MPlayer having difficulty playing some files. The audio was delayed on them, and it wasn't a computer problem; the file was delayed as well in 2 other machines running ubuntu. The weird thing was that it was fine in vlc and xine. Therefore I switched to vlc, but I had problems displaying subtitles in mkv files in vlc. I then switched to xine, but xine has difficulty playing mkv files with vorbis encoding. I then went back to playing with mplayer.

I was able to find an option, "mc=0", that compensates for files with badly encoded VBR audio. Problem fixed, I'm using mplayer, but as for the topic of this thread, Xine still has an audio problem.

Thanks.

---

