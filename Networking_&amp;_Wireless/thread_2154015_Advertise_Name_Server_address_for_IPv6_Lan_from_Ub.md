---
title: "Advertise Name Server address for IPv6 Lan from Ubuntu router"
date: 2013-06-13
forum: Networking &amp; Wireless
---

### Post by ritazreiby on 2013-06-13
Hello, 

we are trying to set up an Ipv6 LAN with the following address range 2a00:1580:8000:6::/64

the IPv6 hosts are directly connected to a switch , which is connected to the router through the interface eth1 that has the address: 2a00:1580:8000:6::5/64

we installed and configured Radvd like this :

```
interface eth1 { 

    AdvSendAdvert on;
    MinRtrAdvInterval 3; 
        MaxRtrAdvInterval 10;
    AdvManagedFlag off;
    AdvOtherConfigFlag off;
    RDNSS 2a00:1580:8000:6::5
    {
    AdvRDNSSPreference 255;    
    
        };    
    prefix 2a00:1580:8000:6::/64 { 
                AdvOnLink on; 
                AdvAutonomous on; 
                AdvRouterAddr on;
        
        };
    
};
```


but it seems like our hosts can't obtain the dns name server adress automatically.
(the dns name server is the adress of eth1)

we tried to configure wide-dhcpv6 but didnt work.

please if you can provide us with step by step tutorial :)

Thanks :)

---

### Post by lemming465 on 2013-06-13
What are your hosts running?   Not too many clients support RDNSS yet.

When you configured wide-dhcpv6, did you change your Radvd **AdvOtherConfigFlag** to **on**?  Remember, in IPv6 the client DHCPv6 behaviors are controlled by the router advertisement flags.

Going v6-only is a little bleeding edge; most production networks so far are dual-stack with DHCPv4 and SLAAC.

---

### Post by ritazreiby on 2013-06-14
the hosts are running on Windows 7 . 
can you provide me with steps for the configuration of widedhcpv6 in case we did something wrong? thank you

---

### Post by ritazreiby on 2013-06-14
SOLVED ! we set  **the AdvOtherConfigFlag** to **on** and it worked ! 

Thank You:D

---

