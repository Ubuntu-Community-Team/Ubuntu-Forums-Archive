---
title: "mplayer - Iterative Frame Capture"
date: 2012-01-12
forum: Multimedia Software
---

### Post by wbest on 2012-01-12
I need to write a line of mplayer to get jpegs from an mpeg file. However, I need to capture every 10th frame, not every frame. The problem is that mplayer, from what I've seen in the man files, can only capture every s seconds.

In the optimal case, I want it to work regardless of the video's frame rate. I know it should be possible for it to work if I knew the frame rate, but I want to make it work for all possible frame rates.

I've looked all over, but can't seem to find anything. Does anyone have any advice?

---

### Post by wbest on 2012-01-13
I figured it out.

You have to use the -vf tag and say something like:

```
mplayer -vf framestep=10 -vo jpeg:outdir=fooDir foo.mov
```

---

