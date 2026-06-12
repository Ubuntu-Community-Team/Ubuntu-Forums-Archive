---
title: "Best clustering solution for Linux"
date: 2009-12-04
forum: Networking &amp; Wireless
---

### Post by badkuk on 2009-12-04
Hi peeps,
 
   There seems to be quite a lot of clustering software available for Linux: Beowulf, Piranha, UltraMonkey, LinuxHA etc., not to mention the commercial ones.

   At the risk of starting a fire here, can anyone tell me which one is the best/more widely used? Kindly add your reasons for saying so as well.

   While i'm familiar with the concept of clusters, i really can't say that i've gone down and dirty with the technology...and since i got time to kill, and a few pcs lying around...

tia

---

### Post by Iowan on 2009-12-04
[Here]("https://help.ubuntu.com/community/Clustering") is a help page for clustering. It doesn't discuss ALL the options, but might be a good place to start your research.

---

### Post by Yoann Juet on 2009-12-05
> **badkuk said:**
> While i'm familiar with the concept of clusters, i really can't say that i've gone down and dirty with the technology...and since i got time to kill, and a few pcs lying around...

LVS is a very robust solution. On my University, mission critical applications are using it : messaging nodes, web proxies and caches, reverse-proxies...  Keepalived (VRRP protocol) is perfectly suited for simple active/passive clusters, for instance a two nodes cluster for building a high-available firewall. If you need advanced services (i.e. shared disk/database), take also a look at heartbeat2.

---

