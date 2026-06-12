---
title: "Unbale to connect Internet thru Ubuntu"
date: 2009-08-29
forum: Networking &amp; Wireless
---

### Post by askbapi on 2009-08-29
Hi,

This is my system configuration :

CPU : Intel Core 2 duo 2.8 GHz
MotherBoard : Intel DG41TY
RAM : 2 GB DDR2 800

BOARD BAND Connection : BSNL
Modem : UT-3000R2U (ADSL2+ Modem)

My problem is that it cannot connect to internetm from Ubuntu 9.04. It could not find Ethernet port.

While i can connect thru WIndows XP

Can any one help me out.

---

### Post by x33a on 2009-08-29
are you using usb on windows or lan card?

try this command
```
sudo pppoeconf
```

---

### Post by askbapi on 2009-08-29
USing LAN CARD!  I tried to connect with USB in Ubuntu 9.04 too but same result.

---

### Post by Iowan on 2009-08-29
Post results of **ifconfig -a** and **lshw -C network**.

---

### Post by askbapi on 2009-08-29
**ifconfig -a  [OUTPUT]**

-------------------------------------------------
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:c5:98:2c  
          inet6 addr: fe80::21c:c0ff:fec5:982c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1836 (1.8 KB)
          Interrupt:252 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

pan0      Link encap:Ethernet  HWaddr c6:25:39:76:42:c4  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


------------------------------------------------

**lshm -C network [OUPUT]**
---------------------------------------------------
command not found

---

### Post by Iowan on 2009-08-29
> **askbapi said:**
> -------------------------------------------------
**lshm -C network [OUPUT]**
---------------------------------------------------
command not found**lsh[COLOR="Red"]w [/COLOR]-C network**

---

### Post by askbapi on 2009-08-30
**lshw -C network [OUTPUT]**
-----------------------------------------------
\ *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 00:1c:c0:c5:98:2c
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
 
 *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: f2:e4:44:07:14:de
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by Iowan on 2009-08-30
If the machine fails to get IP address,  [this]("http://ubuntuforums.org/showthread.php?t=1156441") one* might* help.  Disabling rfc3442 let my laptop get a (wired) DHCP address.

---

