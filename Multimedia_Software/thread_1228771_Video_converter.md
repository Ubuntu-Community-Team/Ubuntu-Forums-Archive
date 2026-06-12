---
title: "Video converter"
date: 2009-08-01
forum: Multimedia Software
---

### Post by Telhma on 2009-08-01
Hello all.

Long long time ago i converted a DVD in to a mp4 with neroburn i think. Now, today I am using linux, and i bought me a multimedia disk. It can't play MP4, so i would like to convert my video to mpg or avi.

I downloaded FF video converter, but when i press convert it always say unknown encoder "mpeg2video or unknown encoder "libxvid"

after that i need to press enter, and then the converter does noting any more.

Is there a other converter i can use, or is there a way to get this working?

greetings

Telhma

---

### Post by starcraft.man on 2009-08-01
I know, video converters that change video from one format to another are a bit difficult to find. Most are for DVD ripping to format x, not conversion.

IMO, the best would be Handbrake which recently implemented universal input (i.e. any format that it can encode/decode). Should work (I haven't tried, I only rip from DVDs). It isn't in the repos, so download from site ([http://handbrake.fr/?article=download](http://handbrake.fr/?article=download)) and then just install like any other deb. You want the GTK build for a GUI, and either the 32 or 64 bit version depending on which version your computer is. If you don't know, it's probably not 64.

---

### Post by SuperSonic4 on 2009-08-01
I think ffmpeg would be the best solution for converting video although it does require some learning.

Something like ```
ffmpeg -i input.mp4 -sameq -vcodec mpeg4 -acodec libfaac -ac 2 -ab 128k output.avi
```

edit the first: It may just be easier to re-encode the dvd to avi using handbrake, dvdrip, k9copy etc

---

### Post by xc3RnbFO8P on 2009-08-01
Try **Devede** in Add/Remove (all available application)

---

### Post by starcraft.man on 2009-08-01
> **SuperSonic4 said:**
> 
edit the first: It may just be easier to re-encode the dvd to avi using handbrake, dvdrip, k9copy etc
+1 Conversion of a video files from one compressed format to another will almost always result in some loss of video quality. Best to re-encode from dvd source if possible, it is time consuming and a pain though I know.

> Try Devede in Add/Remove (all available application) 
Devede is more of a disc authoring converter though, even with the divx conversion.

---

### Post by xc3RnbFO8P on 2009-08-01
> It can't play MP4, so i would like to convert my video to mpg or avi.

> Devede is more of a disc authoring converter though, even with the divx conversion.
I meant Mp4 to mpeg and Avi's :)

---

### Post by cptrohn on 2009-08-01
WinFF works well... I think it is listed in adept as Video converter..

avidemux(GTK+) is also one I have used that worked well for converting my videos to be used with my Cowon D2+ it is in add/remove as well.

---

