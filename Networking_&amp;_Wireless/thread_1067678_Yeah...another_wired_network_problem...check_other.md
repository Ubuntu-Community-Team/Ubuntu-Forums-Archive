---
title: "Yeah...another wired network problem...check other threads, haven't found a solution"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by BenAtM on 2009-02-12
Hi

I am new to linux, just installed ubuntu 8.10 this week using dual boot with my windows xp and the wired network is not working. Detailed info:

```
_**ifconfig**_
**eth0 **     Link encap:Ethernet  HWaddr 00:1a:4d:f6:ef:e2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 **dropped:792717744** overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0x4000 
```

why all the packets dropped??

```
**_lshw_**
  ***-network**               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1a:4d:f6:ef:e2
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
 ** *-network DISABLED**
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 7a:9b:84:4c:34:9b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

How come the second network is disable?

 ```
**_dmesg|grep eth_**
[    2.800824] eth0: RTL8168c/8111c at 0xf884c000, 00:1a:4d:f6:ef:e2, XID 3c2000c0 IRQ 220
[    3.447976] Driver 'sr' needs updating - please use bus_type methods
[    3.452266] Driver 'sd' needs updating - please use bus_type methods
[   21.064865] r8169: eth0: link down
[  237.286609] ADDRCONF(NETDEV_UP): **eth0: link is not **ready
```

what does this "not ready" mean??

```
**_lspci -v_**
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: Giga-byte Technology Device e000
	Flags: bus master, fast devsel, latency 0, IRQ 220
	I/O ports at a000 [size=256]
	Memory at d3010000 (64-bit, prefetchable) [size=4K]
	Memory at d3000000 (64-bit, prefetchable) [size=64K]
	[virtual] Expansion ROM at d3020000 [disabled] [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [b0] MSI-X: Enable- Mask- TabSize=2
	Capabilities: [d0] Vital Product Data <?>
	Kernel driver in use: r8169
	Kernel modules: r8169
```


Can somebody please have a look, Thanks a lot!

---

### Post by chili555 on 2009-02-12
Here is the relevant data:> configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 **link=no** module=r8169 multicast=yes port=twisted pair
Is the ethernet cable present and firmly connected at both the ethernet card and the router/DSL box or other network device? Is the router/DSL box or other network device hooked up correctly and turned on? Finally, and I hate to even say this, but does the setup work perfectly in XP?

---

### Post by chili555 on 2009-02-12
This: [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448) may help, also.

---

### Post by superprash2003 on 2009-02-12
eth0 isnt getting an ip

---

### Post by odium1 on 2009-02-12
what kernel are you running? i corrected my problem by using kernelcheck to find the newest kernel (2.6.28-4) and install it for me.

---

### Post by BenAtM on 2009-02-12
> **chili555 said:**
> Here is the relevant data:Is the ethernet cable present and firmly connected at both the ethernet card and the router/DSL box or other network device? Is the router/DSL box or other network device hooked up correctly and turned on? Finally, and I hate to even say this, but does the setup work perfectly in XP?

Hi thanks for reply, the network working perfectly in XP without a touch.

---

### Post by BenAtM on 2009-02-12
> **chili555 said:**
> This: [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448) may help, also.

the description of this one looks same with mine, will give a try when I back home. Thanks :P

---

### Post by BenAtM on 2009-02-13
> **chili555 said:**
> This: [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448) may help, also.

This fixed the problem...thanks a lot!!!

---

