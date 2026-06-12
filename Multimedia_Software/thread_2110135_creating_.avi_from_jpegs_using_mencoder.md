---
title: "creating .avi from jpegs using mencoder"
date: 2013-01-29
forum: Multimedia Software
---

### Post by grey1beard on 2013-01-29
I've tried the following code but it doesn't output an .avi file.

> mencoder -ovc copy -mf w=640:h=480:fps=6:type=jpg 'mf://*.jpg' -o snap.avi

I've got a small test set of jpegs in /home/Pictures directory, so I opened Terminal, cd to /Pictures, then ran memcoder with the above line of code, and got the following result -

> *grey1beard*:~/Pictures$ mencoder -ovc copy -mf w=640:h=480:fps=6:type=jpg 'mf://*.jpg' -o snap.avi
MEncoder svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team
success: format: 16  data: 0x0 - 0x0
MF file format detected.
[mf] search expr: *.jpg
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.


Most grateful for help in telling me what I'm doing wrong.
John

---

### Post by grey1beard on 2013-01-29
I  may have  found the answer by using
> *grey1beard*:~/Pictures$ mencoder mf://*.jpeg -mf w=800:h=600:fps=25:type=jpeg -ovc lavc \-lavcopts vcodec=mpeg4:mbd=2:trell -oac copy   -o output.avi

It might have been the use of jpg instead of jpeg in the first trial that tripped me up.

We'll see.
John
EDIT yes, runs perfectly.

---

