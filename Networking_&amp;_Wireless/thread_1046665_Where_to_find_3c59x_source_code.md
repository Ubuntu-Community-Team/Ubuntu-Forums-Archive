---
title: "Where to find 3c59x source code?"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by chconnor on 2009-01-21
Hi there, looking to do a hack similar to that discussed in:
[http://ubuntuforums.org/showthread.php?t=318586](http://ubuntuforums.org/showthread.php?t=318586)

...but I'm new to this and don't know where to get 3c59x.c... It's not in /usr/src... i'm sure this is an easy one but I don't know where to go for it.

We're running 8.04 server.

Any pointers welcome, thanks,
-c

---

### Post by chconnor on 2009-01-21
Aha:

sudo apt-get install linux-source
sudo apt-get install bzip2
bzip2 -d [bz2 filename]
tar -tf linux-source-[etc] | grep 3c59x

shows:

linux-source-2.6.27/drivers/net/3c59x.c

---

