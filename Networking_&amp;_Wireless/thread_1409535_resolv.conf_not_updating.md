---
title: "resolv.conf not updating"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by sleepyjon on 2010-02-17
I've found my resolv.conf does not get updated when connecting to an open wireless network. 

I'm using:
```

wicd version 1.6.1
$ uname -a
Linux GNUMachine 2.6.32 #1 SMP Mon Jan 25 18:31:32 PST 2010 x86_64 GNU/Linux

```

I've tried manually connecting with the command line as well as with wicd, with the same results. I've also tried with an older kernel. As a work around I've done:

```

sudo rm /etc/resolv.conf
sudo touch /etc/resolv.conf

```

Has anyone else run into this problem? It seems to only be an issue with open networks, however I don't connect very often to protected networks so it is possible I just didn't notice it and the networks all were using the same DNS.

---

