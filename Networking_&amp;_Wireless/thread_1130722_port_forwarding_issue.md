---
title: "port forwarding issue"
date: 2009-04-20
forum: Networking &amp; Wireless
---

### Post by odror on 2009-04-20
I have an ubuntu server connected to the Internet. I have a windows vista client. The internet is through eth1 and the client is connected through eth0. I would like to forward port 4006 to the client. 

I used the following commads that worked on fedora 9, but is not working and forwarding on ubuntu 9.4 (actually mythbuntu). 192.168.0.97 is the client ip. and 192.168.0.5 is the server ip on the localnet.

/sbin/iptables -t nat -A PREROUTING -p tcp -i eth0 -d 192.168.0.5 --dport 4007 -j DNAT --to 192.168.0.97:4007
/sbin/iptables -A FORWARD -p tcp -i eth0 -d 192.168.0.97 --dport 4007 -j ACCEPT

I suspect that the network on the server does not "think" that eth1 and eth0 are on the same computer thus the ip of the server on the net is not "linked" with the local ip of the server 192.168.0.5

Any help will be appreciated. Including how to debug it.

Thanks

---

