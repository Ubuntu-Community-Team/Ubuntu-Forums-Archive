---
title: "kernel 2.6.35-999 (daily) is very good"
date: 2010-06-15
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by QQi on 2010-06-15
this is my results about kernel 2.6.35-3 and 2.6.35-999(daily) 64 bit

my labtop : acer aspire 5583 

[COLOR=Red]**kernel 2.6.35-3**[/COLOR]
[http://upic.me/i/5d/2.6.353.png](http://upic.me/i/5d/2.6.353.png)
[[IMG]http://upic.me/i/5d/2.6.353.png[/IMG]]("http://upic.me/show.php?id=198ac098d7026d714129f9083296a86b")

[COLOR=Red]**ram in used on startup**[/COLOR]
[http://upic.me/i/q4/ram2.6.353.png](http://upic.me/i/q4/ram2.6.353.png)
[[IMG]http://upic.me/i/q4/ram2.6.353.png[/IMG]]("http://upic.me/show.php?id=eb3f6291e2fc50b527136113644b002e")  


[COLOR=DarkGreen]**kernel 2.6.35-999 (daily)**[/COLOR] [http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/daily/current/")
[http://upic.me/i/h6/2.6.35999.png](http://upic.me/i/h6/2.6.35999.png)
[[IMG]http://upic.me/i/h6/2.6.35999.png[/IMG]]("http://upic.me/show.php?id=818611e316ba662f24bc27a65b4cf53f")

[COLOR=DarkGreen]**ram in used on startup**[/COLOR]
[http://upic.me/i/16/ram2.6.35999.png](http://upic.me/i/16/ram2.6.35999.png)
[[IMG]http://upic.me/i/16/ram2.6.35999.png[/IMG]]("http://upic.me/show.php?id=19864984f61e633d309835e6d5d1a8f1")

---

### Post by questioning on 2010-06-16
whats the point ?

---

### Post by Old Marcus on 2010-06-16
I do believe he's trying to squeeze more power out of his top of the range abacus.

---

### Post by questioning on 2010-06-16
no i believe, hes trying to squeeze more !!!free!!! ram out of it.

cause as long as the random used ram number is low, everyone is happy!

---

### Post by Tanakornp on 2010-06-16
yes he want to use kernel memory a little.

---

### Post by bruno9779 on 2010-06-16
3.5 less memory usage seems very good to me too.

---

### Post by questioning on 2010-06-16
> **bruno9779 said:**
> 3.5 less memory usage seems very good to me too.

thats not what you can read out of those screenshots.

you can read 2 different numbers, one is higher, one is lower.

you dont know if, the higher number includes reserved ram, if theres been more preloaded, etc.

this screenshots are completely irrelevant.

---

### Post by philinux on 2010-06-16
Vanilla Mav 64 bit.
There is something going on because yesterday a clean boot showed 1.1 gig of memory used in free with nothing extra running. On update and reboot it was then around 400 meg.

---

### Post by andrewabc on 2010-06-16
I guess the question is why the ram reported there is so much lower. Is the calculation just different? Or is there actually less being put into ram at startup? If less, then what is being left out? garbage? stuff not deemed important for ram on startup?

---

### Post by cariboo on 2010-06-16
System monitor seems to be rounding down memory usage here, using free -m I get:

```
free -m
             total       used       free     shared    buffers     cached
Mem:          2008       1975         32          0         24        912
-/+ buffers/cache:       1038        969
Swap:         1906          0       1906
```

While system monitor shows 1Gb being used.

---

### Post by Nr90 on 2010-06-16
Is it possible to add a PPA to get the daily kernel?
I tried "https://launchpad.net/~kernel-ppa/+archive/ppa" but that didn't give me the daily one, just some kernels intended for lucid.

---

### Post by bladerunner6 on 2010-06-16
there is a pre-proposed one for maverick but doesnt look uptodate to me
[https://launchpad.net/~kernel-ppa/+archive/pre-proposed](https://launchpad.net/~kernel-ppa/+archive/pre-proposed)

---

### Post by arpanaut on 2010-06-16
[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)

Not sure of the PPA to add to get it regularily, but if you want to mess with debs.
Have at it, the debs are working for me.

---

