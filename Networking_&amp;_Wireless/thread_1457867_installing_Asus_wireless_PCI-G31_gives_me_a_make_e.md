---
title: "installing Asus wireless PCI-G31 gives me a make error"
date: 2010-04-19
forum: Networking &amp; Wireless
---

### Post by hugo-heykers on 2010-04-19
I have a pc installed with ubuntu 8.10 server edition.  It has to work as a router with 2 LAN-segments, one wired (this works) and the other wireless, acting as an AP. The PCI card has to have a fixed ip. Problem is that ubuntu 8.10 doesn't make this pci card with rt61 chipset, work out of the box.(as mentioned in some article) The pci card is ASUS PCI-G31
When i try to install the linux drivers "2009_0123_RT61_Linux_STA_v1.1.2.3" with the "make all" command, i get following error:
make:***/lib/modules/2.6.27-17server/build: No such file or directory. Stop
make:***[all] Error2
I already tried to fix it through a similar post thread of rt61...but without result.
My linux headers matches the linux kernel being 2.6.27-17
Does anyone has had some problem.
Thanks!!

---

### Post by chili555 on 2010-04-19
Do you have the package *build-essential* installed?

---

### Post by hugo-heykers on 2010-04-19
yes, i have the build-essentials installed also.  Problem did not go away.

---

### Post by chili555 on 2010-04-19
> My linux headers matches the linux kernel being 2.6.27-17Does it say 2.6.27-17-server?```
ls /usr/src
uname -r
```

---

### Post by hugo-heykers on 2010-04-20
when i do the command ls /usr/src, i get these two:
linux-headers-2.6.27-17     linux-headers-2.6.27-17-generic

---

### Post by hugo-heykers on 2010-04-20
the command uname -r gives me:
2.6.27-17-server

---

