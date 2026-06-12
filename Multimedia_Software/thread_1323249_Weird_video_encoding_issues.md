---
title: "Weird video encoding issues"
date: 2009-11-11
forum: Multimedia Software
---

### Post by lovinglinux on 2009-11-11
I need to re-encode some videos to play with Miro, but I'm experiencing two types of problems.

[LIST=1]
[*]video starts immediately after clicking the play button, but takes a long time and CPU cycles when using the seek bar or keyboard arrows.
[*]video takes longer to start, but seeks fast. Additionally, thumbnails are messed and when I use the seek bar, the video becomes completely messed and exhibit some pixelated blocks for a few seconds, then goes back to normal.
[/LIST]

When I encode the video with mencoder using avi, wmv or mp4 containers and lavc codecs (msmpeg4, msmpeg4v2, mpeg4, h263p, wmv1, wmv2, H264) the problem experienced is #2. When I further convert it to mkv with mkvtoolnix, the problem experienced is #1.

The commands I' using are these:

```
mencoder source.avi -o output.avi -oac mp3lame &#8722;lameopts fast:preset=standard -ovc lavc -lavcopts vcodec=msmpeg4v2:vbitrate=1200
```

```
mencoder source.avi -o output.wmv -oac lavc -lavcopts acodec=wmav1:abitrate=128 -ovc lavc -lavcopts vcodec=wmv1:vbitrate=1200
```

```
mencoder source.avi -o output.mp4 -oac lavc -lavcopts acodec=libfaac:abitrate=128 -ovc lavc -lavcopts vcodec=libx264:vbitrate=1200
```

I have some original mp4 videos downloaded from my ISP video portal that plays perfectly. The video format is AVC1, the video codec FFH264 and the audio codec is FAAD. So I tried to re-encode my videos to a similar format using libx264 and libfaac codecs, but it takes a long time to encode and the resulting video format is not AVC1 but H264. Besides, it also suffers from problem #2.

So, I'm wondering what I'm doing wrong and how can I re-encode the video to get AVC1 format or something else that plays well with Miro (gstreamer)?

---

