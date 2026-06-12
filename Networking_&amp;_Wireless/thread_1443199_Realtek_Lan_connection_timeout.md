---
title: "Realtek Lan connection timeout"
date: 2010-03-30
forum: Networking &amp; Wireless
---

### Post by dillzz on 2010-03-30
With Ubuntu 9.10 I have had a frustrating experience with the following hardware/driver.  All network settings are statically set.  Upon first boot and random times during normal usage I experience a loss in pings to public servers.  At this point all network connectivity is very sporadic.  The only resolution to this is sudo sh /etc/init.d/networking stop, then a start.  This is not hardware related as I dual boot and this has never been seen in Win.  Also this never happend in prior Ubuntu versions, such as 8.04.  Any ideas? 

**2.6.31-17-generic #54-Ubuntu SMP x86_64**

**Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)**

**lsmod | grep r8**
r8168                 101556  0

**sudo modinfo r8168**
filename:       /lib/modules/2.6.31-17-generic/kernel/drivers/net/r8168.ko
version:        8.017.00-NAPI
license:        GPL
description:    RealTek RTL-8168 Gigabit Ethernet driver
author:         Realtek and the Linux r8168 crew <netdev@vger.kernel.org>
srcversion:     A1C7F4F267B431A9A62A658
alias:          pci:v000010ECd00008168sv*sd*bc*sc*i*
depends:       
vermagic:       2.6.31-17-generic SMP mod_unload modversions
parm:           speed:force phy operation. Deprecated by ethtool (8). (array of int)
parm:           duplex:force phy operation. Deprecated by ethtool (8). (array of int)
parm:           autoneg:force phy operation. Deprecated by ethtool (8). (array of int)
parm:           rx_copybreak:Copy breakpoint for copy-only-tiny-frames (int)
parm:           use_dac:Enable PCI DAC. Unsafe on 32 bit PCI slot. (int)
parm:           debug:Debug verbosity level (0=none, ..., 16=all) (int)


**sudo ethtool eth0**
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes

---

