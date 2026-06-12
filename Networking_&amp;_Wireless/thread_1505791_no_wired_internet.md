---
title: "no wired internet"
date: 2010-06-09
forum: Networking &amp; Wireless
---

### Post by qwertyuio on 2010-06-09
I have no wired or wireless internet after installing 10.04 on a dell e1505 laptop.

---

### Post by qwertyuio on 2010-06-09
> **qwertyuio said:**
> I have no wired or wireless internet after installing 10.04 on a dell e1505 laptop.

:confused:

---

### Post by Iowan on 2010-06-09
Moved to Networking & Wireless

The dell e1505 sounds familiar - there may be another thread you can Search for. Otherwise, from a terminal (Applications>Accessories>Terminal) check **ifconfig -a** - if no IP addresses show, check **sudo lshw -C network** - post results if possible. (help on doing that is only a request away ;) )

Link to your [other thread]("http://ubuntuforums.org/showthread.php?t=1498606").

---

