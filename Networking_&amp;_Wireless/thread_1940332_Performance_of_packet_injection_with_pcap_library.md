---
title: "Performance of packet injection with pcap library"
date: 2012-03-13
forum: Networking &amp; Wireless
---

### Post by phjay on 2012-03-13
I write a 802.11 radiotap packet injection program (works in monitor mode) and experience a slow speed of packet injection. It is about 1Mbits. My wireless card is supposed to be 300Mbps.I didn't need to get the full speed but I would like to know how to improve.

I simply use a while loop and perform pcap_inject(). The program is not very "smooth". Suddenly it injects 20 packet and stop a while and inject again. I have to set a delay between each injection to make it smooth.

Does anyone have experience about pcap library injection? Thanks for help

---

