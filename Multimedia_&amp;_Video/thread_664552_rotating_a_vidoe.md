---
title: "rotating a vidoe"
date: 2008-01-11
forum: Multimedia &amp; Video
---

### Post by bigmonmulgrew on 2008-01-11
I want to rotate a video 90 degrees, taken on a phone. Basically I want it the right way up. What software and how do I do it

---

### Post by ron999 on 2008-01-11
Hi
Avidemux has a 'rotate' setting.

But if you don't mind using command-line, this will work instead, and it's quick:-

```
mencoder -ovc lavc -lavcopts vcodec=mjpeg -vf rotate=1 -oac copy filename.avi -o newfilename.avi
```

(use your own file instead of filename.avi)
8-)

---

### Post by camij on 2008-01-30
And if i want to rotate the video 180 degrees then what should i change in the command-line?
thanx in advance

---

### Post by andrew.46 on 2008-02-06
Hi,

 Finally one that I can answer:

> **camij said:**
> And if i want to rotate the video 180 degrees then what should i change in the command-line?
thanx in advance

> rotate[=<0-7>]
 Rotates the image by 90 degrees and optionally  flips  it.   For values  between  4-7 rotation is only done if the movie geometry  is portrait and not landscape.

             0    Rotate by 90 degrees clockwise and flip (default).
             1    Rotate by 90 degrees clockwise.
             2    Rotate by 90 degrees counterclockwise.
             3    Rotate by 90 degrees counterclockwise and flip.
Straight from the mplayer man pages.

     Andrew

---

