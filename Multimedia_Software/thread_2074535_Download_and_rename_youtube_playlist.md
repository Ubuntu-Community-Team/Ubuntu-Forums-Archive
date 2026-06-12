---
title: "Download and rename youtube playlist"
date: 2012-10-21
forum: Multimedia Software
---

### Post by alfirdaous on 2012-10-21
Hello everybody

I am using frequently 2 youtube commands line:

Download a playlist:```
youtube-dl -f 35 http://www.youtube.com/playlist?list=PLAYLIST_CODE
```

Download a video and renaming:
```
youtube-dl -o INPUT.flv -f 35 http://www.youtube.com/watch?v=VIDEO_CODE
```


So how can I download a playlist and renaming on the same time like below??

```
video1.mp4 video2.mp4 video3.mp4 video4.mp4
```
I tried this command line:
```

for i in {001..003}; do youtube-dl -o video_$i.mp4 -f 18 http://www.youtube.com/playlist?list=PLfdtiltiRHWEjLi_X8RV7GBsCAHef45eJ ; done

```

It is downloading the same video 3 times.

Thx in advance

---

### Post by oldos2er on 2012-10-21
Closed. See [http://ubuntuforums.org/showthread.php?t=1850955](http://ubuntuforums.org/showthread.php?t=1850955)

---

