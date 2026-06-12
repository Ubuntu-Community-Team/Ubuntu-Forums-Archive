---
title: "Easy? Activate eth1 as second Network Card using USB Adapter"
date: 2009-01-13
forum: Networking &amp; Wireless
---

### Post by Max_Welf on 2009-01-13
I am a Linux Beginner and can use some help. Trying to setup second network adapter for Ubuntu 8.04. I plugged in a new Trendnet TU-ET100C Network USB adapter (not wireless, old-fasioned wire. Reviewers on Amazon said it worked out of the box for them on Ubuntu). Light comes on and Ubuntu seems to recognize it properly:
```

root@tinman:/etc# lsusb
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 07a6:8511 ADMtek, Inc. ADM8511 Pegasus II Ethernet
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Next I updated /etc/network/interfaces with a dummy address to see if it is working (plugged into the same hub; trying to install OpenVPN later). Then I restarted network via /etc/init.d/networking restart

```

auto eth0
iface eth0 inet static
  address 192.168.0.20
  netmask 255.255.255.0
  network 192.168.0.0
  broadcast 192.168.1.255
  gateway 192.168.0.1

auth eth1
iface eth1 inet static
  address 192.168.0.30
  netmask 255.255.255.0
  network 192.168.0.0
  broadcast 192.168.1.255
  gateway 192.168.0.1

```

Did I miss anything? ifconfig will only show eth0, but not eth1. Neither 'Network Tools' in GNOME -> System ->  Administration (only shows eth0). Any help is appreciated.



Max

---

### Post by Max_Welf on 2009-01-13
the output of lshw -C network maybe helpful

```

root@tinman:/etc/network# lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:30:1b:46:da:71
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.0.20 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: a2:8b:27:77:8d:21
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: eth1
       serial: 00:14:d1:17:13:2f
       size: 100MB/s
       capacity: 100MB/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=pegasus driverversion=v0.6.14 (2006/09/27) duplex=full link=yes multicast=yes port=MII speed=100MB/s
root@tinman:/etc/network# 

```

---

### Post by Max_Welf on 2009-01-14
... ok making progress. almost there. Thanks for everybody's help! (just kidding). Next I have to startup the interface I guess: ifup eth1 -> and there it is. ifconfig now shows both IP addresses and it works. Screws up my Internet connection at this point, but will worry about it later.

Now I need to figure out how to make it stick after reboot without typing in ifup eth1 after restarting the box? Anybody?

---

