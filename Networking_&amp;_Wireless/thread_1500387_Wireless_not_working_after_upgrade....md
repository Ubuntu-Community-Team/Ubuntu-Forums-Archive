---
title: "Wireless not working after upgrade..."
date: 2010-06-03
forum: Networking &amp; Wireless
---

### Post by levis lover on 2010-06-03
I installed these packages after a lot of search over the internet but all in vain..

1. bcmwl-modaliases
2. broadcom-sta-common

But still when i do ```
pppoeconf
``` it finds the device wlan0 but is unable to use it.. Any ideas?

Also there's no Network manager applet in the Panel..
I could not start the applet even after this
```
nm-applet --sm-disable
```

What could be wrong..?

---

### Post by levis lover on 2010-06-03
**iwconfig**
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
vboxnet0  no wireless extensions.

ppp0      no wireless extensions.

```

**iwlist scan**
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

vboxnet0  Interface doesn't support scanning.

ppp0      Interface doesn't support scanning.

```

**lshw -c network**
```
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:ba:03:41:d5
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:d8200000-d8203fff ioport:4000(size=256)
  *-network DISABLED
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:5d:6d:e5:da
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:d7100000-d7101fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes


```

---

### Post by levis lover on 2010-06-03
Please anyone..
i need to fix this urgently..

---

### Post by Linfreak on 2010-06-15
As mentioned earlier in another thread [http://ubuntuforums.org/showthread.php?t=1468507&page=1](http://ubuntuforums.org/showthread.php?t=1468507&page=1), RIGHT clicking the network-manager tray icon and selecting enable networking did the trick for me...

HTH,
Siva

---

