---
title: "Tried ndiswrapper and now there is no wifi connectivity whatsoever"
date: 2013-05-26
forum: Networking &amp; Wireless
---

### Post by dopesickbadfish on 2013-05-26
So I tried ndiswrapper today and totally botched something up. 
I resorted to ndiswrapper because I've been having wifi connectivity issues for MONTHS, and I wanted to settle it.
But somehow, I ended up 100% disabling wireless.  (Wired works fine.)
The thing I don't get at all is the WARNINGS. /etc/modprobe.conf does not exist, and I'm not sure what the 2nd warnings meangs whatsoever.

Can someone help to get Wifi back up and running again? Even the constant dropping was better than none at all...

Running Xubuntu 12.04 LTS, HP Pavilion dv6, wireless driver: Realtek RTL8188CE (r8169 is, i think, the wired driver)

I ran the commands in the ndiswrapper sticky:

```
 
**ndiswrapper -l**

WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
WARNING: All config files need .conf: /etc/modprobe.d/aliases, it will be ignored in a future release.
rt64win7 : driver installed
    device (10EC:8168) present (alternate driver: r8169)
[B]
sudo lshw -C Network[/B]

  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: 08:2e:5f:9a:4d:fb
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=10.0.0.14 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:52 ioport:3000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network UNCLAIMED
       description: Network controller
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:f0200000-f0203fff
[B]
lsmod | grep ndis[/B]
ndiswrapper           283384  0 

**sudo modprobe ndiswrapper**
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
WARNING: All config files need .conf: /etc/modprobe.d/aliases, it will be ignored in a future release.

```

---

