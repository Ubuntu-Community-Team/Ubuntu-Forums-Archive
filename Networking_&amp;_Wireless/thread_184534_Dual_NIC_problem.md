---
title: "Dual NIC problem"
date: 2006-05-30
forum: Networking &amp; Wireless
---

### Post by hotshots on 2006-05-30
I have a computer with dual NICs. 

They both recieve their Ips using DHCP, both are public IPs. My problem is that if I have both NICs enabled at the  same time the computer loses contact with the Internet. 

If I disable one of the NICs on the other hand (either one of them) the connection is re-established.

The reason I use two NICs on the box is because I want to host two unique domains, and i want to separate them at the NIC level.

I have tried the various tips and trix in the sticky and I have verified that both NICs have their drivers loaded, and that they both recieve and IP from the DHCP server.

Anyone have a clue as to what might be wrong, or any tips as to how I can investigate further ?

---

### Post by mips on 2006-06-01
If the two IP's are in the same network/subnet then it won't work.

Post the output of ifconfig -a here.

---

