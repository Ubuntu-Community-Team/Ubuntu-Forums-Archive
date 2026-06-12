---
title: "Help needed with Sun Quad Fast Ethernet PCI Card X1034A"
date: 2009-06-06
forum: Networking &amp; Wireless
---

### Post by vmashburn on 2009-06-06
I am running Ubuntu 9.04 and I cannot get my 4 x Sun Quad Fast Ethernet PCI Card X1034A NICs to pass traffic. I can connect them to switches, but they will not respond to ARP requests. There is no default gateway configured on them because they are being used for a lab. My primary integrated NIC is used as the gateway to the network. My ifconfig shows all the NIC's operational, but they are labled a little crazy. I have a total of 12 NIC's on these 4 cards (PCI slots 4,5 and 6 repectively) and the output of the if config shows the NICs as:
eth49
eth54
eth55
eth56
eth57
eth58
eth59
eth60
eth61
eth62
eth63
eth64
 
Other than that, they all show up and they show my IP addresses assigned to them. 
 
I would really appreciate any help that you could provide as to how to get this working.

---

### Post by uberlinux on 2012-02-18
I'm sure that you found an answer to this by now but just for others searching X1034A +Linux via search engines (this is high on page one...), please check out this thread:
[http://scientificlinuxforum.org/index.php?showtopic=1411](http://scientificlinuxforum.org/index.php?showtopic=1411)

The short story on these cards is that:
1. Performance is spotty on machines with more than 2GB RAM.
2. The cards make up bogus MAC addresses upon booting every time you boot, which is why you have a million eth## numbers - every MAC address UDEV sees, it will create an eth# for, and it'll keep it forever.

---

