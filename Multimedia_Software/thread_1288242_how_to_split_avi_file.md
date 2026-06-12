---
title: "how to split avi file"
date: 2009-10-11
forum: Multimedia Software
---

### Post by sn0m on 2009-10-11
Hi guys
I just can't get my head around to split an avi file to a specific time in two parts with avi split.
I have a home video that I would like to cut it at 6minutes59sec. The whole video is 20min14sec.
Could any of you gentle souls tell me how to do that as I'm struggling to get it done.
Kind regards
Sokol

---

### Post by Albert Clarke on 2009-10-11
I feel you could a google search on this to get lots of information, i had read an article that i am pasting the link for reference. Thanks. [http://www.solveigmm.com/HowTo/how-to-split-avi-file-with-video-splitter](http://www.solveigmm.com/HowTo/how-to-split-avi-file-with-video-splitter)

---

### Post by mister_playboy on 2009-10-11
I have a similar question.  I've figured out how to do this with Cinelerra, but the output file I get looks like crap... is there a way to cut out a section of video without rerendering it?  Could this been done with Mencoder?

The program linked above looks like it would work, but I can't get it to install in WINE.

---

### Post by andrew.46 on 2009-10-12
Hi sokol,

> **sn0m said:**
> I have a home video that I would like to cut it at 6minutes59sec. The whole video is 20min14sec.

I have not used avisplit very much but I suspect the following should serve:
```

avisplit -i myfile.avi -o split.avi -t 00:00:00-00:06:59,00:07:00-00:20:14
```

and certainly in a few tests on my own system this worked well.

Andrew

---

### Post by vinutux on 2009-10-12
Try openshot or pitivi video editors ....

---

