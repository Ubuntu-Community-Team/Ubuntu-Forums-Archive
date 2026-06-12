---
title: "WiCD no wifi shown"
date: 2009-09-14
forum: Networking &amp; Wireless
---

### Post by elwylly on 2009-09-14
Hi,

I have the same problem on my desktop and on my netbook. I had no problem at all with my wifi until I updated ubuntu to 9.04. In both cases wicd stopped showing any network. I've tried reinstalling the driver but it's not working. Any suggestion? Maybe we could start with the netbook and then I'd try with the desktop.

I've run the command lspci -v|less:

03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
        Subsystem: Foxconn International, Inc. Device e008
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at 55200000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath_pci
        Kernel modules: ath5k, ath_pci

Thanks! I'm really desperated, I'd followed several similar posts but I never get it working.

---

### Post by atomizer on 2009-09-14
You should remove all the drivers you installed by yourself. Atheros ar242 is supported in the kernel in 9.04 and should work out of the box (I have to admid I did a clean install of 9.04 when I discovered my wireless didn't work any more after upgrade)

---

