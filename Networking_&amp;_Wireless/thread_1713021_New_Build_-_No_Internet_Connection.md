---
title: "New Build - No Internet Connection"
date: 2011-03-23
forum: Networking &amp; Wireless
---

### Post by Mpire on 2011-03-23
Hello all! I just finished with a new computer and I am trying Ubuntu for the first time. I have zero experience with anything other than windows, so please forgive my ignorance. I have googled and searched for an answer to no avail, but being absolutely new to linux I may just not know an answer when I see it.

After finishing the build I downloaded installed the latest ubuntu desktop, 64bit. It is installed, and up and running, but I have no internet connection. I don't know what to do from here. Any help would be greatly appreciated.

Here's some info I've seen requested in response to similar questions:

-Motherboard is Gigabyte GA-X58A-UD3R
-Internet is a wired connection to the motherboard.


-ifconfig:

eth0      Link encap:Ethernet  HWaddr 1c:6f:65:9f:3c:dc  
          inet6 addr: fe80::1e6f:65ff:fe9f:3cdc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12967 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2822071 (2.8 MB)  TX bytes:8322 (8.3 KB)
          Interrupt:48 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:736 errors:0 dropped:0 overruns:0 frame:0
          TX packets:736 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:56712 (56.7 KB)  TX bytes:56712 (56.7 KB)


-lspci -vv

07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 48
	Region 0: I/O ports at ce00 [size=256]
	Region 2: Memory at fbbff000 (64-bit, prefetchable) [size=4K]
	Region 4: Memory at fbbf8000 (64-bit, prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169



-lshw -C network

PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 06
       serial: 1c:6f:65:9f:3c:dc
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:48 ioport:ce00(size=256) memory:fbbff000-fbbfffff memory:fbbf8000-fbbfbfff

---

### Post by wyliecoyoteuk on 2011-03-23
not getting a DHCP address.
try:
```

sudo ifconfig eth0 down
sudo ifconfig eth0 up

```
sometimes that will wake a slow router up.

Mind you, it is getting an IPv6 address, just not IPv4.
I would try giving it a fixed IP, see if it works ok.

---

### Post by Mpire on 2011-03-23
sudo ifconfig eth0 down
sudo ifconfig eth0 up

That worked! Thank you kindly!

---

