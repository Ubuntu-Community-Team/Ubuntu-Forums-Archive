---
title: "Cancatinating .wmv help"
date: 2008-02-06
forum: Multimedia &amp; Video
---

### Post by Syndacate on 2008-02-06
Hey,

I just got a quick Q about .wmv

I'm trying to cancatinate 2 or more of them - and it's working fine - but the tracking is WAY off, like I'll click the middle and the slider will go to the end and it jumps 'n such (there's places where the tracker actually doesn't go - it just jumps over - but the video appears smooth.

I don't get what's going on, can anybody shed some light?

I'm using mencoder through the command prompt.

EDIT:
avimerge works great for .avi files - but from what I gathered there's some header on .wmv files which makes 'em a bit different to encode?

---

### Post by Syndacate on 2008-02-07
*bump

---

### Post by Syndacate on 2008-02-07
Blah, anybody?

---

### Post by andrew.46 on 2008-02-10
Hi,

I presume you are using the following syntax:

```
$ mencoder -ovc copy -oac copy -o joined.wmv file1.wmv file2.wmv
```

But if the files have each been encoded a little differently this will not work particularly well.

            Andrew

---

### Post by Syndacate on 2008-02-11
I didn't use the options and type "copy" twice - but yeah, that's what I used.

They are encoded the same, I know this simply because it's the same file split into 2 or more parts.

Like somebody thought it was too large in one piece or something.

---

