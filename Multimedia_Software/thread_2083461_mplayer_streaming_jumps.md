---
title: "mplayer streaming jumps"
date: 2012-11-12
forum: Multimedia Software
---

### Post by raggiotralenuvole on 2012-11-12
Hi, 

sorry for my bad english, I'm italian

When I try to open a streaming video with mplayer ([http://www.rai.tv/dl/RaiTV/programmi/media/ContentItem-e43b8900-ab5c-47f5-b190-9f570923e590.html](http://www.rai.tv/dl/RaiTV/programmi/media/ContentItem-e43b8900-ab5c-47f5-b190-9f570923e590.html) ), the stream jumps frequently

Here is the terminal output:

> Cache empty, consider increasing -cache and/or -cache-min. [performance issue]
[]("http://www.rai.tv/dl/RaiTV/programmi/media/ContentItem-e43b8900-ab5c-47f5-b190-9f570923e590.html")

---

### Post by andrew.46 on 2012-11-12
You could try increasing the cache value:

```

-cache <kBytes>
    This option specifies how much memory (in kBytes) to use 
     when precaching a file or URL. Especially useful on slow media.

```

or adding in a cache-min value:

```

-cache-min <percentage>
   Playback  will  start when the cache has been filled up to 
   <percentage> of the total.

```

Perhaps something like:

```
-cache 8000 -cache-min 80
```

Do you have a direct link for this stream?

---

### Post by raggiotralenuvole on 2012-11-17
> Do you have a direct link for this stream?

[http://mediapolisvod.rai.it/relinker/relinkerServlet.htm?cont=Ca9BwpPpPlussSWkS8eeqqEEqual](http://mediapolisvod.rai.it/relinker/relinkerServlet.htm?cont=Ca9BwpPpPlussSWkS8eeqqEEqual)

---

### Post by andrew.46 on 2012-11-17
Puzzling, even increasing the cache values to outlandish levels the cache warnings continue. Not sure about this one....

---

### Post by andrew.46 on 2012-11-17
Some suggestions as to what the problem may be can be found here:

[http://lists.mplayerhq.hu/pipermail/mplayer-users/2011-August/083153.html](http://lists.mplayerhq.hu/pipermail/mplayer-users/2011-August/083153.html)

Of course this particular stream is an mp4 one...

---

### Post by SeijiSensei on 2012-11-18
I watched some of this stream in SMPlayer with a cache of 1 megabyte without any skipping.  However I'm using [mplayer2]("http://www.mplayer2.org/") as the engine.  I could even skip ahead half way into the video without any issues.

---

### Post by raggiotralenuvole on 2012-11-19
> Some suggestions as to what the problem may be can be found here:

[http://lists.mplayerhq.hu/pipermail/...st/083153.html]("http://lists.mplayerhq.hu/pipermail/mplayer-users/2011-August/083153.html")

Of course this particular stream is an mp4 one... 	

thanks...it seems a bug

> I watched some of this stream in SMPlayer

I tried SMPlayer and it works very well!!
Thanks!

---

### Post by andrew.46 on 2012-11-21
> **raggiotralenuvole said:**
> I tried SMPlayer and it works very well!!


Great news! Mind you SMplayer is simply a frontend for the commandline MPlayer... Anyway it is all working :)

---

