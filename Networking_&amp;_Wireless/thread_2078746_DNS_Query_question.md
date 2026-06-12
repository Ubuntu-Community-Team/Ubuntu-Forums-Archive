---
title: "DNS Query question"
date: 2012-10-31
forum: Networking &amp; Wireless
---

### Post by dnoyeb on 2012-10-31
I have a device that is sending out DNS queries but the checksum in the UDP packet is 0x00.  It appears that DNS servers won't respond when the checksum is 0x00?  Is that correct?

Is it possible for me to setup my own DNS server and have it respond to the DNS query even with a checksum of 0?

Do you think its possible that some device in my network is blocking the UPD packet because of its 0 checksum?

Thank you!

---

### Post by fwre01 on 2012-11-07
The checksum is located in either the IP or UDP headers, so it may not be a DNS specific issue. From some reading on how the IPv4 checksums are calculated, a 0x00 value definitely looks incorrect. This article also states:

> At each hop, the checksum is recalculated and the packet will be discarded upon checksum mismatch.

[http://en.wikipedia.org/wiki/IPv4_header_checksum]("http://en.wikipedia.org/wiki/IPv4_header_checksum")

Based on this it is possible that a router in the path may be dropping it. I think the fix would be to understand why these packets are being written with a broken checksum. 

EDIT:
It also seems as though the UDP checksum is optional, so my assumption would be that this may not be causing the issue.

[http://en.wikipedia.org/wiki/User_Datagram_Protocol#Checksum_computation]("http://en.wikipedia.org/wiki/User_Datagram_Protocol#Checksum_computation")

Are all clients on the network doing this? Or is this client transmitting other packets with a broken checksum? Is the checksum broken at layer 3 or layer 4?

---

