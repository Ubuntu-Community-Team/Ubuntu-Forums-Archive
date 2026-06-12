---
title: "Problem installing EVDO card in Ubuntu 9.10..."
date: 2010-04-05
forum: Networking &amp; Wireless
---

### Post by sankarvichu on 2010-04-05
Hi friends, i am a newbie, i have loaded ubuntu 9.10 few days back. I am having problem in configuring my BSNL EVDO CDMA2000 modem(Micromax MMX 300c). Guided by some of the threads, i have followed the below mentioned steps..

          xxxxxxx@xxxxxxx:~$ sudo modprobe usbserial vendor=0x05c6 product=0x2001  
 [sudo] password for xxxxxxx: 



Then connected the modem and gave the comment


           xxxxxxx@xxxxxxx:~$ lsusb  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 002 Device 004: ID 05c6:2001 Qualcomm, Inc.  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 



then i edited the wvdial.conf(i dont understand the details provided in the threads in configuring .conf file)



           xxxxxxx@xxxxxxx:~$ sudo gedit /etc/wvdial.conf
 

     [Dialer Defaults]  
     Init1 = ATZ  
     Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0  
     Modem Type = Analog Modem  
     ISDN = 0  
     Phone = #777  
     Modem = /dev/ttys0
     Username = xxxxxxxx
     Password = xxxxxxxx  
     Baud = 460800  
     Stupid Mode = 1
 


after saving the above mentioned(not sure about the correctness) .conf file, tried to dial, the result is...



           xxxxxxx@xxxxxxx:~$ wvdial  
 --> WvDial: Internet dialer version 1.60  
 --> Cannot open /dev/ttys0: No such file or directory  
 --> Cannot open /dev/ttys0: No such file or directory  
 --> Cannot open /dev/ttys0: No such file or directory 



as guided in the thread i gave the command dmesg, i am copying the whole output, as i am not sure which part is helpful in finding the error, pls bear with me...


           [    0.189253] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold  
 [    0.189256] pci 0000:00:02.0: PME# disabled  
 [    0.189279] pci 0000:00:02.1: reg 10 32bit mmio: [0xd9ffec00-0xd9ffecff]  
 [    0.189305] pci 0000:00:02.1: supports D1 D2  
 [    0.189307] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold  
 [    0.189311] pci 0000:00:02.1: PME# disabled  
 [    0.189371] pci 0000:00:05.0: reg 10 32bit mmio: [0xd9ff8000-0xd9ffbfff]  
 [    0.189397] pci 0000:00:05.0: PME# supported from D3hot D3cold  
 [    0.189401] pci 0000:00:05.0: PME# disabled  
 [    0.189434] pci 0000:00:06.0: reg 20 io port: [0xffa0-0xffaf]  
 [    0.189470] pci 0000:00:07.0: reg 10 32bit mmio: [0xd9ffd000-0xd9ffdfff]  
 [    0.189474] pci 0000:00:07.0: reg 14 io port: [0xd480-0xd487]  
 [    0.189496] pci 0000:00:07.0: supports D1 D2  
 [    0.189499] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold  
 [    0.189503] pci 0000:00:07.0: PME# disabled  
 [    0.189525] pci 0000:00:08.0: reg 10 io port: [0xd400-0xd407]  
 [    0.189529] pci 0000:00:08.0: reg 14 io port: [0xd080-0xd083]  
 [    0.189533] pci 0000:00:08.0: reg 18 io port: [0xd000-0xd007]  
 [    0.189537] pci 0000:00:08.0: reg 1c io port: [0xcc00-0xcc03]  
 [    0.189541] pci 0000:00:08.0: reg 20 io port: [0xc880-0xc88f]  
 [    0.189546] pci 0000:00:08.0: reg 24 32bit mmio: [0xd9ffc000-0xd9ffcfff]  
 [    0.189594] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold  
 [    0.189597] pci 0000:00:09.0: PME# disabled  
 [    0.189629] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold  
 [    0.189632] pci 0000:00:0b.0: PME# disabled  
 [    0.189664] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold  
 [    0.189667] pci 0000:00:0c.0: PME# disabled  
 [    0.189781] pci 0000:01:06.0: reg 10 32bit mmio: [0xdb000000-0xdbffffff]  
 [    0.189837] pci 0000:01:06.1: reg 10 32bit mmio: [0xda000000-0xdaffffff]  
 [    0.189898] pci 0000:00:04.0: transparent bridge  
 [    0.189903] pci 0000:00:04.0: bridge 32bit mmio: [0xda000000-0xdbffffff]  
 [    0.189928] pci 0000:02:00.0: reg 10 32bit mmio: [0xdf000000-0xdfffffff]  
 [    0.189936] pci 0000:02:00.0: reg 14 64bit mmio: [0xc0000000-0xcfffffff]  
 [    0.189943] pci 0000:02:00.0: reg 1c 64bit mmio: [0xdc000000-0xddffffff]  
 [    0.189948] pci 0000:02:00.0: reg 24 io port: [0xec00-0xec7f]  
 [    0.189954] pci 0000:02:00.0: reg 30 32bit mmio: [0xdefe0000-0xdeffffff]  
 [    0.190007] pci 0000:00:09.0: bridge io port: [0xe000-0xefff]  
 [    0.190010] pci 0000:00:09.0: bridge 32bit mmio: [0xdc000000-0xdfffffff]  
 [    0.190014] pci 0000:00:09.0: bridge 64bit mmio pref: [0xc0000000-0xcfffffff]  
 [    0.190090] pci_bus 0000:00: on NUMA node 0  
 [    0.190095] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]  
 [    0.190271] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]  
 [    0.190358] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]  
 [    0.190417] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR11._PRT]  
 [    0.190477] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR12._PRT]  
 [    0.197046] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *11  
 [    0.197235] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.  
 [    0.197421] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.  
 [    0.197608] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.  
 [    0.197794] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *0, disabled.  
 [    0.197981] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.  
 [    0.198167] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.  
 [    0.198354] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *11  
 [    0.198544] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *11  
 [    0.198731] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *10  
 [    0.198917] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *11  
 [    0.199104] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *11  
 [    0.199290] ACPI: PCI Interrupt Link [LACI] (IRQs 20 21 22 23) *0, disabled.  
 [    0.199477] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *0, disabled.  
 [    0.199665] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *10  
 [    0.199851] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *0, disabled.  
 [    0.200045] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *15  
 [    0.200233] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *0, disabled.  
 [    0.200452] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.  
 [    0.200635] SCSI subsystem initialized  
 [    0.200684] libata version 3.00 loaded.  
 [    0.200684] usbcore: registered new interface driver usbfs  
 [    0.200684] usbcore: registered new interface driver hub  
 [    0.200684] usbcore: registered new device driver usb  
 [    0.200684] ACPI: WMI: Mapper loaded 
 [    0.200684] PCI: Using ACPI for IRQ routing  
 [    0.216008] Bluetooth: Core ver 2.15 
 [    0.216023] NET: Registered protocol family 31  
 [    0.216023] Bluetooth: HCI device and connection manager initialized  
 [    0.216023] Bluetooth: HCI socket layer initialized  
 [    0.216023] NetLabel: Initializing  
 [    0.216023] NetLabel:  domain hash size = 128  
 [    0.216023] NetLabel:  protocols = UNLABELED CIPSOv4  
 [    0.216037] NetLabel:  unlabeled traffic allowed by default  
 [    0.216068] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31  
 [    0.216074] hpet0: 3 comparators, 32-bit 25.000000 MHz counter  
 [    0.224022] Switched to high resolution mode on CPU 0  
 [    0.224570] Switched to high resolution mode on CPU 1  
 [    0.232019] pnp: PnP ACPI init  
 [    0.232038] ACPI: bus type pnp registered  
 [    0.235610] pnp 00:07: io resource (0x900-0x97f) overlaps 0000:00:01.0 BAR 0 (0x900-0x9ff), disabling  
 [    0.235614] pnp 00:07: io resource (0x980-0x9ff) overlaps 0000:00:01.0 BAR 0 (0x900-0x9ff), disabling  
 [    0.238781] pnp: PnP ACPI: found 16 devices  
 [    0.238783] ACPI: ACPI bus type pnp unregistered  
 [    0.238787] PnPBIOS: Disabled by ACPI PNP  
 [    0.238802] system 00:07: ioport range 0xa30-0xa37 has been reserved  
 [    0.238805] system 00:07: ioport range 0x4d0-0x4d1 has been reserved  
 [    0.238808] system 00:07: ioport range 0x800-0x80f has been reserved  
 [    0.238811] system 00:07: ioport range 0x500-0x57f has been reserved  
 [    0.238814] system 00:07: ioport range 0x580-0x5ff has been reserved  
 [    0.238818] system 00:07: ioport range 0x800-0x87f could not be reserved  
 [    0.238821] system 00:07: ioport range 0x880-0x8ff has been reserved  
 [    0.238824] system 00:07: ioport range 0xd00-0xd7f has been reserved  
 [    0.238827] system 00:07: ioport range 0xd80-0xdff has been reserved  
 [    0.238830] system 00:07: ioport range 0x2000-0x207f has been reserved  
 [    0.238834] system 00:07: ioport range 0x2080-0x20ff has been reserved  
 [    0.238838] system 00:07: iomem range 0xfefe0000-0xfefe01ff has been reserved  
 [    0.238841] system 00:07: iomem range 0xfefe1000-0xfefe1fff has been reserved  
 [    0.238844] system 00:07: iomem range 0xfee01000-0xfeefffff has been reserved  
 [    0.238848] system 00:07: iomem range 0xffb80000-0xffffffff has been reserved  
 [    0.238851] system 00:07: iomem range 0xff300000-0xff3fffff has been reserved  
 [    0.238858] system 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved  
 [    0.238861] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved  
 [    0.238867] system 00:0c: ioport range 0x230-0x23f has been reserved  
 [    0.238870] system 00:0c: ioport range 0x290-0x29f has been reserved  
 [    0.238877] system 00:0c: ioport range 0xa00-0xa0f has been reserved  
 [    0.238880] system 00:0c: ioport range 0xa10-0xa1f has been reserved  
 [    0.238886] system 00:0e: iomem range 0xe0000000-0xefffffff has been reserved  
 [    0.238892] system 00:0f: iomem range 0x0-0x9ffff could not be reserved  
 [    0.238895] system 00:0f: iomem range 0xc0000-0xcffff could not be reserved  
 [    0.238898] system 00:0f: iomem range 0xe0000-0xfffff could not be reserved  
 [    0.238901] system 00:0f: iomem range 0x100000-0xbfffffff could not be reserved  
 [    0.238905] system 00:0f: iomem range 0xff780000-0xffffffff could not be reserved  
 [    0.273587] AppArmor: AppArmor Filesystem Enabled  
 [    0.273618] pci 0000:00:04.0: PCI bridge, secondary bus 0000:01  
 [    0.273621] pci 0000:00:04.0:   IO window: disabled  
 [    0.273625] pci 0000:00:04.0:   MEM window: 0xda000000-0xdbffffff  
 [    0.273628] pci 0000:00:04.0:   PREFETCH window: disabled  
 [    0.273632] pci 0000:00:09.0: PCI bridge, secondary bus 0000:02  
 [    0.273635] pci 0000:00:09.0:   IO window: 0xe000-0xefff  
 [    0.273639] pci 0000:00:09.0:   MEM window: 0xdc000000-0xdfffffff  
 [    0.273642] pci 0000:00:09.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff  
 [    0.273646] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:03  
 [    0.273648] pci 0000:00:0b.0:   IO window: disabled  
 [    0.273651] pci 0000:00:0b.0:   MEM window: disabled  
 [    0.273654] pci 0000:00:0b.0:   PREFETCH window: disabled  
 [    0.273657] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04  
 [    0.273659] pci 0000:00:0c.0:   IO window: disabled  
 [    0.273662] pci 0000:00:0c.0:   MEM window: disabled  
 [    0.273664] pci 0000:00:0c.0:   PREFETCH window: disabled  
 [    0.273672] pci 0000:00:04.0: setting latency timer to 64  
 [    0.273678] pci 0000:00:09.0: setting latency timer to 64  
 [    0.273682] pci 0000:00:0b.0: setting latency timer to 64  
 [    0.273687] pci 0000:00:0c.0: setting latency timer to 64  
 [    0.273691] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]  
 [    0.273694] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]  
 [    0.273697] pci_bus 0000:01: resource 1 mem: [0xda000000-0xdbffffff]  
 [    0.273700] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]  
 [    0.273702] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffff]  
 [    0.273705] pci_bus 0000:02: resource 0 io:  [0xe000-0xefff]  
 [    0.273708] pci_bus 0000:02: resource 1 mem: [0xdc000000-0xdfffffff]  
 [    0.273711] pci_bus 0000:02: resource 2 pref mem [0xc0000000-0xcfffffff]  
 [    0.273750] NET: Registered protocol family 2  
 [    0.273844] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)  
 [    0.274177] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)  
 [    0.274901] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)  
 [    0.275269] TCP: Hash tables configured (established 131072 bind 65536)  
 [    0.275272] TCP reno registered  
 [    0.275368] NET: Registered protocol family 1  
 [    0.275440] Trying to unpack rootfs image as initramfs...  
 [    0.486345] Freeing initrd memory: 7725k freed  
 [    0.491667] cpufreq-nforce2: No nForce2 chipset.  
 [    0.491694] Scanning for low memory corruption every 60 seconds  
 [    0.491796] audit: initializing netlink socket (disabled)  
 [    0.491811] type=2000 audit(1270511015.488:1): initialized  
 [    0.500831] highmem bounce pool size: 64 pages  
 [    0.500837] HugeTLB registered 4 MB page size, pre-allocated 0 pages  
 [    0.502344] VFS: Disk quotas dquot_6.5.2  
 [    0.502406] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)  
 [    0.503023] fuse init (API version 7.12)  
 [    0.503105] msgmni has been set to 1679  
 [    0.503354] alg: No test for stdrng (krng)  
 [    0.503377] io scheduler noop registered  
 [    0.503379] io scheduler anticipatory registered  
 [    0.503381] io scheduler deadline registered  
 [    0.503423] io scheduler cfq registered (default)  
 [    0.927175] pci 0000:00:00.0: Found enabled HT MSI Mapping  
 [    0.927223] pci 0000:00:00.0: Found enabled HT MSI Mapping  
 [    0.927282] pci 0000:00:00.0: Found enabled HT MSI Mapping  
 [    0.927339] pci 0000:00:00.0: Found enabled HT MSI Mapping  
 [    0.927401] pci 0000:00:00.0: Found enabled HT MSI Mapping  
 [    0.927467] pci 0000:00:00.0: Found enabled HT MSI Mapping  
 [    0.927537] pci 0000:00:00.0: Found enabled HT MSI Mapping  
 [    0.927554] pci 0000:02:00.0: Boot video device  
 [    0.927647]   alloc irq_desc for 24 on node -1  
 [    0.927649]   alloc kstat_irqs on node -1  
 [    0.927658] pcieport-driver 0000:00:09.0: irq 24 for MSI/MSI-X  
 [    0.927663] pcieport-driver 0000:00:09.0: setting latency timer to 64  
 [    0.927729]   alloc irq_desc for 25 on node -1  
 [    0.927731]   alloc kstat_irqs on node -1  
 [    0.927735] pcieport-driver 0000:00:0b.0: irq 25 for MSI/MSI-X  
 [    0.927739] pcieport-driver 0000:00:0b.0: setting latency timer to 64  
 [    0.927803]   alloc irq_desc for 26 on node -1  
 [    0.927805]   alloc kstat_irqs on node -1  
 [    0.927809] pcieport-driver 0000:00:0c.0: irq 26 for MSI/MSI-X  
 [    0.927813] pcieport-driver 0000:00:0c.0: setting latency timer to 64  
 [    0.927872] pci_hotplug: PCI Hot Plug PCI Core version: 0.5  
 [    0.927897] pciehp: PCI Express Hot Plug Controller Driver version: 0.4  
 [    0.928040] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0  
 [    0.928044] ACPI: Power Button [PWRF]  
 [    0.928101] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1  
 [    0.928108] ACPI: Power Button [PWRB]  
 [    0.928361] processor LNXCPU:00: registered as cooling_device0  
 [    0.928393] processor LNXCPU:01: registered as cooling_device1  
 [    0.932040] isapnp: Scanning for PnP cards...  
 [    1.285588] isapnp: No Plug & Play device found  
 [    1.286803] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled  
 [    1.286905] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A  
 [    1.287230] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A  
 [    1.288267] brd: module loaded  
 [    1.288730] loop: module loaded  
 [    1.288807] input: Macintosh mouse button emulation as /devices/virtual/input/input2  
 [    1.289025] sata_nv 0000:00:08.0: version 3.5  
 [    1.289329] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23  
 [    1.289335]   alloc irq_desc for 23 on node -1  
 [    1.289337]   alloc kstat_irqs on node -1  
 [    1.289347] sata_nv 0000:00:08.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23  
 [    1.289391] sata_nv 0000:00:08.0: setting latency timer to 64  
 [    1.289489] scsi0 : sata_nv  
 [    1.289596] scsi1 : sata_nv  
 [    1.289732] ata1: SATA max UDMA/133 cmd 0xd400 ctl 0xd080 bmdma 0xc880 irq 23  
 [    1.289735] ata2: SATA max UDMA/133 cmd 0xd000 ctl 0xcc00 bmdma 0xc888 irq 23  
 [    1.289825] pata_amd 0000:00:06.0: version 0.4.1  
 [    1.289863] pata_amd 0000:00:06.0: setting latency timer to 64  
 [    1.289940] scsi2 : pata_amd  
 [    1.290004] scsi3 : pata_amd  
 [    1.290566] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14  
 [    1.290569] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15  
 [    1.291287] Fixed MDIO Bus: probed  
 [    1.291322] PPP generic driver version 2.4.2  
 [    1.291430] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver  
 [    1.291721] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 22  
 [    1.291725]   alloc irq_desc for 22 on node -1  
 [    1.291727]   alloc kstat_irqs on node -1  
 [    1.291736] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUB2] -> GSI 22 (level, low) -> IRQ 22  
 [    1.291746] ehci_hcd 0000:00:02.1: setting latency timer to 64  
 [    1.291750] ehci_hcd 0000:00:02.1: EHCI Host Controller  
 [    1.291806] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1  
 [    1.291837] ehci_hcd 0000:00:02.1: debug port 1  
 [    1.291842] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported  
 [    1.291860] ehci_hcd 0000:00:02.1: irq 22, io mem 0xd9ffec00  
 [    1.300012] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00  
 [    1.300091] usb usb1: configuration #1 chosen from 1 choice  
 [    1.300121] hub 1-0:1.0: USB hub found  
 [    1.300131] hub 1-0:1.0: 8 ports detected  
 [    1.300195] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver  
 [    1.300477] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 21  
 [    1.300480]   alloc irq_desc for 21 on node -1  
 [    1.300482]   alloc kstat_irqs on node -1  
 [    1.300490] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUB0] -> GSI 21 (level, low) -> IRQ 21  
 [    1.300498] ohci_hcd 0000:00:02.0: setting latency timer to 64  
 [    1.300501] ohci_hcd 0000:00:02.0: OHCI Host Controller  
 [    1.300533] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2  
 [    1.300557] ohci_hcd 0000:00:02.0: irq 21, io mem 0xd9fff000  
 [    1.358054] usb usb2: configuration #1 chosen from 1 choice  
 [    1.358079] hub 2-0:1.0: USB hub found  
 [    1.358087] hub 2-0:1.0: 8 ports detected  
 [    1.358146] uhci_hcd: USB Universal Host Controller Interface driver  
 [    1.358234] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12  
 [    1.358602] serio: i8042 KBD port at 0x60,0x64 irq 1  
 [    1.358608] serio: i8042 AUX port at 0x60,0x64 irq 12  
 [    1.358691] mice: PS/2 mouse device common for all mice  
 [    1.358787] rtc_cmos 00:02: RTC can wake from S4  
 [    1.358824] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0  
 [    1.358862] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs  
 [    1.358996] device-mapper: uevent: version 1.0.3  
 [    1.359103] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]  
 [    1.359206] device-mapper: multipath: version 1.1.0 loaded  
 [    1.359208] device-mapper: multipath round-robin: version 1.0.0 loaded  
 [    1.359363] EISA: Probing bus 0 at eisa.0  
 [    1.359371] Cannot allocate resource for EISA slot 2  
 [    1.359388] EISA: Detected 0 cards.  
 [    1.359504] cpuidle: using governor ladder  
 [    1.359506] cpuidle: using governor menu  
 [    1.359993] TCP cubic registered  
 [    1.360161] NET: Registered protocol family 10  
 [    1.360591] lo: Disabled Privacy Extensions  
 [    1.360894] NET: Registered protocol family 17  
 [    1.360912] Bluetooth: L2CAP ver 2.13  
 [    1.360914] Bluetooth: L2CAP socket layer initialized  
 [    1.360917] Bluetooth: SCO (Voice Link) ver 0.6  
 [    1.360919] Bluetooth: SCO socket layer initialized  
 [    1.360958] Bluetooth: RFCOMM TTY layer initialized  
 [    1.360962] Bluetooth: RFCOMM socket layer initialized  
 [    1.360964] Bluetooth: RFCOMM ver 1.11  
 [    1.360992] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ processors (2 cpu cores) (version 2.20.00)  
 [    1.361017] [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found.  
 [    1.361018] [Firmware Bug]: powernow-k8: Try again with latest BIOS.  
 [    1.361037] Using IPI No-Shortcut mode  
 [    1.361098] PM: Resume from disk failed.  
 [    1.361110] registered taskstats version 1  
 [    1.361231]   Magic number: 6:487:756  
 [    1.361331] rtc_cmos 00:02: setting system clock to 2010-04-05 23:43:37 UTC (1270511017)  
 [    1.361335] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found  
 [    1.361337] EDD information not available.  
 [    1.376434] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3  
 [    1.444039] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)  
 [    1.452308] ata1.00: ATA-8: ST3500418AS, CC38, max UDMA/133  
 [    1.452311] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)  
 [    1.468301] ata1.00: configured for UDMA/133  
 [    1.468418] scsi 0:0:0:0: Direct-Access     ATA      ST3500418AS      CC38 PQ: 0 ANSI: 5  
 [    1.468538] sd 0:0:0:0: Attached scsi generic sg0 type 0  
 [    1.468576] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)  
 [    1.468620] sd 0:0:0:0: [sda] Write Protect is off  
 [    1.468623] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00  
 [    1.468646] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA  
 [    1.468774]  sda:  
 [    1.515579] ldm_parse_tocblock(): Cannot find TOCBLOCK, database may be corrupt.  
 [    1.515583] ldm_parse_tocblock(): Cannot find TOCBLOCK, database may be corrupt.  
 [    1.533222]  [LDM] sda1 sda2 sda3 sda4 sda5  
 [    1.533763] sd 0:0:0:0: [sda] Attached SCSI disk  
 [    1.624034] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)  
 [    1.632118] ata2.00: ATAPI: HL-DT-STDVD-RAM GH22NS30, 1.01, max UDMA/100  
 [    1.649128] ata2.00: configured for UDMA/100  
 [    1.651264] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GH22NS30 1.01 PQ: 0 ANSI: 5  
 [    1.652916] sr0: scsi3-mmc drive: 125x/48x writer dvd-ram cd/rw xa/form2 cdda tray  
 [    1.652919] Uniform CD-ROM driver Revision: 3.20  
 [    1.652994] sr 1:0:0:0: Attached scsi CD-ROM sr0  
 [    1.653050] sr 1:0:0:0: Attached scsi generic sg1 type 5  
 [    1.653089] ata4: port disabled. ignoring.  
 [    1.653112] Freeing unused kernel memory: 540k freed  
 [    1.653521] Write protecting the kernel text: 4568k  
 [    1.653558] Write protecting the kernel read-only data: 1836k  
 [    1.782453] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.  
 [    1.782782] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20  
 [    1.782788]   alloc irq_desc for 20 on node -1  
 [    1.782790]   alloc kstat_irqs on node -1  
 [    1.782801] forcedeth 0000:00:07.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, low) -> IRQ 20  
 [    1.782806] forcedeth 0000:00:07.0: setting latency timer to 64  
 [    1.820962] Floppy drive(s): fd0 is 1.44M  
 [    1.851500] FDC 0 is a post-1991 82077  
 [    1.917024] usb 2-1: new full speed USB device using ohci_hcd and address 2  
 [    2.133112] usb 2-1: configuration #1 chosen from 1 choice  
 [    2.154619] Initializing USB Mass Storage driver...  
 [    2.154862] scsi4 : SCSI emulation for USB Mass Storage devices  
 [    2.154965] usb-storage: device found at 2  
 [    2.154968] usb-storage: waiting for device to settle before scanning  
 [    2.154975] usbcore: registered new interface driver usb-storage  
 [    2.154979] USB Mass Storage support registered.  
 [    2.300822] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x1374 @ 1, addr 00:1b:fc:ac:c3:fc  
 [    2.300826] forcedeth 0000:00:07.0: highdma pwrctl mgmt gbit lnktim msi desc-v3  
 [    3.568364] EXT4-fs (loop0): barriers enabled  
 [    3.589070] kjournald2 starting: pid 409, dev loop0:8, commit interval 5 seconds  
 [    3.589086] EXT4-fs (loop0): delayed allocation enabled  
 [    3.589090] EXT4-fs: file extents enabled  
 [    3.590910] EXT4-fs: mballoc enabled 
 [    3.590927] EXT4-fs (loop0): mounted filesystem with ordered data mode  
 [    4.046627] type=1505 audit(1270511020.183:2): operation="profile_load" pid=433 name=/usr/share/gdm/guest-session/Xsession  
 [    4.048608] type=1505 audit(1270511020.183:3): operation="profile_load" pid=434 name=/sbin/dhclient3  
 [    4.048892] type=1505 audit(1270511020.183:4): operation="profile_load" pid=434 name=/usr/lib/NetworkManager/nm-dhcp-client.action  
 [    4.049052] type=1505 audit(1270511020.187:5): operation="profile_load" pid=434 name=/usr/lib/connman/scripts/dhclient-script  
 [    4.082129] type=1505 audit(1270511020.218:6): operation="profile_load" pid=435 name=/usr/bin/evince  
 [    4.086655] type=1505 audit(1270511020.222:7): operation="profile_load" pid=435 name=/usr/bin/evince-previewer  
 [    4.089361] type=1505 audit(1270511020.226:8): operation="profile_load" pid=435 name=/usr/bin/evince-thumbnailer  
 [    4.103703] type=1505 audit(1270511020.238:9): operation="profile_load" pid=437 name=/usr/lib/cups/backend/cups-pdf  
 [    4.104057] type=1505 audit(1270511020.242:10): operation="profile_load" pid=437 name=/usr/sbin/cupsd  
 [    4.946831] udev: starting version 147  
 [    5.259155] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141  
 [    5.314449] lp: driver loaded but no devices found  
 [    5.316418] parport_pc 00:06: reported by Plug and Play ACPI  
 [    5.316464] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]  
 [    5.339777] ppdev: user-space parallel port driver  
 [    5.353662] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x600  
 [    5.353681] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x700  
 [    5.412194] lp0: using parport0 (interrupt-driven).  
 [    5.430282] Linux video capture interface: v2.00  
 [    5.466438] psmouse serio1: ID: 10 00 64  
 [    5.486698] ip_tables: (C) 2000-2006 Netfilter Core Team  
 [    5.652670] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded  
 [    5.653011] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 19  
 [    5.653017]   alloc irq_desc for 19 on node -1  
 [    5.653019]   alloc kstat_irqs on node -1  
 [    5.653030] cx8800 0000:01:06.0: PCI INT A -> Link[LNKA] -> GSI 19 (level, low) -> IRQ 19  
 [    5.653554] cx88[0]: subsystem: 1554:4976, board: Prolink Pixelview Global Extreme [card=74,autodetected], frontend(s): 0  
 [    5.653557] cx88[0]: TV tuner type 71, Radio tuner type 0  
 [    5.666713] cx2388x alsa driver version 0.0.7 loaded  
 [    5.865064] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 23  
 [    5.865071] HDA Intel 0000:00:05.0: PCI INT B -> Link[LAZA] -> GSI 23 (level, low) -> IRQ 23  
 [    5.865095] HDA Intel 0000:00:05.0: setting latency timer to 64  
 [    5.892100] tuner 2-0061: chip found @ 0xc2 (cx88[0])  
 [    5.938137] xc2028 2-0061: creating new instance  
 [    5.938141] xc2028 2-0061: type set to XCeive xc2028/xc3028 tuner  
 [    5.938145] cx88[0]: Asking xc2028/3028 to load firmware xc3028-v27.fw  
 [    5.952093] input: cx88 IR (Prolink Pixelview Glob as /devices/pci0000:00/0000:00:04.0/0000:01:06.0/input/input4  
 [    5.952148] cx88[0]/0: found at 0000:01:06.0, rev: 5, irq: 19, latency: 64, mmio: 0xdb000000  
 [    5.952161] IRQ 19/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs  
 [    5.952218] cx88[0]/0: registered device video0 [v4l2]  
 [    5.952241] cx88[0]/0: registered device vbi0  
 [    5.952264] cx88[0]/0: registered device radio0  
 [    5.952332] cx8800 0000:01:06.0: firmware: requesting xc3028-v27.fw  
 [    6.069567] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5  
 [    6.122242] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.  
 [    6.122367] cx88_audio 0000:01:06.1: PCI INT A -> Link[LNKA] -> GSI 19 (level, low) -> IRQ 19  
 [    6.122379] IRQ 19/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs  
 [    6.122400] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards  
 [    6.215290] xc2028 2-0061: Error on line 1135: -6  
 [    6.215712] cx8800 0000:01:06.0: firmware: requesting xc3028-v27.fw  
 [    6.221640] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.  
 [    6.222439] xc2028 2-0061: Error on line 1135: -6  
 [    6.453106] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:05.0/input/input6  
 [    7.154087] usb-storage: device scan complete  
 [    7.161060] scsi 4:0:0:0: Direct-Access     CDMA2000 Modem            2.31 PQ: 0 ANSI: 2  
 [    7.161493] sd 4:0:0:0: Attached scsi generic sg2 type 0  
 [    7.183045] sd 4:0:0:0: [sdb] Attached SCSI removable disk  
 [   14.385768] Adding 262136k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:262136k  
 [   14.437084] EXT4-fs (loop0): internal journal on loop0:8  
 [   14.765335]   alloc irq_desc for 27 on node -1  
 [   14.765339]   alloc kstat_irqs on node -1  
 [   14.765350] forcedeth 0000:00:07.0: irq 27 for MSI/MSI-X  
 [   14.765537] eth0: no link during initialization.  
 [   14.766023] ADDRCONF(NETDEV_UP): eth0: link is not ready  
 [   14.776789] __ratelimit: 3 callbacks suppressed  
 [   14.776793] type=1505 audit(1270525430.914:12): operation="profile_replace" pid=952 name=/usr/share/gdm/guest-session/Xsession  
 [   14.778557] type=1505 audit(1270525430.914:13): operation="profile_replace" pid=953 name=/sbin/dhclient3  
 [   14.778842] type=1505 audit(1270525430.914:14): operation="profile_replace" pid=953 name=/usr/lib/NetworkManager/nm-dhcp-client.action  
 [   14.779004] type=1505 audit(1270525430.914:15): operation="profile_replace" pid=953 name=/usr/lib/connman/scripts/dhclient-script  
 [   14.783301] type=1505 audit(1270525430.918:16): operation="profile_replace" pid=954 name=/usr/bin/evince  
 [   14.787935] type=1505 audit(1270525430.922:17): operation="profile_replace" pid=954 name=/usr/bin/evince-previewer  
 [   14.790660] type=1505 audit(1270525430.926:18): operation="profile_replace" pid=954 name=/usr/bin/evince-thumbnailer  
 [   14.801455] type=1505 audit(1270525430.938:19): operation="profile_replace" pid=958 name=/usr/lib/cups/backend/cups-pdf  
 [   14.801807] type=1505 audit(1270525430.938:20): operation="profile_replace" pid=958 name=/usr/sbin/cupsd  
 [   14.803733] type=1505 audit(1270525430.938:21): operation="profile_replace" pid=959 name=/usr/sbin/tcpdump  
 [   15.306001] cx8800 0000:01:06.0: firmware: requesting xc3028-v27.fw  
 [   15.321478] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.  
 [   15.323036] xc2028 2-0061: Error on line 1135: -6  
 [   29.090973] UDF-fs: No VRS found  
 [   29.090978] UDF-fs: No partition found (1)  
 [   29.153037] ISO 9660 Extensions: Microsoft Joliet Level 3  
 [   29.153780] ISOFS: changing to secondary root  
 [  110.214326] usb 2-1: USB disconnect, address 2  
 [  116.009014] usb 2-1: new full speed USB device using ohci_hcd and address 3  
 [  116.224121] usb 2-1: configuration #1 chosen from 1 choice  
 [  116.232476] scsi5 : SCSI emulation for USB Mass Storage devices  
 [  116.233846] usb-storage: device found at 3  
 [  116.233850] usb-storage: waiting for device to settle before scanning  
 [  119.623716] usb 2-1: USB disconnect, address 3  
 [  152.665956] usbcore: registered new interface driver usbserial  
 [  152.665973] USB Serial support registered for generic  
 [  152.665990] usbcore: registered new interface driver usbserial_generic  
 [  152.665993] usbserial: USB Serial Driver core  
 [  178.221014] usb 2-1: new full speed USB device using ohci_hcd and address 4  
 [  178.436121] usb 2-1: configuration #1 chosen from 1 choice  
 [  178.444391] scsi6 : SCSI emulation for USB Mass Storage devices  
 [  178.445841] usb-storage: device found at 4  
 [  178.445846] usb-storage: waiting for device to settle before scanning  
 [  183.446085] usb-storage: device scan complete  
 [  183.453076] scsi 6:0:0:0: CD-ROM            CDMA2000 Modem            2.31 PQ: 0 ANSI: 2  
 [  183.481048] sr1: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray  
 [  183.481183] sr 6:0:0:0: Attached scsi CD-ROM sr1  
 [  183.481257] sr 6:0:0:0: Attached scsi generic sg2 type 5  
 [  183.583034] sr 6:0:0:0: ioctl_internal_command return code = 8000002  
 [  183.583039]    : Sense Key : No Sense [current]  
 [  183.583043]    : Add. Sense: No additional sense information  
 [  183.600033] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00  
 [  183.600044] sr: Sense Key : No Sense [current]  
 [  183.600047] sr: Add. Sense: No additional sense information  
 [  183.825035] sr 6:0:0:0: ioctl_internal_command return code = 8000002  
 [  183.825039]    : Sense Key : No Sense [current]  
 [  183.825043]    : Add. Sense: No additional sense information  
 [  183.842033] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00  
 [  183.842043] sr: Sense Key : No Sense [current]  
 [  183.842046] sr: Add. Sense: No additional sense information  
 [  184.077035] sr 6:0:0:0: ioctl_internal_command return code = 8000002  
 [  184.077040]    : Sense Key : No Sense [current]  
 [  184.077044]    : Add. Sense: No additional sense information  
 [  184.101030] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00  
 [  184.101040] sr: Sense Key : No Sense [current]  
 [  184.101044] sr: Add. Sense: No additional sense information  
 [  184.191035] sr 6:0:0:0: ioctl_internal_command return code = 8000002  
 [  184.191039]    : Sense Key : No Sense [current]  
 [  184.191043]    : Add. Sense: No additional sense information  
 [  184.225032] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00  
 [  184.225042] sr: Sense Key : No Sense [current]  
 [  184.225046] sr: Add. Sense: No additional sense information  
 [  184.249031] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 28 00 00 00 00 10 00  
 [  184.249040] sr: Sense Key : No Sense [current]  
 [  184.249043] sr: Add. Sense: No additional sense information  
 [  184.283031] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 20 00 00 00 00 18 00  
 [  184.283039] sr: Sense Key : No Sense [current]  
 [  184.283043] sr: Add. Sense: No additional sense information  
 [  244.993018] usb 2-1: reset full speed USB device using ohci_hcd and address 4  
 [  245.241032] sr 6:0:0:0: ioctl_internal_command return code = 8000002  
 [  245.241036]    : Sense Key : No Sense [current]  
 [  245.241041]    : Add. Sense: No additional sense information  
 [  245.258031] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00  
 [  245.258041] sr: Sense Key : No Sense [current]  
 [  245.258044] sr: Add. Sense: No additional sense information  
 [  245.282034] ISO 9660 Extensions: Microsoft Joliet Level 3  
 [  245.311041] sr 6:0:0:0: ioctl_internal_command return code = 8000002  
 [  245.311046]    : Sense Key : No Sense [current]  
 [  245.311050]    : Add. Sense: No additional sense information  
 [  245.319044] ISOFS: changing to secondary root  
 [  245.336035] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00  
 [  245.336046] sr: Sense Key : No Sense [current]  
 [  245.336049] sr: Add. Sense: No additional sense information  
 [  245.572037] sr 6:0:0:0: ioctl_internal_command return code = 8000002  
 [  245.572042]    : Sense Key : No Sense [current]  
 [  245.572046]    : Add. Sense: No additional sense information  
 [  245.606034] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00  
 [  245.606044] sr: Sense Key : No Sense [current]  
 [  245.606047] sr: Add. Sense: No additional sense information  
 [  245.991066] sr 6:0:0:0: ioctl_internal_command return code = 8000002  
 [  245.991071]    : Sense Key : No Sense [current]  
 [  245.991075]    : Add. Sense: No additional sense information  
 [  246.021049] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00  
 [  246.021063] sr: Sense Key : No Sense [current]  
 [  246.021067] sr: Add. Sense: No additional sense information  
 [  246.119045] sr 6:0:0:0: ioctl_internal_command return code = 8000002  
 [  246.119049]    : Sense Key : No Sense [current]  
 [  246.119053]    : Add. Sense: No additional sense information  
 [  246.136054] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00  
 [  246.136068] sr: Sense Key : No Sense [current]  
 [  246.136072] sr: Add. Sense: No additional sense information  
 [  306.373025] usb 2-1: reset full speed USB device using ohci_hcd and address 4  
 xxxxxxx@xxxxxxx:~$  
 

Pls help me to connect to internet...

---

### Post by sankarvichu on 2010-04-05
anybody there... pls help me...

---

### Post by pdc on 2010-04-05
all these devices are likely seen as virtual CD-ROM devices by a linux computer, as they are loaded with windows software;

so one needs to "flip" them; or change their identify; so linux sees the modem bit of them;

yours will be the same; so to "flip":

several ways:
1) if the device gives an icon, right-click and "eject" if you use lsusb again, it should have changed to 1e0e:ce16

2) however you are probably going to need usb_modeswitch

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)
       
to download the .deb version of 1.1.1 which they recommend

go here

[http://packages.debian.org/search?keywords=usb-modeswitch](http://packages.debian.org/search?keywords=usb-modeswitch)           ....... so you choose the version for your processor ... 


feel fine about the phrase "unstable": means it is cutting-edge

and the entry for your device seems to be

> # D-Link DWM-162-U5
#
# Contributor: Zhang Le

;DefaultVendor=  0x05c6
;DefaultProduct= 0x2001

;TargetVendor=   0x1e0e
;TargetProduct=  0xce16

;MessageContent="55534243e0c26a85000000000000061b000000020000000000000000000000"


so ....... its ID after flipping should be 

 ... > 1e0e:ce16  .........

here is a thread 

[http://www.sifoo.net/v2/?p=146](http://www.sifoo.net/v2/?p=146)

describing success with similar devices to yours: you can see they did the crucial step of installing usb_modeswitch: the advantage of the latest version  (1.1.1) is that it automates the configuration; unlike earlier editions, which they describe in the above post !! so the above post is just a general read ..... grasp the ideas stuff .........

let us know how it gets along

---

### Post by alexfish on 2010-04-05
hi

try to find which ports the modem is using, also to see if any drivers are allocated

from the terminal type or copy these commands and post the results

Code:

dmesg | grep -e "modem" -e "tty" 

this will give a message like the one below yours may be different as my modem is a zte  the basic are the same



[    0.000000] console [tty0] enabled
[    0.267111] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.267383] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.422052] tty tty28: hash matches
[   20.545041] USB Serial support registered for GSM modem (1-port)
[   20.545073] option 1-9:1.0: GSM modem (1-port) converter detected
[   20.545160] usb 1-9: GSM modem (1-port) converter now attached to [COLOR=Blue]ttyUSB0[/COLOR]
[   20.545177] option 1-9:1.1: GSM modem (1-port) converter detected
[   20.545224] usb 1-9: GSM modem (1-port) converter now attached to [COLOR=Blue]ttyUSB1[/COLOR]
[   20.545244] option 1-9:1.3: GSM modem (1-port) converter detected
[   20.545300] usb 1-9: GSM modem (1-port) converter now attached to [COLOR=Blue]ttyUSB2[/COLOR]
[   20.545320] option: v0.7.2:USB Driver for GSM modems


I have highlighted the tty ports in blue

as you can see there are three ports/lines been  use by this modem if using wvdial then we would work through ttyUSB0  through to ttyUSB2

so the wvdial config file should have an entry like

[FONT=monospace][FONT=monospace]Modem = /dev/ttyUSB0

or try others if the wvdial fails

also you may need to check permissions if you want to use wvdial as a user, you can use wvdial in superusermode by using the sudo command although this is not a recommended way

also check out this site

[http://www.pcurtis.com/ubuntu-mobile.htm](http://www.pcurtis.com/ubuntu-mobile.htm)

regards

alexfish


just noticed pdc post, hi pdc ... added if the device is successfully flipped  or with the usb modeswich as suggested by pdc then try to configure the connection with the network manager
[/FONT][/FONT]

---

### Post by sonu 1807 on 2010-04-05
In 

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
Phone = #777
Modem = /dev/ttys0
Username = xxxxxxxx
Password = xxxxxxxx
Baud = 460800
Stupid Mode = 1


Change to 
Modem = /dev/ttyUSB0

Hope it helps!

---

### Post by sankarvichu on 2010-04-07
thanks pdc for replying and sorry for delayed response as the links are bit lengthy but very informative and also not straight for me a novice in ubundu... anyway, i did to the extend i understud... 

the jest of what i did and system was...

downloaded deb modeswitch and installed...
then

sankar@ubuntu:~$ sudo gedit /etc/usb_modeswitch.conf 
[sudo] password for sankar: 

in the window, copied the below data as said

# D-Link DWM-162-U5
 #
 # Contributor: Zhang Le
 
 DefaultVendor=  0x05c6
 DefaultProduct= 0x2001
 
 TargetVendor=   0x1e0e
 TargetProduct=  0xce16
 
 MessageContent="55534243e0c26a85000000000000061b000000020000000000000000000000"
 
sankar@ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 1e0e:cefe  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

sankar@ubuntu:~$ sudo gedit /etc/wvdial.conf

copied the below details in the window as said (bsnl phone = #777) 

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
ISDN = 0
Phone = #777
Modem = /dev/ttyUSB0
New PPPD = yes
Baud = 912600
Idle Seconds = 0
Auto Reconnect = 1
Auto DNS = 1
Stupid Mode = 1
Compuserve = 0
Dial Command = ATD
Ask Password = 0
FlowControl = NOFLOW
Username = xxxxxx
Password = xxxxxx

sankar@ubuntu:~$ sudo gedit /usr/sbin/initmodem.sh

in the window, copied the below details

#!/bin/sh
sudo usb_modeswitch
sleep 10
sudo modprobe usbserial vendor=0x1e0e product=0xce16

then

[COLOR=Red]sankar@ubuntu:~$ sudo /usr/sbin/initmodem.sh[/COLOR]

[COLOR=Red]Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 No devices in default mode or class found. Nothing to do. Bye.[/COLOR]

then i tried wvdial

sankar@ubuntu:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> [COLOR=Red]Modem not responding.[/COLOR]
sankar@ubuntu:~$ 

i dont know what went wrong...

before modeswitch, the command used to display "Bus 002 Device 004: ID 05c6:2001 Qualcomm, Inc. " for command "lsusb" now it is showing "Bus 002 Device 002: ID 1e0e:cefe"...

pls help me connect to internet... anyway thanks in advance..

---

### Post by sankarvichu on 2010-04-07
sorry deleted the erronious double post

---

### Post by dineshs on 2010-04-08
Can you install gnome-ppp ? 
In its setup click detect (Device) to detect modem automatically.
Give username , password and tel no then proceed
ref:[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)

---

### Post by pdc on 2010-04-08
you are welcome to follow dinesh' advice;

as I understand it though, gnome-ppp is a front-end for wvdial; which ain't working so far ........

after running usb_modeswitch, 

lsusb seemed to say 

> 1e0e:cefe  ????

whereas we thought it might say 

> 0xce16

I think you need to flip this modem; 

I think you need to join the usb_modeswitch forum and ask their advice; josh runs the programme, and answers a lot 

[http://www.draisberghof.de/usb_modeswitch/bb/](http://www.draisberghof.de/usb_modeswitch/bb/)

join up; seek help; come back and tell us what you learned

---

### Post by alexfish on 2010-04-08
Hi all

if the integrated usb modeswitch pkg has been installed there should be no  need to edit the conf files, also the file association to the new pkg is called usb_modeswitch.setup and now used only as a reference.

the only point of note here is the are two devices which can give ID's as listed and can be confusing.One device unflipped "only seen as the CD or file" has Ids which will give the same id's as to a one that has flipped IE it has been recognised as a modem, so there for can be difficult to decide which is which, therefore please check if the device is been recognised on the system as I have mentioned,

once the device has been fully recognised and the ports/lines are configured to the device then the methods of dial up can be tried. ensure you have full details from your ISP etc


regards

alexfish

---

### Post by sankarvichu on 2010-04-08
@ pdc... thankyou guy... shall do it and come back...

@ alexfish... thanks...

---

### Post by sankarvichu on 2010-04-08
hi pdc,

as adviced i tried to register in the provided link or site... they are asking to discover the hint answer to get registered... i tried my level best, but cant find the producer, brand... the question is...

"Due to continuous forum spamming the visual confirmation has been replaced by a 'semantic' one.
 You are asked for an authorization code when registering (and only then). At that point please enter:  **the name of the maker (producer, brand) of the GlobeSurfer iCON**
 (six letters, case does not matter) 
 You'll easily find the answer on the [USB_ModeSwitch]("http://www.draisberghof.de/usb_modeswitch/index.html") page. It's the first single device listed under "Known Working Hardware". There is no advertising involved and the word may change in the future.
  Our apologies for this inconvenience ..."
 

 the modeswitch page link is [http://www.draisberghof.de/usb_modeswitch/index.html](http://www.draisberghof.de/usb_modeswitch/index.html)
 

 if u can find the answer please pass it on...
 

 thanks in advance...

---

### Post by pdc on 2010-04-09
how about ...

option

---

### Post by sankarvichu on 2010-04-12
hi pdc,

i have posted the new output(not new) after doing things said by josh, in usb modeswitch forum... 

[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=2262#2262](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=2262#2262)

sorry to say, no joy...

hope, may get a solution...

thanks in advance

---

### Post by pdc on 2010-04-12
thanks; if we wait for Josh to answer first on the usb_modeswitch forum

---

### Post by sankarvichu on 2010-04-15
hi pdc,

hope USB Modeswitch - sucess with the help of josh (posted in usb modeswitch forum)... but not yet connected to net... 
 
the wvdial.conf is modified as below...

  quote 
    [Dialer Defaults] 
    Init1 = ATZ 
    Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
    Modem Type = Analog Modem 
    ISDN = 0 
    Phone = #777 
    Modem = /dev/ttyUSB2 
    Username = xxxxxx(the provided username) 
    Password = xxxxxx(the provided password) 
    Baud = 460800 
    Stupid Mode = 1 
unquote 
 
then dialed using wvdial... the output is... 
 
quote 
sankar@ubuntu:~$ wvdial 
--> WvDial: Internet dialer version 1.60 
--> Cannot get information for serial port. 
--> Initializing modem. 
--> Sending: ATZ 
ATZ 
OK 
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
OK 
--> Modem initialized. 
--> Sending: ATDT#777 
--> Waiting for carrier. 
ATDT#777 
--> Timed out while dialing.  Trying again. 
--> Sending: ATDT#777 
--> Waiting for carrier. 
ATDT#777 
--> Timed out while dialing.  Trying again. 
--> Sending: ATDT#777 
--> Waiting for carrier. 
ATDT#777 
--> Timed out while dialing.  Trying again. 
--> Sending: ATDT#777 
--> Waiting for carrier. 
ATDT#777 
^CCaught signal 2:  Attempting to exit gracefully... 
--> Disconnecting at Fri Apr 16 00:26:34 2010 
sankar@ubuntu:~$  
unquote 
 
can you help me... thanks in advance...

---

### Post by pdc on 2010-04-16
running out of ideas now ...........

have you tried different ttyUSB values?

ie ttyUSB0 and if that does not work, ttyUSB1 ?

you need to edit the wvdial.conf file to try these

> sudo gedit /etc/wvdial.conf

---

### Post by sankarvichu on 2010-04-20
hi pdc,

heartly thanks for your help, got connected... 

found in googling to configure pppcofig.. 

thankyou very much...

---

### Post by pdc on 2010-04-20
great! well done! enjoy!

PLEASE tell us the settings that worked for you as it will help others who follow you

---

### Post by tusharkoshti on 2012-04-28
Hello friends,

I am also facing problem with EVDO card in Ubuntu( 11.10)

I just got info like before doing anything I will have to install wvdial. For that I will have to install following packages in the same order :

libxplc0.3.13
libwvstreams4.4-base
libwvstreams4.4-extras
libuniconf4.4
wvdial_1.60.1+nmu2_i386

I have downloaded these packages (don't know the r correct or not but by looking name seems that they r right ) but can't install in Ubuntu. Install tab is inactive when I double click on packages. So plz can anyone help me in installing wvdial ? ( I don't have Internet connection on Ubuntu)

---

### Post by dharanitharan on 2012-05-03
> **sankarvichu said:**
> hi pdc,

heartly thanks for your help, got connected... 

found in googling to configure pppcofig.. 

thankyou very much...
Hi sankarvichu,
I am trying to configure BSNL EVDO modem in Ubuntu 11.10. Can you please share the things you modified, any help will be highly appreciated.

Thanks in Advance,
Dharanitharan

---

