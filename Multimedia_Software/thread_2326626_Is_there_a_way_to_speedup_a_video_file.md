---
title: "Is there a way to speedup a video file"
date: 2016-06-02
forum: Multimedia Software
---

### Post by jacatone on 2016-06-02
I work with many different video formats (avi, mpg4, wmv, etc.). Often it would be really helpful to speed them up and often re-encode them with the speed change. Is there a command line solution or an app that would allow me to do that? Thanks.

---

### Post by mcduck on 2016-06-03
Sure. If you want command-line, the ffmpeg should do the trick: [https://trac.ffmpeg.org/wiki/How%20to%20speed%20up%20/%20slow%20down%20a%20video]("https://trac.ffmpeg.org/wiki/How%20to%20speed%20up%20/%20slow%20down%20a%20video")

...and for a graphical one, I'd recommend Avidemux.

---

### Post by jacatone on 2016-06-05
Tried replacing "input.mkv" in "ffmpeg -i input.mkv -filter:v "setpts=0.5*PTS" output.mkv" with the mp4 or avi file I wanted to speedup, but it didn't work. How do you use this command? Couldn't find directions in Avidemux for speeding up and saving the result either.

---

### Post by $yl9pAR%t on 2016-06-05
I have no idea about ffmpeg and Avidemux, but if I understand you right, this feature is available in OpenShot Video Editor.

---

### Post by FakeOutdoorsman on 2016-06-06
> **jacatone said:**
> Tried replacing "input.mkv" in "ffmpeg -i input.mkv -filter:v "setpts=0.5*PTS" output.mkv" with the mp4 or avi file I wanted to speedup, but it didn't work.
What do you mean by, "didn't work"? Please show the complete console output from the command (and use the code button to format it).

---

### Post by uwe-bungto on 2016-06-06
I have use Lightworks; but that maybe overkill

---

