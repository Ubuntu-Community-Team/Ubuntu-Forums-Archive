---
title: "Routing problem, I think, no ping to server public IPs"
date: 2011-03-28
forum: Networking &amp; Wireless
---

### Post by 8Kuula on 2011-03-28
I have combined 2 internet connections using these instructions: [http://www.linuxquestions.org/linux/answers/Networking/Spanning_Multiple_DSLs](http://www.linuxquestions.org/linux/answers/Networking/Spanning_Multiple_DSLs)

One little nag thou. Now I cant ping or anything else to eth1 or eth2 ip's from local net computers. From server itself it works, and from outside (internet).

On my server box I have 3 NICs
eth0 - 192.168.1.1 - local net (clients in 192.168.1.10-19)
eth1 - ip from dhcp - isp1 connection to internet
eth2 - ip from dhcp - isp2 connection to internet

```
$ ip route show
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.1 
$ISP1_SOMETHING dev eth1  proto kernel  scope link  src $ISP1_IP
$ISP2_SOMETHING dev eth2  proto kernel  scope link  src $ISP2_IP
default 
	nexthop via $ISP1_GW  dev eth1 weight 20
	nexthop via $ISP2_GW  dev eth2 weight 1
default via $ISP2_GW dev eth2  metric 100 
default via $ISP1_GW dev eth1  metric 100
```
```
$ ip route show table isp1                      
default dev eth1  scope link  src $ISP1_GW
```
```
$ ip route show table isp2
default dev eth2  scope link  src $ISP2_GW
```
```
$ ip rule
0:	from all lookup local 
32764:	from $ISP2_IP lookup isp2 
32765:	from $ISP1_IP lookup isp1 
32766:	from all lookup main 
32767:	from all lookup default
```
```
$ iptables -nL -t nat 
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
SNAT       all  --  192.168.1.0/24       0.0.0.0/0           to:$ISP1_IP
SNAT       all  --  192.168.1.0/24       0.0.0.0/0           to:$ISP2_IP

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

Im not 100% sure even that I have done this correctly but atleast seems to work.

---

### Post by 8Kuula on 2011-03-30
[http://lartc.org/howto/lartc.rpdb.multiple-links.html](http://lartc.org/howto/lartc.rpdb.multiple-links.html)
That did do the trick.

---

