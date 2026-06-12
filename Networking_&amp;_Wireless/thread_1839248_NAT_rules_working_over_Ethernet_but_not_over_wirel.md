---
title: "NAT rules working over Ethernet but not over wireless"
date: 2011-09-05
forum: Networking &amp; Wireless
---

### Post by matthew106 on 2011-09-05
Hi,

I have a fresh installation of 32-bit Ubuntu 11.04 server as a Virtual machine which i intend to use as a gateway and route certain client machines through it.

I have set up a static ip address for the physical network card (eth0) and have set up a virtual interface (eth0:0). My /etc/network/interfaces file is as follows:

```

#The primary network interface 
auto eth0 
iface eth0 inet static 
address 192.168.0.9 
netmask 255.255.255.0 
network 192.168.0.0 
broadcast 192.168.0.255 
gateway 192.168.0.1

#Virtual interface for gateway purposes 
auto eth0:0 
iface eth0:0 inet static 
address 192.168.0.10
netmask 255.255.255.0
```I also set up the necessary routing rules using the following commands:

```

sudo iptables -A FORWARD -o eth0 -i 192.168.0.10 -s 192.168.0.0/24 -m conntrack --ctstate NEW -j ACCEPT 
sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT 
sudo iptables -A POSTROUTING -t nat -j MASQUERADE 

```I then configured the gateway for routing between two interfaces by enabling IP forwarding:

```

sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"

```and added the following lines to /etc/sysctl.conf:

```

net.ipv4.conf.default.forwarding=1 
net.ipv4.conf.all.forwarding=1

```

The wired and wireless interfaces of the host machine (Win 7) are set up with static ip addresses as follows:

```
ip address: 192.168.0.4
subnet mask: 255.255.255.0
default gateway: 192.168.0.1 (or 192.168.0.10 if i want the host machine itself to be routed through the ubuntu gateway machine)
```**And now here's the problem:**

When the host machine is connected to the network via ethernet then everything works as expected and if i set up the default gateway of either the host machine or other client machines to 192.168.0.10 all traffic gets routed through the ubuntu machine.

However, when the host machine is connected to the network via wireless the routing does not occur and client machines with 192.168.0.10 as a default gateway have no internet access.

[I][B] Does anyone know why connecting the host machine via wireless has this effect and how can i fix it so that it works over wireless as well?
[/B] [/I]
Thanks

---

### Post by matthew106 on 2011-09-06
[B]UPDATE:
[/B]
Using a simple tcp monitoring tool ([tcptrack]("http://www.rhythm.cx/%7Esteve/devel/tcptrack/")) i can see then when the host is connected via ethernet requests from client machines successfully reach the Virtual machine. However when the host is connected via wireless (all other things being equal) then requests from either the host (to the virtual machine) or client machines do not appear in the connection displayed in tcptrack. (so i assume they are not reaching the VM?)

Could this possibly be something to do with having to place the wireless card into promiscuous mode?

Thanks

---

