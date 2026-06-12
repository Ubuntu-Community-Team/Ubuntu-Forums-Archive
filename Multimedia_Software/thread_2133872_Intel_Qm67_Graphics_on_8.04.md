---
title: "Intel Qm67 Graphics on 8.04"
date: 2013-04-09
forum: Multimedia Software
---

### Post by D0natell0 on 2013-04-09
Hi, 
For various reasons, I'm trying to build an Intel graphics driver to run on an Intel QM67 system but with Ubuntu 8.04.4 


Kernel: 2.6.24-32-generic

Intel 2010Q4 (from [www.01.org/linuxgraphics](www.01.org/linuxgraphics) designed for kernel 2.6.37, the oldest they provide)


 Basically, I've got other hardware depending on Ubuntu 8.04 as the manufacturer stopped supporting Linux at that point.


The question is am I wasting my time even trying this?
 Thanks in advance.

---

### Post by D0natell0 on 2013-04-09
I'm trying to build an Intel linux graphics driver and getting an error about an invalid package.

Kernel: 2.6.24-32-generic
Intel 2010Q4 (from [www.01.org/linuxgraphics]("http://www.01.org/linuxgraphics") designed for kernel 2.6.37, the oldest they provide)

When I run ./configure I get the error: 
```
Requested 'xorg-server >= 1.6' but version of xorg-server is 1.4.0.90
```

However, Synaptic says I've got v1.7, as does this:
```
sudo apt-cache show xutils-dev
Version: 1:7.2.ds2-1ubuntu1

```

Also, the abbreviated contents of "/usr/lib/pkgconfig/xorg-server.pc" are:
```
Name: xorg-server
Description: Modular X.Org X Server
Version: 1.4.0.90
```

So, I think my question is how do I get this driver to install? Why the discrepancy between these definitions of x server?
Thanks in advance.

---

### Post by mörgæs on 2013-04-09
Most developers prefer working on the latest kernel, but you chose an ancient one. May we hear why?

---

### Post by Yellow Pasque on 2013-04-09
There's a difference between X.org version and Xserver version. Xserver is a component of X.org, and you have have Xserver 1.4.90 while the driver requires 1.6.x, so you're SOL there.

> However, Synaptic says I've got v1.7
No, it says you have version 7.2 of xutils  (don't read the '1:' as part of the version number since it refers to packaging version only).

---

### Post by D0natell0 on 2013-04-10
Temüjin > Very helpful, Thanks.
mörgæs > Not helpful! If you *read the OP* "I've got other hardware depending on Ubuntu 8.04 as the manufacturer stopped supporting Linux at that point." Moderators should know better!

---

### Post by D0natell0 on 2013-04-10
I thought I'd try the Intel Linux Graphics GUI installer ([https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads)). It failed with this dependency error (see below):

Why does this installer complain about libglib2.0-0 missing, when it is clearly visible in synaptic?
:confused:


[IMG]http://i1276.photobucket.com/albums/y475/dmunro2020/IntelG-Screenshot_zps3edc9a7c.png[/IMG]

---

### Post by Yellow Pasque on 2013-04-10
Sorry, double post.

---

### Post by Yellow Pasque on 2013-04-10
You probably don't have a new enough version of libglib. Ubuntu 8.04 is not listed as supported by the GUI installer. 

> The question is am I wasting my time even trying this?
It would appear that way. You're trying to fit a square peg into a round hole...

---

