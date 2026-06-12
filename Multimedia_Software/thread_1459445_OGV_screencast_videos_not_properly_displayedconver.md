---
title: "OGV screencast videos not properly displayed/converted on youtube"
date: 2010-04-21
forum: Multimedia Software
---

### Post by dugh on 2010-04-21
After switching from Ubuntu 9.04 to 10.04, screencasts I create with gtk-recordmydesktop are no longer working when I upload them to youtube.

The best I can figure out is that Ubuntu is using a new version of the theora encoder that apparently is not backward compatible.  Perhaps Youtube is still using an older version that can't handle it, as someone suggested in this thread:
[http://www.google.com/support/forum/p/youtube/thread?tid=7b9148c46c6b6f90&hl=en](http://www.google.com/support/forum/p/youtube/thread?tid=7b9148c46c6b6f90&hl=en)

Here are some related threads and bug reports:
[https://bugs.launchpad.net/ffmpeg/+bug/305286](https://bugs.launchpad.net/ffmpeg/+bug/305286)
[http://ubuntuforums.org/showthread.php?t=1410740](http://ubuntuforums.org/showthread.php?t=1410740)
[https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/522812](https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/522812)
[https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/305286](https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/305286)
[http://ubuntuforums.org/showthread.php?p=7166839](http://ubuntuforums.org/showthread.php?p=7166839)


Here are some sample youtube videos demonstrating the problem:
[http://www.youtube.com/watch?v=kPiRak0aDAQ](http://www.youtube.com/watch?v=kPiRak0aDAQ)
[http://www.youtube.com/watch?v=CQ9L6kk_vPU](http://www.youtube.com/watch?v=CQ9L6kk_vPU)
[http://www.youtube.com/watch?v=1wIsJLWZPco](http://www.youtube.com/watch?v=1wIsJLWZPco)

My question is - is there any way to down-convert my ogv video screencasts to an older, compatible version of theora or whatever.  Can I convert it to something compatible with ffmpeg or mencoder or mkvmerge or whatever.  Just converting to mkv or avi first and then uploading to youtube does not work (so it may be still an ubuntu issue, too).

I'd rather not have to completely re-install ubuntu 9.04 just for this one issue.

---

### Post by dugh on 2010-04-22
Is anyone successfully creating screencasts in Ubuntu 10.04 and uploading them to Youtube where they display correctly?  

If you could share how you did it, I'd appreciate it, thanks

---

### Post by FakeOutdoorsman on 2010-04-22
If I remember correctly, someone on the #ffmpeg irc channel reported success with:
```
ffmpeg -i from-recordmydesktop.ogv -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre hq -crf 22 -threads 0 output-for-youtube.mkv
```
Results may vary.  Next time you need to screencast I recommend following the following instructions and avoiding recordmydesktop:
[url=http://verb3k.wordpress.com/2010/01/26/how-to-do-proper-screencasts-on-linux/]
How to do Proper Screencasts on Linux Using FFmpeg[/url]

---

### Post by X_Splinter on 2010-05-12
I notice that too, no matter what program, the ogv simply display horrible wrong in Youtube.

---

### Post by suli8 on 2010-05-15
im using devede for converting to .avi but since upgrade to lucid the .avi file has 10 minutes more...dont know why...

---

### Post by edgarinventor on 2010-06-08
> **X_Splinter said:**
> I notice that too, no matter what program, the ogv simply display horrible wrong in Youtube.

Used this:[http://gtk-apps.org/content/show.php?content=90837]("http://gtk-apps.org/content/show.php?content=90837")

Converted a 3 min 20 sec video, I later edited out 3 sec off, and added subtitles on Kdelive:
[http://faz-voce-mesmo.blogspot.com/2010/06/como-sacar-o-som-do-youtube-no-ubuuntu.html]("http://faz-voce-mesmo.blogspot.com/2010/06/como-sacar-o-som-do-youtube-no-ubuuntu.html")

---

### Post by X_Splinter on 2010-06-08
> **edgarinventor said:**
> Used this:[http://gtk-apps.org/content/show.php?content=90837]("http://gtk-apps.org/content/show.php?content=90837")

Converted a 3 min 20 sec video, I later edited out 3 sec off, and added subtitles on Kdelive:
[http://faz-voce-mesmo.blogspot.com/2010/06/como-sacar-o-som-do-youtube-no-ubuuntu.html]("http://faz-voce-mesmo.blogspot.com/2010/06/como-sacar-o-som-do-youtube-no-ubuuntu.html")
Gonna try it, thanks mate

---

