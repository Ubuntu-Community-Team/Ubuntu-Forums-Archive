---
title: "Disable Checksum offload"
date: 2012-07-18
forum: Networking &amp; Wireless
---

### Post by alopez@ac.upc.edu on 2012-07-18
Hi everyone,

I would like to disable the checksum offload of my network card. I have found this command that should solve my problem:

[LIST]
[*]ethtool -K eth0 tx off rx off
[/LIST]
When I query the status of the network card with ethtool -k eth0 everything seems ok, but when I use wireshark, the TCP packets have errors in the checksum. The connectivity is ok so I suppose that the checksum offload is not disabled. 



    rx-checksumming: off
    tx-checksumming: off


I am using Ubuntu 12.04




Thanks in advance

---

### Post by Sergius14 on 2012-07-18
You can also turn off checksum validation at Wireshark Preferences...

---

### Post by alopez@ac.upc.edu on 2012-07-19
Thanks for your replay. We are developing a new protocol that  encapsulates the packets. If the checksum is calculated by the network  card, it will just calculate the correct cheksum for the external packet  and not the internal one. When the packet is decapsulated, the internal  packet has a wrong checksum and the packet is discarded.
I have noticed that when I turn off the checksum offload using the  ethtool command, the only packets that wireshark detects with wrong  checksum are SYN and ACK tcp packets. The other ones are correctly  detected. I need that the checksum of these packets (SYN, ACK) are also  calculated by the cpu.

---

