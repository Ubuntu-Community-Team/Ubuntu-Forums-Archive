---
title: "Need help with the wireless."
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by dremare on 2008-12-14
Hi,

       I just install Ubuntu 8.10. My wireless router was reconginzed and it ask for WEP 128-bit key. So I typed in and waited about for a minute and it ask for again. I know that typed it right, so I tried about 3 times. Still no connection, so please if anybody can help me with this issue.

Thanks,
Dremare 

Oh I'm use RealTek 8185 wifi on my laptop and AT&T 2wire gateway wireless router.

---

### Post by boterbram on 2008-12-14
Are you sure it is a WEP connection?

And can you maybe post the ouput of the dmesg command?

---

### Post by Kartsa67 on 2008-12-14
Well, I have almost the same problem. I cannot connect to my WLAN, because Ubuntu asks always the WPA password, and finally disconnects. BUT when I move near (less than 3 feet) to my WLAN transmitter (Buffalo), I can easily connect to Internet using WLAN?? Weird?? And if I move little away from transmitter, Ubuntu disconnects the connection even the signal level is about 70%.

-Kari-

---

### Post by dremare on 2008-12-14
hi, here it goes. I can only send a page at a time.

[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc038329a - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038329a   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004022] Calibrating delay loop (skipped), value calculated using timer frequency.. 3192.29 BogoMIPS (lpj=6384580)
[    0.004068] Security Framework initialized
[    0.004090] SELinux:  Disabled at boot.
[    0.004139] AppArmor: AppArmor initialized
[    0.004158] Mount-cache hash table entries: 512
[    0.004536] Initializing cgroup subsys ns
[    0.004549] Initializing cgroup subsys cpuacct
[    0.004556] Initializing cgroup subsys memory
[    0.004589] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004596] CPU: L2 cache: 1024K
[    0.004602] CPU: Physical Processor ID: 0
[    0.004607] CPU: Processor Core ID: 0
[    0.004616] using mwait in idle threads.
[    0.004640] Checking 'hlt' instruction... OK.
[    0.024011] ACPI: Core revision 20080609
[    0.029325] ACPI: Checking initramfs for custom DSDT
[    0.888318] ENABLING IO-APIC IRQs
[    0.888562] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.928282] CPU0: Intel Genuine Intel(R) CPU           T2060  @ 1.60GHz stepping 0c
[    0.932031] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3192.70 BogoMIPS (lpj=6385408)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    1.016710] CPU1: Intel Genuine Intel(R) CPU           T2060  @ 1.60GHz stepping 0c
[    1.016756] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    1.020071] Brought up 2 CPUs
[    1.020078] Total of 2 processors activated (6384.99 BogoMIPS).
[    1.020125] CPU0 attaching sched-domain:
[    1.020132]  domain 0: span 0-1 level MC
[    1.020139]   groups: 0 1
[    1.020154] CPU1 attaching sched-domain:
[    1.020160]  domain 0: span 0-1 level MC
[    1.020166]   groups: 1 0
[    1.020335] net_namespace: 840 bytes
[    1.020335] Booting paravirtualized kernel on bare hardware
[    1.020660] Time:  9:12:00  Date: 12/14/08
[    1.020722] NET: Registered protocol family 16

---

### Post by dremare on 2008-12-14
[    1.020769] EISA bus registered
[    1.020769] ACPI: bus type pci registered
[    1.020769] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 9
[    1.020769] PCI: MCFG area at e0000000 reserved in E820
[    1.020769] PCI: Using MMCONFIG for extended config space
[    1.020769] PCI: Using configuration type 1 for base access
[    1.028157] ACPI: EC: Look up EC in DSDT
[    1.039407] ACPI: Interpreter enabled
[    1.039415] ACPI: (supports S0 S3 S4 S5)
[    1.039454] ACPI: Using IOAPIC for interrupt routing
[    1.040397] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    1.068350] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    1.068350] ACPI: EC: driver started in interrupt mode
[    1.068350] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    1.068350] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    1.068350] pci 0000:00:04.0: PME# disabled
[    1.068350] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    1.068350] pci 0000:00:05.0: PME# disabled
[    1.068394] PCI: 0000:00:13.0 reg 10 32bit mmio: [d0504000, d0504fff]
[    1.068504] PCI: 0000:00:13.1 reg 10 32bit mmio: [d0505000, d0505fff]
[    1.068637] PCI: 0000:00:13.2 reg 10 32bit mmio: [d0506000, d0506fff]
[    1.068730] pci 0000:00:13.2: supports D1
[    1.068734] pci 0000:00:13.2: supports D2
[    1.068740] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    1.068751] pci 0000:00:13.2: PME# disabled
[    1.068799] PCI: 0000:00:14.0 reg 10 io port: [8400, 840f]
[    1.068815] PCI: 0000:00:14.0 reg 14 32bit mmio: [d0507000, d05073ff]
[    1.068878] HPET not enabled in BIOS. You might try hpet=force boot option
[    1.068944] PCI: 0000:00:14.1 reg 10 io port: [8428, 842f]
[    1.068960] PCI: 0000:00:14.1 reg 14 io port: [8434, 8437]
[    1.068976] PCI: 0000:00:14.1 reg 18 io port: [8420, 8427]
[    1.068992] PCI: 0000:00:14.1 reg 1c io port: [8430, 8433]
[    1.069008] PCI: 0000:00:14.1 reg 20 io port: [8410, 841f]
[    1.069144] PCI: 0000:00:14.2 reg 10 64bit mmio: [d0500000, d0503fff]
[    1.069232] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    1.069243] pci 0000:00:14.2: PME# disabled
[    1.069499] PCI: 0000:01:05.0 reg 10 32bit mmio: [d8000000, dfffffff]
[    1.069511] PCI: 0000:01:05.0 reg 14 io port: [9000, 90ff]
[    1.069522] PCI: 0000:01:05.0 reg 18 32bit mmio: [d0000000, d000ffff]
[    1.069551] PCI: 0000:01:05.0 reg 30 32bit mmio: [0, 1ffff]
[    1.069574] pci 0000:01:05.0: supports D1
[    1.069578] pci 0000:01:05.0: supports D2
[    1.069624] PCI: bridge 0000:00:01.0 io port: [9000, 9fff]
[    1.069633] PCI: bridge 0000:00:01.0 32bit mmio: [d0000000, d00fffff]
[    1.069643] PCI: bridge 0000:00:01.0 32bit mmio pref: [d8000000, dfffffff]
[    1.069738] PCI: 0000:02:00.0 reg 10 64bit mmio: [d0100000, d0103fff]
[    1.069754] PCI: 0000:02:00.0 reg 18 io port: [a000, a0ff]
[    1.069825] pci 0000:02:00.0: supports D1
[    1.069830] pci 0000:02:00.0: supports D2
[    1.069836] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.069846] pci 0000:02:00.0: PME# disabled
[    1.069938] PCI: bridge 0000:00:04.0 io port: [a000, afff]
[    1.069947] PCI: bridge 0000:00:04.0 32bit mmio: [d0100000, d01fffff]
[    1.070052] PCI: bridge 0000:00:05.0 io port: [6000, 7fff]
[    1.070060] PCI: bridge 0000:00:05.0 32bit mmio: [b0000000, b1ffffff]
[    1.070073] PCI: bridge 0000:00:05.0 64bit mmio pref: [b2000000, b3ffffff]

---

### Post by dremare on 2008-12-14
[    1.096948] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[    1.096956] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[    1.096964] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[    1.096972] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[    1.096979] system 00:08: ioport range 0x8000-0x805f has been reserved
[    1.096987] system 00:08: ioport range 0x8210-0x821f has been reserved
[    1.096996] system 00:08: ioport range 0xf40-0xf47 has been reserved
[    1.097003] system 00:08: ioport range 0x280-0x293 has been reserved
[    1.097011] system 00:08: ioport range 0x87f-0x87f has been reserved
[    1.097028] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[    1.097037] system 00:09: iomem range 0xfff00000-0xffffffff could not be reserved
[    1.133193] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    1.133202] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    1.133212] pci 0000:00:01.0:   MEM window: 0xd0000000-0xd00fffff
[    1.133222] pci 0000:00:01.0:   PREFETCH window: 0x000000d8000000-0x000000dfffffff
[    1.133234] pci 0000:00:04.0: PCI bridge, secondary bus 0000:02
[    1.133242] pci 0000:00:04.0:   IO window: 0xa000-0xafff
[    1.133252] pci 0000:00:04.0:   MEM window: 0xd0100000-0xd01fffff
[    1.133261] pci 0000:00:04.0:   PREFETCH window: disabled
[    1.133272] pci 0000:00:05.0: PCI bridge, secondary bus 0000:05
[    1.133280] pci 0000:00:05.0:   IO window: 0x6000-0x7fff
[    1.133289] pci 0000:00:05.0:   MEM window: 0xb0000000-0xb1ffffff
[    1.133299] pci 0000:00:05.0:   PREFETCH window: 0x000000b2000000-0x000000b3ffffff
[    1.133311] pci 0000:00:14.4: PCI bridge, secondary bus 0000:08
[    1.133323] pci 0000:00:14.4:   IO window: 0xb000-0xbfff
[    1.133336] pci 0000:00:14.4:   MEM window: 0xf0200000-0xf02fffff
[    1.133347] pci 0000:00:14.4:   PREFETCH window: 0x000000f0300000-0x000000f03fffff
[    1.133385] pci 0000:00:04.0: setting latency timer to 64
[    1.133401] pci 0000:00:05.0: setting latency timer to 64
[    1.133421] bus: 00 index 0 io port: [0, ffff]
[    1.133427] bus: 00 index 1 mmio: [0, ffffffff]
[    1.133433] bus: 01 index 0 io port: [9000, 9fff]
[    1.133439] bus: 01 index 1 mmio: [d0000000, d00fffff]
[    1.133446] bus: 01 index 2 mmio: [d8000000, dfffffff]
[    1.133451] bus: 01 index 3 mmio: [0, 0]
[    1.133457] bus: 02 index 0 io port: [a000, afff]
[    1.133463] bus: 02 index 1 mmio: [d0100000, d01fffff]
[    1.133469] bus: 02 index 2 mmio: [0, 0]
[    1.133474] bus: 02 index 3 mmio: [0, 0]
[    1.133480] bus: 05 index 0 io port: [6000, 7fff]
[    1.133486] bus: 05 index 1 mmio: [b0000000, b1ffffff]
[    1.133493] bus: 05 index 2 mmio: [b2000000, b3ffffff]
[    1.133498] bus: 05 index 3 mmio: [0, 0]
[    1.133504] bus: 08 index 0 io port: [b000, bfff]
[    1.133510] bus: 08 index 1 mmio: [f0200000, f02fffff]
[    1.133517] bus: 08 index 2 mmio: [f0300000, f03fffff]
[    1.133523] bus: 08 index 3 io port: [0, ffff]
[    1.133528] bus: 08 index 4 mmio: [0, ffffffff]
[    1.133551] NET: Registered protocol family 2
[    1.144911] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.145527] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.146905] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.147894

---

### Post by dremare on 2008-12-14
] TCP: Hash tables configured (established 131072 bind 65536)
[    1.147904] TCP reno registered
[    1.149026] NET: Registered protocol family 1
[    1.149295] checking if image is initramfs...<7>Switched to high resolution mode on CPU 1
[    1.636073] Switched to high resolution mode on CPU 0
[    1.989114]  it is
[    2.903831] Freeing initrd memory: 7973k freed
[    2.906920] audit: initializing netlink socket (disabled)
[    2.906952] type=2000 audit(1229245920.904:1): initialized
[    2.922537] highmem bounce pool size: 64 pages
[    2.922553] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.929251] VFS: Disk quotas dquot_6.5.1
[    2.929503] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.929767] msgmni has been set to 1744
[    2.930088] io scheduler noop registered
[    2.930095] io scheduler anticipatory registered
[    2.930102] io scheduler deadline registered
[    2.930133] io scheduler cfq registered (default)
[    2.930255] pci 0000:01:05.0: Boot video device
[    2.930522] pcieport-driver 0000:00:04.0: setting latency timer to 64
[    2.930588] pcieport-driver 0000:00:04.0: found MSI capability
[    2.930655] pci_express 0000:00:04.0:pcie00: allocate port service
[    2.930788] pci_express 0000:00:04.0:pcie02: allocate port service
[    2.930993] pcieport-driver 0000:00:05.0: setting latency timer to 64
[    2.931057] pcieport-driver 0000:00:05.0: found MSI capability
[    2.931119] pci_express 0000:00:05.0:pcie00: allocate port service
[    2.931238] pci_express 0000:00:05.0:pcie02: allocate port service
[    2.932095] isapnp: Scanning for PnP cards...
[    3.289386] isapnp: No Plug & Play device found
[    3.389141] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    3.395185] brd: module loaded
[    3.395367] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    3.395681] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    3.399673] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.399689] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.408329] mice: PS/2 mouse device common for all mice
[    3.408682] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    3.408725] rtc0: alarms up to one month
[    3.409076] EISA: Probing bus 0 at eisa.0
[    3.409093] Cannot allocate resource for EISA slot 1
[    3.409128] Cannot allocate resource for EISA slot 6
[    3.409135] Cannot allocate resource for EISA slot 7
[    3.409141] Cannot allocate resource for EISA slot 8
[    3.409146] EISA: Detected 0 cards.
[    3.409154] cpuidle: using governor ladder
[    3.409160] cpuidle: using governor menu
[    3.410468] TCP cubic registered
[    3.410534] Using IPI No-Shortcut mode
[    3.411031] registered taskstats version 1
[    3.411295]   Magic number: 4:210:222
[    3.411350] tty ttyu6: hash matches
[    3.411540] rtc_cmos 00:04: setting system clock to 2008-12-14 09:12:02 UTC (1229245922)
[    3.411549] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found

---

### Post by dremare on 2008-12-14
[    3.411555] EDD information not available.
[    3.412138] Freeing unused kernel memory: 424k freed
[    3.412258] Write protecting the kernel text: 2576k
[    3.412331] Write protecting the kernel read-only data: 936k
[    3.445144] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    3.713348] fuse init (API version 7.9)
[    3.810116] ACPI: SSDT 7BE8EC67, 01EA (r1  PmRef  Cpu0Ist     3000 INTL 20050228)
[    3.811618] ACPI: SSDT 7BE8E9F2, 01F0 (r1  PmRef  Cpu0Cst     3001 INTL 20050228)
[    3.943038] processor ACPI0007:00: registered as cooling_device0
[    3.943051] ACPI: Processor [CPU0] (supports 8 throttling states)
[    3.943906] ACPI: SSDT 7BE8EE51, 0089 (r1  PmRef  Cpu1Ist     3000 INTL 20050228)
[    3.944711] ACPI: SSDT 7BE8EBE2, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050228)
[    3.945832] processor ACPI0007:01: registered as cooling_device1
[    3.945845] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.955199] thermal LNXTHERM:01: registered as thermal_zone0
[    3.957485] ACPI: Thermal Zone [THRM] (62 C)
[    4.744857] usbcore: registered new interface driver usbfs
[    4.744913] usbcore: registered new interface driver hub
[    4.777270] usbcore: registered new device driver usb
[    4.793470] sky2 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.793496] sky2 0000:02:00.0: setting latency timer to 64
[    4.793539] sky2 0000:02:00.0: v1.22 addr 0xd0100000 irq 16 Yukon-2 FE rev 1
[    4.794455] sky2 eth0: addr 00:03:25:3f:dd:89
[    4.801628] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    4.801653] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    4.801767] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    4.801861] ehci_hcd 0000:00:13.2: irq 19, io mem 0xd0506000
[    4.813048] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.813426] usb usb1: configuration #1 chosen from 1 choice
[    4.813499] hub 1-0:1.0: USB hub found
[    4.813522] hub 1-0:1.0: 8 ports detected
[    4.831437] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.836224] No dock devices found.
[    4.899701] SCSI subsystem initialized
[    4.946844] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    4.946877] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    4.946940] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    4.946983] ohci_hcd 0000:00:13.0: irq 19, io mem 0xd0504000
[    4.949160] libata version 3.00 loaded.
[    5.005418] usb usb2: configuration #1 chosen from 1 choice
[    5.005495] hub 2-0:1.0: USB hub found
[    5.005523] hub 2-0:1.0: 4 ports detected
[    5.110246] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    5.110278] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    5.110352] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    5.110391] ohci_hcd 0000:00:13.1: irq 19, io mem 0xd0505000
[    5.169575] usb usb3: configuration #1 chosen from 1 choice

---

### Post by dremare on 2008-12-14
[    5.169655] hub 3-0:1.0: USB hub found
[    5.169682] hub 3-0:1.0: 4 ports detected
[    5.273720] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.273801] pata_atiixp 0000:00:14.1: setting latency timer to 64
[    5.274661] scsi0 : pata_atiixp
[    5.274910] scsi1 : pata_atiixp
[    5.278743] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8410 irq 14
[    5.278753] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8418 irq 15
[    5.450077] ata1.00: ATA-7: HTS421280H9AT00, HA3OA70S, max UDMA/100
[    5.450087] ata1.00: 156301488 sectors, multi 16: LBA48 
[    5.450141] ata1.01: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4244N, GW01, max UDMA/33
[    5.465969] ata1.00: configured for UDMA/100
[    5.481650] ata1.01: configured for UDMA/33
[    5.649851] scsi 0:0:0:0: Direct-Access     ATA      HTS421280H9AT00  HA3O PQ: 0 ANSI: 5
[    5.654436] scsi 0:0:1:0: CD-ROM            HL-DT-ST RW/DVD GCC-4244N GW01 PQ: 0 ANSI: 5
[    5.719768] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    5.719870] scsi 0:0:1:0: Attached scsi generic sg1 type 5
[    5.753671] Driver 'sr' needs updating - please use bus_type methods
[    5.764930] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    5.764940] Uniform CD-ROM driver Revision: 3.20
[    5.765374] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    5.767611] Driver 'sd' needs updating - please use bus_type methods
[    5.767859] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    5.767913] sd 0:0:0:0: [sda] Write Protect is off
[    5.767920] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.768035] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.768222] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    5.768271] sd 0:0:0:0: [sda] Write Protect is off
[    5.768278] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.768369] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.768381]  sda: sda1 sda2 sda3 < sda5 sda6 > sda4
[    5.823233] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.419941] PM: Starting manual resume from disk
[    6.419951] PM: Resume from partition 8:5
[    6.419956] PM: Checking hibernation image.
[    6.420240] PM: Resume from disk failed.
[    6.509145] kjournald starting.  Commit interval 5 seconds
[    6.509183] EXT3-fs: mounted filesystem with ordered data mode.
[   37.536084] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   37.536157] ata1.00: cmd c8/00:88:7b:5c:29/00:00:00:00:00/e6 tag 0 dma 69632 in
[   37.536161]          res 40/00:02:00:08:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[   37.536273] ata1.00: status: { DRDY }
[   37.536368] ata1: soft resetting link
[   37.724943] ata1.00: configured for UDMA/100
[   37.740594] ata1.01: configured for UDMA/33
[   37.740615] ata1: EH complete
[   37.750879] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   37.750933] sd 0:0:0:0: [sda] Write Protect is off
[   37.750941] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00

---

### Post by dremare on 2008-12-14
[   37.751026] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.751112] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   37.760249] sd 0:0:0:0: [sda] Write Protect is off
[   37.760255] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   37.771593] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   44.805399] udevd version 124 started
[   45.879708] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   45.950161] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   46.123021] Linux agpgart interface v0.103
[   46.590489] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   46.610069] ACPI: Power Button (FF) [PWRF]
[   46.610260] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   46.625045] ACPI: Power Button (CM) [PWRB]
[   46.625241] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input4
[   46.625785] ACPI: Lid Switch [LID0]
[   46.625964] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input5
[   46.648057] ACPI: Sleep Button (CM) [SLPB]
[   46.660915] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   46.750135] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8400, revision 0
[   46.776721] ACPI: AC Adapter [AC] (on-line)
[   47.329003] ACPI: Battery Slot [BAT0] (battery present)
[   47.971090] ACPI: \_SB_.PCI0.IDE_.SECD.S_D0: found ejectable bay
[   47.971102] ACPI: \_SB_.PCI0.IDE_.SECD.S_D0: Adding notify handler
[   47.971179] ACPI: Error installing bay notify handler
[   47.971625] ACPI: \_SB_.PCI0.IDE_.SECD.S_D1: found ejectable bay
[   47.971635] ACPI: \_SB_.PCI0.IDE_.SECD.S_D1: Adding notify handler
[   47.971691] ACPI: Error installing bay notify handler
[   48.133243] ACPI: \_SB_.PCI0.IDE_.SECD.S_D0: found ejectable bay
[   48.133256] ACPI: \_SB_.PCI0.IDE_.SECD.S_D0: Adding notify handler
[   48.133325] ACPI: Error installing bay notify handler
[   48.133514] ACPI: \_SB_.PCI0.IDE_.SECD.S_D1: found ejectable bay
[   48.133524] ACPI: \_SB_.PCI0.IDE_.SECD.S_D1: Adding notify handler
[   48.133574] ACPI: Error installing bay notify handler
[   48.323857] rtl8180 0000:08:09.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   48.446035] phy0: Selected rate control algorithm 'pid'
[   48.516681] acpi device:1e: registered as cooling_device2
[   48.517166] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1b/device:1c/input/input7
[   48.540075] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   49.439109] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x23aeb3, caps: 0xa04713/0x10008
[   49.478913] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   49.699434] phy0: hwaddr 00:c0:a8:ce:e8:36, RTL8185vD + rtl8225
[   49.699921] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   51.989232] lp: driver loaded but no devices found
[   52.348656] Adding 947824k swap on /dev/sda5.  Priority:-1 extents:1 across:947824k
[   52.992322] EXT3 FS on sda4, internal journal

---

### Post by dremare on 2008-12-14
[   54.073384] kjournald starting.  Commit interval 5 seconds
[   54.073684] EXT3 FS on sda6, internal journal
[   54.073698] EXT3-fs: mounted filesystem with ordered data mode.
[   54.442485] type=1505 audit(1229263973.853:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4033
[   54.905966] type=1505 audit(1229263974.317:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4038
[   54.906459] type=1505 audit(1229263974.317:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4038
[   55.105035] ip_tables: (C) 2000-2006 Netfilter Core Team
[   56.095773] ACPI: \_SB_.PCI0.IDE_.SECD.S_D0: found ejectable bay
[   56.095787] ACPI: \_SB_.PCI0.IDE_.SECD.S_D0: Adding notify handler
[   56.095873] ACPI: Error installing bay notify handler
[   56.097175] ACPI: \_SB_.PCI0.IDE_.SECD.S_D1: found ejectable bay
[   56.097186] ACPI: \_SB_.PCI0.IDE_.SECD.S_D1: Adding notify handler
[   56.097261] ACPI: Error installing bay notify handler
[   56.266098] ACPI: WMI: Mapper loaded
[   57.557226] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   57.625798] apm: BIOS not found.
[   57.846289] ppdev: user-space parallel port driver
[   59.903338] Bluetooth: Core ver 2.13
[   59.903729] NET: Registered protocol family 31
[   59.903735] Bluetooth: HCI device and connection manager initialized
[   59.903744] Bluetooth: HCI socket layer initialized
[   59.938381] Bluetooth: L2CAP ver 2.11
[   59.938397] Bluetooth: L2CAP socket layer initialized
[   59.979607] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   59.979624] Bluetooth: BNEP filters: protocol multicast
[   60.046503] Bridge firewalling registered
[   60.047969] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   60.076139] Bluetooth: SCO (Voice Link) ver 0.6
[   60.076153] Bluetooth: SCO socket layer initialized
[   60.101034] Bluetooth: RFCOMM socket layer initialized
[   60.101074] Bluetooth: RFCOMM TTY layer initialized
[   60.101084] Bluetooth: RFCOMM ver 1.10
[   61.288457] pci 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   61.741859] [drm] Initialized drm 1.1.0 20060810
[   61.767882] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   62.265249] [drm] Setting GART location based on new memory map
[   62.266317] [drm] Loading R300 Microcode
[   62.266365] [drm] Num pipes: 3
[   62.266374] [drm] writeback test succeeded in 1 usecs
[   64.260346] sky2 eth0: enabling interface
[   67.736459] NET: Registered protocol family 17
[   67.954486] hda-intel: Invalid position buffer, using LPIB read method instead.
[  480.248597] CPU0 attaching NULL sched-domain.
[  480.248618] CPU1 attaching NULL sched-domain.
[  480.252274] CPU0 attaching sched-domain:
[  480.252289]  domain 0: span 0-1 level MC
[  480.252299]   groups: 0 1
[  480.252314] CPU1 attaching sched-domain:
[  480.252319]  domain 0: span 0-1 level MC
[  480.252325]   groups: 1 0

[    1.147894] TCP: Hash tables configured (established 131072 bind 65536)
[    1.147904] TCP reno registered
[    1.149026] NET: Registered protocol family 1
[    1.149295] checking if image is initramfs...<7>Switched to high resolution mode on CPU 1
[    1.636073] Switched to high resolution mode on CPU 0
[    1.989114]  it is
[    2.903831] Freeing initrd memory: 7973k freed
[    2.906920] audit: initializing netlink socket (disabled)
[    2.906952] type=2000 audit(1229245920.904:1): initialized
[    2.922537] highmem bounce pool size: 64 pages
[    2.922553] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.929251] VFS: Disk quotas dquot_6.5.1
[    2.929503] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.929767] msgmni has been set to 1744
[    2.930088] io scheduler noop registered
[    2.930095] io scheduler anticipatory registered
[    2.930102] io scheduler deadline registered
[    2.930133] io scheduler cfq registered (default)
[    2.930255] pci 0000:01:05.0: Boot video device
[    2.930522] pcieport-driver 0000:00:04.0: setting latency timer to 64
[    2.930588] pcieport-driver 0000:00:04.0: found MSI capability
[    2.930655] pci_express 0000:00:04.0:pcie00: allocate port service
[    2.930788] pci_express 0000:00:04.0:pcie02: allocate port service
[    2.930993] pcieport-driver 0000:00:05.0: setting latency timer to 64
[    2.931057] pcieport-driver 0000:00:05.0: found MSI capability
[    2.931119] pci_express 0000:00:05.0:pcie00: allocate port service
[    2.931238] pci_express 0000:00:05.0:pcie02: allocate port service
[    2.932095] isapnp: Scanning for PnP cards...
[    3.289386] isapnp: No Plug & Play device found
[    3.389141] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    3.395185] brd: module loaded
[    3.395367] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    3.395681] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    3.399673] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.399689] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.408329] mice: PS/2 mouse device common for all mice
[    3.408682] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    3.408725] rtc0: alarms up to one month
[    3.409076] EISA: Probing bus 0 at eisa.0
[    3.409093] Cannot allocate resource for EISA slot 1
[    3.409128] Cannot allocate resource for EISA slot 6
[    3.409135] Cannot allocate resource for EISA slot 7
[    3.409141] Cannot allocate resource for EISA slot 8
[    3.409146] EISA: Detected 0 cards.
[    3.409154] cpuidle: using governor ladder
[    3.409160] cpuidle: using governor menu
[    3.410468] TCP cubic registered
[    3.410534] Using IPI No-Shortcut mode
[    3.411031] registered taskstats version 1
[    3.411295]   Magic number: 4:210:222
[    3.411350] tty ttyu6: hash matches
[    3.411540] rtc_cmos 00:04: setting system clock to 2008-12-14 09:12:02 UTC (1229245922)
[    3.411549] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.411555] EDD information not available.

---

### Post by dremare on 2008-12-14
[    3.412138] Freeing unused kernel memory: 424k freed
[    3.412258] Write protecting the kernel text: 2576k
[    3.412331] Write protecting the kernel read-only data: 936k
[    3.445144] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    3.713348] fuse init (API version 7.9)
[    3.810116] ACPI: SSDT 7BE8EC67, 01EA (r1  PmRef  Cpu0Ist     3000 INTL 20050228)
[    3.811618] ACPI: SSDT 7BE8E9F2, 01F0 (r1  PmRef  Cpu0Cst     3001 INTL 20050228)
[    3.943038] processor ACPI0007:00: registered as cooling_device0
[    3.943051] ACPI: Processor [CPU0] (supports 8 throttling states)
[    3.943906] ACPI: SSDT 7BE8EE51, 0089 (r1  PmRef  Cpu1Ist     3000 INTL 20050228)
[    3.944711] ACPI: SSDT 7BE8EBE2, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050228)
[    3.945832] processor ACPI0007:01: registered as cooling_device1
[    3.945845] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.955199] thermal LNXTHERM:01: registered as thermal_zone0
[    3.957485] ACPI: Thermal Zone [THRM] (62 C)
[    4.744857] usbcore: registered new interface driver usbfs
[    4.744913] usbcore: registered new interface driver hub
[    4.777270] usbcore: registered new device driver usb
[    4.793470] sky2 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.793496] sky2 0000:02:00.0: setting latency timer to 64
[    4.793539] sky2 0000:02:00.0: v1.22 addr 0xd0100000 irq 16 Yukon-2 FE rev 1
[    4.794455] sky2 eth0: addr 00:03:25:3f:dd:89
[    4.801628] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    4.801653] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    4.801767] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    4.801861] ehci_hcd 0000:00:13.2: irq 19, io mem 0xd0506000
[    4.813048] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.813426] usb usb1: configuration #1 chosen from 1 choice
[    4.813499] hub 1-0:1.0: USB hub found
[    4.813522] hub 1-0:1.0: 8 ports detected
[    4.831437] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.836224] No dock devices found.
[    4.899701] SCSI subsystem initialized
[    4.946844] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    4.946877] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    4.946940] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    4.946983] ohci_hcd 0000:00:13.0: irq 19, io mem 0xd0504000
[    4.949160] libata version 3.00 loaded.
[    5.005418] usb usb2: configuration #1 chosen from 1 choice
[    5.005495] hub 2-0:1.0: USB hub found
[    5.005523] hub 2-0:1.0: 4 ports detected
[    5.110246] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    5.110278] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    5.110352] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    5.110391] ohci_hcd 0000:00:13.1: irq 19, io mem 0xd0505000
[    5.169575] usb usb3: configuration #1 chosen from 1 choice
[    5.169655] hub 3-0:1.0: USB hub found
[    5.169682] hub 3-0:1.0: 4 ports detected
[    5.273720] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.273801] pata_atiixp 0000:00:14.1: setting latency timer to 64
[    5.274661] scsi0 : pata_atiixp
[    5.274910] scsi1 : pata_atiixp
[    5.278743] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8410 irq 14
[    5.278753] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8418 irq 15
[    5.450077] ata1.00: ATA-7: HTS421280H9AT00, HA3OA70S, max UDMA/100
[    5.450087] ata1.00: 156301488 sectors, multi 16: LBA48 
[    5.450141] ata1.01: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4244N, GW01, max UDMA/33
[    5.465969] ata1.00: configured for UDMA/100
[    5.481650] ata1.01: configured for UDMA/33
[    5.649851] scsi 0:0:0:0: Direct-Access     ATA      HTS421280H9AT00  HA3O PQ: 0 ANSI: 5
[    5.654436] scsi 0:0:1:0: CD-ROM            HL-DT-ST RW/DVD GCC-4244N GW01 PQ: 0 ANSI: 5
[    5.719768] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    5.719870] scsi 0:0:1:0: Attached scsi generic sg1 type 5
[    5.753671] Driver 'sr' needs updating - please use bus_type methods
[    5.764930] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    5.764940] Uniform CD-ROM driver Revision: 3.20
[    5.765374] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    5.767611] Driver 'sd' needs updating - please use bus_type methods
[    5.767859] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    5.767913] sd 0:0:0:0: [sda] Write Protect is off
[    5.767920] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.768035] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.768222] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    5.768271] sd 0:0:0:0: [sda] Write Protect is off
[    5.768278] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.768369] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.768381]  sda: sda1 sda2 sda3 < sda5 sda6 > sda4
[    5.823233] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.419941] PM: Starting manual resume from disk
[    6.419951] PM: Resume from partition 8:5
[    6.419956] PM: Checking hibernation image.
[    6.420240] PM: Resume from disk failed.
[    6.509145] kjournald starting.  Commit interval 5 seconds
[    6.509183] EXT3-fs: mounted filesystem with ordered data mode.
[   37.536084] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   37.536157] ata1.00: cmd c8/00:88:7b:5c:29/00:00:00:00:00/e6 tag 0 dma 69632 in
[   37.536161]          res 40/00:02:00:08:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[   37.536273] ata1.00: status: { DRDY }
[   37.536368] ata1: soft resetting link
[   37.724943] ata1.00: configured for UDMA/100
[   37.740594] ata1.01: configured for UDMA/33
[   37.740615] ata1: EH complete
[   37.750879] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   37.750933] sd 0:0:0:0: [sda] Write Protect is off
[   37.750941] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   37

---

### Post by dremare on 2008-12-14
[   37.751026] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.751112] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   37.760249] sd 0:0:0:0: [sda] Write Protect is off
[   37.760255] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   37.771593] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   44.805399] udevd version 124 started
[   45.879708] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   45.950161] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   46.123021] Linux agpgart interface v0.103
[   46.590489] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   46.610069] ACPI: Power Button (FF) [PWRF]
[   46.610260] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   46.625045] ACPI: Power Button (CM) [PWRB]
[   46.625241] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input4
[   46.625785] ACPI: Lid Switch [LID0]
[   46.625964] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input5
[   46.648057] ACPI: Sleep Button (CM) [SLPB]
[   46.660915] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   46.750135] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8400, revision 0
[   46.776721] ACPI: AC Adapter [AC] (on-line)
[   47.329003] ACPI: Battery Slot [BAT0] (battery present)
[   47.971090] ACPI: \_SB_.PCI0.IDE_.SECD.S_D0: found ejectable bay
[   47.971102] ACPI: \_SB_.PCI0.IDE_.SECD.S_D0: Adding notify handler
[   47.971179] ACPI: Error installing bay notify handler
[   47.971625] ACPI: \_SB_.PCI0.IDE_.SECD.S_D1: found ejectable bay
[   47.971635] ACPI: \_SB_.PCI0.IDE_.SECD.S_D1: Adding notify handler
[   47.971691] ACPI: Error installing bay notify handler
[   48.133243] ACPI: \_SB_.PCI0.IDE_.SECD.S_D0: found ejectable bay
[   48.133256] ACPI: \_SB_.PCI0.IDE_.SECD.S_D0: Adding notify handler
[   48.133325] ACPI: Error installing bay notify handler
[   48.133514] ACPI: \_SB_.PCI0.IDE_.SECD.S_D1: found ejectable bay
[   48.133524] ACPI: \_SB_.PCI0.IDE_.SECD.S_D1: Adding notify handler
[   48.133574] ACPI: Error installing bay notify handler
[   48.323857] rtl8180 0000:08:09.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   48.446035] phy0: Selected rate control algorithm 'pid'
[   48.516681] acpi device:1e: registered as cooling_device2
[   48.517166] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1b/device:1c/input/input7
[   48.540075] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   49.439109] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x23aeb3, caps: 0xa04713/0x10008
[   49.478913] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   49.699434] phy0: hwaddr 00:c0:a8:ce:e8:36, RTL8185vD + rtl8225
[   49.699921] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   51.989232] lp: driver loaded but no devices found
[   52.348656] Adding 947824k swap on /dev/sda5.  Priority:-1 extents:1 across:947824k
[   52.992322] EXT3 FS on sda4, internal journal
[   54.073384] kjournald starting.  Commit interval 5 seconds
[   54.073684] EXT3 FS on sda6, internal journal
[   54.073698] EXT3-fs: mounted filesystem with ordered data mode.
[   54.442485] type=1505 audit(1229263973.853:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4033
[   54.905966] type=1505 audit(1229263974.317:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4038
[   54.906459] type=1505 audit(1229263974.317:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4038
[   55.105035] ip_tables: (C) 2000-2006 Netfilter Core Team
[   56.095773] ACPI: \_SB_.PCI0.IDE_.SECD.S_D0: found ejectable bay
[   56.095787] ACPI: \_SB_.PCI0.IDE_.SECD.S_D0: Adding notify handler
[   56.095873] ACPI: Error installing bay notify handler
[   56.097175] ACPI: \_SB_.PCI0.IDE_.SECD.S_D1: found ejectable bay
[   56.097186] ACPI: \_SB_.PCI0.IDE_.SECD.S_D1: Adding notify handler
[   56.097261] ACPI: Error installing bay notify handler
[   56.266098] ACPI: WMI: Mapper loaded
[   57.557226] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   57.625798] apm: BIOS not found.
[   57.846289] ppdev: user-space parallel port driver
[   59.903338] Bluetooth: Core ver 2.13
[   59.903729] NET: Registered protocol family 31
[   59.903735] Bluetooth: HCI device and connection manager initialized
[   59.903744] Bluetooth: HCI socket layer initialized
[   59.938381] Bluetooth: L2CAP ver 2.11
[   59.938397] Bluetooth: L2CAP socket layer initialized
[   59.979607] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   59.979624] Bluetooth: BNEP filters: protocol multicast
[   60.046503] Bridge firewalling registered
[   60.047969] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   60.076139] Bluetooth: SCO (Voice Link) ver 0.6
[   60.076153] Bluetooth: SCO socket layer initialized
[   60.101034] Bluetooth: RFCOMM socket layer initialized
[   60.101074] Bluetooth: RFCOMM TTY layer initialized
[   60.101084] Bluetooth: RFCOMM ver 1.10
[   61.288457] pci 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   61.741859] [drm] Initialized drm 1.1.0 20060810
[   61.767882] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   62.265249] [drm] Setting GART location based on new memory map
[   62.266317] [drm] Loading R300 Microcode
[   62.266365] [drm] Num pipes: 3
[   62.266374] [drm] writeback test succeeded in 1 usecs
[   64.260346] sky2 eth0: enabling interface
[   67.736459] NET: Registered protocol family 17
[   67.954486] hda-intel: Invalid position buffer, using LPIB read method instead.
[  480.248597] CPU0 attaching NULL sched-domain.
[  480.248618] CPU1 attaching NULL sched-domain.
[  480.252274] CPU0 attaching sched-domain:
[  480.252289]  domain 0: span 0-1 level MC
[  480.252299]   groups: 0 1
[  480.252314] CPU1 attaching sched-domain:
[  480.252319]  domain 0: span 0-1 level MC
[  480.252325]   groups: 1 0

---

### Post by dremare on 2008-12-16
Hey,
     I'm still having problems connecting to wireless router. Ubuntu will see it, but I will it go on line.

please help anybody, thank you.

---

### Post by cyclone5uk on 2008-12-17
Not really a solution, but I'm also having problems (of a different nature) with the realtek 8185 wireless card on Ubuntu 8.10. My problem is still yet to be solved, but one thing I have discovered is that the native driver Ubuntu uses is the 8180 driver (even though Realtek have a Linux driver for the 8185 on their site).

You could try downloading that and installing it in place of the 8180 driver.

I have no idea how to update drivers manually in Ubuntu, as I'm still waiting for help and advice elsewhere on these forums.

---

