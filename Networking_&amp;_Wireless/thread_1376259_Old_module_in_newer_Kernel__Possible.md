---
title: "Old module in newer Kernel ?? Possible ?"
date: 2010-01-09
forum: Networking &amp; Wireless
---

### Post by laihenyi on 2010-01-09
Dear Guys ,

I got a engineering sample wifi card - Intel wimax 5350.
This card work well with kernel 2.6.28-15-generic and earlier kernels.

However after kernel 2.6.28-16 , this card no longer support by newer kernel.
the error is "Unsupported EEPROM VER=0x21b < 0x21e CALIB=0x4 < 0x4"

I knew the reason is that card is a Engineering sample .. it should not get support in newer version kernels.

What i try to think is that "is it possible to replace old wifi module into the new wifi module in new kernel " and the system can also get works !?

I need help ! Thanks !

Below is message of dmesg.

------------------ Kernel version : vmlinuz-2.6.28-15-generic ----------------------------

[   11.683885] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   11.683888] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   11.683988] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.684076] iwlagn 0000:03:00.0: setting latency timer to 64
[   11.684166] iwlagn: Detected Intel Wireless WiFi Link 5350AGN REV=0x24
[   11.703256] iwlagn: Tunable channels: 13 802.11bg, 24 802.11a channels
[   11.703315] iwlagn 0000:03:00.0: irq 2298 for MSI/MSI-X

------------------ Kernel version : vmlinuz-2.6.28-17-generic ----------------------------

[    9.795853] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[    9.795855] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[    9.795940] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.795948] iwlagn 0000:03:00.0: setting latency timer to 64
[    9.795989] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5350AGN REV=0x24
[    9.814342] iwlagn 0000:03:00.0: Unsupported EEPROM VER=0x21b < 0x21e CALIB=0x4 < 0x4
[    9.814361] iwlagn 0000:03:00.0: PCI INT A disabled
[    9.814486] iwlagn: probe of 0000:03:00.0 failed with error -22

---

### Post by steveneddy on 2010-01-09
My response would be to use the kernel that works with your hardware unless you need the newer kernel for another hardware fix.

You can tell Synaptic to pin the software, or in other words,  cause the kernel not to be updated and all of your hardware continues to work.

Or use currently supported hardware.

Just because there is a newer kernel available does not mean that you need to run that kernel.

I have some older hardware at home that still runs on the 2.4.xx kernel quite well.

But in answer to your question, there may be a way to get that kernel module to operate correctly in the newer kernel.

This Google search

[http://www.google.com/search?hl=en&source=hp&q=Intel+wimax+5350+kernel+module&aq=f&oq=&aqi=g1](http://www.google.com/search?hl=en&source=hp&q=Intel+wimax+5350+kernel+module&aq=f&oq=&aqi=g1)

suggests that there may be an issue with this wifi card, though.

Hence my suggestion to use the kernel that just works. The simple answers are usually the best answers, unless you are on a Linux forum, then the user will want to fix the problem no matter what. lol

---

