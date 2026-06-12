---
title: "italc/dynamic ip"
date: 2009-03-31
forum: Networking &amp; Wireless
---

### Post by rick71 on 2009-03-31
Has anyone gotten italc to connect/control with dynamic IPs and host names? According to the developer, it can, but I haven't been able to get it working.

I have a Windows Server 2003 AD, a Linksys router acting as a DHCP server, a Linux master and Windows XP clients. If possible, I'd like to be able to mix Linux, W2k and XP clients, with  Linux italc master.

The Windows machine is able to connect to clients using the client's hostname, even if the client is using dynamic IP. The Ubuntu master can only connect using the client's static IP.

I'd like to be able to connect using hostname, so I can go back to dynamic IPs in the classroom.

Any and all info appreciated.

---

### Post by rick71 on 2009-04-11
I was able to connect and control a Ubuntu client from a Ubuntu master using the client's hostname. I have only done this one test. I do another experiment at school after Spring Break, probably Wednesday.

I have installed winbind on all Linux computers. After configuring nsswitch.conf, I was able to ping windows and Linux machines via hostname. Opensuse, Ubuntu and PCLinux OS. I ping the pclos box, but I can't ping from it using hostname. I believe windbind is only necessary on the Master machine, unless you want to be able to ping from all the Linux boxes using hostnames.

Also, iTalc's author has said control via hostnames is possible if DNS is set up properly. As of yet, I haven't learned how to set up DNS/DHCP.

---

