---
title: "Wired network configuration problems"
date: 2013-03-20
forum: Networking &amp; Wireless
---

### Post by bminyano on 2013-03-20
Hi,

I have problems configuring my network configuration. The problem is that I am not getting an ip.
I have read a lot of posts with similar problems, but none worked to me.
I unistalled network manager to configure the network manually after a lot of tries.

Maybe I am missing something, but I configured the /etc/network/interfaces and /etc/resolv.conf
In the first one i have:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

In resolv.conf:
nameserver 130.206.33.1
search uib.es
domain uib.es

When starting the computer it waits trying to configure the network, but it cannot be configured.

I don't know what else I have to configure or to look. Could anyone help me?

---

### Post by steeldriver on 2013-03-20
What network hardware do you have? is it enabled and has the driver been detected and loaded?

```
sudo lshw -C network
```

Are there any error messages about eth0 in dmesg?

```
dmesg | grep eth0
```

---

### Post by bminyano on 2013-03-20
```
sudo lshw -C network
```

  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1f:d0:87:97:1c
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:d000(size=256) memory:ea000000-ea000fff memory:bff00000-bff1ffff



```
dmesg | grep eth0
```

[    1.215456] r8169 0000:04:00.0: eth0: RTL8168b/8111b at 0xffffc9000063c000, 00:1f:d0:87:97:1c, XID 18000000 IRQ 44
[   17.172801] r8169 0000:04:00.0: eth0: link down
[   17.179902] ADDRCONF(NETDEV_UP): eth0: link is not ready


It seems there is an error here, link is down. I don't understand why.

---

### Post by bminyano on 2013-03-20
I have tried, as some people suggested, installing wicd, but it still doesn't work.
It remains obtaining ip address: the part DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval X repeats eternally

It happened before using wicd, too. Why could be the reason for this to fail?

---

### Post by bminyano on 2013-03-21
Well, googling I found the solution.
I added the following line in the /etc/dhcp/dhclient.conf:
```
send vendor-class-identifier "MSFT 5.0";
```

---

