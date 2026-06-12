---
title: "Wifi Causes Ubuntu to Hang"
date: 2012-10-14
forum: Networking &amp; Wireless
---

### Post by Gorgok on 2012-10-14
Hello, 
I recently got a new laptop, a Toshiba Satellite C855D-S5205 and installed 12.04 (64 bit_ along side a clean install of Windows 7. Straight from the installation I could tell that I was going to have the issue: while installing while the live-cd was connected to wifi (yes, know...), it hang and I had to clear the partition and reinstall, this time while on a wired connection.

Now, I'm having the same problem. If I turn on the Wifi and connect to a network, the system hangs in 1 to 5 minutes. I have to restart to get it to work.

Here is my lspci - v
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device 8212
    Flags: bus master, fast devsel, latency 0, IRQ 16
    I/O ports at 3000 [size=256]
    Memory at f0200000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Kernel driver in use: rtl8192ce
    Kernel modules: rtl8192ce

I'm not to experienced with Ubuntu but am happy to learn
Thanks in advance

---

