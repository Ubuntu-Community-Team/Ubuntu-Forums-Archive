---
title: "suspend and resume causing problem for clean 11.10 install Dell wireless"
date: 2012-01-15
forum: Networking &amp; Wireless
---

### Post by jamesbon on 2012-01-15
I formatted my laptop just now with Ubuntu 11.10 amd 64.
After a reboot and installing Additional Drivers where it showed 
Broadcom STA driver downloaded and installed.Upon a reboot I could not connect to wireless network lspci -vnn out is following

```
c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev ff) (prog-if ff)
        !!! Unknown header type 7f
        Kernel driver in use: wl
        Kernel modules: wl, ssb

```

after another reboot lspci -vnn output is following

```

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
        Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f69fc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
        Capabilities: [58] Vendor Specific Information: Len=78 <?>
        Capabilities: [e8] MSI: Enable- Count=1/1 Maskable- 64bit+
        Capabilities: [d0] Express Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [13c] Virtual Channel
        Capabilities: [16c] Power Budgeting <?>
        Kernel driver in use: wl

```
After another reboot I am unable to connect to the wireless network infact the wireless network option does not show in drop down menu.
```
uname -a 

Linux rin 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by carl4926 on 2012-01-15
You know that b43 works for your device
Solving bugs on closed source = Nil

Why not remove the proprietary driver and run the b43 firmware install

It may solve your issue. And if not, at least we can address it properly.

---

### Post by jamesbon on 2012-01-15
No I was not aware of this fact.Please let me know how to get with b43 open source driver I will do the required thing.

---

### Post by carl4926 on 2012-01-15
You need to remove the current driver. I think you can do that from the 'Additional Drivers' option

I'll PM you the rest

---

### Post by jamesbon on 2012-01-15
Thanks for the help things are working now.I shall observe the behavior of card and see if the same problem persists then I will open a new thread.For the time being I am closing this thread.

---

