---
title: "Modem Octal a360 on Dapper Drake"
date: 2006-07-10
forum: Networking &amp; Wireless
---

### Post by Vnepomuceno on 2006-07-10
Hello, I followed this tutorial, [http://havox.no.sapo.pt/amedyn.html](http://havox.no.sapo.pt/amedyn.html) (it is in portuguese) to install my Internet (Sapo ADSL on modem octal a360) on Breezy Badger. Everything was ok until the release of Dapper Drake.
I've updated 5.10 to 6.06, and, since then, I don't have Internet.
I followed the same tutorial, and many other tutorials, and is the same.
Everything goes well on the instalation, but, when i'm trying to start the internet with:

```
$ sudo amstart.sh
```

It appears to me the following message:

```
 FATAL: Module crc32 not found.
Launching driver in normal mode…
FATAL: Module amedyn not found.
```

Can anybody help me?

---

### Post by Vnepomuceno on 2006-07-10
And so?
No one can help me?

---

### Post by aka_zedweb on 2006-11-22
Same problem here! On Ubuntu 6.10 Help anyone?

------

EDIT:Problem Solved
Used #uname -r and got the amedyn package for my kernel in .deb and everything is up and running. Can't remember the link, but I found it on this forum. Something that ends in .nr

---

