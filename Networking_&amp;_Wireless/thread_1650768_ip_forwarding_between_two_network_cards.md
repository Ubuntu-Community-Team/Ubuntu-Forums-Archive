---
title: "ip forwarding between two network cards"
date: 2010-12-22
forum: Networking &amp; Wireless
---

### Post by pigling on 2010-12-22
Hi all,
I have two PCs both installed with Ubuntu 10.04. Also they both have two network cards installed. One (server) is connected to Panasonic IP camera BL-C131 and the other (client) is connected to the first PC through hub. I want to connect from the client PC through server PC to the camera.
Following is the network configuration:

Camera ip address: 10.81.113.69

Server PC: eth0--192.168.0.19 (connected to client PC through hub) eth1--10.81.113.19 (connected to camera)

Client PC: eth0--192.168.0.17 (connected to server PC through hub)

Server PC can connect to camera very well. I follow the guide [https://help.ubuntu.com/community/Internet/ConnectionSharing]("https://help.ubuntu.com/community/Internet/ConnectionSharing"), but it fails. 

This is what I have done Server PC (in root user already):
```
iptables -A FORWARD -o eth1 -i eth0 -s 10.81.113.0/24 -m conntrack --ctstate NEW -j ACCEPT
iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -A POSTROUTING -t nat -j MASQUERADE 
echo 1 > /proc/sys/net/ipv4/ip_forward

```

Client PC:
```
/etc/init.d/networking stop
route add default gw 192.168.0.19
/etc/init.d/networking restart

```

The system can't work as expected. Have I missed anything? Looking forward to your help. Thanks.

regards,
pigling

---

