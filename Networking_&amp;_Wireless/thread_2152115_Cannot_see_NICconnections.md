---
title: "Cannot see NIC/connections"
date: 2013-06-06
forum: Networking &amp; Wireless
---

### Post by fogu on 2013-06-06
Hello,

I've recently installed a fresh copy of Ubuntu server 12.04 LTS 64 bit and installed the GUI with hopes of getting FOG setup and running on this new machine.  My problem is, is that I cannot see the internet connections in the upper right hand corner/menu and when I enter Devices - Network tools or even Network connections.   I am pretty new to the Ubuntu scene and would greatly appreciate any help.  

More facts:

[LIST]
[*]when I connected to my business network via Ethernet cable it does connect to the network and can function/surf pages. 
[*]Salad is good. 
[/LIST]

---

### Post by Iowan on 2013-06-06
If it is a default server setup, it probably has network information in */etc/network/interfaces* - and Network Manager won't mess with it. On this Network Manager-controlled machine, */etc/network/interfaces* contains only two lines:
```
auto lo
iface lo inet loopback
  
```

---

