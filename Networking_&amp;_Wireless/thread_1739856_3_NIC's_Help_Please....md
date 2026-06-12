---
title: "3 NIC's Help Please..."
date: 2011-04-26
forum: Networking &amp; Wireless
---

### Post by knichel on 2011-04-26
I have a box with 2 NIC's currently.  
eth0 = local LAN interface
eth1 = connection to ISP (gets static IP via dhcp)

The box is a gateway/dhcp/firewall etc....

/etc/network/interfaces 
```

auto eth0
auto eth1

iface eth0 inet static
        address 192.168.6.200
        netmask 255.255.255.0
        broadcast 192.168.6.255
        network 192.168.6.0
        pre-up iptables-restore < /etc/iptables.up.rules
        gateway 24.148.102.64

iface eth1 inet dhcp

```

#route -n
```

Kernel IP routing table                                                                                                                                         
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface                                                                                   
192.168.6.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0                                                                                    
24.148.112.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1                                                                                    
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1                                                                                    
0.0.0.0         24.148.112.252  0.0.0.0         UG    100    0        0 eth1 

```

I need to add a 3rd NIC to the box to connect it to another network (192.168.40.0/23)
When I add the interface to /etc/network/interfaces eth2 gets created and configured, but my routing table looks like this...
```

Kernel IP routing table                                                                                                                                         
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface                                                                                   
192.168.6.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0                                                                                    
24.148.112.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1                                                                                    
192.168.4.0     0.0.0.0         255.255.254.0   U     0      0        0 eth2                                                                                    
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1                                                                                    
0.0.0.0         192.168.40.1  0.0.0.0         UG    100    0        0 eth2 
0.0.0.0         24.148.112.252  0.0.0.0         UG    100    0        0 eth1 

```
I cannot ping 192.168.40.1 either.  I am wondering if the 2 default routes are causing the problem?  


--
JuJuBee

---

### Post by Charlietje on 2011-04-26
Hi,

You can not have 2 default gateways.
A gateway means: if the requested ip is not a local address, it needs to search it through the default gateway.
If you have 2 gateways, it does not know which to use.

Can you post you /etc/network/interfaces file?


Regards
Carl

---

### Post by knichel on 2011-04-27
Thanks,
/etc/network/interfaces
```

auto eth0 eth1 eth2

iface eth0 inet static
        address 192.168.6.200
        netmask 255.255.255.0
        broadcast 192.168.6.255
        network 192.168.6.0
        pre-up iptables-restore < /etc/iptables.up.rules
        gateway 24.148.102.64

iface eth1 inet dhcp

iface eth2 inet static
        address 192.168.40.3
        netmask 255.255.254.0
        broadcast 192.168.41.255
        network 192.168.40.0
        gateway 192.168.40.1

up route add -net 192.168.8.0/24 gw 192.168.40.1 eth2


```

I finally got everything working I think.  Does this look good?

---

### Post by Iowan on 2011-04-27
Can't argue if it works - but looks like you still have multiple gateways defined... :-k

---

### Post by Charlietje on 2011-04-28
You should delete every gateway defined in your /etc/network/interfaces
Even your route add line.

You will get a defaulte gateway from eth1 via DHCP.

---

### Post by knichel on 2011-04-28
A gateway and a default gateway are not the same.  As for the route statement, I need the route statement because the 192.168.8.0 network is not connected.  Without the static route, packets to the 192.168.8.0 network would get forwarded to the Default Gateway which is not what I want.  The 192.168.8.0 network is on the other side of the 192.168.4.1 gateway.

Thanks for the assistance.  I will try to remove the gateway statements and see if all works as it does currently.  

-
JuJuBee

---

