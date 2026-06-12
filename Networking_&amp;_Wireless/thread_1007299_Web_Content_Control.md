---
title: "Web Content Control"
date: 2008-12-10
forum: Networking &amp; Wireless
---

### Post by BUNAC on 2008-12-10
Hi guys,
Can anyone suggest a good way to restrict web content?

I'm currently using Ubuntu 8.04 as an internet gateway. Client PC's (whatever they turn up with - XP / Vista / OSX / RedHat....) can connect through and browse the internet but I want to limit what they can view / do!

I am currently using Firestarter but I want something that can block general categories (e.g. porn, gambling) not just specific websites. I also need to prevent P2P software and games. Just to stop them eating up the bandwidth.

Can anyone suggest a piece of software or where I can get some instructions?

Thank you in advance. ):P

---

### Post by Zack McCool on 2008-12-10
Dansguardian and Squid.  Squid is a proxy server, DansGuardian is a content filter.  They work well together.

Once you have them installed and configured, you'll need to either configure the connecting workstations to use a proxy, or configure the firewall to force everything through the proxy.

Directions are abundant on the net, and packages are available in the repos...

---

### Post by BUNAC on 2008-12-10
Thanks Zack McCool,
I've already got the proxy configured I just needed the content blocker so I'll have a look into DansGuardian.

Cheers!

---

### Post by BUNAC on 2008-12-11
OK... I thought I had this one in the bag but apparently not!

At the moment I have an Ubuntu server setup as an internet gateway and DHCP server. This has a small LAN Hub connected to it allowing customers to connect via ethernet cable and browse the internet. (Once I can filter the content I will set up wireless.)

Customers can connect to the internet and do have auto assigned IP settings. I cannot change any setting on the customers computers other than through DHCP.

The server has Firestarter and DHCP3 both of which are working fine. 

Do I need to install a proxy?
Can I just install a content filter?

Cheers in advance! :p

---

