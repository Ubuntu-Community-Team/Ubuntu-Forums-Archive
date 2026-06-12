---
title: "sound blaster live not detected 7.04"
date: 2007-05-14
forum: Multimedia &amp; Video
---

### Post by skydemon on 2007-05-14
Hi, all I have just installed 7.04 via VMWare but I cannot get sound (using SBlive) to work at all. I have followed this guide:
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

and could manually install the emu10k1 drivers but still no sound coard was detected and Im stumped, can anyone help? Cheers :)

PS there is no onboard sound

here is the output of lspci and dmesg:

mick@mick-desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX
Host bridge (rev 01)
        Subsystem: VMware Inc virtualHW v3
        Flags: bus master, medium devsel, latency 0
        Memory at ec000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP
bridge (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64

00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 08)
        Subsystem: VMware Inc virtualHW v3
        Flags: bus master, medium devsel, latency 0

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev
01) (prog-if 8a [Master SecP PriP])
        Subsystem: VMware Inc virtualHW v3
        Flags: bus master, medium devsel, latency 64
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable)
[disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable)
[disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable)
[disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable)
[disabled] [size=1]
        I/O ports at 1050 [size=16]

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
        Subsystem: VMware Inc virtualHW v3
        Flags: medium devsel, IRQ 9

00:0f.0 VGA compatible controller: VMware Inc [VMware SVGA II] PCI
Display Adapter (prog-if 00 [VGA])
        Subsystem: VMware Inc [VMware SVGA II] PCI Display Adapter
        Flags: bus master, medium devsel, latency 64
        I/O ports at 1060 [size=16]
        Memory at f0000000 (32-bit, non-prefetchable) [size=128M]
        Memory at e8000000 (32-bit, non-prefetchable) [size=8M]
        [virtual] Expansion ROM at 20010000 [disabled] [size=32K]

00:10.0 SCSI storage controller: LSI Logic / Symbios Logic 53c1030
PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 01)
        Flags: bus master, medium devsel, latency 64, IRQ 16
        I/O ports at 1080 [size=128]
        Memory at e8800000 (32-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 20018000 [disabled] [size=16K]

00:11.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970
[PCnet32 LANCE] (rev 10)
        Subsystem: Advanced Micro Devices [AMD] PCnet - Fast 79C971
        Flags: bus master, medium devsel, latency 64, IRQ 17
        I/O ports at 1400 [size=128]
        [virtual] Expansion ROM at 20000000 [disabled] [size=64K]

mick@mick-desktop:~$ 


mick@mick-desktop:~$ dmesg
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc
version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC
2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size:
000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size:
0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000ca000 size:
0000000000002000 end: 00000000000cc000 type: 2
[    0.000000] copy_e820_map() start: 00000000000dc000 size:
0000000000024000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size:
000000000fdf0000 end: 000000000fef0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000fef0000 size:
000000000000f000 end: 000000000feff000 type: 3
[    0.000000] copy_e820_map() start: 000000000feff000 size:
0000000000001000 end: 000000000ff00000 type: 4
[    0.000000] copy_e820_map() start: 000000000ff00000 size:
0000000000100000 end: 0000000010000000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 00000000fec00000 size:
0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size:
0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fffe0000 size:
0000000000020000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800
(usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000
(reserved)
[    0.000000]  BIOS-e820: 00000000000ca000 - 00000000000cc000
(reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000
(reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000fef0000
(usable)
[    0.000000]  BIOS-e820: 000000000fef0000 - 000000000feff000 (ACPI
data)
[    0.000000]  BIOS-e820: 000000000feff000 - 000000000ff00000 (ACPI
NVS)
[    0.000000]  BIOS-e820: 000000000ff00000 - 0000000010000000
(usable)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000
(reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000
(reserved)
[    0.000000]  BIOS-e820: 00000000fffe0000 - 0000000100000000
(reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 256MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f6ce0
[    0.000000] Entering add_active_range(0, 0, 65536) 0 entries of
256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    65536
[    0.000000]   HighMem     65536 ->    65536
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    65536
[    0.000000] On node 0 totalpages: 65536
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 480 pages used for memmap
[    0.000000]   Normal zone: 60960 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                
) @ 0x000f6c70
[    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP
0x00000000) @ 0x0fefab74
[    0.000000] ACPI: FADT (v001 INTEL  440BX    0x06040000 PTL 
0x000f4240) @ 0x0fefef14
[    0.000000] ACPI: MADT (v001 PTLTD    APIC   0x06040000  LTP
0x00000000) @ 0x0fefef88
[    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP
0x00000001) @ 0x0fefefd8
[    0.000000] ACPI: DSDT (v001 PTLTD  Custom   0x06040000 MSFT
0x0100000d) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:4 APIC version 17
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000,
GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high
edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 20000000 (gap:
10000000:eec00000)
[    0.000000] Detected 1342.385 MHz processor.
[ 5989.988179] Built 1 zonelists.  Total pages: 65024
[ 5989.988457] Kernel command line:
root=UUID=568a5614-a18a-4cb7-996a-a32c6652b3e0 ro quiet splash
[ 5989.989315] mapped APIC to ffffd000 (fee00000)
[ 5989.989380] mapped IOAPIC to ffffc000 (fec00000)
[ 5989.989855] Enabling fast FPU save and restore... done.
[ 5989.990258] Initializing CPU#0
[ 5989.991887] PID hash table entries: 1024 (order: 10, 4096 bytes)
[ 5989.995947] Console: colour VGA+ 80x25
[ 5989.996009] Dentry cache hash table entries: 32768 (order: 5,
131072 bytes)
[ 5989.996072] Inode-cache hash table entries: 16384 (order: 4, 65536
bytes)
[ 5989.996134] Memory: 248640k/262144k available (1992k kernel code,
12948k reserved, 893k data, 328k init, 0k highmem)
[ 5989.996197] virtual kernel memory layout:
[ 5989.996206]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[ 5989.996215]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[ 5989.996219]     vmalloc : 0xd0800000 - 0xff7fe000   ( 751 MB)
[ 5989.996222]     lowmem  : 0xc0000000 - 0xd0000000   ( 256 MB)
[ 5989.996225]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[ 5989.996227]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[ 5989.996230]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[ 5989.996290] Checking if this processor honours the WP bit even in
supervisor mode... Ok.
[ 5990.077297] Calibrating delay using timer specific routine..
2692.18 BogoMIPS (lpj=5384374)
[ 5990.077360] Security Framework v1.0.0 initialized
[ 5990.077422] SELinux:  Disabled at boot.
[ 5990.077485] Mount-cache hash table entries: 512
[ 5990.077547] CPU: After generic identify, caps: 0183fbff c1c7fbff
00000000 00000000 00000000 00000000 00000000
[ 5990.077610] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64
bytes/line)
[ 5990.077672] CPU: L2 Cache: 256K (64 bytes/line)
[ 5990.077735] CPU: After all inits, caps: 0183fbff c1c7fbff 00000000
00000420 00000000 00000000 00000000
[ 5990.077797] Compat vDSO mapped to ffffe000.
[ 5990.077860] Remapping vsyscall page to ffffe000
[ 5990.077922] Checking 'hlt' instruction... OK.
[ 5990.091896] SMP alternatives: switching to UP code
[ 5990.091959] Freeing SMP alternatives: 11k freed
[ 5990.092021] Early unpacking initramfs... done
[ 5990.092084] ACPI: Core revision 20060707
[ 5990.095894] ACPI: Looking for DSDT in initramfs... file /DSDT.aml
not found, using machine DSDT.
[ 5990.096144] CPU0: AMD Athlon(tm) Processor stepping 04
[ 5990.096206] Total of 1 processors activated (2692.18 BogoMIPS).
[ 5990.096269] ENABLING IO-APIC IRQs
[ 5990.096493] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[ 5990.284448] Brought up 1 CPUs
[ 5990.313778] Booting paravirtualized kernel on bare hardware
[ 5990.319741] Time: 10:45:14  Date: 04/15/107
[ 5990.324284] NET: Registered protocol family 16
[ 5990.357672] EISA bus registered
[ 5990.359269] ACPI: bus type pci registered
[ 5990.364292] PCI: PCI BIOS revision 2.10 entry at 0xfd9a0, last
bus=1
[ 5990.364418] PCI: Using configuration type 1
[ 5990.364474] Setting up standard PCI resources
[ 5990.488658] ACPI: Interpreter enabled
[ 5990.488716] ACPI: Using IOAPIC for interrupt routing
[ 5990.521235] ACPI: PCI Root Bridge [PCI0] (0000:00)
[ 5990.521437] PCI: Probing PCI hardware (bus 00)
[ 5990.604309] PCI quirk: region 1000-103f claimed by PIIX4 ACPI
[ 5990.604401] PCI quirk: region 1040-104f claimed by PIIX4 SMB
[ 5990.612628] Boot video device is 0000:00:0f.0
[ 5990.629748] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[ 5990.670855] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10
11 14 15) *0, disabled.
[ 5990.675180] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10
11 14 15)
[ 5990.676412] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10
*11 14 15)
[ 5990.679993] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10
11 14 15) *0, disabled.
[ 5990.841923] Linux Plug and Play Support v0.97 (c) Adam Belay
[ 5990.843607] pnp: PnP ACPI init
[ 5991.116465] pnp: PnP ACPI: found 12 devices
[ 5991.116599] PnPBIOS: Disabled by ACPI PNP
[ 5991.120462] PCI: Using ACPI for IRQ routing
[ 5991.120576] PCI: If a device doesn't work, try "pci=routeirq".  If
it helps, post a report
[ 5991.195297] NET: Registered protocol family 8
[ 5991.195326] NET: Registered protocol family 20
[ 5991.223412] PCI: Bridge: 0000:00:01.0
[ 5991.223450]   IO window: disabled.
[ 5991.223596]   MEM window: disabled.
[ 5991.223722]   PREFETCH window: disabled.
[ 5991.227606] PCI: Setting latency timer of device 0000:00:01.0 to 64
[ 5991.228320] NET: Registered protocol family 2
[ 5991.311563] IP route cache hash table entries: 2048 (order: 1,
8192 bytes)
[ 5991.332563] TCP established hash table entries: 8192 (order: 4,
65536 bytes)
[ 5991.339448] TCP bind hash table entries: 4096 (order: 3, 32768
bytes)
[ 5991.340657] TCP: Hash tables configured (established 8192 bind
4096)
[ 5991.340843] TCP reno registered
[ 5991.389860] checking if image is initramfs... it is
[ 5993.101756] Freeing initrd memory: 7006k freed
[ 5993.159795] Simple Boot Flag at 0x36 set to 0x1
[ 5993.180851] audit: initializing netlink socket (disabled)
[ 5993.185000] audit(1179225901.052:1): initialized
[ 5993.205501] VFS: Disk quotas dquot_6.5.1
[ 5993.206308] Dquot-cache hash table entries: 1024 (order 0, 4096
bytes)
[ 5993.219012] io scheduler noop registered
[ 5993.219144] io scheduler anticipatory registered
[ 5993.219160] io scheduler deadline registered
[ 5993.219263] io scheduler cfq registered (default)
[ 5993.223454] Limiting direct PCI/PCI transfers.
[ 5993.242757] isapnp: Scanning for PnP cards...
[ 5994.178070] isapnp: No Plug & Play device found
[ 5994.478216] Real Time Clock Driver v1.12ac
[ 5994.481501] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports,
IRQ sharing enabled
[ 5994.490752] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 5994.498242] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[ 5994.522377] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 5994.527255] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[ 5994.535272] mice: PS/2 mouse device common for all mice
[ 5994.554051] RAMDISK driver initialized: 16 RAM disks of 65536K
size 1024 blocksize
[ 5994.578332] input: Macintosh mouse button emulation as
/class/input/input0
[ 5994.581915] Uniform Multi-Platform E-IDE driver Revision:
7.00alpha2
[ 5994.582099] ide: Assuming 33MHz system bus speed for PIO modes;
override with idebus=xx
[ 5994.593426] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUS] at
0x60,0x64 irq 1,12
[ 5995.645003] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 5995.645235] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 5995.660919] EISA: Probing bus 0 at eisa.0
[ 5995.661435] Cannot allocate resource for EISA slot 1
[ 5995.661557] EISA: Detected 0 cards.
[ 5995.691984] TCP cubic registered
[ 5995.692046] NET: Registered protocol family 1
[ 5995.692109] Using IPI No-Shortcut mode
[ 5995.692546] ACPI: (supports S0 S1 S5)
[ 5995.692671]   Magic number: 7:415:780
[ 5995.692734]   hash matches device ptyq2
[ 5995.692933] Time: tsc clocksource has been installed.
[ 5995.694124] Freeing unused kernel memory: 328k freed
[ 5995.694494] input: AT Translated Set 2 keyboard as
/class/input/input1
[ 5997.247986] Capability LSM initialized
[ 5997.343625] ACPI: Processor [CPU0] (supports 8 throttling states)
[ 5997.343688] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND,
Processor Device is not present [20060707]
[ 5997.343750] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND,
Processor Device is not present [20060707]
[ 5997.343799] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND,
Processor Device is not present [20060707]
[ 5998.378182] SCSI subsystem initialized
[ 5998.378813] libata version 2.20 loaded.
[ 5998.394818] PIIX4: IDE controller at PCI slot 0000:00:07.1
[ 5998.394880] PIIX4: chipset revision 1
[ 5998.394943] PIIX4: not 100% native mode: will probe irqs later
[ 5998.395005]     ide1: BM-DMA at 0x1058-0x105f, BIOS settings:
hdc:DMA, hdd:pio
[ 5998.395068] Probing IDE interface ide1...
[ 5998.461444] Fusion MPT base driver 3.04.03
[ 5998.461481] Copyright (c) 1999-2007 LSI Logic Corporation
[ 5998.465458] Fusion MPT SPI Host driver 3.04.03
[ 5998.474027] pcnet32.c:v1.33 27.Jun.2006 [email]tsbogend@alpha.franken.de[/email]
[ 5998.710586] Floppy drive(s): fd0 is 1.44M
[ 5998.731474] FDC 0 is a post-1991 82077
[ 5999.184357] hdc: VMware Virtual IDE CDROM Drive, ATAPI CD/DVD-ROM
drive
[ 5999.527129] ide1 at 0x170-0x177,0x376 on irq 15
[ 5999.529472] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 17 (level,
low) -> IRQ 16
[ 5999.529535] mptbase: Initiating ioc0 bringup
[ 5999.559167] hdc: ATAPI 40X DVD-ROM drive, 512kB Cache, UDMA(33)
[ 5999.559230] Uniform CD-ROM driver Revision: 3.20
[ 5999.603915] ioc0: 53C1030: Capabilities={Initiator}
[ 5999.739085] scsi0 : ioc0: LSI53C1030, FwRev=00000000h, Ports=1,
MaxQ=128, IRQ=16
[ 5999.865633] scsi 0:0:0:0: Direct-Access     VMware,  VMware
Virtual S 1.0  PQ: 0 ANSI: 2
[ 5999.865696]  target0:0:0: Beginning Domain Validation
[ 5999.865758]  target0:0:0: Domain Validation skipping write tests
[ 5999.865803]  target0:0:0: Ending Domain Validation
[ 5999.865866]  target0:0:0: FAST-40 WIDE SCSI 80.0 MB/s ST (25 ns,
offset 127)
[ 5999.874721] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 18 (level,
low) -> IRQ 17
[ 5999.874783] pcnet32: PCnet/PCI II 79C970A at 0x1400, 00 0c 29 ba
e5 75 assigned IRQ 17.
[ 5999.874846] eth0: registered as PCnet/PCI II 79C970A
[ 5999.874908] pcnet32: 1 cards_found.
[ 5999.907859] SCSI device sda: 20971520 512-byte hdwr sectors (10737
MB)
[ 5999.907922] sda: Write Protect is off
[ 5999.907961] sda: Mode Sense: 5d 00 00 00
[ 5999.908024] sda: cache data unavailable
[ 5999.908052] sda: assuming drive cache: write through
[ 5999.911316] SCSI device sda: 20971520 512-byte hdwr sectors (10737
MB)
[ 5999.911379] sda: Write Protect is off
[ 5999.911387] sda: Mode Sense: 5d 00 00 00
[ 5999.911450] sda: cache data unavailable
[ 5999.911457] sda: assuming drive cache: write through
[ 5999.911519]  sda: sda1 sda2 < sda5 >
[ 5999.916487] sd 0:0:0:0: Attached scsi disk sda
[ 5999.928142] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 6000.123217] Attempting manual resume
[ 6000.123266] swsusp: Resume From Partition 8:5
[ 6000.123298] PM: Checking swsusp image.
[ 6000.123422] PM: Resume from disk failed.
[ 6000.169331] kjournald starting.  Commit interval 5 seconds
[ 6000.170520] EXT3-fs: mounted filesystem with ordered data mode.
[ 6022.090261] eth0: link up
[ 6025.698038] NET: Registered protocol family 10
[ 6025.709797] lo: Disabled Privacy Extensions
[ 6037.402854] eth0: no IPv6 routers present
[ 6039.758281] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 6039.782563] shpchp: Standard Hot Plug PCI Controller Driver
version: 0.4
[ 6040.497939] Linux agpgart interface v0.102 (c) Dave Jones
[ 6040.529731] agpgart: Detected an Intel 440BX Chipset.
[ 6040.546903] agpgart: AGP aperture is 64M @ 0xec000000
[ 6040.997471] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[ 6041.000921] piix4_smbus 0000:00:07.3: Host SMBus controller not
enabled!
[ 6042.216708] input: PC Speaker as /class/input/input2
[ 6042.594694] input: ImPS/2 Generic Wheel Mouse as
/class/input/input3
[ 6042.806710] parport: PnPBIOS parport detected.
[ 6042.808631] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[ 6045.644386] fuse init (API version 7.8)
[ 6045.794710] lp0: using parport0 (interrupt-driven).
[ 6046.363073] Adding 489940k swap on
/dev/disk/by-uuid/8ff0451c-f345-4aa4-9e58-573606ba9160.  Priority:-1
extents:1 across:489940k
[ 6047.003465] EXT3 FS on sda1, internal journal
[ 6051.865501] NET: Registered protocol family 17
[ 6062.197400] ibm_acpi: ec object not found
[ 6062.453541] ACPI: AC Adapter [ACAD] (on-line)
[ 6062.629710] Using specific hotkey driver
[ 6063.661071] input: Power Button (FF) as /class/input/input4
[ 6063.664216] ACPI: Power Button (FF) [PWRF]
[ 6064.266720] No dock devices found.
[ 6064.940684] pcc_acpi: loading...
[ 6066.975995] powernow: No powernow capabilities detected
[ 6086.279501] mtrr: your processor doesn't support write-combining
[ 6086.434052] ppdev: user-space parallel port driver
[ 6102.185152] vmxnet: module license 'unspecified' taints kernel.
[ 6102.324699] VMware vmxnet virtual NIC driver release 1.0.2
build-39867
[ 6103.148342] apm: BIOS version 1.2 Flags 0x03 (Driver version
1.16ac)
[ 6103.148454] apm: overridden by ACPI.
[ 6104.856758] Bluetooth: Core ver 2.11
[ 6104.872453] NET: Registered protocol family 31
[ 6104.872535] Bluetooth: HCI device and connection manager
initialized
[ 6104.879842] Bluetooth: HCI socket layer initialized
[ 6105.225813] Bluetooth: L2CAP ver 2.8
[ 6105.225857] Bluetooth: L2CAP socket layer initialized
[ 6105.287896] Bluetooth: RFCOMM socket layer initialized
[ 6105.292542] Bluetooth: RFCOMM TTY layer initialized
[ 6105.292584] Bluetooth: RFCOMM ver 1.8
mick@mick-desktop:~$

---

### Post by skydemon on 2007-05-14
sorry i forgot to mention the card works fine in XP so physically there is nothing wrong with it or the way it's mounted

---

### Post by skydemon on 2007-05-15
dont worry got it sorted, I didn't realise you need to add the sound card in VMWare directly

---

