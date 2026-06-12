---
title: "Intel 5100 Loses Connection"
date: 2012-06-13
forum: Networking &amp; Wireless
---

### Post by Mark Uhde on 2012-06-13
I recently upgraded my Acer Aspire One to an Intel 5100 (512AN_HMW) card I got cheap on eBay to get dual-band support. It works great 99% of the time, but occasionally the connection randomly quits working. I found in a search some OLD issues with the Intel Wi-Fi drivers but my understanding was they were supposed to be resolved in the 3.x kernels. When it dies, it acts dead, but WireShark shows it quits getting ARP responses from the gateway. It still sees other broadcast traffic (to the printer from the router) but most of what shows up in WireShark while the connection is dead is an endless stream of these messages with no responses received. Any ideas?

13473	506.900098	IntelCor_04:3d:ac	Broadcast	ARP	42	Who has 192.168.2.1?  Tell 192.168.2.99

---

