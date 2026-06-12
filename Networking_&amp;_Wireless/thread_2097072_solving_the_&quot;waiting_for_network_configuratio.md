---
title: "solving the &quot;waiting for network configuration&quot; solved and explained."
date: 2012-12-22
forum: Networking &amp; Wireless
---

### Post by Rockstarever on 2012-12-22
hello all i am making this thread for all those who is facing the above title problem at the time of start up. This problem is created due to the wrongly edited network configuration. by default ubuntu configures the network it-self but in some cases such as those while adding dns and other network configurations it should be strictly configured using network-manager. now just do the following changes as mentioned below. open a terminal make the following changes as stated.

[PHP]nano /etc/network/interfaces [/PHP]

delete every thing there and type in 

[PHP]auto lo
iface lo inet loopback[/PHP]

now press ctrl + x 
press Enter
and reboot  
this should solve your problem.

this is because the dns and the network info is stored into 

 /etc/resolv.conf


please correct me if i am wrong any help required and quries will be answered.

---

