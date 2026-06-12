---
title: "video editing software"
date: 2008-02-18
forum: Multimedia &amp; Video
---

### Post by foug on 2008-02-18
What is some good video editing software for linux? Free preferably. I need to merge 4 seperate video files into one.

---

### Post by chipants on 2008-02-19
don't have too much experience with them, but kino is highly regarded by some. also, there is the 'open movie editor'. both are in gutsy repositories.

---

### Post by erginemr on 2008-02-19
+1 to **kino**, but it is more like towards video camera capturing:
[http://www.kinodv.org/](http://www.kinodv.org/)

Try **avidemux** too, which is also in the repositories:
[http://fixounet.free.fr/avidemux/](http://fixounet.free.fr/avidemux/)

If you don't bother installing and loading KDE libraries, **kdenlive **is also a promising application:
[http://www.kdenlive.org/](http://www.kdenlive.org/)

---

### Post by vanadium on 2008-02-19
If you just want to combine/split/convert video's (linear video editing), then avidemux will be fine.

---

### Post by pwn on 2008-02-19
If you want to combine 4 videos into one... Lets say they're named 1.avi 2.avi 3.avi and 4.avi ...

Just type this in Terminal

```
mencoder -oac copy -ovc copy 1.avi 2.avi -o temp1.avi && mencoder -oac copy -ovc copy temp1.avi 3.avi -o temp2.avi && mencoder -oac copy -ovc copy temp2.avi 4.avi -o final.avi && rm temp*.avi
```

---

### Post by vanadium on 2008-02-19
mencoder is an efficient way to do it, except that the videos need to be exactly the same format (codec, frame size, rate, audiocodec, ...). If not, you need to convert to a common format. That can also be done with mencoder on the command line, or with the graphical tool avidemux.

If you want to use mencoder, an much easier, faster and space efficient way is:
mencoder -oac copy -ovc copy *.avi -o final.avi

You can also explicitly name all files to be combined instead of *.avi if the files should not be in alphabetical order.

1.avi 2.avi -o temp1.avi && mencoder -oac copy -ovc copy temp1.avi 3.avi -o temp2.avi && mencoder -oac copy -ovc copy temp2.avi 4.avi -o final.avi && rm temp*.avi

---

### Post by foug on 2008-02-22
thanks everyone :):KS

---

