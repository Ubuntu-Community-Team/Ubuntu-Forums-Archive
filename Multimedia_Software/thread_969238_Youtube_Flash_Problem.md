---
title: "Youtube Flash Problem"
date: 2008-11-03
forum: Multimedia Software
---

### Post by bg11 on 2008-11-03
Recently, many youtube videos are displaying the error:

```

We're sorry, this video is no longer available.

```

This seems to only occur for Linux users though.  Does anyone have a work around short of downloading the videos?  Anyone know more about this problem?

I'm running adobe flash version 10.0.0.569.

---

### Post by tuxxy on 2008-11-03
Could it be its removed? do you have a link to test it in windows

---

### Post by bg11 on 2008-11-03
Yeah, videos which play fine in windows are unavailable when using linux.  I don't think I'm the only linux user who's noticed this.  There don't seem to be any workarounds yet.  I was hoping that someone here could shed light on the problem.

---

### Post by lukjad on 2008-11-03
I've seen that sometimes if you refresh the page a few times it will come back. Also if you take this YouTube video for example:

```
http://www.youtube.com/watch?v=GmgDGHgF5e&feature=PlayList&p=11f1t5t5ww568d&index=31
```
(Note that this is only an example, not a real YouTube video, at least, to my knowledge. ;))

We can strip away everything after and including the first &. Like so:

```
http://www.youtube.com/watch?v=GmgDGIHasgI
```

This sometimes helps Firefox read the web page better.

Hope this helps!

---

### Post by bg11 on 2008-11-23
**Solved.**

The problem was something to do with flash version 10, youtube videos work fine now that I've gone back to flash 9.

---

