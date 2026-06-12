---
title: "Can't Find Access point!"
date: 2005-12-30
forum: Networking &amp; Wireless
---

### Post by EEPS on 2005-12-30
Hi, I have two computers, one upstairs connected to a router directly, and one downstairs I wan't to set up on wireless. I have a WG311 v2 card. It has the Ti ACX 111 chipset. Ubuntu detects the card, and loads the acx_pci module, and a wlan0 interface shows up. Now here is the weird part, I put it in the upstairs computer, and I set it up with iwconfig, and it works great, but when I put it in the downstairs computer, it can not find the access point. iwconfig has 00:00:00:00:00:00. At first I thought it was smply a range problem, so I moved the router downstairs, and put it ON TOP of the computer, and still no luck. What could cause it not to find the ap when everything apears to work?

---

### Post by EEPS on 2005-12-30
Ok, I got it working! It is a little strange though. When I try to set up through the GUI network-admin tool, it will not work, even if I try to set it up with iwconfig after. If wlan0 is marked as enabled in that utility, it does nto work. When I disable it and set it up with iwconfig, it works. Maby they are conflicting in some way?

---

