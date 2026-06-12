---
title: "mplayer cache size for playing mms?"
date: 2008-03-28
forum: Multimedia &amp; Video
---

### Post by chunchengch on 2008-03-28
The default cache setting of Mplayer is 8192 Kbs, but it keeps buffering while playing mms streams, so I wonder how much cache is enough to play mms streams fluently? thanks!

---

### Post by warp99 on 2008-03-29
Well the buffering is due to you connection not being fast enough. I would double the cache to see if that would help.

You can always use the -dumpstream option and stream the entire file so you can watch it without buffering pauses. All you need is the url of the mms stream:

```
mplayer mms://name_of_your_stream.wma -dumpstream -dumpfile my_stream.wma 
```

---

