---
title: "bulit-in mic not working"
date: 2009-05-30
forum: Multimedia Software
---

### Post by bradturley2009 on 2009-05-30
I have my sound working although my top wound buttons don't work. it shows the graphic as if it was working but doesn't really do anything. that's not really my problem though. I can live with that one but I would really like to get my built-in mic to work. my webcam works fine also my mic port works. I am running amd64 bit version of ubunu. Ubuntu 9.04 - the Jaunty Jackalope

i put this into console (i saw it on another post)
 sudo lspci -nv

result:

00:00.0 0500: 10de:0547 (rev a2)
    Subsystem: 103c:30cf
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: [44] HyperTransport: Slave or Primary Interface
    Capabilities: [dc] HyperTransport: MSI Mapping Enable+ Fixed-

00:01.0 0601: 10de:0548 (rev a2)
    Subsystem: 103c:30cf
    Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 0c05: 10de:0542 (rev a2)
    Subsystem: 103c:30cf
    Flags: 66MHz, fast devsel, IRQ 10
    I/O ports at 3080 [size=64]
    I/O ports at 3040 [size=64]
    I/O ports at 3000 [size=64]
    Capabilities: [44] Power Management version 2

00:01.2 0500: 10de:0541 (rev a2)
    Subsystem: 103c:30cf
    Flags: 66MHz, fast devsel

00:01.3 0b40: 10de:0543 (rev a2)
    Subsystem: 103c:30cf
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
    Memory at f6200000 (32-bit, non-prefetchable) [size=512K]

00:02.0 0c03: 10de:055e (rev a2) (prog-if 10)
    Subsystem: 103c:30cf
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
    Memory at f6486000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: ohci_hcd

00:02.1 0c03: 10de:055f (rev a2) (prog-if 20)
    Subsystem: 103c:30cf
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at f6489000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [44] Debug port: BAR=1 offset=0098
    Capabilities: [80] Power Management version 2
    Kernel driver in use: ehci_hcd

00:04.0 0c03: 10de:055e (rev a2) (prog-if 10)
    Subsystem: 103c:30cf
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
    Memory at f6487000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: ohci_hcd

00:04.1 0c03: 10de:055f (rev a2) (prog-if 20)
    Subsystem: 103c:30cf
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at f6489400 (32-bit, non-prefetchable) [size=256]
    Capabilities: [44] Debug port: BAR=1 offset=0098
    Capabilities: [80] Power Management version 2
    Kernel driver in use: ehci_hcd

00:06.0 0101: 10de:0560 (rev a1) (prog-if 8a [Master SecP PriP])
    Subsystem: f03c:30cf
    Flags: bus master, 66MHz, fast devsel, latency 0
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    I/O ports at 30c0 [size=16]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: pata_amd

00:07.0 0403: 10de:055c (rev a1)
    Subsystem: 103c:30cf
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at f6480000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [44] Power Management version 2
    Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
    Capabilities: [6c] HyperTransport: MSI Mapping Enable+ Fixed+
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:08.0 0604: 10de:0561 (rev a2) (prog-if 01)
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
    Memory behind bridge: f6100000-f61fffff
    Capabilities: [b8] Subsystem: 10de:cb84
    Capabilities: [8c] HyperTransport: MSI Mapping Enable+ Fixed-

00:09.0 0101: 10de:0550 (rev a2) (prog-if 85 [Master SecO PriO])
    Subsystem: 103c:30cf
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 2301
    I/O ports at 30f0 [size=8]
    I/O ports at 30e4 [size=4]
    I/O ports at 30e8 [size=8]
    I/O ports at 30e0 [size=4]
    I/O ports at 30d0 [size=16]
    Memory at f6484000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: [44] Power Management version 2
    Capabilities: [8c] SATA HBA <?>
    Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/3 Enable+
    Capabilities: [cc] HyperTransport: MSI Mapping Enable+ Fixed+
    Kernel driver in use: ahci

00:0a.0 0200: 10de:054c (rev a2)
    Subsystem: 103c:30cf
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 2300
    Memory at f6488000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 30f8 [size=8]
    Memory at f6489c00 (32-bit, non-prefetchable) [size=256]
    Memory at f6489800 (32-bit, non-prefetchable) [size=16]
    Capabilities: [44] Power Management version 2
    Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/3 Enable+
    Capabilities: [6c] HyperTransport: MSI Mapping Enable+ Fixed+
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:0c.0 0604: 10de:0563 (rev a2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: f2000000-f3ffffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
    Capabilities: [40] Subsystem: 10de:0000
    Capabilities: [48] Power Management version 2
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
    Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
    Capabilities: [80] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:0d.0 0604: 10de:0563 (rev a2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: f6000000-f60fffff
    Capabilities: [40] Subsystem: 10de:0000
    Capabilities: [48] Power Management version 2
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
    Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
    Capabilities: [80] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:12.0 0300: 10de:0531 (rev a2)
    Subsystem: 103c:30cf
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
    Memory at f5000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at f4000000 (64-bit, non-prefetchable) [size=16M]
    [virtual] Expansion ROM at 88000000 [disabled] [size=128K]
    Capabilities: [48] Power Management version 2
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb

00:18.0 0600: 1022:1100
    Flags: fast devsel
    Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 0600: 1022:1101
    Flags: fast devsel

00:18.2 0600: 1022:1102
    Flags: fast devsel

00:18.3 0600: 1022:1103
    Flags: fast devsel
    Capabilities: [f0] Secure device <?>
    Kernel driver in use: k8temp
    Kernel modules: k8temp

02:05.0 0c00: 1180:0832 (rev 05) (prog-if 10)
    Subsystem: 103c:30cf
    Flags: bus master, medium devsel, latency 64, IRQ 5
    Memory at f6100000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [dc] Power Management version 2
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

02:05.1 0805: 1180:0822 (rev 22)
    Subsystem: 103c:30cf
    Flags: bus master, medium devsel, latency 64, IRQ 7
    Memory at f6100800 (32-bit, non-prefetchable) [size=256]
    Capabilities: [80] Power Management version 2
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

02:05.2 0880: 1180:0843 (rev 12)
    Subsystem: 103c:30cf
    Flags: bus master, medium devsel, latency 64, IRQ 11
    Memory at f6100c00 (32-bit, non-prefetchable) [size=256]
    Capabilities: [80] Power Management version 2
    Kernel driver in use: ricoh-mmc
    Kernel modules: ricoh_mmc

02:05.3 0880: 1180:0592 (rev 12)
    Subsystem: 103c:30cf
    Flags: bus master, medium devsel, latency 64, IRQ 11
    Memory at f6101000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [80] Power Management version 2

02:05.4 0880: 1180:0852 (rev ff) (prog-if ff)
    !!! Unknown header type 7f

03:00.0 0200: 168c:001c (rev 01)
    Subsystem: 103c:137a
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f6000000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 2
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Capabilities: [60] Express Legacy Endpoint, MSI 00
    Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Virtual Channel <?>
    Kernel driver in use: ath5k_pci
    Kernel modules: ath_pci, ath5k

---

