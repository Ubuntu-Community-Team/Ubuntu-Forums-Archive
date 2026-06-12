---
title: "slow sluggish/choppy sound"
date: 2009-01-18
forum: Multimedia Software
---

### Post by psychomichael on 2009-01-18
This problem corrected itself awhile back, but is back again with a vengeance. I have noticed a few other threads on the subject on the secondlife forums and on here at [http://ubuntuforums.org/showthread.php?t=579488](http://ubuntuforums.org/showthread.php?t=579488)
but no solutions have worked for me. 

It has only been since I switched to 7.10 that these audio problems have been cropping up...and from what I've heard, they continue in through Hardy. 

Can anyone help?

---

### Post by psychomichael on 2009-01-18
Uname info:
```

Linux darkmage 2.6.22-16-generic #1 SMP Mon Nov 24 18:28:27 GMT 2008 i686 GNU/Linux

```

soundcard info:
```

michael@darkmage:~$ cat /proc/asound/cards
 0 [CMI8738MC8     ]: CMI8738-MC8 - C-Media PCI CMI8738-MC8
                      C-Media PCI CMI8738-MC8 (model 68) at 0xbc00, irq 21

```

Results of my dmesg command:

```

[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at e0000000 (gap: dff00000:10100000)
[    0.000000] Built 1 zonelists.  Total pages: 1040384
[    0.000000] Kernel command line: root=UUID=3447434f-2922-4bcf-949d-3e4b22ef49e7 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2133.389 MHz processor.
[   22.466135] spurious 8259A interrupt: IRQ7.
[   22.468181] Console: colour VGA+ 80x25
[   22.468419] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   22.468660] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   22.632184] Memory: 3622896k/4194304k available (2016k kernel code, 44652k reserved, 919k data, 364k init, 2751424k highmem)
[   22.632191] virtual kernel memory layout:
[   22.632192]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   22.632193]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   22.632194]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   22.632194]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   22.632195]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   22.632196]       .data : 0xc02f8186 - 0xc03dde84   ( 919 kB)
[   22.632197]       .text : 0xc0100000 - 0xc02f8186   (2016 kB)
[   22.632199] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   22.632230] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   22.632352] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[   22.632356] hpet0: 3 32-bit timers, 25000000 Hz
[   22.713204] Calibrating delay using timer specific routine.. 4270.26 BogoMIPS (lpj=8540539)
[   22.713223] Security Framework v1.0.0 initialized
[   22.713228] SELinux:  Disabled at boot.
[   22.713238] Mount-cache hash table entries: 512
[   22.713339] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   22.713345] monitor/mwait feature present.
[   22.713347] using mwait in idle threads.
[   22.713350] CPU: L1 I cache: 32K, L1 D cache: 32K
[   22.713352] CPU: L2 cache: 4096K
[   22.713354] CPU: Physical Processor ID: 0
[   22.713355] CPU: Processor Core ID: 0
[   22.713357] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   22.713364] Compat vDSO mapped to ffffe000.
[   22.713374] Checking 'hlt' instruction... OK.
[   22.729256] SMP alternatives: switching to UP code
[   22.729597] Early unpacking initramfs... done
[   22.986565] ACPI: Core revision 20070126
[   22.986601] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   22.991054] CPU0: Intel(R) Core(TM)2 CPU          6420  @ 2.13GHz stepping 06
[   22.991066] SMP alternatives: switching to SMP code
[   22.991120] Booting processor 1/1 eip 3000
[   23.001563] Initializing CPU#1
[   23.080429] Calibrating delay using timer specific routine.. 4266.68 BogoMIPS (lpj=8533368)
[   23.080434] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   23.080438] monitor/mwait feature present.
[   23.080440] CPU: L1 I cache: 32K, L1 D cache: 32K
[   23.080442] CPU: L2 cache: 4096K
[   23.080443] CPU: Physical Processor ID: 0
[   23.080444] CPU: Processor Core ID: 1
[   23.080446] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   23.081048] CPU1: Intel(R) Core(TM)2 CPU          6420  @ 2.13GHz stepping 06
[   23.081063] Total of 2 processors activated (8536.95 BogoMIPS).
[   23.081289] ENABLING IO-APIC IRQs
[   23.081472] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   23.228186] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   23.248156] Brought up 2 CPUs
[   23.353992] migration_cost=33
[   23.354090] Booting paravirtualized kernel on bare hardware
[   23.354140] Time: 16:56:00  Date: 00/18/109
[   23.354154] NET: Registered protocol family 16
[   23.354215] EISA bus registered
[   23.354219] ACPI: bus type pci registered
[   23.387704] PCI: PCI BIOS revision 3.00 entry at 0xfbaa0, last bus=5
[   23.387705] PCI: Using configuration type 1
[   23.387707] Setting up standard PCI resources
[   23.388994] mtrr: your CPUs had inconsistent fixed MTRR settings
[   23.388996] mtrr: probably your BIOS does not setup all CPUs.
[   23.388997] mtrr: corrected configuration.
[   23.390190] ACPI: EC: Look up EC in DSDT
[   23.395975] ACPI: Interpreter enabled
[   23.395978] ACPI: (supports S0 S1 S3 S4 S5)
[   23.395991] ACPI: Using IOAPIC for interrupt routing
[   23.404995] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   23.405008] PCI: Probing PCI hardware (bus 00)
[   23.406703] PCI: Transparent bridge - 0000:00:10.0
[   23.406759] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   23.407014] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   23.475357] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 *10 11 14 15)
[   23.475509] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   23.475662] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 *10 11 14 15)
[   23.475819] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   23.475970] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 *11 14 15)
[   23.476120] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   23.476270] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   23.476419] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   23.476570] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
[   23.476719] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   23.476870] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
[   23.477019] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   23.477169] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   23.477319] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   23.477469] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   23.477620] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 *11 14 15)
[   23.477772] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
[   23.477922] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   23.478073] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[   23.478224] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 *10 11 14 15)
[   23.478405] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[   23.478579] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   23.478753] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[   23.478926] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   23.479099] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0
[   23.479272] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[   23.479444] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[   23.479617] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[   23.479793] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[   23.479967] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   23.480141] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   23.480314] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[   23.480488] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[   23.480661] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0, disabled.
[   23.480835] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[   23.481009] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   23.481182] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[   23.481356] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[   23.481530] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   23.481703] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   23.481877] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[   23.481983] Linux Plug and Play Support v0.97 (c) Adam Belay
[   23.481990] pnp: PnP ACPI init
[   23.481998] ACPI: bus type pnp registered
[   23.486205] pnp: PnP ACPI: found 15 devices
[   23.486207] ACPI: ACPI bus type pnp unregistered
[   23.486211] PnPBIOS: Disabled by ACPI PNP
[   23.486247] PCI: Using ACPI for IRQ routing
[   23.486250] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   23.549296] NET: Registered protocol family 8
[   23.549298] NET: Registered protocol family 20
[   23.549336] pnp: 00:01: ioport range 0x1000-0x107f has been reserved
[   23.549339] pnp: 00:01: ioport range 0x1080-0x10ff has been reserved
[   23.549341] pnp: 00:01: ioport range 0x1400-0x147f has been reserved
[   23.549343] pnp: 00:01: ioport range 0x1480-0x14ff has been reserved
[   23.549345] pnp: 00:01: ioport range 0x1800-0x187f has been reserved
[   23.549347] pnp: 00:01: ioport range 0x1880-0x18ff has been reserved
[   23.549350] pnp: 00:01: iomem range 0x0-0x0 could not be reserved
[   23.549360] pnp: 00:0d: iomem range 0xf0000000-0xf1ffffff could not be reserved
[   23.549364] pnp: 00:0e: iomem range 0xf0000-0xf3fff could not be reserved
[   23.549366] pnp: 00:0e: iomem range 0xf4000-0xf7fff could not be reserved
[   23.549368] pnp: 00:0e: iomem range 0xf8000-0xfbfff could not be reserved
[   23.549371] pnp: 00:0e: iomem range 0xfc000-0xfffff could not be reserved
[   23.551443] Time: tsc clocksource has been installed.
[   23.551449] Switched to high resolution mode on CPU 0
[   23.551514] Switched to high resolution mode on CPU 1
[   23.579542] PCI: Bridge: 0000:00:03.0
[   23.579544]   IO window: c000-cfff
[   23.579547]   MEM window: fa000000-fcffffff
[   23.579550]   PREFETCH window: e0000000-efffffff
[   23.579553] PCI: Bridge: 0000:00:05.0
[   23.579554]   IO window: a000-afff
[   23.579557]   MEM window: fde00000-fdefffff
[   23.579560]   PREFETCH window: fdd00000-fddfffff
[   23.579563] PCI: Bridge: 0000:00:06.0
[   23.579565]   IO window: e000-efff
[   23.579568]   MEM window: fdc00000-fdcfffff
[   23.579570]   PREFETCH window: fdb00000-fdbfffff
[   23.579573] PCI: Bridge: 0000:00:07.0
[   23.579575]   IO window: d000-dfff
[   23.579578]   MEM window: fd800000-fd8fffff
[   23.579580]   PREFETCH window: fdf00000-fdffffff
[   23.579584] PCI: Bridge: 0000:00:10.0
[   23.579585]   IO window: b000-bfff
[   23.579589]   MEM window: fda00000-fdafffff
[   23.579592]   PREFETCH window: fd900000-fd9fffff
[   23.579604] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   23.579612] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   23.579620] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   23.579628] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   23.579636] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   23.579644] NET: Registered protocol family 2
[   23.631250] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   23.631295] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   23.631784] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   23.631947] TCP: Hash tables configured (established 131072 bind 65536)
[   23.631949] TCP reno registered
[   23.647296] checking if image is initramfs... it is
[   24.155424] Freeing initrd memory: 7121k freed
[   24.155894] audit: initializing netlink socket (disabled)
[   24.155905] audit(1232297760.296:1): initialized
[   24.155989] highmem bounce pool size: 64 pages
[   24.157414] VFS: Disk quotas dquot_6.5.1
[   24.157451] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   24.157517] io scheduler noop registered
[   24.157519] io scheduler anticipatory registered
[   24.157521] io scheduler deadline registered
[   24.157531] io scheduler cfq registered (default)
[   24.170135] Boot video device is 0000:01:00.0
[   24.170211] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   24.170246] assign_interrupt_mode Found MSI capability
[   24.170248] Allocate Port Service[0000:00:03.0:pcie00]
[   24.170313] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   24.170347] assign_interrupt_mode Found MSI capability
[   24.170348] Allocate Port Service[0000:00:05.0:pcie00]
[   24.170411] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   24.170444] assign_interrupt_mode Found MSI capability
[   24.170446] Allocate Port Service[0000:00:06.0:pcie00]
[   24.170511] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   24.170545] assign_interrupt_mode Found MSI capability
[   24.170546] Allocate Port Service[0000:00:07.0:pcie00]
[   24.170655] isapnp: Scanning for PnP cards...
[   24.522849] isapnp: No Plug & Play device found
[   24.538369] Real Time Clock Driver v1.12ac
[   24.538530] hpet_resources: 0xfeff0000 is busy
[   24.538569] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   24.538663] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.539140] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.539666] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   24.539837] input: Macintosh mouse button emulation as /class/input/input0
[   24.539900] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   24.540402] serio: i8042 KBD port at 0x60,0x64 irq 1
[   24.540406] serio: i8042 AUX port at 0x60,0x64 irq 12
[   24.540488] mice: PS/2 mouse device common for all mice
[   24.540577] EISA: Probing bus 0 at eisa.0
[   24.540581] Cannot allocate resource for EISA slot 1
[   24.540601] EISA: Detected 0 cards.
[   24.540660] TCP cubic registered
[   24.540669] NET: Registered protocol family 1
[   24.540685] Using IPI No-Shortcut mode
[   24.540824]   Magic number: 9:907:944
[   24.540847]   hash matches device ptyyf
[   24.540865]   hash matches device tty1
[   24.541031] Freeing unused kernel memory: 364k freed
[   24.541041] Write protecting the kernel read-only data: 726k
[   24.574367] input: AT Translated Set 2 keyboard as /class/input/input1
[   25.693853] AppArmor: AppArmor initialized<5>audit(1232297761.796:2):  type=1505 info="AppArmor initialized" pid=1279
[   25.698274] fuse init (API version 7.8)
[   25.701568] Failure registering capabilities with primary security module.
[   25.733340] ACPI: Fan [FAN] (on)
[   25.736436] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   25.736444] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   25.737507] ACPI: Thermal Zone [THRM] (40 C)
[   26.115216] usbcore: registered new interface driver usbfs
[   26.115236] usbcore: registered new interface driver hub
[   26.115254] usbcore: registered new device driver usb
[   26.116276] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 23
[   26.116282] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [APCL] -> GSI 23 (level, low) -> IRQ 16
[   26.116292] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   26.116294] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   26.116403] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[   26.116421] ehci_hcd 0000:00:0b.1: debug port 1
[   26.116426] PCI: cache line size of 32 is not supported by device 0000:00:0b.1
[   26.116433] ehci_hcd 0000:00:0b.1: irq 16, io mem 0xfe02e000
[   26.116440] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   26.116508] usb usb1: configuration #1 chosen from 1 choice
[   26.116526] hub 1-0:1.0: USB hub found
[   26.116531] hub 1-0:1.0: 8 ports detected
[   26.124358] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   26.128146] SCSI subsystem initialized
[   26.163535] libata version 2.21 loaded.
[   26.167299] Floppy drive(s): fd0 is 1.44M
[   26.193428] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[   26.196146] FDC 0 is a post-1991 82077
[   26.218345] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[   26.218351] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [APCF] -> GSI 22 (level, low) -> IRQ 17
[   26.218361] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   26.218363] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   26.218383] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[   26.218397] ohci_hcd 0000:00:0b.0: irq 17, io mem 0xfe02f000
[   26.275714] usb usb2: configuration #1 chosen from 1 choice
[   26.275736] hub 2-0:1.0: USB hub found
[   26.275743] hub 2-0:1.0: 8 ports detected
[   26.380696] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   26.380699] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   26.381138] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
[   26.381153] NFORCE-MCP51: chipset revision 161
[   26.381155] NFORCE-MCP51: not 100% native mode: will probe irqs later
[   26.381161] NFORCE-MCP51: 0000:00:0d.0 (rev a1) UDMA133 controller
[   26.381166]     ide0: BM-DMA at 0xfd00-0xfd07, BIOS settings: hda:DMA, hdb:DMA
[   26.381172]     ide1: BM-DMA at 0xfd08-0xfd0f, BIOS settings: hdc:DMA, hdd:DMA
[   26.381177] Probing IDE interface ide0...
[   26.696764] usb 1-4: new high speed USB device using ehci_hcd and address 3
[   26.948233] Probing IDE interface ide1...
[   26.980198] usb 1-4: configuration #1 chosen from 1 choice
[   27.283521] usb 2-2: new full speed USB device using ohci_hcd and address 2
[   27.492168] usb 2-2: configuration #1 chosen from 1 choice
[   27.495343] usbcore: registered new interface driver libusual
[   27.499548] Initializing USB Mass Storage driver...
[   27.499604] scsi0 : SCSI emulation for USB Mass Storage devices
[   27.499634] usb-storage: device found at 3
[   27.499635] usb-storage: waiting for device to settle before scanning
[   27.499666] scsi1 : SCSI emulation for USB Mass Storage devices
[   27.499692] usb-storage: device found at 2
[   27.499693] usb-storage: waiting for device to settle before scanning
[   27.499703] usbcore: registered new interface driver usb-storage
[   27.499705] USB Mass Storage support registered.
[   27.962178] hdd: TSSTcorpCD/DVDW SH-S182D, ATAPI CD/DVD-ROM drive
[   28.018681] ide1 at 0x170-0x177,0x376 on irq 15
[   28.021721] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 21
[   28.021726] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [APCH] -> GSI 21 (level, low) -> IRQ 18
[   28.021731] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   28.021737] forcedeth: using HIGHDMA
[   28.030772] hdd: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   28.030778] Uniform CD-ROM driver Revision: 3.20
[   28.541214] eth0: forcedeth.c: subsystem: 01043:8221 bound to 0000:00:14.0
[   28.541235] sata_nv 0000:00:0e.0: version 3.4
[   28.541519] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[   28.541523] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 19
[   28.541549] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   28.541574] scsi2 : sata_nv
[   28.541604] scsi3 : sata_nv
[   28.541654] ata1: SATA max UDMA/133 cmd 0x000109f0 ctl 0x00010bf2 bmdma 0x0001f800 irq 19
[   28.541657] ata2: SATA max UDMA/133 cmd 0x00010970 ctl 0x00010b72 bmdma 0x0001f808 irq 19
[   28.852198] ata1: SATA link down (SStatus 0 SControl 300)
[   29.171522] ata2: SATA link down (SStatus 0 SControl 300)
[   29.182237] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23
[   29.182240] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [APSJ] -> GSI 23 (level, low) -> IRQ 16
[   29.182261] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   29.182280] scsi4 : sata_nv
[   29.182308] scsi5 : sata_nv
[   29.182354] ata3: SATA max UDMA/133 cmd 0x000109e0 ctl 0x00010be2 bmdma 0x0001f300 irq 16
[   29.182357] ata4: SATA max UDMA/133 cmd 0x00010960 ctl 0x00010b62 bmdma 0x0001f308 irq 16
[   29.490845] ata3: SATA link down (SStatus 0 SControl 300)
[   29.965848] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   29.995884] ata4.00: ATA-7: WDC WD1600AAJS-00PSA0, 05.06H05, max UDMA/133
[   29.995886] ata4.00: 312581808 sectors, multi 1: LBA48 NCQ (depth 0/32)
[   30.010571] ata4.00: configured for UDMA/133
[   30.010642] scsi 5:0:0:0: Direct-Access     ATA      WDC WD1600AAJS-0 05.0 PQ: 0 ANSI: 5
[   30.010980] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   30.010984] ACPI: PCI Interrupt 0000:05:08.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 20
[   30.062611] sd 5:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   30.062620] sd 5:0:0:0: [sda] Write Protect is off
[   30.062622] sd 5:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   30.062633] sd 5:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.062666] sd 5:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   30.062673] sd 5:0:0:0: [sda] Write Protect is off
[   30.062675] sd 5:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   30.062686] sd 5:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.062688]  sda:<6>ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[fdaff000-fdaff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   30.069623]  sda1 sda2 < sda5 >
[   30.094149] sd 5:0:0:0: [sda] Attached SCSI disk
[   30.097024] sd 5:0:0:0: Attached scsi generic sg0 type 0
[   30.284109] Attempting manual resume
[   30.284111] swsusp: Resume From Partition 8:5
[   30.284113] PM: Checking swsusp image.
[   30.284276] PM: Resume from disk failed.
[   30.314608] kjournald starting.  Commit interval 5 seconds
[   30.314614] EXT3-fs: mounted filesystem with ordered data mode.
[   31.335023] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d800012baa60]
[   32.488606] usb-storage: device scan complete
[   32.489654] usb-storage: device scan complete
[   32.501639] scsi 1:0:0:0: Direct-Access     Brother  MFC-240C         1.00 PQ: 0 ANSI: 2
[   32.523908] scsi 0:0:0:0: Direct-Access     HDT72252 5DLAT80          V44O PQ: 0 ANSI: 2
[   32.526266] sd 0:0:0:0: [sdb] 488393072 512-byte hardware sectors (250057 MB)
[   32.530133] sd 0:0:0:0: [sdb] Write Protect is off
[   32.530135] sd 0:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   32.530137] sd 0:0:0:0: [sdb] Assuming drive cache: write through
[   32.532254] sd 0:0:0:0: [sdb] 488393072 512-byte hardware sectors (250057 MB)
[   32.535123] sd 0:0:0:0: [sdb] Write Protect is off
[   32.535124] sd 0:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   32.535126] sd 0:0:0:0: [sdb] Assuming drive cache: write through
[   32.535129]  sdb: sdb1
[   32.546638] sd 0:0:0:0: [sdb] Attached SCSI disk
[   32.546662] sd 0:0:0:0: Attached scsi generic sg1 type 0
[   32.591456] sd 1:0:0:0: [sdc] Attached SCSI removable disk
[   32.591478] sd 1:0:0:0: Attached scsi generic sg2 type 0
[   36.672130] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   36.674839] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   36.927602] Linux agpgart interface v0.102 (c) Dave Jones
[   37.035360] nvidia: module license 'NVIDIA' taints kernel.
[   37.286268] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[   37.286275] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [APC5] -> GSI 16 (level, low) -> IRQ 21
[   37.286283] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   37.286377] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9639  Mon Apr 16 20:20:06 PDT 2007
[   37.298578] parport_pc 00:0a: reported by Plug and Play ACPI
[   37.298603] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   37.300870] input: PC Speaker as /class/input/input2
[   37.443461] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   37.443477] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c80
[   37.460329] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04F9 pid 0x01AB
[   37.460341] usbcore: registered new interface driver usblp
[   37.460343] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   37.576056] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   37.576060] ACPI: PCI Interrupt 0000:05:06.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 21
[   37.576649] cmipci: no OPL device at 0x388, skipping...
[   37.786469] lp0: using parport0 (interrupt-driven).
[   37.836647] Adding 4554388k swap on /dev/sda5.  Priority:-1 extents:1 across:4554388k
[   38.059694] EXT3 FS on sda1, internal journal
[   38.947068] No dock devices found.
[   38.994100] input: Power Button (FF) as /class/input/input3
[   38.994115] ACPI: Power Button (FF) [PWRF]
[   38.994143] input: Power Button (CM) as /class/input/input4
[   38.994153] ACPI: Power Button (CM) [PWRB]
[   39.073633] input: ImPS/2 Logitech Wheel Mouse as /class/input/input5
[   40.229452] Failure registering capabilities with primary security module.
[   41.091082] ppdev: user-space parallel port driver
[   41.950521] audit(1232297777.877:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5417 profile="/usr/sbin/cupsd"
[   44.117887] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   44.117891] apm: disabled - APM is not SMP safe.
[   46.112038] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   46.112042] vboxdrv: Successfully done.
[   46.112044] vboxdrv: Found 2 processor cores.
[   46.112087] vboxdrv: fAsync=0 offMin=0x420 offMax=0xa40
[   46.112090] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   46.112092] vboxdrv: Successfully loaded version 2.0.6 (interface 0x00090000).
[   46.714137] NET: Registered protocol family 10
[   46.714206] lo: Disabled Privacy Extensions
[   49.130973] Bluetooth: Core ver 2.11
[   49.131021] NET: Registered protocol family 31
[   49.131022] Bluetooth: HCI device and connection manager initialized
[   49.131025] Bluetooth: HCI socket layer initialized
[   49.135153] Bluetooth: L2CAP ver 2.8
[   49.135157] Bluetooth: L2CAP socket layer initialized
[   49.137553] Bluetooth: RFCOMM socket layer initialized
[   49.137562] Bluetooth: RFCOMM TTY layer initialized
[   49.137564] Bluetooth: RFCOMM ver 1.8
[   51.231543] NET: Registered protocol family 17
[   66.745439] eth0: no IPv6 routers present

```

results of lspci:
```

michael@darkmage:~$ lspci -v
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: bus master, 66MHz, fast devsel, latency 0

00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
        Flags: bus master, 66MHz, fast devsel, latency 0

00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: bus master, 66MHz, fast devsel, latency 0

00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fa000000-fcffffff
        Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
        Capabilities: <access denied>

00:05.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: fde00000-fdefffff
        Prefetchable memory behind bridge: 00000000fdd00000-00000000fddfffff
        Capabilities: <access denied>

00:06.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fdc00000-fdcfffff
        Prefetchable memory behind bridge: 00000000fdb00000-00000000fdbfffff
        Capabilities: <access denied>

00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fd800000-fd8fffff
        Prefetchable memory behind bridge: 00000000fdf00000-00000000fdffffff
        Capabilities: <access denied>

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
        Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
        Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
        Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
        Flags: 66MHz, fast devsel, IRQ 11
        I/O ports at 1c00 [size=64]
        I/O ports at 1c80 [size=64]
        Capabilities: <access denied>

00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81bc
        Flags: 66MHz, fast devsel

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at fd00 [size=16]
        Capabilities: <access denied>

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at f800 [size=16]
        Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        I/O ports at 09e0 [size=8]
        I/O ports at 0be0 [size=4]
        I/O ports at 0960 [size=8]
        I/O ports at 0b60 [size=4]
        I/O ports at f300 [size=16]
        Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=128
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: fda00000-fdafffff
        Prefetchable memory behind bridge: fd900000-fd9fffff
        Capabilities: <access denied>

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8221
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
        Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at f200 [size=8]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1) (prog-if 00 [VGA])
        Subsystem: XFX Pine Group Inc. Unknown device 2231
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at fb000000 (64-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at fcfe0000 [disabled] [size=128K]
        Capabilities: <access denied>

05:06.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
        Subsystem: C-Media Electronics Inc CMI8738/C3DX PCI Audio Device
        Flags: bus master, stepping, medium devsel, latency 32, IRQ 21
        I/O ports at bc00 [size=256]
        Capabilities: <access denied>

05:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81fe
        Flags: bus master, medium devsel, latency 32, IRQ 20
        Memory at fdaff000 (32-bit, non-prefetchable) [size=2K]
        I/O ports at bf00 [size=128]
        Capabilities: <access denied>

```

---

### Post by psychomichael on 2009-01-18
also...lsmod report:

```
michael@darkmage:~$ lsmod
Module                  Size  Used by
binfmt_misc            12936  1 
af_packet              24840  2 
rfcomm                 42136  2 
l2cap                  26112  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ipv6                  273892  16 
vboxdrv                67736  0 
ppdev                  10244  0 
cpufreq_conservative     8072  0 
cpufreq_userspace       5280  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7232  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
ac                      6148  0 
container               5504  0 
sbs                    19592  0 
video                  18060  0 
button                  8976  0 
dock                   10656  0 
battery                11012  0 
sbp2                   24072  0 
lp                     12580  0 
snd_cmipci             37024  5 
gameport               16776  1 snd_cmipci
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  4 snd_cmipci,snd_pcm_oss
snd_page_alloc         11400  1 snd_pcm
snd_opl3_lib           11520  1 snd_cmipci
snd_hwdep              10244  1 snd_opl3_lib
snd_mpu401_uart         9600  1 snd_cmipci
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
usblp                  15104  0 
i2c_nforce2             7040  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
serio_raw               8068  0 
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device          9228  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4224  0 
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
nvidia               4716468  32 
snd                    54660  20 snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                39952  0 
soundcore               8800  1 snd
agpgart                35016  1 nvidia
i2c_core               26112  2 i2c_nforce2,nvidia
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  3 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  5 
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
usb_storage            73152  1 
libusual               18448  1 usb_storage
amd74xx                15260  0 [permanent]
ide_core              116804  3 ide_cd,usb_storage,amd74xx
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
forcedeth              51592  0 
sata_nv                20612  2 
floppy                 60004  0 
ata_generic             8452  0 
libata                125168  2 sata_nv,ata_generic
scsi_mod              147084  5 sbp2,sg,sd_mod,usb_storage,libata
ohci_hcd               22916  0 
ehci_hcd               36492  0 
usbcore               138760  6 usblp,usb_storage,libusual,ohci_hcd,ehci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor

```

---

