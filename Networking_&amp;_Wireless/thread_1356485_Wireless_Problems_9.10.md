---
title: "Wireless Problems 9.10"
date: 2009-12-16
forum: Networking &amp; Wireless
---

### Post by portxabia on 2009-12-16
After upgrade to 9.10 my wireless connection runs so slow as to be useless sometimes it won't run at all, the output from lspci is : 
06:02.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
    Subsystem: AMBIT Microsystem Corp. Device 0418
    Flags: bus master, medium devsel, latency 168, IRQ 22
    Memory at c0200000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath5k
    Kernel modules: ath5k
Does anyone know why capabilities says access denied is it something I control

---

### Post by drpjkurian on 2009-12-16
> **portxabia said:**
> After upgrade to 9.10 my wireless connection runs so slow as to be useless sometimes it won't run at all, the output from lspci is : 
06:02.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
    Subsystem: AMBIT Microsystem Corp. Device 0418
    Flags: bus master, medium devsel, latency 168, IRQ 22
    Memory at c0200000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath5k
    Kernel modules: ath5k
Does anyone know why capabilities says access denied is it something I control

Hi portxabia

Please follow the instructions as mentioned in my thread. It might help you.
[http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

Best of luck
Dr Kurian

---

### Post by portxabia on 2009-12-16
Thanks for that, I have installed madwifi driver before without success but I like the look of your code so will give it another try, I am in Windows at the moment will try it tomorrow many thanks in anticipation.

---

