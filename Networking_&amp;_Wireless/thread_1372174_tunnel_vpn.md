---
title: "tunnel vpn"
date: 2010-01-04
forum: Networking &amp; Wireless
---

### Post by yosra_bensaied on 2010-01-04
hi
i've made a tunnel vpn between 2 laptops.each laptop is in a network. the first one has the address 193.48.19.91 and he has the private address  10.0.0.1 given when the tunnel is established. the second laptop which is consider the server vpn has the adress 10.0.0.254 and it is a static address because it is in a private network 10.0.0.0. this private network is connected to another network is the other side 193.48.19.112/28. so that we have a laptop with eth0 10.0.0.3 and eth1 193.48.19.126
now we want that the first laptop with the adress 193.48.19.91 (has also the adress 10.0.0.1 needed for the tunnel) ping a laptop in the network 193.48.19.112/28
for this i added  in this laptop (adress 193.48.19.91 but also 10.0.0.1 which is not visible in ifconfig but is built when we start the tunnel)
 # sudo route add -net 193.48.19.112 network 255.255.255.248 gw 10.0.0.3
but it doesnt work 
please help me 
ps : sorry for my english

---

