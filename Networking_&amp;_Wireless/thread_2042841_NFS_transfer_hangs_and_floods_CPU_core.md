---
title: "NFS transfer hangs and floods CPU core"
date: 2012-08-15
forum: Networking &amp; Wireless
---

### Post by johnnyslogan on 2012-08-15
Hello everybody!

I am enjoying Ubuntu 12.04 on both laptops and a desktop. On the laptops, running 32-bit, NFS works fine and dandy. On my desktop, running 64-bit, it is not possible to transfer a large file from the NFS-server to my desktop. 

The transfer window in Nautilus simply hangs after a couple of megabytes. I have searched and searched and found several posts around the internet and in this forum, discussing issues with NFS on Ubuntu. One of the threads suggested trying the 'async' instead of 'sync' option as one of the NFS parameters. That doesn't help in my case. 

I have gotten a bit of expert help, suggesting that I installed a program called nmon. I did that. And when I use that to look at the CPU utilization, doing an attempt at NFS-file transfer, one of my four CPU-cores gets all flooded with w's meaning waiting. When I cancel the transfer, the core returns to normal.

So my guess is, that data is received over the network - my desktop is on cable by the way - but the CPU, an Intel i5, is having a hard time putting the data down on my drive. 

I have the same NFS-configuration on my desktop as on my laptops - automounting NFS-shares and stuff. I'm pretty sure, it's not an NFS-configuration problem, but then again - who knows?

Any thoughts would be much appreciated.

Best regards

**Quick update: Just tried with Samba, no transfer problems. I would like to use NFS though.**

---

### Post by horchi on 2012-09-14
Hi, I had exact the same Problem since I updated a client to 12.04. 
After many tests I turned out the the mount option vers=3 workaround the problem. Actually it works fine with the mount options "udp,vers=3,bg,soft,intr"
It looks like bug on NFS client side :(
Best regards, Jörg

---

