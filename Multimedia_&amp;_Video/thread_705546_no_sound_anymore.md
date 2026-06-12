---
title: "no sound anymore"
date: 2008-02-23
forum: Multimedia &amp; Video
---

### Post by victor-be on 2008-02-23
hello to all

iy happens to me that i don't have sound anymore; it was working fine untill a few hours ago... then after a few manipulations regardinf virtualbox and an musical score edition software for windows (Finale)... nothing more...

I'm using Ubuntu Studio 7.10

**asoundconf list**... won't return anything

** lspci** shows

```
00:00.0 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. Unknown device 5372
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237S PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. Chrome9 HC IGP (rev 01)
04:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
80:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)

```

**lsmod ** shows

```
Module                  Size  Used by
xt_limit                3584  8 
xt_tcpudp               4224  9 
ipt_LOG                 7552  8 
ipt_MASQUERADE          4608  0 
ipt_TOS                 3200  0 
ipt_REJECT              5760  5 
nf_conntrack_irc        8088  0 
nf_conntrack_ftp       11136  0 
xt_state                3456  6 
af_packet              24840  2 
xt_multiport            4224  0 
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26112  11 rfcomm
bluetooth              56804  4 rfcomm,l2cap
ppdev                  10244  0 
ipv6                  278916  18 
acpi_cpufreq           10568  0 
cpufreq_stats           7232  0 [b]
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  2 
cpufreq_userspace       5280  0 
cpufreq_conservative     8072  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
button                  8976  0 
ac                      6148  0 
video                  17932  0 
sbs                    19592  0 
container               5504  0 
dock                   10656  0 
battery                11012  0 
sbp2                   24584  0 
lp                     12452  0 
usbhid                 29664  0 
hid                    28928  1 usbhid
psmouse                39952  0 
serio_raw               8068  0 
shpchp                 34580  0 
pci_hotplug            32576  1 shpchp
parport_pc             37668  1 
parport                37448  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
evdev                  11136  4 
iptable_nat             8708  0 
nf_nat                 20012  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19724  8 iptable_nat
nf_conntrack           65160  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nfnetlink               6936  3 nf_nat,nf_conntrack_ipv4,nf_conntrack
iptable_mangle          3840  0 
iptable_filter          3968  1 
ip_tables              13924  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               16260  10 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,xt_multiport,iptable_nat,ip_tables
ext3                  133640  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36380  0 
sd_mod                 30336  3 
ide_cd                 32416  0 
cdrom                  37408  1 ide_cd
ohci1394               36784  0 
ieee1394               96312  2 sbp2,ohci1394
ehci_hcd               36748  0 
uhci_hcd               26640  0 [/b]
sata_via               12676  2 
via82cxxx              10244  0 [permanent]
via_rhine              26248  0 
mii                     6656  1 via_rhine
ide_core              116932  2 ide_cd,via82cxxx
usbcore               138760  4 usbhid,ehci_hcd,uhci_hcd
ata_generic             8580  0 
libata                125296  2 sata_via,ata_generic
scsi_mod              146828  4 sbp2,sg,sd_mod,libata
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
capability              5896  0 
commoncap               8320  1 capability
fuse                   47124  1
```

et **dmesg** shows 

```

[    0.000000] Linux version 2.6.22-14-server (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 08:27:05 UTC 2008 (Ubuntu 2.6.22-14.52-server)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000077fa0000 (usable)
[    0.000000]  BIOS-e820: 0000000077fa0000 - 0000000077fae000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000077fae000 - 0000000077fe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000077fe0000 - 0000000078000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fecc0000 - 00000000fecc1000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 1023MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 491424) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   491424
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   491424
[    0.000000] On node 0 totalpages: 491424
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2047 pages used for memmap
[    0.000000]   HighMem zone: 260001 pages, LIFO batch:31
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00FAA80 checksum 0
[    0.000000] ACPI: RSDP 000FAA80, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 77FA0000, 003C (r1 A_M_I_ OEMRSDT   7000724 MSFT       97)
[    0.000000] ACPI: FACP 77FA0200, 0084 (r2 A_M_I_ OEMFACP   7000724 MSFT       97)
[    0.000000] ACPI: DSDT 77FA04A0, 584B (r1  A0661 A0661000        0 INTL 20051117)
[    0.000000] ACPI: FACS 77FAE000, 0040
[    0.000000] ACPI: APIC 77FA0390, 0078 (r1 A_M_I_ OEMAPIC   7000724 MSFT       97)
[    0.000000] ACPI: MCFG 77FA0410, 003C (r1 A_M_I_ OEMMCFG   7000724 MSFT       97)
[    0.000000] ACPI: WDRT 77FA0450, 0047 (r1 A_M_I_ VT-8237S  7000724 MSFT       97)
[    0.000000] ACPI: OEMB 77FAE040, 0061 (r1 A_M_I_ AMI_OEM   7000724 MSFT       97)
[    0.000000] ACPI: HPET 77FA5CF0, 0038 (r1 A_M_I_ VT-8237S  7000724 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x03] address[0xfecc0000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 3, version 3, address 0xfecc0000, GSI 24-47
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 2 I/O APICs
[    0.000000] ACPI: HPET id: 0x11068201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 78000000:86c00000)
[    0.000000] Built 1 zonelists.  Total pages: 487585
[    0.000000] Kernel command line: root=UUID=c5cc20f8-1e7f-4a1f-a888-df1b67610da2 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] mapped IOAPIC to ffffb000 (fecc0000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1600.010 MHz processor.
[   29.849851] Console: colour VGA+ 80x25
[   29.850181] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   29.850480] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   29.942879] Memory: 1937512k/1965696k available (2047k kernel code, 26956k reserved, 920k data, 364k init, 1048192k highmem)
[   29.942888] virtual kernel memory layout:
[   29.942890]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   29.942891]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[   29.942892]     vmalloc : 0xf8800000 - 0xffbfe000   ( 115 MB)
[   29.942893]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   29.942894]       .init : 0xc03eb000 - 0xc0446000   ( 364 kB)
[   29.942896]       .data : 0xc02ffd96 - 0xc03e5f04   ( 920 kB)
[   29.942897]       .text : 0xc0100000 - 0xc02ffd96   (2047 kB)
[   29.942900] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   29.942947] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   29.943108] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   29.943114] hpet0: 3 32-bit timers, 14318180 Hz
[   30.093894] Calibrating delay using timer specific routine.. 3201.61 BogoMIPS (lpj=16008059)
[   30.093922] Security Framework v1.0.0 initialized
[   30.093931] SELinux:  Disabled at boot.
[   30.093945] Mount-cache hash table entries: 512
[   30.094102] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e39d 00000000 00000001
[   30.094111] monitor/mwait feature present.
[   30.094113] using mwait in idle threads.
[   30.094118] CPU: L1 I cache: 32K, L1 D cache: 32K
[   30.094121] CPU: L2 cache: 1024K
[   30.094123] CPU: Physical Processor ID: 0
[   30.094125] CPU: Processor Core ID: 0
[   30.094127] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e39d 00000000 00000001
[   30.094137] Compat vDSO mapped to ffffe000.
[   30.094152] Checking 'hlt' instruction... OK.
[   30.133990] SMP alternatives: switching to UP code
[   30.134551] Early unpacking initramfs... done
[   30.463034] ACPI: Core revision 20070126
[   30.463083] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   30.466019] CPU0: Intel(R) Pentium(R) Dual  CPU  E2140  @ 1.60GHz stepping 0d
[   30.466035] SMP alternatives: switching to SMP code
[   30.466136] Booting processor 1/1 eip 3000
[   30.476433] Initializing CPU#1
[   30.623054] Calibrating delay using timer specific routine.. 3199.96 BogoMIPS (lpj=15999844)
[   30.623061] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e39d 00000000 00000001
[   30.623066] monitor/mwait feature present.
[   30.623070] CPU: L1 I cache: 32K, L1 D cache: 32K
[   30.623072] CPU: L2 cache: 1024K
[   30.623074] CPU: Physical Processor ID: 0
[   30.623075] CPU: Processor Core ID: 1
[   30.623077] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e39d 00000000 00000001
[   30.623538] CPU1: Intel(R) Pentium(R) Dual  CPU  E2140  @ 1.60GHz stepping 0d
[   30.623563] Total of 2 processors activated (6401.58 BogoMIPS).
[   30.623889] ENABLING IO-APIC IRQs
[   30.624070] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   30.842796] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   30.862780] Brought up 2 CPUs
[   30.887899] migration_cost=16
[   30.888032] Booting paravirtualized kernel on bare hardware
[   30.888124] Time: 18:33:49  Date: 01/23/108
[   30.888144] NET: Registered protocol family 16
[   30.888229] EISA bus registered
[   30.888234] ACPI: bus type pci registered
[   30.888412] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
[   30.888414] PCI: Using configuration type 1
[   30.888416] Setting up standard PCI resources
[   30.898769] ACPI: EC: Look up EC in DSDT
[   30.904776] ACPI: Interpreter enabled
[   30.904780] ACPI: (supports S0 S1 S3 S4 S5)
[   30.904800] ACPI: Using IOAPIC for interrupt routing
[   30.914063] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   30.914081] PCI: Probing PCI hardware (bus 00)
[   30.915737] PCI: Transparent bridge - 0000:00:13.1
[   30.915799] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   30.915969] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   30.916054] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBPG._PRT]
[   30.916149] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBP0._PRT]
[   30.916256] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[   30.916342] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PA._PRT]
[   30.933040] ACPI: PCI Root Bridge [PCI1] (0000:80)
[   30.933056] PCI: Probing PCI hardware (bus 80)
[   30.933189] ACPI: PCI Interrupt Routing Table [\_SB_.PCI1._PRT]
[   30.933723] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   30.933850] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   30.933974] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   30.934098] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 *6 7 10 11 12 14 15)
[   30.934228] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   30.934359] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   30.934490] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   30.934620] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   30.934740] Linux Plug and Play Support v0.97 (c) Adam Belay
[   30.934756] pnp: PnP ACPI init
[   30.934764] ACPI: bus type pnp registered
[   30.939313] pnp: PnP ACPI: found 15 devices
[   30.939316] ACPI: ACPI bus type pnp unregistered
[   30.939320] PnPBIOS: Disabled by ACPI PNP
[   30.939377] PCI: Using ACPI for IRQ routing
[   30.939380] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   30.954954] PCI: Device 0000:80:01.0 not found by BIOS
[   30.954986] NET: Registered protocol family 8
[   30.954988] NET: Registered protocol family 20
[   30.954997] NetLabel: Initializing
[   30.954999] NetLabel:  domain hash size = 128
[   30.955001] NetLabel:  protocols = UNLABELED CIPSOv4
[   30.955015] NetLabel:  unlabeled traffic allowed by default
[   30.955072] pnp: 00:05: iomem range 0xfecc0000-0xfecc0fff could not be reserved
[   30.955076] pnp: 00:05: iomem range 0xfed02000-0xfed02fff has been reserved
[   30.955083] pnp: 00:08: ioport range 0x290-0x297 has been reserved
[   30.955090] pnp: 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[   30.955093] pnp: 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
[   30.955098] pnp: 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[   30.955104] pnp: 00:0d: iomem range 0x0-0x9ffff could not be reserved
[   30.955106] pnp: 00:0d: iomem range 0x0-0x0 could not be reserved
[   30.955109] pnp: 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[   30.955112] pnp: 00:0d: iomem range 0x100000-0x77ffffff could not be reserved
[   30.962526] Time: tsc clocksource has been installed.
[   30.962535] Switched to high resolution mode on CPU 0
[   30.962619] Switched to high resolution mode on CPU 1
[   30.985392] PCI: Bridge: 0000:00:01.0
[   30.985393]   IO window: disabled.
[   30.985399]   MEM window: fa000000-fbdfffff
[   30.985403]   PREFETCH window: c0000000-dfffffff
[   30.985408] PCI: Bridge: 0000:00:02.0
[   30.985410]   IO window: disabled.
[   30.985414]   MEM window: disabled.
[   30.985418]   PREFETCH window: disabled.
[   30.985423] PCI: Bridge: 0000:00:03.0
[   30.985424]   IO window: disabled.
[   30.985429]   MEM window: disabled.
[   30.985433]   PREFETCH window: disabled.
[   30.985439] PCI: Bridge: 0000:00:13.1
[   30.985442]   IO window: e000-efff
[   30.985447]   MEM window: fbe00000-fbefffff
[   30.985451]   PREFETCH window: disabled.
[   30.985470] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   30.985488] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 27 (level, low) -> IRQ 16
[   30.985494] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   30.985511] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 31 (level, low) -> IRQ 17
[   30.985517] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   30.985530] PCI: Setting latency timer of device 0000:00:13.1 to 64
[   30.985543] NET: Registered protocol family 2
[   31.112348] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   31.112428] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   31.113592] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   31.114052] TCP: Hash tables configured (established 131072 bind 65536)
[   31.114055] TCP reno registered
[   31.152440] checking if image is initramfs... it is
[   31.802863] Freeing initrd memory: 6834k freed
[   31.803567] audit: initializing netlink socket (disabled)
[   31.803588] audit(1203791629.390:1): initialized
[   31.803661] highmem bounce pool size: 64 pages
[   31.805664] VFS: Disk quotas dquot_6.5.1
[   31.805716] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   31.805818] io scheduler noop registered
[   31.805820] io scheduler anticipatory registered
[   31.805822] io scheduler deadline registered (default)
[   31.805836] io scheduler cfq registered
[   31.805859] PCI: VIA PCI bridge detected. Disabling DAC.
[   31.805935] Boot video device is 0000:01:00.0
[   31.806041] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   31.806085] assign_interrupt_mode Found MSI capability
[   31.806089] Allocate Port Service[0000:00:02.0:pcie00]
[   31.806121] Allocate Port Service[0000:00:02.0:pcie02]
[   31.806206] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   31.806257] assign_interrupt_mode Found MSI capability
[   31.806259] Allocate Port Service[0000:00:03.0:pcie00]
[   31.806293] Allocate Port Service[0000:00:03.0:pcie02]
[   31.806457] isapnp: Scanning for PnP cards...
[   32.162643] isapnp: No Plug & Play device found
[   32.186459] Real Time Clock Driver v1.12ac
[   32.186743] hpet_resources: 0xfed00000 is busy
[   32.186787] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   32.186885] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   32.187643] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   32.188349] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   32.188481] input: Macintosh mouse button emulation as /class/input/input0
[   32.188560] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   32.188563] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   32.188895] serio: i8042 KBD port at 0x60,0x64 irq 1
[   32.188900] serio: i8042 AUX port at 0x60,0x64 irq 12
[   32.189007] mice: PS/2 mouse device common for all mice
[   32.189108] EISA: Probing bus 0 at eisa.0
[   32.189157] EISA: Detected 0 cards.
[   32.189258] TCP cubic registered
[   32.189272] NET: Registered protocol family 1
[   32.189293] Using IPI No-Shortcut mode
[   32.189471]   Magic number: 12:641:595
[   32.189780] Freeing unused kernel memory: 364k freed
[   32.210627] input: AT Translated Set 2 keyboard as /class/input/input1
[   33.405279] fuse init (API version 7.8)
[   33.410764] Capability LSM initialized
[   33.420856] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  01, should be FC [20070126]
[   33.420865] ACPI: SSDT 77FAE0B0, 01D2 (r1    AMI   CPU1PM        1 INTL 20051117)
[   33.421107] ACPI: Processor [CPU1] (supports 16 throttling states)
[   33.421275] ACPI: SSDT 77FAE290, 0143 (r1    AMI   CPU2PM        1 INTL 20051117)
[   33.421480] ACPI: Processor [CPU2] (supports 16 throttling states)
[   33.421492] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   33.421503] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   34.018063] SCSI subsystem initialized
[   34.023071] libata version 2.21 loaded.
[   34.032456] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   34.032463] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   34.032747] usbcore: registered new interface driver usbfs
[   34.032769] usbcore: registered new interface driver hub
[   34.032793] usbcore: registered new device driver usb
[   34.033977] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   34.034043] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 18
[   34.034149] eth0: VIA Rhine II at 0x1c000, 00:1d:60:22:e4:f1, IRQ 18.
[   34.034863] eth0: MII PHY found at address 1, status 0x796d advertising 0de1 Link 41e1.
[   34.035507] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[   34.035533] VP_IDE: chipset revision 7
[   34.035535] VP_IDE: not 100% native mode: will probe irqs later
[   34.035547] VP_IDE: VIA vt8237s (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[   34.035555]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
[   34.035565]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:pio, hdd:pio
[   34.035577] Probing IDE interface ide0...
[   34.045528] USB Universal Host Controller Interface driver v3.0
[   34.956365] hda: Optiarc DVD RW AD-7173A, ATAPI CD/DVD-ROM drive
[   35.675636] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   35.676275] Probing IDE interface ide1...
[   36.284302] sata_via 0000:00:0f.0: version 2.2
[   36.284338] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 21 (level, low) -> IRQ 19
[   36.284382] sata_via 0000:00:0f.0: routed to hard irq line 5
[   36.284472] scsi0 : sata_via
[   36.285352] scsi1 : sata_via
[   36.285608] ata1: SATA max UDMA/133 cmd 0x0001dc00 ctl 0x0001d882 bmdma 0x0001d400 irq 19
[   36.285611] ata2: SATA max UDMA/133 cmd 0x0001d800 ctl 0x0001d482 bmdma 0x0001d408 irq 19
[   36.291782] hda: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
[   36.291792] Uniform CD-ROM driver Revision: 3.20
[   36.493852] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   36.713527] ata2: SATA link up 1.5 Gbps (SStatus 123 SControl 300)
[   36.913580] ata2.00: ATA-7: Hitachi HDS721616PLA380, P22OABEA, max UDMA/133
[   36.913585] ata2.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   36.953519] ata2.00: configured for UDMA/133
[   36.953654] scsi 1:0:0:0: Direct-Access     ATA      Hitachi HDS72161 P22O PQ: 0 ANSI: 5
[   36.953778] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 19
[   36.953800] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   36.953962] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[   36.953993] ehci_hcd 0000:00:10.4: debug port 1
[   36.954003] ehci_hcd 0000:00:10.4: irq 19, io mem 0xf9fffc00
[   36.954014] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   36.954128] usb usb1: configuration #1 chosen from 1 choice
[   36.954161] hub 1-0:1.0: USB hub found
[   36.954169] hub 1-0:1.0: 8 ports detected
[   37.063275] ACPI: PCI Interrupt 0000:04:05.0[A] -> GSI 19 (level, low) -> IRQ 20
[   37.063591] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 20 (level, low) -> IRQ 21
[   37.063602] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   37.063633] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[   37.063659] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000c480
[   37.063758] usb usb2: configuration #1 chosen from 1 choice
[   37.063784] hub 2-0:1.0: USB hub found
[   37.063790] hub 2-0:1.0: 2 ports detected
[   37.116393] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[fbeff800-fbefffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   37.172922] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 22 (level, low) -> IRQ 22
[   37.172938] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   37.172969] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[   37.173007] uhci_hcd 0000:00:10.1: irq 22, io base 0x0000c800
[   37.173107] usb usb3: configuration #1 chosen from 1 choice
[   37.173137] hub 3-0:1.0: USB hub found
[   37.173143] hub 3-0:1.0: 2 ports detected
[   37.282738] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 19
[   37.282751] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   37.282780] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[   37.282804] uhci_hcd 0000:00:10.2: irq 19, io base 0x0000c880
[   37.282917] usb usb4: configuration #1 chosen from 1 choice
[   37.282942] hub 4-0:1.0: USB hub found
[   37.282948] hub 4-0:1.0: 2 ports detected
[   37.392553] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 23 (level, low) -> IRQ 18
[   37.392566] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   37.392595] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[   37.392624] uhci_hcd 0000:00:10.3: irq 18, io base 0x0000cc00
[   37.392738] usb usb5: configuration #1 chosen from 1 choice
[   37.392763] hub 5-0:1.0: USB hub found
[   37.392770] hub 5-0:1.0: 2 ports detected
[   37.532328] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   37.532346] sd 1:0:0:0: [sda] Write Protect is off
[   37.532349] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   37.532364] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.532433] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   37.532442] sd 1:0:0:0: [sda] Write Protect is off
[   37.532445] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   37.532459] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.532463]  sda: sda1 sda2 < sda5 >
[   37.566261] sd 1:0:0:0: [sda] Attached SCSI disk
[   37.570853] sd 1:0:0:0: Attached scsi generic sg0 type 0
[   37.783266] Attempting manual resume
[   37.783269] swsusp: Resume From Partition 8:5
[   37.783271] PM: Checking swsusp image.
[   37.783424] PM: Resume from disk failed.
[   37.815706] kjournald starting.  Commit interval 5 seconds
[   37.815723] EXT3-fs: mounted filesystem with ordered data mode.
[   37.901681] usb 3-1: new low speed USB device using uhci_hcd and address 2
[   38.072726] usb 3-1: configuration #1 chosen from 1 choice
[   38.440905] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[8888888888889259]
[   42.676169] ip_tables: (C) 2000-2006 Netfilter Core Team
[   42.718167] Netfilter messages via NETLINK v0.30.
[   42.722025] nf_conntrack version 0.5.0 (8192 buckets, 65536 max)
[   44.303693] input: PC Speaker as /class/input/input2
[   44.398707] parport_pc 00:04: reported by Plug and Play ACPI
[   44.398815] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   44.432239] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   44.467702] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   44.562254] usbcore: registered new interface driver hiddev
[   44.574620] input: PS/2+USB Mouse as /class/input/input3
[   44.574667] input: USB HID v1.11 Mouse [PS/2+USB Mouse] on usb-0000:00:10.1-1
[   44.574684] usbcore: registered new interface driver usbhid
[   44.574688] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   44.777580] lp0: using parport0 (interrupt-driven).
[   44.861045] Adding 5695000k swap on /dev/sda5.  Priority:-1 extents:1 across:5695000k
[  197.668604] EXT3 FS on sda1, internal journal
[  198.220096] No dock devices found.
[  198.456337] input: Power Button (FF) as /class/input/input4
[  198.456360] ACPI: Power Button (FF) [PWRF]
[  198.456470] input: Sleep Button (CM) as /class/input/input5
[  198.456488] ACPI: Sleep Button (CM) [SLPB]
[  198.456531] input: Power Button (CM) as /class/input/input6
[  198.456545] ACPI: Power Button (CM) [PWRB]
[  199.507956] NET: Registered protocol family 10
[  199.508074] lo: Disabled Privacy Extensions
[  199.737244] ppdev: user-space parallel port driver
[  199.895988] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  199.944504] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  199.944509] apm: disabled - APM is not SMP safe.
[  200.608280] Bluetooth: Core ver 2.11
[  200.608335] NET: Registered protocol family 31
[  200.608338] Bluetooth: HCI device and connection manager initialized
[  200.608343] Bluetooth: HCI socket layer initialized
[  200.627356] Bluetooth: L2CAP ver 2.8
[  200.627362] Bluetooth: L2CAP socket layer initialized
[  200.674850] Bluetooth: RFCOMM socket layer initialized
[  200.674865] Bluetooth: RFCOMM TTY layer initialized
[  200.674868] Bluetooth: RFCOMM ver 1.8
[  205.393956] NET: Registered protocol family 17
[  217.076906] eth0: no IPv6 routers present
[  335.453753] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:16:e3:27:c2:bc:08:00 SRC=192.168.1.39 DST=192.168.1.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=52405 PROTO=UDP SPT=138 DPT=138 LEN=209 


```

I'm a beginner but very eager to learn; i've searched around everywhere i could untill i post this..... =|

thank to everyone available for a bit help...

---

