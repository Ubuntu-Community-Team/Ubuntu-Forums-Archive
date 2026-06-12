---
title: "My new network configuration doesn't work"
date: 2011-12-03
forum: Networking &amp; Wireless
---

### Post by JunYoung Gwak on 2011-12-03
I want to add KVM VPS on my Ubuntu Server 10.04LTS
I want to assign one IP on eth0 and bridge eth1 to use it as VPS.
However, I now lost connection to network now.
I need your help!!

Here are my configurations : 

```

$ sudo cat /etc/network/interfaces

auto eth0
iface eth0 inet static 
address 199.21.###.###
network 199.21.###.###
netmask 255.255.255.
broadcast 199.21.###.###
gateway 199.21.###.###

auto eth1
iface eth1 inet manual

auto br0
iface br0 inet static
address 199.21.###.***
network 199.21.###.###
netmask 255.255.255.0
broadcast 199.21.###.###
gateway 199.21.###.###
bridge_port eth1
bridge_stp yes
bridge_fd 0
bridge_maxwait 0

```

```

$ sudo dmesg | grep 'eth0'
r8169: eth0: linkup
r8169: eth0: linkup
eth0: no IPv6 routers present
$ sudo dmesg | grep 'eth1'
r8169: eth1: linkup
r8169: eth1: linkup
eth0: no IPv6 routers present

```

Could you please help me with this???
Thank you

---

