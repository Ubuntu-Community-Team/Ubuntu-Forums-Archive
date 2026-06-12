---
title: "is there an app to compare cisco configs?"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by SmarterThanMyPhone on 2009-11-24
I use a program on my windows machine at work called hyperconf, it lets me pull up 2 router configs and compare them, color's the differences, pretty cool, and useful program. Is there anything like that for ubuntu? I've tried installing hyperconf with wine, but had no success. I'm using 9.04.
Thanks :)

---

### Post by Lord_ on 2009-11-24
Hi, you can use "diff" to do this. It will compare two text files and report on the difference.

do a man diff for information and options, but its basically:

diff {filename1} {filename2}

---

### Post by SmarterThanMyPhone on 2009-11-24
I'll give that a shot, I dont think it'll be a problem for a pair of smaller configs, but out of a voice router that will probably have a pretty significant amount of output.

---

### Post by SmarterThanMyPhone on 2009-11-27
yea thats not very efficient lol, it'll do for now since I had nothing before, but I'm still looking for a better solution. Does anyone know of a non-opensource linux program for cisco routers?

---

