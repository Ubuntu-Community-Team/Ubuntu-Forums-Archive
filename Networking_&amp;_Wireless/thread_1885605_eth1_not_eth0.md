---
title: "eth1 not eth0?"
date: 2011-11-23
forum: Networking &amp; Wireless
---

### Post by bailout on 2011-11-23
I am trying to solve a boot problem involving networking. My pc is a desktop with a wired connection and no wireless. When I run ifconfig -a it tells me I have lo and eth1. I thought eth numbering started from 0 so with one connection I should have eth 0 whereas I have eth1. 

My boot problem is that it gets stuck on 'waiting for network connection' for a long time and eventually says 'booting without network enabled' or similar. After booting the network is connected fine and works. 

My etc/network/interfaces has:

# The primary network interface
auto eth0
iface eth0 inet dhcp

I am thinking that if it is looking for eth0 whereas my network is under eth1 it could explain why it gets stuck. However, I am puzzled by why my network is called eth1 and if they are numbered sequentially what is eth0>

thanks

---

### Post by matt_symes on 2011-11-23
Hi

Does you have a problem with a udev naming rule ?

```
cat /etc/udev/rules.d/70-persistent-net.rules
```

```
ifconfig
```

I may have to look at this tomorrow.

Kind regards

---

### Post by bailout on 2011-11-23
> **matt_symes said:**
> 

```
cat /etc/udev/rules.d/70-persistent-net.rules
```



```
# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:11:09:f6:71:8e", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="bc:ae:c5:8c:e6:41", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

```

---

### Post by bailout on 2011-11-23
Editing /etc/network/interfaces and replacing eth0 with eth1 solved my boot problem.

I think the problem was caused by recently changing the motherboard. I assume that the networking chip on the original board was given eth0 and although it is no longer there that has been reserved and the new one given eth1.

---

### Post by matt_symes on 2011-11-24
Hi
[FONT=monospace]
[/FONT]> # PCI device 0x10ec:0x8168 (r8169) SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="**bc:ae:c5:8c:e6:41**", ATTR{dev_id}=="0x0",ATTR{type}=="1", KERNEL=="eth*", NAME="**eth1**"

I suspect if you check the hardware address of your network card (using ifconfig) it will have the same address as the udev rule above.

Kind regards

---

