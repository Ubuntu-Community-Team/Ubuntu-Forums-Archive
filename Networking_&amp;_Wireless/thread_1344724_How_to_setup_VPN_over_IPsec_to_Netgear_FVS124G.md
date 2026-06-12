---
title: "How to setup VPN over IPsec to Netgear FVS124G"
date: 2009-12-03
forum: Networking &amp; Wireless
---

### Post by cyclic_redundancy_check on 2009-12-03
Please can anyone tell me how to establish a VPN secure IPsec tunnel from Ubuntu 9.10 client over internet through Netgear DG834G VPN terminated to a Netgear FVS124G behind. (Both have NATS subnets)
I have tried what I considered were the obvious approaches  including Swan,  kvpnc+Racoon (which incidentally bombs out parsing the config file)

FVS124G is configured by its own wiz
DG834G has ports 500, 1701 and 1723 direct  through rules in & out

I am hoping to find some lucky lad or lass who has achieved this who can advise how they managed it !

Thanks, crc

---

### Post by puppywhacker on 2009-12-03
IPsec is running on top of IP, not on top of TCP and UDP like the ports you mentioned "500, 1701 and 1723". The DG834G is probably only forwarding TCP and UDP protocols and not the IPsec protocol.

I used the ipsec-howto to setup my ipsec tunnels in linux.
[http://www.ipsec-howto.org/x304.html](http://www.ipsec-howto.org/x304.html)

---

