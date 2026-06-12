---
title: "3gp conv3rter 0.1"
date: 2007-03-29
forum: Multimedia &amp; Video
---

### Post by ar3ac on 2007-03-29
A pygtk frontend for ffmpeg to convert video files to 3gp format.

Here it is :

[http://cronicar3a.blogspot.com](http://cronicar3a.blogspot.com)

bye,

ar3ac

---

### Post by marklid on 2007-04-12
404 not found :confused:

---

### Post by jakev383 on 2007-04-14
> **ar3ac said:**
> A pygtk frontend for ffmpeg to convert video files to 3gp format.

Here it is :

[http://www.spcnet.it/areac](http://www.spcnet.it/areac)

bye,

ar3ac

Page not available... I'm interested in this!!!

---

### Post by ninthforce on 2007-04-15
tease :confused:

---

### Post by jakev383 on 2007-04-16
> **ninthforce said:**
> tease :confused:

I ended up following this guide to rebuild ffmpeg with the required codecs:
[http://blogger.rukker.org/2007/01/29/enable-mp3-and-amr-support-in-ffmpeg-ubuntu-edgy-eft/](http://blogger.rukker.org/2007/01/29/enable-mp3-and-amr-support-in-ffmpeg-ubuntu-edgy-eft/)
And then doing the conversion by hand:

```

ffmpeg -i video_file.mpg -s qcif -vcodec mpeg4 -acodec aac -ac 2 -ar 16000 -r 25 -ab 32 -y video_file.3gp

```

---

