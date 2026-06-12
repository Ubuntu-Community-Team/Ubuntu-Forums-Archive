---
title: "Disconnected from network upon waking"
date: 2010-01-17
forum: Networking &amp; Wireless
---

### Post by ..::| Dave89 |::.. on 2010-01-17
Sometimes, not always, when I have set my PC to suspend, and wake it up later, it won't allow me to connect to the Wi-Fi network, it detects the netowork tjhough, but the little icon in the notification area just displays a spinning circle, and I have to restart the computer to re-enable connection.  This only happens on my desktop PC, I've never had it happen on my laptop.  My network card is a D-Link Wireless G DWA-510.

---

### Post by adam814 on 2010-01-17
That seems to be a pretty common problem actually.  There are workarounds though.  Could you post the output from "sudo lshw -C network"?

---

### Post by ..::| Dave89 |::.. on 2010-01-17
dave89@dave89-desktop:~$ sudo lshw -C network
[sudo] password for dave89: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: 00:1d:7d:c9:c8:57
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:27 ioport:c000(size=256) memory:f9000000-f9000fff memory:fa200000-fa21ffff(prefetchable)
  *-network
       description: Wireless interface
       product: RT2561/RT61 rev B 802.11g
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 00
       serial: 00:24:01:a6:c4:72
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=10.1.1.4 latency=32 multicast=yes wireless=IEEE 802.11bg
       resources: irq:20 memory:fa000000-fa007fff
dave89@dave89-desktop:~$

---

### Post by adam814 on 2010-01-17
Rather than restarting you can just do this:
```
sudo modprobe -r rt61pci && sudo modprobe rt61pci
```

If anyone knows a more permanent solution I'd be interested.

---

### Post by ..::| Dave89 |::.. on 2010-01-19
That code worked, but I'd still like a more permanent solution.

---

### Post by adam814 on 2010-01-19
[http://ubuntuforums.org/showthread.php?t=552377](http://ubuntuforums.org/showthread.php?t=552377)

I can't really test it on my laptop (suspend doesn't work for several reasons).  It just might work if you do what they did and substitute "rt61pci" for "ndiswrapper" in /etc/default/acpi-support.

---

### Post by ..::| Dave89 |::.. on 2010-01-19
So I add MODULES="rt61pci" to /etc/defaults/acpi-support.  acpi-support is a large text file, where exactly do I put it in?

---

### Post by adam814 on 2010-01-19
There should already be a MODULES= line in it.  I'd just search in the text editor (ctrl+F in gedit) for MODULES= and put it in the existing one.

---

### Post by ..::| Dave89 |::.. on 2010-01-20
Hope I did this right, I have included a section of the text where I put in "rt61pci"


# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES="rt61pci"

---

### Post by adam814 on 2010-01-20
That looks right to me.  Let me know if it works for you.

---

### Post by ..::| Dave89 |::.. on 2010-01-20
I left it in sleep mode for about an hour, upon waking it wouldn't connect or even recognize any networks.

---

### Post by rbroom on 2010-02-13
I'm having the same problem with a LinkSys Wireless-G PCI adapter (Broadcom chipset).

I can manually fix it with

```
# modprobe -r b43
# modprobe b43
```

But putting it in the MODULES= line in /etc/default/acpi-support doesn't have any impact.

Continuing to look for a solution, or at least where the problem is.  (Can't open a bug for the wireless driver, since it's affecting more than one.)

---

