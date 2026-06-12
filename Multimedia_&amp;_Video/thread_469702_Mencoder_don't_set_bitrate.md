---
title: "Mencoder don't set bitrate"
date: 2007-06-10
forum: Multimedia &amp; Video
---

### Post by edric on 2007-06-10
What's wrong in this code???
When i check the 'finish product' with avinfo i get about 900 kbps.. i'm getting crazy..

```

mencoder ./video.vob -vf crop=704:432:8:70,scale=640:360 -sws 9 -mc 0 -oac copy -aid 128 -ovc xvid -xvidencopts bitrate=3000:pass=2:me_quality=6:trellis:chroma_me:chroma_opt:hq_ac:vhq=4:bvhq=1:threads=2 -passlogfile /tmp/xvid2pass.log -o ./video.avi

```

In the first pass i use the turbo option

Ubuntu 64 bit, xvid 1.1.2, mencoder 1.0rc1

---

