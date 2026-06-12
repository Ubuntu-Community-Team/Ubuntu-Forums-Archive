---
title: "Joining  .rmvb files together"
date: 2010-08-30
forum: Multimedia Software
---

### Post by Amgad elsaiegh on 2010-08-30
I need a piece of software that could join  .rmvb files together as one file , i have tried Avidemux  and Lives , but none of them worked :confused:

Any body can help please ?

---

### Post by Amgad elsaiegh on 2010-08-31
no answer yet ?!!! :(

---

### Post by Amgad elsaiegh on 2010-08-31
looks like the thread is dead or the community have no answer

---

### Post by bark50 on 2010-08-31
I've used HJSplit for Java to join files:  [http://www.freebyte.com/hjsplit/#java]("http://www.freebyte.com/hjsplit/#java")  I've never tried using it specifically with rmvb files, though.

One trick to using HJSplit successfully is to properly rename the files before joining them.  For example, lets say you have movie1.rmvb, movie2.rmvb, and movie3.rmvb to join.  You want to rename them movie.rmvb.001, movie.rmvb.002, and movie.rmvb.003 before splicing them together with HJSplit.

---

### Post by Amgad elsaiegh on 2010-09-01
thanks bark50 , i,ll give a try now

---

### Post by FakeOutdoorsman on 2010-09-01
Using the *cat* command worked on the few .rmvb samples I had, but it may not work for your videos and I know next to nothing about RealMedia formats:
```
cat input1.rmvb input2.rmvb > combined.rmvb
```
The input videos were the same frame size (576x320).

---

