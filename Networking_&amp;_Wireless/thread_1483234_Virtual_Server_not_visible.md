---
title: "Virtual Server not visible"
date: 2010-05-14
forum: Networking &amp; Wireless
---

### Post by snaileater on 2010-05-14
I installed IPcop in a virtual machine under kvm on ubuntu 10.04. 
The start script:
```
#!/bin/sh
sudo kvm -hda /VM/IPcop-3/ipcop.img \
	-net nic,vlan=0 -net tap,vlan=0,ifname=tap0,script=/VM/IPcop-3/tap0-up,downscript=/VM/IPcop-3/tap0-down \
	-net nic,vlan=1 -net tap,vlan=1,ifname=tap1,script=/VM/IPcop-3/tap1-up,downscript=/VM/IPcop-3/tap1-down \
	-net nic,vlan=2 -net tap,vlan=2,ifname=tap2,script=/VM/IPcop-3/tap2-up,downscript=/VM/IPcop-3/tap2-down &
sleep 5
sudo ifconfig br0 0.0.0.0
sudo ifconfig tap0 0.0.0.0

```

/etc/interfaces contains this:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
        address 192.168.254.2
        netmask 255.255.255.0
        network 192.168.254.0
        broadcast 192.168.254.255
        #gateway 192.168.254.1
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

auto eth1
iface eth1 inet manual

auto br1
iface br1 inet static
        address 172.30.5.24
        netmask 255.255.255.0
        network 172.30.5.0
        broadcast 172.30.5.255
        gateway 172.30.5.250
        bridge_ports eth1
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

```

After booting IPcop, the host system is unable to access the web, while any other (physical) machine in my LAN has full access to the internet via this virtual IPcop.

Interestingly on the host firefox is able to get update notifications, but accessing the updates is not possible.

How to enable web access on the host?

---

### Post by snaileater on 2010-05-22
The problem gets solved with this /etc/interfaces (adding metric):
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
        address 192.168.254.2
        netmask 255.255.255.0
        network 192.168.254.0
        broadcast 192.168.254.255
	metric 0
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

auto eth1
iface eth1 inet manual

auto br1
iface br1 inet static
        address 172.30.5.24
        netmask 255.255.255.0
        network 172.30.5.0
        broadcast 172.30.5.255
        gateway 172.30.5.250
	metric 1
        bridge_ports eth1
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off


```

---

