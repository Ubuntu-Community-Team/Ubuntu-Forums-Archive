---
title: "Wired network suddenly disconnected"
date: 2011-08-10
forum: Networking &amp; Wireless
---

### Post by chubble10 on 2011-08-10
Hey, I booted up the other day to find that ubuntu was saying that my wired network was unplugged/disconnected. Have made no recent changes to the network and connection light is on on both the ethernet switch and the pc. Have tried with live cds of ubuntu and other distros to find the same problem.
Anyone any ideas?

---

### Post by haqking on 2011-08-10
> **chubble10 said:**
> Hey, I booted up the other day to find that ubuntu was saying that my wired network was unplugged/disconnected. Have made no recent changes to the network and connection light is on on both the ethernet switch and the pc. Have tried with live cds of ubuntu and other distros to find the same problem.
Anyone any ideas?

OSI layer...go straight to Physical layer first.

Check your cable and connectors, if you have a spare, try nit

---

### Post by Basher101 on 2011-08-10
Maybe your cable/modem is broken? Or your ifconfig got somehow corrupted. Run ifconfig in terminal and post the output

---

### Post by haqking on 2011-08-10
> **Basher101 said:**
> Maybe your cable/modem is broken? Or your ifconfig got somehow corrupted. Run ifconfig in terminal and post the output

cable modem ?

he is connected to a switch

---

### Post by Basher101 on 2011-08-10
I did overlook that small part lol my bad^^ But yeah check the cable first and then report. Otherwise it should be your ifconfig

---

### Post by chubble10 on 2011-08-10
Modem etc. definitly work as xbox + other pcs work fine. Cable is ok too as works with xbox.
ifconfig results:
```
ubuntu@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:62 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4556 (4.5 KB)  TX bytes:4556 (4.5 KB)

ubuntu@ubuntu:~$
```

---

### Post by haqking on 2011-08-10
> **chubble10 said:**
> Modem etc. definitly work as xbox + other pcs work fine. Cable is ok too as works with xbox.
ifconfig results:
```
ubuntu@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:62 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4556 (4.5 KB)  TX bytes:4556 (4.5 KB)

ubuntu@ubuntu:~$
```

mmm no eth0 ?

try:

 ifup eth0

to see if you can bring it up

---

### Post by chubble10 on 2011-08-10
Nope, no apparent joy there
```
ubuntu@ubuntu:~$ ifup eth0
ifup: failed to open statefile /var/run/network/ifstate: Permission denied
ubuntu@ubuntu:~$ sudo ifup eth0
Ignoring unknown interface eth0=eth0.
ubuntu@ubuntu:~$ 

```

---

### Post by haqking on 2011-08-10
> **chubble10 said:**
> Nope, no apparent joy there
```
ubuntu@ubuntu:~$ ifup eth0
ifup: failed to open statefile /var/run/network/ifstate: Permission denied
ubuntu@ubuntu:~$ sudo ifup eth0
Ignoring unknown interface eth0=eth0.
ubuntu@ubuntu:~$ 

```

can you show us output of

lspci -v

---

### Post by chubble10 on 2011-08-11
ok then

```
ubuntu@ubuntu:~$ sudo lspci -v
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 8178
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=09 <?>

00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: ddf00000-dfffffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Capabilities: [88] Subsystem: Intel Corporation Device 0000
	Capabilities: [80] Power Management version 2
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [a0] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [140] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: 80000000-801fffff
	Prefetchable memory behind bridge: 0000000080200000-00000000803fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 8179
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: dde00000-ddefffff
	Capabilities: [40] Express Root Port (Slot-), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 8179
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 8000 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 8400 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 8800 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 9000 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at dddffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000b000-0000bfff
	Capabilities: [50] Subsystem: ASUSTeK Computer Inc. Device 8179

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
	Subsystem: ASUSTeK Computer Inc. P5KPL-VM Motherboard
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=0c <?>
	Kernel modules: leds-ss4200, iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. P5KPL-VM Motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: ASUSTeK Computer Inc. Device 2601
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 23
	I/O ports at a800 [size=8]
	I/O ports at a400 [size=4]
	I/O ports at a000 [size=8]
	I/O ports at 9800 [size=4]
	I/O ports at 9400 [size=16]
	Capabilities: [70] Power Management version 2
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
	Subsystem: ASUSTeK Computer Inc. P5KPL-VM Motherboard
	Flags: medium devsel, IRQ 10
	I/O ports at 0400 [size=32]
	Kernel modules: i2c-i801

01:01.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
	Subsystem: Creative Labs SB0570 [SB Audigy SE]
	Flags: bus master, medium devsel, latency 64, IRQ 21
	I/O ports at b800 [size=32]
	Capabilities: [dc] Power Management version 2
	Kernel driver in use: CA0106
	Kernel modules: snd-ca0106

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
	Subsystem: ASUSTeK Computer Inc. P5B
	Flags: bus master, fast devsel, latency 0, IRQ 43
	I/O ports at c800 [size=256]
	Memory at ddeff000 (64-bit, non-prefetchable) [size=4K]
	Expansion ROM at ddee0000 [disabled] [size=64K]
	Capabilities: [40] Power Management version 2
	Capabilities: [48] Vital Product Data
	Capabilities: [50] MSI: Enable+ Count=1/2 Maskable- 64bit+
	Capabilities: [60] Express Endpoint, MSI 00
	Capabilities: [84] Vendor Specific Information: Len=4c <?>
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [12c] Virtual Channel
	Capabilities: [148] Device Serial Number da-06-00-00-00-00-00-00
	Capabilities: [154] Power Budgeting <?>
	Kernel driver in use: r8169
	Kernel modules: r8169

04:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GT] (rev a1) (prog-if 00 [VGA controller])
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at df000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at de000000 (64-bit, non-prefetchable) [size=16M]
	I/O ports at e800 [size=128]
	Expansion ROM at ddfe0000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
	Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [128] Power Budgeting <?>
	Kernel driver in use: nouveau
	Kernel modules: nouveau, nvidiafb

ubuntu@ubuntu:~$ 
```

---

### Post by chubble10 on 2011-08-16
Should i just try getting a pci ethernet card like [this]("http://www.scan.co.uk/products/us-robotics-10-100-pci-network-card-uk-retail") and see if it works?

---

