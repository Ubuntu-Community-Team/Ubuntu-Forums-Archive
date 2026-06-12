---
title: "Large # of Packets killing Windows Wireless"
date: 2009-06-18
forum: Networking &amp; Wireless
---

### Post by xanfantasy on 2009-06-18
Recently I reinstalled Ubuntu Jaunty 9.04 to get a fresh start. I reconfigured my Broadcom wireless card (BCM4306) and have it working. However I have noticed whenever I boot from Ubuntu, the other Windows XP computers my family own have trouble connecting to the Access Point if at all. I checked the bandwidth and it doesn't exceed 756 kilobits of data (our connection is 2.2 Mb/s Verizon DSL). All 4 of our computers (3 laptops, 1 desktop) have no problem when my desktop is booted in Windows XP. 

Using wireshark there is a large amount of LLC, SSDP, and ARP traffic. During the test I closed my networked applications (firefox, pidgin, etc.) so TCP and HTTP was minimal. 

LLC is addressed to AsustekC_4b:c7:53.
ARP is broadcasting asking for who has what internal ip going down the list of 192.168.1.1 to 192.168.1.255
SSDP is addressed to ff02::c

How would it be possible to decrease this traffic to see if that is the problem with our wireless connection or could there be a different problem? If you need anymore information I will post as soon as I can.

Thanks in advance,
Xan Fantasy

---

