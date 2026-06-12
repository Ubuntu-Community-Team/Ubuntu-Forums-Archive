---
title: "Wireless Linux Router + IPTV"
date: 2010-01-05
forum: Networking &amp; Wireless
---

### Post by zibalas on 2010-01-05
This is not exactly Ubuntu question but i don't know where else to ask. I'm trying to setup a Wireless Linux router. My ISP provides multicast IPTV. I've got the whole thing setup'ed with igmpproxy and hostpad. On wired connection IPTV works flawlessly, but on wireless connection IPTV glitches badly and router start to time out. My wireless card is DWA-552 I'm using ath9k driver. More info in my post on [LinuxQuestions.org]("http://www.linuxquestions.org/questions/linux-networking-3/wireless-iptv-with-atheros-ath9k-779521/") Did anyone tried to setup Wireless Router with IPTV? Any help would be greatly appreciated.

---

### Post by shairozan on 2010-01-05
If you are not using Wireless N then you're going to run into issues with glitches and jitter for a high fidelity video transmission. Wireless is not a true full-duplex communication, and it only runs Carrier Sense Multiple Access / Collision Avoidance to make sure the frequency is available. 

A number of people I know have attempted what you're doing (minus the linux router) but the fact is the wireless protocol just can't supply the data fast enough due to it's inability to transmit in full duplex.

---

### Post by zibalas on 2010-01-06
> **shairozan said:**
> If you are not using Wireless N then you're going to run into issues with glitches and jitter for a high fidelity video transmission. Wireless is not a true full-duplex communication, and it only runs Carrier Sense Multiple Access / Collision Avoidance to make sure the frequency is available. 

A number of people I know have attempted what you're doing (minus the linux router) but the fact is the wireless protocol just can't supply the data fast enough due to it's inability to transmit in full duplex.

Not true. I have wireless G DIR-300 router. If setup my DIR-300 to work as access point and plug eth0 (wired card) to it. IPTV works flawlessly if i connect through DIR-300. And also DWA-552 is wireless N card. So it's not throughput problem.

---

### Post by zibalas on 2010-01-09
Bump

---

