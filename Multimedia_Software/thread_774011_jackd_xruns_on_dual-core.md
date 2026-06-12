---
title: "jackd xruns on dual-core"
date: 2008-04-29
forum: Multimedia Software
---

### Post by hendrikwout on 2008-04-29
Hi,
I have installed hardy 32-bit on a brand new dell xps m1530 laptop. It has a dual-core.

I have an little usb audio interface (griffin imic) which I use for jackd.

When I start jackd with: 
/usr/bin/jackd -R -P99 -dalsa -r44100 -p256 -n2 -D -Chw:1 -Phw:1 -S

I get some some xruns every 1-20 seconds. Which is unacceptable off course.

Then I thought it might be caused by dual-core. and indeed, when I turned off the dual-core feature in the bios of my laptop, I didn't have any xruns anymore.

Anyone has a similar problem or knows a solution? I would really like to use all power of my laptop.
(I allready heard of jackdmp, but it didn't compile)

Greetings

---

### Post by hendrikwout on 2008-05-07
I did some more testing and I can only confirm it: when I turn on multi-core, the performance of jackd is bad with lots of xruns and jack audio apps that zombify.

---

### Post by warbread on 2008-05-07
This is something that I'll have to look into when I get home.  I've got an Intel dual core laptop running Hardy that has been having trouble with xruns since upgrading.  My desktop, also a dual core (AMD) is running Gutsy and isn't having any problems at all.

---

