---
title: "Dropped Connections with Netgear WG121"
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by alpage2 on 2009-02-17
I am running ubuntu 8.10, and have installed the windows drivers for my netgear WG121 wireless adapter according to the first section of this HOWTO:

[https://help.ubuntu.com/community/WifiDocs/Device/WG121?highlight=(WG121)|(NETGEAR](https://help.ubuntu.com/community/WifiDocs/Device/WG121?highlight=(WG121)|(NETGEAR)

When booting up ubuntu, the wireless network starts out fine, and I am able to begin loading web pages. But after a brief but variable length of time, both lights go out on the adapter, and the internet is no longer accessible.

some extracts from dmesg:

firstly, from the boot processes, showing the interface being set up:

> 
[   17.880661] wlan0: ethernet device 00:09:5b:a2:cc:76 using NDIS driver: netwg121, version: 0x10005, NDIS version: 0x501, vendor: 'NETGEAR WG121 802.11g Wireless USB2.0 Adapter', 0846:4210.F.conf
[   17.880708] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
[   17.880765] usbcore: registered new interface driver ndiswrapper
[   18.664419] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
[   18.669220] udev: renamed network interface wlan0 to wlan1


And then, when the lights go out .....  :(

> 
[  674.982067] ehci_hcd 0000:00:0f.3: force halt; handhake e085a824 00004000 00000000 -> -110
[  675.695754] irq 23: nobody cared (try booting with the "irqpoll" option)
[  675.695779] Pid: 5646, comm: firefox Tainted: P          2.6.27-11-generic #1
[  675.695784]  [<c037d236>] ? printk+0x1d/0x1f
[  675.695795]  [<c017824c>] __report_bad_irq+0x2c/0xa0
[  675.695803]  [<c01783d4>] note_interrupt+0x114/0x140
[  675.695808]  [<c0177141>] ? handle_IRQ_event+0x41/0x80
[  675.695813]  [<c0178a23>] handle_fasteoi_irq+0xb3/0xe0
[  675.695818]  [<c0106c15>] do_IRQ+0x45/0x80
[  675.695824]  [<c0137984>] ? irq_exit+0x44/0x90
[  675.695829]  [<c0113f8d>] ? smp_apic_timer_interrupt+0x5d/0x90
[  675.695837]  [<c0105003>] common_interrupt+0x23/0x30
[  675.695842]  =======================
[  675.695844] handlers:
[  675.695846] [<e08da9d0>] (usb_hcd_irq+0x0/0x90 [usbcore])
[  675.695895] Disabling IRQ #23
[  677.880035] ndiswrapper (mp_reset:64): wlan1 is being reset
[  677.880853] ndiswrapper (NdisWriteErrorLogEntry:190): log: C000138A, count: 3, return_address: e0b59c5f
[  677.880862] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0xc0000001
[  677.880866] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x6d695442
[  677.880869] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x37
[  697.880042] ndiswrapper (mp_reset:64): wlan1 is being reset
[  697.880789] ndiswrapper (NdisWriteErrorLogEntry:190): log: C000138A, count: 3, return_address: e0b59c5f
[  697.880797] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0xc0000001
[  697.880801] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x6d695442
[  697.880804] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x37


I'd be grateful for advice as to what is going wrong, and possible solutions.

Thanks in anticipation
Alan

---

