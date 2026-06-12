---
title: "ethernet not working in RC forcedeth driver"
date: 2010-10-01
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Salane on 2010-10-01
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a6c
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 45
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at ec00 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth
sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:1f:c6:5f:4c:84
Sending on   LPF/eth0/00:1f:c6:5f:4c:84
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
dmesg|grep forcedeth
[    2.755699] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    2.755966] forcedeth 0000:00:07.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
[    2.755970] forcedeth 0000:00:07.0: setting latency timer to 64
[    3.274363] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1f:c6:5f:4c:84
[    3.274367] forcedeth 0000:00:07.0: highdma pwrctl mgmt lnktim msdesc-v3
[   65.663282] forcedeth 0000:00:07.0: irq 45 for MSI/MSI-X

---

### Post by dino99 on 2010-10-01
try:

sudo modprobe -r forcedeth
sudo modprobe forcedeth
sudo /etc/init.d/networking restart

then look at dmesg: latest lines written after you have applied commands above

---

### Post by coffeecat on 2010-10-01
I'm posting from the Maverick rc live CD using a different nvidia ethenet controller, but using the forcedeth driver:

```
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
    Subsystem: ABIT Computer Corp. Device 1c2f
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 47
    Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at d800 [size=8]
    Memory at fe02a000 (32-bit, non-prefetchable) [size=256]
    Memory at fe029000 (32-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth
```Ethernet autoconnected for me on bootup:

```
ubuntu@ubuntu:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:50:8d:bd:a3:95
Sending on   LPF/eth0/00:50:8d:bd:a3:95
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.4 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.4 from 192.168.1.1
bound to 192.168.1.4 -- renewal in 114881 seconds.
```I think this is your problem:

> **Salane said:**
> 
sudo dhclient eth0

...

No DHCPOFFERS received.

Check your router settings and your cabling. Have you tried setting a static IP address?

By the way, please use [noparse]```

```[/noparse] tags when posting output.

---

### Post by Salane on 2010-10-01
deleted

---

### Post by Salane on 2010-10-01
```

[  308.384925] forcedeth 0000:00:07.0: PCI INT A disabled
[  314.288816] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[  314.288854] forcedeth 0000:00:07.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
[  314.288864] forcedeth 0000:00:07.0: setting latency timer to 64
[  314.809908] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1f:c6:5f:4c:84
[  314.809917] forcedeth 0000:00:07.0: highdma pwrctl mgmt lnktim msi desc-v3
[  314.820457] forcedeth 0000:00:07.0: irq 45 for MSI/MSI-X
[  314.820651] eth0: no link during initialization.
[  314.821459] ADDRCONF(NETDEV_UP): eth0: link is not ready

```

No it works in windows worked in Lucid stable, doesn't work in installer doesn't work in installed. directly connected to router that my wireless is connected to, router has Internet eth0 doesn't. Any other ideas on how to troubleshoot this?

---

### Post by cariboo on 2010-10-01
I get almost the same output, but mine works, it looks like the only difference is the MAC address and irq's:

```
dmesg | grep forcedeth
[    0.789721] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    0.790400] forcedeth 0000:00:07.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, low) -> IRQ 20
[    0.790404] forcedeth 0000:00:07.0: setting latency timer to 64
[    1.331008] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:24:21:da:4e:f4
[    1.331013] forcedeth 0000:00:07.0: highdma pwrctl mgmt lnktim msi desc-v3
[   15.977745] forcedeth 0000:00:07.0: irq 43 for MSI/MSI-X
```

---

### Post by Salane on 2010-10-01
Plain and simple fix. With windows 7 and 10.2, it didn't matter that I was using a crossover cable. With 10.10 it does. Just a push of the hub button fixed the problem. Was there a change in the driver that caused this change in behavior?

---

