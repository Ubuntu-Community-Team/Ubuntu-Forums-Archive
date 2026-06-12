---
title: "Network limitations?"
date: 2009-07-25
forum: Networking &amp; Wireless
---

### Post by Jago6060 on 2009-07-25
Running Ubuntu Server 9.04 64-bit.

My server has 3 network interfaces. LAN1, LAN2, and an added nic(AM1).  I don't have extensive experience doing networking so I use solely the "interfaces" file to handle the nics.  Right now, I only have one entry in the interfaces file for eth1.  Can I have more than one entry?(eth1-eth3?)  Do they all have to eb on the same network or can teh be on different networks?  Can they have different gateways as well?  I tried to have two active connections using the interfaces file.  I setup eth1 and eth2, with identical settings(except IP address) but I when I restarted the network, it would say things like (paraphrasing)SIOCDLERT: No such process and RTNETLINK: Not available.

Also, is there a way in the interfaces file to tell it to shutdown nics that you don't want running?  For example, can I put in an entry in the interfaces file that's something like "auto iface eth3 down"?

---

### Post by superprash2003 on 2009-07-26
1)yes you can use it for multiple interfaces
2)they need not be on the same network
3)yes they can have different gateways
4)post contents of /etc/network/interfaces file
5)those commands need to be run in the terminal , you cannot add them in the /etc/network/interfaces file. although you can schedule the command to run at a specific time using cron

---

