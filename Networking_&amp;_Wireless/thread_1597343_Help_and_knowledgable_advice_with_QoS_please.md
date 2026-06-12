---
title: "Help and knowledgable advice with QoS please"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by RegPerrin on 2010-10-15
I have a Cisco AP1142N access point where I can enable QoS. I have a few questions relating to QoS and how it actually works with devices:   1.How does the Cisco access point (or any router) differentiate between traffic streams?  2.What happens if the source of the stream is not a Cisco device, e.g.: Netperf traffic generator?  3.What is the access point examining to determine what sort of traffic stream it is (whether the AP is Cisco or not)?  4.Is it the TOS field?  5.Should all applications in the network be QoS-aware?

---

### Post by kreggz on 2010-10-15
End points can mark their traffic with DSCP markings. You may not want to trust devices to do this, IP Phones maybe something you can trust. Usually you would setup QoS end to end in your network (LAN/WAN/Carrier) and and at your router you would mark packets going over the WAN.

Wireless supports 802.11e QoS - see the Cisco website for more info


You might be better off posting in the Cisco.com forum

---

