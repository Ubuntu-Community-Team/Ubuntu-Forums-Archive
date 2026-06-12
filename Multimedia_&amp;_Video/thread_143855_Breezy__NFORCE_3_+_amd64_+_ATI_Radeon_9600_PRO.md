---
title: "Breezy : NFORCE 3 + amd64 + ATI Radeon 9600 PRO"
date: 2006-03-13
forum: Multimedia &amp; Video
---

### Post by lepoulpe303 on 2006-03-13
Hi all

I tried without success a lot of tutorials about how to install drivers for my ATI Radeon 9600 Pro on Ubuntu 5.10 .

I'm stuck on a problem that may not come from the drivers but either the AGP support ;i tried to install NFORCE3 drivers without more results.

I have an ASUS k8N motherboard(NVIDIA Chipset) with amd64 processeur ; i tried both i386 and k7 kernel without success.

I always have the following lines in dmesg :
> ...
[4294672.197000] NFORCE3-250: not 100% native mode: will probe irqs later
[4294672.197000] NFORCE3-250: BIOS didn't set cable bits correctly. Enabling workaround.
...
[4294694.061000] agpgart: Detected AGP bridge 0
[4294694.061000] agpgart: Setting up Nforce3 AGP.
---
[4294706.935000] [fglrx] Maximum main memory to use for locked dma buffers: 432 MBytes.
[4294706.935000] [fglrx:firegl_unlock] *ERROR* Process 7003 using kernel context 0


/var/log/xorg.0.log  content :


> (II) LoadModule: "fglrx"
...
(II) fglrx(0): AGP card detected
...
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): MonitorLayout is no longer supported.
(WW) fglrx(0): The hex number setting for DesktopSetup is deprecated,
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENODEV"
(EE) fglrx(0): cannot init AGP
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xe0c03000 at 0xb7b3b000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

So if anyone has any advice to give (excpet "buy an NVIDIA adapter" or "install windows for 3D") I would be happy ; i will probably try ubuntu 64 bits version but with no real hope ...


Thanks for paying attention ...

---

### Post by Mouth on 2006-04-24
I have the exact same hardware (NForce3, 9600, and AMD64) and the same issue. Have you been able to resolve it?

---

### Post by lepoulpe303 on 2006-04-24
unfortunately not :( 

i've reinstalled the crappy redmond production in dual boot ....

Someone told me that a fix exists for dapper... if you need further info tell me

---

### Post by Mouth on 2006-04-24
[QUOTE=lepoulpe303]Someone told me that a fix exists for dapper... if you need further info tell me[/QUOTE]
Yes please.

---

### Post by lepoulpe303 on 2006-04-24
the guy i know who made it work wrote an wiki page in the french ubuntu site, but here is an english page he used as a basis :

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")

Good luck ! 

Personaly i'll wait 1st June .....

---

### Post by alanrr_sr on 2006-06-11
I have a k8n-e and a 9550... 
same problem, dapper 32 or 64 or breezy

Funny: If I boot in windows, and after that reboot on linux, 3d acceleration just works.

---

### Post by lepoulpe303 on 2006-06-12
I tried install again with Dapper without any success.

Please note that for me all works ok on Kororaa 0.2 !

I'll try to find if this livecd may help me to find which settings i need to make the job with ubuntu...

---

### Post by dm1024 on 2006-06-16
I found, that there is no agpgart or agp_amd64 modules in my distibution (Ubuntu for AMD64). Should I compile the kernel or there is some workaround for it?

---

### Post by Andre Moraes on 2006-06-17
[QUOTE=alanrr_sr]I have a k8n-e and a 9550... 
same problem, dapper 32 or 64 or breezy

Funny: If I boot in windows, and after that reboot on linux, 3d acceleration just works.[/QUOTE]

Hi, Alanrr_sr

I've getting the same here, with Asus K8N and RX 9550 (MSI). I've tried 64-bits versions (SUSE, Ubuntu, Mandriva, et alli) and when I boot a 64-bits distro and reboot in Breezy it works fine, with Dapper nothing works... :-(

---

### Post by dm1024 on 2006-06-17
[QUOTE=Andre Moraes]Hi, Alanrr_sr

I've getting the same here, with Asus K8N and RX 9550 (MSI). I've tried 64-bits versions (SUSE, Ubuntu, Mandriva, et alli) and when I boot a 64-bits distro and reboot in Breezy it works fine, with Dapper nothing works... :-([/QUOTE]

I have AGP video card. And in this distro there is no **agpgart** module. I think compiling the kernel from sources will fix this issue, but after that fglrx drivers should be installed from ati binary distribution (*.run), not from ubuntu package. And I'm not sure that all parts of Ubuntu will work fine after manual kernel compilation.

---

### Post by Andre Moraes on 2006-06-17
[QUOTE=alanrr_sr]I have a k8n-e and a 9550... 
same problem, dapper 32 or 64 or breezy

Funny: If I boot in windows, and after that reboot on linux, 3d acceleration just works.[/QUOTE]

Hi, Alanrr_sr

I've getting the same here, with Asus K8N and RX 9550 (MSI). I've tried 64-bits versions (SUSE, Ubuntu, Mandriva, et alli) and when I boot a 64-bits distro and reboot in Breezy it works fine, with Dapper nothing works... :-(

---

### Post by Andre Moraes on 2006-06-26
Problem solved, at last: after hours and hours (and hours and hours) spanking my head on the wall, I've came across a thread from kernel development about this issue. The solution? Downgrade your bios.

Yes, it's true: I've downgraded my bios from version 1011 (Beta) to 1006 and agpgart problems are gone, mtrr problems are gone and my radeon FX 9550 is working fine and from cold boot without problems, using kernel 2.6.15-25-686. I'll paste dmesg output below:

> [17179569.184000] Linux version 2.6.15-25-686 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Wed Jun 14 11:34:19 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003ffc0000 (usable)
[17179569.184000]  BIOS-e820: 000000003ffc0000 - 000000003ffd0000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000003ffd0000 - 0000000040000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff7c0000 - 0000000100000000 (reserved)
[17179569.184000] 127MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000ff780
[17179569.184000] On node 0 totalpages: 262080
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32704 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000fa010
[17179569.184000] ACPI: RSDT (v001 A M I  OEMRSDT  0x05000504 MSFT 0x00000097) @ 0x3ffc0000
[17179569.184000] ACPI: FADT (v002 A M I  OEMFACP  0x05000504 MSFT 0x00000097) @ 0x3ffc0200
[17179569.184000] ACPI: MADT (v001 A M I  OEMAPIC  0x05000504 MSFT 0x00000097) @ 0x3ffc0390
[17179569.184000] ACPI: OEMB (v001 A M I  OEMBIOS  0x05000504 MSFT 0x00000097) @ 0x3ffd0040
[17179569.184000] ACPI: DSDT (v001  A0128 A0128003 0x00000003 INTL 0x02002026) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x4008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:12 APIC version 16
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: BIOS IRQ0 pin2 override ignored.
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] ACPI: IRQ14 used by override.
[17179569.184000] ACPI: IRQ15 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 2009.971 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.436000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.436000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.460000] Memory: 1027052k/1048320k available (2101k kernel code, 20596k reserved, 592k data, 332k init, 130816k highmem)
[17179569.460000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.540000] Calibrating delay using timer specific routine.. 4024.12 BogoMIPS (lpj=8048253)
[17179569.540000] Security Framework v1.0.0 initialized
[17179569.540000] SELinux:  Disabled at boot.
[17179569.540000] Mount-cache hash table entries: 512
[17179569.540000] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000000
[17179569.540000] CPU: After vendor identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000000
[17179569.540000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179569.540000] CPU: L2 Cache: 512K (64 bytes/line)
[17179569.540000] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000000
[17179569.540000] mtrr: v2.0 (20020519)
[17179569.540000] Enabling fast FPU save and restore... done.
[17179569.540000] Enabling unmasked SIMD FPU exception support... done.
[17179569.540000] Checking 'hlt' instruction... OK.
[17179569.556000] SMP alternatives: switching to UP code
[17179569.556000] checking if image is initramfs... it is
[17179570.072000] Freeing initrd memory: 6801k freed
[17179570.080000] ACPI: Looking for DSDT ... not found!
[17179570.080000] CPU0: AMD Athlon(tm) 64 Processor 3000+ stepping 02
[17179570.080000] Total of 1 processors activated (4024.12 BogoMIPS).
[17179570.084000] ENABLING IO-APIC IRQs
[17179570.084000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179570.228000] Brought up 1 CPUs
[17179570.228000] NET: Registered protocol family 16
[17179570.228000] EISA bus registered
[17179570.228000] ACPI: bus type pci registered
[17179570.228000] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[17179570.228000] PCI: Using configuration type 1
[17179570.228000] ACPI: Subsystem revision 20051216
[17179570.232000] ACPI: Interpreter enabled
[17179570.232000] ACPI: Using IOAPIC for interrupt routing
[17179570.232000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.232000] PCI: Probing PCI hardware (bus 00)
[17179570.236000] Boot video device is 0000:01:00.0
[17179570.236000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.248000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[17179570.248000] ACPI: Power Resource [ISAV] (on)
[17179570.248000] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[17179570.248000] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[17179570.248000] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *11
[17179570.252000] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[17179570.252000] ACPI: PCI Interrupt Link [LNKE] (IRQs 16 17 18 19) *11
[17179570.252000] ACPI: PCI Interrupt Link [LUS0] (IRQs 20 21 22) *3
[17179570.252000] ACPI: PCI Interrupt Link [LUS1] (IRQs 20 21 22) *9
[17179570.252000] ACPI: PCI Interrupt Link [LUS2] (IRQs 20 21 22) *10
[17179570.252000] ACPI: PCI Interrupt Link [LKLN] (IRQs 20 21 22) *11
[17179570.252000] ACPI: PCI Interrupt Link [LAUI] (IRQs 20 21 22) *0, disabled.
[17179570.252000] ACPI: PCI Interrupt Link [LKMO] (IRQs 20 21 22) *0, disabled.
[17179570.252000] ACPI: PCI Interrupt Link [LKSM] (IRQs 20 21 22) *0, disabled.
[17179570.256000] ACPI: PCI Interrupt Link [LTID] (IRQs 20 21 22) *0
[17179570.256000] ACPI: PCI Interrupt Link [LTIE] (IRQs 20 21 22) *0, disabled.
[17179570.256000] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22) *14
[17179570.256000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.256000] pnp: PnP ACPI init
[17179570.260000] pnp: PnP ACPI: found 14 devices
[17179570.260000] PnPBIOS: Disabled by ACPI PNP
[17179570.260000] PCI: Using ACPI for IRQ routing
[17179570.260000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.264000] pnp: 00:0a: ioport range 0x480-0x487 has been reserved
[17179570.264000] pnp: 00:0a: ioport range 0xd00-0xd07 has been reserved
[17179570.268000] PCI: Bridge: 0000:00:0b.0
[17179570.268000]   IO window: b000-bfff
[17179570.268000]   MEM window: ff500000-ff5fffff
[17179570.268000]   PREFETCH window: ceb00000-eeafffff
[17179570.268000] PCI: Bridge: 0000:00:0e.0
[17179570.268000]   IO window: c000-cfff
[17179570.268000]   MEM window: disabled.
[17179570.268000]   PREFETCH window: disabled.
[17179570.268000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[17179570.268000] audit: initializing netlink socket (disabled)
[17179570.268000] audit(1151362493.264:1): initialized
[17179570.268000] highmem bounce pool size: 64 pages
[17179570.268000] VFS: Disk quotas dquot_6.5.1
[17179570.268000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.268000] Initializing Cryptographic API
[17179570.268000] io scheduler noop registered
[17179570.268000] io scheduler anticipatory registered
[17179570.268000] io scheduler deadline registered
[17179570.268000] io scheduler cfq registered
[17179570.268000] isapnp: Scanning for PnP cards...
[17179570.620000] isapnp: No Plug & Play device found
[17179570.632000] Real Time Clock Driver v1.12
[17179570.632000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[17179570.632000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179570.640000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179570.640000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179570.640000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179570.640000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.640000] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.640000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179570.640000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.640000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179570.640000] mice: PS/2 mouse device common for all mice
[17179570.640000] EISA: Probing bus 0 at eisa.0
[17179570.640000] Cannot allocate resource for EISA slot 4
[17179570.640000] Cannot allocate resource for EISA slot 5
[17179570.640000] EISA: Detected 0 cards.
[17179570.640000] NET: Registered protocol family 2
[17179570.676000] IP route cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179570.676000] TCP established hash table entries: 262144 (order: 9, 3145728 bytes)
[17179570.680000] TCP bind hash table entries: 65536 (order: 7, 786432 bytes)
[17179570.680000] TCP: Hash tables configured (established 262144 bind 65536)
[17179570.680000] TCP reno registered
[17179570.680000] TCP bic registered
[17179570.680000] NET: Registered protocol family 1
[17179570.680000] NET: Registered protocol family 8
[17179570.680000] NET: Registered protocol family 20
[17179570.680000] Using IPI No-Shortcut mode
[17179570.680000] ACPI wakeup devices: 
[17179570.680000] PS2K UAR1 USB0  MAC USB1 USB2 P0P1 
[17179570.680000] ACPI: (supports S0 S1 S3 S4 S5)
[17179570.680000] Freeing unused kernel memory: 332k freed
[17179570.724000] vga16fb: initializing
[17179570.724000] vga16fb: mapped to 0xc00a0000
[17179570.832000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179570.860000] Console: switching to colour frame buffer device 80x25
[17179570.860000] fb0: VGA16 VGA frame buffer device
[17179572.024000] Capability LSM initialized
[17179572.624000] SCSI subsystem initialized
[17179572.624000] ACPI: bus type scsi registered
[17179572.624000] libata version 1.20 loaded.
[17179572.624000] sata_nv 0000:00:0a.0: version 0.8
[17179572.624000] **** SET: Misaligned resource pointer: dfee4b82 Type 07 Len 0
[17179572.624000] ACPI: PCI Interrupt Link [LTID] BIOS reported IRQ 0, using IRQ 22
[17179572.624000] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 22
[17179572.624000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LTID] -> GSI 22 (level, low) -> IRQ 177
[17179572.628000] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[17179572.628000] ata1: SATA max UDMA/133 cmd 0x9F0 ctl 0xBF2 bmdma 0xD400 irq 177
[17179572.628000] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xB72 bmdma 0xD408 irq 177
[17179572.832000] ata1: no device found (phy stat 00000000)
[17179572.832000] scsi0 : sata_nv
[17179573.040000] ata2: no device found (phy stat 00000000)
[17179573.040000] scsi1 : sata_nv
[17179573.044000] NFORCE3-250: IDE controller at PCI slot 0000:00:08.0
[17179573.044000] NFORCE3-250: chipset revision 162
[17179573.044000] NFORCE3-250: not 100% native mode: will probe irqs later
[17179573.044000] NFORCE3-250: BIOS didn't set cable bits correctly. Enabling workaround.
[17179573.044000] NFORCE3-250: BIOS didn't set cable bits correctly. Enabling workaround.
[17179573.044000] NFORCE3-250: 0000:00:08.0 (rev a2) UDMA133 controller
[17179573.044000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
[17179573.044000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:pio
[17179573.044000] Probing IDE interface ide0...
[17179573.336000] hda: SAMSUNG SP0411N, ATA DISK drive
[17179573.620000] hdb: SAMSUNG SP0802N, ATA DISK drive
[17179573.680000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179573.680000] Probing IDE interface ide1...
[17179574.424000] hdc: SONY DVD RW DRU-710A, ATAPI CD/DVD-ROM drive
[17179575.104000] ide1 at 0x170-0x177,0x376 on irq 15
[17179575.112000] hda: max request size: 1024KiB
[17179575.120000] hda: 78242976 sectors (40060 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[17179575.124000] hda: cache flushes supported
[17179575.124000]  hda: hda1 hda2 hda3 hda4
[17179575.136000] hdb: max request size: 1024KiB
[17179575.140000] hdb: 156368016 sectors (80060 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[17179575.140000] hdb: cache flushes supported
[17179575.140000]  hdb: hdb1 hdb2 hdb3
[17179575.144000] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[17179575.144000] Uniform CD-ROM driver Revision: 3.20
[17179575.708000] usbcore: registered new driver usbfs
[17179575.708000] usbcore: registered new driver hub
[17179575.712000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179575.712000] **** SET: Misaligned resource pointer: dfee47c2 Type 07 Len 0
[17179575.712000] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 21
[17179575.712000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LUS0] -> GSI 21 (level, low) -> IRQ 185
[17179575.712000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[17179575.712000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[17179575.732000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[17179575.732000] ohci_hcd 0000:00:02.0: irq 185, io mem 0xff6fd000
[17179575.756000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.48.
[17179575.792000] hub 1-0:1.0: USB hub found
[17179575.792000] hub 1-0:1.0: 4 ports detected
[17179575.900000] **** SET: Misaligned resource pointer: dfee4642 Type 07 Len 0
[17179575.900000] ACPI: PCI Interrupt Link [LUS1] enabled at IRQ 20
[17179575.900000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LUS1] -> GSI 20 (level, low) -> IRQ 193
[17179575.900000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[17179575.900000] ohci_hcd 0000:00:02.1: OHCI Host Controller
[17179575.920000] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[17179575.920000] ohci_hcd 0000:00:02.1: irq 193, io mem 0xff6fe000
[17179575.980000] hub 2-0:1.0: USB hub found
[17179575.980000] hub 2-0:1.0: 4 ports detected
[17179576.088000] **** SET: Misaligned resource pointer: dfee44c2 Type 07 Len 0
[17179576.088000] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[17179576.088000] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [LUS2] -> GSI 22 (level, low) -> IRQ 177
[17179576.088000] PCI: Setting latency timer of device 0000:00:02.2 to 64
[17179576.088000] ehci_hcd 0000:00:02.2: EHCI Host Controller
[17179576.088000] ehci_hcd 0000:00:02.2: debug port 1
[17179576.088000] PCI: cache line size of 64 is not supported by device 0000:00:02.2
[17179576.088000] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[17179576.088000] ehci_hcd 0000:00:02.2: irq 177, io mem 0xff6ffc00
[17179576.088000] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179576.088000] hub 3-0:1.0: USB hub found
[17179576.088000] hub 3-0:1.0: 8 ports detected
[17179576.196000] **** SET: Misaligned resource pointer: dfee4342 Type 07 Len 0
[17179576.196000] ACPI: PCI Interrupt Link [LKLN] enabled at IRQ 21
[17179576.196000] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LKLN] -> GSI 21 (level, low) -> IRQ 185
[17179576.196000] PCI: Setting latency timer of device 0000:00:05.0 to 64
[17179576.720000] eth0: forcedeth.c: subsystem: 01043:80a7 bound to 0000:00:05.0
[17179576.828000] Attempting manual resume
[17179576.844000] kjournald starting.  Commit interval 5 seconds
[17179576.844000] EXT3-fs: mounted filesystem with ordered data mode.
[17179577.084000] usb 1-1: new low speed USB device using ohci_hcd and address 3
[17179577.628000] usb 1-2: new full speed USB device using ohci_hcd and address 4
[17179584.868000] Linux agpgart interface v0.101 (c) Dave Jones
[17179584.868000] agpgart: Detected AGP bridge 0
[17179584.868000] agpgart: Setting up Nforce3 AGP.
[17179584.872000] agpgart: AGP aperture is 128M @ 0xf0000000
[17179585.236000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179585.240000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179585.308000] input: PC Speaker as /class/input/input1
[17179585.364000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x5000
[17179585.364000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x5040
[17179585.668000] usbcore: registered new driver hiddev
[17179585.680000] gameport: EMU10K1 is pci0000:02:08.1/gameport0, io 0xcc00, speed 1193kHz
[17179585.696000] Floppy drive(s): fd0 is 1.44M
[17179585.708000] input: Microsoft Microsoft IntelliMouse Explorer as /class/input/input2
[17179585.708000] input: USB HID v1.11 Mouse [Microsoft Microsoft IntelliMouse Explorer] on usb-0000:00:02.0-1
[17179585.708000] usbcore: registered new driver usbhid
[17179585.708000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179585.724000] FDC 0 is a post-1991 82077
[17179585.884000] Linux video capture interface: v1.00
[17179585.936000] parport: PnPBIOS parport detected.
[17179585.936000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179586.040000] drivers/usb/media/spca5xx/spca5xx-main.c: USB SPCA5XX camera found. Type Creative NX Pro Zc301+hv7131b
[17179586.108000] **** SET: Misaligned resource pointer: dfa31f42 Type 07 Len 0
[17179586.108000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 19
[17179586.108000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKC] -> GSI 19 (level, low) -> IRQ 201
[17179586.204000] usbcore: registered new driver spca5xx
[17179586.204000] drivers/usb/media/spca5xx/spca5xx-main.c: spca5xx driver 00.57.08 registered
[17179586.224000] ts: Compaq touchscreen protocol output
[17179586.924000] lp0: using parport0 (interrupt-driven).
[17179586.972000] Adding 2096472k swap on /dev/hda2.  Priority:-1 extents:1 across:2096472k
[17179587.152000] EXT3 FS on hda1, internal journal
[17179587.296000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179587.296000] md: bitmap version 4.39
[17179587.860000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179588.792000] cdrom: open failed.
[17179589.408000] kjournald starting.  Commit interval 5 seconds
[17179589.408000] EXT3 FS on hdb2, internal journal
[17179589.408000] EXT3-fs: mounted filesystem with ordered data mode.
[17179589.408000] kjournald starting.  Commit interval 5 seconds
[17179589.408000] EXT3 FS on hdb3, internal journal
[17179589.408000] EXT3-fs: mounted filesystem with ordered data mode.
[17179589.408000] kjournald starting.  Commit interval 5 seconds
[17179589.408000] EXT3 FS on hda3, internal journal
[17179589.408000] EXT3-fs: mounted filesystem with ordered data mode.
[17179591.528000] ACPI: Power Button (FF) [PWRF]
[17179591.528000] ACPI: Power Button (CM) [PWRB]
[17179591.616000] ibm_acpi: ec object not found
[17179591.648000] pcc_acpi: loading...
[17179592.172000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.50.4)
[17179592.176000] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[17179594.064000] ppdev: user-space parallel port driver
[17179594.336000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179594.336000] apm: overridden by ACPI.
[17179597.612000] NET: Registered protocol family 10
[17179597.612000] lo: Disabled Privacy Extensions
[17179597.612000] IPv6 over IPv4 tunneling driver
[17179598.304000] Bluetooth: Core ver 2.8
[17179598.304000] NET: Registered protocol family 31
[17179598.304000] Bluetooth: HCI device and connection manager initialized
[17179598.304000] Bluetooth: HCI socket layer initialized
[17179598.316000] Bluetooth: L2CAP ver 2.8
[17179598.316000] Bluetooth: L2CAP socket layer initialized
[17179598.320000] Bluetooth: RFCOMM socket layer initialized
[17179598.320000] Bluetooth: RFCOMM TTY layer initialized
[17179598.320000] Bluetooth: RFCOMM ver 1.7
[17179599.988000] NET: Registered protocol family 17
[17179614.116000] eth1: no IPv6 routers present
[17179666.272000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179666.276000] [fglrx] Maximum main memory to use for locked dma buffers: 928 MBytes.
[17179666.276000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[17179666.532000] **** SET: Misaligned resource pointer: f75d8402 Type 07 Len 0
[17179666.532000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 18
[17179666.532000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKE] -> GSI 18 (level, low) -> IRQ 209
[17179667.388000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[17179667.388000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[17179667.388000] [fglrx] AGP detected, AgpState   = 0x1f00421b (hardware caps of chipset)
[17179667.388000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[17179667.388000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17179667.388000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[17179667.388000] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[17179667.400000] [fglrx] total      GART = 134217728
[17179667.400000] [fglrx] free       GART = 118222848
[17179667.400000] [fglrx] max single GART = 118222848
[17179667.400000] [fglrx] total      LFB  = 128970752
[17179667.400000] [fglrx] free       LFB  = 122679296
[17179667.400000] [fglrx] max single LFB  = 122679296
[17179667.400000] [fglrx] total      Inv  = 0
[17179667.400000] [fglrx] free       Inv  = 0
[17179667.400000] [fglrx] max single Inv  = 0
[17179667.400000] [fglrx] total      TIM  = 0
[17179733.692000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[17179733.692000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[17179733.692000] [fglrx] AGP detected, AgpState   = 0x1f00421b (hardware caps of chipset)
[17179733.692000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[17179733.692000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17179733.692000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[17179733.692000] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[17179733.700000] [fglrx] total      GART = 134217728
[17179733.700000] [fglrx] free       GART = 118222848
[17179733.700000] [fglrx] max single GART = 118222848
[17179733.700000] [fglrx] total      LFB  = 128970752
[17179733.700000] [fglrx] free       LFB  = 122679296
[17179733.700000] [fglrx] max single LFB  = 122679296
[17179733.700000] [fglrx] total      Inv  = 0
[17179733.700000] [fglrx] free       Inv  = 0
[17179733.700000] [fglrx] max single Inv  = 0
[17179733.700000] [fglrx] total      TIM  = 0

Hope it helps.

Best Regards. 

André

---

### Post by alanrr_sr on 2006-08-02
> **Andre Moraes said:**
> Problem solved, at last: after hours and hours (and hours and hours) spanking my head on the wall, I've came across a thread from kernel development about this issue. The solution? Downgrade your bios.

Yes, it's true: I've downgraded my bios from version 1011 (Beta) to 1006 and agpgart problems are gone, mtrr problems are gone and my radeon FX 9550 is working fine and from cold boot without problems, using kernel 2.6.15-25-686. I'll paste dmesg output below:


Hope it helps.

Best Regards. 

André



Oh, Thanks!!!! It is working now... thanks a lot, a lot, a lot.... I was not able to find the problem in kernel dev... do you have the link???

THANKS!!!!!

---

### Post by alanrr_sr on 2006-12-03
Edgy (or the kernel) has solved the problem with ati 9550, nforce3 and fglrx issues in the latest bios??

Thx in advance

---

### Post by lepoulpe303 on 2007-02-09
I'm still stuck with this problem.

Moving to Edgy didn't changed anything , except no more error messages in dmesg.

(only DRI missing in xorg.0.log and fglrxinfo).

And furthermore, LiveCDs (Kororaa, Mandriva) give me AIGL/Beryl/Compiz/Whatever functionalities ....

So i don't want to take the risk to downgrade bios just for a problem totally linked to Ubuntu . I wouldn't be very happy to move to Mandriva, but , what about all my friends that are proud of their crappy aero vista effects, at who i spoke about XGL , that were  enthusiasts ... And now, i have no more credibility : this thing doesn't work on my PC.... ;)
 


Any suggestions about things to compare between Mandriva and Ubuntu to determine where the problem come from ?

---

### Post by JackCorbae on 2007-03-22
Or upgrade your BIOS to 1012 beta! I have a K8N-E Deluxe and a Radeon x1950 Pro AGP. I had all the same symptoms as many others and fglrxinfo kept reporting Mesa as the default OpenGL driver.
I flashed the BIOS to 1012 and voila! Fully functional ATI drivers running 1680x1050 beautifully!
Not sure if the beta status of the BIOS is a major concern, The file date on it was mid-2006.

---

