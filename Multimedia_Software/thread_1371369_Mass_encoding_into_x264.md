---
title: "Mass encoding into x264?"
date: 2010-01-03
forum: Multimedia Software
---

### Post by Aluxander on 2010-01-03
I have a load of XViD videos and I want to re-encode them into x264 - when I say a load, I mean over 300, anyone have any programs they reccomend to do it?

I want to make them into those "future-sized movies" (700mb --> 300mb, 170mb --> 95mb, 350mb --> 150mb), what settings should I use? I want to keep the quality of the originals intact, along with the video sizes if possible, but if not, I don't really mind, just make them smaller. Here are the settings some people use in windows:

[IMG]http://i40.tinypic.com/24xmdsl.jpg[/IMG]

[IMG]http://i41.tinypic.com/2wmql1g.jpg[/IMG]

what programs shall I use and what settings? thanks in advance everyone :)

oh yeah, one last thing - fast encoders please, I know it'll take a good while, but I want it to take as little time as possible please :)

---

### Post by SuperSonic4 on 2010-01-03
x264 is a video encoder so you don't really have much choice ;)

I'm not entirely sure how you'd do it, a ffmpeg script might work but then you'd have to compile ffmpeg with x264 supportq

---

### Post by Aluxander on 2010-01-03
> **SuperSonic4 said:**
> x264 is a video encoder so you don't really have much choice ;)

I'm not entirely sure how you'd do it, a ffmpeg script might work but then you'd have to compile ffmpeg with x264 supportq
h264 if you're gonna be anal about it :p

---

### Post by Aluxander on 2010-01-03
here's an example of a script that autox264 produced
```
mencoder -vf harddup,crop=624:272:0:40,scale=564:240,hqdn3d=2:1:2  -sws 2 -aspect 1.7727 -of rawvideo -o autox264.h264  -nosound -ovc x264 -x264encopts crf=18:threads=auto:bframes=3:direct_pred=auto:me=hex:subq=6:turbo=2:frameref=3 "/home/alex/Desktop/sample.avi"
mkvmerge -o "/home/alex/Desktop/sample.mkv" --default-duration 0:23.976fps --aspect-ratio -1:2.3529 autox264.h264 
```

anyone have any idea how to make a script where I can just run it on a folder and it'll produce a script I can just run in the terminal and leave to run?

---

### Post by MetalMusicAddict on 2010-02-10
> **Aluxander said:**
> here's an example of a script that autox264 produced
```
mencoder -vf harddup,crop=624:272:0:40,scale=564:240,hqdn3d=2:1:2  -sws 2 -aspect 1.7727 -of rawvideo -o autox264.h264  -nosound -ovc x264 -x264encopts crf=18:threads=auto:bframes=3:direct_pred=auto:me=hex:subq=6:turbo=2:frameref=3 "/home/alex/Desktop/sample.avi"
mkvmerge -o "/home/alex/Desktop/sample.mkv" --default-duration 0:23.976fps --aspect-ratio -1:2.3529 autox264.h264 
```

anyone have any idea how to make a script where I can just run it on a folder and it'll produce a script I can just run in the terminal and leave to run?

Something like this should work:
```
[SIZE="1"]#!/bin/bash

for a in *.avi
        do
                OUT=`echo "$a" | sed s/"\.avi$"/"\.mkv"/g`
		mencoder -vf harddup,crop=624:272:0:40,scale=564:240,hqdn3d=2:1:2 -sws 2 -aspect 1.7727 -of rawvideo -o autox264.h264  -nosound -ovc x264 -x264encopts crf=18:threads=auto:bframes=3:direct_pred=auto:me=hex:subq=6:turbo=2:frameref=3 "$a"
		mkvmerge --default-duration 0:23.976fps --aspect-ratio -1:2.3529 autox264.h264 "$OUT"
        done[/SIZE]
```
Might have to play with the input/output parts.

---

