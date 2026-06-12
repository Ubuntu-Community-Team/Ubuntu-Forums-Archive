---
title: "Routing private IP's"
date: 2012-05-20
forum: Networking &amp; Wireless
---

### Post by ElGatoFlojo on 2012-05-20
I've got a routing question that I thought I would toss out as I'm stumped.

I have one machine, its running OpenVPN and I want to use it as a 
gateway for that openvpn network. Currently it is not a gateway itself.

Machine1
10.0.0.144  (eth0)
10.0.0.1      (gateway)
192.168.1.242 (tun0 for OpenVPN. Remote end is 192.168.1.241)

Machine2
10.0.0.47    (eth0)
10.0.0.1      (gateway)


I'd like to route packets for 192.168.1.0 via the OpenVPN network on 
10.0.0.144. I've tried

/sbin/ip route add 192.168.1.0/24 via 10.0.0.144

How-ever that doesn't work. I'm unable to get anything to route from 
Machine2 to the 192.168.1.0 network.

I'm probably missing something easy and obivous.

Thanks!

---

