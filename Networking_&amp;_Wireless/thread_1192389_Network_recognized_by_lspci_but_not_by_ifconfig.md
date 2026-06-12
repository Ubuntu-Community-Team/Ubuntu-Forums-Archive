---
title: "Network recognized by lspci but not by ifconfig"
date: 2009-06-20
forum: Networking &amp; Wireless
---

### Post by p0rnflake on 2009-06-20
I've been having some bad luck with NIC's under Ubuntu 9.04 and have therefor found an old R8139 based card thats definitely supported ;)

There's a problem however.. The card is recognized and the module is present in the kernel - but it's not loaded correctly is seems according to dmesg outout - the card cant be brought up or seen by neither ifup og ifconfig.

I have an onboard RTL8111 aswell but I'm trying to replace this with the R8139 because of unresolved bugs.

```
lspci -v
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller
	Flags: bus master, fast devsel, latency 0, IRQ 2301
	I/O ports at ee00 [size=256]
	Memory at fdeff000 (64-bit, non-prefetchable) [size=4K]
	Memory at fddf0000 (64-bit, prefetchable) [size=64K]
	[virtual] Expansion ROM at fdd00000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

03:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at <unassigned> [disabled]
	Memory at fdbf0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel modules: 8139too, 8139cp

```

```
ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:30:18:a1:4a:4e  
          inet addr:10.0.0.100  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::230:18ff:fea1:4a4e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38435 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31308 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3953787 (3.9 MB)  TX bytes:3390436 (3.3 MB)
          Interrupt:253 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:54 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3728 (3.7 KB)  TX bytes:3728 (3.7 KB)

```

```

dmesg | grep 8169

[    2.381697] scsi1 : ata_piix
[    3.208776] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.208814] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.208848] r8169 0000:02:00.0: setting latency timer to 64
[    3.209112] r8169 0000:02:00.0: irq 2301 for MSI/MSI-X
[   19.281686] r8169: eth0: link up
[   19.281697] r8169: eth0: link up

dmesg | grep 8139
[    3.244552] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.244613] 8139cp 0000:03:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    3.251598] 8139too Fast Ethernet driver 0.9.28
[    3.251684] 8139too 0000:03:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.251691] 8139too 0000:03:01.0: region #0 not a PIO resource, aborting

```

I'm assuming it's the very last line thats causing the issue ??

---

### Post by p0rnflake on 2009-06-20
Some additional info..

```
sudo rtl8139-diag -f
rtl8139-diag.c:v2.13 2/28/2005 Donald Becker (becker@scyld.com)
 http://www.scyld.com/diag/index.html
Index #1: Found a RealTek (unknown chip type) adapter at 0xee00.
Realtek station address 00:30:18:a1:4a:4e, chip type 'Unknown version'.
  Receiver configuration: Normal unicast and hashed multicast
     Rx FIFO threshold 2048 bytes, maximum burst 1024 bytes, 8KB ring
  Transmitter enabled with NONSTANDARD! settings, maximum burst 1024 bytes.
  Flow control: Tx disabled  Rx disabled.
  The chip configuration is 0x05 0x1f, MII half-duplex mode.
  No interrupt sources are pending.
Index #2: Found a RealTek RTL8139 adapter at 0xfdbf0000.
Realtek station address bd:e6:ac:20:11:98, chip type 'Unknown version'.
  Receiver configuration: Unknown/invalid
     Rx FIFO threshold 2048 bytes, maximum burst 2048 bytes, 64KB ring
  Transmitter enabled with NONSTANDARD! settings, maximum burst 2048 bytes.
  Flow control: Tx enabled  Rx enabled.
  The chip configuration is 0xb4 0x9c, 10baseT half-duplex mode.
  Interrupt sources are pending.
   Rx Complete indication.
   Rx Error indication.
   Transmit OK indication.
   Transmit Error indication.
   Rx Buffer Overflow indication.
   Rx Buffer Underrun indication.
   Rx FIFO Overflow indication.
   unknown-0080 indication.
   unknown-0100 indication.
   unknown-0200 indication.
   PCS timeout - packet too long indication.
   PCI System Error indication.
   (null) indication.
   (null) indication.
   (null) indication.
   (null) indication.

```

---

