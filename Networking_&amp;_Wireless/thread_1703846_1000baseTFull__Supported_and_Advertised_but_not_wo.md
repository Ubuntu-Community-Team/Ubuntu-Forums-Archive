---
title: "1000baseT/Full  Supported and Advertised but not working!"
date: 2011-03-09
forum: Networking &amp; Wireless
---

### Post by teocomi on 2011-03-09
Hello, i'm using a AT3IONT-I motherboard with integrated card. If I ethtool it to 1000 full duplex it wont work!
Here is **sudo ethtool eth0**:
```

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
    Speed: 100Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
    Link detected: yes

```here is **sudo lshw -C network**
```

  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 03
       serial: bc:ae:c5:8b:7d:33
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.021.00-NAPI duplex=full ip=192.168.0.2 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:42 ioport:e800(size=256) memory:f8fff000-f8ffffff memory:f8ff8000-f8ffbfff memory:fbff0000-fbffffff

```And** lspci -nn**
```

 00:00.0 Host bridge [0600]: nVidia Corporation MCP79 Host Bridge [10de:0a82] (rev b1)
00:00.1 RAM memory [0500]: nVidia Corporation MCP79 Memory Controller [10de:0a88] (rev b1)
00:03.0 ISA bridge [0601]: nVidia Corporation MCP79 LPC Bridge [10de:0aad] (rev b3)
00:03.1 RAM memory [0500]: nVidia Corporation MCP79 Memory Controller [10de:0aa4] (rev b1)
00:03.2 SMBus [0c05]: nVidia Corporation MCP79 SMBus [10de:0aa2] (rev b1)
00:03.3 RAM memory [0500]: nVidia Corporation MCP79 Memory Controller [10de:0a89] (rev b1)
00:03.5 Co-processor [0b40]: nVidia Corporation MCP79 Co-processor [10de:0aa3] (rev b1)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP79 OHCI USB 1.1 Controller [10de:0aa5] (rev b1)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP79 EHCI USB 2.0 Controller [10de:0aa6] (rev b1)
00:06.0 USB Controller [0c03]: nVidia Corporation MCP79 OHCI USB 1.1 Controller [10de:0aa7] (rev b1)
00:06.1 USB Controller [0c03]: nVidia Corporation MCP79 EHCI USB 2.0 Controller [10de:0aa9] (rev b1)
00:08.0 Audio device [0403]: nVidia Corporation MCP79 High Definition Audio [10de:0ac0] (rev b1)
00:09.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Bridge [10de:0aab] (rev b1)
00:0b.0 RAID bus controller [0104]: nVidia Corporation MCP79 RAID Controller [10de:0abc] (rev b1)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0ac4] (rev b1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0aa0] (rev b1)
00:15.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0ac6] (rev b1)
03:00.0 VGA compatible controller [0300]: nVidia Corporation ION VGA [10de:087d] (rev b1)
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)

```If i use 

```
sudo ethtool -s eth0  speed 1000 duplex full autoneg off
```then in ethtool speed is Unknown and it doesn't work; if I set it via pre-up it wont work either...

Please help!!

Thanks!

---

### Post by grahammechanical on 2011-03-10
You seem to know more about this than I do and you can tell me that I am wrong if you like but I see the word "off" at the end of the ethtool command. Surely that is switching eth0 off?

It is my understanding that these cards will automatically increase the data through-put according to the size of the data being sent/received and the capabilities of the devices connected to it. Your card will work with a 10baseT device but not at 1000baseT data through-put speeds only at 10baseT data through-put speeds. I could be wrong but this is my understanding.

How does this device work in practice?

Regards.

---

### Post by teocomi on 2011-03-10
Hello, I'm a newbe in Ubuntu.. By the way the 'off' refers to the autonegotiation, thus forcing to use 1000Mb...

All the computers, cables, switches in my house are 1000Mb in fact when I had windows installed on that same device I could reach 70MB/s (~700Mbps) transfers in local LAN, but now only un to 11MB/s..!

May it be a driver problem??

---

### Post by teocomi on 2011-03-14
Hello! The problem was the brand new cat6 cable!! It was malfunctional and as I replaced it everything went fine.. 

Thanks all for the help!

---

### Post by doas777 on 2011-03-14
glad you got it worked out. yes, cabling is usually the first thing I recommend people check when seeing an ethtool output like that.

---

