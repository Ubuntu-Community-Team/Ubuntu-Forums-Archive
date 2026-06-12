---
title: "proxy troubles"
date: 2010-03-05
forum: Networking &amp; Wireless
---

### Post by linuxluver on 2010-03-05
I've recently installed 9.10 on my Acer Aspire One D250 on a separate partition. I have tried to install things via apt-get/synaptic/Software Center, but every time I try or reload my repository lists, it just gives me the following:
```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-proposed/main/binary-i386/Packages.gz  Cannot initiate the connection to 808:80 (0.0.3.40). - connect (22: Invalid argument)
```over and over again.

I use a proxy at home, but not at work, so I am very annoyed. And the strange thing is, regular internet does work, and I was using my proxy to get packages DURING the install (from the Internet of course). Please help.

Oh, and I use a local proxy server with IP 192.168.1.99:808.

---

