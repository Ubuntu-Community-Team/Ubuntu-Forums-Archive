---
title: "Converting video to mp3 using mencoder. (newbie user)"
date: 2010-03-22
forum: Multimedia Software
---

### Post by bantuyo on 2010-03-22
I want to convert a bunch of mp4 and flv files to mp3 files using mencoder. What should be the proper command?

I'm trying this:
```
mencoder in.mp4 -ovc frameno -oac mp3lame -o out.mp3
```

How should I modify it? Are there a better non-GUI apps for extracting audio out of video files?

---

### Post by andrew.46 on 2010-03-23
Hi bantuyo,

> **bantuyo said:**
> Are there a better non-GUI apps for extracting audio out of video files?

IMHO a much superior non-GUI application for this purpose is FFmpeg. I would suggest have a look at this page:

 HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

and install the best possible copy of FFmpeg (the repository version has substantial limitations). Then if you are happy with this you could then *interrogate* one of your files in the following manner:

```
ffmpeg -i **[COLOR="Red"]my_file.mp4[/COLOR]**
```

with **[COLOR="Red"]my_file.mp4[/COLOR]** being substituted with *your own file*, and place the command and full terminal output here. Myself or another can then demonstrate how to strip the audio from the file and transcode to the audio output of your choice :).

Andrew

---

