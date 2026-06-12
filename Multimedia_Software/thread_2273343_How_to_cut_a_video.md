---
title: "How to cut a video?"
date: 2015-04-12
forum: Multimedia Software
---

### Post by remmas-sido on 2015-04-12
What are the possible ways of cutting a video?

---

### Post by TheFu on 2015-04-12
avidemux
ffmpeg
mencoder
mkvmerge
avconv

oh ... and there are well-know video linux editors (lightroom ... kenlive, ... )  - but those seem to be made for content creators, not people trying to cut scenes from TV/Movies.

It really would be helpful if you said which video and audio codecs and what containers are being used. This will determine the best editor more than anyhting else.  For example, editing an xvid/mp3 inside an avi container is harder than editing an mpeg2/aac/ac3 in a TS/mpg/PS container.

Also - many of these editors will not passthru all the streams, so if you have 5 sub, 2 captions and 4 audio streams ... they almost all fail.  For those needs, I've found using mkvmerge to be the most reliable. Plus mkvmerge doesn't require stupid time calculations like start and duration for each cut.  Sometimes I shove other outputs into an MKV just to use the mkvmerge clip facilities.  Never tried the GUI version for that, but it probably works too.

---

### Post by Bucky Ball on 2015-12-01
Kino will probably do that in a jiff. It's in the repos.

---

### Post by shantiq on 2015-12-01
kdenlive or


TRIM AND SPLIT VIDEO or audio
FROM COMMAND-LINE syntax
  avi mkv mp4 etc

ffmpeg Nota Bene:   syntax has changed over the last few years so read carefully :]   also I had time before ffmpeg command to see how long it took


 ```
time ffmpeg -i video.mp4 -ss 00:00:00 [COLOR=#800000]-to[/COLOR] 00:05:00 [COLOR=#800000]c copy[/COLOR] 5minutevideo.mp4

```



```
mencoder -ss 01:00:00 -endpos 00:05:56 -oac copy -ovc copy video.mp4 -o trimmedvideo.mp4

```

if it moans about audio use:

```
mencoder -ss 01:00:00 -endpos 00:05:56 **-oac pcm** -ovc copy video.mp4 -o trimmedvideo.mp4
```

---

### Post by T.J. on 2015-12-02
If you are just looking for something fast and dirty to edit your personal video, try openshot.

---

### Post by MartyBuntu on 2015-12-03
Avidemux...to cut video without the need to re-encode.

---

### Post by blm-ubunet on 2015-12-03
I never had any joy (in the past) with avidemux on H264 (AVC mpeg4 part 10) transport stream container video files.

mpv with lua script plugin..
[https://github.com/lvml/mpv-plugin-excerpt](https://github.com/lvml/mpv-plugin-excerpt)
Even has a cut-list editor like mythtv!

For speed & not re-encoding (esp. with H264/HEVC) you need to cut on keyframes (start of decoder refresh sequence).

As mentioned in post #2:
Mkvmerge (MKVToolNix) can cut/split video file on multiple places & can re-merge the pieces.
It can be scripted (driven from command line) with cut-list.
It will cut only at keyframe sequences.
It only works with mkv container (minor issue).
Appears (these days) you have to use a ppa for MKVToolNix (author/maintainer's below):-
[http://www.bunkus.org/ubuntu/](http://www.bunkus.org/ubuntu/)
or build from source.

---

### Post by Rob Sayer on 2015-12-05
Agreed about avidemux and h.264/AVC video, which is pretty standard nowadays.  Usually .mp4 or .mkv files use it.  Avidemux is great for editing xvid/ASP video like in most .avi files.  Mpeg4 ASP is the only format it'll cut on non key frames.

Cutting where you want isn't as simple as video newbies think it is.  Even in Windows or OS X you can't get free tools that will do smart cutting (ie. not on key frames) with h.264 video.  And the paid ones aren't available for linux AFAIK.

---

