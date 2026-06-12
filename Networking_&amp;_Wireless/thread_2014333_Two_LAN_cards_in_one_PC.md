---
title: "Two LAN cards in one PC"
date: 2012-07-01
forum: Networking &amp; Wireless
---

### Post by jlct021 on 2012-07-01
Hi

My subnet is 172.18.88.32/28 

I've added a second LAN card to PC1 and set is up as follows:

eth0 on PC1's IP is 172.18.88.36 and connects to a NanoBridge that connects to an Intranet

eth1 on PC1's IP is  172.18.88.37 and connects to PC2 via LAN cable

eth0 on PC2's IP is 172.18.88.38

adsl modem is 172.18.88.46

What settings must I adjust on PC1 so that I can:

a) access PC1's file share from PC2 via LAN cable

b) still be able to access the Intranet from PC2

Keeping in mind that in the above scenario:

eth0 on PC1 connects to an Intranet via a NanoBridge

eth1 on PC1 will connect to PC2 via LAN cable 

so far the only way I can think of is to:

bridge eth0 and eth1 to create a bridged interface

Will the above work and or is there a better way?

Thanks

---

