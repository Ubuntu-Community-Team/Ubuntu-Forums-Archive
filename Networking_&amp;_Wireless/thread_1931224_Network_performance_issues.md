---
title: "Network performance issues"
date: 2012-02-25
forum: Networking &amp; Wireless
---

### Post by devil103 on 2012-02-25
First of all a list my system specs:

Running a Samba Fileserver Version: 3.5.11
Kernel: 3.0.0.16-generic

Network card: RTL8168 Gigabit with the correct Kernel Module from Realtek

```
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
        Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards
        Flags: bus master, fast devsel, latency 0, IRQ 43
        I/O ports at e000 [size=256]
        Memory at d0004000 (64-bit, prefetchable) [size=4K]
        Memory at d0000000 (64-bit, prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: r8168
        Kernel modules: r8168

```

Connected to a Gigabit Switch and Gigabit should be working


```
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised pause frame use: Symmetric Receive-only
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on

```

Problem:

I'm not getting the transfer speeds I used to have. In the past I could connect my laptop with a Gigabit network card to the switch and reach transfer speeds from the Samba to Windows 7 machine of 60 MB/s which seems quite normal to me. This was with a larger MTU then the standard 1500. 

However, when I now increase the MTU above 1500 the Samba fileserver cannot be reached, however an SSH session works without a problem! And, strangest of all, when I connect with laptop through the wireless I can also access the Samba server. However, the server is always connected wired.

Now, I can only get up to 20 MB/s with the standard 1500 MTU. 

I don't have another Gigabit computer to test with. And the drivers on my Windows machine haven't changed.

I've been searching like crazy for the past few days to find the problem here. 

Any suggestions?

---

### Post by roelforg on 2012-02-25
May i see the lshw?
```

sudo lshw -C network

```

---

### Post by devil103 on 2012-02-25
As Requested:

```
*-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 06
       serial: f4:6d:04:6f:c7:a7
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.028.00-NAPI duplex=full ip=192.168.2.100 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:43 ioport:e000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
```

---

### Post by roelforg on 2012-02-25
I'd say that either some app is using net a lot or you've got some upstream problems.

---

### Post by devil103 on 2012-02-26
Well, Samba is the only service running when testing so I don't see which service or daemon could be hogging resources. 

Just been testing with iperf. iperf reports the same speeds but shows an mtu of 4000 (which is reported to be the max of my network card).

However, with an mtu of 4000 I can run iperf, ssh into the server but I can't access my Samba shares over the wired connection.

But I can't see where or why Samba could be having problems with a larger mtu?

---

### Post by Vishal Agarwal on 2012-02-26
Check the firewall configuration. the network speed depends on firewall also. you may need to check the firewall log closely to check the unnecessary packets to be removed from the network data transaction.

---

### Post by devil103 on 2012-02-26
> **Vishal Agarwal said:**
> Check the firewall configuration. the network speed depends on firewall also. you may need to check the firewall log closely to check the unnecessary packets to be removed from the network data transaction.

A worthwhile try, I disabled all firewalls in the network. Both the SPI firewall in the router and the firewall on the server; Same result.

In the meantime I've also connected the gigabit laptop to the server directly in an attemp to cut out the router. Speeds are still the same.

The server itself cannot be running into a hd read problem yet, hdparm shows read speeds over 1000 MB/s. Normal for the SATAII connection.

---

