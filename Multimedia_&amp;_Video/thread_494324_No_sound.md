---
title: "No sound"
date: 2007-07-06
forum: Multimedia &amp; Video
---

### Post by Nergar on 2007-07-06
Yesterday everything was working correctly but today I can't get the sound to work. 

I installed apache2 and played with some users and passwords but i really dont think that caused the problem

heres my lspci
```
daniel@ubuntu-pc:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:08.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
00:08.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
00:08.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
00:09.0 Network controller: RaLink RT2561/RT61 802.11g PCI
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]
daniel@ubuntu-pc:~$ 

```

and here is my dmsg
```
daniel@ubuntu-pc:~$ sudo dmesg 
ç[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 00000000000a0000 end: 00000000000a0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000002def0000 end: 000000002dff0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000002dff0000 size: 0000000000003000 end: 000000002dff3000 type: 4
[    0.000000] copy_e820_map() start: 000000002dff3000 size: 000000000000d000 end: 000000002e000000 type: 3
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000001400000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002dff0000 (usable)
[    0.000000]  BIOS-e820: 000000002dff0000 - 000000002dff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000002dff3000 - 000000002e000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 735MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f54c0
[    0.000000] Entering add_active_range(0, 0, 188400) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   188400
[    0.000000]   HighMem    188400 ->   188400
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   188400
[    0.000000] On node 0 totalpages: 188400
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1439 pages used for memmap
[    0.000000]   Normal zone: 182865 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 VIAP4X                                ) @ 0x000f6e70
[    0.000000] ACPI: RSDT (v001 VIAP4X AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x2dff3000
[    0.000000] ACPI: FADT (v001 VIAP4X AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x2dff3040
[    0.000000] ACPI: MADT (v001 VIAP4X AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x2dff6d80
[    0.000000] ACPI: DSDT (v001 VIAP4X AWRDACPI 0x00001000 MSFT 0x0100000d) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 2e000000:d0c00000)
[    0.000000] Detected 2388.518 MHz processor.
[   29.177965] Built 1 zonelists.  Total pages: 186929
[   29.177974] Kernel command line: root=UUID=7c3b4dfb-9ee6-4a87-8370-63ea9796c4eb ro quiet splash
[   29.178167] mapped APIC to ffffd000 (fee00000)
[   29.178170] mapped IOAPIC to ffffc000 (fec00000)
[   29.178174] Enabling fast FPU save and restore... done.
[   29.178178] Enabling unmasked SIMD FPU exception support... done.
[   29.178195] Initializing CPU#0
[   29.178312] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   29.179899] Console: colour VGA+ 80x25
[   29.180753] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   29.182292] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   29.202895] Memory: 735804k/753600k available (1992k kernel code, 17152k reserved, 900k data, 328k init, 0k highmem)
[   29.202908] virtual kernel memory layout:
[   29.202909]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   29.202910]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   29.202912]     vmalloc : 0xee800000 - 0xff7fe000   ( 271 MB)
[   29.202913]     lowmem  : 0xc0000000 - 0xedff0000   ( 735 MB)
[   29.202914]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   29.202915]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   29.202916]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   29.202920] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   29.282140] Calibrating delay using timer specific routine.. 4782.46 BogoMIPS (lpj=9564928)
[   29.282217] Security Framework v1.0.0 initialized
[   29.282229] SELinux:  Disabled at boot.
[   29.282266] Mount-cache hash table entries: 512
[   29.282522] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[   29.282542] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   29.282546] CPU: L2 cache: 128K
[   29.282548] CPU: Hyper-Threading is disabled
[   29.282551] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003080 00004400 00000000 00000000
[   29.282569] Compat vDSO mapped to ffffe000.
[   29.282574] Remapping vsyscall page to ffffe000
[   29.282593] Checking 'hlt' instruction... OK.
[   29.298276] SMP alternatives: switching to UP code
[   29.298758] Freeing SMP alternatives: 11k freed
[   29.299122] Early unpacking initramfs... done
[   29.664749] ACPI: Core revision 20060707
[   29.671779] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   29.676505] CPU0: Intel(R) Celeron(R) CPU 2.40GHz stepping 09
[   29.676562] Total of 1 processors activated (4782.46 BogoMIPS).
[   29.677331] ENABLING IO-APIC IRQs
[   29.677673] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   29.821317] Brought up 1 CPUs
[   29.821762] Booting paravirtualized kernel on bare hardware
[   29.821966] Time: 17:37:49  Date: 06/06/107
[   29.822044] NET: Registered protocol family 16
[   29.822298] EISA bus registered
[   29.822314] ACPI: bus type pci registered
[   29.855428] PCI: PCI BIOS revision 2.10 entry at 0xfb550, last bus=1
[   29.855431] PCI: Using configuration type 1
[   29.855434] Setting up standard PCI resources
[   29.875260] ACPI: Interpreter enabled
[   29.875270] ACPI: Using IOAPIC for interrupt routing
[   29.877148] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   29.877160] PCI: Probing PCI hardware (bus 00)
[   29.878282] PCI quirk: region 0400-047f claimed by vt8235 PM
[   29.878289] PCI quirk: region 0500-050f claimed by vt8235 SMB
[   29.878789] Boot video device is 0000:01:00.0
[   29.878880] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   29.926692] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[   29.927321] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 10 11 *12 14 15)
[   29.927957] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
[   29.928584] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 *3 4 5 6 7 10 11 12 14 15)
[   29.929285] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0, disabled.
[   29.929954] ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0, disabled.
[   29.930672] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0, disabled.
[   29.931343] ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0, disabled.
[   29.937243] Linux Plug and Play Support v0.97 (c) Adam Belay
[   29.937279] pnp: PnP ACPI init
[   29.944960] pnp: PnP ACPI: found 14 devices
[   29.944973] PnPBIOS: Disabled by ACPI PNP
[   29.945159] PCI: Using ACPI for IRQ routing
[   29.945167] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   29.986278] NET: Registered protocol family 8
[   29.986282] NET: Registered protocol family 20
[   29.987044] pnp: 00:02: ioport range 0x400-0x47f could not be reserved
[   29.987050] pnp: 00:02: ioport range 0x500-0x50f has been reserved
[   29.988283] PCI: Bridge: 0000:00:01.0
[   29.988289]   IO window: disabled.
[   29.988296]   MEM window: ec000000-edffffff
[   29.988302]   PREFETCH window: e0000000-e7ffffff
[   29.988329] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   29.988406] NET: Registered protocol family 2
[   30.025024] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   30.025462] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   30.027450] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   30.028494] TCP: Hash tables configured (established 131072 bind 65536)
[   30.028504] TCP reno registered
[   30.037096] checking if image is initramfs... it is
[   30.733057] Freeing initrd memory: 6766k freed
[   30.734235] audit: initializing netlink socket (disabled)
[   30.734265] audit(1183743469.640:1): initialized
[   30.734637] VFS: Disk quotas dquot_6.5.1
[   30.734680] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   30.734792] io scheduler noop registered
[   30.734798] io scheduler anticipatory registered
[   30.734801] io scheduler deadline registered
[   30.734831] io scheduler cfq registered (default)
[   30.735545] isapnp: Scanning for PnP cards...
[   31.089426] isapnp: No Plug & Play device found
[   31.257146] Real Time Clock Driver v1.12ac
[   31.257301] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   31.257516] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   31.260061] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   31.261020] mice: PS/2 mouse device common for all mice
[   31.263083] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   31.263479] input: Macintosh mouse button emulation as /class/input/input0
[   31.263608] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   31.263616] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   31.264279] PNP: No PS/2 controller found. Probing ports directly.
[   31.264849] serio: i8042 KBD port at 0x60,0x64 irq 1
[   31.264862] serio: i8042 AUX port at 0x60,0x64 irq 12
[   31.265271] EISA: Probing bus 0 at eisa.0
[   31.265318] EISA: Detected 0 cards.
[   31.295432] TCP cubic registered
[   31.295460] NET: Registered protocol family 1
[   31.295520] Using IPI No-Shortcut mode
[   31.295723] ACPI: (supports S0 S1 S4 S5)
[   31.295803]   Magic number: 15:838:642
[   31.296683] Freeing unused kernel memory: 328k freed
[   31.298684] Time: tsc clocksource has been installed.
[   32.851785] Capability LSM initialized
[   32.933045] ACPI: Fan [FAN] (on)
[   32.940195] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   32.942226] ACPI: Thermal Zone [THRM] (40 C)
[   34.048425] usbcore: registered new interface driver usbfs
[   34.048478] usbcore: registered new interface driver hub
[   34.048550] usbcore: registered new device driver usb
[   34.050004] USB Universal Host Controller Interface driver v3.0
[   34.050128] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 16 (level, low) -> IRQ 16
[   34.050147] uhci_hcd 0000:00:08.0: UHCI Host Controller
[   34.050386] uhci_hcd 0000:00:08.0: new USB bus registered, assigned bus number 1
[   34.050436] uhci_hcd 0000:00:08.0: irq 16, io base 0x0000c000
[   34.050652] usb usb1: configuration #1 chosen from 1 choice
[   34.050720] hub 1-0:1.0: USB hub found
[   34.050740] hub 1-0:1.0: 2 ports detected
[   34.158008] ACPI: PCI Interrupt 0000:00:08.1[B] -> GSI 17 (level, low) -> IRQ 17
[   34.158028] uhci_hcd 0000:00:08.1: UHCI Host Controller
[   34.158086] uhci_hcd 0000:00:08.1: new USB bus registered, assigned bus number 2
[   34.158129] uhci_hcd 0000:00:08.1: irq 17, io base 0x0000c400
[   34.158327] usb usb2: configuration #1 chosen from 1 choice
[   34.158376] hub 2-0:1.0: USB hub found
[   34.158394] hub 2-0:1.0: 2 ports detected
[   34.199432] via-rhine.c:v1.10-LK1.4.2 Sept-11-2006 Written by Donald Becker
[   34.266268] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
[   34.266275] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[   34.266289] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
[   34.266309] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   34.266387] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 3
[   34.266433] uhci_hcd 0000:00:10.0: irq 18, io base 0x0000c800
[   34.266629] usb usb3: configuration #1 chosen from 1 choice
[   34.266687] hub 3-0:1.0: USB hub found
[   34.266708] hub 3-0:1.0: 2 ports detected
[   34.312853] Floppy drive(s): fd0 is 1.44M
[   34.373586] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
[   34.373607] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   34.373676] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 4
[   34.373710] uhci_hcd 0000:00:10.1: irq 18, io base 0x0000cc00
[   34.373900] usb usb4: configuration #1 chosen from 1 choice
[   34.373955] hub 4-0:1.0: USB hub found
[   34.373974] hub 4-0:1.0: 2 ports detected
[   34.375930] FDC 0 is a post-1991 82077
[   34.421324] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   34.481402] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
[   34.481423] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   34.481484] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 5
[   34.481519] uhci_hcd 0000:00:10.2: irq 18, io base 0x0000d000
[   34.481725] usb usb5: configuration #1 chosen from 1 choice
[   34.481782] hub 5-0:1.0: USB hub found
[   34.481802] hub 5-0:1.0: 2 ports detected
[   34.589396] ACPI: PCI Interrupt 0000:00:08.2[C] -> GSI 18 (level, low) -> IRQ 19
[   34.589425] ehci_hcd 0000:00:08.2: EHCI Host Controller
[   34.589497] ehci_hcd 0000:00:08.2: new USB bus registered, assigned bus number 6
[   34.589641] ehci_hcd 0000:00:08.2: irq 19, io mem 0xee008000
[   34.589652] ehci_hcd 0000:00:08.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   34.589831] usb usb6: configuration #1 chosen from 1 choice
[   34.589894] hub 6-0:1.0: USB hub found
[   34.589915] hub 6-0:1.0: 4 ports detected
[   34.597571] usb 1-1: string descriptor 0 read error: -71
[   34.597735] usb 1-1: configuration #1 chosen from 1 choice
[   34.601560] usb 1-1: can't set config #1, error -71
[   34.697067] ACPI: PCI Interrupt 0000:00:10.3[D] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
[   34.697095] ehci_hcd 0000:00:10.3: EHCI Host Controller
[   34.697155] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 7
[   34.697226] ehci_hcd 0000:00:10.3: irq 18, io mem 0xee009000
[   34.697237] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   34.697478] usb usb7: configuration #1 chosen from 1 choice
[   34.697546] hub 7-0:1.0: USB hub found
[   34.697567] hub 7-0:1.0: 6 ports detected
[   34.744724] usb 1-1: USB disconnect, address 2
[   34.805490] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 23
[   34.805497] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[   34.805511] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 20
[   34.809686] eth0: VIA Rhine II at 0x1e000, 00:0d:87:b8:8c:39, IRQ 20.
[   34.810411] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[   34.811809] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[   34.812330] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
[   34.812336] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[   34.812348] ACPI: PCI Interrupt 0000:00:11.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 21
[   34.812366] VP_IDE: chipset revision 6
[   34.812370] VP_IDE: not 100% native mode: will probe irqs later
[   34.812391] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[   34.812402]     ide0: BM-DMA at 0xd400-0xd407, BIOS settings: hda:pio, hdb:DMA
[   34.812422]     ide1: BM-DMA at 0xd408-0xd40f, BIOS settings: hdc:DMA, hdd:DMA
[   34.812432] Probing IDE interface ide0...
[   35.471550] hdb: ST380011A, ATA DISK drive
[   35.532076] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   35.536288] Probing IDE interface ide1...
[   36.345939] usb 6-2: new high speed USB device using ehci_hcd and address 3
[   36.417946] hdc: TSSTcorpCD/DVDW TS-H552B, ATAPI CD/DVD-ROM drive
[   36.491189] usb 6-2: configuration #1 chosen from 1 choice
[   36.865186] usbcore: registered new interface driver libusual
[   36.879417] SCSI subsystem initialized
[   36.881928] Initializing USB Mass Storage driver...
[   36.885276] usbcore: registered new interface driver hiddev
[   37.108606] usb 1-1: new full speed USB device using uhci_hcd and address 3
[   37.208578] hdd: CRD-8400B, ATAPI CD/DVD-ROM drive
[   37.270763] hdd: Disabling (U)DMA for CRD-8400B (blacklisted)
[   37.270835] ide1 at 0x170-0x177,0x376 on irq 15
[   37.283004] usb 1-1: configuration #1 chosen from 1 choice
[   37.283289] libata version 2.20 loaded.
[   37.300721] hdb: max request size: 512KiB
[   37.322846] hdb: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[   37.328259] hdb: cache flushes supported
[   37.328361]  hdb: hdb1 hdb2 < hdb5 hdb6 hdb7 hdb8 hdb9 >
[   37.426837] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   37.426852] Uniform CD-ROM driver Revision: 3.20
[   37.428869] hdd: ATAPI 40X CD-ROM drive, 128kB Cache
[   37.535905] usb 3-1: new low speed USB device using uhci_hcd and address 2
[   37.715565] usb 3-1: configuration #1 chosen from 1 choice
[   37.890055] Attempting manual resume
[   37.890063] swsusp: Resume From Partition 3:69
[   37.890065] PM: Checking swsusp image.
[   37.890559] PM: Resume from disk failed.
[   37.932342] kjournald starting.  Commit interval 5 seconds
[   37.932371] EXT3-fs: mounted filesystem with ordered data mode.
[   37.959226] usb 3-2: new low speed USB device using uhci_hcd and address 3
[   38.124769] usb 3-2: configuration #1 chosen from 1 choice
[   38.128084] scsi0 : SCSI emulation for USB Mass Storage devices
[   38.128241] usbcore: registered new interface driver usb-storage
[   38.128248] USB Mass Storage support registered.
[   38.128534] usb-storage: device found at 3
[   38.128539] usb-storage: waiting for device to settle before scanning
[   38.129707] hiddev96: USB HID v1.00 Device [Lexmark  5400 Series] on usb-0000:00:08.2-2
[   38.144730] input: PS/2+USB Mouse as /class/input/input1
[   38.144769] input: USB HID v1.10 Mouse [PS/2+USB Mouse] on usb-0000:00:10.0-1
[   38.157721] input: HID 0566:3004 as /class/input/input2
[   38.157762] input: USB HID v1.10 Keyboard [HID 0566:3004] on usb-0000:00:10.0-2
[   38.196563] input: HID 0566:3004 as /class/input/input3
[   38.196655] input,hiddev97: USB HID v1.10 Device [HID 0566:3004] on usb-0000:00:10.0-2
[   38.196684] usbcore: registered new interface driver usbhid
[   38.196689] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   43.122436] usb-storage: device scan complete
[   48.181114] eth0: link down
[   48.736740] usb 6-2: reset high speed USB device using ehci_hcd and address 3
[   49.848769] NET: Registered protocol family 17
[   52.027543] irda_init()
[   52.027578] NET: Registered protocol family 23
[   52.088029] Linux agpgart interface v0.102 (c) Dave Jones
[   52.130036] agpgart: Detected VIA P4M266x/P4N266 chipset
[   52.135340] agpgart: AGP aperture is 64M @ 0xe8000000
[   52.697132] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 17
[   52.697143] rt61 1.1.0 CVS CVS http://rt2x00.serialmonkey.com
[   52.697152] RT61: Vendor = 0x1814, Product = 0x0301 
[   52.733010] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   52.736090] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   52.904229] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x043D pid 0x00F7
[   52.904262] usbcore: registered new interface driver usblp
[   52.904267] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   53.333258] usbcore: registered new interface driver xpad
[   53.333267] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[   53.524123] Linux video capture interface: v2.00
[   53.600402] input: PC Speaker as /class/input/input4
[   53.735542] parport: PnPBIOS parport detected.
[   53.735624] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   53.848005] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[   53.848012] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   53.848025] ACPI: PCI Interrupt 0000:00:11.6[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 22
[   53.855663] PCI: Setting latency timer of device 0000:00:11.6 to 64
[   53.965941] quickcam: QuickCam USB camera found (driver version QuickCam USB 0.6.6 $Date: 2006/11/04 08:38:14 $)
[   53.965953] quickcam: Kernel:2.6.20-16-generic bus:1 class:FF subclass:FF vendor:046D product:0840
[   53.990660] quickcam: Sensor HDCS-1000/1100 detected
[   53.992810] quickcam: Registered device: /dev/video0
[   53.992847] usbcore: registered new interface driver quickcam
[   54.098697] RT61: RfIcType= 3
[   54.372484] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 22
[   54.372651] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   55.178428] fuse init (API version 7.8)
[   55.217160] lp0: using parport0 (interrupt-driven).
[   55.295845] Adding 522072k swap on /dev/disk/by-uuid/35e23a8f-e741-415b-a54a-96407ae155a9.  Priority:-1 extents:1 across:522072k
[   55.530175] EXT3 FS on hdb7, internal journal
[   56.180596] kjournald starting.  Commit interval 5 seconds
[   56.180839] EXT3 FS on hdb9, internal journal
[   56.180850] EXT3-fs: mounted filesystem with ordered data mode.
[   56.391469] kjournald starting.  Commit interval 5 seconds
[   56.391708] EXT3 FS on hdb8, internal journal
[   56.391720] EXT3-fs: mounted filesystem with ordered data mode.
[   56.417206] kjournald starting.  Commit interval 5 seconds
[   56.417462] EXT3 FS on hdb6, internal journal
[   56.417473] EXT3-fs: mounted filesystem with ordered data mode.
[   58.982694] usb 6-2: reset high speed USB device using ehci_hcd and address 3
[   64.960964] Using specific hotkey driver
[   65.049830] No dock devices found.
[   65.101488] ibm_acpi: ec object not found
[   65.227306] input: Power Button (FF) as /class/input/input5
[   65.236301] ACPI: Power Button (FF) [PWRF]
[   65.275864] input: Power Button (CM) as /class/input/input6
[   65.276365] ACPI: Power Button (CM) [PWRB]
[   65.295842] input: Sleep Button (CM) as /class/input/input7
[   65.296358] ACPI: Sleep Button (CM) [SLPB]
[   65.512992] pcc_acpi: loading...
[   69.090854] ppdev: user-space parallel port driver
[   75.210608] usb 6-2: reset high speed USB device using ehci_hcd and address 3
[   75.462180] usb 6-2: reset high speed USB device using ehci_hcd and address 3
[   77.474946] NET: Registered protocol family 10
[   77.475167] lo: Disabled Privacy Extensions
[   77.475271] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   78.350291] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   78.350300] apm: overridden by ACPI.
[   79.303411] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   79.431533] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   79.432594] NFSD: starting 90-second grace period
[   85.211732] Bluetooth: Core ver 2.11
[   85.213080] NET: Registered protocol family 31
[   85.213092] Bluetooth: HCI device and connection manager initialized
[   85.213098] Bluetooth: HCI socket layer initialized
[   85.318603] Bluetooth: L2CAP ver 2.8
[   85.318610] Bluetooth: L2CAP socket layer initialized
[   85.444279] Bluetooth: RFCOMM socket layer initialized
[   85.444763] Bluetooth: RFCOMM TTY layer initialized
[   85.444779] Bluetooth: RFCOMM ver 1.8
[   85.708440] usb 6-2: reset high speed USB device using ehci_hcd and address 3
[   85.844013] scsi 0:0:0:0: scsi: Device offlined - not ready after error recovery
[   88.251954] ra1: no IPv6 routers present
[   89.204403] [drm] Initialized drm 1.1.0 20060810
[   89.220165] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   89.226149] [drm] Initialized savage 2.4.1 20050313 on minor 0
[   89.227134] mtrr: base(0xe2000000) is not aligned on a size(0x5000000) boundary
[   89.228556] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   89.229000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 0x mode
[   89.229504] agpgart: Putting AGP V2 device at 0000:01:00.0 into 0x mode
[  368.844807] mtrr: base(0xe2000000) is not aligned on a size(0x5000000) boundary
[  368.845824] mtrr: base(0xe2000000) is not aligned on a size(0x5000000) boundary
[  368.846701] mtrr: base(0xe2000000) is not aligned on a size(0x5000000) boundary
[  368.848206] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  368.848671] agpgart: Putting AGP V2 device at 0000:00:00.0 into 0x mode
[  368.849182] agpgart: Putting AGP V2 device at 0000:01:00.0 into 0x mode

```

hope you can help me

---

### Post by Gremlinzzz on 2007-07-06
right click volume icon choose open volume control then click edit check all the tabs see if any are mute.
then right click volume icon again choose preferences high lite the one your controling sound with if you get sound.

---

### Post by Nergar on 2007-07-06
When i try to open the volume applet :
```
No volume control GStreamer plugins and/or devices found.
```

If i launch alsamixer 

```
daniel@ubuntu-pc:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

```

aplay 
```
daniel@ubuntu-pc:~$ aplay -l
aplay: device_list:222: no soundcards found...

```

And I noticed that, when GDM (login screen) appears, my system does the usual sound (some drums).

this is really weird to me.

---

### Post by Kubotaz4 on 2007-07-06
I am experiencing the same thing with the same message....but i hear no drumming at all.  I just did an update on the alsa drivers, and now the sound icon has the circle with the slash through it.  I wasnt like that before i did the driver update...the only reason why i did the driver/lib/util update was that i wasnt getting any sound before that either.  I was able to play a cd though, but with no sound...now if i open the player,  it tells me that it cant connect to the source.  getting a little frustrated.  Thanks for the help.

---

### Post by Nergar on 2007-07-07
found this, you might want to take a look at it. I'm checking it right now

[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide")

Help is still appreciated

---

### Post by deadgobby on 2007-07-07
Are you haven problems with getting other users getting sounds? If so you need to give permissions to the users for sound. Yet, does the sound work for you and being the admin? 
Gobby

---

