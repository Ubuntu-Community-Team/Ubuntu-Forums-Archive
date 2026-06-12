---
title: "Cisco 340 Seriees PCMCIA and Monitor Mode"
date: 2006-01-23
forum: Networking &amp; Wireless
---

### Post by standmatt on 2006-01-23
I just installed Breezy on my laptop and I am using a Cisco 340 series wirelesss adaptor.  It uses both eth0 and eth1 as interfaces and I can only access the internet with eht1.  What I am trying to do now is put the card into promiscous mode so that I can capture packets with ethereal.  However, when I go to the shell and type

sudo iwconfig eth1 mode monitor 

it come back to the prompt and I lose my connection to the access point-which I think should be happening.

However, ethereal will not capture any packets on eth1 only stuff on loopback.

What am I doing wrong, should I maybe install the airo drivers:confused: 

Thanks

matt

---

