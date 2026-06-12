---
title: "Cut Assistant"
date: 2010-04-25
forum: Multimedia Software
---

### Post by mastermindg on 2010-04-25
[http://sourceforge.net/projects/cutassistant/](http://sourceforge.net/projects/cutassistant/)

I've used Cut Assistant in the past to edit videos (avi & wmv) and would like to find a way of getting this functionality from Ubuntu, either by using Wine or by using another similar app.

Does anybody know of an app similar to Cut Assistant?

---

### Post by garyedwardjohnston on 2010-04-25
[http://www.webupd8.org/2009/05/join-and-split-files-including-video-in.html](http://www.webupd8.org/2009/05/join-and-split-files-including-video-in.html)

---

### Post by mastermindg on 2010-04-26
[http://www.webupd8.org/2009/05/join-...-video-in.html](http://www.webupd8.org/2009/05/join-...-video-in.html)

...great if you want to package videos for file transfer. I'm looking for a more full-featured cutter/joiner with a GUI, like Cut Assistant. I may end up having to program it myself. I know that I can get the functionality out of ffmpeg.

---

### Post by FakeOutdoorsman on 2010-04-26
I think Avidemux has a trim functionality, but I'm unsure if it does this without the need to re-encode.  FFmpeg, like you mentioned, can cut or trim a video without th need to re-encode thus preserving the quality and doing it quickly:
```
ffmpeg -ss 00:02:34 -t 15 -i input.foo -acodec copy -vcodec copy output.foo
```
The *-ss* option is the offset time from the beginning of the input file.  FFmpeg will ignore the first 2 minutes and 34 seconds in my example.  You can also just use seconds as shown in my *-t* example.  This will create an output file that is 15 seconds long.

---

