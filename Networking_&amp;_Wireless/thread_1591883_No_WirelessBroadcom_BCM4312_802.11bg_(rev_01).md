---
title: "No Wireless:Broadcom BCM4312 802.11b/g (rev 01)"
date: 2010-10-10
forum: Networking &amp; Wireless
---

### Post by lethalfang on 2010-10-10
Problem: Broadcom BCM4312 802.11b/g **[14e4:4315]** (rev 01)

```

sudo lspci -v | less

02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
        Subsystem: Hewlett-Packard Company Device 1507
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at d9500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
        Capabilities: [58] Vendor Specific Information <?>
        Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [d0] Express Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [13c] Virtual Channel <?>
        Capabilities: [160] Device Serial Number ff-ff-00-ff-ff-00-00-00
        Capabilities: [16c] Power Budgeting <?>
        Kernel modules: wl, ssb

```

I've tried a few things:
1) The automatic "Hardware Drivers" function showed me two drivers, one free and one non-free. Unfortunately, none of them work. The free one found the networks, but couldn't connect to any of them. The non-free one couldn't even find a network. 
2) I tried this: [http://jetpackweb.com/blog/2010/04/30/ubuntu-10-4-lucid-lynx-and-broadcom-bcm4312/](http://jetpackweb.com/blog/2010/04/30/ubuntu-10-4-lucid-lynx-and-broadcom-bcm4312/) No luck, either.

Anyway, after a while, there seems to be quite a few posts and long threads regarding this issue, but I can't quite get any of them to work. 
I was looking at this point: [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1266620](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1266620) , but I haven't managed to install linux-headers-*-<amd64/i386>.deb because I don't have the right dependencies. What dependencies do I need to install first?
My computer is a HP Pavilion Entertainment PC.

Thanks in advance..... I've been working on this issue for a few hours now...... damn. :confused:

---

### Post by dineshs on 2010-10-10
From google search
[http://ubuntuforums.org/showthread.php?t=1307995](http://ubuntuforums.org/showthread.php?t=1307995)
[http://ubuntuforums.org/showthread.php?t=1589733](http://ubuntuforums.org/showthread.php?t=1589733)
[http://ubuntuforums.org/showthread.php?t=1591867](http://ubuntuforums.org/showthread.php?t=1591867)

---

### Post by lethalfang on 2010-10-10
> **dineshs said:**
> From google search
[http://ubuntuforums.org/showthread.php?t=1307995](http://ubuntuforums.org/showthread.php?t=1307995)
[http://ubuntuforums.org/showthread.php?t=1589733](http://ubuntuforums.org/showthread.php?t=1589733)
[http://ubuntuforums.org/showthread.php?t=1591867](http://ubuntuforums.org/showthread.php?t=1591867)

I've tried them and none of them works. 
The issue with BCM4312 [14e4:4315] is quite stubborn. I've found one thread which claims a working solution, but I would need to install an updated kernel. I haven't figured out how to install the updated kernel yet, because the .deb file I tired to install didn't have all the dependencies.

---

### Post by Peter09 on 2010-10-10
I have a Broadcon BCM4312 and its working fine with the Wl0 driver

>   *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 90:4c:e5:66:a4:80
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.0.9 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:d9000000-d9003ff

do

```
ifconfig
```
in a terminal and show us the results

---

### Post by lethalfang on 2010-10-10
```

$ sudo lshw -C network

  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 0c:60:76:80:6e:22
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:d9500000-d9503fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:26:9e:41:3c:62
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.117 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:45 ioport:5000(size=256) memory:d1410000-d1410fff memory:d1400000-d140ffff memory:d1420000-d142ffff

```


```

$ ifconfig

eth1      Link encap:Ethernet  HWaddr 0c:60:76:80:6e:22  
          inet6 addr: fe80::e60:76ff:fe80:6e22/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

```

```

$ lspci -n | grep 14e4

02:00.0 0280: 14e4:4315 (rev 01)


```

I just upgraded to 10.10, activated the STA driver recommended/found by "Systems --> Administration --> Additional Drivers," and still no luck.

---

### Post by Peter09 on 2010-10-11
Check that your hardware/function ON/Off switch for wireless is in the On position. I have also heard of a bug where, if the wireless is switched off in windows (through the function key) then it does not resume in Ubuntu. The fix was to go back to windows and switch the wireless on, not sure if this is the case here.

---

