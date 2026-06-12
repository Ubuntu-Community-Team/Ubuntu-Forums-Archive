---
title: "Pixelview Playtv Pro 2 - No sound"
date: 2008-01-18
forum: Multimedia &amp; Video
---

### Post by venkatachar on 2008-01-18
Hi,
I finally figured out a way to get playtv pro 2 tv tuner card to work on my 7.10 ubuntu.
However I am getting only video and there is no sound.
I have connected the audio out form tv tuner to my line in.
The sound is fine in winxp. 

This is the only reason stopping me to move to gusty completely.

Can anyone please help?

Thanks

---

### Post by blob84 on 2008-02-11
hi, i have the same problem, but for me doesn't work the television, but i need only the composite and it works but there is no sound...

i used this command

```
sudo rmmod bt878
sudo rmmod bttv
sudo modprobe card=37 tuner=0
```

this is my dmesg for tv card

```
Thank you for using tvtime.
blob@blob-desktop:~$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Fri Feb 1 04:59:50 UTC 2008 (Ubuntu 2.6.22-14.51-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fff0000 (usable)
[    0.000000]  BIOS-e820: 000000007fff0000 - 000000007fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff3000 - 0000000080000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f5d20
[    0.000000] Entering add_active_range(0, 0, 524272) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   524272
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   524272
[    0.000000] On node 0 totalpages: 524272
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2303 pages used for memmap
[    0.000000]   HighMem zone: 292593 pages, LIFO batch:31
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7730 checksum 0
[    0.000000] ACPI: RSDP 000F7730, 0014 (r0 AWARD )
[    0.000000] ACPI: RSDT 7FFF3000, 002C (r1 AWARD  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 7FFF3040, 0074 (r1 AWARD  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 7FFF30C0, 395B (r1 AWARD  AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 7FFF0000, 0040
[    0.000000] ACPI: APIC 7FFF6A40, 005A (r1 AWARD  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:10 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 20, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ec00000)
[    0.000000] Built 1 zonelists.  Total pages: 520177
[    0.000000] Kernel command line: root=UUID=9ef5ce45-ddf4-427c-b07d-23d443887643 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2000.518 MHz processor.
[   13.017797] Console: colour VGA+ 80x25
[   13.018635] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   13.020117] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   13.121643] Memory: 2067712k/2097088k available (2015k kernel code, 28148k reserved, 916k data, 364k init, 1179584k highmem)
[   13.121654] virtual kernel memory layout:
[   13.121655]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   13.121657]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   13.121658]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   13.121659]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   13.121660]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   13.121662]       .data : 0xc02f7e66 - 0xc03dce84   ( 916 kB)
[   13.121663]       .text : 0xc0100000 - 0xc02f7e66   (2015 kB)
[   13.121667] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   13.121724] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   13.201612] Calibrating delay using timer specific routine.. 4003.21 BogoMIPS (lpj=8006436)
[   13.201657] Security Framework v1.0.0 initialized
[   13.201668] SELinux:  Disabled at boot.
[   13.201690] Mount-cache hash table entries: 512
[   13.201889] CPU: After generic identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[   13.201901] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   13.201904] CPU: L2 Cache: 256K (64 bytes/line)
[   13.201907] CPU: After all inits, caps: 0383fbff c1cbfbff 00000000 00000420 00000000 00000000 00000000
[   13.201922] Compat vDSO mapped to ffffe000.
[   13.201940] Checking 'hlt' instruction... OK.
[   13.217781] SMP alternatives: switching to UP code
[   13.218136] Freeing SMP alternatives: 11k freed
[   13.218565] Early unpacking initramfs... done
[   13.537622] ACPI: Core revision 20070126
[   13.537736] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   14.526835] CPU0: AMD Sempron(tm)   2800+ stepping 00
[   14.526860] Total of 1 processors activated (4003.21 BogoMIPS).
[   14.526967] ENABLING IO-APIC IRQs
[   14.527145] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   14.671233] Brought up 1 CPUs
[   14.671391] Booting paravirtualized kernel on bare hardware
[   14.671468] Time: 15:39:46  Date: 01/11/108
[   14.671509] NET: Registered protocol family 16
[   14.671641] EISA bus registered
[   14.671655] ACPI: bus type pci registered
[   14.710062] PCI: PCI BIOS revision 2.10 entry at 0xfbce0, last bus=1
[   14.710066] PCI: Using configuration type 1
[   14.710068] Setting up standard PCI resources
[   14.717364] ACPI: EC: Look up EC in DSDT
[   14.720268] ACPI: Interpreter enabled
[   14.720272] ACPI: (supports S0 S3 S4 S5)
[   14.720289] ACPI: Using IOAPIC for interrupt routing
[   14.724978] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   14.724991] PCI: Probing PCI hardware (bus 00)
[   14.725870] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   14.740912] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   14.741006] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   14.741095] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   14.741185] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   14.741274] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   14.741362] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   14.741492] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   14.741589] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   14.741686] Linux Plug and Play Support v0.97 (c) Adam Belay
[   14.741701] pnp: PnP ACPI init
[   14.741713] ACPI: bus type pnp registered
[   14.744223] pnp: PnP ACPI: found 13 devices
[   14.744226] ACPI: ACPI bus type pnp unregistered
[   14.744231] PnPBIOS: Disabled by ACPI PNP
[   14.744306] PCI: Using ACPI for IRQ routing
[   14.744311] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   14.752261] NET: Registered protocol family 8
[   14.752263] NET: Registered protocol family 20
[   14.752361] pnp: 00:00: iomem range 0xd0000-0xd3fff has been reserved
[   14.752364] pnp: 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[   14.752367] pnp: 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[   14.752370] pnp: 00:00: iomem range 0xfc000-0xfffff could not be reserved
[   14.755038] Time: tsc clocksource has been installed.
[   14.782666] PCI: Bridge: 0000:00:01.0
[   14.782670]   IO window: 9000-9fff
[   14.782676]   MEM window: e4000000-e5ffffff
[   14.782681]   PREFETCH window: c0000000-dfffffff
[   14.782707] NET: Registered protocol family 2
[   14.819012] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   14.819243] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   14.822279] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   14.823371] TCP: Hash tables configured (established 131072 bind 65536)
[   14.823376] TCP reno registered
[   14.835094] checking if image is initramfs... it is
[   15.282191] Switched to high resolution mode on CPU 0
[   15.434064] Freeing initrd memory: 7064k freed
[   15.434588] audit: initializing netlink socket (disabled)
[   15.434607] audit(1202744385.048:1): initialized
[   15.434693] highmem bounce pool size: 64 pages
[   15.436703] VFS: Disk quotas dquot_6.5.1
[   15.436768] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   15.436895] io scheduler noop registered
[   15.436897] io scheduler anticipatory registered
[   15.436900] io scheduler deadline registered
[   15.436915] io scheduler cfq registered (default)
[   15.553653] Boot video device is 0000:01:00.0
[   15.553872] isapnp: Scanning for PnP cards...
[   15.906717] isapnp: No Plug & Play device found
[   15.934981] Real Time Clock Driver v1.12ac
[   15.935093] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   15.935194] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   15.936124] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   15.937096] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   15.937367] input: Macintosh mouse button emulation as /class/input/input0
[   15.937461] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   15.937767] serio: i8042 KBD port at 0x60,0x64 irq 1
[   15.937773] serio: i8042 AUX port at 0x60,0x64 irq 12
[   15.937950] mice: PS/2 mouse device common for all mice
[   15.938083] EISA: Probing bus 0 at eisa.0
[   15.938095] Cannot allocate resource for EISA slot 1
[   15.938105] Cannot allocate resource for EISA slot 4
[   15.938120] EISA: Detected 0 cards.
[   15.938351] TCP cubic registered
[   15.938362] NET: Registered protocol family 1
[   15.938387] Using IPI No-Shortcut mode
[   15.938607]   Magic number: 12:523:689
[   15.939419] Freeing unused kernel memory: 364k freed
[   15.981021] input: AT Translated Set 2 keyboard as /class/input/input1
[   17.176608] AppArmor: AppArmor initialized<5>audit(1202744386.548:2):  type=1505 info="AppArmor initialized" pid=1185
[   17.184176] fuse init (API version 7.8)
[   17.189901] Failure registering capabilities with primary security module.
[   17.199351] ACPI: Fan [FAN] (on)
[   17.206367] ACPI: Thermal Zone [THRM] (53 C)
[   17.853539] SCSI subsystem initialized
[   17.858884] libata version 2.21 loaded.
[   17.862337] pata_sis 0000:00:02.5: version 0.5.1
[   17.862393] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 16
[   17.862603] scsi0 : pata_sis
[   17.862659] scsi1 : pata_sis
[   17.862776] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00014000 irq 14
[   17.862779] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00014008 irq 15
[   17.915596] usbcore: registered new interface driver usbfs
[   17.915633] usbcore: registered new interface driver hub
[   17.915662] usbcore: registered new device driver usb
[   17.930109] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   17.971358] sis900.c: v1.08.10 Apr. 2 2006
[   18.034678] ata1.00: ATA-7: Maxtor 6G160P0, KA201V00, max UDMA/133
[   18.034685] ata1.00: 312581808 sectors, multi 64: LBA48 
[   18.034786] ata1.01: ATA-7: SAMSUNG SP0802N, TK100-24, max UDMA/100
[   18.034789] ata1.01: 156368016 sectors, multi 16: LBA48 
[   18.050669] ata1.00: configured for UDMA/133
[   18.057603] ata1.01: configured for UDMA/100
[   18.083652] Floppy drive(s): fd0 is 1.44M
[   18.138058] FDC 0 is a post-1991 82077
[   18.540658] ata2.00: ATAPI: _NEC DVD_RW ND-3540A, 1.01, max UDMA/33
[   18.540668] ata2.01: ATAPI: HL-DT-STDVD-ROM GDR8163B, 0L23, max UDMA/33
[   18.712354] ata2.00: configured for UDMA/33
[   18.884023] ata2.01: configured for UDMA/33
[   18.884204] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6G160P0   KA20 PQ: 0 ANSI: 5
[   18.884737] scsi 0:0:1:0: Direct-Access     ATA      SAMSUNG SP0802N  TK10 PQ: 0 ANSI: 5
[   18.886370] scsi 1:0:0:0: CD-ROM            _NEC     DVD_RW ND-3540A  1.01 PQ: 0 ANSI: 5
[   18.889713] scsi 1:0:1:0: CD-ROM            HL-DT-ST DVD-ROM GDR8163B 0L23 PQ: 0 ANSI: 5
[   18.890225] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 17
[   18.890245] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   18.890642] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   18.890672] ohci_hcd 0000:00:03.0: irq 17, io mem 0xe7004000
[   18.903716] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   18.903737] sd 0:0:0:0: [sda] Write Protect is off
[   18.903740] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   18.903803] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   18.903885] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   18.903894] sd 0:0:0:0: [sda] Write Protect is off
[   18.903897] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   18.903910] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   18.903917]  sda:<6>usb usb1: configuration #1 chosen from 1 choice
[   18.945897] hub 1-0:1.0: USB hub found
[   18.945913] hub 1-0:1.0: 3 ports detected
[   19.047702] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 18
[   19.047728] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   19.047758] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[   19.047781] ohci_hcd 0000:00:03.1: irq 18, io mem 0xe7000000
[   19.105499] usb usb2: configuration #1 chosen from 1 choice
[   19.105541] hub 2-0:1.0: USB hub found
[   19.105556] hub 2-0:1.0: 3 ports detected
[   19.207392] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 19
[   19.207417] ohci_hcd 0000:00:03.2: OHCI Host Controller
[   19.207449] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[   19.207471] ohci_hcd 0000:00:03.2: irq 19, io mem 0xe7001000
[   19.265276] usb usb3: configuration #1 chosen from 1 choice
[   19.265311] hub 3-0:1.0: USB hub found
[   19.265327] hub 3-0:1.0: 2 ports detected
[   19.350991] usb 1-2: new low speed USB device using ohci_hcd and address 2
[   19.367772] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 20
[   19.367791] ehci_hcd 0000:00:03.3: EHCI Host Controller
[   19.367835] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
[   19.367886] PCI: cache line size of 64 is not supported by device 0000:00:03.3
[   19.367901] ehci_hcd 0000:00:03.3: irq 20, io mem 0xe7002000
[   19.526687] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   19.526839] usb usb4: configuration #1 chosen from 1 choice
[   19.526872] hub 4-0:1.0: USB hub found
[   19.526887] hub 4-0:1.0: 8 ports detected
[   19.630831] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 21
[   19.631763] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[   19.641006] 0000:00:04.0: Using transceiver found at address 1 as default
[   19.641891] eth0: SiS 900 PCI Fast Ethernet at 0xa800, IRQ 21, 00:11:d8:02:61:b1.
[   19.641999] sata_sis 0000:00:05.0: version 0.8
[   19.642019] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 17 (level, low) -> IRQ 22
[   19.642026] sata_sis 0000:00:05.0: Detected SiS 180/181/964 chipset in SATA mode
[   19.642163] scsi2 : sata_sis
[   19.642216] scsi3 : sata_sis
[   19.642258] ata3: SATA max UDMA/133 cmd 0x0001ac00 ctl 0x0001b002 bmdma 0x0001bc00 irq 22
[   19.642263] ata4: SATA max UDMA/133 cmd 0x0001b400 ctl 0x0001b802 bmdma 0x0001bc08 irq 22
[   19.933969] usb 1-2: device not accepting address 2, error -62
[   19.949935] ata3: SATA link down (SStatus 0 SControl 300)
[   20.269378] ata4: SATA link down (SStatus 0 SControl 300)
[   20.484999] usb 4-3: new high speed USB device using ehci_hcd and address 2
[   20.490761]  sda1
[   20.491267] sd 0:0:0:0: [sda] Attached SCSI disk
[   20.491483] sd 0:0:1:0: [sdb] 156368016 512-byte hardware sectors (80060 MB)
[   20.491498] sd 0:0:1:0: [sdb] Write Protect is off
[   20.491501] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   20.491517] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.491571] sd 0:0:1:0: [sdb] 156368016 512-byte hardware sectors (80060 MB)
[   20.491579] sd 0:0:1:0: [sdb] Write Protect is off
[   20.491582] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   20.491594] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.491598]  sdb: sdb1 sdb2 < sdb5 >
[   20.525629] sd 0:0:1:0: [sdb] Attached SCSI disk
[   20.535265] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   20.535520] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   20.535746] sr 1:0:0:0: Attached scsi generic sg2 type 5
[   20.535893] scsi 1:0:1:0: Attached scsi generic sg3 type 5
[   20.537111] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   20.537120] Uniform CD-ROM driver Revision: 3.20
[   20.537550] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   20.554690] sr1: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
[   20.554777] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   20.619224] usb 4-3: configuration #1 chosen from 1 choice
[   20.800580] usbcore: registered new interface driver libusual
[   20.808064] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   20.808073] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   20.811458] Initializing USB Mass Storage driver...
[   20.978721] Attempting manual resume
[   20.978727] swsusp: Resume From Partition 8:21
[   20.978729] PM: Checking swsusp image.
[   20.979005] PM: Resume from disk failed.
[   21.026875] kjournald starting.  Commit interval 5 seconds
[   21.026895] EXT3-fs: mounted filesystem with ordered data mode.
[   21.103922] usb 1-2: new low speed USB device using ohci_hcd and address 4
[   21.314925] usb 1-2: configuration #1 chosen from 1 choice
[   21.318031] scsi4 : SCSI emulation for USB Mass Storage devices
[   21.318084] usb-storage: device found at 2
[   21.318086] usb-storage: waiting for device to settle before scanning
[   21.318108] usbcore: registered new interface driver usb-storage
[   21.318111] USB Mass Storage support registered.
[   26.307096] usb-storage: device scan complete
[   26.310851] scsi 4:0:0:0: Direct-Access     Generic  USB Storage-CFC  I20A PQ: 0 ANSI: 0 CCS
[   26.314840] scsi 4:0:0:1: Direct-Access     Generic  USB Storage-SDC  I20A PQ: 0 ANSI: 0 CCS
[   26.316242] scsi 4:0:0:2: Direct-Access     Generic  USB Storage-SMC  I20A PQ: 0 ANSI: 0 CCS
[   26.318844] scsi 4:0:0:3: Direct-Access     Generic  USB Storage-MSC  I20A PQ: 0 ANSI: 0 CCS
[   26.326888] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[   26.326956] sd 4:0:0:0: Attached scsi generic sg4 type 0
[   26.330887] sd 4:0:0:1: [sdd] Attached SCSI removable disk
[   26.330946] sd 4:0:0:1: Attached scsi generic sg5 type 0
[   26.334901] sd 4:0:0:2: [sde] Attached SCSI removable disk
[   26.334963] sd 4:0:0:2: Attached scsi generic sg6 type 0
[   26.338426] sd 4:0:0:3: [sdf] Attached SCSI removable disk
[   26.338487] sd 4:0:0:3: Attached scsi generic sg7 type 0
[   28.638369] NET: Registered protocol family 10
[   28.638474] lo: Disabled Privacy Extensions
[   29.721674] eth0: Media Link On 100mbps full-duplex 
[   29.878532] Linux agpgart interface v0.102 (c) Dave Jones
[   29.885254] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   29.895067] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   30.034947] agpgart: Detected SiS chipset - id:1857
[   30.039901] agpgart: AGP aperture is 64M @ 0xe0000000
[   30.514634] Linux video capture interface: v2.00
[   30.618309] bttv: driver version 0.9.17 loaded
[   30.618316] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   30.618391] bttv: Bt8xx card found (0).
[   30.618428] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 23
[   30.618443] bttv0: Bt878 (rev 17) at 0000:00:0a.0, irq: 23, latency: 32, mmio: 0xe7005000
[   30.618454] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[   30.618494] bttv0: gpio: en=00000000, out=00000000 in=009fc0ff [init]
[   30.990545] input: PC Speaker as /class/input/input2
[   31.449527] tveeprom 0-0050: Huh, no eeprom present (err=-121)?
[   31.449536] bttv0: using tuner=-1
[   31.449539] bttv0: i2c: checking for MSP34xx @ 0x80... <6>usbcore: registered new interface driver xpad
[   31.522730] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   31.529841] usbcore: registered new interface driver hiddev
[   31.546265] not found
[   31.546274] bttv0: i2c: checking for TDA9875 @ 0xb0... <6>input: Dual USB Vibration Joystick as /class/input/input3
[   31.555007] input: USB HID v1.10 Joystick [Dual USB Vibration Joystick] on usb-0000:00:03.0-2
[   31.570731] input: Dual USB Vibration Joystick as /class/input/input4
[   31.570810] input: USB HID v1.10 Joystick [Dual USB Vibration Joystick] on usb-0000:00:03.0-2
[   31.570833] usbcore: registered new interface driver usbhid
[   31.570838] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   31.702950] input: ImPS/2 Logitech Wheel Mouse as /class/input/input5
[   31.705834] parport_pc 00:09: reported by Plug and Play ACPI
[   31.705937] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   31.874119] not found
[   31.874128] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   32.061980] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   32.123660] bttv0: registered device video0
[   32.123733] bttv0: registered device vbi0
[   32.123830] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 23
[   32.543828] intel8x0_measure_ac97_clock: measured 52281 usecs
[   32.543834] intel8x0: clocking to 48000
[   32.572599] bt878: AUDIO driver version 0.0.0 loaded
[   32.572677] bt878: Bt878 AUDIO function found (0).
[   32.572702] ACPI: PCI Interrupt 0000:00:0a.1[A] -> GSI 18 (level, low) -> IRQ 23
[   32.572711] bt878_probe: card id=[0x0], Unknown card.
[   32.572712] Exiting..
[   32.572717] ACPI: PCI interrupt for device 0000:00:0a.1 disabled
[   32.572723] bt878: probe of 0000:00:0a.1 failed with error -22
[   33.345190] lp0: using parport0 (interrupt-driven).
[   33.400877] Adding 3229024k swap on /dev/sdb5.  Priority:-1 extents:1 across:3229024k
[   33.811142] EXT3 FS on sdb1, internal journal
[   35.450178] input: Power Button (FF) as /class/input/input6
[   35.456129] ACPI: Power Button (FF) [PWRF]
[   35.494318] input: Power Button (CM) as /class/input/input7
[   35.500270] ACPI: Power Button (CM) [PWRB]
[   35.538503] input: Sleep Button (CM) as /class/input/input8
[   35.544450] ACPI: Sleep Button (CM) [FUTS]
[   35.562005] No dock devices found.
[   37.284447] ppdev: user-space parallel port driver
[   37.653091] audit(1202740809.005:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4884 profile="/usr/sbin/cupsd"
[   37.726246] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   37.726254] apm: overridden by ACPI.
[   38.034557] Failure registering capabilities with primary security module.
[   38.223135] Bluetooth: Core ver 2.11
[   38.223303] NET: Registered protocol family 31
[   38.223306] Bluetooth: HCI device and connection manager initialized
[   38.223311] Bluetooth: HCI socket layer initialized
[   38.249530] Bluetooth: L2CAP ver 2.8
[   38.249537] Bluetooth: L2CAP socket layer initialized
[   38.327174] Bluetooth: RFCOMM socket layer initialized
[   38.327287] Bluetooth: RFCOMM TTY layer initialized
[   38.327290] Bluetooth: RFCOMM ver 1.8
[   39.552420] [drm] Initialized drm 1.1.0 20060810
[   39.566323] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   39.570276] [drm] Initialized radeon 1.27.0 20060524 on minor 0
[   39.575494] eth0: no IPv6 routers present
[   41.654303] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   41.654447] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   41.655436] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   41.934800] [drm] Setting GART location based on new memory map
[   41.934815] [drm] Loading R300 Microcode
[   41.934858] [drm] writeback test succeeded in 1 usecs
[  468.260562] bttv0: unloading
[  496.825042] bttv: driver version 0.9.17 loaded
[  496.825051] bttv: using 8 buffers with 2080k (520 pages) each for capture
[  496.843100] bttv: Bt8xx card found (0).
[  496.843126] bttv0: Bt878 (rev 17) at 0000:00:0a.0, irq: 23, latency: 32, mmio: 0xe7005000
[  496.843286] bttv0: using: Prolink PixelView PlayTV pro [card=37,insmod option]
[  496.843326] bttv0: gpio: en=00000000, out=00000000 in=009fc0ff [init]
[  496.851956] bttv0: using tuner=0
[  496.852026] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[  496.852806] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[  496.853489] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[  496.884345] tuner 0-0060: All bytes are equal. It is not a TEA5767
[  496.884355] tuner 0-0060: chip found @ 0xc0 (bt878 #0 [sw])
[  496.884551] tuner 0-0060: type set to 0 (Temic PAL (4002 FH5))
[  496.884617] tuner 0-0060: type set to 0 (Temic PAL (4002 FH5))
[  496.884804] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[  496.892557] bttv0: registered device video0
[  496.892632] bttv0: registered device vbi0
[  496.892697] bttv0: PLL: 28636363 => 35468950 .. ok


```

post yours

---

### Post by venkatachar on 2008-02-20
Hi,
 I think you can even make your TV option work. The trick here is to select the correct tuner value.
In my country the standard is PAL_B so the following command is working for me

sudo modprobe --remove bt878 bttv
sudo modprobe bttv card=70 tuner=5 radio=1 automute=0

However the sound is not working. Can anyone please help?

Tuner Values: Choose which is applicable for your Country
```
tuner=0 - Temic PAL (4002 FH5)
tuner=1 - Philips PAL_I (FI1246 and compatibles)
tuner=2 - Philips NTSC (FI1236,FM1236 and compatibles)
tuner=3 - Philips (SECAM+PAL_BG) (FI1216MF, FM1216MF, FR1216MF)
tuner=4 - NoTuner
tuner=5 - Philips PAL_BG (FI1216 and compatibles)
tuner=6 - Temic NTSC (4032 FY5)
tuner=7 - Temic PAL_I (4062 FY5)
tuner=8 - Temic NTSC (4036 FY5)
tuner=9 - Alps HSBH1
tuner=10 - Alps TSBE1
tuner=11 - Alps TSBB5
tuner=12 - Alps TSBE5
tuner=13 - Alps TSBC5
tuner=14 - Temic PAL_BG (4006FH5)
tuner=15 - Alps TSCH6
tuner=16 - Temic PAL_DK (4016 FY5)
tuner=17 - Philips NTSC_M (MK2)
tuner=18 - Temic PAL_I (4066 FY5)
tuner=19 - Temic PAL* auto (4006 FN5)
tuner=20 - Temic PAL_BG (4009 FR5) or PAL_I (4069 FR5)
tuner=21 - Temic NTSC (4039 FR5)
tuner=22 - Temic PAL/SECAM multi (4046 FM5)
tuner=23 - Philips PAL_DK (FI1256 and compatibles)
tuner=24 - Philips PAL/SECAM multi (FQ1216ME)
tuner=25 - LG PAL_I+FM (TAPC-I001D)
tuner=26 - LG PAL_I (TAPC-I701D)
tuner=27 - LG NTSC+FM (TPI8NSR01F)
tuner=28 - LG PAL_BG+FM (TPI8PSB01D)
tuner=29 - LG PAL_BG (TPI8PSB11D)
tuner=30 - Temic PAL* auto + FM (4009 FN5)
tuner=31 - SHARP NTSC_JP (2U5JF5540)
tuner=32 - Samsung PAL TCPM9091PD27
tuner=33 - MT20xx universal
tuner=34 - Temic PAL_BG (4106 FH5)
tuner=35 - Temic PAL_DK/SECAM_L (4012 FY5)
tuner=36 - Temic NTSC (4136 FY5)
tuner=37 - LG PAL (newer TAPC series)
tuner=38 - Philips PAL/SECAM multi (FM1216ME MK3)
tuner=39 - LG NTSC (newer TAPC series)
tuner=40 - HITACHI V7-J180AT
tuner=41 - Philips PAL_MK (FI1216 MK)
tuner=42 - Philips 1236D ATSC/NTSC daul in
tuner=43 - Philips NTSC MK3 (FM1236MK3 or FM1236/F)
tuner=44 - Philips 4 in 1 (ATI TV Wonder Pro/Conexant)
tuner=45 - Microtune 4049 FM5
tuner=46 - Panasonic VP27s/ENGE4324D
tuner=47 - LG NTSC (TAPE series)
tuner=48 - Tenna TNF 8831 BGFF)
tuner=49 - Microtune 4042 FI5 ATSC/NTSC dual in
tuner=50 - TCL 2002N
tuner=51 - Philips PAL/SECAM_D (FM 1256 I-H3)
tuner=52 - Thomson DDT 7610 (ATSC/NTSC)
tuner=53 - Philips FQ1286
tuner=54 - tda8290+75
tuner=55 - TCL 2002MB
tuner=56 - Philips PAL/SECAM multi (FQ1216AME MK4)
tuner=57 - Philips FQ1236A MK4
tuner=58 - Ymec TVision TVF-8531MF/8831MF/8731MF
tuner=59 - Ymec TVision TVF-5533MF
tuner=60 - Thomson DDT 7611 (ATSC/NTSC)
tuner=61 - Tena TNF9533-D/IF/TNF9533-B/DF
tuner=62 - Philips TEA5767HN FM Radio
tuner=63 - Philips FMD1216ME MK3 Hybrid Tuner
tuner=64 - LG TDVS-H062F/TUA6034
tuner=65 - Ymec TVF66T5-B/DFF
tuner=66 - LG NTSC (TALN mini series)
tuner=67 - Philips TD1316 Hybrid Tuner
tuner=68 - Philips TUV1236D ATSC/NTSC dual in
tuner=69 - Tena TNF 5335 MF
```

---

