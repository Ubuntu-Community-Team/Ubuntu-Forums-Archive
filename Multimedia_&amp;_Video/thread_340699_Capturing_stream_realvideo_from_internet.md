---
title: "Capturing stream realvideo from internet"
date: 2007-01-17
forum: Multimedia &amp; Video
---

### Post by antelao on 2007-01-17
Hello. I'd like to download stream realvideo (rtps). But I'd like to capture only a middle part of the stream. I have found these options for mplayer: "&#8722;ss" and "&#8722;endpos" and tried this code:

```
mplayer -dumpfile soubor.rm -dumpstream rtsp://ct1.server.streaming.visual.cz/ct/high1/UdalostiP241106.rm -ss 00:41:58 &#8722;endpos 01:19:52
```

But unfotunately this didn't work. After this command the stream is beeing captured from the beginning and not from the time 00:41:58. It is probably connected with the fact that the stream isn't indexed and so the option -ss don't work. But I'm not sure.

The internet playing itself handels mplayer all right - when I click a link on internet, mplayer begins to play from the time 00:41:58. So I think is should be possible to capture this stream. Please, can anybody help me to save only the middle part of a strem? I'm using Kubuntu 6.06.1.

Thanx, jiri.

---

### Post by bé xíu on 2008-04-06
Try:

```
mencoder -oac copy -ovc copy "mms://202.67.154.138/Live_Free_Or_Die_Hard/Live_Free_Or_Die_Hard.wmv" -o "Live_Free_Or_Die_Hard.wmv"
```

---

