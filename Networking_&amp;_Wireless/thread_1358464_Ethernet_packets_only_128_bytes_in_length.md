---
title: "Ethernet packets only 128 bytes in length"
date: 2009-12-18
forum: Networking &amp; Wireless
---

### Post by alager on 2009-12-18
What would cause all my ethernet packets to only be 128 bytes in length?
From a wireshark recording:
TCP    atmp > 53616 [PSH, ACK] Seq=129 Ack=1 Win=5840 **Len=128**
The above packet is from my application trying to send a block of 1024 'x' characters.  But it's being broken up into multiple 128 byte packets.

I have this issue with multiple applications, one written in perl and one in C.  It seems to me to be an OS level thing at this point.


Thanks for your help,
Aaron

---

### Post by puppywhacker on 2009-12-18
in tcpdump is you don't specify "-s 0" the traces will be clipped on something like 128bytes. The other reason can be that somehting in your network can not handle too many bytes in a packet. Ethernet has an MTU of 1500, it might be that something is fragmenting your packets. If your application is too slow in filling your TCP stack it will kick out the packets.

---

