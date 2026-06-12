---
title: "need windows driver for Atheros T77H121 wireless card"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by Landie_UK on 2009-11-08
I have followed the sticky ndiswrapper thread, I found the correct driver for this card but it is corrupt as one of the DLL files won't load.

 > *-network
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ndiswrapper latency=0 module=ndiswrapper
mark@mark-laptop:~$ dmesg | grep -e ndis -e wlan
[   30.820436] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   31.638222] ndiswrapper (link_pe_images:604): DLL initialize failed for athw.sys
[   31.638281] ndiswrapper: driver netathw (,03/27/2009,7.7.0.267) loaded
[   31.645766] ndiswrapper (mp_init:207): assuming WDM (non-NDIS) driver
[   31.702260] usbcore: registered new interface driver ndiswrapper


I have a Gateway LT31 series netbook and the only driver I can find is from gateway and the only card id I can find is T77H121 which isn't recognized by Atheros on their website. I have tried the generic Atheros driver from them it doesn't work. I didn't have to blacklist ATH_pci, does this mean I didn't have it and can I install it?
any help would be appreciated

---

