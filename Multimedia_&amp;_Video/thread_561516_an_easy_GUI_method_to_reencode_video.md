---
title: "an easy GUI method to reencode video?"
date: 2007-09-27
forum: Multimedia &amp; Video
---

### Post by the_darkside_986 on 2007-09-27
Does anyone know of a functional software or script to easily convert any non-free video format to a free video format such as ogg theora? I tried using VLC media player and it simply wrote the file's audio output correctly but the video was missing and just a blank screen.

I've tried looking at some of the command-line tools but the tutorials are poorly written and do not show good examples of how to convert any specific file in only one script or one command.

I did make a little bash script that can convert all mp3's in the current directory to ogg without destroying the mp3's. I can change a line in the script to make the script work on other files like wma. I would like something simple like that for converting videos. Thanks.

Also, Ubuntu really needs more easy tools for converting non-free formats to free alternatives. I would appreciate that far more than making it easy to play the non-free formats.

---

### Post by tbroderick on 2007-09-27
ffmpeg2theora
mencoder
mencoder infile.wmv  -ovc lavc -oac mp3lame -o outfile.avi -ofps 30000/1001

---

### Post by ~LoKe on 2007-09-27
[http://ubuntuforums.org/showthread.php?t=320788&highlight=convert](http://ubuntuforums.org/showthread.php?t=320788&highlight=convert)

---

### Post by the_darkside_986 on 2007-09-27
> **tbroderick said:**
> ffmpeg2theora
mencoder
mencoder infile.wmv  -ovc lavc -oac mp3lame -o outfile.avi -ofps 30000/1001

Thanks. It almost works but when I use mencoder to convert the .mov into the mpeg .avi file, and then use ffmpeg2theora to convert it to ogg, the picture runs too fast, twice as fast as the audio (which works fine). I guess that the video file isn't correct or this is the result of widespread use of non-standard,  closed formats such as quicktime :( . But thanks anyway. I will be able to use this on other files that are not corrupted.

Thankfully I'm on a platform that doesn't require me to install quicktime to use it. There's no way I'd ever install quicktime on any platform, including Windows. It is a major security hazard. The Gnome "Movie Player" application works fine for me.

(This file is for French class.) I cannot help but laugh at the other n00bs in my class who probably are inclined to actually install malware such as RealPlayer and QuickTime on their machines to view the media. I converted all of the RealPlayer files to vorbis. Freedom, FTW. :guitar:

---

