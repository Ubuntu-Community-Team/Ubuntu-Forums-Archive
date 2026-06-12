---
title: "Cannot Play 2 webcams at same time?"
date: 2013-01-20
forum: Multimedia Software
---

### Post by honeybear on 2013-01-20
Hello,

If I remotely watch 2 webcams at the same time, one is green. Is it because v4l2 cannot process 2 webcams at the same time?

It should really be possible in my opinion.

Sincerely,

$VI can be video1, video0, video2,... whatever I would like. 

webcam.sh does use mplayer using :
  mplayer $ESD -tv device=/dev/video$2 tv://

```

 ssh -X $IP  -C sh ~/scripts/webcam.sh -webcam $VI

```

---

