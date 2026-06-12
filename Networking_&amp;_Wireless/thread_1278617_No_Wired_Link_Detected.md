---
title: "No Wired Link Detected"
date: 2009-09-29
forum: Networking &amp; Wireless
---

### Post by nicoloks on 2009-09-29
Hi All,

Have an issue with my Mythbuntu 8.10 box that has only developed over the last few months where it refuses to detect a link over my 100 Mbps ethernet. 

The NIC I'm using is an onboard Realtek RTL8211B which has given me some trouble in the past, however that was because there is some sort of bug with it where the MAC is read in backwards. Manually setting the MAC for forcedeth has fixed this problem for me, and I've been using it like this for quite some time.

Looking at dmesg I can see that eth0 reports there is no link detected when trying to get an IP address from DHCP. I've tried renewing the IP address with no luck, and I've also tried manually setting a static IP address which works (as in it is accepted), however I am still undable to ping any device on the network (everything is on a 192.168.1.0/24 network)

Looking at my switch I can see the connection light is only flickering every now and then. Weird thing is if I plug my laptop into that same switch using the same cable and port the connection light goes solid (like it is meant to) almost straight away.

From this it would seem that it is either my network card or Linux itself on my Mythbuntu box that is causing the issues, so I disabled the on board NIC and installed a PCI based TP-Link card. Same issue.

Something in my Linux network stack is screwy, so just wondering if anyone had any advice on how to trouble shoot this? Would it be worth reinstalling the TCP/IP stack?

---

