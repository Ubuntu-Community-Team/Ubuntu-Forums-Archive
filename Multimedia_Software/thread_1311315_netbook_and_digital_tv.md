---
title: "netbook and digital tv"
date: 2009-11-02
forum: Multimedia Software
---

### Post by rajanm1 on 2009-11-02
i have a dell mini 9 netbook with ubuntu 8 and 2 different types of digital tv tuners. i would just like either one to work so i can watch live digital tv (freeview) here in the uk.
they are a hauppauge wintv nova-t digital tv stick and a cheaper kworld dvbt usb one.

thanks

---

### Post by xc3RnbFO8P on 2009-11-02
You can start with hauppauge wintv nova-t,
in Terminal show the output of:
> lsusb
and 
> dmesg

---

### Post by rajanm1 on 2009-11-02
lsusb gives:

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 2040:7060 Hauppauge 
Bus 005 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 064e:a102 Suyin Corp. 

and dmesg gives:

[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 118MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f7fa0
[    0.000000] Entering add_active_range(0, 0, 259792) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   259792
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   259792
[    0.000000] On node 0 totalpages: 259792
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 237 pages used for memmap
[    0.000000]   HighMem zone: 30179 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7F70 checksum 0
[    0.000000] ACPI: RSDP 000F7F70, 0024 (r2 PTLTD )
[    0.000000] ACPI: XSDT 3F6DBED2, 006C (r1 PTLTD       XSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 3F6E1D48, 00F4 (r3 INTEL  CALISTGA  6040000 ALAN        1)
[    0.000000] ACPI: DSDT 3F6DCDB7, 4F1D (r1 INTEL  CALISTGA  6040000 INTL 20050624)
[    0.000000] ACPI: FACS 3F6E2FC0, 0040
[    0.000000] ACPI: APIC 3F6E1E3C, 0068 (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: HPET 3F6E1EA4, 0038 (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: MCFG 3F6E1EDC, 003C (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: TCPA 3F6E1F18, 0032 (r1 PTLTD  CALISTGA  6040000  PTL        1)
[    0.000000] ACPI: TMOR 3F6E1F4A, 0026 (r1 PTLTD            6040000 PTL         3)
[    0.000000] ACPI: APIC 3F6E1F70, 0068 (r1 PTLTD       APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 3F6E1FD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT 3F6DBF3E, 04F6 (r2  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify [email]linux-acpi@vger.kernel.org[/email]
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 7:12 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 7:12 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257763
[    0.000000] Kernel command line: ro root=UUID=9ae7c327-c83e-4e54-9a76-726750345669 ht=on hpet=disabled quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1596.115 MHz processor.
[    8.125309] Console: colour VGA+ 80x25
[    8.125315] console [tty0] enabled
[    8.125669] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    8.126451] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    8.168382] Memory: 1021596k/1039168k available (3015k kernel code, 16880k reserved, 1301k data, 296k init, 121664k highmem)
[    8.168398] virtual kernel memory layout:
[    8.168400]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[    8.168402]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    8.168404]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    8.168406]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    8.168409]       .init : 0xc053e000 - 0xc0588000   ( 296 kB)
[    8.168411]       .data : 0xc03f1cf5 - 0xc05374bc   (1301 kB)
[    8.168413]       .text : 0xc0100000 - 0xc03f1cf5   (3015 kB)
[    8.168419] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    8.168487] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[    8.248453] Calibrating delay using timer specific routine.. 3196.68 BogoMIPS (lpj=6393372)
[    8.248498] Security Framework initialized
[    8.248506] SELinux:  Disabled at boot.
[    8.248532] AppArmor: AppArmor initialized
[    8.248538] Failure registering capabilities with primary security module.
[    8.248553] Mount-cache hash table entries: 512
[    8.248740] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0040c39d 00000000 00000001 00000000
[    8.248756] monitor/mwait feature present.
[    8.248759] using mwait in idle threads.
[    8.248765] CPU: L1 I cache: 32K, L1 D cache: 24K
[    8.248769] CPU: L2 cache: 512K
[    8.248774] CPU: Physical Processor ID: 0
[    8.248779] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00043940 0040c39d 00000000 00000001 00000000
[    8.248790] Intel machine check architecture supported.
[    8.248796] Intel machine check reporting enabled on CPU#0.
[    8.248803] Compat vDSO mapped to ffffe000.
[    8.248821] Checking 'hlt' instruction... OK.
[    8.264902] SMP alternatives: switching to UP code
[    8.267069] Early unpacking initramfs... done
[    8.467067] ACPI: Core revision 20070126
[    8.467172] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    8.476468] CPU0: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[    8.476497] SMP alternatives: switching to SMP code
[    8.477199] Booting processor 1/1 eip 3000
[    8.487229] Initializing CPU#1
[    8.564169] Calibrating delay using timer specific routine.. 3192.20 BogoMIPS (lpj=6384410)
[    8.564183] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0040c39d 00000000 00000001 00000000
[    8.564194] monitor/mwait feature present.
[    8.564201] CPU: L1 I cache: 32K, L1 D cache: 24K
[    8.564206] CPU: L2 cache: 512K
[    8.564210] CPU: Physical Processor ID: 0
[    8.564215] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00043940 0040c39d 00000000 00000001 00000000
[    8.564225] Intel machine check architecture supported.
[    8.564232] Intel machine check reporting enabled on CPU#1.
[    8.564522] CPU1: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[    8.564564] Total of 2 processors activated (6388.89 BogoMIPS).
[    8.564771] ENABLING IO-APIC IRQs
[    8.564992] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    8.712263] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    8.732266] Brought up 2 CPUs
[    8.732309] CPU0 attaching sched-domain:
[    8.732314]  domain 0: span 03
[    8.732317]   groups: 01 02
[    8.732323]   domain 1: span 03
[    8.732326]    groups: 03
[    8.732330] CPU1 attaching sched-domain:
[    8.732333]  domain 0: span 03
[    8.732336]   groups: 02 01
[    8.732341]   domain 1: span 03
[    8.732344]    groups: 03
[    8.732733] net_namespace: 64 bytes
[    8.732745] Booting paravirtualized kernel on bare hardware
[    8.733710] Time: 19:31:43  Date: 11/02/09
[    8.733803] NET: Registered protocol family 16
[    8.734163] No dock devices found.
[    8.734338] ACPI: bus type pci registered
[    8.735162] PCI: PCI BIOS revision 3.00 entry at 0xfde5f, last bus=5
[    8.735168] PCI: Using configuration type 1
[    8.735181] Setting up standard PCI resources
[    8.740009] ACPI: EC: Look up EC in DSDT
[    8.742698] ACPI: BIOS _OSI(Linux) query ignored
[    8.742704] ACPI: DMI System Vendor: Dell Inc.
[    8.742707] ACPI: DMI Product Name: Inspiron 910
[    8.742710] ACPI: DMI Product Version: A05
[    8.742713] ACPI: DMI Board Name: CN0J14
[    8.742716] ACPI: DMI BIOS Vendor: Dell Inc.
[    8.742719] ACPI: DMI BIOS Date: 03/05/2009
[    8.742722] ACPI: Please send DMI info above to [email]linux-acpi@vger.kernel.org[/email]
[    8.742726] ACPI: If "acpi_osi=Linux" works better, please notify [email]linux-acpi@vger.kernel.org[/email]
[    8.743607] ACPI: Interpreter enabled
[    8.743612] ACPI: (supports S0 S3 S4 S5)
[    8.743638] ACPI: Using IOAPIC for interrupt routing
[    8.744683] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    8.846155] ACPI: Device [J380] status [0000000a]: functional but not present; setting present
[    8.892868] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    8.892876] ACPI: EC: driver started in interrupt mode
[    8.892959] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    8.893895] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    8.893902] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[    8.895768] PCI: Transparent bridge - 0000:00:1e.0
[    8.895823] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    8.896421] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    8.896686] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    8.896934] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    8.897207] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    8.910924] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    8.911128] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    8.911325] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    8.911523] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    8.911721] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    8.911930] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    8.912135] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    8.912334] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    8.912669] ACPI: WMI: Mapper loaded
[    8.912675] Linux Plug and Play Support v0.97 (c) Adam Belay
[    8.912738] pnp: PnP ACPI init
[    8.912752] ACPI: bus type pnp registered
[    8.932197] pnp: PnP ACPI: found 11 devices
[    8.932203] ACPI: ACPI bus type pnp unregistered
[    8.932546] SCSI subsystem initialized
[    8.932621] libata version 3.00 loaded.
[    8.932935] usbcore: registered new interface driver usbfs
[    8.933008] usbcore: registered new interface driver hub
[    8.933089] usbcore: registered new device driver usb
[    8.933709] PCI: Using ACPI for IRQ routing
[    8.933716] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.028003] NET: Registered protocol family 8
[    9.028007] NET: Registered protocol family 20
[    9.028119] AppArmor: AppArmor Filesystem Enabled
[    9.031773] Time: tsc clocksource has been installed.
[    9.048047] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[    9.048054] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[    9.048060] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[    9.048066] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[    9.048072] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[    9.048077] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
[    9.048083] system 00:01: iomem range 0xfed40000-0xfed44fff could not be reserved
[    9.048089] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
[    9.048103] system 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[    9.048114] system 00:06: ioport range 0x680-0x69f has been reserved
[    9.048120] system 00:06: ioport range 0x800-0x80f has been reserved
[    9.048125] system 00:06: ioport range 0x1000-0x107f has been reserved
[    9.048130] system 00:06: ioport range 0x1180-0x11bf has been reserved
[    9.048135] system 00:06: ioport range 0x1640-0x164f has been reserved
[    9.048140] system 00:06: ioport range 0xfe00-0xfe7f has been reserved
[    9.048146] system 00:06: ioport range 0xff00-0xff7f has been reserved
[    9.048156] system 00:07: ioport range 0x6a0-0x6af has been reserved
[    9.048161] system 00:07: ioport range 0x6b0-0x6ff has been reserved
[    9.083526] PCI: Bridge: 0000:00:1c.0
[    9.083530]   IO window: disabled.
[    9.083539]   MEM window: f0100000-f01fffff
[    9.083546]   PREFETCH window: 50000000-500fffff
[    9.083554] PCI: Bridge: 0000:00:1c.1
[    9.083556]   IO window: disabled.
[    9.083564]   MEM window: f0200000-f02fffff
[    9.083570]   PREFETCH window: disabled.
[    9.083578] PCI: Bridge: 0000:00:1c.2
[    9.083583]   IO window: 2000-2fff
[    9.083591]   MEM window: 50100000-501fffff
[    9.083597]   PREFETCH window: f0600000-f06fffff
[    9.083604] PCI: Bridge: 0000:00:1e.0
[    9.083607]   IO window: disabled.
[    9.083614]   MEM window: disabled.
[    9.083619]   PREFETCH window: disabled.
[    9.083666] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[    9.083677] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    9.083707] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[    9.083716] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    9.083748] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[    9.083757] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    9.083774] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    9.083795] NET: Registered protocol family 2
[    9.120027] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    9.120483] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    9.121528] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    9.122080] TCP: Hash tables configured (established 131072 bind 65536)
[    9.122086] TCP reno registered
[    9.132165] checking if image is initramfs... it is
[    9.519431] Freeing initrd memory: 2725k freed
[    9.519712] Simple Boot Flag at 0x36 set to 0x80
[    9.520928] audit: initializing netlink socket (disabled)
[    9.520951] audit(1257190303.228:1): initialized
[    9.521218] highmem bounce pool size: 64 pages
[    9.525001] VFS: Disk quotas dquot_6.5.1
[    9.525152] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    9.526049] io scheduler noop registered
[    9.526054] io scheduler anticipatory registered
[    9.526058] io scheduler deadline registered
[    9.526172] io scheduler cfq registered (default)
[    9.526191] Boot video device is 0000:00:02.0
[    9.526493] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    9.526559] assign_interrupt_mode Found MSI capability
[    9.526618] Allocate Port Service[0000:00:1c.0:pcie00]
[    9.526688] Allocate Port Service[0000:00:1c.0:pcie02]
[    9.526830] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    9.526895] assign_interrupt_mode Found MSI capability
[    9.526947] Allocate Port Service[0000:00:1c.1:pcie00]
[    9.527013] Allocate Port Service[0000:00:1c.1:pcie02]
[    9.527156] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    9.527220] assign_interrupt_mode Found MSI capability
[    9.527274] Allocate Port Service[0000:00:1c.2:pcie00]
[    9.527355] Allocate Port Service[0000:00:1c.2:pcie02]
[    9.535272] ACPI: AC Adapter [ACAD] (off-line)
[    9.583290] Switched to high resolution mode on CPU 0
[    9.583485] Switched to high resolution mode on CPU 1
[    9.935051] ACPI: Battery Slot [BAT1] (battery present)
[    9.935394] input: Power Button (FF) as /devices/virtual/input/input0
[    9.935401] ACPI: Power Button (FF) [PWRF]
[    9.935518] input: Lid Switch as /devices/virtual/input/input1
[    9.935606] ACPI: Lid Switch [LID0]
[    9.935722] input: Power Button (CM) as /devices/virtual/input/input2
[    9.935729] ACPI: Power Button (CM) [PWRB]
[    9.935846] input: Sleep Button (CM) as /devices/virtual/input/input3
[    9.935851] ACPI: Sleep Button (CM) [SLPB]
[    9.954304] ACPI: device:01 is registered as cooling_device0
[    9.954670] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input4
[    9.954678] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    9.955399] ACPI: SSDT 3F6DCA9E, 0245 (r2  PmRef  Cpu0Ist     3000 INTL 20050624)
[    9.955743] ACPI: SSDT 3F6DC434, 05E5 (r2  PmRef  Cpu0Cst     3001 INTL 20050624)
[    9.956484] Monitor-Mwait will be used to enter C-1 state
[    9.956489] Monitor-Mwait will be used to enter C-2 state
[    9.956494] Monitor-Mwait will be used to enter C-3 state
[    9.956605] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    9.956690] ACPI: ACPI0007:00 is registered as cooling_device1
[    9.956698] ACPI: Processor [CPU0] (supports 8 throttling states)
[    9.966053] ACPI: SSDT 3F6DCCE3, 00D4 (r2  PmRef  Cpu1Ist     3000 INTL 20050624)
[    9.966374] ACPI: SSDT 3F6DCA19, 0085 (r2  PmRef  Cpu1Cst     3000 INTL 20050624)
[    9.967318] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    9.967400] ACPI: ACPI0007:01 is registered as cooling_device2
[    9.967408] ACPI: Processor [CPU1] (supports 8 throttling states)
[    9.999115] ACPI: LNXTHERM:01 is registered as thermal_zone0
[   10.008209] ACPI: Thermal Zone [TZ01] (32 C)
[   10.131612] Real Time Clock Driver v1.12ac
[   10.131982] hpet_acpi_add: no address or irqs in _CRS
[   10.132011] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   10.134213] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   10.134817] loop: module loaded
[   10.134902] Driver 'sd' needs updating - please use bus_type methods
[   10.134966] Driver 'sr' needs updating - please use bus_type methods
[   10.135164] ata_piix 0000:00:1f.1: version 2.12
[   10.135194] ACPI: PCI Interrupt 0000:00:1f.1[B] -> GSI 19 (level, low) -> IRQ 19
[   10.135246] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   10.135362] scsi0 : ata_piix
[   10.135495] scsi1 : ata_piix
[   10.136532] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[   10.136538] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[   10.299197] ata1.00: ATA-6: STEC PATA 8GB, E5221-10, max UDMA/133
[   10.299203] ata1.00: 15005088 sectors, multi 1: LBA 
[   10.307069] ata1.00: configured for UDMA/100
[   10.307127] ata2: port disabled. ignoring.
[   10.307337] scsi 0:0:0:0: Direct-Access     ATA      STEC PATA 8GB    E522 PQ: 0 ANSI: 5
[   10.307596] sd 0:0:0:0: [sda] 15005088 512-byte hardware sectors (7683 MB)
[   10.307625] sd 0:0:0:0: [sda] Write Protect is off
[   10.307632] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   10.307679] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   10.307775] sd 0:0:0:0: [sda] 15005088 512-byte hardware sectors (7683 MB)
[   10.307805] sd 0:0:0:0: [sda] Write Protect is off
[   10.307811] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   10.307857] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   10.307864]  sda: sda1 sda2
[   10.308454] sd 0:0:0:0: [sda] Attached SCSI disk
[   10.308592] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   10.308994] USB Universal Host Controller Interface driver v3.0
[   10.309103] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   10.309118] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   10.309125] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   10.309292] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   10.309333] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001820
[   10.309666] usb usb1: configuration #1 chosen from 1 choice
[   10.309749] hub 1-0:1.0: USB hub found
[   10.309761] hub 1-0:1.0: 2 ports detected
[   10.410648] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   10.410663] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   10.410670] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   10.410836] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   10.410877] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[   10.411149] usb usb2: configuration #1 chosen from 1 choice
[   10.411232] hub 2-0:1.0: USB hub found
[   10.411244] hub 2-0:1.0: 2 ports detected
[   10.514539] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   10.514558] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   10.514564] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   10.514722] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   10.514762] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[   10.515031] usb usb3: configuration #1 chosen from 1 choice
[   10.515116] hub 3-0:1.0: USB hub found
[   10.515128] hub 3-0:1.0: 2 ports detected
[   10.618452] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[   10.618467] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   10.618473] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   10.618629] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   10.618669] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[   10.618947] usb usb4: configuration #1 chosen from 1 choice
[   10.619029] hub 4-0:1.0: USB hub found
[   10.619040] hub 4-0:1.0: 2 ports detected
[   10.722362] Initializing USB Mass Storage driver...
[   10.722447] usbcore: registered new interface driver usb-storage
[   10.722453] USB Mass Storage support registered.
[   10.722526] usbcore: registered new interface driver libusual
[   10.722761] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   10.725851] i8042_command I8042_CMD_KBD_DISABLE OK
[   10.757174] i8042_command I8042_CMD_KBD_ENABLE OK
[   10.761574] serio: i8042 KBD port at 0x60,0x64 irq 1
[   10.761584] serio: i8042 AUX port at 0x60,0x64 irq 12
[   10.761804] mice: PS/2 mouse device common for all mice
[   10.834405] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   10.854282] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input6
[   10.909793] cpuidle: using governor ladder
[   11.909741] cpuidle: using governor menu
[   11.909809] sdhci: Secure Digital Host Controller Interface driver
[   11.909815] sdhci: Copyright(c) Pierre Ossman
[   11.909909] sdhci: SDHCI controller found at 0000:02:00.2 [197b:2381] (rev 0)
[   11.909956] ACPI: PCI Interrupt 0000:02:00.2[A] -> GSI 16 (level, low) -> IRQ 17
[   11.909992] PCI: Setting latency timer of device 0000:02:00.2 to 64
[   11.910132] mmc0: SDHCI at 0xf0100400 irq 17 DMA
[   11.913539] ACPI: PCI Interrupt 0000:02:00.3[A] -> GSI 16 (level, low) -> IRQ 17
[   11.913553] PCI: Setting latency timer of device 0000:02:00.3 to 64
[   11.913927] NET: Registered protocol family 1
[   11.914389] NET: Registered protocol family 10
[   11.914729] lo: Disabled Privacy Extensions
[   11.915294] NET: Registered protocol family 17
[   11.915335] Using IPI No-Shortcut mode
[   11.915548]   Magic number: 1:673:545
[   11.915881] Freeing unused kernel memory: 296k freed
[   12.097041] mmc0: new SDHC card at address 8b5a
[   12.097381] mmcblk0: mmc0:8b5a SD16G 15663104KiB 
[   12.097455]  mmcblk0: p1
[   12.304921] usbcore: registered new interface driver hiddev
[   12.305002] usbcore: registered new interface driver usbhid
[   12.305009] /build/buildd/linux-2.6.24/debian/build/custom-source-lpia/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   12.321955] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[   12.321983] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   12.321994] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   12.322204] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   12.326152] ehci_hcd 0000:00:1d.7: debug port 1
[   12.326169] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   12.326182] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xf0544000
[   12.341734] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   12.342027] usb usb5: configuration #1 chosen from 1 choice
[   12.342126] hub 5-0:1.0: USB hub found
[   12.342140] hub 5-0:1.0: 8 ports detected
[   12.517228] Registering unionfs 1.4
[   12.517234] unionfs: debugging is not enabled
[   12.525232] squashfs: version 3.3 (2007/10/31) Phillip Lougher
[   12.611236] fuse init (API version 7.9)
[   12.697401] usb 5-2: new high speed USB device using ehci_hcd and address 2
[   12.868499] usb 5-2: configuration #1 chosen from 1 choice
[   14.031436] kjournald starting.  Commit interval 5 seconds
[   14.031468] EXT3-fs: mounted filesystem with ordered data mode.
[   14.076118] Clocksource tsc unstable (delta = -176486272 ns)
[   14.079114] Time: acpi_pm clocksource has been installed.
[   15.290328] 2.6.2X-Elan-touchpad-2009-03-09
[   15.290336] +elantech_detect
[   15.652081] elantech.c: PSMOUSE_CMD_RESET_BAT  param[0]=aa param[1]=0 param[2]=0
[   15.687487] elantech.c: unexpected magic knock result 0x00, 0x02, 0x64.
[   15.687494] 2.6.2X-Elan-touchpad-2009-03-09
[   15.687497] +elantech_detect
[   16.046513] elantech.c: PSMOUSE_CMD_RESET_BAT  param[0]=aa param[1]=0 param[2]=0
[   16.083718] elantech.c: unexpected magic knock result 0x00, 0x02, 0x64.
[   16.083727] 2.6.2X-Elan-touchpad-2009-03-09
[   16.083731] +elantech_detect
[   16.440269] elantech.c: PSMOUSE_CMD_RESET_BAT  param[0]=aa param[1]=0 param[2]=0
[   16.476314] elantech.c: unexpected magic knock result 0x00, 0x02, 0x64.
[   17.281696] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1c0b1, caps: 0xd04711/0xa00000
[   17.307209] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   17.413628] intel_rng: FWH not detected
[   17.434765] iTCO_vendor_support: vendor-support=0
[   17.449558] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   17.449701] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   17.449758] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   17.462143] ieee80211_crypt: registered algorithm 'NULL'
[   17.477166] r8169 Gigabit Ethernet driver 2.2LK loaded
[   17.477247] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   17.477321] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   17.478770] eth0: RTL8102e at 0xf886a000, 00:24:e8:95:3a:c2, XID 24a00000 IRQ 220
[   17.551916] ieee80211_crypt: registered algorithm 'TKIP'
[   17.600385] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   17.600788] EXT3 FS on sda2, internal journal
[   18.020535] usb 5-8: new high speed USB device using ehci_hcd and address 3
[   18.154448] usb 5-8: configuration #1 chosen from 1 choice
[   18.424634] dib0700: loaded with support for 7 different device-types
[   18.427596] dvb-usb: found a 'Hauppauge Nova-T Stick' in cold state, will try to load a firmware
[   18.450553] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw'
[   18.532486] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   18.532535] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   18.705358] dib0700: firmware started successfully.
[   18.741871] Linux agpgart interface v0.102
[   18.758890] agpgart: Detected an Intel 945GME Chipset.
[   18.759118] agpgart: Detected 7932K stolen memory.
[   18.777212] agpgart: AGP aperture is 256M @ 0xd0000000
[   18.822366] [drm] Initialized drm 1.1.0 20060810
[   19.212058] dvb-usb: found a 'Hauppauge Nova-T Stick' in warm state.
[   19.212219] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   19.224405] DVB: registering new adapter (Hauppauge Nova-T Stick)
[   19.581862] DVB: registering frontend 0 (DiBcom 7000PC)...
[   19.650319] MT2060: successfully identified (IF1 = 1220)
[   20.198959] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb5/5-8/input/input8
[   20.235105] dvb-usb: schedule remote query interval to 150 msecs.
[   20.235120] dvb-usb: Hauppauge Nova-T Stick successfully initialized and connected.
[   20.235421] usbcore: registered new interface driver dvb_usb_dib0700
[   21.317165] drm_psb: exports duplicate symbol drm_order (owned by drm)
[   21.326695] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   21.326729] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   21.330629] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   26.060296] r8169: eth0: link down
[   26.062154] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   37.201244] Bluetooth: Core ver 2.11
[   37.202896] NET: Registered protocol family 31
[   37.202907] Bluetooth: HCI device and connection manager initialized
[   37.202917] Bluetooth: HCI socket layer initialized
[   37.221071] Bluetooth: HCI USB driver ver 2.9
[   37.221161] usbcore: registered new interface driver hci_usb
[   37.290625] Bluetooth: L2CAP ver 2.9
[   37.290636] Bluetooth: L2CAP socket layer initialized
[   37.395196] Bluetooth: RFCOMM socket layer initialized
[   37.395227] Bluetooth: RFCOMM TTY layer initialized
[   37.395233] Bluetooth: RFCOMM ver 1.8
[   37.706252] Linux video capture interface: v2.00
[   37.715490] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_0.3M (064e:a102)
[   37.732677] usbcore: registered new interface driver uvcvideo
[   37.732692] USB Video Class driver (v0.1.0)
[   37.755143] usbcore: registered new interface driver cdc_acm
[   37.755160] /build/buildd/linux-2.6.24/debian/build/custom-source-lpia/drivers/usb/class/cdc-acm.c: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[   37.777047] usbcore: registered new interface driver cdc_ether
[   37.781331] usbcore: registered new interface driver mbm
[   38.114557] ppdev: user-space parallel port driver
[   38.345323] wl: module license 'MIXED/Proprietary' taints kernel.
[   38.373740] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[   38.373769] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   38.395607] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.79.10
[   49.593628] eth1: no IPv6 routers present



thanks

---

### Post by xc3RnbFO8P on 2009-11-02
> dvb-usb: Hauppauge Nova-T Stick successfully initialized and connected.
Looking good.
Install Kaffeine:
> sudo apt-get install kaffeine
In Kaffeine, Television> Configure Television> Device 1> Source> Auto Scan
then, Television> Channels> Start Scan

---

