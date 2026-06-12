---
title: "Intel HDA Audio Problems"
date: 2008-10-12
forum: Multimedia Software
---

### Post by dococo on 2008-10-12
I would really appreciate any help getting my audio to work. I am using Intrepid on my compaq presario notebook and I have tried all the recommended solutions.

When I boot up I hear the drum roll but it seems to go into a 'fading loop'. I also hear error bleeps when I press the wrong key. But other than that, nothing which leads me to believe that I need different drivers.

I have installed Alsa 1.0.18rc3 to see if this will help but to no avail.

I have tried all the options I can find to update the /etc/modprobe.d/alsa-base i.e. options snd-hda-intel model=3stack and so on.

Below are listed the output from various commands that might shed some light on the matter.

Many thanks

------


cat /proc/asound/card0/codec#* | grep Codec 
Codec: IDT 92HD71B7X 
Codec: LSI ID 1040 
Codec: Generic 8086 ID 2802

cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.18rc3. 
Compiled on Oct 11 2008 for kernel 2.6.27-7-generic (SMP).

aplay -l 
**** List of PLAYBACK Hardware Devices **** 
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog] 
  Subdevices: 0/1 
  Subdevice #0: subdevice #0 

lspci -v 
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07) 
	Subsystem: Hewlett-Packard Company Device 30f7 
	Flags: bus master, fast devsel, latency 0 
	Capabilities: <access denied> 
	Kernel driver in use: agpgart-intel 
	Kernel modules: intel-agp 

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) 
	Subsystem: Hewlett-Packard Company Device 30f7 
	Flags: bus master, fast devsel, latency 0, IRQ 16 
	Memory at 90000000 (64-bit, non-prefetchable) [size=4M] 
	Memory at 80000000 (64-bit, prefetchable) [size=256M] 
	I/O ports at 8110 [size=8] 
	Capabilities: <access denied> 

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) 
	Subsystem: Hewlett-Packard Company Device 30f7 
	Flags: bus master, fast devsel, latency 0 
	Memory at 96500000 (64-bit, non-prefetchable) [size=1M] 
	Capabilities: <access denied> 

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) 
	Subsystem: Hewlett-Packard Company Device 30f7 
	Flags: bus master, medium devsel, latency 0, IRQ 16 
	I/O ports at 80e0 [size=32] 
	Capabilities: <access denied> 
	Kernel driver in use: uhci_hcd 
	Kernel modules: uhci-hcd 

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03) 
	Subsystem: Hewlett-Packard Company Device 30f7 
	Flags: bus master, medium devsel, latency 0, IRQ 17 
	I/O ports at 80c0 [size=32] 
	Capabilities: <access denied> 
	Kernel driver in use: uhci_hcd 
	Kernel modules: uhci-hcd 

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20) 
	Subsystem: Hewlett-Packard Company Device 30f7 
	Flags: bus master, medium devsel, latency 0, IRQ 18 
	Memory at 9c804c00 (32-bit, non-prefetchable) [size=1K] 
	Capabilities: <access denied> 
	Kernel driver in use: ehci_hcd 
	Kernel modules: ehci-hcd 

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03) 
	Subsystem: Hewlett-Packard Company Device 30f7 
	Flags: bus master, fast devsel, latency 0, IRQ 22 
	Memory at 9c800000 (64-bit, non-prefetchable) [size=16K] 
	Capabilities: <access denied> 
	Kernel driver in use: HDA Intel 
	Kernel modules: snd-hda-intel 

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03) 
	Flags: bus master, fast devsel, latency 0 
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0 
	I/O behind bridge: 00007000-00007fff 
	Memory behind bridge: 9b800000-9c7fffff 
	Prefetchable memory behind bridge: 0000000090400000-00000000913fffff 
	Capabilities: <access denied> 
	Kernel driver in use: pcieport-driver 
	Kernel modules: shpchp 

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03) 
	Flags: bus master, fast devsel, latency 0 
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0 
	I/O behind bridge: 00006000-00006fff 
	Memory behind bridge: 9a800000-9b7fffff 
	Prefetchable memory behind bridge: 0000000091400000-00000000923fffff 
	Capabilities: <access denied> 
	Kernel driver in use: pcieport-driver 
	Kernel modules: shpchp 

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03) 
	Flags: bus master, fast devsel, latency 0 
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0 
	I/O behind bridge: 00005000-00005fff 
	Memory behind bridge: 99700000-9a7fffff 
	Prefetchable memory behind bridge: 0000000092400000-00000000933fffff 
	Capabilities: <access denied> 
	Kernel driver in use: pcieport-driver 
	Kernel modules: shpchp 

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03) 
	Flags: bus master, fast devsel, latency 0 
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0 
	I/O behind bridge: 00003000-00004fff 
	Memory behind bridge: 98700000-996fffff 
	Prefetchable memory behind bridge: 0000000093400000-00000000944fffff 
	Capabilities: <access denied> 
	Kernel driver in use: pcieport-driver 
	Kernel modules: shpchp 

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03) 
	Flags: bus master, fast devsel, latency 0 
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0 
	I/O behind bridge: 00002000-00002fff 
	Memory behind bridge: 97600000-986fffff 
	Prefetchable memory behind bridge: 0000000094500000-00000000954fffff 
	Capabilities: <access denied> 
	Kernel driver in use: pcieport-driver 
	Kernel modules: shpchp 

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03) 
	Flags: bus master, fast devsel, latency 0 
	Bus: primary=00, secondary=06, subordinate=08, sec-latency=0 
	I/O behind bridge: 00001000-00001fff 
	Memory behind bridge: 96600000-975fffff 
	Prefetchable memory behind bridge: 0000000095500000-00000000964fffff 
	Capabilities: <access denied> 
	Kernel driver in use: pcieport-driver 
	Kernel modules: shpchp 

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03) 
	Subsystem: Hewlett-Packard Company Device 30f7 
	Flags: bus master, medium devsel, latency 0, IRQ 20 
	I/O ports at 80a0 [size=32] 
	Capabilities: <access denied> 
	Kernel driver in use: uhci_hcd 
	Kernel modules: uhci-hcd 

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03) 
	Subsystem: Hewlett-Packard Company Device 30f7 
	Flags: bus master, medium devsel, latency 0, IRQ 22 
	I/O ports at 8080 [size=32] 
	Capabilities: <access denied> 
	Kernel driver in use: uhci_hcd 
	Kernel modules: uhci-hcd 

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03) 
	Subsystem: Hewlett-Packard Company Device 30f7 
	Flags: bus master, medium devsel, latency 0, IRQ 18 
	I/O ports at 8060 [size=32] 
	Capabilities: <access denied> 
	Kernel driver in use: uhci_hcd 
	Kernel modules: uhci-hcd 

00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03) 
	Subsystem: Hewlett-Packard Company Device 30f7 
	Flags: bus master, medium devsel, latency 0, IRQ 19 
	I/O ports at 8040 [size=32] 
	Capabilities: <access denied> 
	Kernel driver in use: uhci_hcd 
	Kernel modules: uhci-hcd 

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20) 
	Subsystem: Hewlett-Packard Company Device 30f7 
	Flags: bus master, medium devsel, latency 0, IRQ 20 
	Memory at 9c804800 (32-bit, non-prefetchable) [size=1K] 
	Capabilities: <access denied> 
	Kernel driver in use: ehci_hcd 
	Kernel modules: ehci-hcd 

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01) 
	Flags: bus master, fast devsel, latency 0 
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=32 
	Capabilities: <access denied> 

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03) 
	Subsystem: Hewlett-Packard Company Device 30f7 
	Flags: bus master, medium devsel, latency 0 
	Capabilities: <access denied> 

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01) 
	Subsystem: Hewlett-Packard Company Device 30f7 
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 2297 
	I/O ports at 8108 [size=8] 
	I/O ports at 811c [size=4] 
	I/O ports at 8100 [size=8] 
	I/O ports at 8118 [size=4] 
	I/O ports at 8020 [size=32] 
	Memory at 9c804000 (32-bit, non-prefetchable) [size=2K] 
	Capabilities: <access denied> 
	Kernel driver in use: ahci 
	Kernel modules: ahci 

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03) 
	Subsystem: Hewlett-Packard Company Device 30f7 
	Flags: medium devsel, IRQ 11 
	Memory at 9c805000 (64-bit, non-prefetchable) [size=256] 
	I/O ports at 8000 [size=32] 
	Kernel modules: i2c-i801 

03:00.0 Network controller: Intel Corporation Device 4237 
	Subsystem: Intel Corporation Device 1211 
	Flags: bus master, fast devsel, latency 0, IRQ 2295 
	Memory at 99700000 (64-bit, non-prefetchable) [size=8K] 
	Capabilities: <access denied> 
	Kernel driver in use: iwlagn 
	Kernel modules: iwlagn 

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02) 
	Subsystem: Hewlett-Packard Company Device 30f7 
	Flags: bus master, fast devsel, latency 0, IRQ 2296 
	I/O ports at 3000 [size=256] 
	Memory at 93410000 (64-bit, prefetchable) [size=4K] 
	Memory at 93400000 (64-bit, prefetchable) [size=64K] 
	Expansion ROM at 93420000 [disabled] [size=128K] 
	Capabilities: <access denied> 
	Kernel driver in use: r8169 
	Kernel modules: r8169 

05:00.0 System peripheral: JMicron Technologies, Inc. Device 2382 
	Subsystem: Hewlett-Packard Company Device 30f7 
	Flags: bus master, fast devsel, latency 0, IRQ 16 
	Memory at 97600300 (32-bit, non-prefetchable) [size=256] 
	Capabilities: <access denied> 
	Kernel driver in use: sdhci-pci 
	Kernel modules: sdhci-pci 

05:00.2 SD Host controller: JMicron Technologies, Inc. Device 2381 (prog-if 01) 
	Subsystem: Hewlett-Packard Company Device 30f7 
	Flags: fast devsel, IRQ 16 
	Memory at 97600200 (32-bit, non-prefetchable) [size=256] 
	Capabilities: <access denied> 
	Kernel modules: sdhci-pci 

05:00.3 System peripheral: JMicron Technologies, Inc. Device 2383 
	Subsystem: Hewlett-Packard Company Device 30f7 
	Flags: bus master, fast devsel, latency 0, IRQ 11 
	Memory at 97600100 (32-bit, non-prefetchable) [size=256] 
	Capabilities: <access denied> 

05:00.4 System peripheral: JMicron Technologies, Inc. Device 2384 
	Subsystem: Hewlett-Packard Company Device 30f7 
	Flags: bus master, fast devsel, latency 0, IRQ 11 
	Memory at 97600000 (32-bit, non-prefetchable) [size=256] 
	Capabilities: <access denied>

---

### Post by odissefs on 2008-10-29
Hi,
I have the same problem on a HP pavilion dv7
and nearly same output;
 lspci -v 
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00008000-00008fff
	Memory behind bridge: d0000000-d2ffffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: [88] Subsystem: Hewlett-Packard Company Device 30f4
	Capabilities: [80] Power Management version 3
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [a0] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [140] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 90e0 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 90c0 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at df304c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCIe advanced features <?>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at df300000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00007000-00007fff
	Memory behind bridge: de200000-df2fffff
	Prefetchable memory behind bridge: 00000000d3000000-00000000d3ffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Hewlett-Packard Company Device 30f4
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: dd200000-de1fffff
	Prefetchable memory behind bridge: 00000000d4000000-00000000d4ffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Hewlett-Packard Company Device 30f4
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: dc200000-dd1fffff
	Prefetchable memory behind bridge: 00000000d5000000-00000000d5ffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Hewlett-Packard Company Device 30f4
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00003000-00004fff
	Memory behind bridge: db200000-dc1fffff
	Prefetchable memory behind bridge: 00000000d6000000-00000000d70fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Hewlett-Packard Company Device 30f4
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: da100000-db1fffff
	Prefetchable memory behind bridge: 00000000d7100000-00000000d80fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Hewlett-Packard Company Device 30f4
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=09, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: d9100000-da0fffff
	Prefetchable memory behind bridge: 00000000d8100000-00000000d90fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Hewlett-Packard Company Device 30f4
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 90a0 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at 9080 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 9060 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 9040 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at df304800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCIe advanced features <?>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=32
	Capabilities: [50] Subsystem: Hewlett-Packard Company Device 30f4

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 215
	I/O ports at 9108 [size=8]
	I/O ports at 9114 [size=4]
	I/O ports at 9100 [size=8]
	I/O ports at 9110 [size=4]
	I/O ports at 9020 [size=32]
	Memory at df304000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/4 Enable+
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] SATA HBA <?>
	Capabilities: [b0] PCIe advanced features <?>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: medium devsel, IRQ 11
	Memory at df305000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 9000 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GT (rev a1)
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d2000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d0000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 8000 [size=128]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [b4] Vendor Specific Information <?>
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [128] Power Budgeting <?>
	Capabilities: [600] Vendor Specific Information <?>
	Kernel driver in use: nvidia
	Kernel modules: nvidiafb, nvidia

02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
	Subsystem: Intel Corporation Device 1211
	Flags: bus master, fast devsel, latency 0, IRQ 214
	Memory at de200000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [e0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Device Serial Number f2-54-dd-ff-ff-ea-16-00
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: bus master, fast devsel, latency 0, IRQ 216
	I/O ports at 3000 [size=256]
	Memory at d6010000 (64-bit, prefetchable) [size=4K]
	Memory at d6000000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at d6020000 [disabled] [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [b0] MSI-X: Enable- Mask- TabSize=2
	Capabilities: [d0] Vital Product Data <?>
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
	Kernel driver in use: r8169
	Kernel modules: r8169

06:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at da100000 (32-bit, non-prefetchable) [size=2K]
	Memory at da100d00 (32-bit, non-prefetchable) [size=128]
	Memory at da100c80 (32-bit, non-prefetchable) [size=128]
	Memory at da100c00 (32-bit, non-prefetchable) [size=128]
	Capabilities: [44] Power Management version 3
	Capabilities: [80] Express Endpoint, MSI 00
	Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

06:00.1 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at da100b00 (32-bit, non-prefetchable) [size=256]
	Capabilities: [a4] Power Management version 3
	Capabilities: [80] Express Endpoint, MSI 00
	Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

06:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller (prog-if 01)
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: fast devsel, IRQ 16
	Memory at da100a00 (32-bit, non-prefetchable) [size=256]
	Capabilities: [a4] Power Management version 3
	Capabilities: [80] Express Endpoint, MSI 00
	Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Kernel modules: sdhci-pci

06:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at da100900 (32-bit, non-prefetchable) [size=256]
	Capabilities: [a4] Power Management version 3
	Capabilities: [80] Express Endpoint, MSI 00
	Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

06:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
	Subsystem: Hewlett-Packard Company Device 30f4
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at da100800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [a4] Power Management version 3
	Capabilities: [80] Express Endpoint, MSI 00
	Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
cat /proc/asound/card0/codec#* | grep Codec
Codec: IDT 92HD71B7X
Codec: Generic 10de ID 6


Anyone has a clue how to resolve this problem?
Regards

---

### Post by markbuntu on 2008-10-29
These might help:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

If you are having problems with headphone/speaker control with your HDA sound device you can try this thread:

[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

---

