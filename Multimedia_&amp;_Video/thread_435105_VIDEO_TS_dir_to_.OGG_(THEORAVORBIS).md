---
title: "VIDEO_TS dir to .OGG (THEORA/VORBIS)"
date: 2007-05-06
forum: Multimedia &amp; Video
---

### Post by Sockerdrickan on 2007-05-06
VIDEO_TS dir to .OGG (THEORA/VORBIS)

Can this be done (Bad question), and can I select what audio track to be used?
Please tell me how :)

---

### Post by Sockerdrickan on 2007-05-06
Please help <=(

---

### Post by Sockerdrickan on 2007-05-07
C'mon this can't be a hard question <=(

---

### Post by Sockerdrickan on 2007-07-05
If anyone wonders, use Thoggen. ;)

---

### Post by chrisbuntu on 2007-09-19
It took me a while, but I've figured this one out using just the command line.  You'll need ffmpeg2theora. ```
sudo apt-get install ffmpeg2theora
```
The following line is specific to Monty Python and the Holy Grail (the main feature is title 1) but I'll explain how to customize it.

```
cat VTS_01_1.VOB VTS_01_2.VOB VTS_01_3.VOB VTS_01_4.VOB VTS_01_5.VOB | ffmpeg2theora -o "The Holy Grail.ogg" --audiostream 4 -
```

replace ```
VTS_01_1.VOB VTS_01_2.VOB VTS_01_3.VOB VTS_01_4.VOB VTS_01_5.VOB
``` with the video files you want to convert- and they need to be in the right order.
replace ```
The Holy Grail.ogg
``` with the name you want for your video and the 4 with the audiotrack you wish to use

---

### Post by Sockerdrickan on 2007-09-20
Ok that's a good way of doing it with bash
If you guys want a gui then use Thoggen

---

### Post by orange2k on 2007-09-20
Thoggen is pretty good, but I couldn figure out how to make the resulting video to be of exact size to my liking - when I encode to XVID in two passes, your resulting video will be exactly how you choose - thats why I still prefer to encode to XVID, and its a free codec, too...

---

