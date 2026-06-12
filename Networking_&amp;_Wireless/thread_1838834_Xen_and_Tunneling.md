---
title: "Xen and Tunneling"
date: 2011-09-04
forum: Networking &amp; Wireless
---

### Post by XenonSk on 2011-09-04
Hello, 
I have a tun/tap tunnel on a Xen machine.
That tunnel routes the IP address that xen clients should use.
For example, i have a tun0 p-T-p interface 10.0.0.10 10.0.0.1 on dom0 which provides 10.0.0.11 ip address to use for an xen domU machine.
First of all i thought i can use tun0 as a bridge interface directly from the xen. I have used vif-bridge and network-bridge scripts, specifying tun0 as a netdev. 
Xen does not even start - falls back with the operation permitted error.
O.K, i have used the vif-route, network-route scripts.
I have create an domU and specified 10.0.0.11 as IP adress and 10.0.0.10 as a default gateway.
I see that traffic goes to the tunnel and then returns back, but on the domU it is still no internet. tcpdump on the internal tapx.0 device shows that the traffic goes out of the domU but does not come back.
How to solve that?
ping 10.0.0.11 from dom0 does not work as well. 
PS. To route traffic with source IP 10.0.0.11 into the tunnel i have used "ip rule from" policy routing. If i put 10.0.0.11 as alias on tun0:0 on dom0 the ip works normally. So problem is somewhere in a Xen routing ...

---

