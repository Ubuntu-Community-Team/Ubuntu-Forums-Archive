---
title: "networking connections not listed in network manager"
date: 2010-08-23
forum: Networking &amp; Wireless
---

### Post by taelatus on 2010-08-23
Greetings.

I have a sudden problem.  Neither of my wired network connections are listed in the network manager applet.  I know that networking seems to be functional since I can ping local devices on the network.  I can't resolve DNS names however.  I suppose this is because network manager usually handles DNS?  I've posted the outputs of various configurations below.

```
/etc/NetworkManager/nm-system-settings.cfg

# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

no-auto-default=00:40:f4:e8:f5:51,

[ifupdown]
managed=false
```

```
/etc/network/interfaces

auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.1.87
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0
```

```
lshw -C network

  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: 00:1c:25:6e:cb:8d
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.87 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:ce00(size=256) memory:fdeff000-fdefffff memory:fdd00000-fdd1ffff(prefetchable)
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:04:01.0
       logical name: eth1
       version: 10
       serial: 00:40:f4:e8:f5:51
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:22 ioport:ee00(size=256) memory:fdbff000-fdbff0ff
```

---

### Post by dineshs on 2010-08-23
If you configure /etc/network/interfaces for static IP NM will not manage your devices.So
first backup  /etc/network/interfaces using
```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```
Now
```
 gksudo gedit /etc/network/interfaces
```
Comment out all lines (put a # before each line)[COLOR="Red"]except these two[/COLOR]```
auto lo
iface lo inet loopback
```
[COLOR="Blue"]Restart your machine[/COLOR]
Configure NM as in this link(substitute your IP...values)
[http://ubuntuforums.org/showpost.php?p=9733891&postcount=6](http://ubuntuforums.org/showpost.php?p=9733891&postcount=6)

---

### Post by Iowan on 2010-08-23
NM *might* be coerced into managing interfaces defined in */etc/network/interfaces* of you edit */etc/NetworkManager/nm-system-settings.conf* and change "managed=false" to "managed=true".

The above method is cleaner, though...

---

### Post by taelatus on 2010-08-24
Only one of my devices is set for a static address.  The other is DHCP.  Shouldn't NM be managing that one?

I will try your suggestions and get back to you.

---

### Post by dineshs on 2010-08-24
If you want to set manual IP 
Right click NM-edit connections-select the device-edit-ipv4-select method-manual
give IP mask and gateway then [COLOR="Red"]hit enter[/COLOR]
give DNS and apply
To set DHCP follow the same method except method-Automatic DHCP

---

