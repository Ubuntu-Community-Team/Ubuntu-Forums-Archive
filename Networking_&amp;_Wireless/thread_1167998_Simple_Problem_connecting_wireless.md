---
title: "Simple Problem connecting wireless"
date: 2009-05-23
forum: Networking &amp; Wireless
---

### Post by Idiocracyisnow on 2009-05-23
Hello, 
 
I just installed Ubuntu and have been reading around the forums for a solution to connecting my wireless network. I know it works on the machine already since its a dual boot and it runs fine from Windows so I know its not a hardware problem.
 
my wireless card is Broadcom Corporation BCM4306 802.11b/g Wireless Lan Controller
 
when I click on the network connections icon it lists my Ethernet controller and a "Wireless Networks" link but they're greyed out and cannot connect to them. It displays "Disconnected" underneath each listing. 
 
Where do I begin to start to correct this? Thanks

---

### Post by Iowan on 2009-05-23
Check **lshw -C network** to see if card gets alias (like eth0), or whether it is disabled.  Another place to check is *ifconfig -a* to see if interface gets an IP address.

---

