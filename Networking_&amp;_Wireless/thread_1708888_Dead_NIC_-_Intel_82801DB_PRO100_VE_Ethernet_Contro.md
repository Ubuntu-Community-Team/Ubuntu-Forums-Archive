---
title: "Dead NIC - Intel 82801DB PRO/100 VE Ethernet Controller"
date: 2011-03-17
forum: Networking &amp; Wireless
---

### Post by mjmtaiwan on 2011-03-17
Hi,

I have no reason to think this MB NIC is bad in a hardware sense as it worked fine 6 months ago (been on the shelf a while).  I updated to 10.10 from 9.4 (or thereabouts) thinking it might be software.

Here is the output (partial) from $lspci -nn
02:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller [8086:1039] (rev 81)

and $sudo lshw -C network

*-network               
       description: Ethernet interface
       product: 82801DB PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 81
       serial: 00:09:6b:55:68:eb
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:11 memory:c0100000-c0100fff ioport:2000(size=64)

One thing that looks suspicious is bus info: pci@000:02:08.0 but for all I know this is standard. 

Here is the output for $ dmesg | grep e100
[    0.208919] pci 0000:02:08.0: Firmware left e100 interrupts enabled; disabling
[    1.437316] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    1.437324] e100: Copyright(c) 1999-2006 Intel Corporation
[    1.437385] e100 0000:02:08.0: can't find IRQ for PCI INT A; probably buggy MP table
[    1.461444] e100 0000:02:08.0: PME# disabled
[    1.462902] e100 0000:02:08.0: eth0: addr 0xc0100000, irq 11, MAC addr 00:09:6b:55:68:eb
[ 1101.098147] e100 0000:02:08.0: eth0: NIC Link is Up 100 Mbps Full Duplex

I have a USB NIC installed for temporary internet. Here is $ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:09:6b:55:68:eb  
          inet6 addr: fe80::209:6bff:fe55:68eb/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:10:60:16:b1:d5  
          inet addr:192.168.1.109  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::210:60ff:fe16:b1d5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5237 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3800 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4110922 (4.1 MB)  TX bytes:533447 (533.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5920 (5.9 KB)  TX bytes:5920 (5.9 KB)



Of course, your help is greatly appreciated.

Michael

---

### Post by chili555 on 2011-03-17
> pci@000:02:08.0 but for all I know this is standard.
Perfectly normal. Every PCI device has a bus number; that's the one assigned to the built-in NIC.

What does the BIOS say about ACPI? Also, are IRQs set by the BIOS or the operating system; usually, that's known in the BIOS as plug and play.

Please look for and adjust these settings in the BIOS and check dmesg again. When this goes away, your NIC should come to life:> can't find IRQ for PCI INT A; probably buggy MP tableIf your MB sat on the shelf for some time, it's reasonable to assume that these settings in the BIOS reverted to some defaults which may be suitable for, say Win 98, but not for Linux.

---

### Post by mjmtaiwan on 2011-03-17
Chili,

Thanks for the reply.

In BIOS the ACPI BIOS IRQ is set to IRQ9
The ACPI Standby Mode is S3

When I run dmesg | grep IRQ I get:

[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.028000] ...trying to set up timer (IRQ0) through the 8259A ...
[    0.175776] PCI: Discovered primary peer bus 01 [IRQ]
[    0.175790] pci 0000:00:1f.0: PIIX/ICH IRQ router [8086:24c0]
[    0.248971] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.259842] ehci_hcd 0000:00:1d.7: can't find IRQ for PCI INT D; probably buggy MP table
[    0.334652] uhci_hcd 0000:00:1d.0: can't find IRQ for PCI INT A; probably buggy MP table
[    0.335436] uhci_hcd 0000:00:1d.1: can't find IRQ for PCI INT B; probably buggy MP table
[    0.336163] uhci_hcd 0000:00:1d.2: can't find IRQ for PCI INT C; probably buggy MP table
[    0.622718]  [<c01a7df4>] ? handle_IRQ_event+0x44/0x150
[    0.622739]  [<c05cf65c>] do_IRQ+0x4c/0xc0
[    0.622875] Disabling IRQ #9
[    1.427263] r8169 0000:02:0a.0: can't find IRQ for PCI INT C; probably buggy MP table
[    1.428248] r8169 0000:02:0a.0: eth0: RTL8169sb/8110sb at 0xf802e000, 00:14:d1:10:01:8d, XID 10000000 IRQ 9
[    1.454079] e100 0000:02:08.0: can't find IRQ for PCI INT A; probably buggy MP table
[   11.255347] Intel ICH 0000:00:1f.5: can't find IRQ for PCI INT B; probably buggy MP table
[   12.100921]  [<c01a7df4>] ? handle_IRQ_event+0x44/0x150
[   12.100950]  [<c05cf65c>] do_IRQ+0x4c/0xc0
[   12.101377] Disabling IRQ #9

and

[    0.622672] irq 9: nobody cared (try booting with the "irqpoll" option)
[   12.100832] irq 9: nobody cared (try booting with the "irqpoll" option)

$cat /proc/interrupts gives
  9:     218447   IO-APIC-fasteoi   ehci_hcd:usb1, eth2, Intel 82801DB-ICH4


Would changing the IRQ number in BIOS help?

In the mean time, I've slid in a Netgear NIC that works fine... just hate to waste a spare NIC in this machine if I can get the on board working.

---

### Post by chili555 on 2011-03-17
> Would changing the IRQ number in BIOS help?Do you have the option to set *all* the IRQs to 'autodetect?'

---

### Post by mjmtaiwan on 2011-03-17
No... I can change the ACPI BIOS to IRQ 9, 10 or 11

I do have the options to turn on "Plug and Play Operating System" and "Legacy Free" but don't know what they will do.

By the way, this is an IBM Netvista 8315, an old machine with BIOS from 2002 but it should still be capable of running 10.10

---

### Post by chili555 on 2011-03-17
> I do have the options to turn on "Plug and Play Operating System"Please try it, reboot and check dmesg for 'buggy' messages. I will be away for several hours; see you tomorrow.

---

### Post by mjmtaiwan on 2011-03-17
Same condition after setting "Plug and Play Operating System" in BIOS.

Hope this is the output you needed:
$ dmesg | grep buggy
[    0.712930] ehci_hcd 0000:00:1d.7: can't find IRQ for PCI INT D; probably buggy MP table
[    0.765865] uhci_hcd 0000:00:1d.0: can't find IRQ for PCI INT A; probably buggy MP table
[    0.810449] uhci_hcd 0000:00:1d.1: can't find IRQ for PCI INT B; probably buggy MP table
[    0.811130] uhci_hcd 0000:00:1d.2: can't find IRQ for PCI INT C; probably buggy MP table
[    1.393721] r8169 0000:02:0a.0: can't find IRQ for PCI INT C; probably buggy MP table
[    1.424594] e100 0000:02:08.0: can't find IRQ for PCI INT A; probably buggy MP table
[   11.672879] Intel ICH 0000:00:1f.5: can't find IRQ for PCI INT B; probably buggy MP table

---

### Post by chili555 on 2011-03-19
Let's have a look at:```
dmesg | grep -i acpi
dmesg | grep -i irq
```Thanks.

---

### Post by mjmtaiwan on 2011-03-19
Ok... so how do you like this.  I updated the BIOS, just for the heck of it, and the nic now works fine.

Thank you for your help.

I would recommend to others to take this step if they are installing a modern OS on an old machine.  My lesson is learned.

Thanks Chili, folks like you make computing tolerable.

---

