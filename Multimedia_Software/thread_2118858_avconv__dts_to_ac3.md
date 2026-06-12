---
title: "avconv : dts to ac3"
date: 2013-02-22
forum: Multimedia Software
---

### Post by bastobuntu on 2013-02-22
Hi!

lately im converting some mkv's which contain several dts streams to ac3 and i'm having little trouble with it.

trying it in one step the process is often killed. i experienced a decreasing fps value while "reencoding" and after a couple of minutes it just says "Getötet" (or killed in english)

the (one-step) command:
```
avconv -i input.mkv -vcodec copy -acodec ac3 -ac 6 -ab 640k -scodec copy output.mkv
```misteriously, when i first reencode the audio streams and copy the subtitles to an extra-mkv prior to rebuilding the mkv with the video-stream from the first file it is working like a charm... (?)

```
avconv -i input.mkv -vn -acodec ac3 -ac 6 -ab 640k -scodec copy -map 0:1 -map 0:2 -map 0:3 ac3.mkv (2 audiostreams + one subtitle stream)
avconv -i input.mkv -i ac3.mkv -vcodec copy -acodec copy -scodec copy -map 0:0 -map 1 output.mkv
```what am i doing wrong, or is it a bug? i would like to do that in one step ;)

greetings

---

