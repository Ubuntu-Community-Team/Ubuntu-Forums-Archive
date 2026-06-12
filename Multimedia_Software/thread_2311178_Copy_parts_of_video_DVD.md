---
title: "Copy parts of video DVD"
date: 2016-01-25
forum: Multimedia Software
---

### Post by freesitebuilder on 2016-01-25
I have two DVDs of old family cine films. File formats are .vob and there's no audio. I'd like to copy parts of these for relatives and friends - they wouldn't be interested in watching the whole thing. I've been looking at the various video software options, but these all look too complex for my needs. If this were a text document, I'd simply want to select, copy, and paste!

What are the best options for very basic stuff like this? I'm running Ubuntu 14.04 LTS.

Thanks.

---

### Post by Vladlenin5000 on 2016-01-25
Openshot, KDEnlive, Pitivi are free and available at the Ubuntu repositories. They're all very simple video editors and you can select, copy and paste parts of a video file as you want. 
However, for most you'll need a video file, not the VOB structure typical of a DVD-Video. In order to convert it in something editable you probably want to use Handbrake first (also available at the repositories).

---

### Post by FakeOutdoorsman on 2016-01-26
You can use ffmpeg:
```
ffmpeg -ss 30 -i input -t 00:01:23 -c:v libx264 -vf yadif=1,format=yuv420p -movflags +faststart output.mp4
```

-ss will skip the first 30 seconds.
-t will make the output 1 minute and 23 seconds. -ss and -t are the only options you will need to modify.
yadif is a filter that will deinterlace. DVDs are interlaced, but watching it on a computer or device can show ugly lines; this filter will fix that. format is a filter that will make a widely compatible "pixel format".
"-movflags +faststart" is added in case the video will be viewed via progressive download so it can begin to play before the file is completely downloaded.

The real ffmpeg isn't in the 14.04 repo, so you can use [mc4man's PPA](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media), or a [static binary](http://johnvansickle.com/ffmpeg/), or [compile](http://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu).

Why do your VOB files contain no audio?

---

### Post by freesitebuilder on 2016-01-26
These are very old films - from the 70s and 80s, I don't think the cine camera used had sound, just film.

---

### Post by shantiq on 2016-01-28
well you can also use Handbrake
first run your DVD in VLC or similar and note the times where you want cuts
then do conversion this [way]("http://ubuntuforums.org/showthread.php?t=2310471&p=13427750#post13427750")

OR much **SIMPLER**:

play your DVD in VLC  and do this
&#10040; View/tick in Advanced Controls
&#10040; Play your DVD
&#10040; Click on red button to start recording/press again to stop
&#10040; Collect result in Videos folder

[ATTACH=CONFIG]267000[/ATTACH]

---

