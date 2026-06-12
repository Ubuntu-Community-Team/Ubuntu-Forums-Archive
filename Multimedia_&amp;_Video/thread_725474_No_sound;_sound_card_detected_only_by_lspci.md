---
title: "No sound; sound card detected only by lspci"
date: 2008-03-15
forum: Multimedia &amp; Video
---

### Post by ftmichael on 2008-03-15
I just installed a new motherboard - an [nForce 630i from XFX](http://www.newegg.com/Product/Product.aspx?Item=N82E16813141008).  I have no sound, and attempting to test anything in my Sound settings (GUI) gives me:

audiotestsrc wave=sine freq=512 !
audioconvert ! audioresample !
gconfaudiosink: Could not open resource for writing.

**alsamixer** from the terminal gives me:
alsamixer: function snd_ctl_open failed for default: No such device

**aplay -l** gives me:
aplay: device_list:204: no soundcards found...

**lsmod | grep snd** gives me:
```
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  1 snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  5 snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
```

**cat /proc/asound/modules** gives me nothing at all.

**lspci -v** gives me:
```
00:09.0 Audio device: nVidia Corporation Unknown device 07fc (rev a1)
        Subsystem: nVidia Corporation Unknown device 07fc
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        Memory at efff8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
```


**dmesg|less** gives me:
```
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003b000000 (usable)
[    0.000000]  BIOS-e820: 000000003b000000 - 000000003f000000 (reserved)
[    0.000000]  BIOS-e820: 000000003f000000 - 000000003fde0000 (usable)
[    0.000000]  BIOS-e820: 000000003fee0000 - 000000003fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fee3000 - 000000003fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003fef0000 - 000000003ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f2000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 125MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f4320
[    0.000000] Entering add_active_range(0, 0, 261600) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   261600
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   261600
[    0.000000] On node 0 totalpages: 261600
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 251 pages used for memmap
[    0.000000]   HighMem zone: 31973 pages, LIFO batch:7
[    0.000000] DMI 2.5 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7DF0 checksum 0
[    0.000000] ACPI: RSDP 000F7DF0, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 3FEE3040, 0038 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: FACP 3FEE30C0, 0074 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI Warning (tbfadt-0442): Optional field "Pm2ControlBlock" has zero address or length: 0000000000000000/1 [20070126]
[    0.000000] ACPI: DSDT 3FEE3180, 5D23 (r1 NVIDIA NVDAACPI     1000 MSFT  3000000)
[    0.000000] ACPI: FACS 3FEE1800, 0040
[    0.000000] ACPI: HPET 3FEE9000, 0038 (r1 Nvidia NVDAACPI 42302E31 NVDA       98)
[    0.000000] ACPI: WDRT 3FEE9080, 0047 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: MCFG 3FEE9140, 003C (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: APIC 3FEE8F00, 0098 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
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
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:b0100000)
[    0.000000] Built 1 zonelists.  Total pages: 259557
[    0.000000] Kernel command line: root=UUID=1f259c45-12f6-4cb8-9429-b58fb5d1bb12 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1600.050 MHz processor.
[   17.835665] spurious 8259A interrupt: IRQ7.
[   17.838386] Console: colour VGA+ 80x25
[   17.838767] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   17.839115] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   17.864015] Memory: 960104k/1046400k available (2015k kernel code, 20016k reserved, 915k data, 364k init, 63360k highmem)
[   17.864024] virtual kernel memory layout:
[   17.864026]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   17.864027]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   17.864028]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   17.864029]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   17.864030]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   17.864032]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   17.864033]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   17.864036] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   17.864070] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   17.864223] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[   17.864228] hpet0: 3 32-bit timers, 25000000 Hz
[   17.864228] hpet0: 3 32-bit timers, 25000000 Hz
[   17.945122] Calibrating delay using timer specific routine.. 3203.58 BogoMIPS (lpj=6407164)
[   17.945146] Security Framework v1.0.0 initialized
[   17.945152] SELinux:  Disabled at boot.
[   17.945166] Mount-cache hash table entries: 512
[   17.945293] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001
[   17.945301] monitor/mwait feature present.
[   17.945302] using mwait in idle threads.
[   17.945307] CPU: L1 I cache: 32K, L1 D cache: 32K
[   17.945310] CPU: L2 cache: 1024K
[   17.945312] CPU: Physical Processor ID: 0
[   17.945314] CPU: Processor Core ID: 0
[   17.945316] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001
[   17.945325] Compat vDSO mapped to ffffe000.
[   17.945338] Checking 'hlt' instruction... OK.
[   17.961201] SMP alternatives: switching to UP code
[   17.961620] Early unpacking initramfs... done
[   18.304195] ACPI: Core revision 20070126
[   18.304239] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   18.309352] CPU0: Intel(R) Pentium(R) Dual  CPU  E2140  @ 1.60GHz stepping 0d
[   18.309368] SMP alternatives: switching to SMP code
[   18.309446] Booting processor 1/1 eip 3000
[   18.319532] Initializing CPU#1
[   18.396409] Calibrating delay using timer specific routine.. 3200.02 BogoMIPS (lpj=6400052)
[   18.396415] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001
[   18.396420] monitor/mwait feature present.
[   18.396423] CPU: L1 I cache: 32K, L1 D cache: 32K
[   18.396425] CPU: L2 cache: 1024K
[   18.396427] CPU: Physical Processor ID: 0
[   18.396429] CPU: Processor Core ID: 1
[   18.396430] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001
[   18.396798] CPU1: Intel(R) Pentium(R) Dual  CPU  E2140  @ 1.60GHz stepping 0d
[   18.396819] Total of 2 processors activated (6403.60 BogoMIPS).
[   18.397016] ENABLING IO-APIC IRQs
[   18.397214] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   18.544261] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   18.564244] Brought up 2 CPUs
[   18.600877] migration_cost=22
[   18.600995] Booting paravirtualized kernel on bare hardware
[   18.601061] Time: 22:35:23  Date: 02/15/108
[   18.601079] NET: Registered protocol family 16
[   18.601155] EISA bus registered
[   18.601160] ACPI: bus type pci registered
[   18.685955] PCI: PCI BIOS revision 3.00 entry at 0xfa6f0, last bus=4
[   18.685957] PCI: Using configuration type 1
[   18.685959] Setting up standard PCI resources
[   18.688218] ACPI: EC: Look up EC in DSDT
[   18.695223] ACPI: Interpreter enabled
[   18.695226] ACPI: (supports S0 S3 S4 S5)
[   18.695243] ACPI: Using IOAPIC for interrupt routing
[   18.706292] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   18.706301] PCI: Probing PCI hardware (bus 00)
[   18.707920] PCI: Transparent bridge - 0000:00:0a.0
[   18.708310] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   18.708596] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   18.774122] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   18.774321] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   18.774516] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   18.774711] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   18.774908] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 *10 11 14 15)
[   18.775102] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   18.775297] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   18.775490] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   18.775684] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   18.775880] ACPI: PCI Interrupt Link [LIGP] (IRQs *5 7 9 10 11 14 15)
[   18.776079] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 *11 14 15)
[   18.776274] ACPI: PCI Interrupt Link [LUB2] (IRQs *5 7 9 10 11 14 15)
[   18.776468] ACPI: PCI Interrupt Link [LU1B] (IRQs 5 7 9 10 11 14 15) *0
[   18.776662] ACPI: PCI Interrupt Link [LU2B] (IRQs 5 7 9 10 11 14 15) *0
[   18.776856] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   18.777051] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
[   18.777247] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 *10 11 14 15)
[   18.777441] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[   18.777635] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   18.777830] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[   18.778067] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   18.778293] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   18.778518] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[   18.778744] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   18.778968] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0
[   18.779192] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[   18.779417] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[   18.779641] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[   18.779866] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0
[   18.780100] ACPI: PCI Interrupt Link [AUBA] (IRQs 20 21 22 23) *0
[   18.780326] ACPI: PCI Interrupt Link [AUB2] (IRQs 20 21 22 23) *0
[   18.780551] ACPI: PCI Interrupt Link [AU1B] (IRQs 20 21 22 23) *0
[   18.780777] ACPI: PCI Interrupt Link [AU2B] (IRQs 20 21 22 23) *0
[   18.781002] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
[   18.781228] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0
[   18.781454] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[   18.781684] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   18.781910] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[   18.782136] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   18.782362] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   18.782499] Linux Plug and Play Support v0.97 (c) Adam Belay
[   18.782510] pnp: PnP ACPI init
[   18.782520] ACPI: bus type pnp registered
[   18.787654] pnp: PnP ACPI: found 13 devices
[   18.787657] ACPI: ACPI bus type pnp unregistered
[   18.787661] PnPBIOS: Disabled by ACPI PNP
[   18.787712] PCI: Using ACPI for IRQ routing
[   18.787715] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   18.987949] NET: Registered protocol family 8
[   18.987951] NET: Registered protocol family 20
[   18.988008] pnp: 00:01: ioport range 0x1000-0x107f has been reserved
[   18.988011] pnp: 00:01: ioport range 0x1080-0x10ff has been reserved
[   18.988014] pnp: 00:01: ioport range 0x1400-0x147f has been reserved
[   18.988017] pnp: 00:01: ioport range 0x1480-0x14ff has been reserved
[   18.988020] pnp: 00:01: ioport range 0x1800-0x187f has been reserved
[   18.988023] pnp: 00:01: ioport range 0x1880-0x18ff has been reserved
[   18.988026] pnp: 00:01: iomem range 0x0-0x0 could not be reserved
[   18.988029] pnp: 00:01: iomem range 0xfefe0000-0xfefe01ff could not be reserved
[   18.988033] pnp: 00:01: iomem range 0xfefe1000-0xfefe10ff could not be reserved
[   18.988036] pnp: 00:01: iomem range 0x3b000000-0x3effffff could not be reserved
[   18.988049] pnp: 00:0b: iomem range 0xf0000000-0xf1ffffff could not be reserved
[   18.988054] pnp: 00:0c: iomem range 0xf0000-0xfffff could not be reserved
[   18.988058] pnp: 00:0c: iomem range 0xfed00000-0xfed000ff could not be reserved
[   18.988061] pnp: 00:0c: iomem range 0x3fee0000-0x3fefffff could not be reserved
[   18.988064] pnp: 00:0c: iomem range 0xffff0000-0xffffffff could not be reserved
[   18.991475] Time: tsc clocksource has been installed.
[   18.991485] Switched to high resolution mode on CPU 0
[   18.991565] Switched to high resolution mode on CPU 1
[   19.018322] PCI: Bridge: 0000:00:0a.0
[   19.018325]   IO window: b000-bfff
[   19.018329]   MEM window: ef800000-ef8fffff
[   19.018333]   PREFETCH window: ef700000-ef7fffff
[   19.018338] PCI: Bridge: 0000:00:0b.0
[   19.018340]   IO window: e000-efff
[   19.018344]   MEM window: efe00000-efefffff
[   19.018347]   PREFETCH window: efd00000-efdfffff
[   19.018352] PCI: Bridge: 0000:00:0c.0
[   19.018354]   IO window: d000-dfff
[   19.018358]   MEM window: efc00000-efcfffff
[   19.018361]   PREFETCH window: efb00000-efbfffff
[   19.018365] PCI: Bridge: 0000:00:0d.0
[   19.018367]   IO window: c000-cfff
[   19.018371]   MEM window: efa00000-efafffff
[   19.018375]   PREFETCH window: ef900000-ef9fffff
[   19.018388] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   19.018399] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   19.018410] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   19.018421] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   19.018431] NET: Registered protocol family 2
[   19.067330] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   19.067415] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   19.068242] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   19.068625] TCP: Hash tables configured (established 131072 bind 65536)
[   19.068628] TCP reno registered
[   19.083433] checking if image is initramfs... it is
[   19.762920] Freeing initrd memory: 7111k freed
[   19.763472] audit: initializing netlink socket (disabled)
[   19.763485] audit(1205620523.504:1): initialized
[   19.763576] highmem bounce pool size: 64 pages
[   19.765427] VFS: Disk quotas dquot_6.5.1
[   19.765475] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   19.765559] io scheduler noop registered
[   19.765562] io scheduler anticipatory registered
[   19.765564] io scheduler deadline registered
[   19.765578] io scheduler cfq registered (default)
[   19.778216] Boot video device is 0000:00:10.0
[   19.778307] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   19.778347] assign_interrupt_mode Found MSI capability
[   19.778350] Allocate Port Service[0000:00:0b.0:pcie00]
[   19.778429] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   19.778468] assign_interrupt_mode Found MSI capability
[   19.778470] Allocate Port Service[0000:00:0c.0:pcie00]
[   19.778546] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   19.778585] assign_interrupt_mode Found MSI capability
[   19.778588] Allocate Port Service[0000:00:0d.0:pcie00]
[   19.778720] isapnp: Scanning for PnP cards...
[   20.131198] isapnp: No Plug & Play device found
[   20.152661] Real Time Clock Driver v1.12ac
[   20.152846] hpet_resources: 0xfeff0000 is busy
[   20.152890] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   20.152986] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.153667] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.154345] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   20.154559] input: Macintosh mouse button emulation as /class/input/input0
[   20.154636] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   20.157988] serio: i8042 KBD port at 0x60,0x64 irq 1
[   20.157993] serio: i8042 AUX port at 0x60,0x64 irq 12
[   20.158111] mice: PS/2 mouse device common for all mice
[   20.158210] EISA: Probing bus 0 at eisa.0
[   20.158216] Cannot allocate resource for EISA slot 1
[   20.158239] EISA: Detected 0 cards.
[   20.158324] TCP cubic registered
[   20.158336] NET: Registered protocol family 1
[   20.158357] Using IPI No-Shortcut mode
[   20.158513]   Magic number: 0:472:603
[   20.158552]   hash matches device ptyd7
[   20.158559]   hash matches device ptyaa
[   20.158603]   hash matches device PNP0C0F:0f
[   20.158786] Freeing unused kernel memory: 364k freed
[   20.177009] input: AT Translated Set 2 keyboard as /class/input/input1
[   21.367585] AppArmor: AppArmor initialized<5>audit(1205620525.004:2):  type=1505 info="AppArmor initialized" pid=1259
[   21.375820] fuse init (API version 7.8)
[   21.381488] Failure registering capabilities with primary security module.
[   21.407348] ACPI: Fan [FAN] (on)
[   21.411830] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   21.411842] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   21.412618] ACPI Error (psargs-0355): [RTMP] Namespace lookup failure, AE_NOT_FOUND
[   21.412623] ACPI Error (psparse-0551): Method parse/execution failed [\_TZ_.THRM._TMP] (Node df8a1e28), AE_NOT_FOUND
[   21.957233] SCSI subsystem initialized
[   21.962104] libata version 2.21 loaded.
[   21.965255] ahci 0000:00:0e.0: version 2.2
[   21.965653] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[   21.965659] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 23 (level, low) -> IRQ 16
[   21.987077] usbcore: registered new interface driver usbfs
[   21.987101] usbcore: registered new interface driver hub
[   21.987122] usbcore: registered new device driver usb
[   22.006211] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   22.006217] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   22.013477] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   22.965139] ahci 0000:00:0e.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[   22.965144] ahci 0000:00:0e.0: flags: 64bit led clo pmp pio 
[   22.965150] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   22.965424] scsi0 : ahci
[   22.965655] scsi1 : ahci
[   22.965797] scsi2 : ahci
[   22.965932] scsi3 : ahci
[   22.966117] ata1: SATA max UDMA/133 cmd 0xf883c100 ctl 0x00000000 bmdma 0x00000000 irq 16
[   22.966121] ata2: SATA max UDMA/133 cmd 0xf883c180 ctl 0x00000000 bmdma 0x00000000 irq 16
[   22.966124] ata3: SATA max UDMA/133 cmd 0xf883c200 ctl 0x00000000 bmdma 0x00000000 irq 16
[   22.966128] ata4: SATA max UDMA/133 cmd 0xf883c280 ctl 0x00000000 bmdma 0x00000000 irq 16
[   23.448361] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   23.449648] ata1.00: ATAPI: PIONEER DVD-RW  DVR-212D, 1.21, max UDMA/66
[   23.605214] ata1.00: configured for UDMA/66
[   23.915617] ata2: SATA link down (SStatus 0 SControl 300)
[   24.227121] ata3: SATA link down (SStatus 0 SControl 300)
[   24.538625] ata4: SATA link down (SStatus 0 SControl 300)
[   24.544831] scsi 0:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-212D 1.21 PQ: 0 ANSI: 5
[   24.545174] NFORCE-MCP73: IDE controller at PCI slot 0000:00:08.0
[   24.545201] NFORCE-MCP73: chipset revision 161
[   24.545203] NFORCE-MCP73: not 100% native mode: will probe irqs later
[   24.545208] NFORCE-MCP73: BIOS didn't set cable bits correctly. Enabling workaround.
[   24.545214] NFORCE-MCP73: 0000:00:08.0 (rev a1) UDMA133 controller
[   24.545223]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:DMA
[   24.545233] Probing IDE interface ide0...
[   24.586963] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   24.586967] Uniform CD-ROM driver Revision: 3.20
[   24.587134] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   24.591283] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   24.830260] hda: WDC WD800BB-00HEA0, ATA DISK drive
[   25.501284] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   25.518346] ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 22
[   25.518353] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [AUBA] -> GSI 22 (level, low) -> IRQ 17
[   25.518366] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   25.518369] ohci_hcd 0000:00:04.0: OHCI Host Controller
[   25.518504] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 1
[   25.518521] ohci_hcd 0000:00:04.0: irq 17, io mem 0xeffff000
[   25.575077] usb usb1: configuration #1 chosen from 1 choice
[   25.575104] hub 1-0:1.0: USB hub found
[   25.575112] hub 1-0:1.0: 10 ports detected
[   25.677397] ACPI: PCI Interrupt Link [AUB2] enabled at IRQ 21
[   25.677405] ACPI: PCI Interrupt 0000:00:04.1[B] -> Link [AUB2] -> GSI 21 (level, low) -> IRQ 18
[   25.677418] PCI: Setting latency timer of device 0000:00:04.1 to 64
[   25.677422] ehci_hcd 0000:00:04.1: EHCI Host Controller
[   25.677451] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[   25.677475] ehci_hcd 0000:00:04.1: debug port 1
[   25.677480] PCI: cache line size of 32 is not supported by device 0000:00:04.1
[   25.677490] ehci_hcd 0000:00:04.1: irq 18, io mem 0xefffe000
[   25.677498] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   25.677580] usb usb2: configuration #1 chosen from 1 choice
[   25.677606] hub 2-0:1.0: USB hub found
[   25.677612] hub 2-0:1.0: 10 ports detected
[   25.787509] hda: max request size: 128KiB
[   25.792670] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[   25.792759] hda: cache flushes supported
[   25.792797]  hda: hda1 hda2 < hda5 >
[   26.085443] Attempting manual resume
[   26.085447] swsusp: Resume From Partition 3:5
[   26.085449] PM: Checking swsusp image.
[   26.085616] PM: Resume from disk failed.
[   26.131781] kjournald starting.  Commit interval 5 seconds
[   26.131787] EXT3-fs: mounted filesystem with ordered data mode.
[   26.379701] usb 1-1: new full speed USB device using ohci_hcd and address 2
[   26.591479] usb 1-1: configuration #1 chosen from 1 choice
[   36.428106] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   36.430687] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   36.502660] Linux agpgart interface v0.102 (c) Dave Jones
[   36.576828] input: PC Speaker as /class/input/input2
[   37.044427] nvidia: module license 'NVIDIA' taints kernel.
[   37.297132] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[   37.297139] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [APC5] -> GSI 16 (level, low) -> IRQ 19
[   37.297153] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   37.297174] sky2 0000:03:00.0: v1.18 addr 0xefcfc000 irq 19 Yukon-EC Ultra (0xb4) rev 3
[   37.297309] sky2 eth0: addr 00:e0:61:09:12:e3
[   37.297677] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 20
[   37.297683] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [AIGP] -> GSI 20 (level, low) -> IRQ 20
[   37.297693] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   37.297828] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   37.305460] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   37.307936] Linux video capture interface: v2.00
[   37.403730] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(SPCA561A)
[   37.417642] usbcore: registered new interface driver gspca
[   37.417647] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
[   37.651063] lp: driver loaded but no devices found
[   37.695334] Adding 1413680k swap on /dev/hda5.  Priority:-1 extents:1 across:1413680k
[   38.090544] EXT3 FS on hda1, internal journal
[   41.045653] input: Power Button (FF) as /class/input/input4
[   41.045671] ACPI: Power Button (FF) [PWRF]
[   41.045717] input: Power Button (CM) as /class/input/input5
[   41.045736] ACPI: Power Button (CM) [PWRB]
[   41.168570] No dock devices found.
[   43.006884] sky2 eth2: enabling interface
[   43.222003] NET: Registered protocol family 10
[   43.222187] lo: Disabled Privacy Extensions
[   43.222289] ADDRCONF(NETDEV_UP): eth2: link is not ready
[   43.485218] ppdev: user-space parallel port driver
[   43.825244] audit(1205620547.993:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4876 profile="/usr/sbin/cupsd"
[   43.928774] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   43.928779] apm: disabled - APM is not SMP safe.
[   44.828102] sky2 eth2: Link is up at 100 Mbps, full duplex, flow control both
[   44.830386] ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready
[   45.526012] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   45.722153] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   45.801825] NFSD: starting 90-second grace period
[   48.038512] Failure registering capabilities with primary security module.
[   48.496601] Bluetooth: Core ver 2.11
[   48.496718] NET: Registered protocol family 31
[   48.496721] Bluetooth: HCI device and connection manager initialized
[   48.496724] Bluetooth: HCI socket layer initialized
[   48.504206] Bluetooth: L2CAP ver 2.8
[   48.504211] Bluetooth: L2CAP socket layer initialized
[   48.560078] Bluetooth: RFCOMM socket layer initialized
[   48.560092] Bluetooth: RFCOMM TTY layer initialized
[   48.560094] Bluetooth: RFCOMM ver 1.8
[   53.223302] NET: Registered protocol family 17
[   64.395019] eth2: no IPv6 routers present
[46756.540263] Bad page state in process 'swapper'
[46756.540265] page:c10c9760 flags:0x40000000 mapping:00000000 mapcount:-1024 count:0
[46756.540266] Trying to fix it up, but a reboot is needed
[46756.540268] Backtrace:
[46756.540284]  [<c01628f3>] bad_page+0x63/0xa0
[46756.540296]  [<c0162e8f>] free_hot_cold_page+0x16f/0x180
[46756.540301]  [<c01317e7>] lock_timer_base+0x27/0x60
[46756.540309]  [<c02c10a0>] tcp_v4_destroy_sock+0x1c0/0x230
[46756.540315]  [<c02ad8b7>] inet_csk_destroy_sock+0x47/0x160
[46756.540320]  [<c02ae000>] inet_csk_clear_xmit_timers+0x30/0x40
[46756.540326]  [<c02aeb9d>] tcp_done+0x8d/0x120
[46756.540331]  [<c02b9061>] tcp_rcv_state_process+0x9d1/0xc60
[46756.540338]  [<c02bfdaa>] tcp_v4_do_rcv+0x13a/0x6e0
[46756.540343]  [<c02a1579>] ip_route_input+0x39/0xd30
[46756.540348]  [<c017b173>] add_partial+0x13/0x40
[46756.540354]  [<c017bf01>] __slab_free+0x111/0x2a0
[46756.540361]  [<f9552924>] _nv004184rm+0x24/0x70 [nvidia]
[46756.540530]  [<c02c2acd>] tcp_v4_rcv+0x81d/0x990
[46756.540535]  [<f9527488>] _nv008106rm+0x70/0x95 [nvidia]
[46756.540687]  [<c02a4c72>] ip_local_deliver+0x122/0x2c0
[46756.540693]  [<c02a489a>] ip_rcv+0x2ea/0x5a0
[46756.540699]  [<f8d3c4aa>] packet_rcv_spkt+0x10a/0x1c0 [af_packet]
[46756.540707]  [<c0284117>] netif_receive_skb+0x237/0x400
[46756.540715]  [<f89b2663>] sky2_poll+0x4b3/0xd90 [sky2]
[46756.540723]  [<f9607125>] os_release_sema+0x45/0x70 [nvidia]
[46756.540856]  [<c0286418>] net_rx_action+0xc8/0x210
[46756.540863]  [<c012d6b2>] __do_softirq+0x82/0x110
[46756.540869]  [<c012d795>] do_softirq+0x55/0x60
[46756.540873]  [<c012da7d>] irq_exit+0x6d/0x80
[46756.540876]  [<c0106b20>] do_IRQ+0x40/0x70
[46756.540880]  [<c0140e56>] getnstimeofday+0x36/0xd0
[46756.540886]  [<c0105223>] common_interrupt+0x23/0x30
[46756.540893]  [<c01022b6>] mwait_idle_with_hints+0x46/0x60
[46756.540898]  [<c01022d0>] mwait_idle+0x0/0x20
[46756.540902]  [<c0102413>] cpu_idle+0x53/0xe0
[46756.540907]  [<c03e3a85>] start_kernel+0x325/0x3b0
[46756.540912]  [<c03e31f0>] unknown_bootoption+0x0/0x260
[46756.540919]  =======================
[54923.186114] usb 2-10: new high speed USB device using ehci_hcd and address 3
[54923.366309] usb 2-10: configuration #2 chosen from 1 choice
[54923.643447] usbcore: registered new interface driver libusual
[54923.692806] Initializing USB Mass Storage driver...
[54923.693536] scsi4 : SCSI emulation for USB Mass Storage devices
[54923.694185] usb-storage: device found at 3
[54923.694190] usb-storage: waiting for device to settle before scanning
[54923.694506] usbcore: registered new interface driver usb-storage
[54923.694672] USB Mass Storage support registered.
[54928.685424] usb-storage: device scan complete
[54928.687068] scsi 4:0:0:0: Direct-Access     TOSHIBA  MK4004GAH        JC00 PQ: 0 ANSI: 0 CCS
[54928.687394] scsi 4:0:0:0: Attached scsi generic sg1 type 0
[54928.721481] sd 4:0:0:0: [sda] 78126048 512-byte hardware sectors (40001 MB)
[54928.724342] sd 4:0:0:0: [sda] Write Protect is off
[54928.724345] sd 4:0:0:0: [sda] Mode Sense: 00 4a 00 00
[54928.724348] sd 4:0:0:0: [sda] Assuming drive cache: write through
[54928.726463] sd 4:0:0:0: [sda] 78126048 512-byte hardware sectors (40001 MB)
[54928.729208] sd 4:0:0:0: [sda] Write Protect is off
[54928.729211] sd 4:0:0:0: [sda] Mode Sense: 00 4a 00 00
[54928.729214] sd 4:0:0:0: [sda] Assuming drive cache: write through
[54928.729217]  sda: sda1
[54928.792874] sd 4:0:0:0: [sda] Attached SCSI disk
[54972.613188] usb 2-10: USB disconnect, address 3
[61231.114853] Bad page state in process 'apt-cache'
[61231.114855] page:c135f800 flags:0x40000000 mapping:00000000 mapcount:-1024 count:0
[61231.114857] Trying to fix it up, but a reboot is needed
[61231.114858] Backtrace:
[61231.114914]  [<c01628f3>] bad_page+0x63/0xa0
[61231.114936]  [<c0163613>] get_page_from_freelist+0x343/0x3a0
[61231.114960]  [<c01636bf>] __alloc_pages+0x4f/0x340
[61231.114967]  [<c013972e>] __rcu_process_callbacks+0x11e/0x1d0
[61231.114979]  [<c0172e5d>] anon_vma_prepare+0x1d/0xe0
[61231.114985]  [<c0165d86>] __pagevec_lru_add_active+0xb6/0xd0
[61231.114994]  [<c016d477>] __handle_mm_fault+0x8c7/0xb00
[61231.115003]  [<c012da61>] irq_exit+0x51/0x80
[61231.115007]  [<c0118735>] smp_apic_timer_interrupt+0x55/0x80
[61231.115028]  [<c02f5c96>] do_page_fault+0x126/0x690
[61231.115050]  [<c02f5b70>] do_page_fault+0x0/0x690
[61231.115056]  [<c02f43f2>] error_code+0x72/0x80
[61231.115067]  [<c02f0000>] clip_ioctl+0x3a0/0x510
[61231.115079]  =======================
[63362.997659] usb 2-10: new high speed USB device using ehci_hcd and address 4
[63363.177760] usb 2-10: configuration #2 chosen from 1 choice
[63363.177881] scsi5 : SCSI emulation for USB Mass Storage devices
[63363.178029] usb-storage: device found at 4
[63363.178032] usb-storage: waiting for device to settle before scanning
[63368.169507] usb-storage: device scan complete
[63368.171260] scsi 5:0:0:0: Direct-Access     TOSHIBA  MK4004GAH        JC00 PQ: 0 ANSI: 0 CCS
[63368.173609] sd 5:0:0:0: [sda] 78126048 512-byte hardware sectors (40001 MB)
[63368.177356] sd 5:0:0:0: [sda] Write Protect is off
[63368.177360] sd 5:0:0:0: [sda] Mode Sense: 00 4a 00 00
[63368.177363] sd 5:0:0:0: [sda] Assuming drive cache: write through
[63368.178985] sd 5:0:0:0: [sda] 78126048 512-byte hardware sectors (40001 MB)
[63368.181358] sd 5:0:0:0: [sda] Write Protect is off
[63368.181363] sd 5:0:0:0: [sda] Mode Sense: 00 4a 00 00
[63368.181366] sd 5:0:0:0: [sda] Assuming drive cache: write through
[63368.181371]  sda: sda1
[63368.253833] sd 5:0:0:0: [sda] Attached SCSI disk
[63368.253873] sd 5:0:0:0: Attached scsi generic sg1 type 0
[63438.338206] usb 2-10: USB disconnect, address 4
[72325.277512] usb 2-10: new high speed USB device using ehci_hcd and address 5
[72325.457842] usb 2-10: configuration #2 chosen from 1 choice
[72325.458076] scsi6 : SCSI emulation for USB Mass Storage devices
[72325.458225] usb-storage: device found at 5
[72325.458227] usb-storage: waiting for device to settle before scanning
[72330.449327] usb-storage: device scan complete
[72330.450576] scsi 6:0:0:0: Direct-Access     TOSHIBA  MK4004GAH        JC00 PQ: 0 ANSI: 0 CCS
[72330.453250] sd 6:0:0:0: [sda] 78126048 512-byte hardware sectors (40001 MB)
[72330.454923] sd 6:0:0:0: [sda] Write Protect is off
[72330.454927] sd 6:0:0:0: [sda] Mode Sense: 00 4a 00 00
[72330.454929] sd 6:0:0:0: [sda] Assuming drive cache: write through
[72330.457042] sd 6:0:0:0: [sda] 78126048 512-byte hardware sectors (40001 MB)
[72330.459925] sd 6:0:0:0: [sda] Write Protect is off
[72330.459930] sd 6:0:0:0: [sda] Mode Sense: 00 4a 00 00
[72330.459933] sd 6:0:0:0: [sda] Assuming drive cache: write through
[72330.459938]  sda: sda1
[72330.528797] sd 6:0:0:0: [sda] Attached SCSI disk
[72330.528847] sd 6:0:0:0: Attached scsi generic sg1 type 0
[72345.807545] usb 2-10: USB disconnect, address 5
(END)
```

Thoughts?

**ETA:** This seems to be a bug. [https://bugs.launchpad.net/ubuntu/+bug/195139](https://bugs.launchpad.net/ubuntu/+bug/195139)  Anyone have any fixes or workarounds?  Is it likely to be fixed in Hardy?

Michael

---

### Post by ftmichael on 2008-03-16
Bump.

---

### Post by kilgor3 on 2008-03-17
bump

---

