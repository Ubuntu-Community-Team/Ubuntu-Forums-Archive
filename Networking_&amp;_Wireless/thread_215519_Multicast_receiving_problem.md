---
title: "Multicast receiving problem"
date: 2006-07-14
forum: Networking &amp; Wireless
---

### Post by ShoGUNMaster on 2006-07-14
I have Ubuntu Dapper running on my HP laptop and I'm using BCM4318 PCMCIA (and also BCM4306, integrated, disabled in OS) WLAN 802.11b/g card. I use it with ndiswrapper and it's workin almost well. It's currently running in 54Mbps ad-hoc mode. Unicast and even broadcast seem to work fine, but it cannot receive multicast packets (there's no problem with sending those). I use OLSR multihop routing which uses IP address 224.0.0.57 for route discovery purposes and I also need use multicast for data transfer. "ifconfig" states that "multicast" is on and enabling "allmulti" won't make a difference either.

Has anyone faced something similar (even with wired) or does anyone just have any ideas overcoming this?

ps. Using "tcpdump" for this (eth2) interface works/responds very slow like having "1 minute delay" and I get e.g. 1 packet out of 154 filtered in its statistics when running it very short time (pressing ctrl-c almost right away and waiting the response). I only see the multicast packets sent from the interface (eth2) itsef and naturally other kind of packets when running "tcpdump" longer. Other network interfaces work fine if I enable them.

---

