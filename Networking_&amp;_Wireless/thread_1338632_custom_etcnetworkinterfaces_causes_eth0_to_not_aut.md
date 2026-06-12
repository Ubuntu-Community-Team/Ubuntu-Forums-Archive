---
title: "custom /etc/network/interfaces causes eth0 to not auto-start"
date: 2009-11-26
forum: Networking &amp; Wireless
---

### Post by sayeo87 on 2009-11-26
I'm running Ubuntu 9.10 inside a VMWare Workstation VM using the NAT networking settings. Per the instructions [here]("http://communities.vmware.com/thread/99481;jsessionid=0AAEAF705B6C0A093D0CE91140F18BC9"), I tried to configure a static IP setup for my Ubuntu system on the virtual network of the host by changing the /etc/network/interfaces file. Here's what mine looks like:
```

auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.67.100
netmask 255.255.255.0
gateway 192.168.67.2
```

Here is the output of "route":
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.67.0    *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.67.2    0.0.0.0         UG    0      0        0 eth0
```

Can anybody spot what I'm doing wrong in the config file? I am certain that it is the issue as eth0 starts up fine when I comment out my changes.

P/S: the DHCP range of the virtual network adapter in question is 192.168.67.[128-254]

---

### Post by Iowan on 2009-11-26
Try adding a line: ```
auto eth0
```

---

### Post by sayeo87 on 2009-11-26
> **Iowan said:**
> Try adding a line: ```
auto eth0
```
Thanks! That worked!

---

