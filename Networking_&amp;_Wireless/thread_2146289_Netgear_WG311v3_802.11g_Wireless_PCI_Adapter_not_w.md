---
title: "Netgear WG311v3 802.11g Wireless PCI Adapter not working"
date: 2013-05-18
forum: Networking &amp; Wireless
---

### Post by v8fusion on 2013-05-18
The interface is not working at all. Here is the comparison between my wired ethernet controller and the wireless one.

network@network-MS-7309:~$ lspci | grep -e 01:0
01:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
network@network-MS-7309:~$ 

network@network-MS-7309:~$ dmesg | grep -e 01:09
[    0.167409] pci 0000:01:09.0: [10ec:8139] type 0 class 0x000200
[    0.167424] pci 0000:01:09.0: reg 10: [io  0xef00-0xefff]
[    0.167437] pci 0000:01:09.0: reg 14: [mem 0xdffffc00-0xdffffcff]
[    0.167477] pci 0000:01:09.0: reg 30: [mem 0xdffc0000-0xdffdffff pref]
[    0.167505] pci 0000:01:09.0: supports D1 D2
[    0.167508] pci 0000:01:09.0: PME# supported from D1 D2 D3hot D3cold
[    0.167512] pci 0000:01:09.0: PME# disabled
[    0.949521] 8139cp 0000:01:09.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    0.950131] 8139too 0000:01:09.0: PCI INT A -> Link[LNKB] -> GSI 19 (level, low) -> IRQ 19
[    0.951094] 8139too 0000:01:09.0: eth0: RealTek RTL8139 at 0xef00, 00:13:f7:0b:d5:82, IRQ 19
[   11.970022] 8139too 0000:01:09.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
network@network-MS-7309:~$ dmesg | grep -e 01:0a
[    0.167530] pci 0000:01:0a.0: [11ab:1faa] type 0 class 0x000200
[    0.167549] pci 0000:01:0a.0: reg 10: [mem 0xdffe0000-0xdffeffff]
[    0.167560] pci 0000:01:0a.0: reg 14: [mem 0xdffb0000-0xdffbffff]
network@network-MS-7309:~$ 

I have installed the device driver in ndiswrapper.

network@network-MS-7309:~$ sudo ndiswrapper -l
mrv8335 : driver installed
    device (11AB:1FAA) present
network@network-MS-7309:~$ 

How do I get this guy working? Thanks in advance for the awesome help that comes from the Ubuntu community!

---

### Post by praseodym on 2013-05-18
Try these drivers:

[http://media.cdn.ubuntu-de.org/forum/attachments/19/38/1888522-marvel_8335_X32.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/19/38/1888522-marvel_8335_X32.tar.gz)

[http://media.cdn.ubuntu-de.org/forum/attachments/20/38/1888522-Marvel_8335_X64.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/20/38/1888522-Marvel_8335_X64.tar.gz)

Check:
```

modinfo ndiswrapper
dmesg | grep ndis
```

---

