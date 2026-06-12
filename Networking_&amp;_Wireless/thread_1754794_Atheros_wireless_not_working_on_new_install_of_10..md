---
title: "Atheros wireless not working on new install of 10.04"
date: 2011-05-10
forum: Networking &amp; Wireless
---

### Post by cwscribner on 2011-05-10
Hi all.

Just did a fresh install of 10.04 and the wireless isn't working.  Here's the output of lshw.

```

*-network
             description: Wireless interface
             product: AR5001 Wireless Network Adapter
             vendor: Atheros Communications Inc.
             physical id: 0
             bus info: pci@0000:07:00.0
             logical name: wlan0
             version: 01
             serial: 00:23:4d:d7:05:1d
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=ath5k driverversion=2.6.32-31-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
             resources: irq:23 memory:c2000000-c200ffff


```

I'm assuming I need a driver of sorts but all the methods that I've seen have yielded nothing for me.  Any links/resources/advice would be greatly appreciated.

---

### Post by chili555 on 2011-05-10
> I'm assuming I need a driver of sortsActually, you have it:> driver=ath5kIf it isn't working, something else is wrong. May we see:```
dmesg | grep -e ath -e wlan
rfkill list all
```What kind of laptop is it?

---

### Post by josephmills on 2011-05-10
> **cwscribner said:**
> Hi all.

Just did a fresh install of 10.04 and the wireless isn't working.  Here's the output of lshw.

```

*-network
             description: Wireless interface
             product: AR5001 Wireless Network Adapter
             vendor: Atheros Communications Inc.
             physical id: 0
             bus info: pci@0000:07:00.0
             logical name: wlan0
             version: 01
             serial: 00:23:4d:d7:05:1d
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=ath5k driverversion=2.6.32-31-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
             resources: irq:23 memory:c2000000-c200ffff


```

I'm assuming I need a driver of sorts but all the methods that I've seen have yielded nothing for me.  Any links/resources/advice would be greatly appreciated.

looks like your mods/driver is loaded lets make sure could we please see a ```
lsmod | grep ath
``` and a ```
dmesg | grep ath5k
``` could we also see a ```
rfkill list
```
thanks

---

