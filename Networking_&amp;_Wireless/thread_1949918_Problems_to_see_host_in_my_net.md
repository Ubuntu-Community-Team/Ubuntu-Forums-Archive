---
title: "Problems to see host in my net"
date: 2012-03-31
forum: Networking &amp; Wireless
---

### Post by f0rexample on 2012-03-31
Hi. Sorry if i've not introduced myself before..
I'm new to ubuntu and i'm running it (11.10) on a vmware virtual machine (bridged mode) that is installed on windows 7. windows 7 is connected wireless to the router.
Settings of the net are:
win 7: 192.168.1.110 /24 (no gateway)
ubuntu: 192.168.1.111 /24 (gateway 192.168.1.1) 

the situation:
from ubuntu i can ping the gateway and i can go over internet, but i can't see win 7 (get no answer pinging win 7)
from win 7 i see ubuntu virtual machine: i get answer pinging it

i checked the routing table and this was the result:
> 
Destination Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0So i've added default gateway this way:
> 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
Now i can see win 7 host but i get a DUP! ping:
> 
PING 192.168.1.110 (192.168.1.110) 56(84) bytes of data.
64 bytes from 192.168.1.110: icmp_req=1 ttl=128 time=0.335 ms
64 bytes from 192.168.1.110: icmp_req=2 ttl=128 time=0.228 ms
64 bytes from 192.168.1.110: icmp_req=2 ttl=128 time=1.90 ms (DUP!)
Any possible solution?

---

### Post by dandnsmith on 2012-03-31
I'd be tempted to try the effect of removing the entry:
"192.168.1.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0"
to see what still works.

---

### Post by f0rexample on 2012-04-03
> **dandnsmith said:**
> I'd be tempted to try the effect of removing the entry:
"192.168.1.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0"
to see what still works.
I tried and i got win7 host reachable with ping DUP!
If i leave 192.168.1.0 in the route table i can't reach my win7 host

Here's the configuration of nic:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.111
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

I can't understand :confused:

---

### Post by haqking on 2012-04-03
So your question is about the DUP! ?

If so this is common using virtual networking under virtual machines especially in vmware due to bridged networking.

or the NIC is in promiscuous mode.

What is the exact issue ? you are getting a reply just a duplicate packet.

IS this causing some kind of networking issue or you just dont want the DUP! ?

If so look at changing your VM network settings and or checking if it is in promiscuous mode and also there is no duplicate IP

You could also change or update the Win 7 driver itself which vmware then virtualises


Edit: I just found a link which says basically the same thing i just did plus a bit more [http://communities.vmware.com/docs/DOC-14170](http://communities.vmware.com/docs/DOC-14170) hope this helps

---

### Post by f0rexample on 2012-04-03
> **haqking said:**
> So your question is about the DUP! ?

If so this is common using virtual networking under virtual machines especially in vmware due to bridged networking.

or the NIC is in promiscuous mode.

What is the exact issue ? you are getting a reply just a duplicate packet.

IS this causing some kind of networking issue or you just dont want the DUP! ?

If so look at changing your VM network settings and or checking if it is in promiscuous mode and also there is no duplicate IP

You could also change or update the Win 7 driver itself which vmware then virtualises


Edit: I just found a link which says basically the same thing i just did plus a bit more [http://communities.vmware.com/docs/DOC-14170](http://communities.vmware.com/docs/DOC-14170) hope this helps
My question is not only about the DUP!
Also i'm wondering why if i delete 192.168.1.0 line in the routing table i see my win7 host but if i don't touch that line i can't see it..
For sure no duplicate IP addresses and no nic promiscuous mode

---

