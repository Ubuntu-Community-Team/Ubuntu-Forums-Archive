---
title: "a strange  issue with ping6"
date: 2013-02-25
forum: Networking &amp; Wireless
---

### Post by iss_2011 on 2013-02-25
Hello,


  I have 2 Ubuntu machines one acting as IPv6 wireless router (running  hostap and radvd on wlan0) and the other is connected to that router.  the router wlan0 interface has the address 2001:db8:1:1::1/64 and the  host has the address 2001:db8:1:1::2/64 on wlan0 which is connected to  ap1 provided by the router. On wireshark, I can see the router  advertisements at the router and the host.
  

When I ping 2001:db8:1:1::2 at the router it says that "Destination  unreachable: Address unreachable" and I can see the neighbour  solicitation and advertisement messages exchange. 
  

When I ping 2001:db8:1:1::1 at the host it says the same "Destination  unreachable: Address unreachable" and I can see the neighbour  solicitation message only 
  

Any idea?
  

Also, I have tried to do the following into the router 
sudo ip -6 neigh add 2001:db8:1:1::2 lladdr 64:50:03:ec:cc:ss dev wlan0
  

and this into the host 

sudo ip -6 neigh add 2001:db8:1:1::1 lladdr 64:50:03:ec:cc:ff dev wlan0
  

Then, when I ping I can see the echo request and reply exchange in  wireshark only but I cannot see that at the command line, rather it says  no packets have been received !!!
  

Thank you
  

Ibra

---

