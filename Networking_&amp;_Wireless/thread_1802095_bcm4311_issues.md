---
title: "bcm4311 issues"
date: 2011-07-11
forum: Networking &amp; Wireless
---

### Post by brysond89 on 2011-07-11
After spending many weeks trying to get wireless to work I am now resorting to ask for help. Here is the status.

bryson@Bryson:~$ ndiswrapper -l
bcmwl6 : driver installed
    device (14E4:4311) present (alternate driver: ssb)


I don't know if the above "E" should be "e"? Does punctuation matter?


bryson@Bryson:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


My wireless card (lspci)

04:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)



Using (sudo lspci -v)

04:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
    Subsystem: AMBIT Microsystem Corp. Device 0422
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at 80400000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 2
    Capabilities: [58] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [13c] Virtual Channel
    Kernel modules: wl, ssb


bryson@Bryson:~$ lspci -nn | grep 14e4
04:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
05:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)


I do not know where to go from here, as far as I know everything hat should be blacklisted is (.conf of course) Any suggestions?

More info on wireless card

bryson@Bryson:~$ sudo lshw -C Network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:80400000-80403fff

---

### Post by chili555 on 2011-07-11
The polite answer I am so famous for: Sure, I'd love to help.

The real answer I am screaming at my computer screen: *What a mess! *

You have not one, not two but three drivers competing and conflicting and none are doing the job for you. Do you have wired ethernet available so we can download things? I need a tranquilizer or three.

---

