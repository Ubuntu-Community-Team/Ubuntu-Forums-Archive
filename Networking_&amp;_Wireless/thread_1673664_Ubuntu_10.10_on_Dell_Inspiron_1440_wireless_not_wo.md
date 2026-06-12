---
title: "Ubuntu 10.10 on Dell Inspiron 1440 wireless not working"
date: 2011-01-22
forum: Networking &amp; Wireless
---

### Post by bruparel on 2011-01-22
I have spent all day trying to wireless network to work on my Dell Inspiron 1440, but no luck.

I followed the guide here:
[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

Here are the details of my network card:

root@bruparel-Inspiron-1440:/home/bruparel# lspci -n | grep 14e4
0c:00.0 0280: 14e4:4315 (rev 01)

Here are the more verbose details:

0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
        Subsystem: Dell Wireless 1397 WLAN Mini-Card
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f69fc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
        Capabilities: [58] Vendor Specific Information: Len=78 <?>
        Capabilities: [e8] MSI: Enable- Count=1/1 Maskable- 64bit+
        Capabilities: [d0] Express Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [13c] Virtual Channel
        Capabilities: [160] Device Serial Number 8a-9a-5f-ff-ff-eb-00-22
        Capabilities: [16c] Power Budgeting <?>
        Kernel driver in use: wl
        Kernel modules: wl, ssb


Things seem to install fine, but the wireless network remains unavailable (wireless network is disabled).

If someone can walk me through the trouble-shooting process, I will appreciate it.  I tried the solution suggested in the sticky at the top too
but no luck.

Thanks in advance.

Bharat

---

### Post by Metaljaz on 2011-01-23
If even though this posts refers to 9.10 give it a try:

[http://ubuntuforums.org/showthread.php?t=1568057](http://ubuntuforums.org/showthread.php?t=1568057)

---

