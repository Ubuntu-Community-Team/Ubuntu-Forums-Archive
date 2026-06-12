---
title: "simple video cropping and stiching"
date: 2010-10-06
forum: Multimedia Software
---

### Post by Hakimjo on 2010-10-06
Hello,

I am looking for a simple tool that would allow me to stitch together short mpeg files or to cut out unwanted sequences of files, without having to use a heavy video editing programme like OpenShot.

If it can do the same for audio files (mp3) and possibly convert between formats, even better !

Thanks for the hints

j

---

### Post by FakeOutdoorsman on 2010-10-06
The formats in a .mpg container are usually *cat* friendly and will allow you to combine your various scenes into one continuous video:
```
cat input1.mpg input2.mpg input3.mpg > combined.mpg
```
...and FFmpeg can be used to cut out sections:
```
ffmpeg -ss 43 -i input.foo -t 00:01:23.00 -vcodec copy -acodec copy output.foo
```
This command will skip the first 43 seconds of the input and then make an output that is 1 minute and 23 seconds in duration.  The *-ss* and *-t* options can take seconds as a value, as *-s* is using in the example, or *hh:mm:ss.ms* as *-t* is using.

---

