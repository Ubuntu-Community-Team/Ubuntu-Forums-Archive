---
title: "Switched to 11.04, wireless not working at all"
date: 2011-09-16
forum: Networking &amp; Wireless
---

### Post by bobthe on 2011-09-16
I have a button on my keyboard to turn the wifi on/off. But it is being lit up as orange indicating its off. Whenever i press it, it doesn't do anything. And because of this I'm not able to connect to any wireless networks. 

Please help me!!!

Also, I'm on a hp dv6-6135dx if that helps.

---

### Post by pytheas22 on 2011-09-16
What is the output of:
```

sudo rfkill list all
dmesg | grep -ie radio -ie wlan
lshw -C Network
```

---

### Post by bobthe on 2011-09-16
this is what it says:
 
 *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: 10:1f:74:0d:7c:54
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 ioport:2000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network UNCLAIMED
       description: Network controller
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0200000-f020ffff

---

### Post by bobthe on 2011-09-16
bump!! someone please help me!!

---

### Post by pytheas22 on 2011-09-16
Please be patient.  No one on this site is being paid and you shouldn't expect instantaneous responses.

Your wireless card is not being recognized by the system, so you will need to install a driver for it.  To help you do that I'll need to know exactly what kind of wireless card you have, however.  Please post the output of these commands:
```

lsusb
lspci -nn
uname -rm
dmesg | grep -ie rt -ie wlan
```

---

### Post by kvmapr on 2011-09-21
I seem to have the same problem, so let me jump in and provide my data:

lsusb
Bus 002 Device 003: ID 0408:03f1 Quanta Computer, Inc. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 [8086:3b4a] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
02:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)

uname -rm
2.6.38-11-generic-pae i686

dmesg | grep -ie rt -ie wlan
[    0.000000] ACPI: WDRT bb7e2000 00047 (v01 HPQOEM SLIC-MPC 00000000 MSFT 01000013)
[    0.000000] Movable zone start PFN for each node
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:20000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] virtual kernel memory layout:
[    0.000285] mce: CPU supports 9 MCE banks
[    0.519115] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.679106] ACPI: (supports S0 S3 S4 S5)
[    0.729052] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.730495] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.733180] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.733322] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.733440] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.733558] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.733678] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.736335] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.736713] pci 0000:00:1f.2: PME# supported from D3hot
[    0.737160] pci 0000:02:00.0: supports D1 D2
[    0.737767] pci 0000:03:00.0: supports D1 D2
[    0.737769] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.738136] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.738307] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.738324] ACPI Warning: For \_SB_.PCI0.P0P1._PRT: Return Package has no elements (empty) (20110112/nspredef-456)
[    0.738361] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.738402] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.738452] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.844422] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.201326] Linux agpgart interface v0.103
[    1.201424] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[    1.201541] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.202485] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    1.202636] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    1.205209] ehci_hcd 0000:00:1a.0: debug port 2
[    1.209100] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.223388] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.223538] hub 1-0:1.0: 3 ports detected
[    1.223725] ehci_hcd 0000:00:1d.0: debug port 2
[    1.227616] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.243379] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.243524] hub 2-0:1.0: 3 ports detected
[    1.266973] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.266980] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.268688] rtc_cmos 00:07: RTC can wake from S4
[    1.268750] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.268781] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    1.271311] Using IPI No-Shortcut mode
[    1.271868] rtc_cmos 00:07: setting system clock to 2011-09-21 18:47:59 UTC (1316630879)
[    1.295174] <30>udev[70]: starting version 167
[    1.345569] r8169 0000:03:00.0: eth0: RTL8102e at 0xf845a000, 00:26:9e:e8:85:32, XID 04e00000 IRQ 40
[    1.352237] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    1.352243] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck pm led clo pio slum part ems sxs apst 
[    1.377188] ata1: SATA max UDMA/133 abar m2048@0xd6405000 port 0xd6405100 irq 41
[    1.377193] ata2: SATA max UDMA/133 abar m2048@0xd6405000 port 0xd6405180 irq 41
[    1.377202] ata5: SATA max UDMA/133 abar m2048@0xd6405000 port 0xd6405300 irq 41
[    1.377207] ata6: SATA max UDMA/133 abar m2048@0xd6405000 port 0xd6405380 irq 41
[    1.672103] hub 1-1:1.0: 6 ports detected
[    1.700897] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.916124] hub 2-1:1.0: 8 ports detected
[   17.400063] <30>udev[315]: starting version 167
[   17.634096] input: ENE eHome Infrared Remote Receiver as /devices/virtual/rc/rc0/input5
[   17.634226] rc0: ENE eHome Infrared Remote Receiver as /devices/virtual/rc/rc0
[   17.810112] input: HP WMI hotkeys as /devices/virtual/input/input7
[   17.830059] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   17.830062] [drm] Driver supports precise vblank timestamp query.
[   18.340647] ppdev: user-space parallel port driver
[ 2055.001927] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x100, writing 0x1ff)
[ 2055.001942] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0x20004040, writing 0x4040)
[ 2055.001993] pcieport 0000:00:1c.1: restoring config space at offset 0xf (was 0x200, writing 0x2ff)
[ 2055.002054] pcieport 0000:00:1c.4: restoring config space at offset 0xf (was 0x100, writing 0x1ff)
[ 2055.002069] pcieport 0000:00:1c.4: restoring config space at offset 0x7 (was 0x20002020, writing 0x2020)
[ 2055.003323] sd 0:0:0:0: [sda] Starting disk
[ 2058.052286] Restarting tasks ... done.

---

### Post by kvmapr on 2011-09-21
Just FYI ...

I found another thread here that discussed a similar problem. In that thread there was a link to some directions that I've followed to successfully activate the wireless driver.

That thread is at this link:
[http://ubuntuforums.org/showthread.php?t=1789409](http://ubuntuforums.org/showthread.php?t=1789409)

And the instructions I followed are at this link:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

