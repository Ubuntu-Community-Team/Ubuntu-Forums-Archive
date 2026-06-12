---
title: "what's wrong? ffmpeg encoding mulit audio tracks"
date: 2012-04-22
forum: Multimedia Software
---

### Post by mimihu88 on 2012-04-22
Hi!
source is a mkv file with 1 video stream and 2 audio streams (0:0 video,0:1 ac3 English,0:2 dts Chinese)
output would be a mp4 file
below is the command-line used

```
$ ffmpeg -i source.mkv  -map 0:0 -c:v:0 libx264 -map 0:1 -c:a:1 libfaac -aq 128k -ac 2 -map 0:2 -c:a:2 ac3 -aq 448k -ac 6 output.mp4 
```

what I want is to encode the 2 audio streams with different encoder,for example,one with libfaac another with ac3 ;
the problem is ffmpeg always encode the two streams only with one encoder ,it is ac3 in my case.

anything wrong?

thanks for help!

---

### Post by ron999 on 2012-04-22
> **mimihu88 said:**
> 
anything wrong?

Hi
Maybe it's not possible to do the job in 1 pass...
```
ffmpeg -i source.mkv -c:v libx264 -c:a libfaac -b:a 128k -ac 2 output.mp4 && \
ffmpeg -i source.mkv -map 0:2 -c:a ac3 -b:a 448k -ac 6 audio.ac3 && \
MP4Box output.mp4 -add audio.ac3
```

Or maybe I'm wrong.:p
 :lolflag:

---

### Post by mimihu88 on 2012-04-23
> **ron999 said:**
> Hi
Maybe it's not possible to do the job in 1 pass...
```
ffmpeg -i source.mkv -c:v libx264 -c:a libfaac -b:a 128k -ac 2 output.mp4 && \
ffmpeg -i source.mkv -map 0:2 -c:a ac3 -b:a 448k -ac 6 audio.ac3 && \
MP4Box output.mp4 -add audio.ac3
```

Or maybe I'm wrong.:p
 :lolflag:

Thank you but it can be easily done by HandBrake,I just want to know whether or not FFmpeg can do it and how.

---

