---
title: "How do I get My .avi file to play"
date: 2009-08-10
forum: Multimedia Software
---

### Post by cquigley on 2009-08-10
Hi Everyone-

  I have some ,avi filse that will not play in Movie Player or any other video player. It's only the 6 .avi files in a particular folder. I have other .avi file that work fine.

I checked the properties and it is indeed a .avi file. It says it doesn't recognize the file type, however it will play other .avi file fine. Can't figure out how to get it to play. Can someone please help.

This is what it says in the properties ".AVI video (x-msvideo) anyone know what this is?

thanks,
  cquigley

---

### Post by Tclarkie on 2009-08-10
install vlc in add remove

---

### Post by cquigley on 2009-08-10
never started working

---

### Post by Tclarkie on 2009-08-10
in vlc? where did you et the nonworking avi's

---

### Post by andrew.46 on 2009-08-10
Hi cquigley,

> **cquigley said:**
> I checked the properties and it is indeed a .avi file. It says it doesn't recognize the file type, however it will play other .avi file fine. Can't figure out how to get it to play. Can someone please help.

There could be a codec problem. Can you identify the file with FFmpeg? Have a look at installation of FFmpeg here:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

and then test the problem avi file as follows:

```
ffmpeg -i **[COLOR="Red"]*my_problem_file.avi*[/COLOR]**
```

and post the full terminal output here. This will show the exact codecs used in the file and from there it should not be too difficult to get playback.

Andrew

---

