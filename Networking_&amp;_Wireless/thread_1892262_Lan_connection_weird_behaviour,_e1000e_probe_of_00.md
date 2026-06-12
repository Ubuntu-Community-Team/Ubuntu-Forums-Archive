---
title: "Lan connection weird behaviour, e1000e probe of 0000:00:19.0 failed with error -3"
date: 2011-12-07
forum: Networking &amp; Wireless
---

### Post by areq on 2011-12-07
[FONT=Fixedsys]Hi[/FONT]
I've recently installed xubuntu 11.10 and I'm having some problems with network interface detection. I depends on, whether I power on my computer using power button (cold start?) or I reboot from system menu. In the first situation, xubuntu has problems with loading module e1000e, ifconfig shows only lo iface, here is the dmesg output:
```

[    1.810299] e1000e: Intel(R) PRO/1000 Network Driver - 1.3.10-k2
[    1.810302] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    1.810332] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.810340] e1000e 0000:00:19.0: setting latency timer to 64
[    1.810420] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[    2.857269] e1000e 0000:00:19.0: PCI INT A disabled
[    2.857281] e1000e: probe of 0000:00:19.0 failed with error -3

```[FONT=Courier New]
[/FONT]The second situation, is just after the first - when I see no network, I  just use the system menu to reboot. After reboot network is working, ifconfig shows lo and eth1 iface,  dmesg shows:
[FONT=Courier New][SIZE=1]
[/SIZE][/FONT]```

[    1.826549] e1000e: Intel(R) PRO/1000 Network Driver - 1.3.10-k2
[    1.826551] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    1.826587] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.826596] e1000e 0000:00:19.0: setting latency timer to 64
[    1.826684] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[    2.102153] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) 00:01:29:00:a4:5b
[    2.102156] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.102208] e1000e 0000:00:19.0: eth0: MAC: 9, PHY: 9, PBA No: FFFFFF-0FF
[   13.887340] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[   13.940242] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[   15.489990] e1000e: eth1 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx
[   15.489994] e1000e 0000:00:19.0: eth1: 10/100 speed: disabling TSO


```[FONT=Courier New]
[/FONT]
Doing this start - reboot procedure, I can reproduce this problem everytime.

Some other info:
```

sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82578DC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth1
       version: 05
       serial: 00:01:29:00:a4:5b
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.3.10-k2 duplex=full firmware=0.10-5 ip=192.168.1.3 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:40 memory:f7fc0000-f7fdffff memory:f7ffc000-f7ffcfff ioport:cc00(size=32)


``````

Linux arekubu 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

``````

sudo lspci -v
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
    Subsystem: DFI Inc Device 0000
    Flags: fast devsel
    Capabilities: [40] #00 [0000]

00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: f8000000-fbefffff
    Prefetchable memory behind bridge: 00000000d4000000-00000000dfffffff
    Capabilities: [40] Subsystem: DFI Inc Device 0000
    Capabilities: [60] MSI: Enable- Count=1/2 Maskable+ 64bit-
    Capabilities: [90] Express Root Port (Slot-), MSI 00
    Capabilities: [e0] Power Management version 3
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [150] Access Control Services
    Capabilities: [160] Vendor Specific Information: ID=0002 Rev=0 Len=00c <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
    Subsystem: Device 00bd:0000
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Vendor Specific Information: ID=0000 Rev=0 Len=000 <?>

00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
    Subsystem: Device 00bd:0000
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Vendor Specific Information: ID=0000 Rev=0 Len=000 <?>

00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
    Subsystem: Device 00bd:0000
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Vendor Specific Information: ID=0000 Rev=0 Len=000 <?>

00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
    Subsystem: Device 00bd:0000
    Flags: fast devsel

00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
    Subsystem: Device 00bd:0000
    Flags: fast devsel

00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
    Subsystem: Device 00bd:0000
    Flags: fast devsel

00:19.0 Ethernet controller: Intel Corporation 82578DC Gigabit Network Connection (rev 05)
    Subsystem: Intel Corporation Device 0000
    Flags: bus master, fast devsel, latency 0, IRQ 40
    Memory at f7fc0000 (32-bit, non-prefetchable) [size=128K]
    Memory at f7ffc000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at cc00 [size=32]
    Capabilities: [c8] Power Management version 2
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [e0] PCI Advanced Features
    Kernel driver in use: e1000e
    Kernel modules: e1000e

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
    Subsystem: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f7ffa000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
    Subsystem: DFI Inc Device 0000
    Flags: bus master, fast devsel, latency 0, IRQ 41
    Memory at f7ff4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: c0200000-c03fffff
    Prefetchable memory behind bridge: 00000000c0400000-00000000c05fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: DFI Inc Device 0000
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fbf00000-fbffffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000c01fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: DFI Inc Device 0000
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
    Subsystem: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f7ff8000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a5) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
    Capabilities: [50] Subsystem: DFI Inc Device 0000

00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 05)
    Subsystem: DFI Inc Device 0000
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=10 <?>
    Kernel modules: iTCO_wdt

00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 05) (prog-if 8a [Master SecP PriP])
    Subsystem: DFI Inc Device 0000
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at ff90 [size=16]
    I/O ports at ffa0 [size=16]
    Capabilities: [70] Power Management version 3
    Capabilities: [b0] PCI Advanced Features
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
    Subsystem: DFI Inc Device 0000
    Flags: medium devsel, IRQ 10
    Memory at f7ff2000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 0400 [size=32]
    Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 05) (prog-if 85 [Master SecO PriO])
    Subsystem: DFI Inc Device 0000
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at c800 [size=8]
    I/O ports at c480 [size=4]
    I/O ports at c400 [size=8]
    I/O ports at c080 [size=4]
    I/O ports at c000 [size=16]
    I/O ports at bc00 [size=16]
    Capabilities: [70] Power Management version 3
    Capabilities: [b0] PCI Advanced Features
    Kernel driver in use: ata_piix

01:00.0 VGA compatible controller: nVidia Corporation GF104 [GeForce GTX 460] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Micro-Star International Co., Ltd. N460GTX Cyclone 1GD5/OC
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f8000000 (32-bit, non-prefetchable) [size=32M]
    Memory at d8000000 (64-bit, prefetchable) [size=128M]
    Memory at d4000000 (64-bit, prefetchable) [size=64M]
    I/O ports at dc00 [size=128]
    [virtual] Expansion ROM at fbe80000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information: Len=14 <?>
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current, nouveau, nvidiafb

01:00.1 Audio device: nVidia Corporation GF104 High Definition Audio Controller (rev a1)
    Subsystem: Micro-Star International Co., Ltd. N460GTX Cyclone 1GD5/OC
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fbe7c000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

03:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02) (prog-if 01 [AHCI 1.0])
    Subsystem: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fbffe000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: [68] Power Management version 2
    Capabilities: [50] Express Legacy Endpoint, MSI 01
    Kernel driver in use: ahci
    Kernel modules: ahci

03:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02) (prog-if 85 [Master SecO PriO])
    Subsystem: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller
    Flags: bus master, fast devsel, latency 0, IRQ 17
    I/O ports at ec00 [size=8]
    I/O ports at e880 [size=4]
    I/O ports at e800 [size=8]
    I/O ports at e480 [size=4]
    I/O ports at e400 [size=16]
    Capabilities: [68] Power Management version 2
    Kernel driver in use: pata_jmicron
    Kernel modules: pata_jmicron

ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0
    Kernel driver in use: i7core_edac
    Kernel modules: i7core_edac

ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0


```I really don't know what to do with this problem, can someone help me?
[FONT=Courier New] 
[/FONT]

---

### Post by matt_symes on 2011-12-07
Hi

Don't get your hopes up as i am not sure what is causing this but i just wanted to try something.

Boot into Ubuntu so it fails and instead of rebooting open a terminal and type



```
sudo modprobe -r e1000e
```

Enter your password. It will not be echoed to the screen.

Then type

```
sudo modprobe e1000e
```

Does this bring up your interface ? Do you get errors (especially on the second command) ? Type themm both even if the first one fails.

Kind regards

---

### Post by areq on 2011-12-07
modprobe -r e1000e gives no error, nothing about it in dmesg
modprobe e1000e shows in dmesg in exactly the same way as originally (e1000e probe of 0000:00:19.0 failed with error -3, etc)

---

### Post by matt_symes on 2011-12-07
Hi
[FONT=monospace]
[/FONT]```
[    2.857269] e1000e 0000:00:19.0: PCI INT A disabled
```I am wondering if you are having issues with your interrupts. Maybe it's not assigning them correctly. I am not sure what would cause this. Have you looked at the noapic (etc) kernel boot options ?

When you boot and your lan fails, open a terminal and type

```
dmesg | grep '0000:00:19.0'
```It may give more info about the lan card on 19.0.

Also type

```
cat /proc/interrupts
```Post both back here. The second one (/proc/interrupts) post back after you have rebooted and you have LAN as well as when it fails.

Kind regards

---

### Post by areq on 2011-12-08
Unfortunately I am not an advanced user and I don't know what You mean by saying 'noapic (etc) kernel boot options'. Here is the suggested commands output:

With lan failing:
```

dmesg | grep '0000:00:19.0'
[    0.555283] pci 0000:00:19.0: [8086:10f0] type 0 class 0x000200
[    0.555299] pci 0000:00:19.0: reg 10: [mem 0xf7fc0000-0xf7fdffff]
[    0.555306] pci 0000:00:19.0: reg 14: [mem 0xf7ffc000-0xf7ffcfff]
[    0.555313] pci 0000:00:19.0: reg 18: [io  0xcc00-0xcc1f]
[    0.555356] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.555359] pci 0000:00:19.0: PME# disabled
[    1.793482] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.793492] e1000e 0000:00:19.0: setting latency timer to 64
[    1.793578] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[    2.842136] e1000e 0000:00:19.0: PCI INT A disabled
[    2.842142] e1000e: probe of 0000:00:19.0 failed with error -3

``````

sudo cat /proc/interrupts 
           CPU0       CPU1       CPU2       CPU3       
  0:         43          0          0      17038   IO-APIC-edge      timer
  1:        615          0          0         22   IO-APIC-edge      i8042
  8:          0          0          0          0   IO-APIC-edge      rtc0
  9:          0          0          0          0   IO-APIC-fasteoi   acpi
 14:          4          0          0        669   IO-APIC-edge      ata_piix
 15:       1017          0          0       5236   IO-APIC-edge      ata_piix
 16:      11348          0        314          0   IO-APIC-fasteoi   ehci_hcd:usb1, ahci, nvidia
 17:        333          0          0          0   IO-APIC-fasteoi   pata_jmicron, hda_intel
 19:          0          0          0          0   IO-APIC-fasteoi   ata_piix
 23:          0         45          0          0   IO-APIC-fasteoi   ehci_hcd:usb2
 40:          0        103          0        268   PCI-MSI-edge      hda_intel
NMI:          0          0          0          0   Non-maskable interrupts
LOC:       8440       8183       5094       1659   Local timer interrupts
SPU:          0          0          0          0   Spurious interrupts
PMI:          0          0          0          0   Performance monitoring interrupts
IWI:          0          0          0          0   IRQ work interrupts
RES:      10427       9234       6496       4109   Rescheduling interrupts
CAL:        518        591        369        508   Function call interrupts
TLB:        162        183        130        129   TLB shootdowns
TRM:          0          0          0          0   Thermal event interrupts
THR:          0          0          0          0   Threshold APIC interrupts
MCE:          0          0          0          0   Machine check exceptions
MCP:          2          2          2          2   Machine check polls
ERR:          0
MIS:          0

```After reboot, with lan working:
```

dmesg | grep '0000:00:19.0'
[    0.562981] pci 0000:00:19.0: [8086:10f0] type 0 class 0x000200
[    0.562997] pci 0000:00:19.0: reg 10: [mem 0xf7fc0000-0xf7fdffff]
[    0.563004] pci 0000:00:19.0: reg 14: [mem 0xf7ffc000-0xf7ffcfff]
[    0.563011] pci 0000:00:19.0: reg 18: [io  0xcc00-0xcc1f]
[    0.563054] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.563058] pci 0000:00:19.0: PME# disabled
[    1.863911] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.863919] e1000e 0000:00:19.0: setting latency timer to 64
[    1.864000] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[    2.135319] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) 00:01:29:00:a4:5b
[    2.135322] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.135374] e1000e 0000:00:19.0: eth0: MAC: 9, PHY: 9, PBA No: FFFFFF-0FF
[   15.616780] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[   15.672549] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[   17.163331] e1000e 0000:00:19.0: eth1: 10/100 speed: disabling TSO

``````

sudo cat /proc/interrupts 
           CPU0       CPU1       CPU2       CPU3       
  0:         43          0          0      11545   IO-APIC-edge      timer
  1:         85          0          0         30   IO-APIC-edge      i8042
  8:          0          0          0          0   IO-APIC-edge      rtc0
  9:          0          0          0          0   IO-APIC-fasteoi   acpi
 14:          4          0          0        669   IO-APIC-edge      ata_piix
 15:        322          0          0       5842   IO-APIC-edge      ata_piix
 16:       8198          0       4434          0   IO-APIC-fasteoi   ehci_hcd:usb1, ahci, nvidia
 17:        314          0          0          0   IO-APIC-fasteoi   pata_jmicron, hda_intel
 19:          0          0          0          0   IO-APIC-fasteoi   ata_piix
 23:          0         45          0          0   IO-APIC-fasteoi   ehci_hcd:usb2
 40:       1010          0          0          0   PCI-MSI-edge      eth1
 41:          0          0          0        388   PCI-MSI-edge      hda_intel
NMI:          0          0          0          0   Non-maskable interrupts
LOC:       6956       5124       4322       1453   Local timer interrupts
SPU:          0          0          0          0   Spurious interrupts
PMI:          0          0          0          0   Performance monitoring interrupts
IWI:          0          0          0          0   IRQ work interrupts
RES:       8993       8667       6320       2710   Rescheduling interrupts
CAL:        425        642        548        494   Function call interrupts
TLB:        159        160        142        220   TLB shootdowns
TRM:          0          0          0          0   Thermal event interrupts
THR:          0          0          0          0   Threshold APIC interrupts
MCE:          0          0          0          0   Machine check exceptions
MCP:          2          2          2          2   Machine check polls
ERR:          0
MIS:          0

```I think something is wrong with these lines:
Lan failing
```

 40:          0        103          0        268   PCI-MSI-edge      hda_intel

```Lan ok
```

 40:       1010          0          0          0   PCI-MSI-edge      eth1
 41:          0          0          0        388   PCI-MSI-edge      hda_intel

```

---

### Post by matt_symes on 2011-12-11
Hi

That does look like an interrupt issue. 

What kernel are you using and do you have the most up to date BIOS ?

Have a read of this for information about kernel parameters (noapci and nolapci). They may help.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Kind regards

---

### Post by areq on 2011-12-25
I am using the latest bios from the dfi site. Kernel is 3.0.0-14-generic. I've tried to boot system with parameters acpi_osi="Linux", noapic, nolapic in various combinations, but still there is no lan after first boot. Here is the log with those three parameters present:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-14-generic (buildd@allspice) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 (Ubuntu 3.0.0-14.23-generic 3.0.9)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic root=UUID=a303a224-b575-4c3b-970c-c5bce24b9485 ro acpi_osi=Linux noapic nolapic quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf680000 (usable)
[    0.000000]  BIOS-e820: 00000000bf680000 - 00000000bf68e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf68e000 - 00000000bf6d0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf6d0000 - 00000000bf6e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf6ed000 - 00000000bf700000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf800000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffa00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI:    /LP DK P55-T3eH9, BIOS 080015  08/27/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-E3FFF write-protect
[    0.000000]   E4000-E7FFF write-through
[    0.000000]   E8000-EBFFF write-protect
[    0.000000]   EC000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 100000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 base 0BFF00000 mask FFFF00000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 4GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 1GB, type UC
[    0.000000] reg 3, base: 3071MB, range: 1MB, type UC
[    0.000000] total RAM covered: 4095M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 2M     num_reg: 4      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3071MB, range: 1MB, type UC
[    0.000000] reg 3, base: 4GB, range: 1GB, type WB
[    0.000000] e820 update range: 00000000bff00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbf680 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff88000009a000] 9a000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000bf680000
[    0.000000]  0000000000 - 00bf600000 page 2M
[    0.000000]  00bf600000 - 00bf680000 page 4k
[    0.000000] kernel direct mapping tables up to bf680000 @ 1fffb000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000140000000
[    0.000000]  0100000000 - 0140000000 page 2M
[    0.000000] kernel direct mapping tables up to 140000000 @ bf67a000-bf680000
[    0.000000] RAMDISK: 365b2000 - 372d1000
[    0.000000] ACPI: RSDP 00000000000f9a30 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 00000000bf680100 00054 (v01 082710 XSDT1410 20100827 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000bf680290 000F4 (v03 082710 FACP1410 20100827 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000bf680460 070D5 (v01  P55DK P55DK000 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 00000000bf68e000 00040
[    0.000000] ACPI: APIC 00000000bf680390 0008C (v01 082710 APIC1410 20100827 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000bf680420 0003C (v01 082710 OEMMCFG  20100827 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000bf68e040 00072 (v01 082710 OEMB1410 20100827 MSFT 00000097)
[    0.000000] ACPI: GSCI 00000000bf68e0c0 02024 (v01 082710 GMCHSCI  20100827 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000bf691330 00363 (v01 DpgPmm    CpuPm 00000012 INTL 20051117)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000140000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000140000000
[    0.000000]   NODE_DATA [000000013fffb000 - 000000013fffffff]
[    0.000000]  [ffffea0000000000-ffffea00045fffff] PMD -> [ffff88013b600000-ffff88013edfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bf680
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 1046031
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3922 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 765624 pages, LIFO batch:31
[    0.000000]   Normal zone: 3584 pages used for memmap
[    0.000000]   Normal zone: 258560 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000] MPTABLE: OEM ID: INTEL   
[    0.000000] MPTABLE: Product ID: PIKETON     
[    0.000000] MPTABLE: APIC at: 0xFEE00000
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] Processor #2
[    0.000000] Processor #4
[    0.000000] Processor #6
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] Processors: 4
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bf680000 - 00000000bf68e000
[    0.000000] PM: Registered nosave memory: 00000000bf68e000 - 00000000bf6d0000
[    0.000000] PM: Registered nosave memory: 00000000bf6d0000 - 00000000bf6e0000
[    0.000000] PM: Registered nosave memory: 00000000bf6e0000 - 00000000bf6ed000
[    0.000000] PM: Registered nosave memory: 00000000bf6ed000 - 00000000bf700000
[    0.000000] PM: Registered nosave memory: 00000000bf700000 - 00000000bf800000
[    0.000000] PM: Registered nosave memory: 00000000bf800000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffa00000
[    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88013fc00000 s79616 r8192 d22784 u524288
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1028106
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic root=UUID=a303a224-b575-4c3b-970c-c5bce24b9485 ro acpi_osi=Linux noapic nolapic quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 4033360k/5242880k available (6109k kernel code, 1058756k absent, 150764k reserved, 4876k data, 984k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2806.385 MHz processor.
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 5612.77 BogoMIPS (lpj=11225540)
[    0.000005] pid_max: default: 32768 minimum: 301
[    0.000025] Security Framework initialized
[    0.000039] AppArmor: AppArmor initialized
[    0.000040] Yama: becoming mindful.
[    0.000380] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001687] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.002258] Mount-cache hash table entries: 256
[    0.002356] Initializing cgroup subsys cpuacct
[    0.002360] Initializing cgroup subsys memory
[    0.002366] Initializing cgroup subsys devices
[    0.002367] Initializing cgroup subsys freezer
[    0.002369] Initializing cgroup subsys net_cls
[    0.002370] Initializing cgroup subsys blkio
[    0.002375] Initializing cgroup subsys perf_event
[    0.002396] CPU: Physical Processor ID: 0
[    0.002397] CPU: Processor Core ID: 0
[    0.002401] mce: CPU supports 9 MCE banks
[    0.002410] using mwait in idle threads.
[    0.004043] ACPI: Core revision 20110413
[    0.007059] ACPI: setting ELCR to 0200 (from 0ce0)
[    0.031549] ftrace: allocating 25647 entries in 101 pages
[    0.037838] SMP disabled
[    0.037840] Performance Events: PEBS fmt1+, erratum AAJ80 worked around, Nehalem events, 
[    0.037844] no APIC, boot with the "lapic" boot parameter to force-enable it.
[    0.037845] no hardware sampling interrupt available.
[    0.037847] Intel PMU driver.
[    0.037849] ... version:                3
[    0.037850] ... bit width:              48
[    0.037851] ... generic registers:      4
[    0.037852] ... value mask:             0000ffffffffffff
[    0.037853] ... max period:             000000007fffffff
[    0.037854] ... fixed-purpose events:   3
[    0.037855] ... event mask:             000000070000000f
[    0.038125] Brought up 1 CPUs
[    0.038127] Total of 1 processors activated (5612.77 BogoMIPS).
[    0.038194] devtmpfs: initialized
[    0.038283] PM: Registering ACPI NVS region at bf68e000 (270336 bytes)
[    0.039480] print_constraints: dummy: 
[    0.039503] Time: 19:51:59  Date: 12/25/11
[    0.039531] NET: Registered protocol family 16
[    0.039607] ACPI: bus type pci registered
[    0.039648] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.039650] PCI: not using MMCONFIG
[    0.039651] PCI: Using configuration type 1 for base access
[    0.040197] bio: create slab <bio-0> at 0
[    0.040249] ACPI: Added _OSI(Linux)
[    0.041181] ACPI: EC: Look up EC in DSDT
[    0.042481] ACPI: Executed 1 blocks of module-level executable AML code
[    0.044482] ACPI: SSDT 00000000bf6900f0 01238 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    0.044756] ACPI: Dynamic OEM Table Load:
[    0.044758] ACPI: SSDT           (null) 01238 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    0.045221] ACPI: Interpreter enabled
[    0.045223] ACPI: (supports S0 S1 S3 S4 S5)
[    0.045237] ACPI: Using PIC for interrupt routing
[    0.045253] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.046327] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.078867] ACPI: No dock devices found.
[    0.078869] HEST: Table not found.
[    0.078871] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.079004] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.079127] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.079129] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.079131] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.079133] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.079135] pci_root PNP0A08:00: host bridge window [mem 0xbff00000-0xdfffffff]
[    0.079136] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfed8ffff]
[    0.079146] pci 0000:00:00.0: [8086:d131] type 0 class 0x000600
[    0.079185] pci 0000:00:03.0: [8086:d138] type 1 class 0x000604
[    0.079219] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.079221] pci 0000:00:03.0: PME# disabled
[    0.079238] pci 0000:00:08.0: [8086:d155] type 0 class 0x000880
[    0.079283] pci 0000:00:08.1: [8086:d156] type 0 class 0x000880
[    0.079327] pci 0000:00:08.2: [8086:d157] type 0 class 0x000880
[    0.079370] pci 0000:00:08.3: [8086:d158] type 0 class 0x000880
[    0.079415] pci 0000:00:10.0: [8086:d150] type 0 class 0x000880
[    0.079452] pci 0000:00:10.1: [8086:d151] type 0 class 0x000880
[    0.079506] pci 0000:00:19.0: [8086:10f0] type 0 class 0x000200
[    0.079522] pci 0000:00:19.0: reg 10: [mem 0xf7fc0000-0xf7fdffff]
[    0.079529] pci 0000:00:19.0: reg 14: [mem 0xf7ffc000-0xf7ffcfff]
[    0.079537] pci 0000:00:19.0: reg 18: [io  0xcc00-0xcc1f]
[    0.079580] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.079583] pci 0000:00:19.0: PME# disabled
[    0.079603] pci 0000:00:1a.0: [8086:3b3c] type 0 class 0x000c03
[    0.079622] pci 0000:00:1a.0: reg 10: [mem 0xf7ffa000-0xf7ffa3ff]
[    0.079687] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.079690] pci 0000:00:1a.0: PME# disabled
[    0.079710] pci 0000:00:1b.0: [8086:3b56] type 0 class 0x000403
[    0.079723] pci 0000:00:1b.0: reg 10: [mem 0xf7ff4000-0xf7ff7fff 64bit]
[    0.079771] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.079774] pci 0000:00:1b.0: PME# disabled
[    0.079790] pci 0000:00:1c.0: [8086:3b42] type 1 class 0x000604
[    0.079838] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.079841] pci 0000:00:1c.0: PME# disabled
[    0.079860] pci 0000:00:1c.4: [8086:3b4a] type 1 class 0x000604
[    0.079908] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.079911] pci 0000:00:1c.4: PME# disabled
[    0.079935] pci 0000:00:1d.0: [8086:3b34] type 0 class 0x000c03
[    0.079954] pci 0000:00:1d.0: reg 10: [mem 0xf7ff8000-0xf7ff83ff]
[    0.080019] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.080023] pci 0000:00:1d.0: PME# disabled
[    0.080040] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    0.080089] pci 0000:00:1f.0: [8086:3b02] type 0 class 0x000601
[    0.080189] pci 0000:00:1f.2: [8086:3b20] type 0 class 0x000101
[    0.080203] pci 0000:00:1f.2: reg 10: [io  0x0000-0x0007]
[    0.080209] pci 0000:00:1f.2: reg 14: [io  0x0000-0x0003]
[    0.080216] pci 0000:00:1f.2: reg 18: [io  0x0000-0x0007]
[    0.080223] pci 0000:00:1f.2: reg 1c: [io  0x0000-0x0003]
[    0.080230] pci 0000:00:1f.2: reg 20: [io  0xff90-0xff9f]
[    0.080237] pci 0000:00:1f.2: reg 24: [io  0xffa0-0xffaf]
[    0.080268] pci 0000:00:1f.3: [8086:3b30] type 0 class 0x000c05
[    0.080281] pci 0000:00:1f.3: reg 10: [mem 0xf7ff2000-0xf7ff20ff 64bit]
[    0.080299] pci 0000:00:1f.3: reg 20: [io  0x0400-0x041f]
[    0.080327] pci 0000:00:1f.5: [8086:3b26] type 0 class 0x000101
[    0.080340] pci 0000:00:1f.5: reg 10: [io  0xc800-0xc807]
[    0.080347] pci 0000:00:1f.5: reg 14: [io  0xc480-0xc483]
[    0.080353] pci 0000:00:1f.5: reg 18: [io  0xc400-0xc407]
[    0.080360] pci 0000:00:1f.5: reg 1c: [io  0xc080-0xc083]
[    0.080367] pci 0000:00:1f.5: reg 20: [io  0xc000-0xc00f]
[    0.080374] pci 0000:00:1f.5: reg 24: [io  0xbc00-0xbc0f]
[    0.080444] pci 0000:01:00.0: [10de:0e22] type 0 class 0x000300
[    0.080453] pci 0000:01:00.0: reg 10: [mem 0xf8000000-0xf9ffffff]
[    0.080463] pci 0000:01:00.0: reg 14: [mem 0xd8000000-0xdfffffff 64bit pref]
[    0.080472] pci 0000:01:00.0: reg 1c: [mem 0xd4000000-0xd7ffffff 64bit pref]
[    0.080478] pci 0000:01:00.0: reg 24: [io  0xdc00-0xdc7f]
[    0.080485] pci 0000:01:00.0: reg 30: [mem 0xfbe80000-0xfbefffff pref]
[    0.080522] pci 0000:01:00.1: [10de:0beb] type 0 class 0x000403
[    0.080531] pci 0000:01:00.1: reg 10: [mem 0xfbe7c000-0xfbe7ffff]
[    0.088420] pci 0000:00:03.0: PCI bridge to [bus 01-01]
[    0.088423] pci 0000:00:03.0:   bridge window [io  0xd000-0xdfff]
[    0.088425] pci 0000:00:03.0:   bridge window [mem 0xf8000000-0xfbefffff]
[    0.088429] pci 0000:00:03.0:   bridge window [mem 0xd4000000-0xdfffffff 64bit pref]
[    0.088464] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.088467] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.088471] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.088475] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.088524] pci 0000:03:00.0: [197b:2363] type 0 class 0x000101
[    0.088607] pci 0000:03:00.0: reg 24: [mem 0xfbffe000-0xfbffffff]
[    0.088648] pci 0000:03:00.0: PME# supported from D3hot
[    0.088652] pci 0000:03:00.0: PME# disabled
[    0.088680] pci 0000:03:00.1: [197b:2363] type 0 class 0x000101
[    0.088703] pci 0000:03:00.1: reg 10: [io  0xec00-0xec07]
[    0.088715] pci 0000:03:00.1: reg 14: [io  0xe880-0xe883]
[    0.088728] pci 0000:03:00.1: reg 18: [io  0xe800-0xe807]
[    0.088740] pci 0000:03:00.1: reg 1c: [io  0xe480-0xe483]
[    0.088753] pci 0000:03:00.1: reg 20: [io  0xe400-0xe40f]
[    0.088819] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.088831] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
[    0.088834] pci 0000:00:1c.4:   bridge window [io  0xe000-0xefff]
[    0.088837] pci 0000:00:1c.4:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.088842] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.088895] pci 0000:00:1e.0: PCI bridge to [bus 04-04] (subtractive decode)
[    0.088898] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.088901] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.088906] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.088908] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.088910] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.088911] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.088913] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.088915] pci 0000:00:1e.0:   bridge window [mem 0xbff00000-0xdfffffff] (subtractive decode)
[    0.088917] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfed8ffff] (subtractive decode)
[    0.088933] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.089064] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR1E._PRT]
[    0.089118] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR20._PRT]
[    0.089143] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR24._PRT]
[    0.089249]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.089380]  pci0000:00: ACPI _OSC request failed (AE_SUPPORT), returned control mask: 0x0d
[    0.089382] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.095667] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
[    0.095700] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[    0.095729] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 *10 11 12 14 15)
[    0.095761] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 *11 12 14 15)
[    0.095792] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 *11 12 14 15)
[    0.095823] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
[    0.095854] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 6 *7 10 11 12 14 15)
[    0.095885] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *6 7 10 11 12 14 15)
[    0.095950] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.095953] vgaarb: loaded
[    0.095954] vgaarb: bridge control possible 0000:01:00.0
[    0.096072] SCSI subsystem initialized
[    0.096100] libata version 3.00 loaded.
[    0.096129] usbcore: registered new interface driver usbfs
[    0.096135] usbcore: registered new interface driver hub
[    0.096150] usbcore: registered new device driver usb
[    0.096203] PCI: Using ACPI for IRQ routing
[    0.101835] PCI: Discovered peer bus ff
[    0.101856] pci 0000:ff:00.0: [8086:2c51] type 0 class 0x000600
[    0.101873] pci 0000:ff:00.1: [8086:2c81] type 0 class 0x000600
[    0.101891] pci 0000:ff:02.0: [8086:2c90] type 0 class 0x000600
[    0.101907] pci 0000:ff:02.1: [8086:2c91] type 0 class 0x000600
[    0.101925] pci 0000:ff:03.0: [8086:2c98] type 0 class 0x000600
[    0.101942] pci 0000:ff:03.1: [8086:2c99] type 0 class 0x000600
[    0.101958] pci 0000:ff:03.4: [8086:2c9c] type 0 class 0x000600
[    0.101975] pci 0000:ff:04.0: [8086:2ca0] type 0 class 0x000600
[    0.101990] pci 0000:ff:04.1: [8086:2ca1] type 0 class 0x000600
[    0.102006] pci 0000:ff:04.2: [8086:2ca2] type 0 class 0x000600
[    0.102021] pci 0000:ff:04.3: [8086:2ca3] type 0 class 0x000600
[    0.102038] pci 0000:ff:05.0: [8086:2ca8] type 0 class 0x000600
[    0.102054] pci 0000:ff:05.1: [8086:2ca9] type 0 class 0x000600
[    0.102070] pci 0000:ff:05.2: [8086:2caa] type 0 class 0x000600
[    0.102086] pci 0000:ff:05.3: [8086:2cab] type 0 class 0x000600
[    0.102338] PCI: pci_cache_line_size set to 64 bytes
[    0.102412] Expanded resource reserved due to conflict with PCI Bus 0000:00
[    0.102414] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.102415] reserve RAM buffer: 00000000bf680000 - 00000000bfffffff 
[    0.102476] NetLabel: Initializing
[    0.102477] NetLabel:  domain hash size = 128
[    0.102478] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.102486] NetLabel:  unlabeled traffic allowed by default
[    0.106602] AppArmor: AppArmor Filesystem Enabled
[    0.106618] pnp: PnP ACPI init
[    0.106626] ACPI: bus type pnp registered
[    0.106697] pnp 00:00: [bus 00-ff]
[    0.106699] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.106701] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.106702] pnp 00:00: [io  0x0d00-0xffff window]
[    0.106704] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.106705] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.106707] pnp 00:00: [mem 0xbff00000-0xdfffffff window]
[    0.106708] pnp 00:00: [mem 0xf0000000-0xfed8ffff window]
[    0.106742] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.106751] pnp 00:01: [mem 0xfc000000-0xfcffffff]
[    0.106753] pnp 00:01: [mem 0xfd000000-0xfdffffff]
[    0.106754] pnp 00:01: [mem 0xfe000000-0xfebfffff]
[    0.106755] pnp 00:01: [mem 0xfed14000-0xfed19fff]
[    0.106787] system 00:01: [mem 0xfc000000-0xfcffffff] has been reserved
[    0.106789] system 00:01: [mem 0xfd000000-0xfdffffff] has been reserved
[    0.106791] system 00:01: [mem 0xfe000000-0xfebfffff] has been reserved
[    0.106793] system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
[    0.106795] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.106821] pnp 00:02: [dma 4]
[    0.106822] pnp 00:02: [io  0x0000-0x000f]
[    0.106824] pnp 00:02: [io  0x0081-0x0083]
[    0.106825] pnp 00:02: [io  0x0087]
[    0.106826] pnp 00:02: [io  0x0089-0x008b]
[    0.106828] pnp 00:02: [io  0x008f]
[    0.106829] pnp 00:02: [io  0x00c0-0x00df]
[    0.106844] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.106851] pnp 00:03: [io  0x0070-0x0071]
[    0.106854] pnp 00:03: [irq 8]
[    0.106868] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.106874] pnp 00:04: [io  0x0061]
[    0.106891] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.106897] pnp 00:05: [io  0x00f0-0x00ff]
[    0.106898] pnp 00:05: [irq 13]
[    0.106913] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.106933] pnp 00:06: [io  0x0060]
[    0.106935] pnp 00:06: [io  0x0064]
[    0.106936] pnp 00:06: [irq 1]
[    0.106957] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.107065] pnp 00:07: [io  0x0000-0xffffffffffffffff disabled]
[    0.107067] pnp 00:07: [io  0x0a00-0x0a0f]
[    0.107068] pnp 00:07: [io  0x0a10-0x0a1f]
[    0.107069] pnp 00:07: [io  0x0a20-0x0a2f]
[    0.107070] pnp 00:07: [io  0x0a30-0x0a3f]
[    0.107103] system 00:07: [io  0x0a00-0x0a0f] has been reserved
[    0.107105] system 00:07: [io  0x0a10-0x0a1f] has been reserved
[    0.107107] system 00:07: [io  0x0a20-0x0a2f] has been reserved
[    0.107109] system 00:07: [io  0x0a30-0x0a3f] has been reserved
[    0.107111] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.107190] pnp 00:08: [io  0x0010-0x001f]
[    0.107191] pnp 00:08: [io  0x0022-0x003f]
[    0.107193] pnp 00:08: [io  0x0044-0x005f]
[    0.107194] pnp 00:08: [io  0x0062-0x0063]
[    0.107195] pnp 00:08: [io  0x0065-0x006f]
[    0.107196] pnp 00:08: [io  0x0072-0x007f]
[    0.107198] pnp 00:08: [io  0x0080]
[    0.107199] pnp 00:08: [io  0x0084-0x0086]
[    0.107200] pnp 00:08: [io  0x0088]
[    0.107201] pnp 00:08: [io  0x008c-0x008e]
[    0.107203] pnp 00:08: [io  0x0090-0x009f]
[    0.107204] pnp 00:08: [io  0x00a2-0x00bf]
[    0.107205] pnp 00:08: [io  0x00e0-0x00ef]
[    0.107206] pnp 00:08: [io  0x04d0-0x04d1]
[    0.107207] pnp 00:08: [io  0x0800-0x087f]
[    0.107209] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    0.107210] pnp 00:08: [io  0x0500-0x057f]
[    0.107212] pnp 00:08: [mem 0xfed1c000-0xfed1ffff]
[    0.107215] pnp 00:08: [mem 0xfed20000-0xfed3ffff]
[    0.107217] pnp 00:08: [mem 0xfed40000-0xfed8ffff]
[    0.107262] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.107264] system 00:08: [io  0x0800-0x087f] has been reserved
[    0.107266] system 00:08: [io  0x0500-0x057f] has been reserved
[    0.107268] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.107270] system 00:08: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.107272] system 00:08: [mem 0xfed40000-0xfed8ffff] has been reserved
[    0.107274] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.107315] pnp 00:09: [mem 0xfed00000-0xfed003ff]
[    0.107333] pnp 00:09: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.107385] pnp 00:0a: [mem 0xfec00000-0xfec00fff]
[    0.107387] pnp 00:0a: [mem 0xfee00000-0xfee00fff]
[    0.107419] system 00:0a: [mem 0xfec00000-0xfec00fff] has been reserved
[    0.107421] system 00:0a: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.107423] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.107785] pnp 00:0b: [io  0x03f8-0x03ff]
[    0.107788] pnp 00:0b: [irq 4]
[    0.107789] pnp 00:0b: [dma 0 disabled]
[    0.107849] pnp 00:0b: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.108215] pnp 00:0c: [io  0x02f8-0x02ff]
[    0.108217] pnp 00:0c: [irq 3]
[    0.108219] pnp 00:0c: [dma 0 disabled]
[    0.108278] pnp 00:0c: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.108484] pnp 00:0d: [mem 0xe0000000-0xefffffff]
[    0.108521] system 00:0d: [mem 0xe0000000-0xefffffff] has been reserved
[    0.108523] system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.108670] pnp 00:0e: [mem 0x00000000-0x0009ffff]
[    0.108672] pnp 00:0e: [mem 0x000c0000-0x000cffff]
[    0.108673] pnp 00:0e: [mem 0x000e0000-0x000fffff]
[    0.108674] pnp 00:0e: [mem 0x00100000-0xbfefffff]
[    0.108676] pnp 00:0e: [mem 0xfed90000-0xffffffff]
[    0.108722] system 00:0e: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.108724] system 00:0e: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.108726] system 00:0e: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.108728] system 00:0e: [mem 0x00100000-0xbfefffff] could not be reserved
[    0.108730] system 00:0e: [mem 0xfed90000-0xffffffff] could not be reserved
[    0.108732] system 00:0e: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.108821] pnp: PnP ACPI: found 15 devices
[    0.108823] ACPI: ACPI bus type pnp unregistered
[    0.114280] Switching to clocksource acpi_pm
[    0.114298] PCI: max bus depth: 1 pci_try_num: 2
[    0.114325] pci 0000:00:1c.4: BAR 15: assigned [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.114328] pci 0000:00:1c.0: BAR 14: assigned [mem 0xc0200000-0xc03fffff]
[    0.114330] pci 0000:00:1c.0: BAR 15: assigned [mem 0xc0400000-0xc05fffff 64bit pref]
[    0.114333] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.114335] pci 0000:00:03.0: PCI bridge to [bus 01-01]
[    0.114337] pci 0000:00:03.0:   bridge window [io  0xd000-0xdfff]
[    0.114340] pci 0000:00:03.0:   bridge window [mem 0xf8000000-0xfbefffff]
[    0.114343] pci 0000:00:03.0:   bridge window [mem 0xd4000000-0xdfffffff 64bit pref]
[    0.114347] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.114349] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    0.114353] pci 0000:00:1c.0:   bridge window [mem 0xc0200000-0xc03fffff]
[    0.114356] pci 0000:00:1c.0:   bridge window [mem 0xc0400000-0xc05fffff 64bit pref]
[    0.114361] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
[    0.114363] pci 0000:00:1c.4:   bridge window [io  0xe000-0xefff]
[    0.114367] pci 0000:00:1c.4:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.114370] pci 0000:00:1c.4:   bridge window [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.114375] pci 0000:00:1e.0: PCI bridge to [bus 04-04]
[    0.114376] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.114380] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.114383] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.114435] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[    0.114436] PCI: setting IRQ 10 as level-triggered
[    0.114441] pci 0000:00:03.0: PCI INT A -> Link[LNKA] -> GSI 10 (level, low) -> IRQ 10
[    0.114444] pci 0000:00:03.0: setting latency timer to 64
[    0.114448] pci 0000:00:1c.0: enabling device (0104 -> 0107)
[    0.114487] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[    0.114489] PCI: setting IRQ 5 as level-triggered
[    0.114493] pci 0000:00:1c.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[    0.114496] pci 0000:00:1c.0: setting latency timer to 64
[    0.114502] pci 0000:00:1c.4: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[    0.114505] pci 0000:00:1c.4: setting latency timer to 64
[    0.114510] pci 0000:00:1e.0: setting latency timer to 64
[    0.114513] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.114515] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.114516] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.114518] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.114520] pci_bus 0000:00: resource 8 [mem 0xbff00000-0xdfffffff]
[    0.114521] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.114523] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.114524] pci_bus 0000:01: resource 1 [mem 0xf8000000-0xfbefffff]
[    0.114526] pci_bus 0000:01: resource 2 [mem 0xd4000000-0xdfffffff 64bit pref]
[    0.114528] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    0.114530] pci_bus 0000:02: resource 1 [mem 0xc0200000-0xc03fffff]
[    0.114531] pci_bus 0000:02: resource 2 [mem 0xc0400000-0xc05fffff 64bit pref]
[    0.114533] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.114535] pci_bus 0000:03: resource 1 [mem 0xfbf00000-0xfbffffff]
[    0.114536] pci_bus 0000:03: resource 2 [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.114538] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.114540] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.114541] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.114543] pci_bus 0000:04: resource 7 [mem 0x000d0000-0x000dffff]
[    0.114545] pci_bus 0000:04: resource 8 [mem 0xbff00000-0xdfffffff]
[    0.114546] pci_bus 0000:04: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.114548] pci_bus 0000:ff: resource 0 [io  0x0000-0xffff]
[    0.114550] pci_bus 0000:ff: resource 1 [mem 0x00000000-0xfffffffff]
[    0.114574] NET: Registered protocol family 2
[    0.114676] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.115425] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.116363] Switched to NOHz mode on CPU #0
[    0.117977] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.118301] TCP: Hash tables configured (established 524288 bind 65536)
[    0.118303] TCP reno registered
[    0.118310] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.118341] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.118433] NET: Registered protocol family 1
[    0.118512] pci 0000:01:00.0: Boot video device
[    0.118542] PCI: CLS 32 bytes, default 64
[    0.118551] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.118553] Placing 64MB software IO TLB between ffff8800bb67a000 - ffff8800bf67a000
[    0.118554] software IO TLB at phys 0xbb67a000 - 0xbf67a000
[    0.118796] audit: initializing netlink socket (disabled)
[    0.118803] type=2000 audit(1324842719.096:1): initialized
[    0.135487] Trying to unpack rootfs image as initramfs...
[    0.174289] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.202284] VFS: Disk quotas dquot_6.5.2
[    0.202326] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.206240] fuse init (API version 7.16)
[    0.206306] msgmni has been set to 7877
[    0.218256] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.218276] io scheduler noop registered
[    0.218278] io scheduler deadline registered
[    0.218309] io scheduler cfq registered (default)
[    0.218504] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.218519] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.218550] intel_idle: MWAIT substates: 0x1120
[    0.218552] intel_idle: v0.4 model 0x1E
[    0.218553] intel_idle: lapic_timer_reliable_states 0x2
[    0.218623] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.218627] ACPI: Power Button [PWRB]
[    0.218654] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.218656] ACPI: Power Button [PWRF]
[    0.218676] ACPI: acpi_idle yielding to intel_idle
[    0.220446] ERST: Table is not found!
[    0.220483] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.240835] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.282473] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.323064] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.366323] 00:0c: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.385896] hpet_acpi_add: no address or irqs in _CRS
[    0.385914] Linux agpgart interface v0.103
[    0.386633] brd: module loaded
[    0.386952] loop: module loaded
[    0.387049] ata_piix 0000:00:1f.2: version 2.13
[    0.387108] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    0.387110] PCI: setting IRQ 11 as level-triggered
[    0.387114] ata_piix 0000:00:1f.2: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.387119] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.387149] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.393765] scsi0 : ata_piix
[    0.393823] scsi1 : ata_piix
[    0.394595] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xff90 irq 14
[    0.394599] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xff98 irq 15
[    0.394627] ata_piix 0000:00:1f.5: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.394630] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    0.394654] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.394780] scsi2 : ata_piix
[    0.394854] scsi3 : ata_piix
[    0.395430] ata3: SATA max UDMA/133 cmd 0xc800 ctl 0xc480 bmdma 0xc000 irq 11
[    0.395433] ata4: SATA max UDMA/133 cmd 0xc400 ctl 0xc080 bmdma 0xc008 irq 11
[    0.395466] pata_acpi 0000:03:00.1: enabling device (0000 -> 0001)
[    0.395471] pata_acpi 0000:03:00.1: PCI INT B -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[    0.395491] pata_acpi 0000:03:00.1: setting latency timer to 64
[    0.395502] pata_acpi 0000:03:00.1: PCI INT B disabled
[    0.395690] Fixed MDIO Bus: probed
[    0.395706] PPP generic driver version 2.4.2
[    0.395732] tun: Universal TUN/TAP device driver, 1.6
[    0.395733] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.395781] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.395792] ehci_hcd 0000:00:1a.0: PCI INT A -> Link[LNKA] -> GSI 10 (level, low) -> IRQ 10
[    0.395803] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.395806] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    0.395828] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.395851] ehci_hcd 0000:00:1a.0: debug port 2
[    0.399815] ehci_hcd 0000:00:1a.0: cache line size of 32 is not supported
[    0.399872] ehci_hcd 0000:00:1a.0: irq 10, io mem 0xf7ffa000
[    0.421633] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.421734] hub 1-0:1.0: USB hub found
[    0.421737] hub 1-0:1.0: 2 ports detected
[    0.421842] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 6
[    0.421844] PCI: setting IRQ 6 as level-triggered
[    0.421849] ehci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKH] -> GSI 6 (level, low) -> IRQ 6
[    0.421861] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.421863] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    0.421889] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.421911] ehci_hcd 0000:00:1d.0: debug port 2
[    0.425821] ehci_hcd 0000:00:1d.0: cache line size of 32 is not supported
[    0.429614] ehci_hcd 0000:00:1d.0: irq 6, io mem 0xf7ff8000
[    0.441703] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.441787] hub 2-0:1.0: USB hub found
[    0.441791] hub 2-0:1.0: 2 ports detected
[    0.441839] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.441850] uhci_hcd: USB Universal Host Controller Interface driver
[    0.441901] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.441902] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.442007] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.442055] mousedev: PS/2 mouse device common for all mice
[    0.442117] rtc_cmos 00:03: RTC can wake from S4
[    0.442201] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.442219] rtc0: alarms up to one month, y3k, 114 bytes nvram
[    0.442291] device-mapper: uevent: version 1.0.3
[    0.442342] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    0.442367] cpuidle: using governor ladder
[    0.442394] cpuidle: using governor menu
[    0.442395] EFI Variables Facility v0.08 2004-May-17
[    0.442563] TCP cubic registered
[    0.442647] NET: Registered protocol family 10
[    0.442984] NET: Registered protocol family 17
[    0.442994] Registering the dns_resolver key type
[    0.443053] PM: Hibernation image not present or could not be loaded.
[    0.443061] registered taskstats version 1
[    0.469188] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.481697] Freeing initrd memory: 13436k freed
[    0.487981]   Magic number: 7:272:901
[    0.488040] acpi PNP0501:01: hash matches
[    0.488077] rtc_cmos 00:03: setting system clock to 2011-12-25 19:51:59 UTC (1324842719)
[    0.488360] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.488361] EDD information not available.
[    0.727709] ata3: SATA link down (SStatus 0 SControl 300)
[    0.738426] ata4: SATA link down (SStatus 0 SControl 300)
[    0.738450] usb 1-1: new high speed USB device number 2 using ehci_hcd
[    0.869367] hub 1-1:1.0: USB hub found
[    0.869455] hub 1-1:1.0: 6 ports detected
[    0.980443] usb 2-1: new high speed USB device number 2 using ehci_hcd
[    1.112833] hub 2-1:1.0: USB hub found
[    1.112922] hub 2-1:1.0: 8 ports detected
[    1.132101] Refined TSC clocksource calibration: 2806.964 MHz.
[    1.132105] Switching to clocksource tsc
[    1.184156] usb 1-1.1: new full speed USB device number 3 using ehci_hcd
[    1.203988] ata2.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.204001] ata2.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.204174] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.204184] ata1.01: SATA link down (SStatus 0 SControl 300)
[    1.212373] ata1.00: ATA-8: SAMSUNG HD502HJ, 1AJ10001, max UDMA/133
[    1.212376] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.220213] ata2.00: ATA-8: SAMSUNG HD502HJ, 1AJ10001, max UDMA/133
[    1.220216] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.220220] ata2.01: ATAPI: TSSTcorp CDDVDW SH-S223C, SB04, max UDMA/100
[    1.220424] ata1.00: configured for UDMA/133
[    1.220495] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD502HJ  1AJ1 PQ: 0 ANSI: 5
[    1.220580] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.220627] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.220657] sd 0:0:0:0: [sda] Write Protect is off
[    1.220659] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.220672] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.226491]  sda: sda1 sda2 sda3
[    1.226655] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.228116] ata2.00: configured for UDMA/133
[    1.243975] ata2.01: configured for UDMA/100
[    1.245427] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HD502HJ  1AJ1 PQ: 0 ANSI: 5
[    1.245506] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.246801] scsi 1:0:1:0: CD-ROM            TSSTcorp CDDVDW SH-S223C  SB04 PQ: 0 ANSI: 5
[    1.246895] sd 1:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.250866] sr0: scsi3-mmc drive: 52x/52x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.250869] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.250935] sr 1:0:1:0: Attached scsi CD-ROM sr0
[    1.250966] sr 1:0:1:0: Attached scsi generic sg2 type 5
[    1.251013] sd 1:0:0:0: [sdb] Write Protect is off
[    1.251015] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.251028] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.311251]  sdb: sdb1 sdb2 sdb3 < sdb5 sdb6 >
[    1.311464] sd 1:0:0:0: [sdb] Attached SCSI disk
[    1.312776] Freeing unused kernel memory: 984k freed
[    1.312969] Write protecting the kernel read-only data: 10240k
[    1.313087] Freeing unused kernel memory: 16k freed
[    1.316363] Freeing unused kernel memory: 1396k freed
[    1.327877] udevd[86]: starting version 173
[    1.347756] usb 1-1.5: new high speed USB device number 4 using ehci_hcd
[    1.418648] pata_jmicron 0000:03:00.1: PCI INT B -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[    1.418673] pata_jmicron 0000:03:00.1: setting latency timer to 64
[    1.424262] scsi4 : pata_jmicron
[    1.428321] scsi5 : pata_jmicron
[    1.428601] ata5: PATA max UDMA/100 cmd 0xec00 ctl 0xe880 bmdma 0xe400 irq 5
[    1.428603] ata6: PATA max UDMA/100 cmd 0xe800 ctl 0xe480 bmdma 0xe408 irq 5
[    1.429597] ahci 0000:03:00.0: version 3.0
[    1.429609] ahci 0000:03:00.0: PCI INT A -> Link[LNKA] -> GSI 10 (level, low) -> IRQ 10
[    1.443446] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    1.443449] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    1.443454] ahci 0000:03:00.0: setting latency timer to 64
[    1.445735] scsi6 : ahci
[    1.447356] scsi7 : ahci
[    1.447416] ata7: SATA max UDMA/133 abar m8192@0xfbffe000 port 0xfbffe100 irq 10
[    1.447419] ata8: SATA max UDMA/133 abar m8192@0xfbffe000 port 0xfbffe180 irq 10
[    1.762896] usb 1-1.6: new high speed USB device number 5 using ehci_hcd
[    1.770698] ata7: SATA link down (SStatus 0 SControl 300)
[    1.770737] ata8: SATA link down (SStatus 0 SControl 300)
[    1.774599] input: A4Tech USB Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input3
[    1.774676] generic-usb 0003:09DA:0080.0001: input,hidraw0: USB HID v1.11 Mouse [A4Tech USB Mouse] on usb-0000:00:1a.0-1.1/input0
[    1.774685] usbcore: registered new interface driver usbhid
[    1.774687] usbhid: USB HID core driver
[    2.475924] EXT4-fs (sdb5): mounted filesystem with ordered data mode. Opts: (null)
[   14.256198] udevd[342]: starting version 173
[   14.288943] lp: driver loaded but no devices found
[   14.291112] e1000e: Intel(R) PRO/1000 Network Driver - 1.3.10-k2
[   14.291114] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[   14.291198] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[   14.291202] e1000e 0000:00:19.0: PCI INT A -> Link[LNKE] -> GSI 11 (level, low) -> IRQ 11
[   14.291209] e1000e 0000:00:19.0: setting latency timer to 64
[   14.291285] e1000e 0000:00:19.0: (unregistered net_device): Failed to initialize MSI interrupts.  Falling back to legacy interrupts.
[   14.300254] Adding 5054460k swap on /dev/sdb6.  Priority:-1 extents:1 across:5054460k 
[   15.369936] e1000e 0000:00:19.0: PCI INT A disabled
[   15.369943] e1000e: probe of 0000:00:19.0 failed with error -3
[   15.382889] EXT4-fs (sdb5): re-mounted. Opts: errors=remount-ro
[   15.445440] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 7
[   15.445443] PCI: setting IRQ 7 as level-triggered
[   15.445448] HDA Intel 0000:00:1b.0: PCI INT A -> Link[LNKG] -> GSI 7 (level, low) -> IRQ 7
[   15.445493] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.462553] wmi: Mapper loaded
[   15.487206] hda_codec: ALC889A: BIOS auto-probing.
[   15.506283] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
[   15.506536] HDA Intel 0000:01:00.1: PCI INT B -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   15.506538] hda_intel: Disabling MSI
[   15.506566] HDA Intel 0000:01:00.1: setting latency timer to 64
[   15.573979] type=1400 audit(1324839134.617:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=596 comm="apparmor_parser"
[   15.574252] type=1400 audit(1324839134.617:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=596 comm="apparmor_parser"
[   15.574426] type=1400 audit(1324839134.617:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=596 comm="apparmor_parser"
[   15.730292] nvidia: module license 'NVIDIA' taints kernel.
[   15.730296] Disabling lock debugging due to kernel taint
[   15.791211] EDAC MC: Ver: 2.1.0
[   15.798345] EDAC MC0: Giving out device to 'i7core_edac.c' 'i7 core #0': DEV 0000:ff:03.0
[   15.798378] EDAC PCI0: Giving out device to module 'i7core_edac' controller 'EDAC PCI controller': DEV '0000:ff:03.0' (POLLED)
[   15.798381] EDAC i7core: Driver loaded.
[   16.311869] init: failsafe main process (766) killed by TERM signal
[   16.366859] type=1400 audit(1324839135.413:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=830 comm="apparmor_parser"
[   16.370991] type=1400 audit(1324839135.417:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=834 comm="apparmor_parser"
[   16.371276] type=1400 audit(1324839135.417:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=834 comm="apparmor_parser"
[   16.371459] type=1400 audit(1324839135.417:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=834 comm="apparmor_parser"
[   16.377387] type=1400 audit(1324839135.421:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=836 comm="apparmor_parser"
[   16.386352] type=1400 audit(1324839135.433:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=836 comm="apparmor_parser"
[   16.394948] type=1400 audit(1324839135.441:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=836 comm="apparmor_parser"
[   16.411226] Linux video capture interface: v2.00
[   16.441441] uvcvideo: Found UVC 1.00 device <unnamed> (046d:081d)
[   16.441473] usbcore: registered new interface driver snd-usb-audio
[   16.454736] input: UVC Camera (046d:081d) as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.2/input/input5
[   16.454898] usbcore: registered new interface driver uvcvideo
[   16.454900] USB Video Class driver (v1.1.0)
[   16.566219] init: apport pre-start process (930) terminated with status 1
[   16.575535] init: apport post-stop process (958) terminated with status 1
[   16.750314] Bluetooth: Core ver 2.16
[   16.750349] NET: Registered protocol family 31
[   16.750350] Bluetooth: HCI device and connection manager initialized
[   16.750352] Bluetooth: HCI socket layer initialized
[   16.750353] Bluetooth: L2CAP socket layer initialized
[   16.750721] Bluetooth: SCO socket layer initialized
[   16.752068] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.752070] Bluetooth: BNEP filters: protocol multicast
[   16.851138] Bluetooth: RFCOMM TTY layer initialized
[   16.851141] Bluetooth: RFCOMM socket layer initialized
[   16.851142] Bluetooth: RFCOMM ver 1.11
[   17.012873] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[   17.044804] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[   17.076733] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[   17.108660] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[   17.127794] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card1/input6
[   17.127899] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card1/input7
[   17.127975] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card1/input8
[   17.128054] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card1/input9
[   17.130744] nvidia 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 10 (level, low) -> IRQ 10
[   17.130751] nvidia 0000:01:00.0: setting latency timer to 64
[   17.130755] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   17.133994] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  280.13  Wed Jul 27 16:53:56 PDT 2011
[   17.167271] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[   17.167273] vesafb: scrolling: redraw
[   17.167274] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   17.176581] vesafb: framebuffer at 0xd5000000, mapped to 0xffffc90013d80000, using 5120k, total 5120k
[   17.176713] Console: switching to colour frame buffer device 160x64
[   17.176734] fb0: VESA VGA frame buffer device
[   17.269783] ppdev: user-space parallel port driver
[   18.654058] EXT4-fs (sdb5): re-mounted. Opts: errors=remount-ro,commit=0
[   19.100648] init: plymouth-stop pre-start process (1218) terminated with status 1
[   19.907731] EXT4-fs (sdb5): re-mounted. Opts: errors=remount-ro,commit=0


```

---

### Post by matt_symes on 2011-12-25
Hi

Can you move the board into a different port ?

Kind regards

---

### Post by areq on 2011-12-25
I'm afraid I don't understand what You mean by moving the board into a different port - if You mean sound card or network card, it is impossible, both are onboard solutions. In the meantime I've enabled HPET in bios and added hpet=enable to the boot options. Here is the log output:

no lan:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-14-generic (buildd@allspice) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 (Ubuntu 3.0.0-14.23-generic 3.0.9)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic root=UUID=a303a224-b575-4c3b-970c-c5bce24b9485 ro hpet=enable quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf680000 (usable)
[    0.000000]  BIOS-e820: 00000000bf680000 - 00000000bf68e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf68e000 - 00000000bf6d0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf6d0000 - 00000000bf6e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf6ed000 - 00000000bf700000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf800000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffa00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI:    /LP DK P55-T3eH9, BIOS 080015  08/27/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-E3FFF write-protect
[    0.000000]   E4000-E7FFF write-through
[    0.000000]   E8000-EBFFF write-protect
[    0.000000]   EC000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 100000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 base 0BFF00000 mask FFFF00000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 4GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 1GB, type UC
[    0.000000] reg 3, base: 3071MB, range: 1MB, type UC
[    0.000000] total RAM covered: 4095M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 2M     num_reg: 4      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3071MB, range: 1MB, type UC
[    0.000000] reg 3, base: 4GB, range: 1GB, type WB
[    0.000000] e820 update range: 00000000bff00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbf680 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff88000009a000] 9a000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000bf680000
[    0.000000]  0000000000 - 00bf600000 page 2M
[    0.000000]  00bf600000 - 00bf680000 page 4k
[    0.000000] kernel direct mapping tables up to bf680000 @ 1fffb000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000140000000
[    0.000000]  0100000000 - 0140000000 page 2M
[    0.000000] kernel direct mapping tables up to 140000000 @ bf67a000-bf680000
[    0.000000] RAMDISK: 365b2000 - 372d1000
[    0.000000] ACPI: RSDP 00000000000f9a30 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 00000000bf680100 0005C (v01 082710 XSDT1410 20100827 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000bf680290 000F4 (v03 082710 FACP1410 20100827 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000bf680460 070D5 (v01  P55DK P55DK000 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 00000000bf68e000 00040
[    0.000000] ACPI: APIC 00000000bf680390 0008C (v01 082710 APIC1410 20100827 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000bf680420 0003C (v01 082710 OEMMCFG  20100827 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000bf68e040 00072 (v01 082710 OEMB1410 20100827 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000bf68a460 00038 (v01 082710 OEMHPET  20100827 MSFT 00000097)
[    0.000000] ACPI: GSCI 00000000bf68e0c0 02024 (v01 082710 GMCHSCI  20100827 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000bf691330 00363 (v01 DpgPmm    CpuPm 00000012 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000140000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000140000000
[    0.000000]   NODE_DATA [000000013fffb000 - 000000013fffffff]
[    0.000000]  [ffffea0000000000-ffffea00045fffff] PMD -> [ffff88013b600000-ffff88013edfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bf680
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 1046031
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3922 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 765624 pages, LIFO batch:31
[    0.000000]   Normal zone: 3584 pages used for memmap
[    0.000000]   Normal zone: 258560 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x86] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x87] disabled)
[    0.000000] ACPI: IOAPIC (id[0x07] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 7, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bf680000 - 00000000bf68e000
[    0.000000] PM: Registered nosave memory: 00000000bf68e000 - 00000000bf6d0000
[    0.000000] PM: Registered nosave memory: 00000000bf6d0000 - 00000000bf6e0000
[    0.000000] PM: Registered nosave memory: 00000000bf6e0000 - 00000000bf6ed000
[    0.000000] PM: Registered nosave memory: 00000000bf6ed000 - 00000000bf700000
[    0.000000] PM: Registered nosave memory: 00000000bf700000 - 00000000bf800000
[    0.000000] PM: Registered nosave memory: 00000000bf800000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffa00000
[    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88013fc00000 s79616 r8192 d22784 u262144
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1028106
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic root=UUID=a303a224-b575-4c3b-970c-c5bce24b9485 ro hpet=enable quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 4032928k/5242880k available (6109k kernel code, 1058756k absent, 151196k reserved, 4876k data, 984k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2806.846 MHz processor.
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 5613.69 BogoMIPS (lpj=11227384)
[    0.000005] pid_max: default: 32768 minimum: 301
[    0.000026] Security Framework initialized
[    0.000040] AppArmor: AppArmor initialized
[    0.000041] Yama: becoming mindful.
[    0.000375] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001685] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.002260] Mount-cache hash table entries: 256
[    0.002367] Initializing cgroup subsys cpuacct
[    0.002372] Initializing cgroup subsys memory
[    0.002378] Initializing cgroup subsys devices
[    0.002379] Initializing cgroup subsys freezer
[    0.002381] Initializing cgroup subsys net_cls
[    0.002382] Initializing cgroup subsys blkio
[    0.002388] Initializing cgroup subsys perf_event
[    0.002409] CPU: Physical Processor ID: 0
[    0.002410] CPU: Processor Core ID: 0
[    0.002414] mce: CPU supports 9 MCE banks
[    0.002424] CPU0: Thermal monitoring enabled (TM1)
[    0.002431] using mwait in idle threads.
[    0.004063] ACPI: Core revision 20110413
[    0.032095] ftrace: allocating 25647 entries in 101 pages
[    0.038703] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.078298] CPU0: Intel(R) Core(TM) i5 CPU         760  @ 2.80GHz stepping 05
[    0.184401] Performance Events: PEBS fmt1+, erratum AAJ80 worked around, Nehalem events, Intel PMU driver.
[    0.184407] ... version:                3
[    0.184408] ... bit width:              48
[    0.184409] ... generic registers:      4
[    0.184410] ... value mask:             0000ffffffffffff
[    0.184411] ... max period:             000000007fffffff
[    0.184413] ... fixed-purpose events:   3
[    0.184414] ... event mask:             000000070000000f
[    0.184739] Booting Node   0, Processors  #1
[    0.184741] smpboot cpu 1: start_ip = 9a000
[    0.296340]  #2
[    0.296342] smpboot cpu 2: start_ip = 9a000
[    0.408010]  #3
[    0.408012] smpboot cpu 3: start_ip = 9a000
[    0.519700] Brought up 4 CPUs
[    0.519703] Total of 4 processors activated (22454.52 BogoMIPS).
[    0.521626] devtmpfs: initialized
[    0.521725] PM: Registering ACPI NVS region at bf68e000 (270336 bytes)
[    0.522919] print_constraints: dummy: 
[    0.522943] Time: 21:07:05  Date: 12/25/11
[    0.522968] NET: Registered protocol family 16
[    0.523046] ACPI: bus type pci registered
[    0.523047] Trying to unpack rootfs image as initramfs...
[    0.523092] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.523094] PCI: not using MMCONFIG
[    0.523096] PCI: Using configuration type 1 for base access
[    0.523662] bio: create slab <bio-0> at 0
[    0.524657] ACPI: EC: Look up EC in DSDT
[    0.525973] ACPI: Executed 1 blocks of module-level executable AML code
[    0.527993] ACPI: SSDT 00000000bf6900f0 01238 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    0.528253] ACPI: Dynamic OEM Table Load:
[    0.528255] ACPI: SSDT           (null) 01238 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    0.528725] ACPI: Interpreter enabled
[    0.528727] ACPI: (supports S0 S1 S3 S4 S5)
[    0.528741] ACPI: Using IOAPIC for interrupt routing
[    0.528757] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.529835] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.562391] ACPI: No dock devices found.
[    0.562394] HEST: Table not found.
[    0.562397] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.562533] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.562658] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.562660] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.562662] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.562664] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.562666] pci_root PNP0A08:00: host bridge window [mem 0xbff00000-0xdfffffff]
[    0.562667] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfed8ffff]
[    0.562678] pci 0000:00:00.0: [8086:d131] type 0 class 0x000600
[    0.562719] pci 0000:00:03.0: [8086:d138] type 1 class 0x000604
[    0.562816] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.562819] pci 0000:00:03.0: PME# disabled
[    0.562836] pci 0000:00:08.0: [8086:d155] type 0 class 0x000880
[    0.562881] pci 0000:00:08.1: [8086:d156] type 0 class 0x000880
[    0.562925] pci 0000:00:08.2: [8086:d157] type 0 class 0x000880
[    0.562968] pci 0000:00:08.3: [8086:d158] type 0 class 0x000880
[    0.563013] pci 0000:00:10.0: [8086:d150] type 0 class 0x000880
[    0.563050] pci 0000:00:10.1: [8086:d151] type 0 class 0x000880
[    0.563104] pci 0000:00:19.0: [8086:10f0] type 0 class 0x000200
[    0.563120] pci 0000:00:19.0: reg 10: [mem 0xf7fc0000-0xf7fdffff]
[    0.563127] pci 0000:00:19.0: reg 14: [mem 0xf7ffc000-0xf7ffcfff]
[    0.563134] pci 0000:00:19.0: reg 18: [io  0xcc00-0xcc1f]
[    0.563177] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.563180] pci 0000:00:19.0: PME# disabled
[    0.563201] pci 0000:00:1a.0: [8086:3b3c] type 0 class 0x000c03
[    0.563219] pci 0000:00:1a.0: reg 10: [mem 0xf7ffa000-0xf7ffa3ff]
[    0.563284] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.563288] pci 0000:00:1a.0: PME# disabled
[    0.563307] pci 0000:00:1b.0: [8086:3b56] type 0 class 0x000403
[    0.563320] pci 0000:00:1b.0: reg 10: [mem 0xf7ff4000-0xf7ff7fff 64bit]
[    0.563368] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.563371] pci 0000:00:1b.0: PME# disabled
[    0.563387] pci 0000:00:1c.0: [8086:3b42] type 1 class 0x000604
[    0.563434] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.563437] pci 0000:00:1c.0: PME# disabled
[    0.563456] pci 0000:00:1c.4: [8086:3b4a] type 1 class 0x000604
[    0.563504] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.563507] pci 0000:00:1c.4: PME# disabled
[    0.563533] pci 0000:00:1d.0: [8086:3b34] type 0 class 0x000c03
[    0.563556] pci 0000:00:1d.0: reg 10: [mem 0xf7ff8000-0xf7ff83ff]
[    0.563622] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.563625] pci 0000:00:1d.0: PME# disabled
[    0.563643] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    0.563692] pci 0000:00:1f.0: [8086:3b02] type 0 class 0x000601
[    0.563792] pci 0000:00:1f.2: [8086:3b20] type 0 class 0x000101
[    0.563805] pci 0000:00:1f.2: reg 10: [io  0x0000-0x0007]
[    0.563812] pci 0000:00:1f.2: reg 14: [io  0x0000-0x0003]
[    0.563819] pci 0000:00:1f.2: reg 18: [io  0x0000-0x0007]
[    0.563826] pci 0000:00:1f.2: reg 1c: [io  0x0000-0x0003]
[    0.563832] pci 0000:00:1f.2: reg 20: [io  0xff90-0xff9f]
[    0.563839] pci 0000:00:1f.2: reg 24: [io  0xffa0-0xffaf]
[    0.563870] pci 0000:00:1f.3: [8086:3b30] type 0 class 0x000c05
[    0.563883] pci 0000:00:1f.3: reg 10: [mem 0xf7ff2000-0xf7ff20ff 64bit]
[    0.563901] pci 0000:00:1f.3: reg 20: [io  0x0400-0x041f]
[    0.563929] pci 0000:00:1f.5: [8086:3b26] type 0 class 0x000101
[    0.563942] pci 0000:00:1f.5: reg 10: [io  0xc800-0xc807]
[    0.563949] pci 0000:00:1f.5: reg 14: [io  0xc480-0xc483]
[    0.563955] pci 0000:00:1f.5: reg 18: [io  0xc400-0xc407]
[    0.563962] pci 0000:00:1f.5: reg 1c: [io  0xc080-0xc083]
[    0.563969] pci 0000:00:1f.5: reg 20: [io  0xc000-0xc00f]
[    0.563976] pci 0000:00:1f.5: reg 24: [io  0xbc00-0xbc0f]
[    0.564037] pci 0000:01:00.0: [10de:0e22] type 0 class 0x000300
[    0.564046] pci 0000:01:00.0: reg 10: [mem 0xf8000000-0xf9ffffff]
[    0.564055] pci 0000:01:00.0: reg 14: [mem 0xd8000000-0xdfffffff 64bit pref]
[    0.564065] pci 0000:01:00.0: reg 1c: [mem 0xd4000000-0xd7ffffff 64bit pref]
[    0.564071] pci 0000:01:00.0: reg 24: [io  0xdc00-0xdc7f]
[    0.564078] pci 0000:01:00.0: reg 30: [mem 0xfbe80000-0xfbefffff pref]
[    0.564115] pci 0000:01:00.1: [10de:0beb] type 0 class 0x000403
[    0.564124] pci 0000:01:00.1: reg 10: [mem 0xfbe7c000-0xfbe7ffff]
[    0.571530] pci 0000:00:03.0: PCI bridge to [bus 01-01]
[    0.571533] pci 0000:00:03.0:   bridge window [io  0xd000-0xdfff]
[    0.571536] pci 0000:00:03.0:   bridge window [mem 0xf8000000-0xfbefffff]
[    0.571540] pci 0000:00:03.0:   bridge window [mem 0xd4000000-0xdfffffff 64bit pref]
[    0.571574] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.571577] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.571581] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.571586] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.571635] pci 0000:03:00.0: [197b:2363] type 0 class 0x000101
[    0.571718] pci 0000:03:00.0: reg 24: [mem 0xfbffe000-0xfbffffff]
[    0.571758] pci 0000:03:00.0: PME# supported from D3hot
[    0.571762] pci 0000:03:00.0: PME# disabled
[    0.571790] pci 0000:03:00.1: [197b:2363] type 0 class 0x000101
[    0.571813] pci 0000:03:00.1: reg 10: [io  0xec00-0xec07]
[    0.571825] pci 0000:03:00.1: reg 14: [io  0xe880-0xe883]
[    0.571838] pci 0000:03:00.1: reg 18: [io  0xe800-0xe807]
[    0.571851] pci 0000:03:00.1: reg 1c: [io  0xe480-0xe483]
[    0.571863] pci 0000:03:00.1: reg 20: [io  0xe400-0xe40f]
[    0.571929] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.571941] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
[    0.571944] pci 0000:00:1c.4:   bridge window [io  0xe000-0xefff]
[    0.571947] pci 0000:00:1c.4:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.571952] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.572005] pci 0000:00:1e.0: PCI bridge to [bus 04-04] (subtractive decode)
[    0.572008] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.572011] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.572016] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.572018] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.572020] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.572022] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.572023] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.572025] pci 0000:00:1e.0:   bridge window [mem 0xbff00000-0xdfffffff] (subtractive decode)
[    0.572027] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfed8ffff] (subtractive decode)
[    0.572043] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.572153] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR1E._PRT]
[    0.572205] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR20._PRT]
[    0.572229] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR24._PRT]
[    0.572333]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.572464]  pci0000:00: ACPI _OSC request failed (AE_SUPPORT), returned control mask: 0x0d
[    0.572465] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.578659] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
[    0.578691] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[    0.578721] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 *10 11 12 14 15)
[    0.578815] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 *11 12 14 15)
[    0.578847] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 *11 12 14 15)
[    0.578878] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
[    0.578910] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 6 *7 10 11 12 14 15)
[    0.578941] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *6 7 10 11 12 14 15)
[    0.579013] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.579016] vgaarb: loaded
[    0.579017] vgaarb: bridge control possible 0000:01:00.0
[    0.579143] SCSI subsystem initialized
[    0.579187] libata version 3.00 loaded.
[    0.579215] usbcore: registered new interface driver usbfs
[    0.579221] usbcore: registered new interface driver hub
[    0.579238] usbcore: registered new device driver usb
[    0.579294] PCI: Using ACPI for IRQ routing
[    0.584885] PCI: Discovered peer bus ff
[    0.584909] pci 0000:ff:00.0: [8086:2c51] type 0 class 0x000600
[    0.584925] pci 0000:ff:00.1: [8086:2c81] type 0 class 0x000600
[    0.584941] pci 0000:ff:02.0: [8086:2c90] type 0 class 0x000600
[    0.584955] pci 0000:ff:02.1: [8086:2c91] type 0 class 0x000600
[    0.584970] pci 0000:ff:03.0: [8086:2c98] type 0 class 0x000600
[    0.584986] pci 0000:ff:03.1: [8086:2c99] type 0 class 0x000600
[    0.585000] pci 0000:ff:03.4: [8086:2c9c] type 0 class 0x000600
[    0.585015] pci 0000:ff:04.0: [8086:2ca0] type 0 class 0x000600
[    0.585028] pci 0000:ff:04.1: [8086:2ca1] type 0 class 0x000600
[    0.585042] pci 0000:ff:04.2: [8086:2ca2] type 0 class 0x000600
[    0.585055] pci 0000:ff:04.3: [8086:2ca3] type 0 class 0x000600
[    0.585070] pci 0000:ff:05.0: [8086:2ca8] type 0 class 0x000600
[    0.585084] pci 0000:ff:05.1: [8086:2ca9] type 0 class 0x000600
[    0.585098] pci 0000:ff:05.2: [8086:2caa] type 0 class 0x000600
[    0.585112] pci 0000:ff:05.3: [8086:2cab] type 0 class 0x000600
[    0.585360] PCI: pci_cache_line_size set to 64 bytes
[    0.585434] Expanded resource reserved due to conflict with PCI Bus 0000:00
[    0.585436] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.585438] reserve RAM buffer: 00000000bf680000 - 00000000bfffffff 
[    0.585507] NetLabel: Initializing
[    0.585508] NetLabel:  domain hash size = 128
[    0.585509] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.585518] NetLabel:  unlabeled traffic allowed by default
[    0.585568] HPET: 8 timers in total, 5 timers will be used for per-cpu timer
[    0.585575] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 40, 41, 42, 43, 44, 0
[    0.585579] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.591489] hpet: hpet2 irq 40 for MSI
[    0.591636] hpet: hpet3 irq 41 for MSI
[    0.595543] hpet: hpet4 irq 42 for MSI
[    0.599550] hpet: hpet5 irq 43 for MSI
[    0.599571] Switching to clocksource hpet
[    0.603411] Switched to NOHz mode on CPU #0
[    0.603490] Switched to NOHz mode on CPU #2
[    0.603528] Switched to NOHz mode on CPU #3
[    0.603554] Switched to NOHz mode on CPU #1
[    0.603946] AppArmor: AppArmor Filesystem Enabled
[    0.603967] pnp: PnP ACPI init
[    0.603976] ACPI: bus type pnp registered
[    0.604065] pnp 00:00: [bus 00-ff]
[    0.604067] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.604069] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.604071] pnp 00:00: [io  0x0d00-0xffff window]
[    0.604072] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.604074] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.604075] pnp 00:00: [mem 0xbff00000-0xdfffffff window]
[    0.604077] pnp 00:00: [mem 0xf0000000-0xfed8ffff window]
[    0.604134] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.604141] pnp 00:01: [mem 0xfc000000-0xfcffffff]
[    0.604143] pnp 00:01: [mem 0xfd000000-0xfdffffff]
[    0.604144] pnp 00:01: [mem 0xfe000000-0xfebfffff]
[    0.604146] pnp 00:01: [mem 0xfed14000-0xfed19fff]
[    0.604186] system 00:01: [mem 0xfc000000-0xfcffffff] has been reserved
[    0.604188] system 00:01: [mem 0xfd000000-0xfdffffff] has been reserved
[    0.604190] system 00:01: [mem 0xfe000000-0xfebfffff] has been reserved
[    0.604192] system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
[    0.604194] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.604222] pnp 00:02: [dma 4]
[    0.604223] pnp 00:02: [io  0x0000-0x000f]
[    0.604225] pnp 00:02: [io  0x0081-0x0083]
[    0.604226] pnp 00:02: [io  0x0087]
[    0.604227] pnp 00:02: [io  0x0089-0x008b]
[    0.604228] pnp 00:02: [io  0x008f]
[    0.604230] pnp 00:02: [io  0x00c0-0x00df]
[    0.604246] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.604253] pnp 00:03: [io  0x0070-0x0071]
[    0.604260] pnp 00:03: [irq 8]
[    0.604278] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.604284] pnp 00:04: [io  0x0061]
[    0.604299] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.604305] pnp 00:05: [io  0x00f0-0x00ff]
[    0.604310] pnp 00:05: [irq 13]
[    0.604325] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.604346] pnp 00:06: [io  0x0060]
[    0.604347] pnp 00:06: [io  0x0064]
[    0.604351] pnp 00:06: [irq 1]
[    0.604374] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.604484] pnp 00:07: [io  0x0000-0xffffffffffffffff disabled]
[    0.604486] pnp 00:07: [io  0x0a00-0x0a0f]
[    0.604487] pnp 00:07: [io  0x0a10-0x0a1f]
[    0.604488] pnp 00:07: [io  0x0a20-0x0a2f]
[    0.604490] pnp 00:07: [io  0x0a30-0x0a3f]
[    0.604524] system 00:07: [io  0x0a00-0x0a0f] has been reserved
[    0.604526] system 00:07: [io  0x0a10-0x0a1f] has been reserved
[    0.604527] system 00:07: [io  0x0a20-0x0a2f] has been reserved
[    0.604529] system 00:07: [io  0x0a30-0x0a3f] has been reserved
[    0.604531] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.604610] pnp 00:08: [io  0x0010-0x001f]
[    0.604612] pnp 00:08: [io  0x0022-0x003f]
[    0.604613] pnp 00:08: [io  0x0044-0x005f]
[    0.604614] pnp 00:08: [io  0x0062-0x0063]
[    0.604618] pnp 00:08: [io  0x0065-0x006f]
[    0.604619] pnp 00:08: [io  0x0072-0x007f]
[    0.604620] pnp 00:08: [io  0x0080]
[    0.604621] pnp 00:08: [io  0x0084-0x0086]
[    0.604623] pnp 00:08: [io  0x0088]
[    0.604624] pnp 00:08: [io  0x008c-0x008e]
[    0.604625] pnp 00:08: [io  0x0090-0x009f]
[    0.604626] pnp 00:08: [io  0x00a2-0x00bf]
[    0.604628] pnp 00:08: [io  0x00e0-0x00ef]
[    0.604629] pnp 00:08: [io  0x04d0-0x04d1]
[    0.604630] pnp 00:08: [io  0x0800-0x087f]
[    0.604632] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    0.604633] pnp 00:08: [io  0x0500-0x057f]
[    0.604634] pnp 00:08: [mem 0xfed1c000-0xfed1ffff]
[    0.604636] pnp 00:08: [mem 0xfed20000-0xfed3ffff]
[    0.604637] pnp 00:08: [mem 0xfed40000-0xfed8ffff]
[    0.604684] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.604686] system 00:08: [io  0x0800-0x087f] has been reserved
[    0.604688] system 00:08: [io  0x0500-0x057f] has been reserved
[    0.604690] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.604692] system 00:08: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.604694] system 00:08: [mem 0xfed40000-0xfed8ffff] has been reserved
[    0.604696] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.604736] pnp 00:09: [mem 0xfed00000-0xfed003ff]
[    0.604754] pnp 00:09: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.604809] pnp 00:0a: [mem 0xfec00000-0xfec00fff]
[    0.604811] pnp 00:0a: [mem 0xfee00000-0xfee00fff]
[    0.604844] system 00:0a: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.604846] system 00:0a: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.604849] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.605214] pnp 00:0b: [io  0x03f8-0x03ff]
[    0.605219] pnp 00:0b: [irq 4]
[    0.605221] pnp 00:0b: [dma 0 disabled]
[    0.605284] pnp 00:0b: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.605644] pnp 00:0c: [io  0x02f8-0x02ff]
[    0.605649] pnp 00:0c: [irq 3]
[    0.605650] pnp 00:0c: [dma 0 disabled]
[    0.605709] pnp 00:0c: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.605901] pnp 00:0d: [mem 0xe0000000-0xefffffff]
[    0.605936] system 00:0d: [mem 0xe0000000-0xefffffff] has been reserved
[    0.605938] system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.606089] pnp 00:0e: [mem 0x00000000-0x0009ffff]
[    0.606091] pnp 00:0e: [mem 0x000c0000-0x000cffff]
[    0.606092] pnp 00:0e: [mem 0x000e0000-0x000fffff]
[    0.606094] pnp 00:0e: [mem 0x00100000-0xbfefffff]
[    0.606095] pnp 00:0e: [mem 0xfed90000-0xffffffff]
[    0.606141] system 00:0e: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.606143] system 00:0e: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.606145] system 00:0e: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.606147] system 00:0e: [mem 0x00100000-0xbfefffff] could not be reserved
[    0.606149] system 00:0e: [mem 0xfed90000-0xffffffff] could not be reserved
[    0.606151] system 00:0e: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.606242] pnp: PnP ACPI: found 15 devices
[    0.606243] ACPI: ACPI bus type pnp unregistered
[    0.611730] PCI: max bus depth: 1 pci_try_num: 2
[    0.611759] pci 0000:00:1c.4: BAR 15: assigned [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.611761] pci 0000:00:1c.0: BAR 14: assigned [mem 0xc0200000-0xc03fffff]
[    0.611764] pci 0000:00:1c.0: BAR 15: assigned [mem 0xc0400000-0xc05fffff 64bit pref]
[    0.611766] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.611769] pci 0000:00:03.0: PCI bridge to [bus 01-01]
[    0.611771] pci 0000:00:03.0:   bridge window [io  0xd000-0xdfff]
[    0.611774] pci 0000:00:03.0:   bridge window [mem 0xf8000000-0xfbefffff]
[    0.611777] pci 0000:00:03.0:   bridge window [mem 0xd4000000-0xdfffffff 64bit pref]
[    0.611780] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.611783] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    0.611786] pci 0000:00:1c.0:   bridge window [mem 0xc0200000-0xc03fffff]
[    0.611790] pci 0000:00:1c.0:   bridge window [mem 0xc0400000-0xc05fffff 64bit pref]
[    0.611795] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
[    0.611797] pci 0000:00:1c.4:   bridge window [io  0xe000-0xefff]
[    0.611801] pci 0000:00:1c.4:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.611804] pci 0000:00:1c.4:   bridge window [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.611809] pci 0000:00:1e.0: PCI bridge to [bus 04-04]
[    0.611810] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.611814] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.611816] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.611833] pci 0000:00:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.611836] pci 0000:00:03.0: setting latency timer to 64
[    0.611841] pci 0000:00:1c.0: enabling device (0104 -> 0107)
[    0.611847] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.611850] pci 0000:00:1c.0: setting latency timer to 64
[    0.611855] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.611858] pci 0000:00:1c.4: setting latency timer to 64
[    0.611863] pci 0000:00:1e.0: setting latency timer to 64
[    0.611866] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.611868] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.611869] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.611871] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.611873] pci_bus 0000:00: resource 8 [mem 0xbff00000-0xdfffffff]
[    0.611874] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.611876] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.611878] pci_bus 0000:01: resource 1 [mem 0xf8000000-0xfbefffff]
[    0.611879] pci_bus 0000:01: resource 2 [mem 0xd4000000-0xdfffffff 64bit pref]
[    0.611881] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    0.611883] pci_bus 0000:02: resource 1 [mem 0xc0200000-0xc03fffff]
[    0.611885] pci_bus 0000:02: resource 2 [mem 0xc0400000-0xc05fffff 64bit pref]
[    0.611886] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.611888] pci_bus 0000:03: resource 1 [mem 0xfbf00000-0xfbffffff]
[    0.611890] pci_bus 0000:03: resource 2 [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.611891] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.611893] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.611895] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.611896] pci_bus 0000:04: resource 7 [mem 0x000d0000-0x000dffff]
[    0.611898] pci_bus 0000:04: resource 8 [mem 0xbff00000-0xdfffffff]
[    0.611900] pci_bus 0000:04: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.611901] pci_bus 0000:ff: resource 0 [io  0x0000-0xffff]
[    0.611903] pci_bus 0000:ff: resource 1 [mem 0x00000000-0xfffffffff]
[    0.611931] NET: Registered protocol family 2
[    0.612047] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.612839] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.615271] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.615612] TCP: Hash tables configured (established 524288 bind 65536)
[    0.615614] TCP reno registered
[    0.615622] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.615652] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.615765] NET: Registered protocol family 1
[    0.615849] pci 0000:01:00.0: Boot video device
[    0.615879] PCI: CLS 32 bytes, default 64
[    0.615880] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.615882] Placing 64MB software IO TLB between ffff8800bb67a000 - ffff8800bf67a000
[    0.615884] software IO TLB at phys 0xbb67a000 - 0xbf67a000
[    0.616224] audit: initializing netlink socket (disabled)
[    0.616231] type=2000 audit(1324847224.440:1): initialized
[    0.641384] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.657448] VFS: Disk quotas dquot_6.5.2
[    0.657491] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.657956] fuse init (API version 7.16)
[    0.658023] msgmni has been set to 7876
[    0.658265] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.658283] io scheduler noop registered
[    0.658284] io scheduler deadline registered
[    0.658314] io scheduler cfq registered (default)
[    0.658505] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.658521] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.658552] intel_idle: MWAIT substates: 0x1120
[    0.658557] intel_idle: v0.4 model 0x1E
[    0.658558] intel_idle: lapic_timer_reliable_states 0x2
[    0.658641] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.658644] ACPI: Power Button [PWRB]
[    0.658671] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.658673] ACPI: Power Button [PWRF]
[    0.658691] ACPI: acpi_idle yielding to intel_idle
[    0.660575] ERST: Table is not found!
[    0.660610] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.680944] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.737579] Freeing initrd memory: 13436k freed
[    0.763625] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.955305] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.975681] 00:0c: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.975900] Linux agpgart interface v0.103
[    0.976666] brd: module loaded
[    0.976995] loop: module loaded
[    0.977093] ata_piix 0000:00:1f.2: version 2.13
[    0.977111] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.977115] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.977147] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.977345] scsi0 : ata_piix
[    0.977404] scsi1 : ata_piix
[    0.978178] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xff90 irq 14
[    0.978183] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xff98 irq 15
[    0.978196] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.978200] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    0.978229] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.978358] scsi2 : ata_piix
[    0.978399] scsi3 : ata_piix
[    0.979052] ata3: SATA max UDMA/133 cmd 0xc800 ctl 0xc480 bmdma 0xc000 irq 19
[    0.979055] ata4: SATA max UDMA/133 cmd 0xc400 ctl 0xc080 bmdma 0xc008 irq 19
[    0.979090] pata_acpi 0000:03:00.1: enabling device (0000 -> 0001)
[    0.979095] pata_acpi 0000:03:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.979116] pata_acpi 0000:03:00.1: setting latency timer to 64
[    0.979127] pata_acpi 0000:03:00.1: PCI INT B disabled
[    0.979319] Fixed MDIO Bus: probed
[    0.979334] PPP generic driver version 2.4.2
[    0.979361] tun: Universal TUN/TAP device driver, 1.6
[    0.979362] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.979411] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.979422] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.979439] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.979442] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    0.979473] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.979496] ehci_hcd 0000:00:1a.0: debug port 2
[    0.983394] ehci_hcd 0000:00:1a.0: cache line size of 32 is not supported
[    0.983405] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf7ffa000
[    0.998727] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.998806] hub 1-0:1.0: USB hub found
[    0.998809] hub 1-0:1.0: 2 ports detected
[    0.998861] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.998870] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.998873] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    0.998898] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.998919] ehci_hcd 0000:00:1d.0: debug port 2
[    1.002815] ehci_hcd 0000:00:1d.0: cache line size of 32 is not supported
[    1.002827] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf7ff8000
[    1.018683] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.018751] hub 2-0:1.0: USB hub found
[    1.018754] hub 2-0:1.0: 2 ports detected
[    1.018798] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.018809] uhci_hcd: USB Universal Host Controller Interface driver
[    1.018849] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.018851] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.018957] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.019018] mousedev: PS/2 mouse device common for all mice
[    1.019095] rtc_cmos 00:03: RTC can wake from S4
[    1.019173] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.019197] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.019266] device-mapper: uevent: version 1.0.3
[    1.019314] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    1.019382] cpuidle: using governor ladder
[    1.019484] cpuidle: using governor menu
[    1.019486] EFI Variables Facility v0.08 2004-May-17
[    1.019658] TCP cubic registered
[    1.019745] NET: Registered protocol family 10
[    1.020107] NET: Registered protocol family 17
[    1.020119] Registering the dns_resolver key type
[    1.020181] PM: Hibernation image not present or could not be loaded.
[    1.020189] registered taskstats version 1
[    1.036579]   Magic number: 7:210:147
[    1.036588] ata_port ata4: hash matches
[    1.036589]  ata4: hash matches
[    1.036628] acpi device:18: hash matches
[    1.036728] rtc_cmos 00:03: setting system clock to 2011-12-25 21:07:05 UTC (1324847225)
[    1.037650] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.037651] EDD information not available.
[    1.042425] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.309078] ata3: SATA link down (SStatus 0 SControl 300)
[    1.310100] usb 1-1: new high speed USB device number 2 using ehci_hcd
[    1.320019] ata4: SATA link down (SStatus 0 SControl 300)
[    1.442825] hub 1-1:1.0: USB hub found
[    1.443021] hub 1-1:1.0: 6 ports detected
[    1.553687] usb 2-1: new high speed USB device number 2 using ehci_hcd
[    1.613601] Refined TSC clocksource calibration: 2806.965 MHz.
[    1.613608] Switching to clocksource tsc
[    1.686274] hub 2-1:1.0: USB hub found
[    1.686516] hub 2-1:1.0: 8 ports detected
[    1.757360] usb 1-1.1: new full speed USB device number 3 using ehci_hcd
[    1.769293] ata2.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.769305] ata2.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.773295] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.773312] ata1.01: SATA link down (SStatus 0 SControl 300)
[    1.781634] ata1.00: ATA-8: SAMSUNG HD502HJ, 1AJ10001, max UDMA/133
[    1.781640] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.785727] ata2.00: ATA-8: SAMSUNG HD502HJ, 1AJ10001, max UDMA/133
[    1.785733] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.785743] ata2.01: ATAPI: TSSTcorp CDDVDW SH-S223C, SB04, max UDMA/100
[    1.789555] ata1.00: configured for UDMA/133
[    1.789853] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD502HJ  1AJ1 PQ: 0 ANSI: 5
[    1.789955] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.790085] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.790482] sd 0:0:0:0: [sda] Write Protect is off
[    1.790488] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.790623] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.793534] ata2.00: configured for UDMA/133
[    1.795334]  sda: sda1 sda2 sda3
[    1.796052] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.809353] ata2.01: configured for UDMA/100
[    1.811389] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HD502HJ  1AJ1 PQ: 0 ANSI: 5
[    1.811533] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.812219] sd 1:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.812753] scsi 1:0:1:0: CD-ROM            TSSTcorp CDDVDW SH-S223C  SB04 PQ: 0 ANSI: 5
[    1.816467] sr0: scsi3-mmc drive: 52x/52x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.816472] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.816612] sr 1:0:1:0: Attached scsi CD-ROM sr0
[    1.816617] sd 1:0:0:0: [sdb] Write Protect is off
[    1.816620] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.816643] sr 1:0:1:0: Attached scsi generic sg2 type 5
[    1.816658] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.874475]  sdb: sdb1 sdb2 sdb3 < sdb5 sdb6 >
[    1.875224] sd 1:0:0:0: [sdb] Attached SCSI disk
[    1.876576] Freeing unused kernel memory: 984k freed
[    1.876694] Write protecting the kernel read-only data: 10240k
[    1.877194] Freeing unused kernel memory: 16k freed
[    1.880267] Freeing unused kernel memory: 1396k freed
[    1.895625] udevd[98]: starting version 173
[    1.922709] pata_jmicron 0000:03:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.922740] pata_jmicron 0000:03:00.1: setting latency timer to 64
[    1.923177] scsi4 : pata_jmicron
[    1.923240] scsi5 : pata_jmicron
[    1.923536] ata5: PATA max UDMA/100 cmd 0xec00 ctl 0xe880 bmdma 0xe400 irq 17
[    1.923538] ata6: PATA max UDMA/100 cmd 0xe800 ctl 0xe480 bmdma 0xe408 irq 17
[    1.924073] ahci 0000:03:00.0: version 3.0
[    1.924082] ahci 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.924806] usb 1-1.5: new high speed USB device number 4 using ehci_hcd
[    1.936689] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    1.936693] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    1.936699] ahci 0000:03:00.0: setting latency timer to 64
[    1.937041] scsi6 : ahci
[    1.937212] scsi7 : ahci
[    1.937292] ata7: SATA max UDMA/133 abar m8192@0xfbffe000 port 0xfbffe100 irq 16
[    1.937296] ata8: SATA max UDMA/133 abar m8192@0xfbffe000 port 0xfbffe180 irq 16
[    2.260278] ata7: SATA link down (SStatus 0 SControl 300)
[    2.264268] ata8: SATA link down (SStatus 0 SControl 300)
[    2.266633] input: A4Tech USB Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input3
[    2.266692] generic-usb 0003:09DA:0080.0001: input,hidraw0: USB HID v1.11 Mouse [A4Tech USB Mouse] on usb-0000:00:1a.0-1.1/input0
[    2.266700] usbcore: registered new interface driver usbhid
[    2.266701] usbhid: USB HID core driver
[    2.340218] usb 1-1.6: new high speed USB device number 5 using ehci_hcd
[    3.031460] EXT4-fs (sdb5): mounted filesystem with ordered data mode. Opts: (null)
[   15.191222] udevd[405]: starting version 173
[   15.224523] Adding 5054460k swap on /dev/sdb6.  Priority:-1 extents:1 across:5054460k 
[   15.226402] lp: driver loaded but no devices found
[   15.228996] e1000e: Intel(R) PRO/1000 Network Driver - 1.3.10-k2
[   15.228999] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[   15.229032] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   15.229043] e1000e 0000:00:19.0: setting latency timer to 64
[   15.229122] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
[   15.237957] nvidia: module license 'NVIDIA' taints kernel.
[   15.237960] Disabling lock debugging due to kernel taint
[   15.249034] EDAC MC: Ver: 2.1.0
[   15.251534] EDAC MC0: Giving out device to 'i7core_edac.c' 'i7 core #0': DEV 0000:ff:03.0
[   15.251546] EDAC PCI0: Giving out device to module 'i7core_edac' controller 'EDAC PCI controller': DEV '0000:ff:03.0' (POLLED)
[   15.251548] EDAC i7core: Driver loaded.
[   15.292573] wmi: Mapper loaded
[   15.343541] type=1400 audit(1324843639.837:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=713 comm="apparmor_parser"
[   15.343815] type=1400 audit(1324843639.837:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=713 comm="apparmor_parser"
[   15.343992] type=1400 audit(1324843639.837:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=713 comm="apparmor_parser"
[   15.432827] Linux video capture interface: v2.00
[   15.433616] uvcvideo: Found UVC 1.00 device <unnamed> (046d:081d)
[   15.447646] input: UVC Camera (046d:081d) as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.2/input/input4
[   15.447746] usbcore: registered new interface driver uvcvideo
[   15.447747] USB Video Class driver (v1.1.0)
[   15.463092] usbcore: registered new interface driver snd-usb-audio
[   15.593384] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.593391] nvidia 0000:01:00.0: setting latency timer to 64
[   15.593395] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   15.593506] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  280.13  Wed Jul 27 16:53:56 PDT 2011
[   15.653737] EXT4-fs (sdb5): re-mounted. Opts: errors=remount-ro
[   16.278007] e1000e 0000:00:19.0: PCI INT A disabled
[   16.278016] e1000e: probe of 0000:00:19.0 failed with error -3
[   16.280530] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   16.280568] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   16.280588] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   16.287777] type=1400 audit(1324843640.781:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=941 comm="apparmor_parser"
[   16.287936] type=1400 audit(1324843640.781:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=942 comm="apparmor_parser"
[   16.288217] type=1400 audit(1324843640.781:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=942 comm="apparmor_parser"
[   16.288395] type=1400 audit(1324843640.781:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=942 comm="apparmor_parser"
[   16.288948] type=1400 audit(1324843640.785:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=945 comm="apparmor_parser"
[   16.289089] type=1400 audit(1324843640.785:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=946 comm="apparmor_parser"
[   16.289296] type=1400 audit(1324843640.785:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=945 comm="apparmor_parser"
[   16.314318] hda_codec: ALC889A: BIOS auto-probing.
[   16.323048] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   16.323149] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   16.323151] hda_intel: Disabling MSI
[   16.323217] HDA Intel 0000:01:00.1: setting latency timer to 64
[   16.379097] init: failsafe main process (886) killed by TERM signal
[   16.379347] init: apport pre-start process (990) terminated with status 1
[   16.385555] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[   16.385557] vesafb: scrolling: redraw
[   16.385559] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   16.387810] vesafb: framebuffer at 0xd5000000, mapped to 0xffffc90012d00000, using 5120k, total 5120k
[   16.387950] Console: switching to colour frame buffer device 160x64
[   16.387971] fb0: VESA VGA frame buffer device
[   16.389339] init: apport post-stop process (1014) terminated with status 1
[   16.429699] ppdev: user-space parallel port driver
[   16.755652] Bluetooth: Core ver 2.16
[   16.755668] NET: Registered protocol family 31
[   16.755670] Bluetooth: HCI device and connection manager initialized
[   16.755671] Bluetooth: HCI socket layer initialized
[   16.755672] Bluetooth: L2CAP socket layer initialized
[   16.755778] Bluetooth: SCO socket layer initialized
[   16.757354] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.757356] Bluetooth: BNEP filters: protocol multicast
[   16.757370] Bluetooth: RFCOMM TTY layer initialized
[   16.757373] Bluetooth: RFCOMM socket layer initialized
[   16.757375] Bluetooth: RFCOMM ver 1.11
[   17.146998] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[   17.178937] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[   17.210829] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[   17.242801] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[   17.258842] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card2/input6
[   17.258903] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card2/input7
[   17.258948] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card2/input8
[   17.258985] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card2/input9
[   18.127343] EXT4-fs (sdb5): re-mounted. Opts: errors=remount-ro,commit=0
[   18.489383] init: plymouth-stop pre-start process (1324) terminated with status 1
[   19.211876] EXT4-fs (sdb5): re-mounted. Opts: errors=remount-ro,commit=0

```interrupts:
```

           CPU0       CPU1       CPU2       CPU3       
  0:         42          0          0          2   IO-APIC-edge      timer
  1:          0        547          0         29   IO-APIC-edge      i8042
  8:          0          0          0          1   IO-APIC-edge      rtc0
  9:          0          0          0          0   IO-APIC-fasteoi   acpi
 14:          4          0          0        671   IO-APIC-edge      ata_piix
 15:         30          0          0       7528   IO-APIC-edge      ata_piix
 16:       9608          0       2765          0   IO-APIC-fasteoi   ehci_hcd:usb1, ahci, nvidia
 17:          0          0        314          0   IO-APIC-fasteoi   pata_jmicron, hda_intel
 19:          0          0          0          0   IO-APIC-fasteoi   ata_piix
 23:          0          0          0         45   IO-APIC-fasteoi   ehci_hcd:usb2
 40:      18179          0          0          0  HPET_MSI-edge      hpet2
 41:          0      10599          0          0  HPET_MSI-edge      hpet3
 42:          0          0       8670          0  HPET_MSI-edge      hpet4
 43:          0          0          0       6009  HPET_MSI-edge      hpet5
 45:          0        393          0          0   PCI-MSI-edge      hda_intel
NMI:          0          0          0          0   Non-maskable interrupts
LOC:         90         74         47         20   Local timer interrupts
SPU:          0          0          0          0   Spurious interrupts
PMI:          0          0          0          0   Performance monitoring interrupts
IWI:          0          0          0          0   IRQ work interrupts
RES:       9687       9351       5047       2620   Rescheduling interrupts
CAL:        560        550        416        470   Function call interrupts
TLB:        113        215         67        107   TLB shootdowns
TRM:          0          0          0          0   Thermal event interrupts
THR:          0          0          0          0   Threshold APIC interrupts
MCE:          0          0          0          0   Machine check exceptions
MCP:          3          3          3          3   Machine check polls
ERR:          0
MIS:          0

```With lan:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-14-generic (buildd@allspice) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 (Ubuntu 3.0.0-14.23-generic 3.0.9)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic root=UUID=a303a224-b575-4c3b-970c-c5bce24b9485 ro hpet=enable quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf680000 (usable)
[    0.000000]  BIOS-e820: 00000000bf680000 - 00000000bf68e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf68e000 - 00000000bf6d0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf6d0000 - 00000000bf6e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf6ed000 - 00000000bf700000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf800000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffa00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI:    /LP DK P55-T3eH9, BIOS 080015  08/27/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-E3FFF write-protect
[    0.000000]   E4000-E7FFF write-through
[    0.000000]   E8000-EBFFF write-protect
[    0.000000]   EC000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 100000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 base 0BFF00000 mask FFFF00000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 4GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 1GB, type UC
[    0.000000] reg 3, base: 3071MB, range: 1MB, type UC
[    0.000000] total RAM covered: 4095M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 2M     num_reg: 4      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3071MB, range: 1MB, type UC
[    0.000000] reg 3, base: 4GB, range: 1GB, type WB
[    0.000000] e820 update range: 00000000bff00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbf680 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff88000009a000] 9a000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000bf680000
[    0.000000]  0000000000 - 00bf600000 page 2M
[    0.000000]  00bf600000 - 00bf680000 page 4k
[    0.000000] kernel direct mapping tables up to bf680000 @ 1fffb000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000140000000
[    0.000000]  0100000000 - 0140000000 page 2M
[    0.000000] kernel direct mapping tables up to 140000000 @ bf67a000-bf680000
[    0.000000] RAMDISK: 365b2000 - 372d1000
[    0.000000] ACPI: RSDP 00000000000f9a30 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 00000000bf680100 0005C (v01 082710 XSDT1410 20100827 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000bf680290 000F4 (v03 082710 FACP1410 20100827 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000bf680460 070D5 (v01  P55DK P55DK000 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 00000000bf68e000 00040
[    0.000000] ACPI: APIC 00000000bf680390 0008C (v01 082710 APIC1410 20100827 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000bf680420 0003C (v01 082710 OEMMCFG  20100827 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000bf68e040 00072 (v01 082710 OEMB1410 20100827 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000bf68a460 00038 (v01 082710 OEMHPET  20100827 MSFT 00000097)
[    0.000000] ACPI: GSCI 00000000bf68e0c0 02024 (v01 082710 GMCHSCI  20100827 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000bf691330 00363 (v01 DpgPmm    CpuPm 00000012 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000140000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000140000000
[    0.000000]   NODE_DATA [000000013fffb000 - 000000013fffffff]
[    0.000000]  [ffffea0000000000-ffffea00045fffff] PMD -> [ffff88013b600000-ffff88013edfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bf680
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 1046031
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3922 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 765624 pages, LIFO batch:31
[    0.000000]   Normal zone: 3584 pages used for memmap
[    0.000000]   Normal zone: 258560 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x86] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x87] disabled)
[    0.000000] ACPI: IOAPIC (id[0x07] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 7, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bf680000 - 00000000bf68e000
[    0.000000] PM: Registered nosave memory: 00000000bf68e000 - 00000000bf6d0000
[    0.000000] PM: Registered nosave memory: 00000000bf6d0000 - 00000000bf6e0000
[    0.000000] PM: Registered nosave memory: 00000000bf6e0000 - 00000000bf6ed000
[    0.000000] PM: Registered nosave memory: 00000000bf6ed000 - 00000000bf700000
[    0.000000] PM: Registered nosave memory: 00000000bf700000 - 00000000bf800000
[    0.000000] PM: Registered nosave memory: 00000000bf800000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffa00000
[    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88013fc00000 s79616 r8192 d22784 u262144
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1028106
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic root=UUID=a303a224-b575-4c3b-970c-c5bce24b9485 ro hpet=enable quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 4032928k/5242880k available (6109k kernel code, 1058756k absent, 151196k reserved, 4876k data, 984k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2806.846 MHz processor.
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 5613.69 BogoMIPS (lpj=11227384)
[    0.000006] pid_max: default: 32768 minimum: 301
[    0.000026] Security Framework initialized
[    0.000040] AppArmor: AppArmor initialized
[    0.000041] Yama: becoming mindful.
[    0.000375] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001683] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.002257] Mount-cache hash table entries: 256
[    0.002366] Initializing cgroup subsys cpuacct
[    0.002371] Initializing cgroup subsys memory
[    0.002376] Initializing cgroup subsys devices
[    0.002378] Initializing cgroup subsys freezer
[    0.002379] Initializing cgroup subsys net_cls
[    0.002381] Initializing cgroup subsys blkio
[    0.002386] Initializing cgroup subsys perf_event
[    0.002407] CPU: Physical Processor ID: 0
[    0.002408] CPU: Processor Core ID: 0
[    0.002413] mce: CPU supports 9 MCE banks
[    0.002423] CPU0: Thermal monitoring enabled (TM1)
[    0.002429] using mwait in idle threads.
[    0.004062] ACPI: Core revision 20110413
[    0.031562] ftrace: allocating 25647 entries in 101 pages
[    0.038175] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.077770] CPU0: Intel(R) Core(TM) i5 CPU         760  @ 2.80GHz stepping 05
[    0.184188] Performance Events: PEBS fmt1+, erratum AAJ80 worked around, Nehalem events, Intel PMU driver.
[    0.184194] ... version:                3
[    0.184195] ... bit width:              48
[    0.184196] ... generic registers:      4
[    0.184197] ... value mask:             0000ffffffffffff
[    0.184198] ... max period:             000000007fffffff
[    0.184199] ... fixed-purpose events:   3
[    0.184200] ... event mask:             000000070000000f
[    0.184525] Booting Node   0, Processors  #1
[    0.184527] smpboot cpu 1: start_ip = 9a000
[    0.296056]  #2
[    0.296058] smpboot cpu 2: start_ip = 9a000
[    0.403857]  #3
[    0.403859] smpboot cpu 3: start_ip = 9a000
[    0.511542] Brought up 4 CPUs
[    0.511545] Total of 4 processors activated (22454.45 BogoMIPS).
[    0.513562] devtmpfs: initialized
[    0.513661] PM: Registering ACPI NVS region at bf68e000 (270336 bytes)
[    0.514854] print_constraints: dummy: 
[    0.514878] Time: 21:17:47  Date: 12/25/11
[    0.514904] NET: Registered protocol family 16
[    0.514981] ACPI: bus type pci registered
[    0.514983] Trying to unpack rootfs image as initramfs...
[    0.515025] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.515027] PCI: not using MMCONFIG
[    0.515029] PCI: Using configuration type 1 for base access
[    0.515600] bio: create slab <bio-0> at 0
[    0.516598] ACPI: EC: Look up EC in DSDT
[    0.517913] ACPI: Executed 1 blocks of module-level executable AML code
[    0.519935] ACPI: SSDT 00000000bf6900f0 01238 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    0.520194] ACPI: Dynamic OEM Table Load:
[    0.520196] ACPI: SSDT           (null) 01238 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    0.520666] ACPI: Interpreter enabled
[    0.520668] ACPI: (supports S0 S1 S3 S4 S5)
[    0.520682] ACPI: Using IOAPIC for interrupt routing
[    0.520698] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.521776] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.554322] ACPI: No dock devices found.
[    0.554325] HEST: Table not found.
[    0.554328] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.554465] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.554590] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.554592] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.554594] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.554596] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.554597] pci_root PNP0A08:00: host bridge window [mem 0xbff00000-0xdfffffff]
[    0.554599] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfed8ffff]
[    0.554610] pci 0000:00:00.0: [8086:d131] type 0 class 0x000600
[    0.554651] pci 0000:00:03.0: [8086:d138] type 1 class 0x000604
[    0.554684] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.554687] pci 0000:00:03.0: PME# disabled
[    0.554703] pci 0000:00:08.0: [8086:d155] type 0 class 0x000880
[    0.554748] pci 0000:00:08.1: [8086:d156] type 0 class 0x000880
[    0.554793] pci 0000:00:08.2: [8086:d157] type 0 class 0x000880
[    0.554835] pci 0000:00:08.3: [8086:d158] type 0 class 0x000880
[    0.554881] pci 0000:00:10.0: [8086:d150] type 0 class 0x000880
[    0.554917] pci 0000:00:10.1: [8086:d151] type 0 class 0x000880
[    0.554971] pci 0000:00:19.0: [8086:10f0] type 0 class 0x000200
[    0.554987] pci 0000:00:19.0: reg 10: [mem 0xf7fc0000-0xf7fdffff]
[    0.554995] pci 0000:00:19.0: reg 14: [mem 0xf7ffc000-0xf7ffcfff]
[    0.555002] pci 0000:00:19.0: reg 18: [io  0xcc00-0xcc1f]
[    0.555045] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.555048] pci 0000:00:19.0: PME# disabled
[    0.555069] pci 0000:00:1a.0: [8086:3b3c] type 0 class 0x000c03
[    0.555087] pci 0000:00:1a.0: reg 10: [mem 0xf7ffa000-0xf7ffa3ff]
[    0.555153] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.555156] pci 0000:00:1a.0: PME# disabled
[    0.555176] pci 0000:00:1b.0: [8086:3b56] type 0 class 0x000403
[    0.555189] pci 0000:00:1b.0: reg 10: [mem 0xf7ff4000-0xf7ff7fff 64bit]
[    0.555237] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.555240] pci 0000:00:1b.0: PME# disabled
[    0.555256] pci 0000:00:1c.0: [8086:3b42] type 1 class 0x000604
[    0.555304] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.555307] pci 0000:00:1c.0: PME# disabled
[    0.555327] pci 0000:00:1c.4: [8086:3b4a] type 1 class 0x000604
[    0.555378] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.555381] pci 0000:00:1c.4: PME# disabled
[    0.555409] pci 0000:00:1d.0: [8086:3b34] type 0 class 0x000c03
[    0.555427] pci 0000:00:1d.0: reg 10: [mem 0xf7ff8000-0xf7ff83ff]
[    0.555493] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.555496] pci 0000:00:1d.0: PME# disabled
[    0.555514] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    0.555563] pci 0000:00:1f.0: [8086:3b02] type 0 class 0x000601
[    0.555663] pci 0000:00:1f.2: [8086:3b20] type 0 class 0x000101
[    0.555677] pci 0000:00:1f.2: reg 10: [io  0x0000-0x0007]
[    0.555683] pci 0000:00:1f.2: reg 14: [io  0x0000-0x0003]
[    0.555690] pci 0000:00:1f.2: reg 18: [io  0x0000-0x0007]
[    0.555697] pci 0000:00:1f.2: reg 1c: [io  0x0000-0x0003]
[    0.555704] pci 0000:00:1f.2: reg 20: [io  0xff90-0xff9f]
[    0.555711] pci 0000:00:1f.2: reg 24: [io  0xffa0-0xffaf]
[    0.555742] pci 0000:00:1f.3: [8086:3b30] type 0 class 0x000c05
[    0.555755] pci 0000:00:1f.3: reg 10: [mem 0xf7ff2000-0xf7ff20ff 64bit]
[    0.555774] pci 0000:00:1f.3: reg 20: [io  0x0400-0x041f]
[    0.555801] pci 0000:00:1f.5: [8086:3b26] type 0 class 0x000101
[    0.555814] pci 0000:00:1f.5: reg 10: [io  0xc800-0xc807]
[    0.555821] pci 0000:00:1f.5: reg 14: [io  0xc480-0xc483]
[    0.555828] pci 0000:00:1f.5: reg 18: [io  0xc400-0xc407]
[    0.555835] pci 0000:00:1f.5: reg 1c: [io  0xc080-0xc083]
[    0.555841] pci 0000:00:1f.5: reg 20: [io  0xc000-0xc00f]
[    0.555848] pci 0000:00:1f.5: reg 24: [io  0xbc00-0xbc0f]
[    0.555910] pci 0000:01:00.0: [10de:0e22] type 0 class 0x000300
[    0.555918] pci 0000:01:00.0: reg 10: [mem 0xf8000000-0xf9ffffff]
[    0.555928] pci 0000:01:00.0: reg 14: [mem 0xd8000000-0xdfffffff 64bit pref]
[    0.555937] pci 0000:01:00.0: reg 1c: [mem 0xd4000000-0xd7ffffff 64bit pref]
[    0.555944] pci 0000:01:00.0: reg 24: [io  0xdc00-0xdc7f]
[    0.555950] pci 0000:01:00.0: reg 30: [mem 0xfbe80000-0xfbefffff pref]
[    0.555988] pci 0000:01:00.1: [10de:0beb] type 0 class 0x000403
[    0.555996] pci 0000:01:00.1: reg 10: [mem 0xfbe7c000-0xfbe7ffff]
[    0.563335] pci 0000:00:03.0: PCI bridge to [bus 01-01]
[    0.563337] pci 0000:00:03.0:   bridge window [io  0xd000-0xdfff]
[    0.563340] pci 0000:00:03.0:   bridge window [mem 0xf8000000-0xfbefffff]
[    0.563344] pci 0000:00:03.0:   bridge window [mem 0xd4000000-0xdfffffff 64bit pref]
[    0.563379] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.563382] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.563385] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.563390] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.563440] pci 0000:03:00.0: [197b:2363] type 0 class 0x000101
[    0.563523] pci 0000:03:00.0: reg 24: [mem 0xfbffe000-0xfbffffff]
[    0.563563] pci 0000:03:00.0: PME# supported from D3hot
[    0.563568] pci 0000:03:00.0: PME# disabled
[    0.563596] pci 0000:03:00.1: [197b:2363] type 0 class 0x000101
[    0.563618] pci 0000:03:00.1: reg 10: [io  0xec00-0xec07]
[    0.563631] pci 0000:03:00.1: reg 14: [io  0xe880-0xe883]
[    0.563644] pci 0000:03:00.1: reg 18: [io  0xe800-0xe807]
[    0.563656] pci 0000:03:00.1: reg 1c: [io  0xe480-0xe483]
[    0.563669] pci 0000:03:00.1: reg 20: [io  0xe400-0xe40f]
[    0.563735] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.563747] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
[    0.563750] pci 0000:00:1c.4:   bridge window [io  0xe000-0xefff]
[    0.563753] pci 0000:00:1c.4:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.563758] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.563811] pci 0000:00:1e.0: PCI bridge to [bus 04-04] (subtractive decode)
[    0.563814] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.563818] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.563823] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.563825] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.563826] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.563828] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.563830] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.563832] pci 0000:00:1e.0:   bridge window [mem 0xbff00000-0xdfffffff] (subtractive decode)
[    0.563834] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfed8ffff] (subtractive decode)
[    0.563850] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.563960] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR1E._PRT]
[    0.564011] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR20._PRT]
[    0.564035] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR24._PRT]
[    0.564139]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.564270]  pci0000:00: ACPI _OSC request failed (AE_SUPPORT), returned control mask: 0x0d
[    0.564272] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.570461] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
[    0.570493] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[    0.570523] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 *10 11 12 14 15)
[    0.570554] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 *11 12 14 15)
[    0.570585] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 *11 12 14 15)
[    0.570616] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
[    0.570648] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 6 *7 10 11 12 14 15)
[    0.570679] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *6 7 10 11 12 14 15)
[    0.570752] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.570754] vgaarb: loaded
[    0.570755] vgaarb: bridge control possible 0000:01:00.0
[    0.570883] SCSI subsystem initialized
[    0.570928] libata version 3.00 loaded.
[    0.570956] usbcore: registered new interface driver usbfs
[    0.570962] usbcore: registered new interface driver hub
[    0.570980] usbcore: registered new device driver usb
[    0.571035] PCI: Using ACPI for IRQ routing
[    0.576746] PCI: Discovered peer bus ff
[    0.576771] pci 0000:ff:00.0: [8086:2c51] type 0 class 0x000600
[    0.576787] pci 0000:ff:00.1: [8086:2c81] type 0 class 0x000600
[    0.576803] pci 0000:ff:02.0: [8086:2c90] type 0 class 0x000600
[    0.576817] pci 0000:ff:02.1: [8086:2c91] type 0 class 0x000600
[    0.576833] pci 0000:ff:03.0: [8086:2c98] type 0 class 0x000600
[    0.576848] pci 0000:ff:03.1: [8086:2c99] type 0 class 0x000600
[    0.576863] pci 0000:ff:03.4: [8086:2c9c] type 0 class 0x000600
[    0.576877] pci 0000:ff:04.0: [8086:2ca0] type 0 class 0x000600
[    0.576891] pci 0000:ff:04.1: [8086:2ca1] type 0 class 0x000600
[    0.576904] pci 0000:ff:04.2: [8086:2ca2] type 0 class 0x000600
[    0.576918] pci 0000:ff:04.3: [8086:2ca3] type 0 class 0x000600
[    0.576933] pci 0000:ff:05.0: [8086:2ca8] type 0 class 0x000600
[    0.576947] pci 0000:ff:05.1: [8086:2ca9] type 0 class 0x000600
[    0.576961] pci 0000:ff:05.2: [8086:2caa] type 0 class 0x000600
[    0.576975] pci 0000:ff:05.3: [8086:2cab] type 0 class 0x000600
[    0.577223] PCI: pci_cache_line_size set to 64 bytes
[    0.577297] Expanded resource reserved due to conflict with PCI Bus 0000:00
[    0.577299] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.577300] reserve RAM buffer: 00000000bf680000 - 00000000bfffffff 
[    0.577370] NetLabel: Initializing
[    0.577371] NetLabel:  domain hash size = 128
[    0.577372] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.577380] NetLabel:  unlabeled traffic allowed by default
[    0.577433] HPET: 8 timers in total, 5 timers will be used for per-cpu timer
[    0.577439] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 40, 41, 42, 43, 44, 0
[    0.577444] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.583292] hpet: hpet2 irq 40 for MSI
[    0.583460] hpet: hpet3 irq 41 for MSI
[    0.587404] hpet: hpet4 irq 42 for MSI
[    0.591395] hpet: hpet5 irq 43 for MSI
[    0.591416] Switching to clocksource hpet
[    0.595216] Switched to NOHz mode on CPU #0
[    0.595352] Switched to NOHz mode on CPU #2
[    0.595374] Switched to NOHz mode on CPU #3
[    0.595383] Switched to NOHz mode on CPU #1
[    0.595947] AppArmor: AppArmor Filesystem Enabled
[    0.595968] pnp: PnP ACPI init
[    0.595981] ACPI: bus type pnp registered
[    0.596070] pnp 00:00: [bus 00-ff]
[    0.596072] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.596073] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.596075] pnp 00:00: [io  0x0d00-0xffff window]
[    0.596077] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.596078] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.596080] pnp 00:00: [mem 0xbff00000-0xdfffffff window]
[    0.596081] pnp 00:00: [mem 0xf0000000-0xfed8ffff window]
[    0.596137] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.596144] pnp 00:01: [mem 0xfc000000-0xfcffffff]
[    0.596146] pnp 00:01: [mem 0xfd000000-0xfdffffff]
[    0.596147] pnp 00:01: [mem 0xfe000000-0xfebfffff]
[    0.596148] pnp 00:01: [mem 0xfed14000-0xfed19fff]
[    0.596190] system 00:01: [mem 0xfc000000-0xfcffffff] has been reserved
[    0.596192] system 00:01: [mem 0xfd000000-0xfdffffff] has been reserved
[    0.596194] system 00:01: [mem 0xfe000000-0xfebfffff] has been reserved
[    0.596196] system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
[    0.596198] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.596225] pnp 00:02: [dma 4]
[    0.596227] pnp 00:02: [io  0x0000-0x000f]
[    0.596228] pnp 00:02: [io  0x0081-0x0083]
[    0.596229] pnp 00:02: [io  0x0087]
[    0.596230] pnp 00:02: [io  0x0089-0x008b]
[    0.596232] pnp 00:02: [io  0x008f]
[    0.596233] pnp 00:02: [io  0x00c0-0x00df]
[    0.596249] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.596256] pnp 00:03: [io  0x0070-0x0071]
[    0.596263] pnp 00:03: [irq 8]
[    0.596281] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.596287] pnp 00:04: [io  0x0061]
[    0.596302] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.596308] pnp 00:05: [io  0x00f0-0x00ff]
[    0.596312] pnp 00:05: [irq 13]
[    0.596328] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.596348] pnp 00:06: [io  0x0060]
[    0.596350] pnp 00:06: [io  0x0064]
[    0.596354] pnp 00:06: [irq 1]
[    0.596376] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.596486] pnp 00:07: [io  0x0000-0xffffffffffffffff disabled]
[    0.596487] pnp 00:07: [io  0x0a00-0x0a0f]
[    0.596489] pnp 00:07: [io  0x0a10-0x0a1f]
[    0.596490] pnp 00:07: [io  0x0a20-0x0a2f]
[    0.596491] pnp 00:07: [io  0x0a30-0x0a3f]
[    0.596525] system 00:07: [io  0x0a00-0x0a0f] has been reserved
[    0.596527] system 00:07: [io  0x0a10-0x0a1f] has been reserved
[    0.596529] system 00:07: [io  0x0a20-0x0a2f] has been reserved
[    0.596531] system 00:07: [io  0x0a30-0x0a3f] has been reserved
[    0.596533] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.596612] pnp 00:08: [io  0x0010-0x001f]
[    0.596613] pnp 00:08: [io  0x0022-0x003f]
[    0.596615] pnp 00:08: [io  0x0044-0x005f]
[    0.596616] pnp 00:08: [io  0x0062-0x0063]
[    0.596619] pnp 00:08: [io  0x0065-0x006f]
[    0.596621] pnp 00:08: [io  0x0072-0x007f]
[    0.596622] pnp 00:08: [io  0x0080]
[    0.596623] pnp 00:08: [io  0x0084-0x0086]
[    0.596624] pnp 00:08: [io  0x0088]
[    0.596626] pnp 00:08: [io  0x008c-0x008e]
[    0.596627] pnp 00:08: [io  0x0090-0x009f]
[    0.596628] pnp 00:08: [io  0x00a2-0x00bf]
[    0.596629] pnp 00:08: [io  0x00e0-0x00ef]
[    0.596631] pnp 00:08: [io  0x04d0-0x04d1]
[    0.596632] pnp 00:08: [io  0x0800-0x087f]
[    0.596633] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    0.596635] pnp 00:08: [io  0x0500-0x057f]
[    0.596636] pnp 00:08: [mem 0xfed1c000-0xfed1ffff]
[    0.596638] pnp 00:08: [mem 0xfed20000-0xfed3ffff]
[    0.596639] pnp 00:08: [mem 0xfed40000-0xfed8ffff]
[    0.596686] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.596688] system 00:08: [io  0x0800-0x087f] has been reserved
[    0.596690] system 00:08: [io  0x0500-0x057f] has been reserved
[    0.596692] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.596694] system 00:08: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.596696] system 00:08: [mem 0xfed40000-0xfed8ffff] has been reserved
[    0.596699] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.596738] pnp 00:09: [mem 0xfed00000-0xfed003ff]
[    0.596756] pnp 00:09: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.596812] pnp 00:0a: [mem 0xfec00000-0xfec00fff]
[    0.596813] pnp 00:0a: [mem 0xfee00000-0xfee00fff]
[    0.596846] system 00:0a: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.596849] system 00:0a: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.596851] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.597216] pnp 00:0b: [io  0x03f8-0x03ff]
[    0.597222] pnp 00:0b: [irq 4]
[    0.597223] pnp 00:0b: [dma 0 disabled]
[    0.597286] pnp 00:0b: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.597645] pnp 00:0c: [io  0x02f8-0x02ff]
[    0.597650] pnp 00:0c: [irq 3]
[    0.597651] pnp 00:0c: [dma 0 disabled]
[    0.597711] pnp 00:0c: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.597903] pnp 00:0d: [mem 0xe0000000-0xefffffff]
[    0.597937] system 00:0d: [mem 0xe0000000-0xefffffff] has been reserved
[    0.597940] system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.598090] pnp 00:0e: [mem 0x00000000-0x0009ffff]
[    0.598092] pnp 00:0e: [mem 0x000c0000-0x000cffff]
[    0.598093] pnp 00:0e: [mem 0x000e0000-0x000fffff]
[    0.598095] pnp 00:0e: [mem 0x00100000-0xbfefffff]
[    0.598096] pnp 00:0e: [mem 0xfed90000-0xffffffff]
[    0.598143] system 00:0e: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.598145] system 00:0e: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.598147] system 00:0e: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.598148] system 00:0e: [mem 0x00100000-0xbfefffff] could not be reserved
[    0.598150] system 00:0e: [mem 0xfed90000-0xffffffff] could not be reserved
[    0.598153] system 00:0e: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.598243] pnp: PnP ACPI: found 15 devices
[    0.598245] ACPI: ACPI bus type pnp unregistered
[    0.603736] PCI: max bus depth: 1 pci_try_num: 2
[    0.603765] pci 0000:00:1c.4: BAR 15: assigned [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.603767] pci 0000:00:1c.0: BAR 14: assigned [mem 0xc0200000-0xc03fffff]
[    0.603770] pci 0000:00:1c.0: BAR 15: assigned [mem 0xc0400000-0xc05fffff 64bit pref]
[    0.603772] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.603775] pci 0000:00:03.0: PCI bridge to [bus 01-01]
[    0.603777] pci 0000:00:03.0:   bridge window [io  0xd000-0xdfff]
[    0.603780] pci 0000:00:03.0:   bridge window [mem 0xf8000000-0xfbefffff]
[    0.603783] pci 0000:00:03.0:   bridge window [mem 0xd4000000-0xdfffffff 64bit pref]
[    0.603787] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.603789] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    0.603793] pci 0000:00:1c.0:   bridge window [mem 0xc0200000-0xc03fffff]
[    0.603796] pci 0000:00:1c.0:   bridge window [mem 0xc0400000-0xc05fffff 64bit pref]
[    0.603801] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
[    0.603803] pci 0000:00:1c.4:   bridge window [io  0xe000-0xefff]
[    0.603807] pci 0000:00:1c.4:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.603810] pci 0000:00:1c.4:   bridge window [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.603815] pci 0000:00:1e.0: PCI bridge to [bus 04-04]
[    0.603816] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.603820] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.603823] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.603840] pci 0000:00:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.603843] pci 0000:00:03.0: setting latency timer to 64
[    0.603847] pci 0000:00:1c.0: enabling device (0104 -> 0107)
[    0.603854] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.603857] pci 0000:00:1c.0: setting latency timer to 64
[    0.603862] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.603865] pci 0000:00:1c.4: setting latency timer to 64
[    0.603870] pci 0000:00:1e.0: setting latency timer to 64
[    0.603873] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.603875] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.603876] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.603878] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.603880] pci_bus 0000:00: resource 8 [mem 0xbff00000-0xdfffffff]
[    0.603881] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.603883] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.603885] pci_bus 0000:01: resource 1 [mem 0xf8000000-0xfbefffff]
[    0.603887] pci_bus 0000:01: resource 2 [mem 0xd4000000-0xdfffffff 64bit pref]
[    0.603888] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    0.603890] pci_bus 0000:02: resource 1 [mem 0xc0200000-0xc03fffff]
[    0.603892] pci_bus 0000:02: resource 2 [mem 0xc0400000-0xc05fffff 64bit pref]
[    0.603893] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.603895] pci_bus 0000:03: resource 1 [mem 0xfbf00000-0xfbffffff]
[    0.603897] pci_bus 0000:03: resource 2 [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.603899] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.603900] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.603902] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.603903] pci_bus 0000:04: resource 7 [mem 0x000d0000-0x000dffff]
[    0.603905] pci_bus 0000:04: resource 8 [mem 0xbff00000-0xdfffffff]
[    0.603907] pci_bus 0000:04: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.603908] pci_bus 0000:ff: resource 0 [io  0x0000-0xffff]
[    0.603910] pci_bus 0000:ff: resource 1 [mem 0x00000000-0xfffffffff]
[    0.603938] NET: Registered protocol family 2
[    0.604052] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.604842] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.607275] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.607609] TCP: Hash tables configured (established 524288 bind 65536)
[    0.607611] TCP reno registered
[    0.607620] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.607650] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.607759] NET: Registered protocol family 1
[    0.607841] pci 0000:01:00.0: Boot video device
[    0.607871] PCI: CLS 32 bytes, default 64
[    0.607872] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.607874] Placing 64MB software IO TLB between ffff8800bb67a000 - ffff8800bf67a000
[    0.607876] software IO TLB at phys 0xbb67a000 - 0xbf67a000
[    0.608278] audit: initializing netlink socket (disabled)
[    0.608286] type=2000 audit(1324847866.432:1): initialized
[    0.633260] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.649342] VFS: Disk quotas dquot_6.5.2
[    0.649385] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.649850] fuse init (API version 7.16)
[    0.649917] msgmni has been set to 7876
[    0.650159] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.650176] io scheduler noop registered
[    0.650178] io scheduler deadline registered
[    0.650208] io scheduler cfq registered (default)
[    0.650398] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.650414] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.650445] intel_idle: MWAIT substates: 0x1120
[    0.650450] intel_idle: v0.4 model 0x1E
[    0.650451] intel_idle: lapic_timer_reliable_states 0x2
[    0.650533] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.650537] ACPI: Power Button [PWRB]
[    0.650563] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.650566] ACPI: Power Button [PWRF]
[    0.650584] ACPI: acpi_idle yielding to intel_idle
[    0.652398] ERST: Table is not found!
[    0.652433] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.672769] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.729553] Freeing initrd memory: 13436k freed
[    0.755561] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.943224] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.963602] 00:0c: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.963830] Linux agpgart interface v0.103
[    0.964572] brd: module loaded
[    0.964924] loop: module loaded
[    0.965022] ata_piix 0000:00:1f.2: version 2.13
[    0.965040] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.965044] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.965078] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.965276] scsi0 : ata_piix
[    0.965334] scsi1 : ata_piix
[    0.966106] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xff90 irq 14
[    0.966111] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xff98 irq 15
[    0.966125] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.966129] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    0.966157] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.966285] scsi2 : ata_piix
[    0.966326] scsi3 : ata_piix
[    0.966915] ata3: SATA max UDMA/133 cmd 0xc800 ctl 0xc480 bmdma 0xc000 irq 19
[    0.966918] ata4: SATA max UDMA/133 cmd 0xc400 ctl 0xc080 bmdma 0xc008 irq 19
[    0.966953] pata_acpi 0000:03:00.1: enabling device (0000 -> 0001)
[    0.966958] pata_acpi 0000:03:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.966981] pata_acpi 0000:03:00.1: setting latency timer to 64
[    0.966991] pata_acpi 0000:03:00.1: PCI INT B disabled
[    0.967178] Fixed MDIO Bus: probed
[    0.967193] PPP generic driver version 2.4.2
[    0.967217] tun: Universal TUN/TAP device driver, 1.6
[    0.967218] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.967268] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.967279] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.967294] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.967297] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    0.967319] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.967344] ehci_hcd 0000:00:1a.0: debug port 2
[    0.971230] ehci_hcd 0000:00:1a.0: cache line size of 32 is not supported
[    0.971242] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf7ffa000
[    0.986674] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.986752] hub 1-0:1.0: USB hub found
[    0.986756] hub 1-0:1.0: 2 ports detected
[    0.986807] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.986817] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.986819] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    0.986842] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.986864] ehci_hcd 0000:00:1d.0: debug port 2
[    0.990743] ehci_hcd 0000:00:1d.0: cache line size of 32 is not supported
[    0.990754] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf7ff8000
[    1.006630] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.006699] hub 2-0:1.0: USB hub found
[    1.006702] hub 2-0:1.0: 2 ports detected
[    1.006746] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.006756] uhci_hcd: USB Universal Host Controller Interface driver
[    1.006795] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.006796] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.006903] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.006966] mousedev: PS/2 mouse device common for all mice
[    1.007040] rtc_cmos 00:03: RTC can wake from S4
[    1.007119] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.007143] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.007217] device-mapper: uevent: version 1.0.3
[    1.007267] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    1.007335] cpuidle: using governor ladder
[    1.007438] cpuidle: using governor menu
[    1.007440] EFI Variables Facility v0.08 2004-May-17
[    1.007617] TCP cubic registered
[    1.007703] NET: Registered protocol family 10
[    1.008059] NET: Registered protocol family 17
[    1.008069] Registering the dns_resolver key type
[    1.008130] PM: Hibernation image not present or could not be loaded.
[    1.008138] registered taskstats version 1
[    1.024240]   Magic number: 7:863:298
[    1.024389] rtc_cmos 00:03: setting system clock to 2011-12-25 21:17:47 UTC (1324847867)
[    1.025313] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.025314] EDD information not available.
[    1.030556] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.296882] ata4: SATA link down (SStatus 0 SControl 300)
[    1.298135] usb 1-1: new high speed USB device number 2 using ehci_hcd
[    1.307844] ata3: SATA link down (SStatus 0 SControl 300)
[    1.430608] hub 1-1:1.0: USB hub found
[    1.430727] hub 1-1:1.0: 6 ports detected
[    1.541630] usb 2-1: new high speed USB device number 2 using ehci_hcd
[    1.605542] Refined TSC clocksource calibration: 2806.964 MHz.
[    1.605549] Switching to clocksource tsc
[    1.674077] hub 2-1:1.0: USB hub found
[    1.674192] hub 2-1:1.0: 8 ports detected
[    1.745458] usb 1-1.1: new full speed USB device number 3 using ehci_hcd
[    1.757242] ata2.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.757254] ata2.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.761368] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.761379] ata1.01: SATA link down (SStatus 0 SControl 300)
[    1.769483] ata1.00: ATA-8: SAMSUNG HD502HJ, 1AJ10001, max UDMA/133
[    1.769489] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.773697] ata2.00: ATA-8: SAMSUNG HD502HJ, 1AJ10001, max UDMA/133
[    1.773703] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.773713] ata2.01: ATAPI: TSSTcorp CDDVDW SH-S223C, SB04, max UDMA/100
[    1.777599] ata1.00: configured for UDMA/133
[    1.777900] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD502HJ  1AJ1 PQ: 0 ANSI: 5
[    1.778004] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.778161] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.778549] sd 0:0:0:0: [sda] Write Protect is off
[    1.778556] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.778623] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.781505] ata2.00: configured for UDMA/133
[    1.790903]  sda: sda1 sda2 sda3
[    1.791591] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.797217] ata2.01: configured for UDMA/100
[    1.799039] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HD502HJ  1AJ1 PQ: 0 ANSI: 5
[    1.799137] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.799978] sd 1:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.800619] scsi 1:0:1:0: CD-ROM            TSSTcorp CDDVDW SH-S223C  SB04 PQ: 0 ANSI: 5
[    1.805222] sr0: scsi3-mmc drive: 52x/52x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.805228] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.805315] sd 1:0:0:0: [sdb] Write Protect is off
[    1.805318] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.805336] sr 1:0:1:0: Attached scsi CD-ROM sr0
[    1.805368] sr 1:0:1:0: Attached scsi generic sg2 type 5
[    1.805416] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.858935]  sdb: sdb1 sdb2 sdb3 < sdb5 sdb6 >
[    1.859661] sd 1:0:0:0: [sdb] Attached SCSI disk
[    1.861160] Freeing unused kernel memory: 984k freed
[    1.861268] Write protecting the kernel read-only data: 10240k
[    1.861667] Freeing unused kernel memory: 16k freed
[    1.864716] Freeing unused kernel memory: 1396k freed
[    1.880156] udevd[99]: starting version 173
[    1.899507] pata_jmicron 0000:03:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.899532] pata_jmicron 0000:03:00.1: setting latency timer to 64
[    1.902081] scsi4 : pata_jmicron
[    1.904934] scsi5 : pata_jmicron
[    1.905226] ata5: PATA max UDMA/100 cmd 0xec00 ctl 0xe880 bmdma 0xe400 irq 17
[    1.905228] ata6: PATA max UDMA/100 cmd 0xe800 ctl 0xe480 bmdma 0xe408 irq 17
[    1.912752] usb 1-1.5: new high speed USB device number 4 using ehci_hcd
[    2.228450] ahci 0000:03:00.0: version 3.0
[    2.228465] ahci 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.230885] input: A4Tech USB Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input3
[    2.230944] generic-usb 0003:09DA:0080.0001: input,hidraw0: USB HID v1.11 Mouse [A4Tech USB Mouse] on usb-0000:00:1a.0-1.1/input0
[    2.230952] usbcore: registered new interface driver usbhid
[    2.230953] usbhid: USB HID core driver
[    2.244242] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    2.244245] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    2.244250] ahci 0000:03:00.0: setting latency timer to 64
[    2.244646] scsi6 : ahci
[    2.245037] scsi7 : ahci
[    2.245179] ata7: SATA max UDMA/133 abar m8192@0xfbffe000 port 0xfbffe100 irq 16
[    2.245185] ata8: SATA max UDMA/133 abar m8192@0xfbffe000 port 0xfbffe180 irq 16
[    2.332021] usb 1-1.6: new high speed USB device number 5 using ehci_hcd
[    2.563422] ata8: SATA link down (SStatus 0 SControl 300)
[    2.563460] ata7: SATA link down (SStatus 0 SControl 300)
[    3.098164] EXT4-fs (sdb5): mounted filesystem with ordered data mode. Opts: (null)
[   15.125992] udevd[438]: starting version 173
[   15.160392] Adding 5054460k swap on /dev/sdb6.  Priority:-1 extents:1 across:5054460k 
[   15.160470] lp: driver loaded but no devices found
[   15.162818] e1000e: Intel(R) PRO/1000 Network Driver - 1.3.10-k2
[   15.162820] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[   15.162852] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   15.162860] e1000e 0000:00:19.0: setting latency timer to 64
[   15.162944] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
[   15.176014] nvidia: module license 'NVIDIA' taints kernel.
[   15.176017] Disabling lock debugging due to kernel taint
[   15.237981] type=1400 audit(1324844281.740:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=688 comm="apparmor_parser"
[   15.238254] type=1400 audit(1324844281.740:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=688 comm="apparmor_parser"
[   15.238430] type=1400 audit(1324844281.740:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=688 comm="apparmor_parser"
[   15.261614] EDAC MC: Ver: 2.1.0
[   15.285130] wmi: Mapper loaded
[   15.300520] Linux video capture interface: v2.00
[   15.300883] uvcvideo: Found UVC 1.00 device <unnamed> (046d:081d)
[   15.343077] EDAC MC0: Giving out device to 'i7core_edac.c' 'i7 core #0': DEV 0000:ff:03.0
[   15.343091] EDAC PCI0: Giving out device to module 'i7core_edac' controller 'EDAC PCI controller': DEV '0000:ff:03.0' (POLLED)
[   15.343093] EDAC i7core: Driver loaded.
[   15.439625] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) 00:01:29:00:a4:5b
[   15.439628] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[   15.439682] e1000e 0000:00:19.0: eth0: MAC: 9, PHY: 9, PBA No: FFFFFF-0FF
[   15.459004] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   15.459045] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   15.459064] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.478880] input: UVC Camera (046d:081d) as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.2/input/input4
[   15.478932] usbcore: registered new interface driver uvcvideo
[   15.478933] USB Video Class driver (v1.1.0)
[   15.492617] usbcore: registered new interface driver snd-usb-audio
[   15.499648] hda_codec: ALC889A: BIOS auto-probing.
[   15.508319] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   15.508425] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   15.508428] hda_intel: Disabling MSI
[   15.508473] HDA Intel 0000:01:00.1: setting latency timer to 64
[   15.527117] udevd[478]: renamed network interface eth0 to eth1
[   15.594475] EXT4-fs (sdb5): re-mounted. Opts: errors=remount-ro
[   15.809147] type=1400 audit(1324844282.312:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=985 comm="apparmor_parser"
[   15.809311] type=1400 audit(1324844282.312:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=986 comm="apparmor_parser"
[   15.809595] type=1400 audit(1324844282.312:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=986 comm="apparmor_parser"
[   15.809774] type=1400 audit(1324844282.312:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=986 comm="apparmor_parser"
[   15.810280] type=1400 audit(1324844282.316:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=989 comm="apparmor_parser"
[   15.810443] type=1400 audit(1324844282.316:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=990 comm="apparmor_parser"
[   15.810629] type=1400 audit(1324844282.316:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=989 comm="apparmor_parser"
[   15.866691] init: failsafe main process (932) killed by TERM signal
[   15.866949] init: apport pre-start process (1023) terminated with status 1
[   15.869127] init: apport post-stop process (1040) terminated with status 1
[   15.929931] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
[   15.976433] Bluetooth: Core ver 2.16
[   15.976452] NET: Registered protocol family 31
[   15.976453] Bluetooth: HCI device and connection manager initialized
[   15.976455] Bluetooth: HCI socket layer initialized
[   15.976456] Bluetooth: L2CAP socket layer initialized
[   15.976487] Bluetooth: SCO socket layer initialized
[   15.977719] Bluetooth: RFCOMM TTY layer initialized
[   15.977724] Bluetooth: RFCOMM socket layer initialized
[   15.977725] Bluetooth: RFCOMM ver 1.11
[   15.978124] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.978126] Bluetooth: BNEP filters: protocol multicast
[   15.985475] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
[   15.985822] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   16.206318] EXT4-fs (sdb5): re-mounted. Opts: errors=remount-ro,commit=0
[   16.360691] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[   16.392843] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[   16.428673] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[   16.460542] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[   16.476563] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card2/input6
[   16.476647] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card2/input7
[   16.476696] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card2/input8
[   16.476733] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card2/input9
[   16.477072] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.477081] nvidia 0000:01:00.0: setting latency timer to 64
[   16.477086] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   16.477203] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  280.13  Wed Jul 27 16:53:56 PDT 2011
[   16.540224] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[   16.540226] vesafb: scrolling: redraw
[   16.540228] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   16.542391] vesafb: framebuffer at 0xd5000000, mapped to 0xffffc90013d80000, using 5120k, total 5120k
[   16.542528] Console: switching to colour frame buffer device 160x64
[   16.542549] fb0: VESA VGA frame buffer device
[   16.555620] init: plymouth-splash main process (1242) terminated with status 1
[   16.571209] ppdev: user-space parallel port driver
[   17.395579] e1000e: eth1 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx
[   17.395583] e1000e 0000:00:19.0: eth1: 10/100 speed: disabling TSO
[   17.395835] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   18.468737] EXT4-fs (sdb5): re-mounted. Opts: errors=remount-ro,commit=0
[   27.551915] eth1: no IPv6 routers present

```interrupts:
```

           CPU0       CPU1       CPU2       CPU3       
  0:         42          0          0          3   IO-APIC-edge      timer
  1:          0       1986          0         31   IO-APIC-edge      i8042
  8:          0          0          0          1   IO-APIC-edge      rtc0
  9:          0          0          0          0   IO-APIC-fasteoi   acpi
 14:          4          0          0        671   IO-APIC-edge      ata_piix
 15:       6644          0          0       6190   IO-APIC-edge      ata_piix
 16:      44877          0       6450          0   IO-APIC-fasteoi   ehci_hcd:usb1, ahci, nvidia
 17:          0          0        326          0   IO-APIC-fasteoi   pata_jmicron, hda_intel
 19:          0          0          0          0   IO-APIC-fasteoi   ata_piix
 23:          0          0          0         45   IO-APIC-fasteoi   ehci_hcd:usb2
 40:     129388          0          0          0  HPET_MSI-edge      hpet2
 41:          0     143607          0          0  HPET_MSI-edge      hpet3
 42:          0          0      61536          0  HPET_MSI-edge      hpet4
 43:          0          0          0      38782  HPET_MSI-edge      hpet5
 45:       9979          0         39          0   PCI-MSI-edge      eth1
 46:          0        387          0          0   PCI-MSI-edge      hda_intel
NMI:          0          0          0          0   Non-maskable interrupts
LOC:         88         72         46         20   Local timer interrupts
SPU:          0          0          0          0   Spurious interrupts
PMI:          0          0          0          0   Performance monitoring interrupts
IWI:          0          0          0          0   IRQ work interrupts
RES:     247193     223669      67550      21409   Rescheduling interrupts
CAL:       6946      10183      15860      14788   Function call interrupts
TLB:       5224       5057        918        685   TLB shootdowns
TRM:          0          0          0          0   Thermal event interrupts
THR:          0          0          0          0   Threshold APIC interrupts
MCE:          0          0          0          0   Machine check exceptions
MCP:          4          4          4          4   Machine check polls
ERR:          0
MIS:          0

```From the above, I can see that interrupts moved from 40,41 to 45,46. Is there a way that I can force hda_intel to use specific interrupt, like 46?

---

### Post by matt_symes on 2011-12-25
Hi

Have a read of this.

[http://kerneltrap.org/mailarchive/linux-netdev/2010/5/11/6276942](http://kerneltrap.org/mailarchive/linux-netdev/2010/5/11/6276942)

What driver do you have ?

You could try this one.

[http://sourceforge.net/projects/e1000/](http://sourceforge.net/projects/e1000/)

Kind regards

---

### Post by areq on 2011-12-25
I think the first link is broken somehow - i can't get to the page, it's loading forever without displaying the page. From the second site, I'll try newest stable e1000e driver (or should I try e1000 driver?).

---

### Post by matt_symes on 2011-12-25
Hi

I'm not sure what is going on with the first link. Sometimes it seems to work. The person in the post had the same problem as you. He patched the driver to fix it. He did mention that other distributions did not have the problem.

I'm not sure what to suggest as it's not a piece of hardware i own. I can only suggest experimenting. It does seem the problem could be with the driver.

Kind regards

---

### Post by areq on 2011-12-25
Unfortunately the newest e1000e driver is behaving the same :(. I'll check the first link tomorrow, maybe that will help...

---

### Post by matt_symes on 2011-12-25
Hi

Try a different distribution like Fedora or openSUSE and see if you get the same problem.

Use a USB stick. That would be my next move. If all distributions do it you may be out of luck. If it's only Ubuntu that fails then you need to look around for a patch.

Kind regards

---

### Post by areq on 2011-12-26
The conclusion from the link says that I need a bios update - impossible as I have the latest and no future versions will be released. I have tried installing fedora 16 and openSUSE 12.1 on the other hdd, but the problem remains the same. I think I'll start looking for a cheap network card on pci...

---

### Post by areq on 2012-01-26
Just wanted to say, that I've bought a new network card on** RTL8139D **chip, and everything works fine now. Thanks for helping me with this problem.

---

### Post by ngrieb on 2012-03-03
I have been having the same issue with 11.04 and multiple kernels for quite some time now. Same card, etc. I will try and see if any of the suggested links have any luck at fixing the problem.

Thanks.

---

