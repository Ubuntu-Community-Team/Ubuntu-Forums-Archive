---
title: "vlan - understanding concept"
date: 2011-03-15
forum: Networking &amp; Wireless
---

### Post by nicolasdiogo on 2011-03-15
hello,

i would like to clarify how i can use VLANs.

as i have red on the web, it is possible to have a switch to allocate ports to a single VLAN.  thus splitting subnets on a port allocation.

since i have a pc running KVM, it is possible to create multiple subnets for DMZ and LAN.

thus my question is - is it possible to have a SINGLE cable connection to a switch that carries TWO subnets?  so that i can decide how to distribute then on the pc?


thanks,

---

### Post by sedawk on 2011-03-15
It might be possible, but the switches I have seen so far
allow only one number to assign to each port.

So a port can be in VLAN 0 (default), VLAN 1, VLAN, 2 or
VLAN 3, but no port can be in VLAN 1+2.

But that might depend on price and vendor. E.g if
they interpred the numbers as bitmasks (so VLAN 3
would actually be 3+2^0+2^1= VLAN 1+2).

Normally I have multiply ethernet connectors on one
server, so I do not have to do that kind of tricks
inside the switch.

---

### Post by doas777 on 2011-03-15
> **nicolasdiogo said:**
> hello,

i would like to clarify how i can use VLANs.

as i have red on the web, it is possible to have a switch to allocate ports to a single VLAN.  thus splitting subnets on a port allocation.

since i have a pc running KVM, it is possible to create multiple subnets for DMZ and LAN.

thus my question is - is it possible to have a SINGLE cable connection to a switch that carries TWO subnets?  so that i can decide how to distribute then on the pc?


thanks,
yes, but it depends on the vendor implementation.
this is called trunking.

---

### Post by nicolasdiogo on 2011-03-15
thanks,

i have found the documents explaining howto do trunk in [DD-WRT]("http://www.dd-wrt.com/wiki/index.php/Switched_Ports")

i will try to do this via trunk/VLAN and see if that works.

with regards,

Nicolas

---

### Post by dnoyeb on 2011-04-19
That is not the same thing as trunking.  Very similar, but the objectives are different.  You just need non-port based VLAN, 802.1Q.  If the switch can't do that, then its not really doing 802.1Q.  Port based VLAN doesn't even require 802.1Q AFAIK since no packets would leave the switch tagged.

---

### Post by nicolasdiogo on 2011-04-20
thanks dnoyeb


let me clarify this i have attached a simple graph

the way i see it. vlan0 (tag 0) is the default, and when we use trunk we start enforcing tags against a network port.  by sending packets with different tags we are able to run multiple subnets within the same cable connection.
this should work fine as long as the recipient understands the setup - to decode tagged traffic.

by using vconfig:
[http://www.linuxfoundation.org/collaborate/workgroups/networking/vlan#3.1_The_vconfig_tool](http://www.linuxfoundation.org/collaborate/workgroups/networking/vlan#3.1_The_vconfig_tool)

please let me know if there is something that i misunderstood.


thanks,

---

### Post by shukalo83 on 2011-04-20
For this kind of setup you will need trunk between server and router/firewall. You can have this kind of setup with any of the vlan config tools available. Vconfig would be one way but there are some others too. Have a look at this [http://ubuntuforums.org/showthread.php?t=703387](http://ubuntuforums.org/showthread.php?t=703387)

So, you will have three virtual network interfaces on your server and on every one of them you will have to provide an IP address for specific subnet. You don't want to have an IP address on physical interface (you mentioned that there is no default vlan). This means that every packet between server and router/firewall is tagged.

---

### Post by nicolasdiogo on 2011-04-20
that is clear now


thanks a lot guys.

---

