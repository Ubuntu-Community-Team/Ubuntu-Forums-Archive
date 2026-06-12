---
title: "Adding Virtual interface with MAC address"
date: 2010-12-21
forum: Networking &amp; Wireless
---

### Post by phnet1111 on 2010-12-21
does anyone know how to get a virtual interface using a different MAC address from the one used my the main nic i have tryed all i can tryed to specify the address and everything in the interface file "/etc/network/interface" and also used the command as 

ifconfig eth0:1 hw ether <MAC>

still the same thing it will only change the mac of the mother nic but to the mac of the child

any help is much thankful 
Links Manuals anything please

---

### Post by sc0g on 2011-10-17
*Bump*

I am having the same problem on 10.04 LTS Lucid. I'm trying to manually set the MAC address for eth0:0 virtual interface in /etc/network/interfaces, but it changes the MAC for both eth0:0 and eth0.

Any help would be greatly appreciated!

```

# Main interface
auto eth0
iface eth0 inet static
address    10.2.1.5
network    10.2.1.0
broadcast  10.2.1.255
netmask    255.255.255.0
gateway    10.2.1.250

# Virtual Interface
auto eth0:0
iface eth0:0 inet static
address    10.2.1.105
network    10.2.1.0
broadcast  10.2.1.255
netmask    255.255.255.0
post-up ifconfig   eth0:0 hw ether 78:2b:cb:49:89:15

```

---

### Post by sc0g on 2012-04-18
*Bump*

Sure do wish someone would throw us a bone on this one. :p

---

