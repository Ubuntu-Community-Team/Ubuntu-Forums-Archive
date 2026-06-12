---
title: "Large file problem with Asus NX1101"
date: 2010-08-08
forum: Networking &amp; Wireless
---

### Post by kubusiowaty on 2010-08-08
Hello,

I've recently bought an Asus NX1101 Gigabit Ethernet PCI Card (ipg driver).
After plugging it in an doing some simple tests everything seemed fine until I've started copying files over 2GB from my Samba (or FTP) share to my Windows 7 desktop computer. After few seconds the network went down. After a restart the network was back but the problem still exists. Has anyone had a simmilar problem? I've searched over the internet but didn't find any usefull information.
I've tried different things like using other kernels but nothing helps.

My system is an Ubuntu 10.04 Server x86. 
Any suggestions or ideas are very welcome. 

PS. I've tried with another card like D-Link using a r8169 driver and everything was ok. Could it be a driver problem?

EDIT:
Any suggestions on ways of diagnosing this problem are also welcome. I've checked samba logs, messages, syslog and there was no info about any network problems. Where can I also check to get some more info? Any advices?

EDIT2:
After a while of testing I have new info:

1. After plugging the card to another PCI slot the problem starts after transferring about 7.5GB 
2. If I use generic-pae kernel, system hangs after the error, after using acpi=ht for this kernel (this machine is an 2.4GHz Penium IV Northwood, on a mobo with Intel 865GV Chipset) stops the crash. Using other kernel for example generic or 386 also doesn't end with a crash. Issuing /etc/init.d/networking restart after error, brings the interface to up and running state but gives such info while restarting:

RTNETLINK answers: No such process
SIOCDELRT: No such process

3. When the error occurs IP routes change. route -n shows that 2 routes have... disappeared

Has anyone got any ideas?

---

### Post by kubusiowaty on 2010-08-10
It seems the problem is solved :D
Changing the PCI slot gave me an idea that maybe this card has some IRQ setting problems.

So I've booted with acpi=off and voila. It works without a problem. Not a perfect solution but it works. I've tested it on different files, 2.5 GB, 8GB, 10GB (read and write) for a total of 50-60GB of transfer, no errors and crash free so far. Samba reads work nice: 50-60MB/s, writing is about 40-47MB/s.

---

### Post by anwmalos on 2010-11-01
Hello, I'm resurrecting this thread because I have the same problem with this NIC (link fails on big file transfers, so it needs to be stopped and started again), but the problem still exists on 10.10 (x64). The strange thing about it is that I tested it with the 10.10 live cd and it works perfectly, as well as with backtrack 4.

I did not try disabling acpi although it might work, because I must keep power consumption as low as possible. Can anybody think any possible solutions/workarounds to this?

---

