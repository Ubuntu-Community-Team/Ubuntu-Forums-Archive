---
title: "Ubuntu 12.10 wireless trouble Macbook Pro, Broadcom BCM4331"
date: 2013-01-28
forum: Networking &amp; Wireless
---

### Post by skyler440 on 2013-01-28
I recently installed ubuntu 12.10 on my Macbook Pro mid 2012  alongside Mountain Lion using rEFIt boot. I am having trouble connecting  to wireless network. When I click the internet icon at the top of the  menu bar, no networks are shown and when I try to manually connect  through edit connections, it doesen't work. I did not instal any drivers  for anything, but the trackpad (even the two finger scrolling works) ,  brightness keys, volume keys and keyboard illumination led brightness  works. So.. I am guessing it came with some drivers.
  Here are my results of some things I typed into terminal
  
[LIST=1]
[*]nm-tool
  State: disconnected  Device: eth0 -----------------------------------------------------------------  Type:              Wired   Driver:            tg3 State:             unavailable Default:           no HW Address:        A8:20:66:2A:05:23  Capabilities: Carrier Detect:  yes  Wired Properties Carrier:         off
[*]sudo lshw -C network
  PCI (sysfs)    *-network                 description: Ethernet interface  product: NetXtreme BCM57765 Gigabit Ethernet PCIe  vendor: Broadcom Corporation  physical id: 0  bus info: pci@0000:01:00.0  logical name: eth0  version: 10  serial: a8:20:66:2a:05:23  capacity: 1Gbit/s  width: 64 bits  clock: 33MHz  capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical tp 10bt   10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation  configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.123   firmware=57765-v1.37 latency=0 link=no multicast=yes port=twisted pair  resources: irq:16 memory:a0400000-a040ffff memory:a0410000-a041ffff  *-network  description: Network controller  product: BCM4331 802.11a/b/g/n  vendor: Broadcom Corporation  physical id: 0  bus info: pci@0000:02:00.0  version: 02  width: 64 bits  clock: 33MHz  capabilities: pm msi pciexpress bus_master cap_list  configuration: driver=bcma-pci-bridge latency=0  resources: irq:17 memory:a0600000-a0603fff
[/LIST]
  Thank you, any help is great, I am only 14 and I just need a bit of help.
  Also, if this doesn't work, will an older version of Ubuntu or a different Linux work?

---

### Post by nothingspecial on 2013-01-31
*Thread moved to **Networking & Wireless**.*

---

### Post by varunendra on 2013-02-03
> **skyler440 said:**
> *-network  description: Network controller  product: **[COLOR="Red"]BCM4331[/COLOR]** 802.11a/b/g/n

Hi skyler, and welcome to the forums! :)

I see it is already 5 days since you posted, hope you found the solution.

If, however, you are still looking for it, read this thread : [http://ubuntuforums.org/showthread.php?t=1966236](http://ubuntuforums.org/showthread.php?t=1966236)

---

