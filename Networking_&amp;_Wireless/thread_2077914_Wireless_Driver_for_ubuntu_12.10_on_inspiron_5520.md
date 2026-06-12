---
title: "Wireless Driver for ubuntu 12.10 on inspiron 5520"
date: 2012-10-29
forum: Networking &amp; Wireless
---

### Post by xxsmarty on 2012-10-29
I have installed ubuntu 12.10 lately and I tried to install the wireless Driver by seeing various sites and threads. I have installed a deb from here : How do I install BCM43142 wireless drivers for Dell Vostro 3460/3560?

But it doesn't have any effect on my system. I additional driver section I get Using Broadcom 802.11 Linux STA wireless drivers source frm wireless-bcm43142-oneiric- dkms(opensource)

But It also shows : This device is using an alternate driver.

I have these results:


```

lspci -vnn

08:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Dell Wireless 1704 802.11n + BT 4.0 [1028:0016]
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at c1500000 (64-bit, non-prefetchable) [size=32K]
	Capabilities: [40] Power Management version 3
	Capabilities: [58] Vendor Specific Information: Len=78 <?>
	Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [d0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [13c] Virtual Channel
	Capabilities: [160] Device Serial Number 00-00-85-ff-ff-c2-c0-18
	Capabilities: [16c] Power Budgeting <?>


```

```

sudo lshw -class network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 05
       serial: d4:be:d9:2d:d3:86
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=172.16.82.142 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:c1404000-c1404fff memory:c1400000-c1403fff
  *-network UNCLAIMED
       description: Network controller
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c1500000-c1507fff



```


Please help me I am sick of trying different things.

---

### Post by mikewhatever on 2012-10-31
I don't think a driver for BCM43142 is available for 12.10.
Check out [This question ]("http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560") for more info.
You may want to try 12.04 instead.

---

### Post by Hadaka on 2012-11-01
Hi please post the output of...

```
lspci -nn | grep 0280 
```

*IF the result shows [14e4:4365] then try this post.
please the entire post.


[http://ubuntuforums.org/showthread.php?p=12313016](http://ubuntuforums.org/showthread.php?p=12313016)

---

### Post by Hadaka on 2012-11-01
Hi, also this post,  the instructions are clearer.

[http://ubuntuforums.org/showthread.php?t=2078800](http://ubuntuforums.org/showthread.php?t=2078800)

---

